# RFC-0011 — Taproot Binding and Canonical Conformance

Status: Accepted

Author: Supermultiverse

Created: 2026-07-25

Ratified: 2026-08-13

---

# Abstract

STAS-01 defines a Bitcoin Digital Object as a structured Object (Type, Identity,
Content, Metadata, Integrity, Capabilities) with a single deterministic Serialized
Form — the `bdo-serialization-cbor` profile — from which Identity and Integrity
derive.

In practice, implementations that anchor BDOs on the Taproot Assets protocol have
diverged from that model: they compute Integrity over an ad-hoc, per-implementation
JSON canonicalisation rather than the STAS Serialized Form, and they conflate
Integrity (is the object intact?) with Authenticity (who vouched for it?), which the
model keeps separate.

The root cause is a gap in the standard: **no profile binds the STAS Object to the
Taproot Assets protocol.** The Representation, Serialization, and Encoding profiles are
Taproot-agnostic, so implementers have filled the gap independently and incompatibly.

This RFC establishes the alignment — Identity, Integrity, Authenticity, and Content
for a BDO-on-Taproot — and calls for a normative `bdo-taproot-binding` profile in
STAS-01. It changes no on-chain behaviour and breaks no existing object; it defines
the target that conforming implementations converge on, and the migration that gets
there without invalidating what is already signed.

---

# Motivation

BDOs are an open category: owned by the user, verifiable by anyone, carried across
compatible applications (README). That promise depends on **independent
implementations agreeing byte-for-byte on what an object is** — its Identity, and the
bytes over which Integrity is evaluated.

Today they do not agree. Because the standard never said how a STAS Object binds to a
Taproot Asset, each implementation invented its own answer:

- **Identity** is taken from the Taproot genesis `asset_id` (reasonable) but nowhere
  declared normatively.
- **Integrity** is computed over a bespoke canonical JSON of the Metadata fields —
  not the STAS `bdo-serialization-cbor` Serialized Form, and not even a recognised
  JSON canonicalisation such as RFC 8785 (JCS).
- **Authenticity** (an issuer or creator signature) is layered onto the same
  Metadata hash, conflating two properties the model separates (STAS RFC-0006;
  BDO RFC-0005 Trust Model).

A second implementation cannot reproduce the first's object identity or verify its
integrity without also reproducing its private canonicalisation — which defeats the
category. Closing this is prerequisite to genuine cross-implementation
interoperability.

---

# Problem Statement

1. **No Taproot binding.** STAS-01's Representation (RFC-0008), Serialization
   (`bdo-serialization-cbor`), and Encoding profiles define an Object and its bytes
   but not how those bind to a Taproot Asset: what is Identity, where the Serialized
   Form (or a commitment to it) lives, and how the on-chain proof relates to Integrity.

2. **Wrong canonical form.** Integrity and content-derived properties must derive from
   the STAS Serialized Form (deterministic CBOR, RFC 8949 §4.2). Deriving them from a
   per-implementation JSON canonicalisation is non-interoperable by construction.

3. **Integrity conflated with Authenticity.** STAS Integrity expresses consistency
   with an expected state and MUST NOT imply authenticity, ownership, provenance, or
   trust (STAS RFC-0006). An issuer/creator signature is Authenticity, evaluated under
   the Trust Model (BDO RFC-0005) — a distinct concern that must not *be* the Integrity
   digest, only reference it.

---

# The Mapping — STAS Object ↔ BDO on Taproot

| STAS component | Binding on Taproot | Status |
|---|---|---|
| **Type** | the declared object kind (collectible, ticket, membership, redeemable, …) | present, but must occupy the `type` slot, not be buried inside Metadata |
| **Identity** | the Taproot genesis `asset_id` | **clean** — STAS permits a protocol-defined Identity (STAS RFC-0003); it must be declared normatively |
| **Content** | the primary carried information, per Type (e.g. media for a collectible; the entitlement for a ticket) | **undefined per Type** — must be specified |
| **Metadata** | the descriptive fields (name, issuer, image, attributes, …) | present; must be serialized via the STAS profile, not ad-hoc |
| **Integrity** | a digest over the STAS Serialized Form, plus the Taproot proof as an on-chain anchor (a second Integrity scope, STAS RFC-0006) | **must move** off the ad-hoc JSON hash |
| **Capabilities** | Type-defined behaviours (redeem, delegate, transfer) | present as behaviours; not yet modelled as Capabilities |
| **Extensions** | issuer/creator attestations (e.g. a Nostr-signed authorship event), AR bindings, evolvable state | the natural home for Authenticity and app-specific data, byte-preserved (STAS RFC-0013) |

Identity and Metadata map cleanly. The load-bearing decisions are Integrity, the
Integrity/Authenticity split, per-Type Content, and — underneath all of them — the
missing Taproot binding.

---

# Alignment (normative intent)

- **A1 — Identity.** A BDO's Identity is the Taproot genesis `asset_id`. It is not
  content-derived; it is protocol-derived and stable for the object's lifetime.

- **A2 — Serialized Form on-chain.** The Taproot `asset_meta` carries a **commitment**
  (a digest) to the STAS Serialized Form, not necessarily the whole Form; the full
  Serialized Form is retrievable off-chain (Storage layer). `asset_meta` is
  size-constrained, and Integrity over a commitment is sufficient.

- **A3 — Integrity.** Integrity is a digest over the STAS `bdo-serialization-cbor`
  Serialized Form, reproducible byte-for-byte by any conforming implementation. The
  Taproot proof is a second Integrity scope binding the object to Bitcoin.

- **A4 — Authenticity is separate.** An issuer or creator signature is an **attestation
  Extension** that references the Integrity digest; it is not the Integrity digest.
  This lets a verifier reason about "intact?" and "who vouched?" independently.

- **A5 — Content.** The `content` slot is defined per Type. This RFC requires that each
  Type profile state what Content is (including "none" for a metadata-only Type).

---

# The Gap — a `bdo-taproot-binding` profile

The single normative deliverable is a new STAS-01 Layer Profile (in the STAS standard)
that binds the Object model to the Taproot Assets protocol:

- Identity ← Taproot `asset_id` (A1);
- placement of the Serialized Form / its commitment relative to `asset_meta` (A2);
- the Taproot proof as an Integrity anchor (A3);
- preservation of Identity and Integrity across mint and transfer.

Every conforming implementation implements this profile; therefore the profile is
written before implementations migrate. It is the honest missing piece that makes
"BDOs using the Taproot Assets protocol" normative rather than assumed.

---

# Migration

No existing object is invalidated.

1. **Design (this RFC + the profile).** Establish the binding above and the
   `bdo-taproot-binding` profile against a stable STAS-01, not a draft.
2. **Adopt.** New objects derive Identity/Integrity from the STAS Serialized Form and
   carry Authenticity as an attestation Extension.
3. **Dual verification.** During a deprecation window, verifiers accept **both** the
   legacy per-implementation digest and the STAS Serialized-Form Integrity. Existing
   objects keep their original digest (or receive a migration attestation).
4. **Deprecate** the legacy canonicalisation once the ecosystem has converged.

Dual verification, not a hard cut, is the requirement: a category cannot break the
objects its users already own.

---

# Scope

This RFC defines the conceptual alignment and the requirement for a Taproot binding
profile. It does not define:

- the CBOR encoding rules (STAS `bdo-serialization-cbor` / `bdo-encoding-cbor`);
- any specific implementation, wallet, or platform;
- the attestation format for Authenticity (a separate Extension specification).

---

# Non-Goals

- Changing on-chain behaviour or breaking existing signed objects.
- Adopting content-derived Identity (the Taproot `asset_id` is Identity).
- Mandating that the full Serialized Form live on-chain (a commitment suffices).

---

# Benefits

- **Interoperability by construction** — any implementation reproduces Identity and
  verifies Integrity from published rules, with no dependency on a vendor's private
  canonicalisation.
- **A coherent standard** — the reference implementation follows the standard the
  ecosystem publishes, instead of diverging from it.
- **Clean separation** — Integrity, Authenticity, Identity, and Ownership are
  independently verifiable, as the BDO models already require.

---

# Decisions — Ratified 2026-08-13

All alignment decisions are **ratified**:

- **A1 — Identity.** The Taproot Asset genesis identifier is the Identity. Ratified.
- **A2 — Commitment.** The meta payload carries a commitment to the Encoded Form, not
  necessarily the full Form. Ratified.
- **A3 — Integrity.** A digest over the STAS Serialized Form, plus the Taproot proof as
  the on-chain anchor scope. Ratified.
- **A4 — Authenticity.** Issuer/creator signatures are attestation Extensions that
  reference the Integrity digest and are never the Integrity mechanism. Ratified.
- **A5 — Content per Type.** Ratified with the following initial definitions:
  - **collectible** — the media is the Content;
  - **ticket** — the admission entitlement (event, ticket type, validity) is the
    Content; media is Metadata;
  - **membership** — the membership grant (access scope, validity) is the Content;
  - **redeemable** — the redeemable promise (what may be redeemed, and how many
    times) is the Content.

**Governing premise (recorded):** the binding follows the Taproot Assets protocol
exactly as specified by its maintainers and never diverges from it; the normative
statement of this premise is the *Taproot Assets Protocol Compatibility* section of
`urn:stas:profile:bdo-taproot-binding`.

**Profile ownership:** `urn:stas:profile:bdo-taproot-binding` is owned by the STAS
Working Group and published in the STAS standard (merged 2026-08-13, Draft 0.1.0).

**Migration priority** is a roadmap matter and does not gate these decisions.

---

# Future Work

- The `bdo-taproot-binding` profile (STAS standard).
- An Authenticity / attestation Extension specification (issuer and creator signatures).
- Modelling Type-defined behaviours as STAS Capabilities.

---

# Conclusion

BDOs promise objects that anyone can verify and carry across applications. That promise
requires independent implementations to agree, byte-for-byte, on identity and integrity.
Today they cannot, because the standard never bound its Object model to Taproot and
implementations filled the gap privately. This RFC closes the gap in principle and
directs the one normative profile that closes it in practice — without breaking a single
object already in users' hands.

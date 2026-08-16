# BDO ↔ RGB — Compatibility Study

**Can RGB contracts satisfy the Bitcoin Digital Object model?**

- Version: 0.1
- Status: **Informative / Experimental** — research, not specification
- Integrated: 2026-08-16 (`docs/research/`, per §12 Phase A)
- Normative effect: **none**

> **STATUS — INFORMATIVE / EXPERIMENTAL.** This document is a technical research
> note for review. It is not a normative BDO or STAS specification, does not
> define conformance, and should not be interpreted as an endorsement of a
> specific RGB version or implementation.

---

## Editorial Integration Note (added at integration, 2026-08-16)

*This section was added when the study entered the repository. It records how
the study relates to standards work that landed after the study was drafted,
and flags the points where later corpus decisions supersede or sharpen the
study's assumptions. It changes nothing normative anywhere.*

**1. Much of the "missing semantic surface" now exists, carrier-neutrally.**
The study's central gap (§5.3) — that independent applications need a common
way to interpret identity, issuer, metadata, capabilities and verification
evidence — has since been addressed for the category as a whole, in documents
that contain nothing Taproot-specific:

| Study says an RGB profile must define… | Already defined, carrier-neutral |
|---|---|
| Canonical metadata + integrity rules (§7.4, R5) | STAS Representation / Serialization (deterministic CBOR) / Encoding Layer Profiles |
| Object/content type semantics, capability discovery (§7.5, R6) | STAS RFC-0017 — BDO Type Vocabulary (consumption semantics; unknown-type rule) |
| Issuer binding and authenticity (§7.3, R4) | STAS Extension `urn:stas:ext:bdo-attestation` (signs a digest — carrier-agnostic by construction) |
| The object model itself | STAS-01 Core Object Model (RFC-0001..0007) |

Consequently, a future RGB profile is **not** a parallel semantic standard: it
is a **second Binding** (in the sense of STAS RFC-0012 and of
`urn:stas:profile:bdo-taproot-binding`), defining only Identity anchoring
(Contract ID), commitment placement, ownership mapping over seals, and the
portable verification package — and composing the same carrier-neutral layers
above. Where the study's compatibility matrix (§6) says *Requires Profile*,
read: *requires an RGB **binding**; the semantics already exist upstream*.

**2. The Taproot precedent to mirror.** BDO RFC-0011 (Accepted) and
`urn:stas:profile:bdo-taproot-binding` 0.2.0 resolved for Taproot Assets the
same questions §7 raises for RGB, with decisions that transfer directly:
Identity is **protocol-derived** (genesis `asset_id` ↔ the study's Contract ID
direction, §7.1); Authenticity is an **attestation Extension**, never the
integrity mechanism (§7.3); and the data-availability question (§8) was
resolved through two meta binding modes — **Inline** (the canonical document
travels with the asset's own proof material; no storage layer needed) vs
**Commitment** (digest on-chain, document via an identified Storage
arrangement). RGB's **consignments are the natural analogue of Inline Mode**:
the evidence travels with the transfer, which is precisely the stronger
reading of *Carry* the study proposes in §8.

**3. Two flags on the study's own text** (per integration instructions —
flagged, not silently rewritten):

- **§7.1 (`bdo:rgb:<network>:<contract-id>` URI):** introducing a URI scheme
  implicitly creates a **cross-carrier identity namespace**, which drags in
  exactly the questions §9 rightly defers. The Taproot precedent needed no
  URI: each binding declares "Identity = the protocol identifier". A URI
  scheme, if ever, deserves its own RFC.
- **§12 (final location `profiles/` or `spec/BDO-RGB-01.md` in this
  repository):** this conflicts with the governance hierarchy — this
  repository answers *what a BDO is*, not *how it is represented*. A future
  RGB **binding** belongs in the technical standards layer, where the Taproot
  binding lives (the naming of that layer for a non-Taproot carrier is a
  governance conversation for that day). Phase A's location
  (`docs/research/`, this file) is correct as proposed.

**4. Phase B gate (decided 2026-08-16).** The RGB profile RFC is **not** to be
opened until both hold: (i) the carrier-neutral CBOR layer is implemented and
validated in code (the conformance epic), and (ii) RGB v0.12 has stabilized.
The §11 technical questions stand as **research backlog** until the gate
opens. Condition for Phase B, agreed: *the RGB RFC should be almost purely a
binding — if drafting it requires redefining Identity, Metadata, Attestation
or Capability semantics, that is a defect found in our carrier-neutral layer,
not an RGB-specific need.* That test is the strategic value of this study:
the milestone before "support RGB" is proving the BDO layer is genuinely
carrier-neutral and executable.

*End of integration note. The study follows verbatim.*

---

## 1. Executive Summary

This study evaluates whether a digital object represented through RGB can
satisfy the conceptual requirements of a Bitcoin Digital Object (BDO), and
whether doing so requires changes to the current BDO architecture or to
STAS-01.

**Primary finding.** An RGB contract can, in principle, satisfy the BDO
properties Own, Verify, and Carry. The BDO conceptual architecture does not
need to change. STAS-01 should also remain unchanged because it is explicitly
a Taproot Assets interoperability specification. If RGB support is formalized,
it should be expressed through a separate compatibility profile or future BDO
interoperability specification.

The core architectural relationship proposed by this study is:

- **Bitcoin Digital Objects (BDO)** — conceptual ownership category
- **STAS-01** — first interoperability specification, specifically for Taproot Assets
- **RGB** — independent Bitcoin-native client-side-validated smart-contract architecture
- **Future RGB BDO Profile** — potential mapping layer defining the minimum
  conditions under which an RGB contract may be recognized as a BDO

The most important unresolved issue is not Bitcoin anchoring or ownership.
RGB provides strong primitives for both. The main gap is **semantic
interoperability**: independent applications need a common way to interpret
object identity, issuer, metadata, capabilities, lifecycle, and portable
verification evidence consistently.

**Recommended decision**

1. Do not modify the canonical BDO definition as a result of this study.
2. Do not expand STAS-01 to cover RGB.
3. Treat RGB as a potential alternative carrier/representation layer for BDOs.
4. Integrate this document, after technical review, as informative research
   rather than normative specification text.
5. If the mapping survives review, open a dedicated RFC for an experimental
   RGB compatibility profile.

## 2. Scope and Non-Goals

### 2.1 Scope

The study maps the current BDO conceptual model to the RGB architecture, with
particular attention to RGB v0.12 concepts. It evaluates compatibility at the
level of object identity, ownership, verification, portability, issuer
semantics, metadata, capabilities, provenance, lifecycle, trust assumptions,
and data availability.

### 2.2 Non-goals

- This document does not define a production RGB contract.
- It does not define a normative RGB BDO schema, issuer, interface, or ABI.
- It does not specify wallet APIs, indexers, storage services, marketplaces,
  or custody systems.
- It does not claim that current RGB wallets are mutually interoperable at the
  BDO semantic layer.
- It does not define cross-carrier migration between Taproot Assets and RGB.
- It does not modify STAS-01 conformance.
- It does not choose between competing RGB ecosystem branches or
  implementations beyond using primary RGB v0.12 design material for
  architectural analysis.

## 3. Baseline Architecture

### 3.1 Bitcoin Digital Objects

The canonical BDO repository defines a Bitcoin Digital Object as a digital
object whose ownership is secured by Bitcoin. The category is explicitly open
and implementation-independent. Its three core properties are Own, Verify, and
Carry.

```text
Bitcoin Digital Object
        |
        +-- Own
        |     Ownership belongs to the user
        |
        +-- Verify
        |     Authenticity can be independently verified
        |
        +-- Carry
              The same object can be recognized and interpreted
              across compatible applications
```

The BDO repository also explicitly separates the conceptual category from
implementation layers and states that future specifications may define
compatible BDO implementations.

### 3.2 STAS-01

STAS is the Shared Taproot Assets Standard. Its current scope is deliberately
narrow: STAS-01 specifies the interoperable technical representation of BDOs
using the Taproot Assets protocol. It defines representation and conformance,
not the conceptual meaning of BDO itself.

> **Architectural constraint.** RGB support should not be added by stretching
> STAS-01. Doing so would weaken the clean separation already established
> between the implementation-independent BDO category and the Taproot
> Assets-specific STAS standard.

## 4. RGB Technical Model Relevant to BDO

RGB is a client-side-validation smart-contract system secured through Bitcoin
commitments and single-use seals. Contract state and transition data are
primarily maintained outside the Bitcoin blockchain; Bitcoin provides the
commitment and double-spend-resistant settlement substrate.

### 4.1 Client-side validation

Validation is performed by the parties that need to validate a specific
contract history or state transition rather than by every Bitcoin node. This
is central to RGB's privacy and scalability model and materially affects the
BDO Carry and data-availability analysis.

### 4.2 Single-use seals and ownership

RGB uses single-use seals tied to Bitcoin transaction outputs to prevent
conflicting state evolution. A party able to control the relevant Bitcoin
spending condition can exercise the rights associated with owned RGB state,
subject to contract rules.

### 4.3 RGB v0.12 architectural change

RGB v0.12 substantially changes the historical RGB programming model. The
v0.12 release line unifies state, simplifies seals, introduces
zk-AluVM-oriented contract programming, and removes the previous
schemata-centric model. Consequently, a future BDO-over-RGB design should
target the v0.12 contract model rather than assume that historical RGB20/RGB21
schemata are the permanent abstraction.

> **Important versioning note.** Historical RGB21/UDA material remains useful
> for understanding prior non-fungible asset semantics, but it should not be
> treated as the definitive contract model for RGB v0.12.

## 5. Compatibility with Own · Verify · Carry

### 5.1 Own — Compatible

BDO requires ownership to belong to the user rather than to an application or
marketplace, and for ownership to ultimately derive from Bitcoin. RGB
satisfies this structurally through owned contract state controlled via
Bitcoin-linked single-use seals.

```text
BDO ownership
     |
     v
RGB owned contract state
     |
     v
single-use seal
     |
     v
Bitcoin transaction graph / spending authority
```

A wallet or application may facilitate key management, state storage, transfer
construction, or discovery, but it is not conceptually required to be the
source of truth for ownership.

### 5.2 Verify — Compatible

BDO requires independent verification without trusting a specific platform.
RGB is explicitly designed for client-side validation. A verifier with the
necessary contract data and Bitcoin evidence can validate the relevant history
and current state against consensus rules and contract logic.

The verification mechanism differs from Taproot Assets, but BDO does not
require a particular proof format. The requirement is that verification be
objective, portable, and not dependent on a vendor assertion.

### 5.3 Carry — Partially direct, semantically incomplete

RGB provides a natural mechanism for transporting contract state and proof
material between participants. In this cryptographic sense, RGB strongly
supports Carry. However, Carry in the BDO model also requires compatible
applications to recognize and interpret the same object consistently.

> **Key distinction.** RGB can make contract state portable. It does not, by
> itself, guarantee that independent applications will attach the same BDO
> meaning to that state.

A BDO compatibility profile would therefore need to standardize the minimum
semantic surface necessary for another implementation to identify the object,
determine its issuer and ownership, discover its metadata, understand its
capabilities, validate continuity, and know which evidence must accompany the
object.

## 6. Compatibility Matrix

| BDO concept | Taproot Assets / STAS-01 | RGB candidate mapping | Assessment |
|---|---|---|---|
| Identity | STAS-defined BDO/object identifiers | RGB Contract ID plus BDO carrier binding | Requires Profile |
| Ownership | Taproot Assets state + Bitcoin | Owned RGB state + single-use seal + Bitcoin | Direct |
| Bitcoin security | Bitcoin-anchored asset state | Bitcoin commitments / seals | Direct |
| Transfer | Taproot Assets transfer/proofs | RGB state transition / consignment | Direct |
| Independent verification | Taproot Assets proof validation | Client-side validation of contract history/state | Direct |
| Issuer | STAS issuer/integrity representation | Contract genesis / issuer identity semantics | Requires Profile |
| Authenticity | Issuer + integrity + proof validation | Genesis + contract validation + issuer binding | Supported |
| Metadata | STAS metadata model | Contract/application data | Requires Profile |
| Capabilities | STAS capability representation | Semantic fields and/or enforceable contract logic | Requires Profile |
| Provenance | Asset/proof history | Contract transition history | Supported |
| Continuity | Stable object identity across transfers | Stable contract identity across state evolution | Supported |
| Carry: evidence | Proof package / implementation data | Consignment / relevant client-side state | Supported |
| Carry: semantics | STAS interpretation | No BDO semantic convention yet | Open Gap |
| Data availability | Implementation-dependent proof/storage model | Holder/participants must retain or obtain required client-side data | Open Question |
| Cross-carrier identity | Not defined | Not defined | Out of Scope |

*(Integration note: where this matrix says "Requires Profile", the semantic
layer has since been defined carrier-neutrally — see the Editorial Integration
Note; what remains is the RGB binding.)*

## 7. Detailed Mapping

### 7.1 Canonical identity

A BDO must expose exactly one canonical identity that persists through
ownership and state changes. For RGB, the natural protocol-level anchor is the
Contract ID. However, the BDO conceptual identifier should not be defined as
"the Contract ID" in a way that makes BDO itself RGB-dependent.

```text
Conceptual BDO identity
        |
        +-- carrier = rgb
        +-- network = <network>
        +-- protocol object = <RGB Contract ID>
```

A future profile could define a canonical URI or structured identifier such as
`bdo:rgb:<network>:<contract-id>`, subject to collision, encoding, versioning,
and future migration analysis. This is only a design direction, not a proposal
in this document. *(Integration note: see the Editorial Integration Note, flag
on the URI namespace.)*

### 7.2 Ownership

The BDO ownership model maps cleanly to RGB owned state. The profile would
need to define what portion of RGB state constitutes ownership of the BDO
itself when a contract contains multiple state components or rights.

### 7.3 Issuer and authenticity

BDO distinguishes the current owner from the issuer. RGB separates contract
genesis/issuance from subsequent owners, which is compatible with this
requirement. A compatibility profile must define how issuer identity is
represented, whether issuer signatures are required, how key rotation or
revocation is handled, and how an application proves that the presented issuer
binding is part of the object's authentic genesis semantics.

### 7.4 Metadata

RGB can carry or reference object-related data, but interoperable BDO metadata
requires canonical semantics. A profile should determine which fields are
mandatory, which are optional, which are mutable, what content-addressing
rules apply, and which metadata changes affect authenticity or continuity.

- name / human-readable label
- description
- media references and integrity digests
- issuer presentation data
- collection or grouping
- external references
- attributes
- capability descriptors
- content type / object type
- version and profile identifiers

### 7.5 Capabilities

RGB can potentially go beyond descriptive capabilities because contract logic
may enforce state transitions. This creates an important distinction for a
future profile:

- **Descriptive capability** — an application interprets a declared ability or
  entitlement.
- **Cryptographically bound capability** — the declaration is bound to
  authenticated contract state.
- **Contract-enforced capability** — RGB contract logic itself constrains
  exercise, consumption, transfer, or state evolution.

The profile should not require all capabilities to be contract-enforced. It
should instead define how applications discover the capability class and its
verification method.

### 7.6 Lifecycle, continuity and provenance

RGB contract evolution provides a strong basis for BDO continuity. The profile
must distinguish changes that preserve object identity from events that
terminate, replace, split, merge, redeem, or otherwise transform the BDO. This
becomes especially important if an RGB contract can represent multiple objects
or multiple independently owned state components.

### 7.7 Verification package

A BDO-over-RGB implementation should define a minimum portable verification
package. The package should allow a compatible verifier to reconstruct enough
context to validate identity, ownership, authenticity, and continuity without
contacting the original application.

- contract identifier and network
- profile/version identifier
- required contract/genesis data
- relevant transition history or compact proof material
- Bitcoin commitment/witness evidence required by the RGB implementation
- issuer/authenticity evidence
- metadata integrity references
- current ownership/state evidence
- optional application data kept clearly outside the conformance-critical core

## 8. Data Availability and the Meaning of Carry

RGB exposes an issue that should be treated explicitly in BDO architecture
discussions: Bitcoin anchoring does not imply universal availability of the
client-side contract data needed to validate or continue using an object.

This does not inherently violate Carry. Instead, it suggests a stronger and
more precise interpretation: the user must be able to retain or obtain a
portable package containing enough authenticated information to continue
control and verification in another compatible implementation.

> **Proposed interpretation for review — not normative.** Carry means that
> ownership authority and the verification material necessary to continue
> recognizing and using the object can travel with the user across compatible
> implementations.

This formulation should be reviewed carefully before any change to canonical
BDO language. It may improve the architecture generally, but the present study
does not recommend changing the core definition solely to accommodate RGB.

## 9. Cross-Carrier Identity Is a Separate Problem

The fact that both Taproot Assets and RGB may represent valid BDOs does not
imply that the same BDO can migrate between them while automatically retaining
canonical identity.

```text
Category-level multi-carrier support
    BDO A may be represented by Taproot Assets
    BDO B may be represented by RGB
    -> compatible with current architecture

Cross-carrier migration
    Taproot representation X == RGB representation Y
    -> requires an explicit cryptographic binding/migration model
    -> NOT defined by current BDO or STAS architecture
```

A future cross-carrier mechanism would need anti-duplication semantics,
termination or locking of the prior representation, explicit issuer/owner
authorization, replay protection, and a canonical identity rule. This should
remain out of scope for an initial RGB profile.

## 10. Candidate Minimum Requirements for an Experimental RGB BDO Profile

If technical review confirms the mapping, a future experimental profile could
define only the minimum interoperable surface. It should avoid prescribing
wallet UX, custody, storage vendors, marketplaces, or business logic.

| Requirement | Draft compatibility condition |
|---|---|
| R1 — Profile declaration | The RGB contract/object representation MUST unambiguously declare the BDO compatibility profile and version it follows. |
| R2 — Canonical identity | The implementation MUST expose a deterministic canonical BDO identifier bound to the RGB contract and Bitcoin network. |
| R3 — Ownership mapping | The profile MUST define which owned RGB state represents control of the BDO and how current ownership is verified. |
| R4 — Issuer binding | The profile MUST define authenticated issuer semantics distinguishable from current ownership. |
| R5 — Metadata integrity | Conformance-critical metadata or references MUST have defined integrity and canonicalization rules. |
| R6 — Capability discovery | Capabilities MUST be discoverable through standardized semantics and MUST identify whether they are descriptive, cryptographically bound, or contract-enforced. |
| R7 — Portable verification | A holder MUST be able to export or transfer sufficient evidence for a compatible implementation to verify the object independently. |
| R8 — Continuity rules | The profile MUST define which state transitions preserve object identity and how terminal/redeemed states are represented. |
| R9 — No vendor dependency | No vendor API, marketplace database, or proprietary registry may be required as the authoritative source of identity or ownership. |
| R10 — Bitcoin-rooted verification | The ownership/validity chain MUST ultimately resolve to Bitcoin-secured RGB consensus evidence. |

These requirements are intentionally phrased as a design checklist, not
normative language. Code review should determine whether each requirement can
be implemented naturally in RGB v0.12 and whether any of them incorrectly
assume data structures or lifecycle primitives that RGB does not expose.

## 11. Technical Questions for Code Review

*(Integration note: research backlog — to be resolved against RGB v0.12 code
only when the Phase B gate opens.)*

1. What is the precise stable identifier primitive in RGB v0.12 that should
   anchor a BDO carrier binding: Contract ID alone, or Contract ID plus
   additional type/issuer/profile context?
2. Can one RGB v0.12 contract naturally represent exactly one BDO, or is a
   multi-object contract model likely? If multi-object, what is the correct
   sub-identity primitive?
3. Which v0.12 data structures replace the historical schema/interface
   assumptions relevant to UDA/RGB21?
4. What data must a recipient possess to validate a complete current-state
   consignment for the proposed BDO use case?
5. What is the minimum self-contained export package a wallet can provide so
   that another implementation can independently validate and continue the
   object?
6. How should reorgs, RBF, unconfirmed witness transactions, and
   Lightning/channel state affect BDO verification status?
7. How are issuer/developer identities represented in current RGB v0.12
   libraries, and are those commitments appropriate for BDO issuer
   authentication?
8. Can metadata and media integrity be bound directly into consensus-relevant
   contract state without making common object updates impractical?
9. Which capability semantics are best expressed as authenticated metadata
   versus enforceable RGB contract logic?
10. How should burned, redeemed, revoked, expired, frozen, split, merged, or
    transformed states map to BDO lifecycle semantics?
11. Does RGB v0.12 provide a stable forward-compatibility model sufficient for
    long-lived BDO identity and verification?
12. What data availability failure modes can cause a valid RGB-controlled
    object to become practically unusable, and what backup/export requirements
    should a BDO profile impose?
13. Can verification remain vendor-neutral without relying on a global RGB
    registry, explorer, or specific indexer?
14. What Lightning-specific differences, if any, must the BDO profile expose
    to applications, or should L1/LN transport remain below the semantic
    layer?

## 12. Proposed Repository Integration Path

The safest integration path is to preserve the current governance separation
between conceptual architecture, informative research, RFC discussion, and
normative specification.

```text
bitcoin-digital-objects/
  docs/
    research/
      bdo-rgb-compatibility-study.md    <-- suggested initial location

Later, if validated:
  rfcs/
    RFC-XXXX-rgb-compatibility-profile.md

Potential future result:
  profiles/ or spec/
    BDO-RGB-01.md                       <-- only after governance acceptance
```

*(Integration note: the final-profile location above is flagged — see the
Editorial Integration Note; a technical binding belongs in the standards
layer, not this conceptual repository.)*

### 12.1 Phase A — Research

- Integrate this compatibility study as informative research.
- Validate every RGB-specific statement against current v0.12 code and
  primary documentation.
- Resolve the technical questions in Section 11.
- Do not define conformance.

### 12.2 Phase B — RFC

- Propose a minimal compatibility profile only if implementation mapping is
  technically sound.
- Define object identity, ownership mapping, issuer semantics, metadata
  integrity, capability discovery, portable verification, and lifecycle.
- Include test vectors or a minimal reference implementation.
- Keep RGB-specific rules outside STAS-01.

### 12.3 Phase C — Experimental implementation

- Issue a minimal RGB object satisfying the proposed profile.
- Export it from implementation A and verify it in implementation B.
- Test loss/recovery of application state, recipient-only validation,
  metadata retrieval, reorg behavior, and transfer continuity.
- Only then consider formal conformance language.

## 13. Risks and Design Traps

| Risk | Why it matters |
|---|---|
| Protocol-version coupling | A profile tied too closely to transient v0.12 APIs rather than stable RGB consensus concepts could age badly. |
| Semantic overreach | Trying to standardize all RGB contract behavior would turn BDO into a competing smart-contract framework. |
| STAS scope pollution | Adding RGB semantics to STAS would undermine its clear Taproot Assets scope. |
| Data-availability blindness | A profile that proves ownership but fails to define portable state/evidence requirements would not fully satisfy Carry. |
| Registry dependency | Requiring a specific global registry/explorer would recreate vendor or infrastructure lock-in. |
| One-contract/one-object assumption | If RGB applications naturally represent multiple independent objects inside one contract, Contract ID alone may be insufficient. |
| Metadata ambiguity | Application-only JSON without canonical integrity rules would create incompatible objects that are cryptographically valid but semantically non-portable. |
| Cross-carrier duplication | Premature migration support could allow two live representations to claim the same BDO identity. |

## 14. Strategic Interpretation

RGB should not be framed as a direct competitor to the BDO category. RGB and
Taproot Assets are protocols/architectures that can provide Bitcoin-native
ownership and state primitives. BDO is intended to define the interoperable
digital-object semantics above such primitives.

> **Working thesis.** RGB and Taproot Assets define ways to own and transfer
> Bitcoin-secured state. BDO defines what that owned state means as a portable
> digital object.

If a real RGB implementation can satisfy a carrier-neutral BDO model without
changing the BDO definition, that would be strong architectural evidence that
BDO is genuinely an open category rather than an abstraction built only around
Taproot Assets.

## 15. Conclusions

1. No fundamental conceptual incompatibility has been identified between BDO
   and RGB.
2. RGB can plausibly satisfy Own through Bitcoin-linked owned state and
   single-use seals.
3. RGB can plausibly satisfy Verify through client-side validation of
   authenticated contract history/state.
4. RGB can satisfy cryptographic Carry, but BDO-level semantic Carry requires
   an interoperability profile.
5. The current BDO definition should remain unchanged.
6. STAS-01 should remain Taproot Assets-specific and should not be expanded to
   RGB.
7. A future RGB BDO profile should be separate, minimal, vendor-neutral, and
   tested through at least two independent implementations.
8. Data availability and portable verification evidence are the most important
   architectural issues to resolve.
9. Cross-carrier identity/migration should remain explicitly out of scope for
   the first profile.

## 16. Primary Sources

- **Bitcoin Digital Objects — canonical repository**
  <https://github.com/supermultiverse-LLC/bitcoin-digital-objects>
  Defines BDO as an open, implementation-independent category; Own, Verify,
  Carry; relationship to STAS and future specifications.
- **STAS — Shared Taproot Assets Standard**
  <https://github.com/supermultiverse-LLC/stas-standard>
  Defines STAS-01 as the interoperable representation of BDOs specifically
  using Taproot Assets.
- **RGB v0.12 RC1 architecture overview**
  <https://rgb.tech/blog/release-v0-12-rc-1/>
  Primary RGB source describing v0.12 simplification, state unification, seal
  unification, zk-AluVM direction, and removal of schemata.
- **RGB Core releases**
  <https://github.com/RGB-WG/rgb-core/releases>
  Primary release history for RGB consensus-layer code.
- **RGB Blackpaper — Design overview**
  <https://black-paper.rgb.tech/general-information/2.-protocol-design/2.2.-design-overview>
  Primary conceptual source for RGB client-side validation, contract state,
  Bitcoin commitments, ownership, and separation of issuer and state owner.
- **RGB Blackpaper — Client-side validation**
  <https://black-paper.rgb.tech/consensus-layer/3.-client-side-validation>
  Background on the client-side-validation paradigm.
- **RGB Blackpaper — Single-use seals**
  <https://black-paper.rgb.tech/consensus-layer/3.-client-side-validation/3.2.-single-use-seals>
  Technical basis for Bitcoin-linked single-use seals and double-spend-
  resistant client-side state.

## 17. Document Status

- Version: 0.1
- Status: Informative / Experimental
- Intended audience: BDO/STAS maintainers and technical reviewers
- Normative effect: None
- Integrated: 2026-08-16 into `docs/research/` (Phase A) with the Editorial
  Integration Note above; no normative document was modified.
- Next action: **gated** — the Phase B RFC opens only when the carrier-neutral
  CBOR layer is implemented and validated in code and RGB v0.12 has
  stabilized. Until then, §11 stands as research backlog.

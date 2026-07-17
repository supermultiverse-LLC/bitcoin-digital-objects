# BDO ↔ STAS-01 Consistency Mapping

**Status:** Draft v1.0

**Type:** Informative (reference)

---

# Purpose

This document records the cross-standard consistency review between the Bitcoin Digital Objects (BDO) conceptual model and the STAS-01 interoperability specification.

It is informative. It defines no new requirements. It maps each BDO concept to the STAS component or layer that represents it, records the outcome of the consistency review, and documents two alignment notes for a future STAS profile.

The layering follows RFC-0001 and RFC-0002 of this repository: BDO defines the concepts; STAS-01 is one interoperable representation of those concepts. A specification implements the BDO model; it does not redefine it.

---

# Concept Mapping

| BDO concept | BDO RFC | STAS representation | Relationship |
|---|---|---|---|
| Identity | RFC-0003 | STAS Identity (STAS RFC-0003) | Direct component. Consistent, with two alignment notes below. |
| Capability | RFC-0004 | STAS Capabilities (STAS RFC-0007) | Direct component. Fully consistent. |
| Metadata | RFC-0008 | STAS Metadata (STAS RFC-0005) | Direct component. |
| Ownership | RFC-0006 | STAS Content / Integrity + Taproot Assets / Bitcoin | Supported, not defined by STAS core. STAS-01 explicitly does not define ownership semantics. |
| Lifecycle | RFC-0007 | STAS state / Transport + future specifications | Conceptual. STAS represents individual states and events; the lifecycle itself stays in BDO. |
| Issuer | RFC-0009 | STAS provenance / Content / Integrity | Supported, not a STAS component. |
| Trust | RFC-0005 | STAS Integrity substrate + Bitcoin as root of trust | Principle. STAS provides the verification substrate; the stance stays in BDO. |
| Verification | RFC-0010 | STAS Integrity (STAS RFC-0006) + verification mechanisms | Supported through Integrity. |

Three BDO concepts map one-to-one onto STAS Core Object Model components (Identity, Capability, Metadata). The remaining five (Ownership, Lifecycle, Issuer, Trust, Verification) are BDO-layer concepts that STAS **supports** through its components and pipeline but does not itself define. This is the intended separation established by RFC-0001 and RFC-0002.

---

# Review Outcome

The review compared the mirrored pairs directly:

- BDO Identity (RFC-0003) against STAS Identity (STAS RFC-0003);
- BDO Capability (RFC-0004) against STAS Capabilities (STAS RFC-0007);

and checked that the five BDO-layer concepts do not contradict the STAS representation.

**No contradictions were found.**

**Capability is fully consistent.** BDO frames a capability as a possibility that is optional, independent from ownership, interpreted by compatible applications, and safely ignorable when unrecognized. STAS frames it as a semantic possibility interpreted by Type that is not an operation, authorization, availability, or execution. The two align without friction, and BDO's "ignore unrecognized capabilities" corresponds to the STAS extension-processing rules (STAS RFC-0013).

**Identity is consistent, with two alignment notes** recorded below. These are differences of strength, not contradictions: BDO states a stricter requirement than the STAS core.

---

# Alignment Notes

The following two notes identify places where the BDO model is stricter than the STAS core Identity component. They are not contradictions — the BDO requirement is a stricter case of the STAS requirement — but a STAS representation could conform to STAS while failing to satisfy the BDO model.

### Note 1 — Uniqueness scope

- BDO RFC-0003 requires identity to be **globally unique**.
- STAS RFC-0003 requires identity to be unique **within its intended scope**.

### Note 2 — Permanence strength

- BDO RFC-0003 requires identity to be **permanent** ("Identity must not change").
- STAS RFC-0003 states identity **SHOULD** be preserved throughout the object's lifetime.

---

# Resolution

The two alignment notes are **deferred to a future STAS profile**, not resolved by changing the STAS core.

The STAS core is intentionally kept general so that STAS-01 can serve as one representation among the multiple compatible specifications anticipated by RFC-0002. A future **STAS BDO Profile** (post-v1) will strengthen the two properties for the purpose of representing Bitcoin Digital Objects:

- require **global** uniqueness of identity;
- strengthen identity permanence from **SHOULD** to **MUST**.

No erratum to the STAS core is required. No merged RFC in either repository is changed by this review. Until the STAS BDO Profile exists, an implementation that represents Bitcoin Digital Objects with STAS-01 should apply these two strengthenings itself.

---

# Conclusion

The BDO conceptual model and the STAS-01 representation are consistent. Every BDO concept maps cleanly onto a STAS component or is a BDO-layer concept that STAS supports without redefining, and the only differences found are two points where BDO is deliberately stricter than the general STAS core — both to be carried by a future STAS BDO Profile.

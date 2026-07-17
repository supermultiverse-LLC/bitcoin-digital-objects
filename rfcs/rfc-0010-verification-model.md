# RFC-0010 — Define the Bitcoin Digital Object Verification Model

Status: Draft

Author: Supermultiverse

Created: 2026-07-17

---

# Abstract

This RFC defines the verification model for Bitcoin Digital Objects (BDOs).

Ownership only has value if it can be independently verified. Bitcoin Digital Objects are designed so that existence, identity, ownership, authenticity, and continuity can be confirmed without relying on a trusted intermediary.

This RFC defines the conceptual verification model shared by every Bitcoin Digital Object. It defines what verification establishes, not how it is performed; verification mechanisms belong to interoperability specifications such as STAS-01.

---

# Motivation

Traditional digital platforms require trust. Users trust databases, companies, and applications to answer questions about what they own.

Bitcoin introduced a different model, in which verification replaces trust. Bitcoin Digital Objects extend this principle to digital ownership.

A shared verification model defines the objective questions any party may answer for themselves, so that ownership and authenticity never depend on the word of an issuer, a marketplace, or an application.

---

# Verification

Verification answers objective questions about a Bitcoin Digital Object, such as:

- Does this object exist?
- Is this the same object?
- Who currently owns it?
- Who issued it?
- Has ownership changed?
- Is the object authentic?

Verification does not answer subjective questions, such as:

- Is this object valuable?
- Is this issuer reputable?
- Should I engage with this project?

Objective questions belong to the verification model. Subjective questions belong to human judgement and remain outside it.

---

# Authenticity

Authenticity establishes that a Bitcoin Digital Object originates from its claimed issuer.

Authenticity is objective and can be independently confirmed. It should never depend on the continued existence of the issuing platform, and it is established by verification rather than by an issuer's assertion, consistent with the Issuer Model.

---

# Provenance

Every Bitcoin Digital Object carries a verifiable history.

Ownership may change, applications may change, and representations may change, yet the object's provenance remains verifiable. Provenance allows any party to confirm not only the object's current state but the chain of events that led to it.

---

# Verification versus Trust

Verification is a technical process. Trust is a human decision.

Bitcoin Digital Objects maximize what can be verified while minimizing what must be trusted. Users remain free to decide whom they trust, but the architecture does not require that trust in order to establish objective facts about an object.

The Trust Model establishes why trust is minimized and why Bitcoin is the root of trust. This RFC establishes what can be objectively confirmed once that principle is in place. The two are complementary: trust is the stance, verification is the mechanism by which the stance becomes practical.

---

# Verification Independence

Verification should remain independent from:

- applications;
- wallets;
- marketplaces;
- custodians;
- companies.

Any compatible implementation provided with the same evidence should reach the same verification result. Independence is what makes verification meaningful across parties who do not trust one another.

---

# Continuity

Verification also confirms continuity.

A party should always be able to answer:

> Is this still the same Bitcoin Digital Object?

Verification therefore protects identity continuity across the entire lifetime of the object, connecting every phase of the Lifecycle Model. Without verifiable continuity, a sequence of states cannot be shown to belong to one object.

---

# Relationship with Ownership

Ownership defines who controls a Bitcoin Digital Object.

Verification allows anyone to independently confirm that ownership. Ownership is meaningful precisely because it can be verified without trusting the party that asserts it, as established by the Ownership Model.

---

# Relationship with Identity

Identity defines what the object is.

Verification confirms that identity and its continuity over time. Verification never assigns or alters identity; it establishes, objectively, that a given object is the one it claims to be.

---

# Relationship with Issuers

Verification confirms that a Bitcoin Digital Object originates from its claimed issuer.

This confirmation must remain independent of the issuer's continued existence. A claim of issuance carries weight only insofar as it can be verified, consistent with the Issuer Model.

---

# Relationship with Trust

The Trust Model defines the principle that authenticity and ownership are determined by verification rather than by trusting an intermediary, with Bitcoin as the common root of trust.

This RFC defines the objective properties that principle makes verifiable. Neither redefines the other: the Trust Model states the stance, and the verification model states what that stance lets any party confirm for themselves.

---

# Relationship with Specifications

This RFC defines the conceptual verification model only.

Concrete proofs, signatures, verification procedures, and the evidence required to verify belong to interoperability specifications such as STAS-01.

A specification implements this verification model; it does not redefine it. Multiple compatible specifications may provide verification that reaches the same objective results.

---

# Design Principles

Verification should be:

- objective;
- independent;
- reproducible;
- interoperable;
- implementation-agnostic.

---

# Future Work

Subsequent RFCs and specifications may define:

- proof representation and serialization;
- verification procedures;
- verifier interoperability;
- provenance and history representation;
- offline verification workflows.

These build upon the verification model without altering it.

---

# Conclusion

Verification is what turns ownership from a claim into a fact. Existence, identity, ownership, authenticity, provenance, and continuity can all be confirmed by anyone, without trusting anyone.

Trust remains a choice. Verification does not have to be.

> Trust is optional.
>
> Verification should not be.

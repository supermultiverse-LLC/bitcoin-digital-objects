# AP-005 — BDO Verification Model

**Status:** Draft v1.0

---

# Abstract

Ownership only has value if it can be independently verified.

Bitcoin Digital Objects (BDOs) are designed so that ownership, authenticity and continuity can be verified without relying on a trusted intermediary.

This document defines the conceptual verification model shared by every Bitcoin Digital Object.

It intentionally remains independent from any particular implementation or interoperability specification.

---

# Introduction

Traditional digital platforms require trust.

Users trust databases.

They trust companies.

They trust applications.

Bitcoin introduced a different model.

Verification replaces trust.

Bitcoin Digital Objects extend this principle to digital ownership.

---

# Verification

Verification answers objective questions.

Examples include:

- Does this object exist?
- Is this the same object?
- Who currently owns it?
- Who issued it?
- Has ownership changed?
- Is the object authentic?

Verification does not answer subjective questions.

Examples include:

- Is this object valuable?
- Is this issuer reputable?
- Should I trust this project?

Those questions belong outside the verification model.

---

# Authenticity

Authenticity proves that a Bitcoin Digital Object originates from its claimed issuer.

Authenticity is objective.

It can be independently verified.

Authenticity should never depend on the continued existence of the issuing platform.

---

# Provenance

Every Bitcoin Digital Object carries a verifiable history.

Ownership may change.

Applications may change.

Representations may change.

The object's provenance remains verifiable.

---

# Trust

Trust is a human decision.

Verification is a technical process.

Bitcoin Digital Objects maximize verification while minimizing required trust.

Users remain free to decide whom they trust.

The architecture does not require that trust.

---

# Verification Independence

Verification should remain independent from:

- applications
- wallets
- marketplaces
- custodians
- companies

Compatible implementations should reach the same verification result.

---

# Continuity

Verification also confirms continuity.

Users should always be able to answer:

> Is this still the same Bitcoin Digital Object?

Verification therefore protects identity continuity across the lifetime of the object.

---

# Relationship with Ownership

Ownership defines who controls a Bitcoin Digital Object.

Verification allows anyone to independently confirm that ownership.

---

# Relationship with Identity

Identity defines what the object is.

Verification confirms that identity.

---

# Relationship with Specifications

This document intentionally avoids implementation details.

Verification mechanisms belong to interoperability specifications such as STAS-01.

This document defines only the conceptual verification model.

---

# Design Principles

Verification should be:

- objective
- independent
- reproducible
- interoperable
- implementation-agnostic

---

# Guiding Principle

> Trust is optional.

> Verification should not be.
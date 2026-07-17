# RFC-0009 — Define the Bitcoin Digital Object Issuer Model

Status: Draft

Author: Supermultiverse

Created: 2026-07-17

---

# Abstract

This RFC defines the issuer model for Bitcoin Digital Objects (BDOs).

Every Bitcoin Digital Object originates from an issuer. The issuer creates the object and establishes its initial authenticity. Once issued, however, the issuer no longer defines ownership.

This RFC defines the conceptual role of issuers only. It intentionally avoids implementation details, which belong to interoperability specifications such as STAS-01.

---

# Motivation

Every object has an origin. A Bitcoin Digital Object begins with an issuer, who establishes the object's initial existence and authenticity.

After issuance, ownership becomes independent. Issuance and ownership are separate concepts, and keeping them separate is what prevents the issuer from becoming a permanent authority over an object that belongs to its owner.

A shared issuer model lets independent applications agree on what an issuer does — and, just as importantly, on what an issuer may not do.

---

# What is an Issuer

An issuer is an entity that creates a Bitcoin Digital Object.

An issuer may be:

- a person;
- a company;
- a community;
- an institution;
- a software system;
- an autonomous protocol.

The architecture intentionally does not restrict who may issue Bitcoin Digital Objects.

---

# Responsibilities

The issuer is responsible for establishing the initial authenticity of the object.

Typical responsibilities include:

- creating the object;
- defining its initial metadata;
- establishing its initial owner;
- providing provenance;
- publishing the information required for independent verification.

The issuer does not control the object after issuance unless it remains the current owner.

---

# Issuance

Issuance is a one-time event.

A Bitcoin Digital Object is issued exactly once. Issuance establishes:

- identity;
- origin;
- initial ownership.

Future ownership transfers do not modify the issuer. The issuer of an object is a permanent fact of its origin, whereas its owner may change many times, consistent with the Lifecycle Model.

---

# Ownership Independence

Ownership belongs to the current owner, not to the issuer.

Issuers do not retain implicit authority over Bitcoin Digital Objects. Being the issuer does not, by itself, grant the ability to:

- revoke ownership;
- reclaim ownership;
- transfer ownership;
- modify ownership.

Such abilities exist only where they are explicitly defined by an open specification and accepted by the owner. Absent that, ownership remains an independent concept and the issuer holds no privileged control.

---

# Authenticity

Issuers establish authenticity. Verification confirms it. Trust remains a personal decision.

Applications may choose how to represent issuer reputation, but the BDO architecture does not assign privileged status to any issuer. An object is authentic because its origin can be independently verified, not because a particular issuer asserts it.

---

# Reputation

Issuers may build reputation over time, and applications may use reputation to help users evaluate Bitcoin Digital Objects.

Reputation exists outside the ownership model and outside the verification model. It is a human and social signal, and it should never replace independent verification of authenticity.

---

# Multiple Issuers

The conceptual model permits more than one issuer for an object, provided that authenticity remains independently verifiable.

Future specifications may define collaborative issuance, such as:

- co-issued credentials;
- consortium memberships;
- multi-organization certifications.

Collaborative issuance does not weaken ownership independence: regardless of how many issuers participate, ownership after issuance still belongs to the current owner.

---

# Issuer Independence

The issuer may disappear. The company may disappear. The website may disappear.

The Bitcoin Digital Object should remain verifiable regardless. Applications should never depend on the issuer remaining online, and the authenticity established at issuance should remain independently verifiable long after the issuer is gone.

---

# Relationship with Ownership

The issuer creates the object. The owner controls the object.

These responsibilities are intentionally separate. The Ownership Model governs control; the issuer model governs origin. Neither redefines the other.

---

# Relationship with Verification

Verification confirms that a Bitcoin Digital Object originates from its claimed issuer.

Verification should remain independent from the issuer's continued existence, and a claim of issuance carries weight only insofar as it can be verified.

---

# Relationship with Metadata

Issuer information forms part of the object's metadata.

Metadata describes the issuer; it does not grant authority. As established by the Metadata Model, an issuer identity expressed in metadata is descriptive and must be confirmed through verification rather than trusted on its face.

---

# Relationship with Specifications

This RFC defines the conceptual role of issuers only.

Identity encoding, signatures, provenance, and verification mechanisms belong to interoperability specifications such as STAS-01.

A specification implements this issuer model; it does not redefine it. Multiple compatible specifications may represent the same issuer model.

---

# Design Principles

Issuers should:

- establish authenticity;
- publish verifiable information;
- remain independent from ownership;
- avoid privileged control;
- enable long-term verification.

---

# Future Work

Subsequent RFCs and specifications may define:

- issuer identity representation;
- issuance and provenance proofs;
- collaborative issuance procedures;
- issuer reputation frameworks;
- revocation semantics where explicitly permitted and owner-accepted.

These build upon the issuer model without altering it.

---

# Conclusion

An issuer gives a Bitcoin Digital Object its origin and its initial authenticity, and then steps back: it holds no ownership over what it created unless it remains the owner.

Origin is permanent and verifiable; control belongs to whoever owns the object now.

> The issuer creates the object.
>
> The owner controls the object.

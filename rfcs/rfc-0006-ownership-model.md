# RFC-0006 — Define the Bitcoin Digital Object Ownership Model

Status: Draft

Author: Supermultiverse

Created: 2026-07-17

---

# Abstract

This RFC defines the ownership model for Bitcoin Digital Objects (BDOs).

Ownership is the defining characteristic of a Bitcoin Digital Object. An object exists independently from any application, but it only becomes meaningful when ownership can be established, transferred and independently verified.

This RFC defines ownership semantics only. It intentionally avoids implementation details, which belong to interoperability specifications such as STAS-01.

---

# Motivation

Traditional digital platforms manage ownership internally.

Applications decide who owns what, and accounts become the source of truth. When the application disappears, the ownership disappears with it.

Bitcoin introduced a different model, in which ownership exists independently from any application. Bitcoin Digital Objects extend this principle to digital objects.

An ownership model that is portable, verifiable and independent of any single service is what allows a Bitcoin Digital Object to be owned by a user rather than by a platform.

---

# Ownership

Every Bitcoin Digital Object has exactly one current owner.

Ownership represents the exclusive authority to control the object.

Ownership is independent from:

- the issuer;
- the application;
- the marketplace;
- the wallet software;
- the storage provider.

Ownership continues to exist even if none of those systems remain online.

---

# Ownership Transfer

Ownership may change over time.

A transfer changes only the owner. It does not change:

- the object's identity;
- the object's history;
- the object's meaning.

Ownership evolves. Identity persists.

A transfer must be independently verifiable, so that any party can determine the current owner without trusting the party that performed the transfer.

---

# Issuance

Issuing a Bitcoin Digital Object creates its first owner.

Issuance does not grant permanent authority to the issuer. After issuance, ownership belongs exclusively to the current owner.

An issuer may publish metadata and may establish reputation, but retains no ownership authority unless the issuer remains the current owner.

The relationship between an object and the party that issued it is defined by the Issuer Model, not by continued control.

---

# Independent Verification of Ownership

Ownership must be independently verifiable.

Verification of ownership must never depend on trusting:

- the issuer;
- a marketplace;
- a wallet;
- an application;
- Supermultiverse;
- any other third party.

Ownership verification ultimately derives from Bitcoin, consistent with the Trust Model and the Verification Model. Any compatible verifier provided with the same evidence should reach the same conclusion about who owns the object.

---

# Custody versus Ownership

Ownership and custody are different concepts.

Ownership answers:

> Who owns the object?

Custody answers:

> Who currently manages the keys?

A user may delegate custody without transferring ownership, and changing custody does not by itself change ownership.

Applications may offer custodial or self-custodial experiences. The ownership model remains identical in either case.

---

# Recovery

Recovery mechanisms may vary between implementations.

Recovery is an implementation concern. It is not part of the ownership model itself.

The conceptual ownership model remains unchanged regardless of how keys are lost, rotated or recovered.

---

# Continuity

Ownership is continuous.

Applications may disappear. Wallets may disappear. Marketplaces may disappear.

Ownership survives because it is anchored to Bitcoin rather than to any individual service. A gap in the availability of any service does not create a gap in ownership.

---

# Rights

Ownership grants authority over the object.

The specific rights associated with ownership depend on the object itself. Examples include:

- access;
- membership;
- participation;
- collection;
- transfer;
- display;
- redemption.

The ownership model does not define these rights. It defines only who possesses them. What an object enables is described by the Capability Model.

---

# Ownership versus Identity

Identity answers:

> Which object is this?

Ownership answers:

> Who controls it?

The two concepts are independent. Identity persists across the lifetime of the object; ownership may change many times. A change of owner never changes identity, and a change of identity is never implied by a change of owner.

---

# Ownership versus Capability

Capabilities describe what may be done with an object.

Ownership determines who may exercise those capabilities.

Capabilities are defined independently of ownership. Ownership authorizes them; it does not define them. Transferring ownership does not, by itself, add or remove capabilities.

---

# Relationship with Trust and Verification

The Trust Model establishes that authenticity and ownership should be determined by verification rather than by trusting an intermediary.

The Verification Model establishes what can be objectively confirmed, including who currently owns an object.

The ownership model depends on both: ownership is meaningful precisely because it can be verified independently and does not require trust in any single party.

---

# Relationship with Specifications

This RFC defines ownership semantics only.

How ownership is represented, proven, serialized and exchanged is defined by interoperability specifications such as STAS-01.

A specification implements this ownership model; it does not redefine it. Multiple compatible specifications may represent the same ownership model.

---

# Design Principles

The ownership model follows several principles.

Ownership should be:

- independent;
- transferable;
- verifiable;
- persistent;
- application-agnostic;
- interoperable.

---

# Future Work

Subsequent RFCs and specifications may define:

- ownership proof representation;
- transfer verification procedures;
- custody and recovery interoperability;
- issuer interoperability;
- application-level ownership experiences.

These build upon the ownership model without altering it.

---

# Conclusion

A Bitcoin Digital Object belongs to its owner, not to the application that displays it.

Ownership is exclusive, transferable, verifiable and continuous, and it survives the disappearance of any individual service because it is anchored to Bitcoin.

> Identity tells us what the object is.
>
> Ownership tells us who controls it.

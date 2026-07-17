# RFC-0004 — Define the Bitcoin Digital Object Capability Model

Status: Accepted

Author: Supermultiverse

Created: 2026-07-15

---

# Abstract

This RFC introduces the capability model for Bitcoin Digital Objects
(BDOs).

A Bitcoin Digital Object is more than a transferable digital asset.

It may expose one or more capabilities that compatible applications can
interpret and execute.

Capabilities define what an object can do, while preserving a common,
portable identity.

---

# Motivation

Traditional digital assets usually represent ownership only.

Bitcoin Digital Objects extend this concept.

An object may represent:

- ownership;
- access rights;
- memberships;
- credentials;
- licenses;
- collectibles;
- tickets;
- game items;
- governance rights;
- or any future digital experience.

Rather than defining every possible use case, the ecosystem should define
a generic capability model that remains open and extensible.

---

# Capability Principles

Capabilities are properties of a Bitcoin Digital Object.

A capability:

- extends the usefulness of an object;
- is independent from ownership;
- is interpreted by compatible applications;
- may evolve without changing the object's identity.

Capabilities are optional.

Objects remain valid even if an application does not recognize every
capability they expose.

---

# Identity versus Capability

Identity answers:

> "What object is this?"

Capability answers:

> "What can this object do?"

Identity is permanent.

Capabilities may evolve.

---

# Ownership versus Capability

Ownership determines who controls an object.

Capabilities determine what that object enables.

Ownership transfer does not necessarily modify capabilities.

Capabilities remain attached to the object itself.

---

# Capability Discovery

Compatible applications should be able to determine which capabilities an
object exposes.

Capability discovery should be:

- deterministic;
- verifiable;
- implementation independent;
- extensible.

Applications may ignore capabilities they do not understand while still
preserving interoperability.

---

# Extensibility

The capability model is intentionally open.

New capabilities may be introduced over time without affecting existing
objects.

Applications are free to innovate by supporting additional capabilities.

This enables ecosystem growth without requiring protocol redesign.

---

# Examples

A Bitcoin Digital Object may expose capabilities such as:

- Collection Item
- Membership
- Event Ticket
- Achievement
- Access Pass
- License
- Game Asset
- Governance Token

These examples are illustrative only.

The capability model is not limited to predefined categories.

---

# Architectural Impact

This RFC introduces no changes to:

- proof format;
- serialization;
- ownership model;
- metadata format;
- verification;
- APIs.

It defines only the conceptual capability layer.

Future RFCs may specify how capabilities are represented within STAS-01.

---

# Future Work

Subsequent RFCs may define:

- capability serialization;
- capability negotiation;
- capability registries;
- application interoperability;
- capability versioning.

---

# Conclusion

Identity defines what a Bitcoin Digital Object is.

Ownership defines who controls it.

Capabilities define what it enables.

Separating these concerns creates a flexible, extensible and
implementation-independent architecture that allows innovation without
fragmenting interoperability.

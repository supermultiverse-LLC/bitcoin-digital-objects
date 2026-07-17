# RFC-0003 — Define the Bitcoin Digital Object Identity Model

Status: Accepted

Author: Supermultiverse

Created: 2026-07-15

---

# Abstract

This RFC defines the identity model for Bitcoin Digital Objects (BDOs).

The objective is to distinguish the permanent identity of a Bitcoin Digital
Object from its mutable properties.

Identity must remain stable regardless of ownership changes, metadata
updates or application-specific representations.

---

# Motivation

Digital ownership only makes sense if an object can preserve its identity
over time.

Ownership may change.

Metadata may evolve.

Capabilities may be extended.

Applications may disappear.

The object itself must remain the same.

This RFC establishes that principle.

---

# Identity Principles

A Bitcoin Digital Object has one identity.

That identity is:

- globally unique;
- persistent;
- independently verifiable;
- application independent.

Identity is not defined by a wallet.

Identity is not defined by an application.

Identity is not defined by an issuer.

Identity belongs to the object itself.

---

# Identity versus State

Identity and state are different concepts.

Identity answers:

> "What object is this?"

State answers:

> "What is true about this object right now?"

State may change.

Identity must not.

---

# Identity versus Ownership

Ownership is dynamic.

Identity is permanent.

The owner of a Bitcoin Digital Object may change many times during its
lifetime.

The identity never changes.

---

# Identity versus Metadata

Metadata describes an object.

Identity defines the object.

Metadata may evolve.

Identity remains constant.

Applications should never rely on metadata to establish identity.

---

# Identity Requirements

An identity should satisfy the following properties.

- Unique
- Persistent
- Portable
- Verifiable
- Independent
- Stable

Any compatible specification representing Bitcoin Digital Objects should
preserve these properties.

---

# Architectural Impact

This RFC introduces no changes to:

- proof format;
- serialization;
- metadata;
- APIs;
- verification;
- ownership model.

It defines only the conceptual identity layer.

Future RFCs may define how specifications represent that identity.

---

# Future Work

Subsequent RFCs may define:

- identity serialization;
- issuer identifiers;
- metadata evolution;
- capability negotiation;
- object relationships.

---

# Conclusion

A Bitcoin Digital Object is not defined by its owner.

It is not defined by its metadata.

It is not defined by the application that displays it.

A Bitcoin Digital Object is defined by its identity.

Everything else may evolve.

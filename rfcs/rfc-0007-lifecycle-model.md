# RFC-0007 — Define the Bitcoin Digital Object Lifecycle Model

Status: Accepted

Author: Supermultiverse

Created: 2026-07-17

---

# Abstract

This RFC defines the lifecycle model for Bitcoin Digital Objects (BDOs).

A Bitcoin Digital Object exists throughout a lifecycle. Ownership changes, capabilities evolve, and applications appear and disappear, yet the object itself persists.

This RFC defines the conceptual lifecycle shared by every Bitcoin Digital Object. It defines lifecycle semantics only and intentionally avoids implementation details, which belong to interoperability specifications such as STAS-01.

---

# Motivation

A Bitcoin Digital Object is not static. Like any object, it has a lifecycle.

That lifecycle does not describe the object's identity, which remains constant. Instead, it describes how the object evolves over time while preserving continuity.

A shared lifecycle model is what allows independent applications to agree on how an object may change without ever losing the guarantee that it remains the same object.

---

# Lifecycle Overview

Every Bitcoin Digital Object progresses through a series of conceptual phases.

```text
Creation
      │
      ▼
Ownership
      │
      ▼
Transfer
      │
      ▼
Evolution
      │
      ▼
Long-Term Preservation
```

These phases are conceptual rather than technical. Implementations may represent, order, or expose them differently, but the conceptual lifecycle remains the same.

The phases are not strictly sequential: after creation, an object may alternate between ownership, transfer, and evolution many times, while long-term preservation applies throughout.

---

# Creation

Every Bitcoin Digital Object begins with a creation event.

Creation establishes:

- the object's identity;
- its initial owner;
- its origin.

Creation occurs exactly once. A Bitcoin Digital Object can never be created twice, and its identity, once established at creation, is never reassigned.

---

# Ownership

After creation, a Bitcoin Digital Object remains under the control of its current owner.

Ownership may persist for any duration. Ownership itself does not modify identity.

The ownership phase is governed by the Ownership Model. Within the lifecycle, ownership is the ordinary resting state of an object between transfers.

---

# Transfer

Ownership may be transferred.

A transfer changes only the owner. It does not change:

- identity;
- authenticity;
- continuity.

Every valid transfer preserves the same Bitcoin Digital Object. A transfer is an event within the lifecycle, and each transfer must be independently verifiable so that continuity across owners can be demonstrated.

---

# Evolution

A Bitcoin Digital Object may evolve throughout its lifetime.

Examples include:

- metadata updates;
- capability expansion;
- compatibility with new applications;
- new user experiences.

Evolution extends the object. It does not replace it. No act of evolution may alter the object's identity or break its continuity; an evolution that would do so produces a different object, not an evolved one.

---

# Long-Term Preservation

A Bitcoin Digital Object should remain usable long after its original application disappears.

Long-term preservation is one of the primary goals of the BDO architecture. Applications are temporary; objects are intended to persist.

Preservation applies across the entire lifecycle rather than only at its end, and it depends on the object remaining independently verifiable at any point in the future.

---

# Continuity

Continuity connects every phase of the lifecycle.

Regardless of how many times ownership changes, capabilities evolve, or applications interpret the object differently, it remains the same Bitcoin Digital Object.

Without continuity there is no lifecycle, only disconnected objects. Continuity is therefore the property that makes the lifecycle a single object's history rather than a sequence of unrelated states.

---

# Lifecycle Independence

The lifecycle is independent from:

- wallets;
- applications;
- marketplaces;
- custodians;
- issuers.

Implementations may expose different workflows, but the conceptual lifecycle remains identical. The disappearance of any of these systems does not end the lifecycle of the object.

---

# Relationship with Identity

Identity establishes the object at creation.

The lifecycle preserves that identity through time. Every phase — ownership, transfer, evolution, preservation — operates on the same identity and never redefines it.

---

# Relationship with Ownership

Ownership changes are events within the lifecycle.

Ownership itself does not define the lifecycle. The Ownership Model defines who controls the object; the lifecycle model places ownership and its transfers within the object's continuous history.

---

# Relationship with Capabilities

Capabilities may evolve during the lifecycle.

Their evolution must never compromise identity continuity. A capability may be added or extended as part of evolution, but doing so extends the same object rather than creating a new one.

---

# Relationship with Verification

Verification allows every stage of the lifecycle to be independently confirmed.

Without verification, lifecycle continuity cannot be demonstrated. Creation, transfer, and evolution are meaningful across independent parties precisely because each can be verified without trusting the party that performed it.

---

# Relationship with Specifications

This RFC defines the conceptual lifecycle only.

How lifecycle events are represented, proven, serialized, and exchanged belongs to interoperability specifications such as STAS-01.

A specification implements this lifecycle model; it does not redefine it. Multiple compatible specifications may represent the same lifecycle.

---

# Design Principles

The lifecycle model should guarantee:

- continuity;
- permanence;
- portability;
- verifiability;
- implementation independence.

---

# Future Work

Subsequent RFCs and specifications may define:

- lifecycle event representation;
- transfer and evolution verification procedures;
- preservation and archival interoperability;
- history and provenance representation.

These build upon the lifecycle model without altering it.

---

# Conclusion

A Bitcoin Digital Object moves through creation, ownership, transfer, evolution, and long-term preservation, and remains the same object throughout.

Everything about the object may change except the one thing that makes the lifecycle coherent: its identity.

> A Bitcoin Digital Object evolves through time.
>
> Its identity does not.

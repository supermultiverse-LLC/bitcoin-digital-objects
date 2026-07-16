# AP-006 — BDO Lifecycle Model

**Status:** Draft v1.0

---

# Abstract

A Bitcoin Digital Object (BDO) exists throughout a lifecycle.

Ownership changes.

Capabilities evolve.

Applications appear and disappear.

The object itself persists.

This document defines the conceptual lifecycle shared by every Bitcoin Digital Object independently from any implementation or interoperability specification.

---

# Introduction

A Bitcoin Digital Object is not static.

Like any object, it has a lifecycle.

That lifecycle does not describe the object's identity.

Identity remains constant.

Instead, the lifecycle describes how the object evolves over time while preserving continuity.

---

# Lifecycle Overview

Every Bitcoin Digital Object progresses through a series of conceptual phases.

```
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

These phases are conceptual rather than technical.

Implementations may represent them differently.

---

# Creation

Every Bitcoin Digital Object begins with a creation event.

Creation establishes:

- the object's identity
- its initial owner
- its origin

Creation occurs exactly once.

A BDO can never be created twice.

---

# Ownership

After creation, a Bitcoin Digital Object remains under the control of its current owner.

Ownership may persist for any duration.

Ownership itself does not modify identity.

---

# Transfer

Ownership may be transferred.

Transfer changes only the owner.

Transfer does not change:

- identity
- authenticity
- continuity

Every valid transfer preserves the same Bitcoin Digital Object.

---

# Evolution

A Bitcoin Digital Object may evolve throughout its lifetime.

Examples include:

- metadata updates
- capability expansion
- compatibility with new applications
- new user experiences

Evolution extends the object.

It does not replace it.

---

# Long-Term Preservation

A Bitcoin Digital Object should remain usable long after its original application disappears.

Long-term preservation is one of the primary goals of the BDO architecture.

Applications are temporary.

Objects are intended to persist.

---

# Continuity

Continuity connects every phase of the lifecycle.

Regardless of how many times ownership changes, capabilities evolve or applications interpret the object differently, it remains the same Bitcoin Digital Object.

Without continuity there is no lifecycle.

Only disconnected objects.

---

# Lifecycle Independence

The lifecycle is independent from:

- wallets
- applications
- marketplaces
- custodians
- issuers

Implementations may expose different workflows.

The conceptual lifecycle remains identical.

---

# Relationship with Identity

Identity establishes the object.

The lifecycle preserves that identity through time.

---

# Relationship with Ownership

Ownership changes are events within the lifecycle.

Ownership itself does not define the lifecycle.

---

# Relationship with Capabilities

Capabilities may evolve during the lifecycle.

Their evolution must never compromise identity continuity.

---

# Relationship with Verification

Verification allows every stage of the lifecycle to be independently confirmed.

Without verification, lifecycle continuity cannot be demonstrated.

---

# Relationship with Specifications

This document intentionally avoids implementation details.

Lifecycle events, serialization and protocol behavior belong to interoperability specifications such as STAS-01.

This document defines only the conceptual lifecycle model.

---

# Design Principles

The lifecycle model should guarantee:

- continuity
- permanence
- portability
- verifiability
- implementation independence

---

# Guiding Principle

> A Bitcoin Digital Object evolves through time.

> Its identity does not.
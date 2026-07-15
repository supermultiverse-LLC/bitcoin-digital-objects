# BDO Identity Model

**Status:** Draft v1.0

---

# Abstract

A Bitcoin Digital Object (BDO) is defined by its identity.

Ownership may change.

Metadata may evolve.

Applications may appear and disappear.

Representations may vary.

Yet the object remains the same.

This document defines the conceptual identity model shared by every Bitcoin Digital Object, independently of any implementation, application or interoperability specification.

---

# Identity First

Identity is the foundation of every Bitcoin Digital Object.

A BDO is not defined by:

- where it is stored
- which application created it
- who currently owns it
- how it is displayed
- which protocol represents it

A BDO is defined only by its canonical identity.

Everything else may evolve.

---

# Canonical Identity

Every Bitcoin Digital Object possesses exactly one canonical identity.

That identity uniquely distinguishes the object from every other BDO.

A canonical identity never changes during the lifetime of the object.

It exists independently from software, applications and organizations.

Compatible implementations should always refer to the same underlying identity.

---

# Identity and State

Identity and state describe different aspects of a BDO.

Identity answers one question:

> **Which object is this?**

State answers another:

> **What is true about this object right now?**

State may evolve continuously.

Identity does not.

---

# Identity and Ownership

Ownership is a property of a Bitcoin Digital Object.

Ownership is not its identity.

The same BDO may be transferred between different owners throughout its lifetime.

Every transfer changes ownership.

No transfer creates a new object.

---

# Identity and Metadata

Metadata describes a BDO.

Metadata does not define a BDO.

Names, descriptions, images and external references may evolve without affecting identity.

Applications should therefore distinguish between:

- canonical identity
- mutable metadata

This separation allows objects to evolve while preserving continuity.

---

# Identity and Representation

A single Bitcoin Digital Object may have multiple representations.

Examples include:

- wallets
- web applications
- NFC cards
- QR codes
- printed certificates
- augmented reality experiences

These representations are interfaces.

They are not the object itself.

Different representations should always resolve to the same canonical identity.

---

# Identity and Capabilities

Capabilities describe what a Bitcoin Digital Object can do.

Examples include:

- granting access
- representing membership
- unlocking rewards
- authorizing actions
- representing collectibles

Capabilities may change over time.

Identity remains constant.

---

# Continuity

The defining property of a Bitcoin Digital Object is continuity.

Every valid operation performed on a BDO must preserve its identity.

Ownership may change.

Metadata may change.

Capabilities may change.

Representations may change.

Applications may change.

The object remains the same.

Continuity allows users and applications to reason about a BDO as one persistent digital object throughout its lifecycle.

---

# Identity Independence

The identity of a Bitcoin Digital Object is independent from any particular implementation.

This document intentionally does not define:

- serialization
- transport
- storage
- interoperability mechanisms

Those responsibilities belong to interoperability specifications such as STAS-01.

The purpose of this document is solely to define the conceptual identity shared by every Bitcoin Digital Object.

---

# Design Goals

The identity model is designed to guarantee:

- uniqueness
- continuity
- portability
- interoperability
- independent verification
- long-term stability

These properties ensure that Bitcoin Digital Objects can outlive individual applications, platforms and companies.

---

# Guiding Principle

> A Bitcoin Digital Object is not defined by where it exists.

> It is defined by who it is.
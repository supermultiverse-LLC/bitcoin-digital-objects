# AP-007 — BDO Metadata Model

**Status:** Draft v1.0

---

# Abstract

Every Bitcoin Digital Object (BDO) carries information about itself.

This information is called metadata.

Metadata allows applications to understand, display and interpret a Bitcoin Digital Object without changing its identity or ownership.

This document defines the conceptual metadata model shared by all Bitcoin Digital Objects.

It intentionally avoids implementation details.

---

# Introduction

A Bitcoin Digital Object consists of more than ownership.

Applications also need descriptive information.

Examples include:

- a name
- an image
- a description
- an issuer
- capabilities
- application-specific attributes

This information forms the object's metadata.

Metadata provides context.

It does not define ownership.

---

# Purpose of Metadata

Metadata exists to describe a Bitcoin Digital Object.

It allows compatible applications to present meaningful experiences to users.

Metadata should never become the source of truth for ownership.

Ownership remains anchored to Bitcoin.

---

# Identity and Metadata

Identity and metadata are different concepts.

Identity answers:

> Which object is this?

Metadata answers:

> What do we know about this object?

Changing metadata does not necessarily create a new Bitcoin Digital Object.

Identity persists independently from metadata.

---

# Ownership and Metadata

Ownership determines who controls the object.

Metadata describes the object.

These responsibilities remain independent.

Applications must never infer ownership solely from metadata.

---

# Metadata Categories

Metadata may include information such as:

### Visual

- name
- description
- image
- animation
- media

---

### Informational

- issuer
- collection
- creation date
- language
- version

---

### Functional

- supported capabilities
- application hints
- interaction requirements

---

### Domain-Specific

Applications may introduce additional metadata relevant to their domain.

Examples include:

- player statistics
- ticket information
- event schedules
- memberships
- credentials

These extensions should remain compatible with the underlying object.

---

# Extensibility

The metadata model is intentionally extensible.

New metadata fields may appear over time.

Applications should ignore unknown fields whenever possible.

This allows the ecosystem to evolve without breaking compatibility.

---

# Interpretation

Different applications may interpret the same metadata differently.

One application may display an image.

Another may focus on capabilities.

Another may ignore certain fields entirely.

Metadata provides information.

Applications decide how to present it.

---

# Persistence

Metadata may evolve.

Descriptions may improve.

Media may change.

Capabilities may expand.

Identity remains unchanged.

Metadata evolution should preserve continuity.

---

# Relationship with Specifications

This document defines the conceptual role of metadata.

Serialization, encoding and transport belong to interoperability specifications such as STAS-01.

---

# Design Principles

Metadata should be:

- descriptive
- extensible
- interoperable
- application-independent
- identity-preserving

---

# Guiding Principle

> Metadata describes the object.

> It never defines ownership.
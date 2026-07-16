# AP-010 — BDO Interoperability Model

**Status:** Draft v1.0

---

# Abstract

Bitcoin Digital Objects (BDOs) are designed to move freely across compatible applications.

Interoperability allows different software systems to recognize, verify and interact with the same Bitcoin Digital Object without requiring permission from its creator.

This document defines the conceptual interoperability model for Bitcoin Digital Objects.

It intentionally avoids implementation details.

---

# Introduction

Interoperability is one of the defining characteristics of Bitcoin Digital Objects.

Without interoperability, ownership becomes tied to individual applications.

With interoperability, ownership belongs to users.

Applications become interchangeable.

---

# Purpose

The purpose of interoperability is to ensure that Bitcoin Digital Objects remain usable across multiple compatible implementations.

Interoperability allows innovation without fragmenting ownership.

---

# Shared Understanding

Compatible applications should agree on the meaning of a Bitcoin Digital Object.

Applications may differ in design, features and user experience.

They should not disagree about:

- identity
- ownership
- authenticity
- continuity

These concepts must remain consistent across the ecosystem.

---

# Compatible Implementations

Different implementations may provide different capabilities.

Examples include:

- wallets
- games
- marketplaces
- ticketing systems
- identity platforms
- enterprise software

Each implementation remains free to innovate while preserving compatibility.

---

# Graceful Degradation

Applications should never fail simply because they encounter information they do not understand.

Unknown capabilities.

Unknown metadata.

Unknown extensions.

These should be ignored rather than rejected whenever possible.

This allows the ecosystem to evolve without breaking compatibility.

---

# Open Specifications

Interoperability depends on open specifications.

Specifications should remain:

- publicly documented
- implementation-independent
- extensible
- versionable

No implementation should require proprietary behavior in order to remain compatible.

---

# Forward Compatibility

Future versions of the ecosystem should remain compatible whenever reasonably possible.

Applications should be encouraged to understand new concepts without breaking existing objects.

Evolution should preserve continuity.

---

# Backward Compatibility

Existing Bitcoin Digital Objects should remain usable as the ecosystem evolves.

New applications should continue to recognize previously issued objects whenever technically possible.

---

# Independence

Interoperability should remain independent from:

- companies
- applications
- hosting providers
- marketplaces
- wallets

Compatibility belongs to the ecosystem.

Not to individual implementations.

---

# Relationship with STAS-01

STAS-01 defines the technical mechanisms that enable interoperability.

This document defines the conceptual goals those mechanisms should achieve.

---

# Design Principles

Interoperability should be:

- open
- deterministic
- extensible
- implementation-independent
- backward-compatible
- forward-compatible

---

# Guiding Principle

> Ownership should move freely.

> Compatibility should make that possible.
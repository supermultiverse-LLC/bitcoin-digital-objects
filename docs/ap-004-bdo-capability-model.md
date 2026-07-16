# AP-004 — BDO Capability Model

**Status:** Draft v1.0

---

# Abstract

A Bitcoin Digital Object (BDO) is more than something that can be owned.

It can also express capabilities.

Capabilities define what compatible applications may allow an owner to do with a BDO.

Capabilities do not define the object's identity.

They define how applications interpret the object.

This document introduces the conceptual capability model for Bitcoin Digital Objects.

---

# Introduction

Ownership answers one question:

> Who controls this object?

Capabilities answer another:

> What can this object do?

Separating ownership from capabilities allows Bitcoin Digital Objects to remain stable while continuously gaining new functionality.

---

# What is a Capability?

A capability represents a possible interaction between a Bitcoin Digital Object and a compatible application.

Examples include:

- granting access
- proving membership
- unlocking content
- enabling participation
- representing collectibles
- authorizing actions
- providing rewards
- proving achievements

Capabilities describe behavior.

They do not define identity.

---

# Identity and Capabilities

Identity is permanent.

Capabilities may evolve.

Adding a new capability never creates a new Bitcoin Digital Object.

Removing a capability never changes the object's identity.

Applications should therefore treat identity and capabilities as independent concepts.

---

# Ownership and Capabilities

Ownership determines who may exercise a capability.

Capabilities determine what the owner may do.

These concepts complement each other.

Neither replaces the other.

---

# Capability Interpretation

Capabilities are interpreted by applications.

Different applications may interpret the same capability differently.

For example:

A football club may interpret a BDO as:

- stadium access
- premium membership
- voting rights

A game may interpret the same BDO as:

- playable character
- exclusive tournament access
- cosmetic item

The identity remains unchanged.

Only the interpretation differs.

---

# Capability Evolution

Capabilities may evolve throughout the lifetime of a Bitcoin Digital Object.

Examples include:

- enabling new experiences
- removing obsolete features
- introducing seasonal functionality
- supporting additional applications

Capability evolution should never affect identity continuity.

---

# Capability Composition

A Bitcoin Digital Object may expose multiple capabilities simultaneously.

For example:

- membership
- access
- collectible
- credential
- reward

Capabilities are composable.

Applications may combine them to create richer experiences.

---

# Capability Discovery

Applications should be able to determine which capabilities they support.

Unsupported capabilities should simply be ignored.

This allows Bitcoin Digital Objects to remain compatible across a diverse ecosystem without requiring every application to implement every capability.

---

# Capability Independence

Capabilities are independent from:

- wallets
- marketplaces
- issuers
- applications
- custody models

Applications interpret capabilities.

They do not own them.

---

# Capability Categories

Capabilities may generally fall into categories such as:

- Access
- Identity
- Membership
- Governance
- Rewards
- Credentials
- Collectibles
- Commerce
- Gaming
- Social

These categories are descriptive rather than normative.

Future specifications may define additional capability types.

---

# Relationship with Specifications

This document intentionally does not define capability encoding or serialization.

Those responsibilities belong to interoperability specifications such as STAS-01.

This document defines only the conceptual capability model.

---

# Design Principles

The capability model follows several principles.

Capabilities should be:

- composable
- interoperable
- extensible
- application-independent
- identity-preserving

---

# Guiding Principle

> Identity defines what a Bitcoin Digital Object is.

> Capabilities define what compatible applications can do with it.
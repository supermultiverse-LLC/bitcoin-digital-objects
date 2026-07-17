# RFC-0001 — Alignment of STAS-01 with the Bitcoin Digital Objects Architecture

Status: Superseded by RFC-0002

---

> **Note:** This RFC has been superseded by [RFC-0002 — Align STAS-01 with the Bitcoin Digital Objects Architecture](./rfc-0002-stas-alignment.md), which formally establishes the same alignment with complete document metadata. RFC-0001 is retained for historical context.

---

# Abstract

The Bitcoin Digital Objects (BDO) architecture introduces a conceptual model that clearly separates digital ownership concepts from technical interoperability mechanisms.

This RFC aligns STAS-01 with that architecture.

No technical behavior is modified.

No compatibility is broken.

The purpose of this RFC is to clarify responsibilities and establish a stable long-term governance model for the ecosystem.

---

# Motivation

STAS-01 was originally developed as an open interoperability standard for Bitcoin-native digital assets.

As the ecosystem evolved, a broader conceptual model emerged:

Bitcoin Digital Objects (BDOs).

BDOs define:

- what a digital object is
- identity
- ownership
- verification
- capabilities
- lifecycle
- metadata
- issuers
- applications

These concepts belong to the conceptual architecture.

STAS-01 should not redefine them.

Its responsibility is different.

---

# Responsibility Separation

The ecosystem is intentionally divided into independent layers.
FOUNDATION

Bitcoin
Taproot Assets

↓

INTEROPERABILITY

STAS-01

↓

CONCEPTUAL MODEL

Bitcoin Digital Objects

↓

APPLICATIONS

Wallets
Games
Communities
Commerce
Identity
Future Applications

Each layer has a distinct responsibility.

---

# Responsibilities of BDO

The Bitcoin Digital Objects repository defines:

- conceptual architecture
- ownership semantics
- identity model
- capability model
- lifecycle model
- metadata model
- issuer model
- application model
- design principles

BDO intentionally avoids implementation details.

---

# Responsibilities of STAS-01

STAS-01 defines how compatible implementations exchange and interpret Bitcoin Digital Objects.

Its responsibilities include:

- serialization
- interoperability
- compatibility
- versioning
- extensibility
- verification mechanisms

STAS-01 intentionally does not define ownership semantics.

---

# What Moves to BDO

The following concepts should be considered part of the BDO architecture rather than STAS-01.

- definition of a Bitcoin Digital Object
- ownership concepts
- identity concepts
- lifecycle semantics
- capability semantics
- application philosophy
- ecosystem principles

Future documentation should reference the BDO repository instead of redefining these concepts.

---

# What Remains in STAS-01

STAS-01 remains responsible for:

- normative requirements
- data structures
- serialization
- protocol rules
- compatibility
- interoperability
- extension mechanisms

This RFC intentionally introduces no technical changes.

---

# Repository Relationship

The repositories complement each other.
bitcoin-digital-objects

↓

Defines concepts

↓

stas-standard

↓

Defines interoperability

↓

Reference Implementations

↓

Applications

Neither repository replaces the other.

Each solves a different problem.

---

# Compatibility

This RFC introduces no breaking changes.

Existing STAS-01 implementations remain fully compatible.

Only documentation, terminology and repository responsibilities are clarified.

---

# Migration Strategy

Alignment should happen incrementally.

Recommended order:

1. Update README.
2. Update architecture documentation.
3. Update terminology.
4. Replace duplicated conceptual explanations with references to BDO Architecture.
5. Preserve normative behavior.

---

# Long-Term Vision

The Bitcoin Digital Objects repository becomes the conceptual source of truth.

STAS-01 becomes the technical interoperability specification implementing that architecture.

This separation allows both repositories to evolve independently while remaining fully aligned.

---

# Guiding Principle

> Bitcoin Digital Objects define the concepts.

> STAS-01 defines how compatible systems implement them.

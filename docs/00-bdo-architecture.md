# 00 — BDO Architecture

**Status:** Draft v1.0

---

# Overview

Bitcoin Digital Objects (BDOs) are built as an open architecture composed of independent layers.

Each layer has a single responsibility.

Each higher layer builds upon the layers below it without replacing them.

This separation allows the ecosystem to evolve while preserving interoperability, portability and long-term ownership.

---

# Architectural Stack

```
APPLICATIONS
──────────────────────────────────────────────

Wallets
Games
Communities
Marketplaces
Ticketing
Commerce
Identity
AI
Future Applications

──────────────────────────────────────────────

OWNERSHIP MODEL

Bitcoin Digital Objects
Identity
Ownership
Verification
Capabilities
Lifecycle

──────────────────────────────────────────────

OPEN STANDARD

STAS-01

──────────────────────────────────────────────

FOUNDATION

Taproot Assets
Bitcoin
```

---

# Layer Responsibilities

## Foundation

The Foundation provides the technical infrastructure upon which the entire ecosystem is built.

### Bitcoin

Provides:

- security
- consensus
- decentralization
- immutable settlement

Bitcoin is the ultimate source of ownership.

---

### Taproot Assets

Provides Bitcoin-native digital asset primitives.

Taproot Assets enable digital assets to inherit Bitcoin's security while remaining independent from application logic.

---

## Open Standard

### STAS-01

STAS-01 defines how compatible implementations represent and exchange Bitcoin Digital Objects.

It is responsible for:

- interoperability
- serialization
- verification mechanisms
- compatibility between implementations

STAS-01 does **not** define what a Bitcoin Digital Object is.

It defines how compatible systems communicate.

---

## Conceptual Model

The conceptual model defines the shared language of the ecosystem.

It explains the meaning of Bitcoin Digital Objects independently from any implementation.

The conceptual model consists of six documents.

### AP-001

What is a Bitcoin Digital Object?

Defines the category itself.

---

### AP-002

Identity Model

Defines what makes a Bitcoin Digital Object remain the same object throughout its lifetime.

---

### AP-003

Ownership Model

Defines who controls a Bitcoin Digital Object.

---

### AP-004

Capability Model

Defines how applications interpret and interact with Bitcoin Digital Objects.

---

### AP-005

Verification Model

Defines how ownership, identity and authenticity are independently verified.

---

### AP-006

Lifecycle Model

Defines how Bitcoin Digital Objects evolve while preserving continuity.

---

## Applications

Applications create user experiences.

Applications may include:

- wallets
- games
- communities
- ticketing systems
- marketplaces
- commerce platforms
- enterprise software
- AI systems

Applications interpret Bitcoin Digital Objects.

They do not define them.

---

# Design Philosophy

The architecture follows several core principles.

- Build on Bitcoin.
- Keep standards open.
- Separate concepts from implementations.
- Separate ownership from experiences.
- Verification replaces trust.
- Applications compete through user experience.
- Ownership outlives applications.

---

# Repository Architecture

The ecosystem is intentionally divided into independent repositories.

```
bitcoin-digital-objects
        │
        ├── Conceptual architecture
        │
        ▼
stas-standard
        │
        ├── Open interoperability specification
        │
        ▼
Reference Implementations
        │
        ├── Supermultiverse
        ├── BTCPay Server Plugin
        └── Future compatible implementations
```

Each repository has a different responsibility.

### bitcoin-digital-objects

Defines the conceptual architecture.

No implementation details.

---

### stas-standard

Defines the open interoperability specification.

No application-specific behavior.

---

### Reference Implementations

Demonstrate how Bitcoin Digital Objects can be implemented in real-world applications.

Implementations may vary while remaining fully compatible with the open standard.

---

# Evolution

Each layer may evolve independently.

Applications may evolve without changing the conceptual model.

The Ownership model may evolve without modifying Bitcoin.

New interoperability specifications may emerge.

New implementations may appear.

The architecture is designed for long-term evolution.

---

# Guiding Principle

> Bitcoin secures ownership.

> Open standards enable interoperability.

> Bitcoin Digital Objects define ownership.

> Applications create experiences.
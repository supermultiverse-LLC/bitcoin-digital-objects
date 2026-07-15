![Status](https://img.shields.io/badge/status-working%20draft-blue)

![License](https://img.shields.io/badge/license-CC0-green)

![Open](https://img.shields.io/badge/open-standard-orange)

# Bitcoin Digital Objects (BDOs)

**An open category for digital ownership secured by Bitcoin.**

---

## What is a Bitcoin Digital Object?

A **Bitcoin Digital Object (BDO)** is a digital object whose ownership is secured by Bitcoin.

Unlike traditional digital files, a BDO can be:

- **Owned**
- **Verified**
- **Carried** across compatible applications

Ownership belongs to the user—not to any application, marketplace or platform.

Bitcoin Digital Objects are an open category.

No single company owns them.

No single platform controls them.

---

# Why BDOs?

The internet made it possible to create and share digital things.

Bitcoin made it possible to own digital things.

Bitcoin Digital Objects make that ownership useful.

The goal is simple:

> Build an open ecosystem where digital ownership is portable, verifiable and interoperable.

---

# Core Properties

Every Bitcoin Digital Object is designed around three fundamental properties.

## Own

Ownership belongs to the user.

Applications may facilitate ownership, but they never own the object.

---

## Verify

Authenticity can be independently verified.

Verification should never depend on trusting a platform.

---

## Carry

Ownership travels with the user.

A compatible application should be able to recognize and interpret the same BDO without requiring permission from its creator.

---

# Architecture

The BDO ecosystem is intentionally layered.

```
                 Bitcoin Digital Objects
                         │
        ┌────────────────┼────────────────┐
        │                │                │
 Applications        STAS-01      Future Specifications
        │                │
        └────────────────┘
                 │
          Taproot Assets
                 │
              Bitcoin
```

Each layer has a distinct responsibility.

| Layer | Responsibility |
|--------|----------------|
| Bitcoin | Security and consensus |
| Taproot Assets | Bitcoin-native digital asset primitives |
| STAS-01 | Open interoperability specification |
| Bitcoin Digital Objects | Open ownership category |
| Applications | User experiences |

---

# Design Principles

Bitcoin Digital Objects follow a few simple principles.

- Ownership should outlive applications.
- Verification should not require trust.
- Objects should remain portable.
- Standards should remain open.
- Applications should compete through experiences, not through lock-in.

---

# Repository

This repository is the canonical home of the Bitcoin Digital Object (BDO) architecture.

It defines the conceptual foundations of the category independently from any specific implementation or company.

## Documentation

- BDO Architecture
- BDO Identity Model
- BDO Ownership Model
- BDO Capability Model
- BDO Trust Model

Additional documents will be added as the architecture evolves.

---

# Relationship with STAS-01

Bitcoin Digital Objects (BDOs) are **not** a protocol.

They are an open conceptual category.

**STAS-01** is the first open interoperability specification designed to represent Bitcoin Digital Objects on Bitcoin-native infrastructure.

Future specifications may also define compatible BDO implementations.

---

# Ecosystem

Bitcoin Digital Objects are implementation-independent.

Current reference projects include:

- **STAS-01** — First open interoperability specification
- **Supermultiverse** — First reference implementation
- **BTCPay Server Plugin** — First reference integration

Future implementations are encouraged.

---

# Contributing

Bitcoin Digital Objects are an open initiative.

Contributions, discussions and compatible implementations are welcome.

The category will evolve through open discussion and practical implementations.

---

# Guiding Principle

> Applications are temporary.
>
> Ownership is not.

---

# Vision

> The internet let us create digital things.
>
> Bitcoin lets us own them.
>
> Bitcoin Digital Objects make that ownership portable.
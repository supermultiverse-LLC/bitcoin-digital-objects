![Status](https://img.shields.io/badge/status-working%20draft-blue)

![License](https://img.shields.io/badge/license-CC0-green)

![Open](https://img.shields.io/badge/open-standard-orange)

# Bitcoin Digital Objects (BDOs)

**An open category for Bitcoin-native digital ownership.**

Bitcoin Digital Objects (BDOs) define a simple idea:

> Digital things should be ownable.

A Bitcoin Digital Object (BDO) is a digital object whose ownership is secured by Bitcoin and can be independently verified, transferred and interpreted across compatible applications.

BDOs are an open category.

No single company owns them.

No single platform controls them.

---

# Vision

The internet made it possible to create digital things.

Bitcoin made it possible to own digital things.

Bitcoin Digital Objects make that ownership useful.

The goal is simple:

Build an open ecosystem where digital ownership is portable, verifiable and interoperable.

---

# Architecture

The BDO ecosystem is intentionally layered.

```
Applications
        ↑
Bitcoin Digital Objects (Category)
        ↑
STAS-01 (Open Specification)
        ↑
Taproot Assets
        ↑
Bitcoin
```

Each layer has a different responsibility.

| Layer | Responsibility |
|-------|----------------|
| Bitcoin | Security and consensus |
| Taproot Assets | Bitcoin-native digital asset primitives |
| STAS-01 | Open interoperability specification |
| Bitcoin Digital Objects | Shared ownership category |
| Applications | User experiences |

---

# Design Principles

Bitcoin Digital Objects follow a few fundamental principles.

- Ownership should outlive applications.
- Verification should not require trust.
- Objects should be portable.
- Standards should be open.
- Applications should compete through experiences, not lock-in.

---

# Repository

This repository contains the conceptual architecture of Bitcoin Digital Objects.

It is intentionally independent from any particular implementation or company.

## Documentation

- BDO Architecture
- BDO Identity Model
- BDO Ownership Model
- BDO Capability Model
- BDO Trust Model

---

# Relationship with STAS-01

BDOs are **not** a protocol.

BDOs are an open category.

STAS-01 is the first open specification designed to represent Bitcoin Digital Objects on Bitcoin-native infrastructure.

Future specifications may also define compatible BDO implementations.

---

# Ecosystem

The Bitcoin Digital Objects ecosystem currently includes:

- STAS-01 — Open interoperability specification
- Supermultiverse — Reference implementation
- BTCPay Server Plugin — Reference integration

---

# Contributing

Bitcoin Digital Objects are an open initiative.

Contributions, discussions and alternative implementations are welcome.

---

# Guiding Principle

> Applications may disappear.
>
> Ownership should not.
![Status](https://img.shields.io/badge/status-working%20draft-blue)

![License](https://img.shields.io/badge/license-CC0-green)

![Open](https://img.shields.io/badge/open-standard-orange)

# Bitcoin Digital Objects (BDOs)

**An open architecture for digital ownership on Bitcoin.**

---

## What is a Bitcoin Digital Object?

A **Bitcoin Digital Object (BDO)** is a digital object whose ownership is secured by Bitcoin.

Unlike traditional digital files, a BDO can be:

- Truly owned
- Independently verified
- Carried across compatible applications

A BDO is not tied to any single platform.

Applications may disappear.

Ownership remains.

---

## Why BDOs?

The internet allowed us to create and share digital things.

Bitcoin allows us to own them.

Bitcoin Digital Objects bridge those two worlds.

They transform digital content into independently owned digital objects.

---

## Architecture

The BDO ecosystem is built as a layered architecture.

```
Applications
        ↑
Bitcoin Digital Objects (BDOs)
        ↑
STAS-01
        ↑
Taproot Assets
        ↑
Bitcoin
```

Each layer has a different responsibility.

Bitcoin provides security.

Taproot Assets provide digital asset primitives.

STAS-01 defines interoperability.

BDOs define the ownership model.

Applications create user experiences.

---

## Design Principles

Every Bitcoin Digital Object should satisfy five fundamental properties.

### Ownership

Ownership belongs to users.

Not to applications.

---

### Verification

Anyone should be able to independently verify authenticity.

Verification should never require trusting a platform.

---

### Portability

Ownership travels with the user.

Applications support BDOs.

They do not contain them.

---

### Persistence

Digital ownership should outlive individual services.

A BDO should survive the disappearance of any application.

---

### Composability

The same BDO may unlock different experiences across different applications without changing its identity.

---

## Repository Structure

```
docs/

    01-bdo-architecture.md

    02-bdo-identity-model.md

    03-bdo-ownership-model.md

    04-bdo-capability-model.md

    05-bdo-trust-model.md

    ...
```

---

## Relationship with STAS-01

**Bitcoin Digital Objects (BDOs)** define the conceptual model for digital ownership.

**STAS-01** defines the open interoperability specification that allows BDOs to work across compatible implementations.

---

## Reference Implementations

This repository does not define a single implementation.

Compatible implementations are encouraged.

Current reference implementations include:

- STAS-01
- Supermultiverse
- BTCPay Server Plugin

---

## Status

Bitcoin Digital Objects are an open architecture under active development.

Community discussion and compatible implementations are encouraged.

---

## Guiding Principle

> Applications may disappear.

> Ownership should not.

---

## Vision

> The internet let us share digital things.

> Bitcoin lets us own them.


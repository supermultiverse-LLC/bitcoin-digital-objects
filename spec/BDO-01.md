# BDO-01 — Bitcoin Digital Objects

Status: Draft
Category: Open Standard
Version: 1.0 (draft)

## Abstract

Bitcoin Digital Objects (BDOs) are an open category of digital objects whose ownership is secured by Bitcoin.

This document is the conceptual specification of Bitcoin Digital Objects. It defines what a Bitcoin Digital Object is and the model that makes one ownable, verifiable, and portable across independent applications, without depending on any single vendor, platform, or issuer.

BDO-01 is compiled from the accepted BDO RFCs and defines the conceptual model only. It intentionally avoids implementation details. How a Bitcoin Digital Object is represented, proven, serialized, and exchanged is defined by interoperability specifications such as STAS-01, which implement this model without redefining it.

---

## 1. Introduction

The internet made it possible to create and share digital things. Bitcoin made it possible to own them. Bitcoin Digital Objects make that ownership useful.

A Bitcoin Digital Object is a digital object whose ownership is secured by Bitcoin. Unlike a traditional digital file, it can be owned, verified, and carried across compatible applications. Ownership belongs to the user, not to any application, marketplace, or platform.

Bitcoin Digital Objects are an open category. No single company owns them, and no single platform controls them.

### 1.1 Core Properties

Every Bitcoin Digital Object is designed around three properties:

- **Own** — ownership belongs to the user; applications may facilitate ownership but never hold it.
- **Verify** — authenticity and ownership can be confirmed independently, without trusting an intermediary.
- **Carry** — the object is portable across any compatible application.

### 1.2 Goal

The goal is an open ecosystem where digital ownership is portable, verifiable, and interoperable.

---

## 2. Architecture and Layering

The ecosystem is composed of independent layers, each with a single responsibility:

```text
Applications              (wallets, games, marketplaces, communities, …)
      ▲
Bitcoin Digital Objects   (the open ownership category — this document)
      ▲
STAS-01                   (an open interoperability specification)
      ▲
Taproot Assets
      ▲
Bitcoin
```

Bitcoin Digital Objects define the concepts. STAS-01 is one interoperable representation of those concepts. A specification implements this model; it does not redefine it, and multiple compatible specifications may represent the same model. Bitcoin is the ultimate source of ownership and the common root of trust for every higher layer.

The remainder of this document defines the conceptual model: Identity, Ownership, Lifecycle, Capabilities, Metadata, Issuer, Trust, and Verification.

---

## 3. Identity

A Bitcoin Digital Object has exactly one identity. That identity is globally unique, persistent, independently verifiable, and application-independent. It belongs to the object itself — not to a wallet, an application, or an issuer.

Identity answers "what object is this?" and must remain stable for the entire lifetime of the object. Everything else about the object may change; its identity must not. Identity is distinct from state, from ownership, and from metadata: applications must never rely on metadata to establish identity.

---

## 4. Ownership

Ownership is the defining characteristic of a Bitcoin Digital Object.

Every object has exactly one current owner, holding the exclusive authority to control it. Ownership is independent of the issuer, the application, the marketplace, the wallet software, and the storage provider, and continues to exist even if none of those systems remain online.

Ownership may be transferred. A transfer changes only the owner — never the object's identity, history, or meaning — and must be independently verifiable. Ownership and custody are different concepts: a user may delegate custody (who manages the keys) without transferring ownership (who owns the object). Ownership grants authority over the object; the specific rights it grants depend on the object and are exercised through its Capabilities. Recovery of keys is an implementation concern and is not part of the ownership model.

---

## 5. Lifecycle

A Bitcoin Digital Object exists throughout a lifecycle while remaining the same object:

```text
Creation → Ownership → Transfer → Evolution → Long-Term Preservation
```

Creation happens exactly once and establishes the object's identity, initial owner, and origin. Ownership is the resting state between transfers; each transfer preserves identity, authenticity, and continuity. Evolution — metadata updates, capability expansion, compatibility with new applications — extends the object without replacing it; an act that would alter identity produces a different object, not an evolved one. Long-term preservation applies throughout: objects are intended to outlive the applications that display them.

**Continuity** connects every phase. Regardless of how many times ownership changes or capabilities evolve, the object remains the same Bitcoin Digital Object. Without continuity there is no lifecycle, only disconnected objects.

---

## 6. Capabilities

A Bitcoin Digital Object may expose one or more capabilities. A capability describes what an object can do — access, membership, collection, redemption, participation, and so on — while preserving a common, portable identity.

Capabilities are properties of the object, optional, and independent of ownership: ownership determines who may exercise a capability, while the capability itself defines only what is possible. Capabilities may evolve over the object's lifetime without changing its identity, and the model is intentionally open so new capabilities may appear without affecting existing objects. Applications may ignore capabilities they do not understand while preserving interoperability. A capability describes a possibility; it is not an authorization, an execution, or a guarantee of a result.

---

## 7. Metadata

Every Bitcoin Digital Object carries descriptive information about itself, called metadata. Metadata lets compatible applications understand, display, and interpret an object.

Metadata describes the object; it never defines the object's identity or ownership. An application must never infer ownership from metadata — ownership is established only by verification anchored to Bitcoin. Metadata may include visual information (name, image, media), informational fields (issuer, collection, dates), functional hints (supported capabilities), and domain-specific attributes. It is intentionally extensible: applications should ignore metadata fields they do not understand and preserve rather than discard them. Metadata may evolve while identity remains unchanged.

---

## 8. Issuer

Every Bitcoin Digital Object originates from an issuer, which creates the object and establishes its initial authenticity. An issuer may be a person, a company, a community, an institution, a software system, or an autonomous protocol; the architecture does not restrict who may issue.

Issuance is a one-time event that establishes identity, origin, and initial ownership. After issuance, ownership belongs exclusively to the current owner: being the issuer grants no power to revoke, reclaim, transfer, or modify ownership, unless explicitly defined by an open specification and accepted by the owner. Issuers may build reputation, but reputation is a social signal outside the ownership and verification models and never replaces independent verification. An object must remain verifiable even after its issuer disappears.

---

## 9. Trust

A Bitcoin Digital Object should never require trust in an application, issuer, or platform to establish its authenticity. Trust is replaced by independent verification using publicly available cryptographic evidence anchored to Bitcoin.

Verification should be publicly reproducible, should not depend on a specific application, and should remain possible even if the issuer or original platform no longer exists. Bitcoin provides the root of trust from which every higher layer inherits its security. Reputation and trust are distinct from authenticity: authenticity is determined through verification, not through reputation. Digital ownership should outlive digital businesses.

---

## 10. Verification

Ownership only has value if it can be independently verified. Verification answers objective questions about an object — does it exist? is it the same object? who currently owns it? who issued it? has ownership changed? is it authentic? — and deliberately not subjective ones, such as whether an object is valuable or an issuer reputable.

Verification establishes authenticity (that an object originates from its claimed issuer) and provenance (its verifiable history), and confirms continuity (that it is still the same object across its lifecycle). Verification is a technical process; trust is a human decision. Bitcoin Digital Objects maximize what can be verified while minimizing what must be trusted. Verification should be objective, independent, reproducible, and interoperable: any compatible implementation given the same evidence should reach the same result, without trusting any application, wallet, marketplace, custodian, or company.

> Trust is optional. Verification should not be.

---

## 11. Relationship to STAS-01

This document defines the conceptual model. STAS-01 defines how compatible systems represent Bitcoin Digital Objects.

The concepts map onto the STAS-01 representation as follows: Identity, Capabilities, and Metadata correspond directly to STAS Core Object Model components; Ownership, Lifecycle, Issuer, Trust, and Verification are conceptual properties that STAS supports through its components and pipeline but does not itself define. STAS-01 explicitly does not define ownership semantics, which remain in this layer. A detailed mapping is maintained in `docs/bdo-stas-mapping.md`.

A specification representing Bitcoin Digital Objects preserves the requirements of this model. In particular, such a representation is expected to preserve the global uniqueness and permanence of Identity defined in Section 3.

---

## 12. References

### 12.1 BDO RFCs

- RFC-0001 — Alignment of STAS-01 with the Bitcoin Digital Objects Architecture (superseded by RFC-0002)
- RFC-0002 — Align STAS-01 with the Bitcoin Digital Objects Architecture
- RFC-0003 — Identity Model
- RFC-0004 — Capability Model
- RFC-0005 — Trust Model
- RFC-0006 — Ownership Model
- RFC-0007 — Lifecycle Model
- RFC-0008 — Metadata Model
- RFC-0009 — Issuer Model
- RFC-0010 — Verification Model

### 12.2 Informative References

- STAS-01 — Shared Taproot Assets Standard (interoperability specification representing Bitcoin Digital Objects)
- `docs/bdo-stas-mapping.md` — BDO ↔ STAS-01 consistency mapping
- Taproot Assets; Bitcoin

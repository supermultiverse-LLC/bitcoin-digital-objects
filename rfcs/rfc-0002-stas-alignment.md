# RFC-0002 — Align STAS-01 with the Bitcoin Digital Objects Architecture

Status: Accepted

Author: Supermultiverse

Created: 2026-07-15

---

# Abstract

This RFC formally aligns STAS-01 with the Bitcoin Digital Objects (BDO)
architecture.

The purpose of this document is not to change the STAS-01 specification,
its proof model or its serialization format.

Instead, it redefines the architectural role of STAS-01 inside the
broader Bitcoin Digital Objects ecosystem.

After this RFC:

- Bitcoin Digital Objects (BDOs) become the open ownership category.
- STAS-01 becomes an interoperability specification for representing BDOs.
- Existing implementations remain fully compatible.

No protocol changes are introduced.

---

# Motivation

STAS-01 was originally created before the Bitcoin Digital Objects concept
existed.

As the ecosystem evolved, it became clear that the specification and the
category it represented had become conceptually intertwined.

This created unnecessary confusion.

An interoperability specification should not define the ownership category
itself.

Instead, it should define how compatible systems represent objects within
that category.

This RFC separates those two responsibilities.

---

# Problem Statement

Prior documentation often described STAS-01 as if it were both:

- the ownership model
- the interoperability standard

These are different concerns.

An ownership category should remain independent from any specific
representation.

Otherwise:

- innovation becomes tied to one implementation;
- future specifications become harder to introduce;
- the ecosystem becomes unnecessarily centralized.

---

# New Architectural Position

The Bitcoin Digital Objects ecosystem is composed of multiple layers.
Applications
        ↑
Bitcoin Digital Objects (Category)
        ↑
STAS-01 (Open Specification)
        ↑
Taproot Assets
        ↑
Bitcoin

Each layer has a distinct responsibility.

| Layer | Responsibility |
|-------|----------------|
| Bitcoin | Security and consensus |
| Taproot Assets | Native digital asset primitives |
| STAS-01 | Open interoperability specification |
| Bitcoin Digital Objects | Open ownership category |
| Applications | User experiences |

STAS-01 therefore defines one interoperable representation of Bitcoin
Digital Objects.

It does not define the category itself.

---

# Scope

This RFC changes only the architectural positioning of STAS-01.

It does not modify:

- proof format;
- metadata format;
- serialization;
- signatures;
- verification rules;
- APIs;
- compatibility;
- existing implementations.

---

# Required Documentation Updates

Following approval of this RFC, project documentation should be updated
to reflect the new architecture.

This includes:

- README
- specification introduction
- terminology
- diagrams
- implementation references

Documentation should consistently distinguish between:

- Bitcoin Digital Objects (category)
- STAS-01 (specification)

---

# Migration

No migration is required.

Existing STAS-01 proofs remain valid.

Existing implementations remain compatible.

No software changes are required to adopt this RFC.

Only documentation and architectural positioning are affected.

---

# Benefits

This alignment provides several advantages.

- Clear separation between category and specification.
- Multiple compatible specifications become possible.
- Implementations compete through user experience rather than ownership.
- Long-term architectural flexibility.
- Better interoperability across the ecosystem.

---

# Future Work

This RFC establishes the foundation for future architectural work.

Subsequent RFCs may define:

- metadata evolution;
- capability negotiation;
- issuer interoperability;
- verification improvements;
- additional compatible specifications.

---

# Conclusion

Bitcoin Digital Objects define what is being owned.

STAS-01 defines how compatible systems represent that ownership.

Separating these responsibilities creates a cleaner, more extensible and
more interoperable architecture while preserving complete compatibility

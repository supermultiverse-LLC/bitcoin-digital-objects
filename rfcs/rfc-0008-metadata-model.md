# RFC-0008 — Define the Bitcoin Digital Object Metadata Model

Status: Draft

Author: Supermultiverse

Created: 2026-07-17

---

# Abstract

This RFC defines the metadata model for Bitcoin Digital Objects (BDOs).

Every Bitcoin Digital Object carries information about itself. This information is called metadata. Metadata allows applications to understand, display, and interpret an object without changing its identity or ownership.

This RFC defines the conceptual role of metadata only. It intentionally avoids implementation details, which belong to interoperability specifications such as STAS-01.

---

# Motivation

A Bitcoin Digital Object consists of more than ownership.

Applications also need descriptive information — a name, an image, a description, an issuer, capabilities, or application-specific attributes. This information forms the object's metadata.

Metadata provides context. A shared metadata model lets independent applications describe and present the same object meaningfully, while keeping description strictly separate from ownership and identity.

---

# Purpose of Metadata

Metadata exists to describe a Bitcoin Digital Object.

It allows compatible applications to present meaningful experiences to users.

Metadata should never become the source of truth for ownership. Ownership remains anchored to Bitcoin and is determined by the Ownership Model, never by metadata.

---

# Metadata versus Identity

Identity and metadata are different concepts.

Identity answers:

> Which object is this?

Metadata answers:

> What do we know about this object?

Changing metadata does not, by itself, create a new Bitcoin Digital Object. Identity persists independently from metadata, and metadata is descriptive information attached to an identity rather than a definition of it.

---

# Metadata versus Ownership

Ownership determines who controls the object. Metadata describes the object.

These responsibilities remain independent.

An application must never infer ownership solely from metadata. A claim about ownership expressed in metadata has no authority; ownership is established only through verification anchored to Bitcoin.

---

# Metadata Categories

Metadata may include several kinds of information. These categories are descriptive, not exhaustive or mutually exclusive.

### Visual

- name;
- description;
- image;
- animation;
- media.

### Informational

- issuer;
- collection;
- creation date;
- language;
- version.

### Functional

- supported capabilities;
- application hints;
- interaction requirements.

### Domain-Specific

Applications may introduce additional metadata relevant to their domain, such as player statistics, ticket information, event schedules, memberships, or credentials.

Domain-specific metadata should remain compatible with the underlying object and should not contradict its identity, ownership, or verified properties.

---

# Extensibility

The metadata model is intentionally extensible.

New metadata fields may appear over time. Applications should ignore metadata fields they do not understand whenever doing so is safe, and should preserve them rather than discard them.

This allows the ecosystem to evolve without breaking compatibility. How unknown fields are processed and preserved in a concrete representation is defined by interoperability specifications; in STAS-01 this is governed by the extension processing rules.

---

# Interpretation

Different applications may interpret the same metadata differently.

One application may display an image, another may focus on capabilities, and another may ignore certain fields entirely.

Metadata provides information; applications decide how to present it. Interpretation by an application never changes the object's identity, ownership, or verified properties.

---

# Persistence and Evolution

Metadata may evolve. Descriptions may improve, media may change, and capabilities may expand.

Identity remains unchanged throughout. Metadata evolution should preserve continuity, consistent with the Lifecycle Model: describing an object differently over time extends the same object rather than replacing it.

---

# Relationship with Capabilities

Metadata may declare which capabilities an object exposes.

Such declarations are descriptive hints that help applications discover capabilities. They do not define the capabilities themselves, which are governed by the Capability Model, and they do not grant authority to exercise them, which is governed by the Ownership Model.

---

# Relationship with Specifications

This RFC defines the conceptual role of metadata only.

How metadata is structured, serialized, encoded, and transported belongs to interoperability specifications such as STAS-01.

A specification implements this metadata model; it does not redefine it. Multiple compatible specifications may represent the same metadata.

---

# Design Principles

Metadata should be:

- descriptive;
- extensible;
- interoperable;
- application-independent;
- identity-preserving.

---

# Future Work

Subsequent RFCs and specifications may define:

- metadata representation and serialization;
- canonical metadata fields;
- metadata extension handling;
- media and content addressing;
- localization.

These build upon the metadata model without altering it.

---

# Conclusion

Metadata is how a Bitcoin Digital Object describes itself to the applications that display it.

It is rich, extensible, and free to evolve, but it carries no authority over the two things it can never define: the object's identity and its ownership.

> Metadata describes the object.
>
> It never defines ownership.

# AP-008 — BDO Issuer Model

**Status:** Draft v1.0

---

# Abstract

Every Bitcoin Digital Object (BDO) originates from an issuer.

The issuer creates the object and establishes its initial authenticity.

Once issued, however, the issuer no longer defines ownership.

This document defines the conceptual role of issuers within the Bitcoin Digital Objects ecosystem.

It intentionally avoids implementation details.

---

# Introduction

Every object has an origin.

A Bitcoin Digital Object begins with an issuer.

The issuer establishes the object's initial existence.

After issuance, ownership becomes independent.

Issuance and ownership are separate concepts.

---

# What is an Issuer?

An issuer is an entity that creates a Bitcoin Digital Object.

An issuer may be:

- a person
- a company
- a community
- an institution
- a software system
- an autonomous protocol

The architecture intentionally does not restrict who may issue Bitcoin Digital Objects.

---

# Responsibilities

The issuer is responsible for establishing the initial authenticity of the object.

Typical responsibilities include:

- creating the object
- defining its initial metadata
- establishing its initial owner
- providing provenance
- publishing information required for independent verification

The issuer does not control the object after issuance unless it remains the current owner.

---

# Issuance

Issuance is a one-time event.

A Bitcoin Digital Object is issued exactly once.

Issuance establishes:

- identity
- origin
- initial ownership

Future ownership transfers do not modify the issuer.

---

# Ownership Independence

Ownership belongs to the current owner.

Not to the issuer.

Issuers do not retain implicit authority over Bitcoin Digital Objects.

Being the issuer does not grant the ability to:

- revoke ownership
- reclaim ownership
- transfer ownership
- modify ownership

unless explicitly defined by an open specification and accepted by the owner.

Ownership always remains an independent concept.

---

# Authenticity

Issuers establish authenticity.

Verification confirms authenticity.

Trust remains a personal decision.

Applications may choose how to represent issuer reputation.

The BDO architecture does not assign privileged status to any issuer.

---

# Reputation

Issuers may build reputation over time.

Applications may use reputation to help users evaluate Bitcoin Digital Objects.

Reputation exists outside the ownership model.

Reputation should never replace independent verification.

---

# Multiple Issuers

Future specifications may allow collaborative issuance.

Examples include:

- co-issued credentials
- consortium memberships
- multi-organization certifications

The conceptual model permits multiple issuers provided that authenticity remains independently verifiable.

---

# Issuer Independence

The issuer may disappear.

The company may disappear.

The website may disappear.

The Bitcoin Digital Object should remain verifiable.

Applications should never depend on the issuer remaining online.

---

# Relationship with Ownership

The issuer creates the object.

The owner controls the object.

These responsibilities are intentionally separate.

---

# Relationship with Verification

Verification confirms that a Bitcoin Digital Object originates from its claimed issuer.

Verification should remain independent from the issuer's continued existence.

---

# Relationship with Metadata

Issuer information forms part of the object's metadata.

Metadata describes the issuer.

It does not grant authority.

---

# Relationship with Specifications

This document defines the conceptual role of issuers.

Identity encoding, signatures and verification mechanisms belong to interoperability specifications such as STAS-01.

---

# Design Principles

Issuers should:

- establish authenticity
- publish verifiable information
- remain independent from ownership
- avoid privileged control
- enable long-term verification

---

# Guiding Principle

> The issuer creates the object.

> The owner controls the object.
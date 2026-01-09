# Inactivity Models — Continuum Protocol

## Purpose

This document explores different models for determining user inactivity in a trust-minimized, on-chain inheritance protocol.

Continuum Protocol does not attempt to prove death.  
It relies on **cryptographic inactivity** instead.

This document:
- Explains supported inactivity signals
- Evaluates trade-offs
- Guides future implementation choices

---

## Design Constraints

Any inactivity model must:

- Be enforceable on-chain
- Avoid reliance on off-chain authorities
- Favor safety over automation
- Allow user override while active
- Be understandable and auditable

---

## Model 1: Explicit Activity Pings (Primary Model)

### Description

The user periodically submits an explicit on-chain transaction (“activity ping”) to signal liveness.

Examples:
- Calling a `ping()` function
- Updating a nonce or timestamp
- Resetting an inactivity counter

### Pros
- Simple and deterministic
- Fully on-chain
- User-controlled
- Clear audit trail

### Cons
- Requires user discipline
- Users may forget to ping

### Suitability
✅ Strong default model  
✅ Recommended baseline

---

## Model 2: Transaction-Based Activity

### Description

Any user-initiated transaction counts as activity.

### Pros
- Low friction
- No special transactions required

### Cons
- Ambiguous intent
- Inactivity may be accidental
- Difficult to distinguish noise from intent

### Suitability
⚠️ Useful as a supplementary signal  
❌ Not recommended as the sole trigger

---

## Model 3: Multi-Signal Hybrid Model

### Description

Combines:
- Explicit activity pings
- Transaction presence
- Optional grace periods

Inheritance triggers only if **all signals indicate inactivity**.

### Pros
- More robust
- Reduces false positives

### Cons
- Increased complexity
- Harder to reason about formally

### Suitability
⚠️ Advanced implementation only

---

## Model 4: Third-Party Oracles (Rejected)

### Description

Relies on oracles or off-chain attestations to determine inactivity.

### Reason for Rejection
- Introduces trust assumptions
- Adds censorship and manipulation risk
- Conflicts with protocol philosophy

### Suitability
❌ Explicitly out of scope

---

## Safety Principles

Continuum Protocol follows these rules:

- False negatives (late inheritance) are acceptable
- False positives (early inheritance) are catastrophic
- User activity always overrides automation
- Time buffers are mandatory

---

## Recommended Default Configuration

For early implementations:

- Explicit activity ping required
- Conservative inactivity periods (months or years)
- Grace window before any asset release
- Clear on-chain reactivation path

---

## Relationship to Threat Model

This document complements:
- `THREAT_MODEL.md` (false inactivity triggers)
- `ARCHITECTURE.md` (time-based logic)

---

## Status

This document reflects:
- Design exploration
- No finalized implementation
- Subject to revision based on research and audits

---

## Disclaimer

This is not a production specification.

Continuum Protocol is experimental and should not be used with real assets at this stage.

# Architecture — Continuum Protocol

## Purpose

This document describes the high-level architecture of Continuum Protocol, including its core components, trust boundaries, and interaction flow.

Continuum Protocol is an early-stage research design.  
This document exists to clarify system structure and guide future implementations.

---

## Architectural Goals

The protocol is designed to:

- Preserve user sovereignty over assets
- Minimize trust assumptions
- Avoid custodial control
- Be composable with existing wallets and smart contracts
- Favor explicit, on-chain state over implicit off-chain logic

---

## Core Components

### 1. User Wallet (Owner)

The asset owner:
- Defines inheritance parameters
- Remains in full control while active
- Can modify or cancel inheritance at any time before triggering

Trust assumption:
- User controls their private keys securely while active

---

### 2. Continuity Smart Contracts

Protocol contracts are responsible for:
- Storing inheritance configuration
- Tracking inactivity state
- Enforcing time-based conditions
- Controlling when withdrawals become possible

Properties:
- Non-custodial
- Deterministic execution
- No admin or privileged roles

---

### 3. Time & Inactivity Logic

Inactivity is determined using:
- On-chain timestamps
- Explicit user activity signals
- Protocol-defined inactivity windows

Design principle:
- Favor delayed inheritance over premature triggering

---

### 4. Beneficiaries

Beneficiaries:
- Are predefined by the user
- Can only act once inheritance conditions are satisfied
- Cannot bypass protocol rules

Trust assumption:
- Beneficiaries are untrusted by default

All constraints are enforced on-chain.

---

## Trust Boundaries

| Component | Trust Level |
|---------|------------|
| Blockchain consensus | Trusted |
| Smart contract execution | Trusted |
| User key management | User responsibility |
| Beneficiaries | Untrusted |
| Off-chain actors | Untrusted |

No off-chain trust is required for protocol correctness.

---

## High-Level Interaction Flow

1. User deploys or configures inheritance parameters
2. User remains active → protocol is idle
3. Inactivity threshold is reached
4. Inheritance state becomes active
5. Withdrawal windows open according to schedule
6. Assets are released progressively
7. User activity at any point can halt the process

---

## Failure Philosophy

The system is designed such that:
- False negatives (late inheritance) are acceptable
- False positives (early inheritance) are critical failures

Safety is prioritized over automation.

---

## Non-Goals

The architecture does not attempt to solve:
- Legal inheritance enforcement
- Identity verification
- Death certification
- Custodial recovery
- Off-chain arbitration

---

## Status

Architecture reflects:
- Concept & design phase
- No production deployment
- Subject to change based on research and security review

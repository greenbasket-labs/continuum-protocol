# Continuum Protocol — Protocol Flow

This document describes the lifecycle of an inheritance plan
from creation to execution.

---

## 1. Plan Creation

A user (the Owner) initializes an inheritance plan by defining:

- One or more beneficiary identities
- Inactivity period (minimum 1 year)
- Withdrawal schedule (staged or sequential)
- Cancellation and override permissions
- Optional public visibility settings

No funds are transferred to the protocol at this stage.

---

## 2. Inactivity Monitoring

The protocol tracks **activity signals**, which may include:
- signed on-chain transactions
- periodic cryptographic pings
- optional off-chain attestations

If valid activity is detected, the plan remains inactive.

---

## 3. Inactivity Threshold Reached

If no valid activity is detected for the defined period:

- The plan enters a **Pending Execution** state
- Public metadata may reflect this transition
- The Owner continues to receive notifications if enabled

At this stage, execution is not yet final.

---

## 4. Grace & Cancellation Window

During the withdrawal grace period:

- The Owner may cancel execution at any time
- Cancellation immediately resets the plan state
- No assets are transferred during this window

This prevents accidental or false-positive execution.

---

## 5. Beneficiary Validation

Once execution proceeds:

- Beneficiary claims are validated
- Identity matching occurs via cryptographic proof
- Stored hashed metadata is matched, not revealed

Invalid claims are rejected automatically.

---

## 6. Sequential Asset Release

Assets are released in **defined stages**, not all at once:
- time-based tranches
- asset-type ordering
- optional rate limits

This reduces risk, abuse, and operational failure.

---

## 7. Completion & Final State

After full execution:
- The plan is marked as completed
- No further actions are allowed
- Historical records remain publicly verifiable

---

## Key Properties

- Non-custodial
- Owner-controlled until final execution
- Privacy-preserving
- Chain-agnostic

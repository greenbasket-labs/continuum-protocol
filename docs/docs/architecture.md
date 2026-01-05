# Continuum Protocol — Architecture

## Design Philosophy

Continuum Protocol is designed as a **non-custodial, chain-agnostic inheritance protocol**
that integrates with existing wallets, smart contracts, and blockchains.

The protocol does NOT:
- Hold user funds
- Control private keys
- Act as a custodian
- Replace existing wallets or L1/L2 chains

Instead, it provides **inheritance logic as a composable protocol layer**.

---

## High-Level Components

### 1. Inheritance Logic Layer (Core Protocol)
- Defines rules for inactivity periods
- Manages beneficiary validation
- Controls staged and sequential asset release
- Enforces cancellation and override by the owner

This layer is implemented via smart contracts and/or protocol standards,
depending on the host chain.

---

### 2. Identity & Proof Layer (Abstracted)
- Supports verification of beneficiary identity
- May use:
  - hashed personal metadata
  - zero-knowledge proofs
  - off-chain attestations
- No raw personal data is stored on-chain

Exact implementation is intentionally abstracted.

---

### 3. Execution Layer (Chain-Specific)
- Executes inheritance actions on:
  - Ethereum-compatible chains
  - Other L1s or L2s via adapters
- Designed to be extended, not hard-coded to one chain

---

## Privacy Model

- Sensitive personal information is never stored in plaintext on-chain
- Public visibility is limited to:
  - existence of an inheritance plan
  - time windows
  - execution state
- Identity matching occurs via cryptographic proofs or attestations

---

## Extensibility

Continuum Protocol is designed so that:
- Wallets can integrate it
- DAOs can build governance inheritance
- Institutions can extend it for compliant use cases

The protocol defines **rules**, not **UI or custody**.

---

## Non-Goals

- Building a new L1 or L2
- Replacing MetaMask or wallets
- Acting as a legal will substitute
- Custody of user assets

---

## Status

This architecture is **conceptually finalized**  
Implementation details will evolve iteratively.

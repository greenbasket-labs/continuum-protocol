# Continuum Protocol — Threat Model

This document outlines potential attack vectors,
failure modes, and mitigation strategies within Continuum.

---

## 1. False Death / Premature Execution

### Threat
An attacker attempts to trigger inheritance execution
while the Owner is still alive.

### Mitigations
- Long minimum inactivity period (≥ 1 year)
- Grace and cancellation window
- Multiple activity signals instead of a single trigger
- Owner override always takes precedence

---

## 2. Beneficiary Impersonation

### Threat
A malicious actor claims inheritance by pretending
to be a listed beneficiary.

### Mitigations
- Cryptographic identity matching
- Hashed metadata comparison (not plaintext)
- Optional multi-factor verification
- Claim attempts are publicly auditable

---

## 3. Griefing & Lock Attacks

### Threat
Attackers attempt to permanently lock assets
by triggering partial states or invalid claims.

### Mitigations
- Explicit state machine transitions
- Automatic rejection of invalid claims
- No irreversible transitions until final execution
- Sequential release prevents full lockup

---

## 4. Oracle or Signal Manipulation

### Threat
Manipulation of off-chain signals to fake inactivity.

### Mitigations
- Preference for on-chain cryptographic signals
- Optional multiple independent signal sources
- No single oracle dependency
- Owner-side cancellation remains authoritative

---

## 5. Privacy Leakage

### Threat
Sensitive personal information is exposed on-chain.

### Mitigations
- No plaintext identity data stored
- All sensitive data hashed or proven via ZK
- Public visibility is optional and minimal
- Beneficiary details never revealed unless required

---

## 6. Smart Contract Exploits

### Threat
Bugs or exploits drain or freeze assets.

### Mitigations
- Minimal contract surface area
- Modular architecture
- No custody of assets by default
- Sequential execution limits blast radius

---

## 7. Governance Capture

### Threat
Protocol governance alters rules maliciously.

### Mitigations
- No governance control over individual plans
- Immutable plan parameters after creation
- Governance limited to protocol upgrades only

---

## Security Philosophy

Continuum prioritizes:
- Owner sovereignty
- Delay over immediacy
- Verification over trust
- Safety over convenience

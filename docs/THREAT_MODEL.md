Threat Model — Continuum Protocol
Purpose
This document outlines the primary threat assumptions, attack surfaces, and mitigation strategies for the Continuum Protocol.
Continuum Protocol is an early-stage research design, not production software.
This threat model exists to:
Make risks explicit
Guide future implementations
Encourage responsible protocol design
Security Assumptions
The protocol assumes:
The underlying blockchain provides:
Transaction ordering guarantees
Finality
Resistance to double-spending
Users control their private keys securely while active
Smart contract execution is deterministic
Time measurements rely on on-chain or protocol-defined timestamps
No off-chain trust assumptions are required.
Threat Surface Overview
Primary attack surfaces include:
Inactivity detection logic
Beneficiary withdrawal mechanism
Time-based triggers
User reactivation / cancellation flow
Smart contract implementation errors
Threat Categories & Analysis
1. False Inactivity Trigger
Description:
An attacker or edge case causes inheritance to trigger while the owner is still active.
Impact:
Unauthorized asset release.
Mitigations (Design-Level):
Conservative inactivity thresholds
User-defined inactivity windows
Explicit on-chain “activity pings”
Grace periods before withdrawal execution
2. Beneficiary Abuse or Premature Withdrawal
Description:
A beneficiary attempts to withdraw assets earlier than allowed.
Impact:
Violation of owner intent.
Mitigations:
Strict on-chain time checks
Sequential release schedules
Immutable withdrawal conditions once triggered
3. Key Compromise Before Inactivity
Description:
An attacker gains access to the user’s private key before inactivity is detected.
Impact:
Inheritance logic becomes irrelevant.
Mitigations:
Out of scope for protocol
Key management remains user responsibility
Protocol does not increase attack surface beyond normal wallet usage
4. Reactivation Race Conditions
Description:
User becomes active near or during the withdrawal window.
Impact:
Ambiguous ownership state.
Mitigations:
Clear precedence rules:
Owner activity overrides inheritance
Cooldown periods before asset release
Explicit reactivation transactions
5. Time Manipulation Attacks
Description:
Exploiting timestamp inconsistencies or edge cases.
Impact:
Early or delayed inheritance triggers.
Mitigations:
Use protocol-native time sources
Avoid reliance on block timestamps alone
Apply minimum inactivity buffers
6. Smart Contract Bugs
Description:
Implementation errors introduce unintended behavior.
Impact:
Critical asset loss.
Mitigations:
Minimal contract surface
Formal verification where possible
Independent audits before production deployment
Incremental release strategy
Non-Goals / Out of Scope
The protocol explicitly does not attempt to solve:
Legal inheritance disputes
Identity verification
Death certification
Custodial recovery
Off-chain arbitration
Continuum Protocol enforces cryptographic continuity, not legal ownership.
Design Philosophy
Favor false negatives (delayed inheritance) over false positives
Make all critical state transitions explicit and verifiable
Prefer user control over automation
Minimize trust and complexity
Status
This threat model reflects the design phase of Continuum Protocol.
It will evolve alongside:
Formal specifications
Reference implementations
Security reviews
Disclaimer
This document does not constitute a security audit.
Continuum Protocol is not production-ready and should not be used to manage real assets at this stage.
License
MIT License

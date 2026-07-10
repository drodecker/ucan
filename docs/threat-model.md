# Threat Model

This document identifies early security concerns. It is not complete.

## Threats

### Unauthorized namespace creation

An attacker attempts to create a UCAN namespace derived from a domain they do not control.

Potential mitigation:

- DNS challenge-response
- DNSSEC validation
- signed authorization records
- short-lived nonces
- authorization expiry

### Malicious namespace operator

A legitimate domain owner designates an operator that serves false, inconsistent, or abusive responses.

Potential mitigation:

- resolver-specific trust policy
- operator signing keys
- transparency logs
- independent monitoring
- revocation
- reputation
- optional stake and slashing

### Compromised origin domain

An attacker gains temporary control over DNS and publishes a fraudulent UCAN authorization.

Potential mitigation:

- DNSSEC
- authorization delay
- multi-party approval
- key pinning
- change notifications
- transparency logs
- recovery keys

### Replay attacks

A previously valid authorization is replayed after revocation or expiry.

Potential mitigation:

- timestamps
- sequence numbers
- expiration
- revocation records
- signed state transitions

### Namespace collision

Different systems assign conflicting meanings to the same virtual namespace.

Potential mitigation:

- explicit origin binding
- resolver policy
- namespace identifiers
- signed authority chains
- conflict reporting

### Trust-list capture

A central trust list, DAO, registry, or token majority is captured.

Potential mitigation:

- multiple trust sources
- resolver sovereignty
- transparent policy
- threshold signatures
- independent implementations
- fork and recovery procedures

### Sybil operators

One party creates many operator identities to appear decentralized.

Potential mitigation:

- cryptographic identity continuity
- ASN or organizational verification
- stake
- independent audits
- rate limits
- diversity requirements

### Privacy leakage

UCAN discovery or validation queries reveal user interests or namespace use.

Potential mitigation:

- encrypted DNS transport
- caching
- privacy-preserving discovery
- minimization of validation queries

## Non-security policy risks

- trademark disputes
- inconsistent resolver policies
- jurisdictional conflict
- governance capture
- speculative token incentives
- exclusion of small operators
- overreliance on existing registries or network incumbents

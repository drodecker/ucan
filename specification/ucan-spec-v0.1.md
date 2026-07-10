# UCAN Protocol Specification v0.1

## Status

This document is an early discussion draft.

It does not define an interoperable production standard.

## 1. Scope

UCAN defines a framework for:

- asserting authority from an existing namespace;
- delegating authority to a virtual namespace;
- identifying namespace operators;
- validating signed operator responses;
- revoking or replacing delegations;
- permitting resolvers to apply independent trust policy.

## 2. Non-goals

This version does not:

- alter the ICANN root;
- require a blockchain;
- define a cryptocurrency;
- create a universal operator trust list;
- guarantee browser or resolver adoption;
- define trademark policy;
- define a final governance model.

## 3. Roles

### 3.1 Origin authority

Controls the origin domain and publishes an authorization record.

### 3.2 Namespace operator

Serves the virtual namespace and signs authoritative responses.

### 3.3 UCAN-aware resolver

Discovers and validates authorization records, evaluates operators, and returns results according to local policy.

### 3.4 Trust provider

Optionally publishes evidence about operators, such as audits, endorsements, revocations, or reputation.

## 4. Authorization record

A provisional authorization record may be published beneath the origin domain.

Example:

```dns
_ucan.qwerty.onion.com. 3600 IN TXT (
  "v=ucan1;"
  "namespace=onion.qwerty;"
  "operator=ns1.example.net;"
  "key=BASE64URL_PUBLIC_KEY;"
  "issued=2026-07-10T00:00:00Z;"
  "expires=2026-08-10T00:00:00Z;"
  "nonce=EXAMPLE_NONCE;"
  "sig=BASE64URL_SIGNATURE"
)
```

This syntax is illustrative only.

## 5. Validation sequence

A resolver evaluating `onion.qwerty` should conceptually:

1. determine the expected origin domain;
2. query the UCAN authorization record;
3. validate syntax and version;
4. verify origin-domain control;
5. verify signatures;
6. verify issuance and expiry;
7. discover the namespace operator;
8. evaluate the operator under local trust policy;
9. query the operator;
10. verify the operator response;
11. return the result with validation status.

## 6. Operator identity

An operator should possess a stable public/private key pair.

The operator public key may be:

- embedded in the authorization record;
- referenced by a digest;
- published in a signed operator identity document;
- certified by one or more trust providers.

## 7. Trust policy

The base protocol must not require all resolvers to trust the same operators.

A resolver policy may use:

- cryptographic validity;
- DNSSEC validation;
- registry or registrar endorsement;
- ASN ownership;
- operator audits;
- key age and continuity;
- reputation;
- stake;
- local allowlists or denylists.

## 8. Revocation

A delegation may be revoked by:

- removing the authorization record;
- publishing a signed revocation;
- advancing a sequence number;
- rotating the operator key;
- publishing a replacement authorization.

Resolvers must define cache behavior so revocation can take effect within a bounded period.

## 9. Security considerations

See [Threat Model](../docs/threat-model.md).

## 10. IANA considerations

This draft makes no request of IANA.

## 11. Open issues

The record format, namespace derivation rules, operator protocol, signature format, and discovery method remain unresolved.

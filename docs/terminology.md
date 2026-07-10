# Terminology

## Origin domain

An existing domain name used to establish the initial proof of authority.

Example:

```text
onion.com
```

## Origin authority

The party able to publish or authorize records for the origin domain.

## Virtual namespace

A namespace recognized by UCAN-aware systems but not necessarily present in the ICANN root.

Example:

```text
onion.qwerty
```

## Namespace operator

A server or service authorized to serve records for a UCAN namespace.

## UCAN-aware resolver

A resolver capable of discovering UCAN authorizations, applying trust policy, validating operators, and returning UCAN namespace results.

## Authorization record

A signed or otherwise verifiable declaration connecting an origin domain to a virtual namespace and operator.

## Operator identity

The cryptographic identity used by a namespace operator to sign responses or complete challenges.

## Trust policy

A resolver's local rules for determining whether an authorization, operator, or response should be accepted.

## Trust evidence

Verifiable information used by a trust policy, such as signatures, DNSSEC validation, registry endorsement, ASN control, audit status, or stake.

## Revocation

A mechanism that invalidates a prior authorization, operator key, or trust assertion.

## Federation

Cooperation among independently operated UCAN servers or resolvers without requiring a single universal administrator.

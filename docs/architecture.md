# Architecture

## Overview

UCAN separates naming into four conceptual layers:

1. **Origin authority** — proof that an existing namespace owner authorizes a delegation.
2. **Namespace operator** — the service that hosts or serves the delegated namespace.
3. **Trust and validation** — the rules used by resolvers to determine whether an operator and delegation are acceptable.
4. **Resolution** — the process of returning records to applications.

This separation prevents a common design error: treating control of an existing DNS name as sufficient proof that any designated server should be trusted by all other servers.

## Example

A registrant controls:

```text
onion.com
```

The registrant wishes to authorize:

```text
onion.qwerty
```

The registrant publishes a UCAN authorization record beneath the existing DNS name, for example:

```dns
_ucan.qwerty.onion.com. IN TXT "v=ucan1; namespace=onion.qwerty; operator=ns1.example.net; key=..."
```

The exact record format is not yet standardized.

A UCAN-aware resolver may then:

1. verify control of the originating DNS name;
2. validate the authorization record;
3. discover the designated operator;
4. evaluate that operator under local trust policy;
5. query the operator;
6. validate the response;
7. return the result.

## Data plane and control plane

UCAN should preserve a distinction between:

### Data plane

The data plane serves namespace records and resolution responses.

This may use DNS-compatible protocols, signed DNS messages, DNS-over-TLS, DNS-over-HTTPS, or another standardized transport.

### Control plane

The control plane publishes:

- operator identities;
- public keys;
- authorization status;
- revocations;
- trust anchors;
- policy statements;
- optional stake or reputation information.

A blockchain may be used by one implementation for control-plane coordination, but the UCAN base architecture should not require it.

## Resolver sovereignty

No UCAN server should be required to trust another server merely because a registrant designated it.

Each resolver maintains its own trust policy.

A policy may consider:

- cryptographic validity;
- DNSSEC status;
- operator key continuity;
- registry or registrar endorsement;
- network operator identity;
- ASN control;
- independent audits;
- software attestation;
- reputation;
- stake;
- revocation status;
- jurisdictional or contractual policy.

The protocol should define how evidence is represented and validated without forcing every resolver to use the same policy.

## No UCAN root required

The current design does not require a globally hosted UCAN root zone.

UCAN namespaces may be discovered through verifiable origin records and resolver policy rather than through a single authoritative `.qwerty` zone.

This is a defining architectural choice and remains an open area for further analysis.

## Potential participants

- Domain registrants
- Registries
- Registrars
- DNS hosting providers
- ISPs
- Autonomous System operators
- UCAN namespace operators
- Resolver operators
- Validators and auditors
- Governance organizations
- Standards bodies

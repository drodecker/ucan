# UCAN Protocol Specification v0.1

## Status

This document is an early discussion draft.

It does not define an interoperable production standard.

## 1. Scope

UCAN defines a framework for:

- asserting authority from an existing namespace or network resource;
- delegating authority to a virtual or non-IANA namespace;
- identifying namespace operators;
- validating signed operator responses;
- revoking or replacing delegations;
- permitting resolvers to apply independent trust policy.

## 2. Non-goals

This version does not:

- alter the ICANN root;
- require a blockchain (though optional control-plane uses are described);
- define a mandatory cryptocurrency;
- create a universal operator trust list;
- guarantee browser or resolver adoption;
- define trademark policy;
- define a final governance model.

## 3. Roles

### 3.1 Origin authority

Controls the origin domain, IP block, or other verifiable resource and publishes an authorization record.

### 3.2 Namespace operator

Serves the virtual namespace and signs authoritative responses. In the DannyClaw reference architecture, this role is filled by an OpenClaw-managed application.

### 3.3 UCAN-aware resolver

Discovers and validates authorization records, evaluates operators, and returns results according to local policy. May fall back to conventional DNS or a local database of non-IANA TLDs.

### 3.4 Trust provider

Optionally publishes evidence about operators, such as audits, endorsements, revocations, reputation, or stake.

## 4. Authorization record

A provisional authorization record may be published beneath the origin domain or in reverse DNS (ARPA).

Example (origin domain):

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

Example (IP-based via reverse DNS, as used in DannyClaw):

```dns
1.2.3.4.in-addr.arpa. IN TXT (
  "v=ucan1;"
  "claim=ip-block;"
  "wallet=WALLET_ADDRESS;"
  "stake=COIN_IDENTIFIER;"
  "operator=danny.claw;"
  "sig=..."
)
```

This syntax is illustrative only.

## 5. Validation sequence

A resolver evaluating a non-IANA name such as `name.tld` should conceptually:

1. determine whether the TLD is in the IANA root;
2. if not, query a local or distributed database of claimed namespaces;
3. if a record exists, discover the designated operator (or proxy);
4. validate authorization (origin domain, IP reverse record, stake, or other proof);
5. query the operator or proxy;
6. verify the response;
7. return the result with validation status.

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
- ARIN/RIPE reverse DNS and PTR claims;
- operator audits;
- key age and continuity;
- reputation;
- stake or token minting;
- local allowlists or denylists.

## 8. Revocation

A delegation may be revoked by:

- removing the authorization record;
- publishing a signed revocation;
- advancing a sequence number;
- rotating the operator key;
- publishing a replacement authorization.

Resolvers must define cache behavior so revocation can take effect within a bounded period.

## 9. DannyClaw reference architecture

DannyClaw is a concrete OpenClaw-managed reference implementation of a UCAN-style TLD system.

### 9.1 Overview

An OpenClaw agent (named Danny) generates and operates a fully functioning DNS server application. The application:

- Proxies ordinary DNS queries to Cloudflare authoritative DNS when Cloudflare has an answer.
- For TLDs not present in the IANA/ICANN root, consults a local database of claimed `name.tld` → nameserver mappings.
- If a matching record exists, directs the query to the designated nameserver (or continues proxying).
- Supports direct WebSocket delivery of Cloudflare responses to the client when applicable.

DNS records are created by instructing the OpenClaw agent. The agent records the request as an open-source application that manages Cloudflare DNS under the operator’s account.

### 9.2 Authority and claiming

Authority for the system is established via:

- Reverse DNS (ARPA) TXT records on the operator’s IP addresses.
- ARIN (or equivalent) reverse PTR records that have been exchanged for a blockchain claim on the IP block.
- A wallet address associated with the claim.
- A single-coin stake sufficient to claim the namespace or operator role.
- The Danny agent mints a token representing the claim.

This provides a verifiable link between network-layer ownership (IP block) and the right to operate non-IANA namespaces.

### 9.3 Database

A simple database stores:

- Claimed `name.tld` entries
- Associated nameserver addresses
- Authorization metadata (wallet, stake, timestamp, signature)

### 9.4 Relationship to the protocol

DannyClaw demonstrates one path for incremental deployment:

- Compatible with existing Cloudflare DNS for ordinary domains.
- Adds a side database and proxy logic for experimental TLDs.
- Uses existing reverse-DNS and IP ownership signals as the root of authority rather than a new global root.
- Keeps the operator under user control via OpenClaw.

It is not required for UCAN compliance. Other implementations may use different authorization anchors, storage, or proxy mechanisms.

## 10. Security considerations

See [Threat Model](../docs/threat-model.md).

Additional considerations for the DannyClaw path include:

- Security of the OpenClaw agent and its Cloudflare credentials.
- Integrity of the local namespace database.
- Validation of reverse-DNS and blockchain claims.
- Prevention of unauthorized proxying or record injection.

## 11. IANA considerations

This draft makes no request of IANA.

## 12. Open issues

The record format, namespace derivation rules, operator protocol, signature format, discovery method, and precise staking semantics remain unresolved.

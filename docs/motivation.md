# Motivation

## A decentralized network with a centralized namespace

The Internet is one of the most decentralized systems ever created.

Millions of independently operated networks cooperate through open protocols. Autonomous Systems exchange routes. Operators deploy resolvers, authoritative servers, applications, and transport infrastructure independently while remaining interoperable because they share technical standards.

The globally recognized namespace follows a different model.

Authority to create new top-level namespaces ultimately flows through a single administrative hierarchy. Responsibility is delegated through registries, registrars, and registrants, but the entry point for new globally recognized namespaces remains centralized.

This architecture has delivered substantial stability.

It has also made experimentation with new namespace models expensive, slow, and institutionally constrained.

## The current alternatives

A party seeking to create a new namespace generally has three choices:

1. Apply through the existing ICANN process.
2. Operate beneath an existing DNS name as a conventional subdomain.
3. Create an alternate naming system requiring custom resolvers, gateways, applications, browser support, or private coordination.

The first path is globally compatible but highly regulated.

The second path is technically straightforward but does not provide the semantics, portability, or independent authority associated with a distinct namespace.

The third path enables experimentation but commonly fragments naming because different systems lack a shared method for authority discovery and verification.

## The opportunity

Existing DNS ownership already provides a globally recognized chain of administrative control.

A registrant who controls `example.com` can publish records, delegate subdomains, use DNSSEC, and prove control through challenge-response mechanisms such as DNS-01.

UCAN asks whether that existing authority can be used as the starting point for a broader, interoperable delegation system.

For example, a registrant controlling `onion.com` might publish an authorization record indicating its intention to establish `onion.qwerty` within a UCAN-compatible namespace system.

That record would not make `onion.qwerty` part of the ICANN root.

Instead, it would provide a verifiable origin of authority that UCAN-aware systems could validate independently.

## The trust problem

Proof that a registrant controls a DNS name does not automatically prove that every server designated by that registrant should be universally trusted.

UCAN therefore separates several questions:

- Who controls the originating DNS name?
- Who is authorized to operate the delegated namespace?
- Which operators or validators are trusted by a given resolver?
- Which trust signals are mandatory, optional, or policy-specific?
- How are authorizations revoked, rotated, or disputed?

This separation is central to the project.

UCAN should not equate domain control with universal server trust.

Instead, resolvers should validate a chain of authority and apply explicit trust policy.

## Why a universal model matters

Future networks may not share one root, one regulatory jurisdiction, one round-trip time, or one administrative authority.

A Mars settlement, isolated industrial network, sovereign infrastructure, or delay-tolerant communications system may need the ability to create and manage local namespace authority independently.

At the same time, those systems may benefit from interoperable delegation rules that allow namespaces to be recognized across networks when trust relationships exist.

UCAN's long-term purpose is therefore broader than creating another alternative DNS root.

It is to explore a portable standard for namespace authority, delegation, verification, and cooperation among autonomous naming systems.

## Design direction

UCAN should:

- preserve compatibility with existing DNS wherever practical;
- avoid requiring modification of the global DNS root;
- use verifiable proofs of control and delegation;
- separate authority, hosting, validation, and policy;
- allow resolvers to maintain independent trust policies;
- support multiple operator and governance models;
- remain independent of any single blockchain or token;
- permit experimentation without claiming premature global authority.

## What UCAN is not

UCAN is not intended to:

- replace ICANN by decree;
- redefine the existing DNS root;
- guarantee that every UCAN namespace is globally recognized;
- make every domain registrant a trusted network operator;
- require blockchain storage of DNS records;
- require a DAO, token, or staking system in the core protocol.

Those mechanisms may be explored as optional trust or governance layers, but they should not define the base protocol.

## Invitation

UCAN is an open research and engineering proposal.

The project invites criticism from DNS operators, standards experts, security researchers, registry and registrar professionals, identity architects, distributed-systems engineers, and anyone concerned with the future of Internet naming.

The first objective is not adoption.

It is to determine whether a coherent, secure, and interoperable model can be designed.

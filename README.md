# UCAN

**Universal Cooperative Addressing Network**

UCAN is an open protocol proposal for decentralized namespace delegation.

Rather than replacing DNS, UCAN explores how authority over new namespaces can be cryptographically delegated from existing DNS ownership while preserving compatibility with today's Internet infrastructure.

## Why UCAN?

The Internet is operated by millions of independent networks, yet the creation of globally recognized namespaces ultimately follows a single administrative hierarchy.

UCAN investigates whether namespace authority can become more open, portable, and cooperative without requiring modification of the global DNS root.

## Project status

UCAN is an early-stage proposal intended for discussion, experimentation, and community contribution.

Nothing in this repository should be treated as a finalized standard.

## Start here

- [Manifesto](docs/manifesto.md)
- [Motivation](docs/motivation.md)
- [Architecture](docs/architecture.md)
- [Terminology](docs/terminology.md)
- [Threat model](docs/threat-model.md)
- [Governance](docs/governance.md)
- [Roadmap](docs/roadmap.md)
- [Draft specification](specification/ucan-spec-v0.1.md)
- [Open questions](docs/open-questions.md)

## Guiding principles

- Preserve compatibility with existing DNS infrastructure
- Avoid dependence on a single global administrative authority
- Prefer cryptographic proof over institutional trust alone
- Support incremental deployment
- Allow multiple trust and governance models
- Keep the protocol separate from any particular token, blockchain, company, or product
- Encourage interoperability among independent implementations

## Repository structure

```text
docs/             Motivation, architecture, governance, and design notes
specification/    Draft protocol specification
examples/         Example records and flows
diagrams/         Architecture diagrams
reference/        Future reference implementations
.github/          Issue and pull request templates
```

## Name

**UCAN** stands for **Universal Cooperative Addressing Network**.

The name also communicates the project's purpose: expanding who can create and participate in trusted namespace systems.

## Contributing

UCAN is intentionally incomplete. Constructive criticism, competing designs, security analysis, and implementation experiments are welcome.

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

Documentation is licensed under [CC BY 4.0](LICENSE-DOCUMENTATION).

Code, when added, will be licensed under the [Apache License 2.0](LICENSE).

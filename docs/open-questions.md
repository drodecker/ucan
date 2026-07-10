# Open Questions

## Namespace model

- How is a virtual namespace uniquely identified?
- Is an origin domain always required?
- Can one origin domain authorize multiple virtual namespaces?
- Can one virtual namespace have multiple origin authorities?
- How should collisions be represented?

## Authorization

- What exact DNS record name should be used?
- Should TXT be used, or should a new RR type eventually be requested?
- Must origin records be DNSSEC-signed?
- How are authorization expiry and renewal handled?
- How are keys rotated?

## Operator trust

- What minimum evidence should every UCAN operator provide?
- Should an ASN be required?
- Should PTR records be considered only supplemental evidence?
- Should registry or registrar endorsements be supported?
- How should shared hosting and multi-tenant operators be represented?
- Can operators cross-sign one another without creating circular trust?

## Resolver behavior

- How are trusted operators discovered?
- What happens when trust policies disagree?
- Should resolvers expose trust status to applications?
- How should negative answers be cached?
- How should split-horizon or local namespaces work?

## Governance and economics

- Is staking useful, necessary, or harmful?
- What behavior could be objectively slashed?
- How can governance avoid capture by token holders or incumbent operators?
- Should protocol governance and operator accreditation be separate?
- Is a DAO appropriate at all?

## Relationship with ICANN and IANA

- Is UCAN complementary to the DNS root or an alternate naming system?
- Should the protocol use the IANA root only as an origin trust source?
- Should UCAN seek any IANA registry assignment?
- Could a future ICANN gTLD serve as a bridge without becoming a central root?

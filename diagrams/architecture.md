# UCAN Architecture Diagram

```mermaid
flowchart TD
    A[Application or user] --> B[UCAN-aware resolver]
    B --> C[Origin DNS]
    B --> D[Namespace operator]
    B --> E[Trust evidence sources]

    C --> F[Authorization record]
    F --> B

    E --> G[Operator identity]
    E --> H[Revocation status]
    E --> I[Optional registry, audit, ASN, or stake evidence]

    D --> J[Signed namespace response]
    J --> B

    B --> K{Local trust policy}
    K -->|Accept| L[Return validated result]
    K -->|Reject| M[Return failure or insecure status]
```

## Trust chain

```text
Origin domain control
        ↓
Signed namespace authorization
        ↓
Designated namespace operator
        ↓
Independent operator trust evidence
        ↓
Resolver-local trust policy
        ↓
Validated response
```

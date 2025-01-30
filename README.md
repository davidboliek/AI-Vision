# Development Workflow

This diagram illustrates our basic development workflow from feature request to deployment.

```mermaid
graph TD
    subgraph Networks
        subgraph Network_A[Network 1]
            MA[Member DB]
            VA[Vendor A Store]
            VB[Vendor B Store]
        end
        
        subgraph Network_B[Network 2]
            MB[Member DB]
            VC[Vendor C Store]
            VD[Vendor D Store]
        end
    end

    C[Customer] --> FM[Front-End Marketplace]
    FM -->|302 Redirect + Encrypted Token| SS[Switchboard Service]
    SS -->|Validate & Route| VI[Vendor Integration]
    VI --> VA
    VI --> VB
    VI --> VC
    VI --> VD
    
    FM -.-> MA
    FM -.-> MB
    SS -.->|Log Transactions| ML[Monitoring & Analytics]
    
    style C fill:#f9f,stroke:#333
    style FM fill:#7ff,stroke:#333
    style SS fill:#ffa,stroke:#333
    style VI fill:#8f8,stroke:#333
    style Networks fill:#fff,stroke:#666
```

## Diagram Explanation

The workflow consists of these key steps:

1. Feature Request: New feature is requested and documented
2. Development: Feature is implemented by developers
3. Code Review: Team reviews the code changes
4. Approval Gate: Changes are either approved or sent back for revision
5. Deploy: Approved changes are deployed
6. Production: Feature is live in production environment

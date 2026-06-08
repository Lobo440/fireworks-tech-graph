# Supplier Labeling Non-Compliance Notification Process

This flowchart describes the proposed automation for notifying suppliers when inbound freight does not meet the packaging/labeling requirement (effective 3/13/26).

## Process Flowchart

```mermaid
flowchart TD
    A([Supplier sends freight package]) --> B[Receiving opens package<br/>and verifies contents]
    B --> C{Internal packaging<br/>has exposed labels?}
    C -->|Yes| D([Proceed with normal<br/>receiving process])
    C -->|No| E[Receiving enters PO # and<br/>line number in quick interface]
    E --> F[System looks up supplier<br/>email contact in Coupa]
    F --> G{Supplier contact<br/>found?}
    G -->|No| H[Flag for buyer<br/>manual follow-up]
    G -->|Yes| I[System sends generic<br/>form letter to supplier<br/>with updated requirement]
    I --> J[(Log event to<br/>tracking dashboard)]
    H --> J
    J --> K{Monthly review:<br/>Supplier over<br/>10 emails?}
    K -->|No| L([Continue monitoring])
    K -->|Yes| M[Issue RCCA and start<br/>formal communication process]

    classDef start fill:#d4edda,stroke:#155724,color:#155724
    classDef decision fill:#fff3cd,stroke:#856404,color:#856404
    classDef action fill:#cce5ff,stroke:#004085,color:#004085
    classDef escalate fill:#f8d7da,stroke:#721c24,color:#721c24
    classDef data fill:#e2e3e5,stroke:#383d41,color:#383d41

    class A,D,L start
    class C,G,K decision
    class B,E,F,I action
    class H,M escalate
    class J data
```

## Key Steps

| # | Step | Owner | System |
|---|------|-------|--------|
| 1 | Open freight and verify labeling | Receiving | — |
| 2 | Enter PO # + line number for non-compliant packages | Receiving | Quick interface (new) |
| 3 | Look up supplier contact | Automated | Coupa |
| 4 | Send form letter with updated requirement | Automated | Email |
| 5 | Log event | Automated | Dashboard |
| 6 | Monthly threshold review (>10 emails) | Supply Chain / Quality | Dashboard |
| 7 | Issue RCCA and formal escalation | Supply Chain / Quality | Existing RCCA process |

## Notes

- Packaging/labeling standard change effective **3/13/26**; Coupa banner already directs suppliers to updated instructions.
- Goal is to empower the receiving team to act in the moment without waiting on buyers.
- Dashboard threshold (10 emails/month) is the proposed trigger for formal RCCA escalation.

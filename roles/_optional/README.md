# Optional expansion roles

This directory holds optional expansion role specifications — roles that are not part of the default council but are available for invocation by name in custom council compositions.

**v1 status:** empty. CHRO ships in the default council in v1 because the people lens is gating in nearly every substantive business decision (pricing, M&A, expansion, technology, restructuring). CHRO lives at [`../chro.md`](../chro.md) alongside the other six default roles, making the default council 7 strong (CEO, CFO, COO, CTO, GC, CHRO, Board Chair).

## Planned for v1.1

| Role | Domain | Best for | Status |
|------|--------|----------|--------|
| CPO | Product, customer value, roadmap | Product launches, feature prioritization, customer-strategy decisions | planned |
| CRO | Pipeline, sales motion, pricing economics | Pricing changes, GTM model changes, sales-team scaling | planned |
| CISO | Security, compliance, threat surface | Vendor risk, data-handling, regulatory exposure, incident response | planned |

## Contributing a new optional role

Use `roles/chro.md` as the structural template — every role file follows the same 13-section structure:

1. Mandate
2. Time horizon
3. Decision lens — questions asked first
4. Default concerns
5. Trade-offs they care about
6. Stress signals
7. Voice and posture (including vocabulary banks)
8. Quantitative anchor (LOAD-BEARING)
9. Forbidden moves (LOAD-BEARING)
10. Information asymmetry
11. Personality (OCEAN profile)
12. Dissent requirement (LOAD-BEARING)
13. Things this role is NOT

Open a PR with your role file in this directory. Include 1-2 example outputs showing role-distinct voice. Not all PRs will be merged — Boardroom is an opinionated artifact — but well-structured role files for common contexts are welcomed.

See [`../../docs/customization.md`](../../docs/customization.md) for the full guidance.

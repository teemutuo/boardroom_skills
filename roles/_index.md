# Role catalog

## Default council (7 roles)

The default Boardroom council. Invoke with `boardroom: [decision]` and these seven roles run automatically.

| Role | File | Primary lens | When this role's perspective is most critical |
|------|------|--------------|------------------------------------------------|
| **CEO** | [`ceo.md`](./ceo.md) | Strategic positioning, long-term horizon, narrative coherence | Capital allocation, strategic direction, public commitments |
| **CFO** | [`cfo.md`](./cfo.md) | Cash, payback, scenario analysis, covenants | Financial decisions, growth investment, pricing changes |
| **COO** | [`coo.md`](./coo.md) | Execution, capacity, operational risk | Implementation timelines, scaling moves, integration |
| **CTO** | [`cto.md`](./cto.md) | Technical architecture, build vs. buy, lock-in | Technology decisions, vendor selection, platform changes |
| **GC** | [`general-counsel.md`](./general-counsel.md) | Contractual exposure, regulatory risk, governance | Pricing changes (MFN), M&A, international expansion, partnerships |
| **CHRO** | [`chro.md`](./chro.md) | People, organizational design, total rewards, cultural runway, succession | Restructuring, RTO / remote-policy, layoffs, M&A integration, compensation, hiring plans — and as a contributing voice on pricing, expansion, technology hiring (where people impact is decisive but easy to under-weight) |
| **Board Chair** ⚔ | [`board-chair.md`](./board-chair.md) | Devil's advocate, motivated reasoning, hostile activist view | EVERY decision (this is the structural counter-voice) |

**Why CHRO is in the default council, not optional.** The people lens is gating in nearly every substantive business decision: pricing changes affect CS team capability and sales comp; M&A is a people decision masquerading as a financial one; international expansion is a hiring problem with regulatory wrapping; technical decisions create senior-IC retention issues. The decisions where CHRO is *not* important to surface tend to be the trivial ones — and on those, CHRO's "I don't have meaningful dissent here" flag is itself useful information.

## Optional expansion roles (planned v1.1)

Will live in `roles/_optional/`. Invoke by name in custom council compositions once shipped.

| Role | Domain | Best for |
|------|--------|----------|
| CPO | Product, customer value, roadmap | Product launches, feature prioritization, customer-strategy decisions |
| CRO | Pipeline, sales motion, pricing economics | Pricing changes, GTM model changes, sales-team scaling |
| CISO | Security, compliance, threat surface | Vendor risk, data-handling, regulatory exposure, incident response |

Contributions welcome via PR using `chro.md` as the structural template. See [`_optional/README.md`](./_optional/README.md) for guidance.

## Composing custom councils

For repeated decision contexts, define a named council in `councils/[name].md`.

**Council presets shipping in v1:**

- **[`councils/m-and-a.md`](../councils/m-and-a.md)** — Default 7 (CHRO already included; preset adds aggregator context for M&A-specific gating)
- **[`councils/restructuring.md`](../councils/restructuring.md)** — Default 7, with **CHRO designated as lead voice** for layoffs, reorganizations, RTO mandates, compensation framework changes

**Patterns worth defining yourself** (using the CHRO file as a template for any new role):

- `councils/product-launch.md` — CEO, CPO, CRO, CFO, CTO (requires CPO/CRO from v1.1 or your own role files)
- `councils/pricing-change.md` — CFO, CRO, GC (MFN!), COO, Board Chair
- `councils/fundraise.md` — CEO, CFO, GC, Board Chair, CRO
- `councils/regulated-industry.md` — CEO, GC, CISO, Regulator (custom), Board Chair, CFO

Then invoke as: `boardroom council m-and-a: [decision]`

## Role file structure

Every role file uses the same 13-section structure:

1. **Mandate** — what this role is responsible for
2. **Time horizon** — what timeframes this role thinks in
3. **Decision lens** — the questions this role asks first
4. **Default concerns** — standing worries
5. **Trade-offs they care about** — explicit tensions
6. **Stress signals** — what triggers heightened pushback
7. **Voice and posture** — including vocabulary banks (uses / does not use)
8. **Quantitative anchor** — required numbers/thresholds (LOAD-BEARING)
9. **Forbidden moves** — out-of-character behaviors (LOAD-BEARING)
10. **Information asymmetry** — what this role doesn't see
11. **Personality (OCEAN)** — Big Five trait profile + optional MBTI label
12. **Dissent requirement** — must disagree with at least one other role
13. **Things this role is NOT** — boundaries

The four LOAD-BEARING sections (Quantitative anchor, Forbidden moves, Vocabulary bank, Dissent requirement) are what prevent role homogenization. Don't trim them when customizing.

## Customization

[Full customization guide →](../docs/customization.md)

---
name: boardroom
description: |
  Boardroom convenes a multi-stakeholder council on a specific business decision the user is actively considering. Seven default roles (CEO, CFO, COO, CTO, General Counsel, CHRO, Board Chair acting as red team) contribute structured perspectives via isolated parallel subagent invocation, then an aggregator produces a structured table or decision memo. Each role runs in a sealed context with its own specification — preventing the output homogenization typical of multi-agent persona work. CHRO is included by default because the people lens (regretted attrition, comp precedent, cultural runway, manager capability) is gating in nearly every substantive business decision, not auxiliary.

  Use this skill when the user explicitly asks for stakeholder perspectives on a decision OR poses a substantive strategic question and pauses (e.g., "should we...", "thinking about...", "before we decide...", "run this by my board", "what would my CFO/CEO/COO/CTO/GC/CHRO say...").

  Do NOT use for: information requests about roles ("what does a CFO do"), generic finance/strategy questions, or anything that isn't a specific decision under consideration.
license: Apache-2.0
---

# Boardroom

A multi-stakeholder council that runs any business decision through seven structurally independent perspectives, then synthesizes them.

## When this skill triggers

Trigger on these patterns:
- `boardroom: [decision]` — full council
- `boardroom [role]: [decision]` — single-role deep dive
- `boardroom council [role list]: [decision]` — custom council composition
- Any phrasing like "what would my CFO/CEO/board think about [decision]"
- Substantive decision phrasings: "should we...", "thinking about...", "before we decide...", "stakeholder review on...", "stress-test this idea"

Do NOT trigger on:
- Informational questions about roles ("what does a CFO do?")
- Generic finance/strategy education
- Anything where the user is not in active decision mode

## The orchestration protocol

This skill follows the **orchestrator-worker pattern** described in Anthropic's *Building Effective Agents* guidance. Two phases.

### Phase 1 — Parallel isolated council members

For each role in the council composition (default: CEO, CFO, COO, CTO, General Counsel, CHRO, Board Chair), invoke a separate subagent with **only that role's specification file as context**, plus the decision text. This is the load-bearing isolation: each role-Claude must NOT see the other roles' outputs or specifications, otherwise outputs converge to "thoughtful executive voice" regardless of role.

Implementation:
1. Determine council composition. If user invoked with no role list → use default 7 (CEO, CFO, COO, CTO, GC, CHRO, Board Chair). If user invoked with `council [list]` → use that list.
2. For each role in the composition, invoke a subagent with the Task tool (or equivalent), passing:
   - The role's `.md` file from `roles/` as context
   - The decision text verbatim
   - Output format instructions (see Phase 1 output template below)
3. Run subagent invocations in parallel where the runtime supports it (Claude Code's Task tool supports parallel invocation; serial fallback is acceptable but slower).

**Phase 1 output template (each role produces this):**

```
## [Role Title] perspective

**Verdict:** [Yes / Conditional / No / Pause / STOP]

**Top concern:** [one-sentence concern, in this role's voice and vocabulary]

**Question they would ask:** [the question this role would surface, that the team has not yet answered]

**Pushback:** [what this role would push back against — direct, in role voice, with this role's forbidden moves observed]

**Numbers / evidence cited:** [the quantitative anchor — this is mandatory; if the role can't cite something, flag it explicitly]

**Where they disagree with another role:** [mandatory — this role must identify at least one disagreement with another role's likely perspective. If unable to find legitimate dissent, flag explicitly: "I don't have meaningful dissent here."]
```

### Phase 2 — Aggregator synthesis

After all role outputs are returned, invoke a separate aggregator pass with all role perspectives + the original decision (seven for the default council; more if expansion roles are added; fewer if a custom council is composed). The aggregator's job is to synthesize, not to blend. It produces structured output in one of two formats.

**Output format A — Structured Table (default):**

See `output-formats/structured-table.md` for the canonical template. The synthesis section is mandatory and must include:
- Where the council agrees (≥4 roles aligned)
- Named disagreements (e.g., "GC says STOP; CEO says yes" — explicit who-vs-who)
- Questions not yet answered (the data the council still needs)
- Decision criteria the user should weight
- The risk no role fully owns (the orphaned concern)

**Output format B — Decision Memo:**

User invokes with `format: memo`. Aggregator produces a 1-page synthesized memo: situation, key risks, options, recommendation. See `output-formats/decision-memo.md` (deferred to v2; for v1, the structured table format is the default and only output).

## Default council composition

Seven roles, all in `roles/`:

1. **CEO** (`roles/ceo.md`) — strategic positioning, narrative coherence, long-term horizon
2. **CFO** (`roles/cfo.md`) — capital, cash, payback, scenario analysis
3. **COO** (`roles/coo.md`) — execution capacity, operational risk, scaling readiness
4. **CTO** (`roles/cto.md`) — technical architecture, build vs buy, lock-in
5. **General Counsel** (`roles/general-counsel.md`) — contractual exposure, regulatory risk, governance
6. **CHRO** (`roles/chro.md`) — people, organizational design, total rewards, cultural runway, succession; **gating voice on restructuring, RTO, layoffs, M&A integration, compensation**, and a substantive contributor to nearly every other decision (pricing, expansion, acquisitions, technology hiring)
7. **Board Chair** (`roles/board-chair.md`) — adversarial / red team / pattern detection

CHRO is in the default council, not optional. The people lens is gating in most substantive business decisions: pricing changes affect CS team capability and sales comp; M&A is a people decision masquerading as a financial one; international expansion is a hiring problem with regulatory wrapping; technical decisions create senior-IC retention issues. Treating CHRO as auxiliary produces decisions that look complete on a financial / strategic / legal axis but unwind on the people axis 6-18 months later.

Optional expansion roles in `roles/_optional/` (planned v1.1):
- **CPO** — product, customer value, roadmap
- **CRO** — pipeline, sales motion, pricing
- **CISO** — security, compliance, threat surface

User can compose custom councils for context-specific decisions. Two preset councils ship in v1: `councils/m-and-a.md` and `councils/restructuring.md` (CHRO as lead voice). Document additional custom councils in `councils/[name].md`.

## Customization

Read `docs/customization.md` for detail on:
- Editing existing role specs (30 seconds)
- Adding new roles (15 minutes)
- Creating custom council compositions (10 minutes)
- Running optional first-time configuration (`boardroom: configure`)

## What this skill does NOT do

- Does not replace actual stakeholder conversations
- Does not produce decisions; produces inputs to decisions
- Does not simulate specific real people; simulates archetypal role behavior
- Does not substitute for high-stakes red-team review

These limits are documented in the user-facing README and should be acknowledged when output value is questioned.

## Quality requirements (for development and contribution)

Outputs must pass these tests before any change to role files is merged:

1. **Blind-role test:** strip role names from output; peer should identify which output is which role correctly for ≥6 of 7 roles
2. **Forbidden-moves test:** zero forbidden-move violations in 5 example runs
3. **Dissent test:** every output shows ≥1 explicit named disagreement
4. **Quantitative-anchor test:** every output cites at least one number or threshold
5. **First-run friction test:** new user can get useful output in <60 seconds with zero setup

A formal `evals/evals.json` with positive and negative trigger cases is deferred to v2; for v1, the trigger patterns above plus the worked examples in `examples/` are the de-facto evaluation set.

## License

Apache 2.0. See LICENSE.

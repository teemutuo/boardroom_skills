# Customizing Boardroom

Boardroom is designed to be customized in three increasingly deep ways. Most users start with the first; some never go further. Choose the depth that matches your need.

## Path 1 — Tweak existing roles (5 minutes)

The default role specifications are *opinionated starting points*, not authoritative templates. Your real CFO may be ESTJ-A (commanding implementer) instead of the default INTJ-T (turbulent architect). Your COO may be more strategic than operational. Edit the role file to match.

**To tweak a role:**

1. Open the role file (`roles/cfo.md`, `roles/coo.md`, etc.)
2. Edit any of the 13 sections. Most-changed sections in practice:
   - **Vocabulary bank** — words this role uses / doesn't use. Adjust to match your industry vocabulary.
   - **Quantitative anchor** — adjust the example numbers/thresholds to match your scale (e.g., €X-cap thresholds for a Series B vs. an enterprise).
   - **Personality (OCEAN)** — adjust trait scores to match your real role-holder.
   - **Stress signals** — what specifically triggers heightened pushback in *your* business context.
3. Save. Done.

The next Boardroom run uses your edited specification automatically.

**Example — tuning the CFO role for a PE-backed company:**

In `roles/cfo.md`, replace the *Personality (OCEAN)* section with higher Conscientiousness and lower Agreeableness (PE-backed CFOs are typically more disciplined and more willing to push back than scale-up CFOs). Add to *Stress signals*: "covenant headroom under 20%, debt maturities within 18 months." Add to *Vocabulary bank*: "covenant compliance, debt service, earn-out economics, sponsor reporting cadence." The CFO output will now sound like a PE-backed CFO, not a generic startup CFO.

## Path 2 — Add new roles (15 minutes)

The seven default roles (CEO, CFO, COO, CTO, GC, CHRO, Board Chair) cover most decisions. For specific contexts, you may want roles that aren't in the default set.

Common additions:
- **Founder** (different from CEO — usually higher Openness, lower Conscientiousness, more directly invested)
- **Activist Investor** (adversarial outsider; useful for capital-structure decisions)
- **Major Customer** (their priorities, their concerns, their renewal logic)
- **Specific Country Lead** (regional perspective when international expansion is the topic)
- **Engineering Director** (more granular than CTO, for technical operating decisions)
- **Privacy Officer / DPO** (focused regulatory lens on data-handling decisions)
- **Regulator** (adversarial regulatory perspective)

**To add a new role:**

1. Copy any existing role file (e.g., `roles/cfo.md` → `roles/founder.md`)
2. Rename it
3. Edit all 13 sections to match the perspective you want simulated. Pay particular attention to:
   - **Mandate** — clear, specific, distinct from existing roles
   - **Forbidden moves** — what's out of character (most important section for distinctness)
   - **Vocabulary bank** — what words this role uses / doesn't use
   - **Quantitative anchor** — what type of number this role MUST cite
   - **Dissent requirement** — common dissent patterns with other roles
4. Save the file
5. Add the role to `roles/_index.md` so others can find it
6. Done. Invoke the role by name: `boardroom Founder: [decision]` or in custom council compositions.

**Time investment:** 15 minutes for a useful first draft. Test it on 2-3 example decisions; refine the role file based on output quality.

## Path 3 — Custom council compositions (10 minutes)

For repeated decision contexts (M&A reviews, product launches, restructuring), define named councils — preset combinations of roles for that context.

**To create a custom council:**

1. Create a new file in `councils/[name].md`
2. Inside, list the roles in the council and any context-specific instructions:

```markdown
# Council: M&A review

## Composition
- CEO
- CFO  
- COO
- General Counsel
- Board Chair
- CHRO (optional expansion role — included because people-integration matters in M&A)

## Context for the aggregator
This is an M&A council. Pay particular attention to:
- Change-of-control clauses on acquired company's customer contracts
- Cultural/integration risk in the senior team
- Synergy realization timeline
- Deal economics including earn-out
```

3. Save
4. Invoke as: `boardroom council m-and-a: [decision]`

Common council compositions worth defining:

| Council name | Roles | Best for |
|--------------|-------|----------|
| `m-and-a` | CEO, CFO, COO, GC, Chair, CHRO | Acquisition / divestiture decisions |
| `product-launch` | CEO, CPO, CRO, CFO, CTO | Product launch / pricing / GTM |
| `pricing-change` | CFO, CRO, GC (MFN!), COO, Chair | Material pricing decisions |
| `restructuring` | CEO, CFO, CHRO, GC, Chair | Workforce / cost actions |
| `fundraise` | CEO, CFO, GC, Chair, CRO | Series / round structure decisions |
| `tech-buy` | CTO, CFO, COO, GC | Vendor selection / build vs. buy |
| `int-expansion` | CEO, CFO, COO, GC, Chair | International market entry |

## Optional configuration on first run

Boardroom works immediately with smart defaults — no setup required. If you want to calibrate the council to your specific context, run:

```
boardroom: configure
```

This opens a 5-question optional calibration:
1. What kind of organization are you operating in? (listed / private / PE-backed / scale-up / family-owned)
2. What industry?
3. Approximate scale? (employees / revenue / countries)
4. Any specific real people whose perspective you want me to simulate?
5. Any roles you want to add or drop from the default 7?

Your answers save to `boardroom-config.md` in your local skill folder. All future Boardroom runs read this config automatically. Re-run configuration any time with `boardroom: configure`.

**This step is fully optional.** Most users skip it on first run and add it later when they want sharper outputs.

## What NOT to change

A few things hold the system together; changing them weakens the architecture:

- **The 13-section role file structure.** Each section is load-bearing. Skipping "Forbidden moves" or "Quantitative anchor" or "Dissent requirement" is the most common way roles homogenize.
- **The two-phase orchestration** (parallel isolated subagents → aggregator). Combining Phase 1 and Phase 2 into a single pass is the antipattern that destroys output distinctness.
- **The Board Chair as adversarial role.** Don't make it supportive. Its job is structurally enforced dissent. Soft Board Chair = no red team = decision-quality regression.
- **Mandatory dissent requirement.** Every role must identify at least one disagreement. Removing this is how outputs drift toward homogeneous consensus.

## Sharing your customizations

If you build a useful role file or council composition, contributions are welcome:

- Open a PR against `roles/_optional/` or `councils/` with your file
- Include 1-2 example outputs showing how your role/council performs
- Note the specific context where this role/council is most valuable

Not all PRs will be merged — Boardroom is an opinionated artifact, not a community framework — but useful additions for common contexts are welcomed.

## Examples of customization in action

### Example A — A founder configuring Boardroom for their Series A startup

Edits made:
- `roles/cfo.md` — changed time horizon to 6-12 months (vs. default 12-24); reduced Conscientiousness from VERY HIGH to HIGH; added "runway dynamics" to Stress signals
- Added `roles/founder.md` (using CEO as template, edited to higher Openness, more direct equity in outcomes)
- Created `councils/early-stage.md` — Founder, CFO, COO (informal), Board Chair

Result: Boardroom outputs that read as Series A-flavored, not generic-CFO-flavored. The Founder role surfaces equity-and-vision concerns; the CFO focuses on runway and burn; the abbreviated council matches the smaller real-world team.

### Example B — A CFO configuring Boardroom for their PE-backed mid-cap

Edits made:
- `roles/cfo.md` — added Personality note: "covenant-aware, sponsor-reporting cadence, exit-horizon thinking"; added "covenant headroom" and "earn-out economics" to Vocabulary bank
- Added `roles/sponsor-rep.md` (a new role: PE sponsor representative, with mandate "represent sponsor interests on capital allocation, exit timing, and management compensation")
- Created `councils/pe-portfolio.md` — CEO, CFO, COO, Sponsor Rep, Board Chair

Result: Outputs that surface the sponsor-perspective questions a typical operator would miss — exit timing implications, sponsor-reporting requirements, capital allocation in service of exit narrative.

### Example C — A regulated industry compliance lead

Edits made:
- Promoted CISO from optional to default council
- Added `roles/regulator.md` (a new role: external regulator perspective, adversarial)
- Created `councils/regulated-industry.md` — CEO, GC, CISO, Regulator, Board Chair, CFO

Result: Outputs that lead with regulatory exposure and compliance requirements, with adversarial regulator perspective surfacing what an actual enforcement action would target.

---

The customization architecture is intentionally simple: edit Markdown files. No code. No configuration syntax. No DSL. The intelligence lives in the role specifications themselves; the system orchestrates them.

If you build something interesting, send it back. The most-shared customization patterns shape what becomes standard in v2.

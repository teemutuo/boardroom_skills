# Output format: Structured table (default)

This is the default Boardroom output format. The aggregator pass produces this structure after all seven role perspectives (default council) are collected from Phase 1.

## Template

```
# Boardroom decision review

**DECISION:** [user's decision text, verbatim]

**COUNCIL:** [list of roles invoked]

---

## Role-by-role perspectives

| Role | Verdict | Top concern | Question they would ask | Pushback | Numbers / evidence cited |
|------|---------|-------------|-------------------------|----------|--------------------------|
| **CEO** | [Yes / Conditional / No / Pause / STOP] | [one-sentence concern in role voice] | [the question this role would surface that the team has not yet answered] | [what this role would push back against — direct, in role voice] | [the quantitative anchor — mandatory] |
| **CFO** | ... | ... | ... | ... | ... |
| **COO** | ... | ... | ... | ... | ... |
| **CTO** | ... | ... | ... | ... | ... |
| **GC** | ... | ... | ... | ... | ... |
| **CHRO** | ... | [people-impact concern: regretted attrition, comp precedent, cultural runway] | [the people-cohort question others won't ask] | [pushback on timelines that ignore ramp/training/change-management] | [people number: regretted attrition %, ramp time, span of control, headcount affected] |
| **Board Chair** ⚔ | [adversarial verdict] | [what the team is motivated NOT to see] | [the question the team hopes nobody asks] | [the strongest case against the decision] | [adversarial number / comparison case / asymmetric metric] |

---

## SYNTHESIS

**Where the council agrees** (≥4 roles aligned):
- [bullet]
- [bullet]
- [bullet]

**Named disagreements** (explicit who-vs-who tensions):
- [Role X says ___; Role Y says ___ — the specific tension]
- [bullet]
- [bullet]

**Questions not yet answered** (what the council still needs):
- [bullet — specific data or analysis the council needs]
- [bullet]
- [bullet]

**Decision criteria the user should weight**:
- [bullet — what this decision actually hinges on]
- [bullet]
- [bullet]

**The risk no role fully owns** (the orphaned concern):
[one paragraph — the structural risk that crosses functional boundaries and doesn't have a clear owner. Often the most important thing surfaced.]

---

*Produced by Boardroom — multi-stakeholder decision review. github.com/teemutuo/boardroom_skills*
```

## Style guidelines for the aggregator

When producing this output, the aggregator pass should:

1. **Preserve role voice in the table.** The CFO row should sound like the CFO; the GC row should sound like the GC. Don't smooth them toward a unified executive voice.

2. **Be explicit about disagreement.** Don't say "there are some differing views." Say "GC says STOP; CEO says yes pending strategic story; CFO says calculate first." Name the roles. Name the tension.

3. **Don't force consensus where none exists.** If the council is split 4-2 or 3-3, say so. Boardroom's value is surfacing legitimate tension, not resolving it.

4. **Surface the orphaned risk.** The "risk no role fully owns" paragraph is the most important part of the synthesis. It's where structural blind spots live. Take time to identify it; don't repeat what individual roles already covered.

5. **Use the user's own decision text in the header.** Verbatim. Anchors the output to what was actually asked.

6. **Cite specific numbers in the role rows.** If a role's output didn't cite a number, flag it: "[role] did not cite a quantitative anchor — output may be generic." This signals to the user that the role spec or the runtime needs adjustment.

7. **Maintain the visual hierarchy.** Role-by-role table → synthesis sections in order → orphaned risk. Don't reorder. Users learn the format and skim it efficiently.

## When to deviate from this format

Don't, generally. The format is designed to be skimmable in 30 seconds and re-readable for depth. Custom output formats fragment the user's mental model.

Two acceptable variations:

- **Decision memo format** (`output-formats/decision-memo.md`, deferred to v2) — a 1-page synthesized memo. User invokes with `format: memo`. For when the user wants a single coherent recommendation rather than the structural disagreement.
- **Single-role deep dive** — when user invokes a single role (`boardroom CFO: [decision]`), the output is just that role's perspective in extended form. No synthesis section needed.

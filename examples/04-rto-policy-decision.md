# Example 4 — Return-to-office policy decision

*This example uses the default 7-role council, with **CHRO as the lead voice** because the decision is people-led. CHRO is now part of the default council in v1 — every `boardroom: [decision]` invocation includes CHRO automatically. The `boardroom council restructuring: [decision]` invocation produces the same composition with the additional aggregator context that CHRO is the lead voice on this class of decision.*

## The decision (input)

> *We're a 350-person Series C SaaS company that has been fully-remote since 2021. Productivity metrics are flat-to-positive but board members have raised concerns about culture, mentorship of junior employees, and senior-leader visibility. CEO is proposing mandatory 3-days-per-week in-office for all employees, with a 90-day transition. We have offices in San Francisco (~120 employees within commute), New York (~80), and Austin (~60). 90 employees are remote outside these metros. Should we proceed?*

---

## Without Boardroom (typical thinking)

> Board has been clear: they want more in-person culture. The data on remote-only at this scale is mixed. Most peer companies have moved to hybrid. Three days a week is a reasonable middle ground. 90 days gives people time to plan. Let's announce it Monday.

This is the answer most CEOs arrive at after a board-pressure conversation. *It is not wrong about the strategic concern.* The board's pressure is real. Remote-only at 350-person scale has documented mentorship and culture risks.

But the framing — *"a reasonable middle ground announced in 90 days"* — is missing the dimensions where this kind of decision unwinds.

---

## With Boardroom (full council output, custom composition)

### CEO perspective

**Verdict:** Conditional — strategic case is real, but the announcement-timeline framing is wrong.

**Top concern:** We have 90 employees (26% of headcount) who are remote outside metros. Some of them relocated to lower-cost areas after 2021 with documented or implicit understanding that remote was permanent. The strategic story cannot be "everyone benefits from in-office" — for that 26%, this is a fundamental change to the deal we made with them. We need to be specific about what we're saying to them.

**Question they would ask:** "What's the 18-month positioning for the remote-outside-metro cohort? Are we (a) accepting that some of them will leave and that's the cost of the policy, (b) carving exceptions, or (c) offering relocation packages? You can pick one — but the announcement narrative has to match the policy reality."

**Pushback:** I push back on framing this as "implementation by Monday." This is an organizational decision with strategic implications across the next 24 months. The board pressure is the trigger; it's not the strategy. We owe them an analysis with options, not a policy memo.

**Numbers / evidence cited:** 26% of headcount affected differently than the rest. Strategic-narrative cost: if we lose 8-12% of staff in regretted attrition (industry comparable rates from Salesforce, Apple, Disney RTO mandates), that's 28-42 people. Replacement and re-ramp cost approximately $4-6M. The 3-year strategic question is whether the cultural value of in-person exceeds that recovery cost — and whether the recovery cost lands on the wrong people.

**Where they disagree with another role:** I disagree with the CFO if the analysis is purely cost-driven. The strategic question is what kind of company we want to be in 3 years. Cost is downstream of that.

---

### CFO perspective

**Verdict:** This is mostly cost, not benefit, in financial terms. Not a financial decision — it's a strategic decision with financial consequences.

**Top concern:** Our real-estate footprint is roughly $2.4M/year currently. Mandatory RTO doesn't change the footprint until lease renegotiations land in 2027-2028. The financial impact in the next 12 months is dominated by transition costs, not savings.

**Question they would ask:** "What's the total estimated cost of regretted attrition + replacement + ramp? Have we modeled bear case at 12% departures, base case at 8%, and bull case at 4%?"

**Pushback:** I push back on any framing that presents this as cost-neutral or cost-positive in year one. The math doesn't support that.

**Numbers / evidence cited:**
- Real-estate cost (next 12 months): $2.4M; doesn't change with policy
- Estimated regretted attrition cost (base case 8% = 28 people × $150K loaded replacement cost): $4.2M
- Productivity hit during 90-day transition (industry data: 5-8% productivity dip during major policy changes): $2-3M revenue impact
- Required real-estate capacity audit: do we even have desk capacity for 260 in SF/NY/Austin combined? Current build-out supports ~200. Capex required: $0.5-1.5M
- 12-month financial impact: roughly neutral to slightly negative (-$1 to -$3M)

**Where they disagree with another role:** I agree with the CHRO on regretted-attrition risk being the dominant variable. I disagree with the CEO if "strategic" is being used to dismiss the cost reality. The board can make a strategic case that's worth the cost; what they cannot do is make a strategic case that pretends the cost doesn't exist.

---

### COO perspective

**Verdict:** Conditional — operational machinery is not in place for a 90-day transition.

**Top concern:** Hybrid management is a different operational discipline than fully-remote or fully-in-office. Roughly 25% of our managers have never managed in a hybrid model. They will default to either treating remote and in-office reports the same (ignoring the structural asymmetry) or treating them differently (creating equity issues). Both fail.

**Question they would ask:** "Who owns the hybrid-management training rollout, on what timeline, and how do we know it landed before we enforce the policy?"

**Pushback:** I push back on the 90-day timeline. Operationally, this requires: real-estate capacity audit and remediation (60 days), manager training rollout (45-60 days), accommodation review process (30 days, GC-led), and policy alignment with our compensation framework (CHRO-led, 30 days). These can run in parallel but the floor is roughly 120 days of preparation, not 90.

**Numbers / evidence cited:**
- 350 employees × 3 days/week × 4 weeks = 4,200 person-days/month of new in-office attendance to support
- Manager population: 70 people-managers (1:5 ratio); ~25% (~18 managers) have no hybrid-model experience
- Training cost: 4-hour module × 70 managers = 280 manager-hours = ~7 weeks of one L&D person's full capacity
- Real-estate capacity gap: SF 120 / Austin 60 / NY 80 = 260 expected on peak days, current desk capacity ~200 across the three offices. Gap of ~60 desks.
- Daily attendance enforcement overhead: 1 FTE People Ops + manager time

**Where they disagree with another role:** I disagree with anyone framing the timeline as a 90-day announcement-and-go. The operational machinery isn't there. Compressing the timeline is how we lose the people on policy execution alone, before regretted attrition even kicks in.

---

### CTO perspective

**Verdict:** Adjacent risk — engineering attrition is the single biggest threat.

**Top concern:** Senior IC engineers in remote-favorable functions (platform, security, ML) have extreme leverage in the current market. They have chosen our company in part because of the remote-first deal. A mandate-and-comply approach loses senior ICs to companies still offering remote, and senior IC ramp time is 6-7 months. The cost is structural.

**Question they would ask:** "What's the expected regretted-attrition rate specifically in engineering, and have we modeled the timeline impact on the 2026 product roadmap if we lose 8-12% of senior IC capacity?"

**Pushback:** I push back on treating engineering attrition as the same as company-wide attrition. It isn't. Senior platform and security ICs are a separate market with separate elasticity. Lose six of them, and we have an 18-month roadmap problem the rest of the company doesn't see.

**Numbers / evidence cited:**
- Engineering headcount: 110 (31% of company)
- Senior IC concentration: ~30 senior+ ICs across platform, security, ML, infrastructure
- Industry data on RTO mandates in tech (2023-2024): senior IC attrition 12-18% within 12 months of mandate, ~2x company average
- Senior IC ramp time at this level: 5-7 months from offer-accept to fully productive
- Replacement cost: $200-300K loaded per senior IC, plus 6 months of productivity gap
- 2026 roadmap impact: likely 2-3 quarter slip on platform reliability investments if we lose 5+ senior platform engineers

**Where they disagree with another role:** I disagree with anyone treating "8% regretted attrition" as a uniform number across functions. In engineering, the upper end is closer to 15% — and the cost per departure is roughly 2x company average due to ramp time. The bear case in CFO's model under-prices engineering specifically.

---

### General Counsel perspective

**Verdict:** Process-gated. Cannot announce until accommodation framework and selection criteria are documented.

**Top concern:** A blanket RTO mandate without documented accommodation process exposes us to ADA cases (employees with documented disability), pregnancy-related accommodation requests, and potential disparate-impact claims. Selection criteria for any "remote-allowed" exemptions must be documented and consistent before policy goes live, or we are creating litigation surface.

**Question they would ask:** "What's the documented accommodation process? Who reviews requests, on what criteria, with what appeal path? And what's our position on employees who relocated post-2021 with written or implied agreements that remote was permanent?"

**Pushback:** I push back on any announcement timeline that doesn't include 30 days of accommodation-framework documentation and manager training on legally-compliant request handling. The policy itself is legally permissible. Implementation without process is where the legal exposure lives.

**Numbers / evidence cited:**
- Accommodation framework drafting + comp-committee + EEO review: 3-4 weeks
- Manager training on accommodation request handling: 2-hour module × 70 managers
- Litigation exposure if accommodation process is informal: median settlement in ADA hybrid-policy cases ranges $50-250K per case; class-action exposure higher
- Employees who relocated post-2021 with documented arrangement: legal review needed; some may have effective contractual claim depending on documentation
- WARN Act considerations: not triggered at this scale unless attrition is consolidated as constructive termination

**Where they disagree with another role:** I generally agree with CHRO on the people-impact dimension but I separate concerns: CHRO names the regretted-attrition risk, I name the legal-process exposure. Both are gating; neither substitutes for the other.

---

### CHRO perspective (lead voice on this decision)

**Verdict:** **Strong stop on a 90-day timeline.** The strategic case for hybrid may be sound; this implementation plan will cost us 25-40 of our best people and a culture we can't rebuild for two years.

**Top concern:** Three compounding risks the team has not modeled together. (1) Regretted attrition concentrated in our top performers — they have the most leverage and the most outside options. (2) Cultural runway exhausted — this is the fifth structural change in 18 months (board reshuffle, comp framework revision, two reorgs, now RTO); the organization's adaptive capacity is tapped. (3) Compensation precedent — whatever we do for relocation/retention sets a template we'll be answering to in every M&A and senior hire for three years.

**Question they would ask:** "Have we segmented the regretted-attrition risk by tenure, performance rating, and remote-vs-metro location? Specifically: of our top 50 performers (top 14% of company), how many are in the 90-person remote-outside-metro cohort, and what is our retention plan for them by name?"

**Pushback:** I push back firmly on the announcement-and-implement framing. People decisions of this magnitude require: segmentation of impact (not "everyone gets the same policy" but "different cohorts have different risk profiles"), individual retention plans for top performers in the affected cohorts, compensation policy alignment (relocation packages, equity acceleration for forced moves), and 60-90 days of manager training on hybrid-equity issues. None of this exists.

I push back further on the assumption that "90 days is enough notice." For employees who would need to relocate, 90 days is roughly the time to sell a house and arrange schools. That timeline is humane only if we offer relocation support. If we don't, 90 days becomes "we made it impossible to comply, then counted the departures as their choice." That's regretted attrition we caused structurally.

**Numbers / evidence cited:**
- Regretted attrition base case: 8-12% within 12 months (industry data: Salesforce 2023 ~10%; Apple 2022 RTO survey indicated 56% staff opposition; Disney 2023 ~10%; Google 2023 ~6%)
- Regretted attrition for the 90-person remote-outside-metro cohort specifically: 25-35% if no opt-out or relocation support — these are people who have already self-selected for a remote-life arrangement
- Top-performer concentration: roughly 14% of company (our top 50 by calibration). If regretted attrition disproportionately hits this cohort (it does — top performers have the most outside leverage), losing 8 of our top 50 is a different cost than losing 8 random staff
- 6+ year tenure cohort impact: ~60% of regretted-attrition cohort has 4+ year tenure based on industry data; that's institutional knowledge we cannot replace
- Cultural-runway estimate: 4 prior structural changes in 18 months. Adaptive capacity for change is depleted. Adding a fifth change without a recovery period is how organizations break.
- Compensation precedent risk: relocation package decisions will set the template for the next 6-12 senior hires and any future M&A integration. A poorly-designed package now compounds.
- Manager-effectiveness gap: ~25% of our 70 managers have never managed in a hybrid model. Without targeted training, they default to inequity (favoring in-office reports). This produces a *second* wave of regretted attrition in months 6-12.
- Required preparation timeline: accommodation framework (4 weeks, GC-led), manager training (6-8 weeks), retention conversations with named top performers (4-6 weeks), real-estate capacity remediation (8-12 weeks). Total preparation floor: 16 weeks, not 12.

**Where they disagree with another role:** I disagree with the CEO if the strategic-positioning argument doesn't address the 90-person remote-outside-metro cohort by name. "Strategic" cannot mean "we'll figure out the people implications later" — the people implications *are* the strategic implementation. I agree with CFO on the cost reality but I add: the cost is concentrated in our top performers and our 4+ year tenure cohort, which is worse than uniform attrition. I disagree with the COO's 120-day floor — it should be 16 weeks (112 days) at minimum for the people work alone, before we even touch real estate. I agree with CTO on engineering being structurally different but extend it: every function has its own leverage curve; senior CS, senior product, senior data also have outside options we haven't priced.

---

### Board Chair perspective ⚔ (devil's advocate / red team)

**Verdict:** **Pause.** This is the highest-risk decision type — board-pressure-driven with motivated reasoning on the executive team.

**Top concern:** The team is motivated toward yes because the board has been pressuring on culture. A board-pressure-driven decision made on a board-meeting timeline is the canonical structural-bias decision. The team will compress analysis, under-weight downside, and over-weight signaling to the board.

**Question they would ask:** "What's the failure case at month 18? Specifically: top-performer departures by name, engineering roadmap slip in quarters, culture recovery timeline if the change breaks adaptive capacity, and the public Glassdoor/Blind narrative our recruiting team has to fight against for 24 months. Has the team modeled that case at the same level of detail as the success case?"

**Pushback:** I push back on the entire framing. We are evaluating a binary — *RTO at 90 days, yes/no*. The actual decision space has at least four options the team has not modeled symmetrically:

1. *Mandate at 90 days as proposed* (the current framing)
2. *Mandate at 6 months with retention package + accommodation framework + manager training pre-built*
3. *"Recommended" 3-day in-office for those within commute, formal remote-allowed designation for the 90-outside-metro cohort with structured culture-investment alternative*
4. *Targeted in-person investment for high-leverage moments (annual offsites, quarterly team weeks, mentorship circles for junior employees) without a blanket attendance mandate*

The *hostile activist letter at month 18* would read: *"Series C SaaS company implemented blanket 3-day RTO on a 90-day timeline under board pressure. Lost 11% of staff in regretted attrition over 12 months, including 9 of top 50 performers and 7 senior platform engineers. Net effect: $7M in replacement and recovery cost, 2-quarter product roadmap slip, recruiting Net Promoter Score collapsed for 18 months, and the cultural-improvement KPIs the board originally wanted (mentorship, leader visibility, employee engagement) showed no measurable improvement at month 12 because the policy was implemented through coercion rather than design."*

**Numbers / evidence cited:**
- Comparison case data: Disney's 2023 RTO mandate produced ~20% staff actively considering departure per internal surveys; Apple's 2022 mandate produced 56% opposition. Most "successful" RTO mandates show culture KPIs roughly flat at month 12 vs. baseline; the case for mandate is structurally weaker than the case for designed in-person investment
- Asymmetric framing: team has detailed case for option 1 (mandate); options 2-4 not modeled
- Board-pressure-driven decisions: cohort data shows ~40% of these unwind within 24 months when not preceded by independent-analysis process. Board pressure is an input, not a decision.

**Where they disagree with another role:** I disagree with the entire council if the comparison case (options 2-4) hasn't been modeled before policy is announced. The CEO is right that the strategic question is real. The CFO is right about cost. The CHRO is right about regretted attrition concentration. The GC is right about process. The COO is right about operational floor. The CTO is right about engineering specifically. They are all right about parts. Adding the parts together: this decision is being made on a 90-day timeline because the board is in 90 days, not because the right answer requires 90 days.

---

## SYNTHESIS

**Where the council agrees** (≥4 roles aligned):
- Strategic concern is real (mentorship, culture, leader visibility at 350-person scale)
- 90-day timeline is operationally and legally insufficient for a clean implementation
- Regretted attrition is the dominant cost variable, and it concentrates in top performers and longer-tenure cohorts
- Cost of poorly-executed RTO substantially exceeds cost of a longer, better-designed implementation

**Named disagreements** (explicit who-vs-who tensions):
- **CHRO says STOP** at 90 days; **CEO** acknowledges but emphasizes strategic-narrative requirement; both gate the same decision from different angles
- **CFO** focuses on cost dimension; **CHRO** adds top-performer concentration; **CTO** adds function-specific risk (engineering 2x company average)
- **GC** gates on accommodation-framework documentation; **CHRO** gates on people-process readiness; **COO** gates on real-estate capacity and manager training; all three are valid floors and they compound
- **Board Chair** flags that the binary framing (yes/no on mandate at 90 days) excludes options 2-4 that have not been modeled; no other role pushed back on the framing
- The CEO and the implicit "the board wants this" framing are in tension; Board Chair names the structural bias explicitly

**Questions not yet answered**:
- Top-50 performer mapping by location, tenure, function, and likely-departure risk (CHRO-led, 1-2 weeks)
- Accommodation framework and selection criteria for any exemptions (GC-led, 3-4 weeks)
- Real-estate capacity audit and gap remediation plan (COO-led, 4-6 weeks)
- Manager training rollout plan for hybrid management (CHRO + L&D, 6-8 weeks)
- Engineering function-specific attrition modeling (CTO + CHRO, 2 weeks)
- Symmetric modeling of options 2-4 against option 1 (CFO + CHRO + CEO, 3 weeks)
- Compensation framework alignment for relocation, retention bonuses, equity acceleration policy (CHRO + CFO, 4 weeks)
- Cultural-runway assessment: are we adding a fifth structural change to an organization at adaptive-capacity limit? (CHRO + leadership team, 1-2 weeks)

**Decision criteria the user should weight**:
- Top-performer retention plan must exist by name before announcement
- Accommodation framework must be documented and legally reviewed before announcement
- Manager training must be deployed before enforcement
- Real-estate capacity must be audited before peak-day attendance is required
- Comparison cases (options 2-4) must be modeled and presented to the board, not just option 1
- Cultural-runway condition: if the organization has had 4+ structural changes in the prior 12 months, defer

**The risk no role fully owns**:
*Cumulative organizational fatigue from compounding structural changes, expressed not as visible attrition but as quiet disengagement that slowly degrades execution quality across all functions for 12-24 months.* The CFO sees aggregate cost; the CHRO names the regretted-attrition cost; the COO sees operational disruption; the CTO sees roadmap slip; the GC sees process exposure. But no single role is accountable for *the slow degradation of the people who stay* — the unmeasured productivity loss, the disengagement of mid-career managers who no longer trust leadership decisions, the recruiting harm that takes 24 months to surface. Board Chair flags it indirectly through the activist-letter framing; the team should assign explicit ownership to the CHRO and instrument it.

---

## What Boardroom surfaced that single-perspective thinking missed

| Concern | Surfaced without Boardroom | Surfaced with Boardroom |
|---------|----------------------------|-------------------------|
| Strategic mentorship/culture concern is real | ✅ Yes | ✅ Yes |
| Generic regretted-attrition number (8-12%) | ❌ Missed | ✅ CHRO + CFO surface |
| Top-performer concentration in attrition risk | ❌ Missed | ✅ CHRO surfaces (load-bearing) |
| 90-person remote-outside-metro cohort impact | ❌ Missed | ✅ CHRO surfaces (named cohort) |
| Engineering-specific attrition (2x company average) | ❌ Missed | ✅ CTO surfaces |
| Real-estate capacity gap (60 desks short) | ❌ Missed | ✅ COO surfaces |
| Accommodation framework requirement | ❌ Missed | ✅ GC surfaces (gating) |
| Cultural-runway exhaustion (5th change in 18 months) | ❌ Missed | ✅ CHRO surfaces |
| Compensation precedent for future hires/M&A | ❌ Missed | ✅ CHRO surfaces |
| Manager-effectiveness gap on hybrid management | ❌ Missed | ✅ COO + CHRO surface |
| Comparison cases (options 2-4) not modeled | ❌ Missed | ✅ Board Chair surfaces |
| Board-pressure-driven decision = structural-bias risk | ❌ Missed | ✅ Board Chair surfaces |

**The single most important addition:** *CHRO's segmentation of regretted-attrition risk.* Without segmentation, the team treats "8% regretted attrition" as uniform across functions, tenure, and performance. With segmentation, the team sees that the 8% is concentrated in top performers, longer-tenure cohorts, and engineering — and that the cost-per-departure is 2-3x higher in those cohorts than the average. That changes the financial model entirely and reframes the policy from "8% acceptable cost" to "loss of 9 top-50 performers and 7 senior engineers, with 18-month recovery."

**The second most important:** *Board Chair's reframing of the decision space.* The team was evaluating a binary — mandate or no mandate — when the decision space had at least four options. The single most important structural failure in board-pressure-driven decisions is collapsing the option space to "yes/no on the recommendation" rather than "what is the right design here?". Boardroom surfaces that the team is making a one-option decision while believing it is evaluating multiple options.

These together — the segmented attrition risk and the expanded decision space — are what change this from "implement the board's preferred policy on the board's timeline" to "design the right people transition with the strategic concern as input, not as conclusion."

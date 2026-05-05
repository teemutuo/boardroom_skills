# Example 3 — International expansion

## The decision (input)

> *We're a Series B SaaS company, $40M ARR, US-based, 80 employees. Board has been pushing for an international play. Specific proposal: open a UK office in Q2 2026 (4 months out) with 8 hires (1 country lead, 4 sales, 2 customer success, 1 ops). Estimated setup cost: $2M (legal entity, recruiting, lease, equipment). Year-1 run-rate: $3M (8-person team fully loaded). Current European pipeline: ~$1.5M committed/in-stage. Cash position: $25M, 14-month runway at current burn. Should we proceed with Q2 launch?*

---

## Without Boardroom (typical thinking)

> European demand is real, board is aligned, we have the runway. Let's commit to Q2 launch — start recruiting the country lead now, signal the move at next investor update.

A clean 30-second analysis. Board pressure validates the strategic frame. Cash position appears adequate. Pipeline confirms demand. *Most operators reach this conclusion within minutes.*

But the cohort data on early-stage SaaS internationalization tells a different story. Read on.

---

## With Boardroom (full council output)

### CEO perspective

**Verdict:** Strategic timing question. Depends on European pipeline density.

**Top concern:** Opening UK office at $40M ARR signals to investors and customers that we're going international. That's a strategic positioning move. But: the pipeline density right now is thin ($1.5M committed against $3M Y1 run-rate cost). Are we signaling first or validating first?

**Question they would ask:** "What's the alternative? At $40M ARR, do we open the UK office now, or do we hire a European-focused sales rep + Customer Success rep based in the US for 12 months and prove out the demand before committing to office infrastructure?"

**Pushback:** I push back on the framing that "board wants international" forces the timing. Board pressure is valid input, not a deadline. The strategic question is whether *now* is right, and the analysis is incomplete on the alternative case.

**Numbers / evidence cited:** UK office at $40M ARR represents ~7.5% capacity allocation to international ($3M/$40M). At 7.5% capacity, we expect ~7.5% revenue contribution within 18-24 months for break-even. That requires ~$3M Y2 European ARR. Current European pipeline conversion suggests realistic Y1 ARR of $2-3M, Y2 of $4-6M. The math works *if* pipeline conversion holds. It's tighter than the board narrative suggests.

**Where they disagree with another role:** I disagree with the CFO's likely "wait" response if it doesn't account for strategic timing cost. Some windows close. But I also disagree with the timeline if the alternative case (US-based EMEA rep first) hasn't been modeled.

---

### CFO perspective

**Verdict:** Cost is real; timing is questionable. Recommend phased approach.

**Top concern:** $5M Y1 cash impact ($2M setup + $3M operating) on $25M cash position is 20% of available capital. Pipeline density doesn't justify that allocation yet.

**Question they would ask:** "What's the European pipeline today and what's the realistic 12-month conversion? If pipeline is $1.5M committed and $4M in active stages, then realistic Y1 ARR is ~$1.5-2M. That makes Y1 cash payback materially negative — we burn $5M to gain $1.5-2M revenue. Can we afford that timing?"

**Pushback:** I push back on the Q2 timeline. The cash math at current pipeline density doesn't justify office infrastructure. Phased approach: 1-2 EMEA-focused reps US-based for 6-9 months, prove pipeline conversion, then open office in Q4 or Q1 next year with validated demand.

**Numbers / evidence cited:**
- Y1 cash impact: -$5M ($2M setup + $3M operating)
- Y1 expected ARR: $1.5-3M (range based on pipeline conversion)
- Y1 cash gap: -$2-4M to revenue covering operating cost
- Y2 break-even threshold: ~$3M European ARR
- Current cash: $25M ($14-month runway). Post-Q2 launch: ~$20M ($11-month runway). Tight for a Series B with no committed Series C
- Phased alternative: 2 EMEA reps US-based for 6 months, $400K total cost, expected Y1 EMEA ARR of $1-2M (similar to office case but at 8% of the cost) — gates the office investment on validated demand

**Where they disagree with another role:** I disagree with anyone framing this as "office now or never." The cash dynamics make a phased approach materially better unless there's a strategic reason the office presence specifically (vs. just sales presence) is required. Has anyone made that case?

---

### COO perspective

**Verdict:** Q2 timeline is operationally tight. Recommend Q3 minimum.

**Top concern:** Office establishment is a 6-9 month operational project (legal entity, recruiting, onboarding, processes). Q2 launch means starting the work yesterday — and we haven't.

**Question they would ask:** "Have we identified the country lead candidate? Recruited at this level (UK SaaS country lead), we're looking at 90-120 days from offer to start. If we don't have a candidate identified by today, Q2 launch is operationally impossible without compromising lead quality."

**Pushback:** I push back firmly on the Q2 timeline. The operational work to set up a UK entity (incorporation, payroll provider selection, employer-of-record setup or local entity, lease, equipment, IT, employment contracts under UK law) is 90-120 days minimum — and that's after we've made hiring decisions. We're doing both in parallel in 4 months. That's how operational integrity gets sacrificed for board optics.

**Numbers / evidence cited:**
- UK entity setup: 30-45 days legal incorporation; 60-90 days for payroll/employment infrastructure
- Country lead recruiting at SaaS scale-up scale: 90-120 days from search start to first day
- Sales rep recruiting: 60-90 days each, parallel possible if 4 reps × 1 search = 4 concurrent searches (we don't have the recruiter capacity)
- Customer Success onboarding: 30-60 days from start to billable (against existing US accounts moving to UK ownership)
- Realistic operational launch: Q3 or Q4 2026, not Q2

**Where they disagree with another role:** I disagree with the CEO framing of this as a "strategic timing" question. The strategic timing might be Q2; the operational reality is Q3 or Q4. Choose: signal Q2 and execute poorly, or signal Q3 with a realistic operational plan.

---

### CTO perspective

**Verdict:** Adjacent risks worth flagging.

**Top concern:** UK customers will surface GDPR compliance questions our US-only customer base hasn't pressured us on. Are we GDPR-compliant in product architecture or only in policy?

**Question they would ask:** "Do we have EU data residency? UK customers — especially regulated industries — will ask. If we're routing data through US servers, that's a contractual blocker for ~30-50% of European enterprise prospects."

**Pushback:** I push back on going to market in Europe before the GDPR / data-residency question is technically resolved. Sales reps will hit this in customer conversations within 30 days, and we'll lose deals because the answer isn't ready.

**Numbers / evidence cited:**
- GDPR compliance audit + remediation: typical timeline 3-6 months for a Series B SaaS without prior EU customer base
- Data residency option (EU data center or AWS EU region): 2-4 engineering quarters depending on architecture
- Cohort impact: ~30-50% of European enterprise SaaS deals require EU data residency for procurement approval
- Engineering opportunity cost: 2 quarters of platform team capacity = $400-600K opportunity cost

**Where they disagree with another role:** I disagree with launching the office before product readiness for European customers. Sales reps without product readiness lose deals AND signal weakness back to the team — bad pattern.

---

### General Counsel perspective

**Verdict:** Significant pre-launch legal work; recommend 60-day pause for structure decisions.

**Top concern:** UK employment law is fundamentally different from US (probationary periods, statutory rights, redundancy procedures, holiday entitlements, pension contributions). Setting up a UK presence requires structural decisions that have material long-term implications.

**Question they would ask:** "Are we setting up a UK Ltd entity, an EU entity for European access, using a Professional Employer Organization (PEO) like Deel, or going contractor-first? These are different legal structures with different tax, IP, and liability implications. What's the answer?"

**Pushback:** I push back on any timeline that doesn't include 60 days of structure-decision work. UK Ltd vs PEO vs contractor — these aren't paperwork choices, they're material structural decisions that bind the company for years. Brexit also complicates: UK is no longer EU, so UK entity does not give EU access. If the strategic case is European access, UK Ltd alone is insufficient — we'd need an EU entity (Ireland, Netherlands typical) for full coverage.

**Numbers / evidence cited:**
- UK Ltd setup: ~£3K + 30 days
- EU entity (Ireland/Netherlands): €5-15K setup, 45-90 days, ongoing tax compliance ~€20-30K/year
- PEO (Deel, Remote, etc.): no entity setup, 7-14 days to start hiring, but ~15-20% premium on payroll cost; suitable for 6-12 month exploration
- IP assignment risk: UK employees and contractors must have proper IP assignment language (different from US norm) — gap creates IP-ownership ambiguity
- Brexit implication: UK customers ≠ EU customers; data residency is separate question from corporate domicile

**Where they disagree with another role:** I disagree with the framing of this as a "UK office" decision. The real decision is "what European structure, what timeline, what scope" — and that decision hasn't been made. Going to UK Ltd thinking it gives EU access is a structural mistake.

---

### CHRO perspective

**Verdict:** Conditional — Q2 2026 timeline assumes UK hiring math that doesn't work, and the founding-team selection isn't scoped.

**Top concern:** A UK office of 8 people in Q2 2026 means hiring decisions in Q4 2025 — and we're already past that window if the GA target is firm. UK senior hiring runs 4-6 months search + 3 months notice (UK notice periods are structurally longer than US) = 7-9 months from search start to first day. Add 4-6 months ramp at this level. Realistic full-team productivity: Q4 2026 to Q1 2027, not Q2.

**Question they would ask:** "Who specifically runs the UK office on day 1, has that person been identified, and have they accepted? If not — and the answer is almost always 'not yet' at this stage — what's the realistic GA date once we account for UK hiring timelines? And is the founding team profile (first 3 hires) scoped, since those 3 hires set the cultural and operational foundation of the UK office for 5 years?"

**Pushback:** I push back firmly on the Q2 2026 timeline as currently scoped. The hiring math doesn't work. I push back equally on the implicit assumption that we can "find good people in London quickly" — at the senior end of this market, in the regulated-fintech segment, hiring is harder than the team is treating it. Lose the first UK leader hire and the office is set back 9-12 months minimum, with regretted attrition cascading because early UK joiners feel orphaned.

I also push back on absent compensation harmonization analysis. UK senior comp at the level we'd hire is roughly 70-80% of equivalent US comp at face value — but UK total rewards include statutory benefits (pension contributions, holiday entitlement, statutory sick pay) that materially change the comparison. Without comp-band harmonization done before the first offer, we either over-pay (setting precedent we can't sustain) or under-offer (losing candidates and signaling the UK office as second-tier).

**Numbers / evidence cited:**
- UK senior hiring timeline at this level: 4-6 months search + 3 months notice (UK statutory + market norm) = 7-9 months from kickoff to start date
- Ramp to fully productive at this level in a new market: 4-6 months
- UK senior comp (Sales / Account Director / Engineering Lead): face-value ~70-80% of US equivalent, but loaded total rewards including pension and benefits closes the gap to ~85-90%; comp-band harmonization needed before first offer
- Realistic full-productivity timeline for an 8-person UK office starting search now: 12-15 months from decision date, not 4
- Founding-team selection: first 3 hires set the office culture for 3-5 years; getting one of the three wrong is a 6-12 month setback for the whole office; getting the leader wrong is unrecoverable
- Cultural-runway risk: distance from US HQ creates "second-class office" dynamic if not designed against; manifests as 25-30% regretted attrition in months 9-18 if not actively managed
- US-based US-to-UK transfer option: 2-3 month visa timeline (Skilled Worker visa); requires UK Ltd entity with sponsor licence; not faster than a fresh UK hire when including visa work

**Where they disagree with another role:** I disagree with the CEO's Q2 2026 framing if it doesn't address the hiring-math floor — the strategic case for UK presence in Q2 may be real, but Q2 isn't on offer at the people-level scope described. I agree with the CFO that £5M Y1 cost may underestimate compensation harmonization and recruiting costs (recruiting fees in UK senior segment 25-33% of base); add this as a discrete line item. I agree with the GC that PEO is the right structure for first 6-12 months — and I add: PEO also lets us validate which UK roles are worth permanent investment before locking comp-band precedent that's hard to walk back.

---

### Board Chair perspective ⚔ (devil's advocate)

**Verdict:** **Strong skepticism on timing.** What's the rush?

**Top concern:** The motivated reasoning here is *"the board wants international."* Board input is valid; board pressure as a decision driver isn't. The team is biased toward yes because the alternative is having a hard conversation with the board.

**Question they would ask:** "What's the cost of waiting 12 months until we hit $60M ARR? Run that case explicitly. Cohort data on Series B SaaS internationalization shows 70% of companies that internationalize before $50M ARR have negative cash impact for 18+ months. We're at $40M. We're in the danger zone for this decision."

**Pushback:** I push back hard on the speed. The team has analyzed the upside (board wants this, market opportunity exists) without proportional analysis of the downside (cash burn during pipeline ramp, GDPR remediation cost, operational integration). That asymmetry is a structural decision-quality failure.

The *hostile activist letter at month 18* would read: *"Series B SaaS company opened UK office at $40M ARR with $1.5M committed European pipeline. Y1 cash burn: $5M. Y1 European ARR: $1.8M. Y2 European ARR: $3.2M. Cumulative cash gap: $4M behind plan. Core US ARR growth slowed from 30% YoY to 22% during international expansion period due to management distraction. CEO bandwidth pulled to international 25-30% of weeks. Better outcome would have been: hire 2 US-based EMEA reps at total cost $400K, validate $2M+ European ARR over 12 months, then open European entity at $60M+ ARR with full pipeline conviction."*

What's the comparison case? The team hasn't modeled it.

**Numbers / evidence cited:**
- Series B SaaS internationalization cohort data: 70% have negative cash impact for 18+ months when timing is pre-$50M ARR
- The ~30% who succeed: typically have $5M+ committed European pipeline at decision time
- Current pipeline: $1.5M committed (below the threshold for the historical-success cohort)
- Asymmetric framing: bull case modeled (3 European hires productive in 6 months), bear case (90-day onboarding, GDPR remediation delay, country lead leaves in year 1) under-modeled
- Phased alternative cost: $400K vs. $5M (12.5x cost differential) for similar Y1 expected ARR

**Where they disagree with another role:** I disagree with the council if anyone says "yes, Q2." The CFO is right about cash. The COO is right about timeline. The CTO is right about GDPR. The GC is right about structure. The CEO has correctly identified the alternative case but hasn't pushed for it. The team's bias is yes — and the cohort data says wait.

---

## SYNTHESIS

**Where the council agrees** (≥4 roles aligned):
- European market opportunity is real
- Q2 timeline is operationally aggressive
- Phased approach (US-based EMEA reps first) is materially better economics
- Multiple pre-launch work streams not yet started
- Timing is the real question; expansion itself is justifiable later

**Named disagreements** (explicit who-vs-who tensions):
- **CFO** says cost-to-pipeline ratio doesn't justify office; prefers phased approach
- **COO** says Q2 is operationally impossible without sacrificing quality
- **CTO** says GDPR / data residency must be resolved before customer-facing presence
- **GC** says structural decision (UK Ltd vs EU entity vs PEO) isn't made yet — and is material
- **CHRO** says Q2 is impossible at the *hiring-math* layer regardless of operational layer; founding-team selection isn't scoped; comp-band harmonization isn't done
- **Board Chair** says decision is structurally biased toward yes due to board pressure
- **CEO** is closest to "yes if we adjust" but acknowledges all council concerns

**Questions not yet answered**:
- European pipeline density — does $1.5M committed support office infrastructure? What's the realistic 12-month conversion?
- Country lead candidate — identified? In conversation? Started? (CHRO: typically 4-6 month search at this level, then 3-month notice)
- Legal structure — UK Ltd, EU entity, or PEO? With what timeline implications?
- GDPR compliance — current state and remediation timeline?
- UK comp-band harmonization vs. US bands (CHRO + CFO + comp committee, 3 weeks)
- Founding-team profile (first 3 hires set culture for 5 years) — scoped? (CHRO + CEO, 2 weeks)
- Phased alternative — has it been seriously costed and compared?
- Brexit implication — UK office vs. EU office for European market access; which is being chosen?

**Decision criteria the user should weight**:
- Pipeline density vs. cohort thresholds for successful internationalization (currently below historical-success threshold)
- Cash position resilience (post-launch runway should be ≥10 months; tight at current plan)
- Operational readiness for Q2 (currently absent)
- Legal-structure decision (must precede commitment)
- Comparison case results (phased approach vs. office launch)

**The risk no role fully owns**:
*Core US business growth deceleration during international expansion period.* Cohort data shows core-business growth typically slows 5-10 percentage points during the first 18 months of international expansion due to management distraction. CFO sees the cash; COO sees the operations; but no role is accountable for *modeling the core-business opportunity cost*. Board Chair flags it; team should assign explicit ownership.

---

## What Boardroom surfaced that single-perspective thinking missed

| Concern | Surfaced without Boardroom | Surfaced with Boardroom |
|---------|----------------------------|-------------------------|
| Strategic case (European demand exists) | ✅ Yes | ✅ Yes |
| Cash position adequacy at headline level | ✅ Yes | ✅ Yes |
| Pipeline-density vs. cohort threshold | ❌ Missed | ✅ Board Chair + CFO surface |
| Operational timeline (Q2 impossible operationally) | ❌ Missed | ✅ COO surfaces |
| Hiring-math timeline (Q2 impossible at people-level) | ❌ Missed | ✅ CHRO surfaces |
| Founding-team selection criticality (first 3 set culture for 5 years) | ❌ Missed | ✅ CHRO surfaces |
| UK comp-band harmonization (precedes first offer, not follows) | ❌ Missed | ✅ CHRO surfaces |
| GDPR / EU data residency requirement | ❌ Missed | ✅ CTO surfaces |
| Legal structure decision (UK Ltd ≠ EU access post-Brexit) | ❌ Missed | ✅ GC surfaces |
| Comparison case (phased approach 12.5× cheaper for similar Y1 ARR) | ❌ Missed | ✅ CFO + Board Chair surface |
| Cultural-runway risk (US-HQ distance, "second-class office") | ❌ Missed | ✅ CHRO surfaces |
| Core-business growth deceleration risk | ❌ Missed | ✅ Board Chair surfaces |

**The single most important addition:** *Phased approach modeling.* CFO + Board Chair surface that the same 12-month European ARR can likely be achieved at 8% of the cost via 2 US-based EMEA reps. This isn't a small optimization — it's a fundamentally different decision. The team would be choosing between $5M cash deployment and $400K cash deployment for similar Y1 outcomes.

**The second most important:** *GDPR / data residency requirement.* CTO surfaces that going to market in Europe without EU data residency may block 30-50% of enterprise prospects. Sales reps will hit this in month 1 of customer conversations.

**The third:** *GC's Brexit clarification.* UK Ltd entity does not provide EU access. If the strategic case is European market access, UK office alone is structurally wrong — Ireland or Netherlands entity is needed. This is the kind of detail that doesn't surface in strategic discussions but breaks at execution.

These three questions, surfaced in 60 seconds, transform the decision from "Q2 office launch" to "phased entry over 18 months with explicit gating questions answered first." That's the difference between a board-pleasing announcement that unwinds in 12 months and a measured market entry that compounds for 5 years.

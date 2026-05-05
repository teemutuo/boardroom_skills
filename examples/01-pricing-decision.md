# Example 1 — Enterprise SaaS pricing change

## The decision (input)

> *Our enterprise SaaS plan is currently $2,000/user/month. Our largest competitor (Competitor X) just raised theirs to $3,500/user/month. We have approximately 30% feature parity vs. them. We're considering raising our enterprise plan to $2,500/user/month for new contracts and applying it to renewals over the next 6 months. Currently 40 enterprise customers, 8,500 enterprise seats, ~$200M ARR contribution from this segment. Cash position: 14 months runway. Should we proceed?*

---

## Without Boardroom (typical thinking)

A founder, sales VP, or CFO thinking about this alone in 90 seconds:

> Market clearly supports a higher price. Competitor X is now 75% above us; we're 30% below the new market benchmark. Even with some logo churn, the math is favorable. Let's raise to $2,500/month — start with new logos in Q2, roll to renewals over Q3.

This is *not wrong*. The price is justified by market. But it's *incomplete* — and the incompleteness has a 25% chance of turning a +18% revenue gain into a -5% net effect. Read on for what's missing.

---

## With Boardroom (full council output)

### CEO perspective

**Verdict:** Conditional — strategic story needs work first.

**Top concern:** A 25% price increase with only 30% feature parity puts us in awkward middle-tier — neither the value play nor the premium play. The strategic story is unclear.

**Question they would ask:** "What's the 18-month positioning narrative? Are we becoming the value alternative to Competitor X, or are we closing the feature gap? You can pick one — pricing without a chosen narrative is just opportunism."

**Pushback:** I disagree with framing this as a pricing decision. It's a positioning decision. Pricing follows from positioning, not the other way around. We can't sustain a 25% price increase without a story for why our $2,500 is the right answer at our feature level.

**Numbers / evidence cited:** A 25% increase shifts our segment ARR from ~$200M to ~$235M base case. Optionality cost: locks us out of "value alternative" positioning, which would have been a $500M+ TAM with a different sales motion. We're choosing the smaller revenue gain over the larger optionality.

**Where they disagree with another role:** I disagree with the CRO's instinct (if invoked) to do this immediately. The strategic positioning question must be answered before the pricing change is announced externally. We have time; this isn't a close-the-deal moment.

---

### CFO perspective

**Verdict:** Run the math first; don't proceed without a 30-day analysis.

**Top concern:** We don't have a churn model for a 25% price increase at our feature level. Without that, the +18% revenue figure is illustrative, not actionable.

**Question they would ask:** "What's the cohort-based churn elasticity at the 25% price point? At 8% churn — bear case — do we still come out ahead at month 18? At 15% churn — extreme bear — does this turn negative?"

**Pushback:** I push back on the timeline. A pricing change of this magnitude requires base/bull/bear scenario analysis with churn elasticity modeling. We've done none of that. Without scenario analysis, we're committing to a decision based on an unmodeled assumption.

**Numbers / evidence cited:** Base case at 8% net logo churn over 12 months: +18% revenue, but new-logo CAC payback worsens from ~14 months to ~17 months because sales cycles extend. Cash impact: net positive at month 18 at base case; net negative at month 6-9 (revenue lag from longer sales cycles before renewals catch up). At 15% churn (bear case): net effect roughly flat. We have 14 months runway. If cash position is tight, the timing matters.

**Where they disagree with another role:** I agree with the CEO's positioning concern but I disagree on emphasis. The financial scenario analysis is the gating analysis, not the strategic story. Get the math first; the strategic story has to fit the math.

---

### COO perspective

**Verdict:** Conditional — Customer Success is not ready.

**Top concern:** Customer Success team will own the customer conversations defending a 25% price increase with parity-only feature set. They are not currently structured for that.

**Question they would ask:** "Who specifically owns the price-defense conversation with our top 20 customers, and have they done this before successfully?"

**Pushback:** I push back on rolling to renewals at the 6-month timeline. Customer Success requires 60 days of preparation: training on the price-defense conversation, escalation paths, retention offer parameters, churn prevention scripts. We don't have that infrastructure today. Announcing pricing before CS readiness is operationally how we lose 12% of customers we could have kept.

**Numbers / evidence cited:** Current CS team: 14 people at ~80% utilization. Price-defense conversations average 90 minutes each across 2-3 meetings. 40 enterprise customers × 2.5 hours × 3 meetings = 300 hours of CS load over the rollout period. That's 8 weeks of one CS rep's full capacity. We don't have the buffer.

**Where they disagree with another role:** I disagree with anyone (CFO, CRO, CEO) who frames this as "raise prices Q2" without the 60-day CS readiness window. The operational reality is that 60-day window or we burn 5-10% of customers we shouldn't lose.

---

### CTO perspective

**Verdict:** Adjacent risk worth flagging — but not the deciding role.

**Top concern:** Premium pricing creates premium-uptime expectations. A 25% price increase implicitly raises our SLA expectations from current 99.9% to 99.95% in the customer's mental model.

**Question they would ask:** "If we lift price to $2,500, do we publicly commit to 99.95% SLA? Have we built for that? What's the engineering investment required?"

**Pushback:** I push back on treating this as purely a commercial decision. Higher price triggers customer expectations on uptime, support response time, and feature velocity. We have ~6 months of technical debt that becomes urgent if we price into the premium tier.

**Numbers / evidence cited:** Current uptime: 99.92% trailing 90 days. Moving to 99.95% requires ~2 engineering quarters of reliability work (incident response automation, redundancy, observability). That's $500K-700K of opportunity cost in roadmap displacement.

**Where they disagree with another role:** I disagree with the CEO's framing if it ignores the technical commitment that comes with premium pricing. You can't raise prices into the premium tier and keep delivering tier-2 reliability. Either the price stays where it is, or the engineering investment in reliability must be approved.

---

### General Counsel perspective

**Verdict:** **STOP.** Full MFN audit required before any pricing change.

**Top concern:** Most enterprise SaaS contracts have most-favored-nation (MFN) clauses or price-protection language for mid-tier customers. A 25% price increase will likely trigger retroactive obligations on a meaningful portion of existing revenue.

**Question they would ask:** "Have we audited our top 50 customer contracts for MFN clauses, price-protection language, and discount-anchoring obligations? If not, this decision cannot proceed."

**Pushback:** I push back firmly on any timeline that announces pricing before MFN audit completion. This is not a process suggestion — it's a fiduciary requirement. Triggering MFN obligations without recognizing them is a material misstatement to existing customers.

**Numbers / evidence cited:** Industry data on enterprise SaaS contracts: ~60-70% have some form of MFN clause or price-protection language. If 40% of our enterprise revenue is in MFN-clause contracts, a 25% price increase could create retroactive credit obligations on $80M+ of ARR. The +18% revenue gain becomes a ~-5% net effect once MFN obligations are honored. Audit takes 4-6 weeks with outside counsel.

**Where they disagree with another role:** I disagree with all other roles' analysis if it doesn't gate on MFN audit. The strategic positioning, the financial modeling, the CS readiness, the technical investment — none of it matters if the pricing change is contractually impossible without retroactive credits. MFN exposure is the *first* gate, not a parallel concern.

---

### CHRO perspective

**Verdict:** Comp gating — sales comp framework rewrite must precede external announcement.

**Top concern:** A 25% pricing change cascades into the sales comp plan (40 sellers' quotas, accelerators, and SPIFs are all calibrated to the $2,000 ASP) and into CS retention conversations (14 reps will own price-defense work they haven't been compensated, trained, or staffed for). The team is treating this as a pricing decision; structurally it is also a compensation decision and a CS people-readiness decision.

**Question they would ask:** "Have we mapped which 4-6 CS reps carry the top-account relationships, and what's our retention plan for them by name? And has the sales comp plan been redesigned for the $2,500 tier, or are we just changing the headline price and assuming reps will figure it out?"

**Pushback:** I push back firmly on announcing externally before two things land internally: (1) a rewritten sales comp plan reflecting the new tier (target setting, accelerator math, SPIFs), and (2) named retention conversations with the top 4 CS reps. Without those, regretted attrition concentrates in the people we cannot afford to lose, and 12-month retention cohort metrics degrade in a way that takes 3 years to recover.

**Numbers / evidence cited:**
- CS team: 14 reps; top 4 carry ~60% of high-touch enterprise accounts. Top-performer concentration is the load-bearing variable
- Industry data on regretted attrition under high-stress price-defense rollouts: 10-15% of CS team within 12 months; concentrated in top quartile (the people with most outside leverage)
- Sales comp framework rewrite scope: 40 sellers, 8 SKUs, accelerator and SPIF logic — typical timeline 4-6 weeks with comp-committee review
- Compensation precedent risk: this sets the template for how every future price change cascades into sales comp. Get it wrong and we are answering to it for 3 years
- Manager capability: 4 CS managers; 0 have coached price-defense conversations at the +25% magnitude. Training requirement: ~2 weeks pre-rollout
- Replacement cost per regretted CS rep at this level: $180-240K loaded plus 4-6 month ramp; cohort relationships do not transfer cleanly

**Where they disagree with another role:** I disagree with COO's framing if "60-day CS readiness" is presented as a training problem. It's a comp + retention + training problem, in that order. Training without comp redesign produces compliance theater. I disagree with CFO if the scenario analysis doesn't include the comp-framework rewrite cost as a discrete line item; it's not free. I agree with GC's gating logic in principle and add: even if MFN audit clears, this still cannot be announced before the comp framework is rewritten and the CS retention conversations are mapped — the people-readiness window is parallel to MFN, not subordinate to it.

---

### Board Chair perspective ⚔ (devil's advocate)

**Verdict:** **Pause.** This is the structurally biased "yes" decision.

**Top concern:** The team is motivated toward yes because revenue solves a Q4 problem. The motivated reasoning is showing up as compressed analysis.

**Question they would ask:** "What's the failure case at month 18? Specifically: revenue down X%, customer count down Y%, MFN obligations recognized at $Z, CS team in retention firefight. Have we modeled that case symmetrically with the success case? If not, why not?"

**Pushback:** I push back on the speed of this decision. The team has analyzed the upside (market supports a higher price) without proportional analysis of the downside (MFN exposure, CS readiness, technical commitment, positioning lock-in). That asymmetry is a structural decision-quality failure.

The *hostile activist letter at month 18* would read: *"Company raised prices into a market where they had only 30% feature parity, ignored MFN exposure on ~40% of revenue, lost 12% of enterprise customers due to inadequate CS preparation, and committed to reliability targets they hadn't built for. Net effect: revenue contracted by 4%, churn cohort retention metrics damaged for 3 years, IR credibility dented."*

What's the comparison case? *Hold price; invest the equivalent capital in feature gap closure; raise prices in 12 months when feature parity is closer to 60%.* Has anyone modeled that?

**Numbers / evidence cited:** Cohort data on B2B SaaS pricing changes shows: ~25% of pricing increases at >20% magnitude with feature gaps result in net-negative 18-month impact when downstream effects (CS load, MFN, technical) are counted. The team's base case at +18% revenue may be the 75th percentile outcome, not the median.

**Where they disagree with another role:** I disagree with the council if anyone other than GC or CHRO says "proceed." The CFO is right about the math. The COO is right about CS capacity. The CTO is right about reliability. The CEO is right about positioning. The GC is right about MFN. The CHRO is right about comp framework and CS retention. They're all right about parts. Adding all the parts together: this decision is not ready. The team wants it to be ready because Q4 is approaching. That's the structural bias.

---

## SYNTHESIS

**Where the council agrees** (≥4 roles aligned):
- The pricing change is *eventually* justifiable — value math is real
- The current proposal is *not yet decision-ready* — multiple gating concerns unresolved
- A 6-month rollout timeline is too aggressive given preparation work required

**Named disagreements** (explicit who-vs-who tensions):
- **GC says STOP** until MFN audit completes; **CEO/CFO/COO/CTO/CHRO** all have important input but acknowledge GC's gate is logically prior
- **CFO** says math gating is primary; **CEO** says strategic story gating is primary; **CHRO** says comp framework gating is primary; all three are correct at different layers
- **COO** says 60-day CS readiness window required (capacity); **CHRO** says the readiness window is comp-redesign + retention plan + training in that order, and the training-only framing under-weights regretted attrition risk
- **CTO** says premium-pricing implies premium-reliability commitment; this was not in the original analysis
- **CHRO** says sales comp plan rewrite is a 4-6 week dependency on the critical path that the original timeline didn't include
- **Board Chair** flags structural decision-quality failure: asymmetric scenario modeling

**Questions not yet answered**:
- MFN exposure on top 50 customer contracts (legal audit, 4-6 weeks)
- Strategic positioning narrative — value alternative vs. premium value (CEO call, 30 days)
- Churn elasticity model at 25% price increase (CFO + RevOps, 2 weeks)
- CS readiness plan and timeline (COO + CS leadership, 60 days)
- Reliability investment trade-off if entering premium tier (CTO + Engineering, 2 weeks)
- Sales comp framework rewrite for the $2,500 tier (CHRO + Sales leadership + comp committee, 4-6 weeks)
- Named retention plans for top 4 CS reps and top quartile sellers (CHRO + CS / Sales leadership, 2-3 weeks)

**Decision criteria the user should weight**:
- MFN audit results (if exposure on >25% of revenue, defer pricing change)
- Strategic positioning choice (value alternative vs. closing feature gap)
- Cash position (14 months runway — is the timing pressure real or imagined?)
- CS team readiness (60-day prep is the operational floor; CHRO comp + retention work is parallel and gating, not optional)
- Sales comp framework readiness (4-6 weeks; cannot announce externally without it)
- Reliability commitment (if pricing premium, infrastructure investment is mandatory)

**The risk no role fully owns**:
*Customer Success backlash that doesn't show in numbers for 90 days but kills 12-month retention cohort metrics.* The CFO sees aggregate churn; the COO sees CS load; the CRO would see the conversation quality; the GC sees the contract; but no single role is responsible for the *3-month-lagged retention damage* that follows a poorly-executed pricing change. Board Chair flags it; team should assign explicit ownership.

---

## What Boardroom surfaced that single-perspective thinking missed

Run side-by-side, the value differential is concrete:

| Concern | Surfaced without Boardroom | Surfaced with Boardroom |
|---------|----------------------------|-------------------------|
| Market-supported price logic | ✅ Yes | ✅ Yes |
| Revenue impact estimate | ✅ Yes | ✅ Yes (with sensitivity) |
| Strategic positioning question | ❌ Missed | ✅ CEO surfaces |
| MFN clause exposure | ❌ Missed | ✅ GC surfaces (gating concern) |
| Customer Success readiness (capacity) | ❌ Missed | ✅ COO surfaces (60-day floor) |
| Sales comp framework rewrite (4-6 weeks, gating) | ❌ Missed | ✅ CHRO surfaces |
| Top-performer concentration in regretted attrition | ❌ Missed | ✅ CHRO surfaces |
| CS retention plan by name (top 4 carry 60% of accounts) | ❌ Missed | ✅ CHRO surfaces |
| Reliability/SLA commitment | ❌ Missed | ✅ CTO surfaces |
| Comparison case (hold + invest in features) | ❌ Missed | ✅ Board Chair surfaces |
| Asymmetric scenario modeling failure | ❌ Missed | ✅ Board Chair surfaces |

The single most important addition: **GC's MFN clause concern.** That alone can flip a +18% revenue decision into -5% net effect, and most operators forget about it during pricing analysis. Without the council, the team makes the decision and discovers the contractual exposure in month 3 — by which point retroactive credits are already obligated.

This is the value pattern Boardroom is built to deliver: the questions a single decision-maker doesn't think to ask, surfaced in 60 seconds, before the decision is committed.

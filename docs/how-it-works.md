# How Boardroom works — architecture explained

Boardroom is built on a simple but specific architectural pattern: **isolated parallel subagent invocation with structured aggregation**. This document explains why that pattern was chosen and how it prevents the failure mode that kills most multi-agent persona work.

## The problem this architecture solves

When you ask a single LLM "what would my CEO, CFO, COO, CTO, GC, CHRO, and Board Chair think about [decision]?" — and the LLM produces all seven perspectives in one pass within a single context window — you almost always get *one voice in different costumes*. The CFO sounds like a thoughtful executive. The CEO sounds like a thoughtful executive. The CHRO sounds like a thoughtful executive. They use slightly different vocabulary, but they reach broadly aligned conclusions. The exercise feels rich; the output is shallow.

This is the **role-contamination antipattern** in multi-agent prompting. It's documented in the academic literature (Park et al. 2023, *Generative Agents*; AutoGen GroupChat literature) and well-known to anyone who has tried building practitioner-grade multi-agent tools.

The cause is straightforward: when one model context contains all seven role specifications plus the decision, the model implicitly synthesizes across roles as it generates each one. The CFO's output is influenced by the visible CEO spec; the GC's output is colored by the COO spec it just produced. Output convergence is mechanical.

## How Boardroom solves it: sealed contexts

Boardroom uses the **orchestrator-worker pattern** described in [Anthropic's Building Effective Agents guidance](https://www.anthropic.com/research/building-effective-agents). The architecture is two phases:

### Phase 1 — Parallel isolated council members

For each role in the council composition, a separate subagent runs in a **sealed context**. That role-Claude has visibility into:

- That role's specification file (and only that one)
- The user's decision text
- The output format instructions

It does NOT see:
- Other roles' specifications
- Other roles' outputs
- Anything outside the immediate scope of its job

This isolation is what makes Boardroom different from a "multi-persona prompt." Each role-Claude is *structurally* required to think only as that role, with that role's vocabulary, with that role's forbidden moves, observing that role's quantitative-anchor requirement. There's no leakage from the CEO spec into the CFO output, because the CFO output is generated in a context that has never seen the CEO spec.

In Anthropic Skills runtime (Claude Code, Cowork mode), this is implemented via the `Task` tool — each role spawns a subagent with its own context window. In runtimes without subagent capability (Claude.ai, ChatGPT, Gemini), the portable prompt simulates isolation through structured prompt engineering: explicit instructions to the model that *each role's output must be produced as if no other role specs are visible*. Less perfectly isolated than true subagents, but functionally adequate when the role specs are themselves well-engineered.

### Phase 2 — Aggregator synthesis

After all role outputs are returned (in parallel where supported — six for the default council, more if CHRO or another optional role is included, or fewer if a custom council is composed), a **separate aggregator pass** receives all role perspectives + the original decision and produces structured output:

- Where the council agrees (≥4 roles aligned)
- Named disagreements (explicit who-vs-who)
- Questions not yet answered
- Decision criteria
- The risk no role fully owns

The aggregator's job is to *organize, not blend*. It surfaces the structural patterns across role outputs without homogenizing them. The CFO's analysis remains visibly CFO-flavored in the structured table; the GC's analysis remains visibly GC-flavored. The aggregator highlights agreement and disagreement *between* role perspectives, but does not soften either.

This separation matters: if Phase 1 outputs were aggregated within the same context (i.e., a single model produces both perspectives and synthesis), the synthesis tends to soften the disagreement to produce a coherent narrative. By running aggregation in a separate context, the disagreement is preserved and named explicitly.

## The four mechanisms that prevent role homogenization

Architecture is necessary but not sufficient. Even with sealed contexts, role outputs can converge to "thoughtful executive voice" if the role specifications themselves are too generic. Boardroom prevents this through four load-bearing mechanisms baked into every role file:

### 1. Forbidden moves (negative-space prompting)

Each role file explicitly lists behaviors *out of character* for that role. The CFO file says "does NOT use language like 'exciting opportunity'; does NOT make technical architecture recommendations." The General Counsel file says "does NOT optimize for speed over diligence; does NOT make capacity utilization arguments." The Board Chair file says "does NOT go along with consensus; does NOT make positive recommendations."

Negative-space prompting is documented in Anthropic's contrastive prompting guidance as a high-leverage technique for behavioral specificity. Telling a model what *not* to do produces sharper differentiation than telling it only what to do.

### 2. Quantitative anchors (mandatory specificity)

Each role MUST cite at least one specific number or threshold per output. CFO cites payback periods or covenant headroom. COO cites cycle times or capacity utilization. GC cites contractual exposure as percentage of revenue or regulatory penalty ranges. Board Chair cites comparison-case data or asymmetric-modeling metrics.

Without quantitative anchors, role outputs default to generic executive language. With them, role identity becomes unmistakable — a CFO output saying "covenant headroom narrows from X to Y" is structurally different from a COO output saying "current cycle time is X days."

### 3. Vocabulary banks (uses / does not use)

Each role file specifies words that role uses AND words it does not. The CFO uses "payback, IRR, NPV, covenant headroom" and does not use "exciting, transformational, no-brainer." The CTO uses "lock-in, abstraction layer, build vs. buy" and does not use "strategic positioning, payback period."

Vocabulary banks enforce voice differentiation at the language level, complementing the conceptual differentiation in mandate and decision lens.

### 4. Mandatory dissent

Every role MUST identify at least one disagreement with another role's likely perspective on every decision review. This forces structural disagreement; prevents homogenized "everyone agrees" outputs. If a role finds itself unable to identify legitimate dissent, it must flag explicitly: *"I don't have meaningful dissent here — verify by re-running with stronger devil's advocate."*

The Board Chair role inverts this: it cannot flag "no dissent." Its purpose IS dissent. If the Board Chair finds itself agreeing with the council on everything, that itself is a finding: *"Unanimous council agreement is suspicious. What are we all missing?"*

## Personality framework — Big Five (OCEAN), not MBTI

Each role spec includes an OCEAN (Big Five) personality profile: Openness, Conscientiousness, Extraversion, Agreeableness, Neuroticism. Each dimension is rated HIGH / MEDIUM / LOW with brief justification.

Big Five is the only personality framework with peer-reviewed multi-agent persona research behind it (Jiang et al. 2023, *Evaluating and Inducing Personality in Pre-trained Language Models*). MBTI has documented reliability and validity issues. Boardroom uses Big Five at the architecture layer for credibility; an optional MBTI label appears at the user-facing layer for adoption (most business leaders think in MBTI vocabulary, even where they recognize its limitations).

The personality dimension adds cognitive texture beyond functional role spec. A high-Openness CTO explores; a low-Openness CTO defends. A low-Agreeableness CFO pushes back firmly; a high-Agreeableness CFO seeks consensus. These traits show up in the output texture even when the functional analysis is similar.

Personality is fully overridable per role file. Edit the OCEAN scores to match the personality you want to simulate.

## Why this differentiates from existing tools

| Tool | Architecture | Why it differs from Boardroom |
|------|--------------|-------------------------------|
| **Custom GPTs / Persona prompts** | Single context, single persona | No multi-perspective synthesis; chat mode, not decision mode |
| **Agent Council** | Multiple LLM models providing opinions | Architectural decision focus; not designed for business-decision council |
| **CrewAI / AutoGen / LangGraph** | Multi-agent frameworks | Python framework; requires engineering investment; library not application |
| **Generic "ask my CFO/CEO" prompts** | Single context, multiple roles in one pass | Role-contamination antipattern; outputs converge |

Boardroom occupies a specific position: **practitioner-grade, business-decision-focused, structurally-isolated multi-stakeholder simulation, no-code, runs in any LLM**.

## What this architecture does NOT solve

Honest about limits:

- **It is not a substitute for actual stakeholder conversations.** Real people have private context, current emotional state, prior relationships with the question, and lived experience the role spec doesn't capture.
- **Outputs are inputs to decisions, not decisions.** The council surfaces structural perspectives; you (or your real council) make the call.
- **It simulates archetypal role behavior, not specific real people.** Your actual CFO might be wildly different from the default INTJ-flavored one. Edit the role file or it remains a generic-CFO simulation.
- **It does not replace adversarial human review at the highest stakes.** For decisions where being wrong is catastrophic, supplement Boardroom output with red-team review by people who understand your specific business.

These limits are intentional. The value is in surfacing the perspectives a single decision-maker tends to miss — not in pretending the simulator knows your business better than you do.

## Reading the architecture diagram

![Boardroom architecture](../assets/architecture.svg)

**Top:** the user's decision, in plain language.

**Middle (Phase 1):** six parallel isolated council members. Each runs in a sealed context with only its own role specification + the decision. The Board Chair runs in adversarial / red-team mode (visualized in oxblood vs. the navy of the operational roles). The note below the role boxes describes the isolation property — what makes this architecturally different from a "multi-persona prompt."

**Lower middle (Phase 2):** the aggregator pass. Receives all role outputs, produces structured synthesis: agreements, named disagreements, unanswered questions, the risk no role fully owns.

**Bottom:** the structured output — table format by default, decision memo as an alternative.

The whole flow happens in roughly 30-60 seconds in any modern LLM, depending on the runtime's parallel-subagent capability.

## Further reading

- [Anthropic — Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) — the orchestrator-worker pattern Boardroom uses
- [Anthropic — Skills documentation](https://docs.claude.com/en/docs/agents-and-tools/skills) — how the Skill format works
- Park, Joon Sung et al. (2023). *Generative Agents: Interactive Simulacra of Human Behavior.* Stanford. — foundational research on persona-based agent architectures
- Jiang, Guangyuan et al. (2023). *Evaluating and Inducing Personality in Pre-trained Language Models.* — empirical work on Big Five personality in LLMs
- Du, Yilun et al. (2023). *Improving Factuality and Reasoning in Language Models through Multiagent Debate.* — research on structured multi-agent disagreement
- Anthropic — *Contrastive prompting* guidance — the basis for negative-space prompting (forbidden moves)

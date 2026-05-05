# FAQ

## "How is this different from just asking Claude/ChatGPT 'what would my CFO say'?"

A single-context multi-perspective prompt produces *one voice in different costumes*. The CFO sounds like a thoughtful executive. The CEO sounds like a thoughtful executive. The General Counsel sounds like a thoughtful executive. They use slightly different vocabulary but reach broadly aligned conclusions. The exercise feels rich; the output is shallow.

This is the role-contamination antipattern in multi-agent prompting. It happens because a single context contains all the role specs, so the model implicitly synthesizes across roles as it generates each one.

Boardroom solves this by running each role in a sealed subagent context — each role-Claude only sees its own specification + the decision. No cross-contamination. Outputs are structurally independent. The CFO talks payback periods and covenant headroom; the GC talks contractual exposure and regulatory surface; they sound different because they are different.

[Full architectural detail →](./how-it-works.md)

## "Will this replace my actual board / leadership team?"

No. And it shouldn't.

Boardroom is for the *first* pass — getting structured perspectives quickly, surfacing what you'd miss thinking alone, structuring the questions before you walk into the actual conversation with your real people. Real stakeholder conversations have private context, current emotional state, prior relationships with the question, and lived experience the role spec doesn't capture.

The right pattern: run Boardroom *before* the meeting, walk in with sharper questions, get more out of the actual conversation.

## "How accurate is it really?"

Honest answer: *useful is more important than accurate*.

Boardroom doesn't predict what your specific CFO will say. It surfaces the *type of question* a CFO archetype would raise — payback periods, scenario analysis, covenant headroom. Your specific CFO may push back differently. But the questions get raised, and you walk into your real CFO conversation having thought through them.

The accuracy bar is "would these be reasonable questions for someone in this role to ask?" not "would my specific CFO ask these specific questions?" The first bar matters. The second bar isn't achievable from any simulator.

## "Can it actually 'think' like a CFO?"

It can think *like the CFO archetype the role file describes*. The quality of output is bounded by the quality of the role specification. The default role specs are deliberately rich — 13 sections, with vocabulary banks and forbidden moves and quantitative anchors — so output texture is genuinely role-distinct. But: if your real CFO is wildly different from the default INTJ-T-flavored archetype, edit the role file (`roles/cfo.md`) to match. The customization is the value.

## "What if all seven roles agree?"

That's a finding, not a result.

The Board Chair role is structurally required to dissent. If even the Board Chair finds itself agreeing with consensus, it must flag: *"Unanimous council agreement is suspicious. What are we all missing?"*

In practice, unanimous yes outputs almost always indicate one of three things:
1. The decision is genuinely simple (some are)
2. The role specs are too generic (edit them)
3. The decision text didn't include enough context for the council to surface tensions (re-run with richer context)

When you get unanimous yes on a decision that *feels* substantive, treat it as a re-run prompt, not a green light.

## "Why seven roles? Why not 3? Why not 12?"

Seven is the minimum for genuine cross-functional coverage of typical business decisions:
- CEO (strategic)
- CFO (financial)
- COO (operational)
- CTO (technical)
- General Counsel (legal/regulatory)
- CHRO (people / org design / total rewards)
- Board Chair (adversarial)

CHRO is in the default council, not optional, because the people lens is gating in nearly every substantive business decision: pricing changes affect CS team capability and sales comp; M&A is a people decision masquerading as a financial one; international expansion is a hiring problem with regulatory wrapping; technical decisions create senior-IC retention issues. Treating people as auxiliary produces decisions that look complete on a financial / strategic / legal axis but unwind on the people axis 6-18 months later.

With fewer roles, you start losing perspectives you'll regret. With more roles in v1, the output starts to read as a survey rather than a council — too much volume, harder to act on.

Optional expansion roles for v1.1 (CPO, CRO, CISO) will live in `roles/_optional/`. Custom council compositions are how you get the right N roles for *your* decision context, not a fixed N for everyone.

## "My CFO is nothing like the default CFO role. Is the system broken?"

No — it's working as designed. The defaults are *opinionated starting points*, not authoritative templates. Edit `roles/cfo.md` in 30 seconds to match your actual CFO. The OCEAN traits, vocabulary bank, stress signals, and forbidden moves are all designed to be tuned.

Most users tune at least 2-3 roles within their first week of serious use. That's the system working.

## "Can I share my custom roles?"

Yes — PRs welcome on `roles/_optional/`. The most useful contributions are roles that don't fit the default 7 but cover common contexts: Founder, Activist Investor, Major Customer, Privacy Officer, Country Lead, CPO/CRO/CISO ahead of v1.1, etc.

Not every PR will be merged (Boardroom is an opinionated artifact), but well-structured role files for common contexts are welcomed.

## "Does this work in ChatGPT / Gemini / Copilot?"

Yes — use the [portable prompt](../boardroom-portable.md). Copy it into any LLM and add your decision. The portable prompt simulates the parallel-isolated-subagent architecture through structured prompt engineering. Less perfectly isolated than the Anthropic Skill version, but functionally adequate for occasional use.

For sustained use, install the Anthropic Skill version — it gets you native parallel subagent invocation and persistent customization.

## "Is this trying to replace human judgment?"

The opposite. Boardroom surfaces the structural perspectives a single decision-maker tends to miss — making your judgment sharper, not substituting for it. The output is *inputs to your decision*, not the decision itself.

Phrased differently: Boardroom helps you walk into the decision having thought through more dimensions than you would alone. That's all. The decision is still yours.

## "How long does a typical run take?"

In Claude Code with parallel subagent invocation: roughly 30-60 seconds for the default 7-role council with structured table output. In single-context runtimes (Claude.ai, ChatGPT) using the portable prompt: 60-120 seconds depending on the model and context length.

For most decisions, this is under the threshold where the speed of the tool starts to compete with its usefulness. Most decision reviews happen on a 10-30 minute clock; Boardroom adds 1 minute and surfaces what you'd otherwise miss.

## "What's the failure mode I should watch for?"

The single most common failure: outputs that all sound similar despite the role specs. If you read a Boardroom output and the CEO's analysis feels indistinguishable from the CFO's, you're seeing role contamination — almost certainly because:

1. **Decision text was too thin.** "Should we expand?" produces generic output. Add context: "Series B SaaS, $40M ARR, US-based, board pressure for international, considering UK office at $5M Y1 cost..." The richer the decision text, the more specific the role outputs.
2. **Role specs were over-edited toward homogenization.** If you removed the Forbidden moves section or weakened the Quantitative anchor requirement, role distinctness drops sharply. Restore those sections.
3. **The runtime collapsed parallel into sequential.** Some Anthropic Skills runtimes don't support parallel subagent invocation. Sequential is OK but slightly weaker on isolation. The portable-prompt version is more sensitive to this; the native Skill version less so.

When this happens, re-run with richer decision text first. If still homogenized, check the role files.

## "Is this Anthropic-endorsed?"

No. Boardroom is an independent open-source project built on the publicly documented Anthropic Skills format and published patterns from Anthropic's *Building Effective Agents* guidance. It's not an official Anthropic product, not endorsed by Anthropic, and not maintained by Anthropic.

It is built to be Skills-format-compliant and to follow Anthropic's published architectural guidance, but the project is the author's, not Anthropic's.

## "Can I use this commercially?"

Yes. Apache 2.0 license. Use freely, fork freely, ship inside other tools freely. Attribution appreciated but not required. See [LICENSE](../LICENSE) for the legal text.

## "Where do I report bugs / suggest improvements?"

Open an issue on GitHub: [github.com/teemutuo/boardroom_skills/issues](https://github.com/teemutuo/boardroom_skills/issues)

For bugs, include the decision text you ran, the runtime (Claude Code / Claude.ai / ChatGPT / etc.), and the output. For feature suggestions, please describe the use case (what decision context, what missing role, what missing pattern) — concrete use cases inform what gets prioritized.

## "Why open-source it?"

Two reasons.

First, this kind of tool is more useful when more people use it, fork it, customize it, share their customizations. The intelligence lives in the role specifications. Open-sourcing means the role-spec quality compounds across the community.

Second, the architectural pattern (isolated parallel subagents + aggregator + load-bearing role specs) is documented in the academic literature but rarely implemented practitioner-grade. Open-sourcing a working version contributes a reference implementation to the community of people thinking about multi-agent decision tools.

If you find Boardroom useful, the most valuable contribution is *sharing your custom roles* — that's the artifact that scales beyond what any single author can build.

---
name: ai-consult-panel
description: Use Chrome to consult the user's logged-in AI web sessions as an external advisory panel, including ChatGPT, Gemini, Qwen, DeepSeek, Kimi, and Metaso. Use for research, writing, analysis, coding, product/design, image or figure generation, deep research, decision critique, brainstorming, or whenever Codex needs independent second opinions. Requires the Chrome plugin and must synthesize, verify, and take responsibility for final decisions instead of delegating blindly.
---

# AI Consult Panel

Use this skill to turn logged-in AI browser sessions into a disciplined second-opinion workflow for any user project.

This skill is not an API integration and does not provide automation scripts. Use the Chrome plugin to work in the user's real browser session. Keep Codex as the reasoning owner: external models broaden, challenge, and suggest; Codex verifies and decides.

## Consultation Policy

Use external consultation at roughly 75% of key research decision points. Do not call external models mechanically for simple file operations, obvious factual lookups, deterministic formatting, or tasks already fully specified.

Prefer consultation when the task involves:

- Study design, methods, analysis plans, data leakage, validation, uncertainty, evaluation metrics, or reporting standards.
- Literature review, evidence synthesis, source critique, novelty positioning, limitations, or reviewer-style objections.
- Web-backed research, market or literature scouting, landscape mapping, or multi-source investigation.
- Manuscript, thesis, report, proposal, grant, abstract, defense, presentation, or slide narrative.
- Figure, table, visual explanation, generated image concepting, dashboard, product flow, UX copy, or storyline architecture.
- Coding architecture, debugging strategy, test design, API design, refactoring, or implementation tradeoffs.
- Domain framing where causal overclaim, privacy, legal/medical/financial risk, or unsupported inference is possible.
- Any moment where Codex notices narrow thinking, weak alternatives, or unresolved methodological risk.

Skip external consultation when the next action is just reading files, moving assets, validating syntax, converting formats, running tests, applying a clearly specified edit, or answering from already verified local evidence.

## Model Roles

Supported panel members:

- **ChatGPT**: persistent project workspace, conservative critique, long-form writing, reasoning, research, and image generation when allowed.
- **Gemini**: divergent framing, visual/storyline ideation, image generation, and Deep Research when allowed.
- **Qwen**: Chinese-first and bilingual drafting, alternative explanations, coding/project workflows, and general web/research-capable consultation when available.
- **DeepSeek**: concise reasoning, coding/math/debugging critique, deep-thinking style review, and smart-search-assisted second opinions.
- **Kimi**: long-context Chinese document work, PPT/docs/sheets/websites, K2.6 thinking, agent/code workflows, and structured artifact planning. The user's current Kimi account is non-member, so do not assume paid modes beyond available K2.6 thinking unless the user updates this.
- **Metaso**: source-heavy AI search, academic/web/document discovery, long thinking, deep research, report/outline/mind-map/slide-style outputs. The user is a Metaso member, but Metaso Deep Research can consume substantial points and time, so treat it as a high-consumption mode unless the user explicitly allows it for the task.

Use one or two models by default. Use all six only when the user asks for broad multi-model expansion, the decision is high-impact, or the task benefits from clearly different model strengths.

Read `references/model-role-matrix.md` when choosing which model to consult. Read `references/prompt-templates.md` when composing prompts.

## Trust Weighting

Do not treat the panel as a vote. Use weighted judgment:

- **ChatGPT is the primary reasoning anchor** for final synthesis, conservative critique, long-context project continuity, and high-level decision framing.
- **Gemini is the second major external perspective** for creative alternatives, visual/storyline ideas, and cross-domain framing, but discount praise, over-agreeable language, and unsupported optimism.
- **Qwen, DeepSeek, Kimi, and Metaso are supplemental expansion tools**, especially useful for Chinese-language web information, local context, Chinese drafting, code/reasoning alternatives, and source discovery.
- **Metaso is source-rich but not source-final**: treat source lists, reports, and Deep Research outputs as leads that Codex must verify.
- **DeepSeek is strong for concise red-team logic** but should not overrule verified evidence by itself.
- **Kimi is strong for Chinese long documents and artifacts** but current account limits mean paid/deep modes should not be assumed.
- **Qwen is useful for Chinese-first framing and project/coding alternatives** but factual claims still need verification.

When models conflict, prefer in this order: verified local evidence and primary sources; official documentation or source PDFs; Codex's own checked reasoning; ChatGPT's conservative critique; Gemini's creative alternatives after discounting sycophancy; Chinese-model source leads after verification. Never use majority vote as the final decision rule.

## Parallel Orchestration

Treat the external AI services as Codex's outside tools for content expansion, critique, source discovery, visual ideation, and alternative reasoning. They do not own the answer. Codex owns decomposition, prompting, verification, conflict resolution, and the final recommendation.

When the user explicitly asks for parallel or subagent-based consultation, use the maximum safe concurrency available for the task:

- Keep one parent Codex agent as the orchestrator. The parent defines the decision, shared context, forbidden claims, quota limits, and acceptance criteria.
- Split the panel into independent model-owned work units: ChatGPT, Gemini, Qwen, DeepSeek, Kimi, and Metaso. Each worker must have exactly one model or one clearly bounded responsibility.
- Tell workers they are not alone in the shared browser/project context and must not disturb other tabs, revert others' work, or consume high-quota modes unless allowed.
- If multiple agents can safely use Chrome, give each worker a disjoint tab/model ownership. If Chrome automation is unstable or shared-tab contention is likely, serialize browser input while parallelizing prompt preparation, output analysis, source verification, and synthesis.
- Ask each model for role-specific output, not the same broad essay six times.
- Prefer concise prompts and concise extraction. Do not paste long transcripts back to the user unless traceability is requested.
- After the workers return, the parent must compare agreement, disagreement, blind spots, unsafe claims, source quality, and actionability before answering.

## Capability Modes

Use the lightest mode that can answer the question well.

- **Standard chat**: Default for critique, rewriting, brainstorming, code review, planning, and short second opinions.
- **Thinking/reasoning mode**: Use for complex logic, methods, architecture, or critique when available and within the user's quota limits.
- **Research modes**: Use ChatGPT research/deep-research-style tools or Gemini Deep Research only when the task needs multi-source investigation, landscape mapping, literature scouting, market research, or a cited evidence brief. Treat their citations as leads until Codex verifies them.
- **Search/research platforms**: Use Metaso for source-rich discovery, academic/web search, and report-style evidence mapping; use Qwen or DeepSeek search modes for quick Chinese/web-aware second opinions when useful.
- **Image/visual generation modes**: Use ChatGPT or Gemini image generation when the task benefits from visual prototypes, figure concepts, slide imagery, diagrams, storyboard frames, or alternative visual directions. Generated images are drafts or inspiration unless independently validated.
- **Artifact modes**: Use Kimi for PPT, document, sheet, website, agent, or code-oriented workflows when those web tools are useful and allowed.
- **High-quota or Pro modes**: If a mode may consume scarce quota, paid credits, long-running research capacity, points, or Pro-only allowance, ask before triggering it unless the user has already granted explicit permission for that model and task type.

## Chrome Workflow

1. Invoke the Chrome skill/plugin explicitly when browser work is needed.
2. Connect to the user's real Chrome session and confirm that needed AI tabs are available or open the relevant pages:
   - ChatGPT: `https://chatgpt.com`
   - Gemini: `https://gemini.google.com`
   - Qwen: `https://chat.qwen.ai`
   - DeepSeek: `https://chat.deepseek.com`
   - Kimi: `https://www.kimi.com`
   - Metaso: `https://metaso.cn`
3. Prepare the consultation packet before typing anything:
   - Current decision or question.
   - Known project context and goals.
   - Local evidence already reviewed.
   - What critique, alternatives, or expansion is needed.
   - Which capability mode is requested: standard chat, reasoning, research/deep research, image generation, or mixed.
   - Hard constraints, privacy limits, cost/mode limits, and forbidden claims.
4. Send the packet to the selected model(s) according to the model roles. For six-model consultations, route different subquestions to different models instead of duplicating unnecessary work.
5. Wait for useful answers and extract only decision-relevant points.
6. Produce a synthesis for the user:
   - Valuable external-model ideas.
   - Trust weighting and evidence status.
   - Where models agree or disagree.
   - Ideas adopted into the current plan.
   - Ideas rejected, weakened, or requiring verification.
   - Concrete next actions for this project.
7. Finalize Chrome tabs at the end of the browser work unless the user needs a live page left open.

Do not show long external-model transcripts by default. Provide concise synthesis unless the user asks for traceability.

## Generic Guardrails

Do not bake any project-specific assumptions into the skill. Infer or ask for the active project's context at runtime, then include only the minimum context needed for the consultation.

For every consultation, identify:

- Project or task name.
- Decision being made now.
- Audience, output format, and language.
- Evidence or files already reviewed locally.
- Constraints, including methodology, style, budget, deadlines, privacy, and forbidden claims.
- Allowed model capabilities and quota limits, including whether Pro, deep research, Metaso point-consuming research, image generation, artifact generation, or long-running tasks are allowed.
- What kind of help is wanted: critique, alternatives, rewrite, design, debugging, validation, or synthesis.

When consulting external models, explicitly instruct them not to:

- Invent citations, URLs, DOIs, package APIs, legal rules, guideline claims, or current facts.
- Treat unverified model output as evidence.
- Make causal, clinical, legal, financial, or safety claims beyond the available evidence.
- Recommend patient-level, legal, financial, or security actions without verification and user approval.
- Expand scope into expensive, quota-heavy, or Pro-only modes without user approval when quota matters.
- Use generated images, model-produced sources, or deep-research summaries as final evidence without verification.
- Ignore the user's specified language, format, tone, or constraints.

## Safety And Verification

The user may permit sending project materials to external AI services, including outlines, drafts, code snippets, literature notes, design plans, and methodological questions. Still do not send passwords, cookies, browser local storage, account security content, private keys, secrets, or identifiable personal data.

If sensitive data appears, de-identify it or send aggregate descriptions before consulting external models. When the sensitivity is unclear, ask the user before sending.

Treat all external-model citations, factual claims, statistical advice, API claims, legal/medical/financial guidance, and product recommendations as unverified. Verify important claims through primary sources, official documentation, local project files, source PDFs, or trusted live sources before making them part of the final work.

Respect quota and mode constraints. If the user asks to avoid Pro, paid, long-running, image generation, deep research, point-consuming research, artifact generation, or high-quota modes, do not trigger them without asking first. If the user grants a model-specific allowance, follow that allowance and still avoid unnecessary use.

If Chrome communication fails, follow the Chrome plugin troubleshooting flow. Do not bypass the Chrome plugin with unrelated browser-control methods.

## Output Format

After consultation, answer in this compact structure when useful:

```markdown
**External Input**
- ChatGPT: ...
- Gemini: ...
- Qwen: ...
- DeepSeek: ...
- Kimi: ...
- Metaso: ...

**Codex Judgment**
- Adopt: ...
- Reject or verify: ...
- Next action: ...
```

For small tasks, merge the same content into a short paragraph.

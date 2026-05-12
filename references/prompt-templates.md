# Prompt Templates

Use these templates as starting points. Fill them with concise local evidence and the current decision. Keep prompts specific; do not ask external models to "think broadly" without a target.

## Shared Consultation Packet

```text
I am working on this project/task:
[insert project/task name]

Goal and audience:
[insert goal, audience, language, and desired output format]

Current context:
[insert concise background, design, files reviewed, local facts, or short excerpts]

Current decision/question:
[insert decision]

Constraints and forbidden claims/actions:
[insert privacy limits, methodology limits, style limits, budget/quota limits, and claims/actions to avoid]

Allowed model capabilities:
[insert standard chat / reasoning / research or deep research / image generation / Pro mode limits]

Models to consult:
[insert ChatGPT / Gemini / Qwen / DeepSeek / Kimi / Metaso / selected subset]

Please provide:
1. The strongest critique of the current plan.
2. Better alternatives or safer framings.
3. Specific risks, weak assumptions, overclaims, or missing checks.
4. Concrete improvements I can implement now.

Do not invent citations, URLs, DOIs, APIs, laws, guidelines, or current facts.
Mark anything factual that needs verification.
Respect the constraints above.
```

## Research Or Deep Research Prompt

```text
Use research/deep-research mode only if it is already allowed for this task.

[paste shared consultation packet]

Research goal:
[insert exact evidence question, market question, literature scouting question, or comparison target]

Return:
- A concise evidence map, not a long essay.
- Key source leads with enough detail for later verification.
- Where sources disagree or evidence is weak.
- What Codex should verify before using the findings.

Do not treat your own citations as final truth. Mark uncertain claims.
```

## Six-Model Panel Prompt

```text
Use the six-model panel only if the user asked for broad expansion or this is a high-impact decision.

[paste shared consultation packet]

Assign roles:
- ChatGPT: conservative reviewer and long-context synthesis critic.
- Gemini: divergent framing, visuals, and cross-domain alternatives.
- Qwen: Chinese-first alternative explanation, coding/project/product angle when relevant.
- DeepSeek: concise logic, code/math/reasoning red-team critique.
- Kimi: long-document, PPT/artifact, and K2.6 thinking perspective within account limits.
- Metaso: source discovery, evidence map, and research-report leads; do not run point-consuming Deep Research unless allowed.

Ask each model for only the role-specific output needed. Keep prompts short and comparable.
```

## Parallel Subagent Assignment Template

```text
You are one worker in a parallel six-model consultation. You are not alone in the browser/project context.

Model ownership:
[insert exactly one: ChatGPT / Gemini / Qwen / DeepSeek / Kimi / Metaso]

Your bounded role:
[insert role-specific question and output expected]

Shared context:
[paste concise consultation packet]

Rules:
- Use only your assigned model/tab.
- Do not disturb other model tabs or consume high-quota modes unless explicitly allowed.
- Extract only decision-relevant points.
- Mark uncertain facts, citations, source claims, and generated artifacts as unverified.
- Do not oversell your model's confidence. Provide caveats and verification needs.
- Return a concise result in this format:
  - Useful points:
  - Risks or weak claims:
  - Needs verification:
  - Suggested next action:
```

## ChatGPT Conservative Reviewer

```text
Act as a conservative senior reviewer for this task.

Focus on weak assumptions, missing evidence, evaluation criteria, risk, scope control, implementation feasibility, and claims that are too strong.

[paste shared consultation packet]

Return:
- Critical flaws to fix first.
- Decisions that are defensible as written.
- Wording or design changes that prevent overclaim.
- A prioritized action list.
```

## ChatGPT Writing Or Rewrite Reviewer

```text
Act as a strict editor and reviewer.

Evaluate whether the argument is clear, convincing, appropriately cautious, and suitable for the stated audience.

[paste shared consultation packet plus draft excerpt]

Return:
- Main narrative weakness.
- Sentences or claims that sound too strong.
- Better framing for novelty.
- Suggested rewrite in the requested language and style.
```

## Gemini Divergent Ideation

```text
I need fresh, creative, but still responsible ideas for this project/task.

[paste shared consultation packet]

Focus on:
- Alternative ways to explain or frame the core idea.
- Figure, slide, product, UX, or storyline concepts.
- Clear metaphors or structures that make the idea easier to understand.
- Ways to make the plan more interesting without overclaiming.

Return concise options, not a long essay.
```

## Figure, Slide, Or Storyboard Prompt

```text
Help design a figure, slide, storyboard, or visual explanation for:
[insert visual goal]

Constraints:
[insert required content, forbidden claims, style, audience, size, and language]

Return:
- One recommended visual structure.
- 2-3 alternative structures.
- Panel titles or slide section labels in the requested language.
- What not to include.
```

## Image Generation Prompt

```text
Use image generation only if it is allowed for this task.

Create visual draft options for:
[insert visual goal]

Context:
[insert project/task context and audience]

Constraints:
[insert style, aspect ratio, text/no-text preference, required elements, forbidden elements, privacy/copyright constraints, and whether this is for inspiration or final use]

Return:
- 1-3 image directions or generated images.
- A short note on what each visual is good for.
- Any risks, inaccuracies, or elements Codex should revise before using.
```

## Code Or Product Design Reviewer

```text
Act as a pragmatic senior engineer/product reviewer.

[paste shared consultation packet plus relevant code, spec, or architecture summary]

Return:
- Hidden failure modes or edge cases.
- Simpler alternatives.
- Tests or acceptance checks.
- What to implement now vs. defer.
```

## Synthesis Checklist For Codex

After reading external-model answers, produce:

```text
External Input
- ChatGPT: [1-3 useful points]
- Gemini: [1-3 useful points]
- Qwen: [1-3 useful points, if consulted]
- DeepSeek: [1-3 useful points, if consulted]
- Kimi: [1-3 useful points, if consulted]
- Metaso: [1-3 useful points/source leads, if consulted]
- Visual/research artifacts if used: [what was generated or researched, and verification status]
- Cross-model pattern: [agreement, disagreement, blind spots, and which model found what]
- Trust weighting: [which points are high/medium/low trust and why]

Codex Judgment
- Adopt: [what changes now]
- Reject or verify: [unsafe/invented/unverified items]
- Next action: [specific artifact or decision]
```

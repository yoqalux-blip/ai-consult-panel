# Model Role Matrix

Use this reference to choose how to consult logged-in AI web sessions through the user's Chrome browser.

## ChatGPT

Trust weight: primary reasoning anchor.

Best for:

- Persistent project memory when the user has a project workspace or ongoing conversation.
- Conservative critique of research design, analysis plans, assumptions, evaluation, validation, and reporting.
- Research or deep-research-style investigation when the user needs a structured evidence brief, landscape scan, or source lead list.
- Long-form rewriting, chapter/section restructuring, paragraph-level argument refinement, and tone control.
- Code architecture critique, debugging strategy, test planning, and implementation tradeoffs.
- Discussion, limitations, novelty positioning, product requirements, review responses, and adversarial objections.
- Image generation or visual draft exploration when the user wants concept images, slide visuals, figure directions, or storyboard alternatives and ChatGPT's image mode is appropriate.
- Keeping separate conversations for major streams such as methods, evidence, implementation, writing, figures, and presentation.

Avoid using ChatGPT as:

- A source of final factual truth without verification.
- A replacement for local project files or primary literature.
- A judge of high-stakes patient, legal, financial, security, or account decisions.
- A way to trigger Pro, paid, research, image, or other high-quota modes when the user has restricted quota.

## Gemini

Trust weight: high creative value, secondary decision weight.

Best for:

- Fresh-task divergent thinking.
- Alternative figure, storyline, product, UX, presentation, or narrative concepts.
- Gemini Deep Research for broad landscape scans, comparative research, and source discovery when the user allows long-running research.
- Visual metaphors, slide logic, defense or pitch narrative, and plain-language framing.
- Image generation or visual ideation when the user wants multiple visual styles, draft imagery, figure metaphors, or storyboard concepts.
- Cross-field analogies and ways to explain technical or domain-specific ideas.
- Independent critique that is less influenced by the accumulated ChatGPT project context.
- Quick generation of multiple options before Codex chooses and verifies.

Avoid using Gemini as:

- The long-term source of project state.
- The only reviewer for methods, statistics, code correctness, or high-stakes claims.
- A citation authority without primary-source checks.
- A way to bypass quota or mode limits the user has set.
- A source of reassurance without adversarial checking; discount overly agreeable or flattering conclusions.

## Qwen

Trust weight: supplemental, especially for Chinese-first framing and local web-aware alternatives.

Observed current workspace: Qwen Studio with Qwen3.6-Plus, automatic mode, Coder, projects, community, and research/search-related capability hints.

Best for:

- Chinese-first or bilingual drafting, polishing, alternative phrasing, and local-context explanation.
- Coding, product, project, and structured planning tasks where a second implementation path is useful.
- Fast alternative reasoning or web-aware Chinese perspective when Qwen search/research modes are available.

Avoid using Qwen as:

- The sole source for current facts, citations, or product claims.
- A replacement for official docs, local code inspection, or primary literature.
- A high-consumption research tool unless the active mode and quota impact are clear.

## DeepSeek

Trust weight: supplemental red-team logic and code/math critique.

Observed current workspace: expert mode is available, with quick mode, deep thinking, and smart search controls.

Best for:

- Concise reasoning, math, coding, debugging, and algorithmic critique.
- Red-team review of logic, assumptions, edge cases, and implementation tradeoffs.
- Quick search-assisted second opinions when smart search is enabled and citations will be verified later.

Avoid using DeepSeek as:

- The only source for evidence, citations, medical/legal/financial claims, or current facts.
- A long-context project memory store.
- A source of final decisions without Codex synthesis.

## Kimi

Trust weight: supplemental for Chinese long-context thinking and structure critique.

Observed current workspace: the user's Kimi account is non-member. `Kimi 2.6` thinking is available. The sidebar exposes PPT, documents, deep research, websites, sheets, Agent cluster, Kimi Code, and Kimi Claw, but those visible entries should be treated as possibly membership-only, paid, quota-limited, or unavailable unless the user confirms otherwise.

Best for current non-member use:

- `Kimi 2.6` thinking as a text consultant for Chinese long documents, PPT structure, outlines, and expression critique.
- Chinese narrative organization, slide logic, section hierarchy, and document restructuring suggestions.
- Careful Chinese reasoning within available free-account limits.

Best for paid-member use, only after user confirmation:

- PPT, document, sheet, website, Agent, Kimi Code, Kimi Claw, or other artifact workflows that require membership or paid quota.
- Richer long-document, artifact planning, or agent/code workflows when the user explicitly allows the relevant paid feature for the task.

Avoid using Kimi as:

- A paid/deep/artifact mode unless the user confirms membership or availability and approves the current task.
- A reason to assume visible UI features are actually usable on the current account.
- The only verifier for sources, code correctness, or high-stakes claims.
- A place to send sensitive files without de-identification and user approval.

## Metaso

Trust weight: supplemental source-discovery engine; high value for Chinese web and academic leads, low value as final truth without source checks.

Observed current workspace: the user is a member. Metaso exposes AI search, all-web/document/academic/image/video/podcast search surfaces, long thinking, concise/deep modes, Deep Research, source lists, reports, outlines, mind maps, and slide/report-style follow-ups. A short Deep Research test consumed substantial points and time, so treat it as high-consumption.

Best for:

- Source-heavy web, academic, document, and landscape discovery.
- Producing evidence maps, source leads, reports, outlines, mind maps, and research brief drafts.
- Finding Chinese sources and broad web leads that Codex will later verify.

Avoid using Metaso as:

- A casual chat model when a lighter model is enough.
- A source of final truth without checking original sources.
- A default deep-research engine without user approval because it can consume points and run for minutes.

## Use Multiple Models

Consult multiple models when:

- A decision affects project direction, methods, architecture, evidence claims, public-facing writing, or deliverable structure.
- Codex needs both conservative methodological critique and creative alternatives.
- A project needs both research-backed evidence leads and visual/storyline exploration.
- The user asks for broad thinking or says Codex's current thinking feels limited.

Use all six when:

- The user explicitly asks for the six-model panel.
- A high-stakes direction decision needs conservative critique, divergent ideation, source discovery, coding/product review, and Chinese-language framing.
- Codex needs to compare model disagreement before making a synthesis.

## Parallel Panel Rule

When the user asks for parallel/subagent consultation, the parent Codex agent remains the orchestrator and assigns disjoint model ownership:

- ChatGPT worker: conservative critique, long-context reasoning, writing/research/image mode if allowed.
- Gemini worker: divergent alternatives, visual/storyline framing, image or Deep Research mode if allowed.
- Qwen worker: Chinese-first alternatives, coding/project/product angle, quick web-aware framing.
- DeepSeek worker: logic, code/math, failure modes, concise red-team critique.
- Kimi worker: `Kimi 2.6` text-thinking consultation for Chinese long-document/PPT structure by default; paid artifact tools only if the user confirms membership and allows them.
- Metaso worker: source discovery, evidence map, report/outline/mind-map leads; do not use point-consuming Deep Research unless allowed.

Use real browser parallelism only when tabs are disjoint and stable. Otherwise serialize Chrome operations and parallelize non-browser work such as prompt drafting, extracted-output analysis, verification, and synthesis. Never allow workers to make the final decision independently.

Consult only one when:

- The task is time-sensitive and one model's role clearly fits.
- The question is mostly visual or narrative: prefer Gemini.
- The question is mostly deep evidence gathering: use the model's research mode only if the user has allowed it.
- The question is mostly visual artifact generation: use image generation only if a generated visual is genuinely useful.
- The question is mostly methods, accumulated project context, strict critique, code architecture, or detailed rewriting: prefer ChatGPT.
- The question is mostly Chinese source discovery or academic/web evidence mapping: prefer Metaso, then verify sources.
- The question is mostly Chinese long-document or PPT-structure thinking and Kimi free-account limits are acceptable: prefer Kimi 2.6 text consultation.
- The question is mostly concise code/math/logic red-team critique: prefer DeepSeek.
- The question needs Chinese-first alternative framing or coding/project perspective: consider Qwen.

## Mode And Quota Rule

Default to standard chat or lightweight reasoning. Before using Pro, deep research, long-running research, point-consuming research, image generation, artifact generation, Kimi membership-only functions, or other quota-heavy modes, check the user's standing preference for that model. If unclear, ask first and name the tradeoff.

## Synthesis Rule

Never paste model outputs together as the answer. Convert them into a decision:

- What is genuinely useful?
- Where do models agree, disagree, or reveal each other's blind spots?
- Which claims deserve high, medium, or low trust?
- What conflicts with local evidence?
- What is attractive but unsafe?
- What needs source verification?
- What should change in the project artifact now?

Apply this trust order:

1. Verified local evidence, primary sources, source PDFs, official documentation.
2. Codex's checked reasoning and reproducible local work.
3. ChatGPT's conservative critique and long-context synthesis.
4. Gemini's creative alternatives after discounting sycophancy and unsupported optimism.
5. Qwen, DeepSeek, Kimi, and Metaso as supplemental perspectives, Chinese-web/source leads, local-language framing, artifact ideas, and red-team checks.

Do not decide by majority vote. Prefer verified evidence over model confidence.

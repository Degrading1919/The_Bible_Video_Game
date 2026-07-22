# Effective Skill Anatomy and Authoring Principles

Artifact file: [Download the session markdown output](sandbox:/mnt/data/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md)

## Evidence base and scope

This session could not directly access the project-private files named in the prompt from the tools available in this chat, so the project-specific portions of the analysis are necessarily limited to public, verifiable material rather than those internal Bible Video Game documents. The research therefore grounds its findings in primary OpenAI documentation, the official `openai/skills` repository, the open Agent Skills specification, and first-party prompting and governance guidance. Where I make a recommendation rather than report an explicit source statement, I label it as a recommendation or inference. citeturn25view1turn38view0turn34view0turn22view4turn10view2

The strongest public evidence comes from how skills are actually defined and routed today. OpenAI’s Skills guide defines a skill as a **versioned bundle of files** with a `SKILL.md` manifest, and says the runtime exposes only each skill’s `name`, `description`, and `path` at first; the model then decides whether to invoke the skill and reads the full `SKILL.md` only after selection. The Build Skills documentation for Codex says the same thing in product terms: skills use progressive disclosure, the initial skills list is context-budgeted, and long descriptions may be shortened or omitted from the initial list when many skills are installed. citeturn25view1turn26view0turn38view0

I also audited current official skill files and their repository history, because the user asked for actual skill-file evidence rather than popularity or marketing claims. The sample included the built-in `skill-creator` (`368` total lines shown on GitHub; latest audited commit `4ab6e0fd99c6667163bc34173e3ed3a3fed75ebc`, February 9, 2026), `openai-docs` (`161` lines; commit `da7611f0ddb078b641407842473e4fa308988516`, April 24, 2026), `define-goal` (`99` lines; commit `b0401f07213a66414d84a65cb50c1d226f99485a`, May 21, 2026), `security-threat-model` (`81` lines; commit `5c8f1e26803bcfaffeceef1e7accbcf7e388417a`, February 2, 2026), and `figma-implement-design` (`258` lines; commit `0e7823cca07bc2cbf34718a383f9ae92525be6a5`, March 24, 2026). That range matters: the official examples are not tiny one-liners, but they are also not encyclopedic dossiers. citeturn34view0turn36view0turn15view0turn21view0turn15view2turn21view2turn15view1turn21view1turn15view4turn17view0

One important contradiction in the evidence should be stated up front. The open Agent Skills specification allows optional frontmatter such as `license`, `compatibility`, `metadata`, and `allowed-tools`; however, OpenAI’s own `skill-creator` guidance says the Codex-facing frontmatter should contain only `name` and `description`, because those are the fields Codex reads for routing. In practice, that means a future Bible Video Game skill-builder should probably target the **conservative Codex subset first**, and only emit richer frontmatter after validating that the current runtime and validator actually use it the way the project expects. citeturn23view0turn23view2turn34view0

## Effective-skill thesis

### Findings

An effective reusable skill is **not** merely a long prompt. It is a **routable operating contract** with four distinct properties.

First, it is **discoverable**. The runtime sees a small metadata surface first and uses that to decide whether to pull in the full instructions. That makes the `name` and especially the `description` the routing surface, not just documentation. If invocation is wrong, the rest of the skill does not matter. citeturn26view0turn22view3turn38view0

Second, it is **progressively disclosed**. The body should contain only the instructions the model needs on every activation, while detailed references, scripts, and assets stay outside the primary file until needed. Both the open specification and OpenAI’s built-in `skill-creator` explicitly recommend this pattern, including keeping the main `SKILL.md` under roughly 500 lines and pushing bulky detail into `references/`, `scripts/`, and `assets/`. citeturn24view0turn22view2turn34view0

Third, it is **operationally bounded**. Good skills define scope, non-goals, approval points, stopping rules, and output requirements so the agent can proceed autonomously where safe and stop where human judgment or external side effects matter. OpenAI’s model guidance explicitly recommends compact autonomy policies and says prompts should define approval boundaries for external writes, destructive actions, purchases, and scope expansion. citeturn10view0turn32view2turn32view1

Fourth, it is **testable and versionable**. OpenAI’s skills API treats skills as versioned bundles, and the OpenAI eval guidance for agent skills argues that skill quality should be measured with prompt-plus-trace evals rather than “feels better” judgments. That is what turns a reusable skill from a prose artifact into an engineering artifact. citeturn25view1turn26view0turn28view3turn22view0

### Recommendations

The practical implication is that the primary `SKILL.md` should hold only the **smallest complete contract** needed for correct routing and reliable execution. Based on the public guidance and the line counts of official skills, a good default target is **roughly 100–250 lines** for most skills, with a hard ceiling near the published recommendation of **under 500 lines** and the Agent Skills guidance of **under about 5,000 instruction tokens**. That 100–250 line range is an inference from the official sample set, not a formal platform rule. citeturn24view0turn22view2turn34view0turn15view0turn15view1turn15view2turn15view4

This recommendation is also supported by OpenAI’s broader prompt guidance: leaner prompts can outperform bloated ones, and internal coding-agent tests found directional gains from removing repeated instructions, extra examples, and unnecessary tool text. The lesson is not “be short at all costs”; it is “keep only the load-bearing guidance in the always-loaded path.” citeturn29search0turn10view0

## Skill versus long prompt

### Comparison

| Dimension | Effective skill | Merely long prompt | Why it matters |
|---|---|---|---|
| Packaging | Versioned bundle of files with `SKILL.md`, plus optional scripts/references/assets. citeturn25view1turn22view4 | Single block of prose in one conversation or one prompt. citeturn25view1 | Bundling lets the skill carry the minimum instructions plus the specific resources needed to execute reliably. |
| Routing | Triggered by reusable metadata: `name`, `description`, and path are surfaced before body loading. citeturn26view0turn38view0 | No reusable routing surface beyond the current conversation. | A skill can be discovered repeatedly across sessions; a plain prompt cannot. |
| Context loading | Progressive disclosure: metadata first, full body second, references/scripts only as needed. citeturn24view0turn22view3 | Everything is front-loaded. | This directly controls context pressure and reduces irrelevant instruction load. |
| Determinism | Can move fragile or repeated logic into scripts. citeturn22view1turn34view0 | Repeats fragile shell/code instructions in prose. | Deterministic code beats prose when the same steps are repeatedly error-prone. |
| Scope control | Can define non-goals, approval boundaries, and output contracts as reusable policy. citeturn15view2turn15view1turn10view0 | Often mixes desired outcome, edge cases, side-effect rules, and examples in one undifferentiated block. | Reuse fails when the agent cannot tell what is core versus incidental. |
| Evaluation | Can be regression-tested with trigger evals and output evals over time. citeturn37view0turn22view0turn28view3 | Usually judged ad hoc. | Reusable skills need measurable quality, not vibes. |
| Versioning | Explicit skill versions and default/latest pointers exist in the API. citeturn26view0 | No first-class version identity. | Provenance and rollback become possible. |
| Distribution | Skills are the authoring unit; plugins are the distribution package for skills plus connectors and presentation assets. citeturn38view0 | A prompt is not a deployable unit. | This separates authorship from packaging and installation. |

### Findings on related artifacts

A skill is also **not** the same thing as repository policy. OpenAI’s AGENTS guidance says `AGENTS.md` loads before work begins and is the right home for repo-wide build commands, review expectations, conventions, constraints, and “what done means” for that repository. That is durable ambient policy, not a specialized reusable capability. A skill should add specialized behavior without duplicating repo law. citeturn28view0turn28view1

A skill is **not** the same thing as a reference dossier either. The Agent Skills specification and the `skill-creator` both recommend placing bulky technical references in `references/` and reading them on demand. If content is mostly knowledge and not execution guidance, it is usually a reference file, not primary `SKILL.md` material. citeturn24view0turn34view0

A skill is also **not** just a command wrapper. The scripts guide says complex or fragile commands should move into `scripts/`, but those scripts still need a routing surface, scope statements, instructions for when to use them, and output expectations. The wrapper is a dependency of the skill, not the skill itself. citeturn22view1turn34view0

Finally, a skill is distinct from a one-off workflow script or durable thread goal. OpenAI’s Goals guidance explicitly says a normal prompt remains the right tool for one-off edits, while a Goal is a thread-scoped completion contract for long-horizon work. A reusable skill sits in a different layer: it teaches a repeatable capability that multiple future tasks can invoke. citeturn32view3

## Anatomy and allocation

### Classification legend

The table below uses five allocation classes:

- **Mandatory primary**: should appear in the main `SKILL.md`.
- **Optional primary**: useful when relevant, but not universal.
- **Progressive reference**: better in `references/` or a similar on-demand file.
- **Code/config/test**: better represented as scripts, config, metadata, or eval fixtures than prose.
- **Usually unnecessary**: not worth standardizing into every skill.

### Field-by-field anatomy table

| Element | Best allocation | Why | Guidance |
|---|---|---|---|
| `name` | Mandatory primary | Required by the spec and used for identity. citeturn23view0turn25view1 | Keep it short, specific, and stable. |
| `description` and invocation triggers | Mandatory primary | This is the main implicit routing surface. citeturn22view3turn38view0turn26view0 | Put trigger language, scope, and key non-triggers here. |
| purpose | Mandatory primary | A one- or two-sentence purpose statement orients execution after invocation. Official skills do this consistently. citeturn15view0turn15view1turn15view2 | Put it near the top of the body. |
| scope | Mandatory primary | Scope reduces drift and overlap. Official skills often state what they own. citeturn15view0turn15view2 | Define what the skill is responsible for. |
| non-goals | Mandatory primary | Negative boundaries improve invocation precision and reduce accidental use. citeturn15view2turn15view1turn22view3 | Keep concise and concrete. |
| preconditions | Optional primary | Necessary only when the environment or access assumptions are material. The spec treats compatibility and requirements as optional. citeturn23view1turn22view1 | State only blocking prerequisites. |
| required files/context | Mandatory primary | If missing context blocks execution, the skill should say so up front. citeturn15view1turn34view0 | Name required repo paths, documents, or tools succinctly. |
| inputs | Optional primary | Helpful for structured tasks, but often inferable from the user request. citeturn22view4turn28view3 | Use when the task has stable input shapes. |
| questions the skill may ask | Optional primary | Clarifying questions matter mainly for true blockers; over-specifying them can cause unnecessary handoffs. citeturn39view0turn32view1 | Prefer a small blocker-only rule. |
| facts it should discover rather than ask | Mandatory primary | OpenAI guidance repeatedly favors using tools to inspect files and gather context instead of guessing or over-asking. citeturn39view2turn30view0 | Add a “discover first” rule for file contents, repo structure, and available evidence. |
| process | Mandatory primary | Stepwise instructions are explicitly recommended body content. citeturn24view0turn22view4 | Keep the default workflow in the main body. |
| decision checkpoints | Mandatory primary | They are the points where the agent must branch, stop, or load more context. citeturn10view0turn32view2 | Keep to the load-bearing branch points only. |
| human-in-the-loop boundaries | Mandatory primary | Approval boundaries are central to safe autonomy. citeturn10view0turn32view1turn26view0 | State exactly what needs human confirmation. |
| tool permissions | Code/config/test | Tool allowlists exist in the open spec but are experimental, and Codex also supports dependency metadata in `agents/openai.yaml`. citeturn23view2turn38view0 | Declare actual dependencies in config/metadata; mention only unusual usage rules in prose. |
| file-write permissions | Code/config/test | Write authority is mostly a harness or approval-policy concern, not a prose field. citeturn10view0turn26view0 | Express as approval policy and test it. |
| safety boundaries | Mandatory primary | Skill-local safety and scope boundaries are reusable behavior, especially for risky domains. citeturn26view0turn10view2 | Keep local; do not restate global platform policy. |
| output contract | Mandatory primary | OpenAI guidance repeatedly recommends exact required outputs and schemas. citeturn32view2turn39view1turn28view3 | Specify artifact names, sections, schema, and evidence expectations. |
| completion criteria | Mandatory primary | A reusable skill needs to define what “done” means. citeturn32view3turn28view1turn28view3 | Tie completion to verifiable evidence. |
| stopping conditions | Mandatory primary | Agentic prompts work better when stop conditions are explicit. citeturn32view1turn32view2 | State success stop, safe stop, and pause-to-human stop. |
| failure conditions | Mandatory primary | Structured failure is better than silent drift or tool thrash. citeturn32view2turn39view0 | Say what counts as blocked or unresolved. |
| escalation behavior | Mandatory primary | The agent should know when to stop and hand to a human or another system. citeturn39view2turn10view0 | Keep the escalation rubric short and concrete. |
| examples | Progressive reference | Examples help execution, but the model should try zero-shot first; examples add cost and can anchor behavior. citeturn32view0turn29search0turn34view0 | Keep only one tiny example in primary when output shape is fragile. |
| counterexamples | Code/config/test | The best home for counterexamples is trigger evals and output evals, not prose. citeturn37view0turn22view0 | Encode as should-trigger / should-not-trigger cases and failure fixtures. |
| anti-patterns | Optional primary | A short “do not do” block is useful when one mistake is common, but long anti-pattern catalogs bloat context. citeturn34view0turn29search0 | Keep only recurring, high-cost failure modes. |
| dependencies | Code/config/test | Scripts, `agents/openai.yaml`, environment config, and package metadata are more reliable than prose lists. citeturn22view1turn38view0 | Mention only blocking prerequisites in the main body. |
| compatible companion skills | Usually unnecessary | Most standalone skills do not need a companion list. Overlap is better handled by sharper scope and routing. citeturn22view3turn15view4 | Mention adjacent skills only when confusion is common. |
| incompatible skills | Usually unnecessary | “Incompatibility” is usually better expressed as non-goals or invocation policy rather than a separate taxonomy. citeturn15view2turn38view0 | Prefer “do not trigger for…” instead. |
| reference documents | Progressive reference | This is exactly what `references/` is for. citeturn24view0turn34view0 | Keep focused, one level deep, and explicitly referenced. |
| supporting scripts | Code/config/test | Deterministic helper logic belongs in `scripts/`. citeturn22view1turn34view0 | Reference them clearly from the workflow. |
| evaluation cases | Code/config/test | Evals are first-class external artifacts. citeturn22view0turn28view3 | Store in `evals/` or equivalent. |
| version/provenance metadata | Code/config/test | Skills are versioned bundles, but current Codex guidance is conservative about extra frontmatter. citeturn26view0turn23view2turn34view0 | Prefer repo history, release tags, eval manifests, or conservative metadata outside core routing fields. |

### Recommendations on primary versus progressive allocation

A robust primary `SKILL.md` should therefore include: `name`, `description`, purpose, scope, non-goals, blocker prerequisites, required context, workflow, decision points, approval/safety boundaries, output contract, completion criteria, stopping rules, failure/escalation rules, and links to the exact reference or script files to load next. Everything else should be moved outward unless there is measured evidence that keeping it in the primary file improves results. That “move outward by default” recommendation is the clearest synthesis of the official material. citeturn24view0turn22view2turn34view0turn29search0

## Invocation and execution patterns

### Findings on descriptions and trigger language

Descriptions should be written for **routing**, not for human marketing copy. The best-verifiable guidance is consistent across the Agent Skills optimization guide and OpenAI’s Build Skills docs: use imperative phrasing (“Use this skill when…”), focus on **user intent** rather than internal implementation, keep the description concise, front-load the key use case and trigger words, and include boundary language so the skill does not fire on near misses. citeturn37view0turn38view0

The tradeoff is precision versus recall. Under-specified descriptions fail to trigger; over-broad ones accidentally trigger. That is why strong descriptions often need both positive and negative language. Public OpenAI examples do this well: `security-threat-model` says “trigger only when” the task is explicit AppSec threat modeling and “do not trigger” for general architecture summaries or code review; `define-goal` says it is for goal definition only and explicitly excludes durable snapshots and decision logs. citeturn15view1turn15view2

Descriptions should also be treated as **eval targets**, not pure prose. The Agent Skills description guide recommends should-trigger and should-not-trigger query sets, train/validation splits, repeated runs because model behavior is nondeterministic, and avoiding keyword stuffing from failed prompts because that overfits. That is the best public answer to how to maximize correct invocation while minimizing accidental invocation. citeturn37view0

For skills where accidental activation is especially risky or annoying, Codex also exposes an additional control outside `SKILL.md`: `agents/openai.yaml` can set `allow_implicit_invocation: false`, which disables implicit matching while preserving explicit invocation. That is better than overloading the main prompt with “don’t accidentally use this” prose when the skill should simply never auto-trigger. citeturn38view0

### Findings on process, checkpoints, uncertainty, and safe stopping

A reusable skill should express its process as the **default happy path plus branch points**, not as a fully expanded essay. The spec recommends step-by-step instructions, and the official skills commonly organize around quick start, workflow, and output expectations. The main body should tell the model what to do first, what to verify, when to load more detail, and when to stop. citeturn24view0turn15view0turn15view1turn15view2

Decision checkpoints matter at the points where the agent could otherwise thrash or take the wrong side effect. OpenAI’s model guidance recommends explicit concurrency, retry, and stopping limits, plus a clear handoff between direct and programmatic tool use. The same principle applies more generally: if there is a risky branch, approval gate, or narrow source-priority rule, it belongs near the top-level workflow and not buried in a reference annex. citeturn32view2turn15view0

On uncertainty, the best current guidance is nuanced. GPT-5.2 guidance says ambiguous requests should either produce a few precise clarifying questions or explicit interpretations with labeled assumptions; it also says the model should never fabricate exact figures or references when uncertain. GPT-5 prompting guidance adds that you can tune how persistent the agent should be, but you should always define stop conditions and safe versus unsafe actions. The implication for skill authoring is: **teach the skill when to continue under stated assumptions, when to inspect tools or references, when to ask a blocker question, and when to stop with an honest failure message**. citeturn39view0turn32view1turn32view2

### Recommendations

For the future skill-builder, the most robust primary execution pattern is:

1. **Orientation**: What this skill owns, and what it does not own.
2. **Discovery-first rule**: What to inspect or gather before asking the user.
3. **Default workflow**: The shortest reliable path.
4. **Decision checkpoints**: Where to branch, approve, or load additional references.
5. **Output contract**: Exact artifact and evidence requirements.
6. **Completion / stop / failure / escalation**: Explicit end states.

That pattern matches the strongest common denominator across the official skill corpus and OpenAI’s broader agent-guidance material. citeturn15view0turn15view1turn15view2turn10view0turn32view2

## Examples and anti-patterns

### Findings on when examples help

Examples do **not** materially help invocation if they live only in the `SKILL.md` body, because the body is loaded only after the skill has already triggered. Invocation quality is driven much more by the `description`, by trigger evals, and by the surrounding skill catalog’s overlap structure. citeturn22view3turn26view0turn34view0

Examples do help **execution** when they encode one of three things: a fragile output contract, a non-obvious transformation pattern, or a measured gap seen in evals. OpenAI’s model guidance says to keep examples and style guidance when they encode a product requirement or fix a measured failure. The reasoning best-practices guide similarly recommends trying zero-shot first and using few-shot examples only when needed. citeturn29search0turn32view0

### Findings on when examples hurt

Examples become harmful when they substitute for generalizable instructions. There are three main failure modes in the evidence.

The first is **anchoring**. If examples are too specific, the model imitates the example path instead of understanding the higher-level rule. That risk is implicit in OpenAI’s “zero-shot first” recommendation and in the warning that example/instruction discrepancies can produce poor results. citeturn32view0

The second is **verbosity cost**. Extra examples consume context and can crowd out more important prompt content. OpenAI’s latest model guidance explicitly recommends removing repeated instructions and examples unless they are carrying real weight. citeturn29search0turn10view0

The third is **overfitting**. The Agent Skills trigger-optimization guide warns against stuffing descriptions with the exact failed keywords from a training set and recommends train/validation splits precisely to avoid shipping a skill that only works on the phrases used during authoring. The same logic applies to execution examples. If examples cover only one surface phrasing or one artifact shape, the skill may cargo-cult those patterns rather than generalize. citeturn37view0

### Negative cases and anti-patterns

The strongest public anti-pattern evidence is not theoretical; it appears in official issue trackers.

A path-assumption anti-pattern showed up in `gh-address-comments`, where the skill told the agent to run `scripts/fetch_comments.py`, but users reported that Codex often looked for the script in the **target repo** instead of the **skill directory**, then fell back to GraphQL. The lesson is clear: if a skill depends on a bundled script, path semantics must be explicit and tested. citeturn33view1turn22view1

A prompt-dependence anti-pattern appeared in feedback on Codex’s default testing experience, where a user reported that the default testing skill still required a strong master prompt and additional testing guidance before it felt effective. That is evidence that a skill with weak process definition is still behaving too much like a thin prompt wrapper. citeturn33view2

An installation/drift anti-pattern appeared in a Codex bug report where a symlink-wrapper installation pattern caused valid skills to be skipped; the user specifically called out the resulting drift risk between canonical repo skills and visible installed skills. Even though the Build Skills docs say Codex supports symlinked **skill folders**, this issue shows that authoring and distribution patterns still need real install-path testing. citeturn33view0turn38view0

From the source corpus as a whole, the main anti-patterns are:

- treating `SKILL.md` like a catch-all knowledge dump rather than the always-loaded execution contract; citeturn24view0turn34view0
- repeating the same rule in multiple places instead of stating it once; citeturn10view0
- hiding scope boundaries inside long prose instead of stating clear non-goals; citeturn15view1turn15view2
- using prose to simulate deterministic logic that should be a script; citeturn22view1turn34view0
- pushing provenance, changelog, and other author-facing clutter into the skill package. OpenAI’s `skill-creator` explicitly says not to generate auxiliary files like `README.md`, `INSTALLATION_GUIDE.md`, `QUICK_REFERENCE.md`, or `CHANGELOG.md` just because a human might expect them. citeturn34view0

## Generic template and skill-builder implications

### Recommended generic template outline

The outline below is a **template shape**, not a completed project skill.

```md
---
name: skill-name
description: Use this skill when [user intent + trigger cues + key near-miss boundaries].
---

# Human-readable title

## Purpose and scope
- What this skill owns.
- What it explicitly does not own.
- Authority note: follow [project-wide protocol path] for global rules; this skill adds only local specialized behavior.

## Preconditions
- Blocking environment or access assumptions only.

## Required context
- Minimal files, paths, tools, or documents required before execution.
- Discovery-first rule: inspect these before asking the user when possible.

## Workflow
- Step 1: initial inspection / context gathering.
- Step 2: core execution path.
- Step 3: validation or evidence gathering.
- Step 4: produce the required artifact.

## Decision checkpoints
- If [condition], read [reference path].
- If [condition], run [script path].
- If [condition], stop and ask for approval.
- If [condition], stop with structured failure.

## Safety and approvals
- Allowed autonomous actions.
- Actions that require human confirmation.
- Local safety boundaries or do-not rules.

## Output contract
- Required artifact(s), sections, fields, filenames, citations/evidence expectations.

## Completion and stopping
- Completion criteria.
- Safe stopping conditions.
- Failure conditions.
- Escalation behavior.

## On-demand resources
- references/[file].md — when to read it.
- scripts/[tool].py — when to run it.
- assets/[template] — when to use it.

## Minimal example
- One short example only if needed to stabilize output shape.
```

This outline follows the strongest common denominators from the spec, the `skill-creator`, the current official skill corpus, and OpenAI’s prompt guidance: keep the frontmatter minimal; keep the main body load-bearing; push large specificity outward; and make the final output and stopping logic explicit. citeturn24view0turn34view0turn15view0turn15view1turn15view2turn32view2

### Recommendations for the future skill-builder

The future skill-builder for The Bible Video Game should enforce the following authoring model.

**Require routing before prose.** The builder should force the author to write the description and non-goals before elaborating process. If the route is vague, the skill is not ready. The builder should also generate should-trigger and should-not-trigger eval cases at the same time. citeturn37view0turn28view3

**Require an authority-reference block instead of protocol duplication.** Because OpenAI’s AGENTS and Model Spec materials distinguish between ambient higher-authority guidance and task-local instructions, the builder should insert a short authority line that references the project’s master protocol by path and states that the skill does not override it. That preserves hierarchy without cloning the whole protocol into every skill. citeturn10view2turn28view0turn28view1

**Default to instruction-only, then justify scripts.** OpenAI’s Build Skills guide says instruction-only is the default path, while scripts are for cases where determinism or repeated fragile logic is actually needed. The builder should ask for a script only when prose has already failed or when the task is inherently brittle. citeturn38view0turn22view1turn34view0

**Separate operating contract from reference payload.** The builder should generate a short main `SKILL.md`, plus `references/`, `scripts/`, `assets/`, and `evals/` scaffolding when the task warrants them. It should never respond to “more coverage” by bloating the primary file first. citeturn24view0turn22view2turn22view0turn34view0

**Emit explicit completion, stop, failure, and escalation clauses.** These fields are the difference between a capability and a long prompt. Without them, the agent either stalls, over-asks, or keeps going past the intended boundary. citeturn32view1turn32view2turn10view0

**Keep provenance and evaluation attached, but outside the main prose path.** Given the tension between the broad Agent Skills spec and the current conservative Codex subset, the builder should avoid stuffing extra operational metadata into frontmatter by default. Instead, it should connect the skill to repo history, a small provenance manifest if needed, and evaluation fixtures in `evals/` or a neighboring testing directory. That makes provenance durable without risking routing drift or frontmatter incompatibility. citeturn23view2turn26view0turn22view0turn34view0

The net result is an authoring model in which a reusable skill is best understood as **a small always-loaded contract plus larger on-demand support files and measurable tests**. That is what separates a skill from a long prompt.

## Source appendix

### Primary OpenAI and Agent Skills sources used

| Source | What it contributed |
|---|---|
| OpenAI Skills API guide. citeturn25view1turn26view0 | Definition of skills as versioned bundles; routing metadata; versioning and safety model. |
| OpenAI Build Skills documentation. citeturn38view0 | Progressive disclosure behavior in Codex; context-budget limits for the initial skill list; plugin/skill distinction; optional `openai.yaml` controls. |
| OpenAI `skill-creator` skill and commit history. citeturn34view0turn36view0 | Current first-party authoring guidance, progressive disclosure recommendations, anti-clutter rules, and Codex-specific minimal frontmatter practice. |
| OpenAI official skill examples: `openai-docs`, `define-goal`, `security-threat-model`, `figma-implement-design`. citeturn15view0turn21view0turn15view2turn21view2turn15view1turn21view1turn15view4turn17view0 | Evidence from actual skill anatomy, scope statements, non-goals, and line-length patterns. |
| Agent Skills specification. citeturn22view4turn24view0turn23view2 | Formal schema, optional directories, progressive disclosure model, and file-reference recommendations. |
| Agent Skills best practices, using scripts, optimizing descriptions, and evaluating skills. citeturn22view2turn22view1turn37view0turn22view0 | Placement rules, description-eval method, script usage, and eval structure. |
| OpenAI model guidance and prompting guides. citeturn10view0turn32view2turn32view1turn32view0turn39view0 | Lean-prompt guidance, approval boundaries, uncertainty handling, output-contract patterns, and example usage guidance. |
| OpenAI AGENTS and best-practices documentation. citeturn28view0turn28view1turn28view2 | Distinction between ambient repo policy and specialized reusable skills. |
| Official issue evidence used as negative cases. citeturn33view1turn33view2turn33view0 | Path ambiguity, residual prompt dependence, and install/drift risk from real-world skill usage. |

### Audited official skill files with dates and commit SHAs

| Skill file | Audit date in repo history | Commit SHA audited |
|---|---|---|
| `skills/.system/skill-creator/SKILL.md` citeturn35view0turn36view0 | February 9, 2026 | `4ab6e0fd99c6667163bc34173e3ed3a3fed75ebc` |
| `skills/.curated/openai-docs/SKILL.md` citeturn19view0turn21view0 | April 24, 2026 | `da7611f0ddb078b641407842473e4fa308988516` |
| `skills/.curated/define-goal/SKILL.md` citeturn20view1turn21view2 | May 21, 2026 | `b0401f07213a66414d84a65cb50c1d226f99485a` |
| `skills/.curated/security-threat-model/SKILL.md` citeturn20view0turn21view1 | February 2, 2026 | `5c8f1e26803bcfaffeceef1e7accbcf7e388417a` |
| `skills/.curated/figma-implement-design/SKILL.md` citeturn16view0turn17view0 | March 24, 2026 | `0e7823cca07bc2cbf34718a383f9ae92525be6a5` |
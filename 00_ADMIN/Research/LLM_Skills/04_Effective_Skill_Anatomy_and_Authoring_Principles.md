# Effective Skill Anatomy and Authoring Principles

**Session:** 4 of the LLM-skills deep-research sequence
**Research date:** 2026-07-22
**Repository:** [Degrading1919/The_Bible_Video_Game](https://github.com/Degrading1919/The_Bible_Video_Game)
**Predecessor checkout:** [71be766ca4281307ce0ca09e6e1265df8882e941](https://github.com/Degrading1919/The_Bible_Video_Game/tree/71be766ca4281307ce0ca09e6e1265df8882e941)
**Scope:** Authoring model only. This report does not create the skill-builder, select an engine/tool stack, or define a final project skill catalog.

Claim labels used below:

- **Finding** — directly supported by an identified primary source or inspected artifact.
- **Inference** — reasoned consequence of findings, not a platform guarantee.
- **Recommendation** — an authoring choice proposed for this project.
- **Unverified** — a material claim the reviewed primary sources do not establish.

OpenAI documentation cited here is living documentation accessed on 2026-07-22. It exposed no page-level publication date or documentation-repository commit in the fetched manual, so the access date is the currency marker. Repository examples are pinned to commits.

## 1. Effective-skill thesis

An effective skill is a **small, discoverable, testable workflow package that transfers non-obvious procedural knowledge to an agent and improves a defined class of real tasks without violating authority, permissions, or scope**. It is not made effective by prompt length. Its value comes from six coupled properties:

1. **Correct selection:** its name and description make it available for the right user intents and avoid near-miss intents.
2. **Operational procedure:** its body tells the agent what to inspect, decide, do, validate, and return.
3. **Calibrated freedom:** fragile operations receive deterministic controls; judgment-heavy work receives principles and checkpoints rather than brittle scripts.
4. **Progressive disclosure:** every-run instructions remain compact while conditional references, assets, scripts, and fixtures load only when needed.
5. **Truthful boundaries:** it distinguishes instructions from authority, permissions, installed capabilities, source facts, and human approvals.
6. **Demonstrated benefit:** realistic evaluations show that invocation and outputs improve on a no-skill or previous-version baseline, including negative cases.

**Finding:** Current OpenAI guidance says a skill packages task-specific instructions, resources, and optional scripts for a repeatable workflow. Codex first receives only discovery metadata, and OpenAI recommends one focused job, explicit inputs/outputs, and prompt tests against the description ([Build skills](https://learn.chatgpt.com/docs/build-skills), accessed 2026-07-22). The open Agent Skills creator guidance likewise emphasizes grounding a skill in real tasks and project artifacts, spending context on what the agent lacks, calibrating specificity to fragility, favoring procedures over declarations, and evaluating against a baseline ([best practices](https://agentskills.io/skill-creation/best-practices) and [evaluation guidance](https://agentskills.io/skill-creation/evaluating-skills), accessed 2026-07-22).

**Finding:** Structural validity is necessary but insufficient. The Agent Skills validator can check the required SKILL.md structure, naming, and frontmatter; it cannot prove correct invocation, faithful research, authorized actions, or useful outputs ([specification](https://agentskills.io/specification), accessed 2026-07-22).

**Recommendation:** Accept a skill only when all of these are true:

- it is structurally valid;
- it triggers appropriately;
- it is executable with declared prerequisites;
- it preserves higher authority;
- it improves a real task class against a baseline;
- it stops safely; and
- its dependencies and sources can be maintained.

For The Bible Video Game, a skill cannot become an alternative source of project truth. The [Master Assistant Protocol at the predecessor SHA](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) keeps the user/Creative Director, witness premise, biblical-source commitments, sacred-event protection, era-knowledge separation, uncertainty labeling, and schema-first development above a task workflow. A future skill should route to current controlling files and operationalize a bounded procedure, not paste a drifting copy of those rules into conditional context.

## 2. Skill versus long prompt

The distinction is architectural, not a word-count test. A long prompt can be excellent for a one-off task; a short skill can be poor.

| Dimension | Long task prompt | Effective skill package | Authoring consequence |
|---|---|---|---|
| Purpose | Direct one instance | Transfer a method across a recurring task class | Begin with observed repeated use cases. |
| Selection | Present because the user supplied it | Must be discovered or explicitly invoked | Test discovery metadata separately. |
| Context cost | Entire prompt loads for that task | Metadata, body, and resources load progressively | Keep only every-run procedure in SKILL.md. |
| Inputs | May rely on the current conversation | Must obtain inputs across varied runs | State inputs and discoverable facts. |
| Authority | Co-located with current user direction | Persists beyond the creating context | Cite live authority; do not duplicate it. |
| Resources | Usually inline or ad hoc | May bundle references, scripts, assets, metadata, and tests | Give each resource a purpose and loading condition. |
| Tools | May rely on visible turn capabilities | Runs may occur on different clients/environments | Preflight capabilities; prose grants no permission. |
| Process | May encode an answer or instance plan | Encodes a generalizable procedure | Favor methods, checkpoints, and error paths. |
| Side effects | Governed by the current request | Repeated under future requests | Define write scope, approvals, and stopping. |
| Verification | Often task-local | Must be reproducible | Add structural, behavioral, and human review. |
| Maintenance | Expires with the task | Versioned and capable of becoming stale | Preserve provenance and reevaluate. |
| Portability | No portability implied | Portable core can contain client-specific extensions | Mark compatibility and test each surface. |

**Finding:** OpenAI describes skills as reusable workflow artifacts and plugins as a separate distribution bundle. The open specification defines the portable directory core. Neither source says a long prompt becomes effective merely because it is saved as SKILL.md ([Build skills](https://learn.chatgpt.com/docs/build-skills); [specification](https://agentskills.io/specification), accessed 2026-07-22).

**Inference:** A saved prompt becomes skill-like only when it solves a coherent recurring problem, supplies selection metadata, separates conditional resources, handles environmental variation, and survives realistic evaluation. Otherwise it is better retained as a prompt, policy, reference dossier, command wrapper, workflow script, or one-off output—the distinctions established by [Session 2](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md).

### Boundary with adjacent artifacts

| Adjacent artifact | Its controlling function | Why a skill is different | Correct relationship |
|---|---|---|---|
| Repository policy / Master Protocol | Carries durable, always-applicable authority and project constraints | A skill is conditionally selected and cannot be the sole carrier of universal rules | Keep policy canonical; have the skill locate it, apply the relevant parts, and stop on conflict. |
| Reference dossier | Carries sourced domain facts, uncertainty, provenance, or technical detail | A reference informs reasoning but does not itself define an execution sequence | Load the smallest relevant dossier on demand; do not relabel its claims as skill authority. |
| Command wrapper | Invokes a concrete executable operation with parameters | A workflow includes discovery, judgment, approval, interpretation, and validation around commands | Put deterministic command behavior in a reviewed script; let the skill decide when it is appropriate and interpret results. |
| Workflow script | Mechanically implements a stable sequence | A skill can coordinate human decisions, contextual branches, evidence gathering, and tools that cannot be safely hard-coded | Use code for repeatable mechanics and prose for bounded judgment; test both layers. |
| Role/persona prompt | Assigns perspective, responsibility, or response behavior for a task/session | A skill is best centered on a coherent recurring job, not a job title | Keep role ownership in governance or agent configuration; package a repeatable procedure within that role only when evidenced. |
| Evaluation suite | Measures triggering, behavior, artifacts, failures, and regression | Evaluation does not execute the production workflow or confer approval | Version fixtures with the skill, but keep them outside the body so execution is not contaminated by expected answers. |

**Recommendation:** If an authoring request is satisfied by one row above without a reusable decision-bearing workflow, do not force it into a skill. A validator wrapped by a two-line usage instruction may be a script plus repository documentation; a set of historical facts may be a dossier; sacred-event protection must remain governance plus future schema/runtime/evaluation controls. Artifact economy is a quality feature.

## 3. Field-by-field anatomy

Classification key:

- **Mandatory in primary** — express in SKILL.md for a robust skill, even if only as a sentence or step. Only name and description are universally mandatory frontmatter fields.
- **Optional in primary** — include when material; omit empty headings.
- **Progressive reference** — place detailed/conditional material in a directly linked reference.
- **Code/config/test** — represent operative truth in code, client metadata/config, schema, or evaluation fixtures.
- **Usually unnecessary** — omit by default; include only after an evidenced need.

Unless a row explicitly reports a platform fact, the classifications and acceptance criteria below are **recommendations derived from the cited findings**, not claims that the Agent Skills format mandates these headings.

| Element | Default classification | Allocation and rationale | Testable acceptance criterion |
|---|---|---|---|
| Name | **Mandatory in primary** | Required frontmatter. Use a short lowercase hyphenated identifier matching the directory; prefer an action/job over a role title. | Validator accepts it; folder and name match; adjacent skills remain distinguishable. |
| Description and triggers | **Mandatory in primary** | Required discovery signal. State intent, artifacts/domain, positive contexts, and nearest exclusions; front-load key language. | Positive, paraphrased, embedded, and near-miss cases meet agreed held-out trigger thresholds. |
| Purpose | **Mandatory in primary** | One compact outcome statement; explain recurring value, not marketing. | A reader names the finished result and need in one sentence. |
| Scope | **Mandatory in primary** | Define unit of work, artifacts, and phase boundaries. | Reviewers classify representative in/out cases consistently. |
| Non-goals | **Optional in primary** | Include the few adjacent tasks or unsafe expansions likely to be confused. Put exhaustive negatives in tests/references. | Near misses do not activate, or are safely declined/rerouted. |
| Preconditions | **Optional in primary** | Required when files, auth, schema approval, tools, or decisions must exist. Move install detail to references. | Missing prerequisites are detected before consequential work. |
| Required files/context | **Mandatory in primary** | Name or explain how to locate minimum live sources and freshness checks. Keep domain detail outside. | A clean run loads current files and does not invent absent artifacts. |
| Inputs | **Mandatory in primary** | State required/optional inputs, defaults, forms, and precedence. | Every required input in an eval has a traceable source. |
| Questions it may ask | **Optional in primary** | Reserve for decisions that materially change the result and cannot be discovered. | No unnecessary question is asked for a repository-resolvable fact. |
| Facts to discover | **Mandatory in primary** | Give an inspection order for repository state, files, tools, versions, and authority. | Seeded facts are found/cited rather than asked or invented. |
| Process | **Mandatory in primary** | Imperative ordered phases with clear branches and a default. | A trace follows phases without irrelevant exploration. |
| Decision checkpoints | **Mandatory in primary** for risky/branching work | Gate scope, authority, cost, or side effects immediately before the decision. | The selected branch, evidence, and reason are recorded first. |
| Human boundaries | **Mandatory in primary** when judgment/side effects require ownership | Name what the agent may recommend versus approve. | Reserved decisions cannot be taken silently. |
| Tool permissions | **Code/config/test** | Body may state expected tools and preflight them; host policy, sandbox, approvals, and authorization govern access. | Missing/denied capability produces stop or authorized fallback, never a false permission claim. |
| File-write permissions | **Code/config/test**, with concise body boundary | State output roots and overwrite/commit rules; enforce with sandbox, approvals, Git, or validators where possible. | Out-of-scope write tests are refused or escalated. |
| Safety boundaries | **Mandatory in primary** for task-specific hazards | Keep universal policy above the skill; put action-adjacent guards in the body and mechanical controls in tests/config/code. | Boundary cases stop before hazardous action and name the rule. |
| Output contract | **Mandatory in primary** | Define artifact, path/return form, required structure/fields, evidence, and intermediate-file policy. | Output validates and no unrequested artifact appears. |
| Completion criteria | **Mandatory in primary** | Express observable done conditions including validation. | Completion cannot be claimed with absent output or failing check. |
| Stopping conditions | **Mandatory in primary** for consequential work | Stop for unresolved authority, missing source, denied approval, ambiguous target, failed validation, or competing change. | No partial consequential action occurs after a stop condition. |
| Failure conditions | **Optional in primary** | Separate recoverable retry, fallback, user action, and terminal stop. Put script diagnostics with scripts. | Simulated failures produce the documented class, not success. |
| Escalation behavior | **Mandatory in primary** when possible | Name decision owner, evidence to present, and paused action. | Escalation is specific, bounded, and state-preserving. |
| Examples | **Progressive reference** by default | Keep one short example only when it clarifies syntax, branching, or output better than prose. | Held-out tasks do not copy irrelevant example values. |
| Counterexamples | **Code/config/test** or reference | Put near-miss invocation, forbidden outputs, and bad traces in negative fixtures. | Counterexamples do not trigger or safely decline. |
| Anti-patterns | **Optional in primary** | Keep concrete frequent mistakes the agent would not notice; move long catalogs out. | Each retained item maps to a real failure/source/test. |
| Dependencies | **Code/config/test**, with body preflight | Declare supported tool dependencies in metadata; pin executable versions; state file dependencies/fallbacks. | Tests cover present, absent, incompatible, and unauthenticated states. |
| Compatible companion skills | **Usually unnecessary** | Codex publishes no portable companion field or deterministic composition order. Use explicit tested workflow only when needed. | No unsupported automatic-invocation claim appears. |
| Incompatible skills | **Usually unnecessary** | Avoid speculative catalogs. Describe tested conflicting behavior and safe stop in governance/tests. | Conflict yields visible stop or precedence decision, not silent blending. |
| Reference documents | **Progressive reference**, with body routing | Link directly and state exactly when to read. Canonical project authority stays in governed location. | Each resource is one hop away and has a condition. |
| Supporting scripts | **Code/config/test** | Use for deterministic, repeatedly reinvented, or fragile work; require bounded paths, helpful errors, and tests. | Source is inspected and representative success/failure tests pass. |
| Evaluation cases | **Code/config/test** | Store realistic prompts, inputs, expected behavior, assertions, baselines, and negatives outside every-run context. | Trigger and output suites compare skill and baseline/previous version. |
| Version/provenance metadata | **Code/config/test** | Git is primary history; optional standard license/compatibility/metadata or implementation record can supplement it. | Origin, license, tested commit/surface, and changes are reconstructable. |

Mandatory does not mean one heading per row. A compact preflight can express required files, prerequisites, discover-versus-ask rules, and stopping conditions. One workflow step can combine a checkpoint, approval boundary, and failure path. Coverage matters; boilerplate does not.

## 4. Primary-file versus progressive-reference allocation

**Finding:** Codex initially includes skill name, description, and path; it loads the body only after selection. The current manual limits the initial skill list to at most 2% of context or 8,000 characters when context size is unknown, shortens descriptions first, and may omit entries in large installations ([Build skills](https://learn.chatgpt.com/docs/build-skills), accessed 2026-07-22). The open specification recommends a body below 5,000 tokens and 500 lines, direct relative links, and resources one level from SKILL.md ([specification](https://agentskills.io/specification), accessed 2026-07-22). These are ceilings/heuristics, not size targets.

| Layer | Content | Loading rule | Exclude |
|---|---|---|---|
| Discovery metadata | Name; concise intent/job/artifacts; positive triggers; nearest exclusions | Always catalog-visible, subject to shortening/omission | Workflow history, broad policy, implementation detail |
| Primary SKILL.md | Purpose; scope; preflight; required-source routing; core workflow; decisions/approvals/stops; output contract; completion; resource map | Loaded in full on activation | Encyclopedic data, many variants, large templates, duplicated authority |
| On-demand resources | Conditional references; schemas; examples; assets; scripts; eval fixtures; client metadata | Load/copy/execute on a stated condition | Undocumented files, deep chains, unreviewed executables |

Allocation decision test:

1. Is it needed to select the skill? Put the smallest sufficient wording in the description.
2. Is it needed on nearly every successful run? Put action-guiding content in the body.
3. Is it conditional on a domain, variant, error, file type, or tool? Put it in a focused reference and name its loading condition.
4. Does correctness require deterministic parsing, validation, or transformation? Put operative behavior in reviewed code/schema/test and keep invocation/interpretation in the body.
5. Is it always-on repository governance? Keep it in the protocol/instruction layer; link rather than clone.
6. Does it explain package history? Keep it in Git history or an implementation record.

### Referencing project authority without duplication

A future skill should locate and read the current Master Protocol when its workflow may affect project content/policy; name relevant sections; quote sparingly; stop if the controlling file is missing/superseded/conflicting; and record the tested commit without hard-wiring an old commit as forever-current authority. This preserves the protocol and satisfies [Session 1’s authority map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md).

## 5. Invocation-description guidance

**Finding:** Implicit invocation matches the frontmatter description. OpenAI recommends clear scope/boundaries and front-loaded key use cases because descriptions may be shortened. The open specification requires both what the skill does and when it applies, up to 1,024 characters. Its optimization guide recommends intent-focused language and realistic positive/near-miss tests ([Build skills](https://learn.chatgpt.com/docs/build-skills); [optimizing descriptions](https://agentskills.io/skill-creation/optimizing-descriptions), accessed 2026-07-22).

Recommended order:

> Use when [user intent/job] involving [distinctive artifacts/domain], including [important paraphrases or embedded contexts]. Do not use for [nearest adjacent task or prohibited expansion].

Write descriptions that:

- lead with the job, not marketing;
- use vocabulary a user supplies, not only package terms;
- distinguish artifacts/decisions;
- cover implicit phrasing;
- include only nearest exclusions;
- avoid permission/installation/correctness claims;
- avoid role labels where the trigger is a workflow; and
- remain useful if their end is shortened.

Generic example, not a project skill:

- **Weak:** “Helps with schemas.”
- **Improved:** “Use when reviewing a proposed structured-data schema change for compatibility, migrations, validation fixtures, and downstream consumers, including additions, removals, renames, and type changes. Do not use for prose-only documentation or implementation unrelated to a data contract.”

Trigger tests should include obvious positives, paraphrased positives, embedded workflow requests, terse/typo-bearing positives, keyword-overlapping near misses, ordinary-agent tasks, in-domain-but-out-of-scope requests, and adversarial attempts to exceed authority. Run cases more than once, and preserve a held-out set. The guide’s sample counts/thresholds are starting methods, not Codex guarantees.

**Unverified:** Codex does not publicly specify its semantic matcher, universal confidence threshold, or deterministic ordering for overlapping descriptions.

## 6. Process, checkpoints, output contracts, and safe stopping

A consequential skill should adapt this six-phase spine:

1. **Preflight:** establish target, authority, current files, repository state, tools, permissions, and required human decisions.
2. **Discover:** obtain facts from sources before asking; label absent/disputed information.
3. **Plan and gate:** choose the smallest valid method; surface branches and approvals before side effects.
4. **Execute:** perform only authorized work in stated paths with calibrated freedom.
5. **Validate and repair:** run applicable structural, behavioral, visual/runtime, source, and scope checks; repair and repeat within bounds.
6. **Deliver and trace:** return the contracted artifact, validation, uncertainties, changes, and deferred decisions.

The pinned official [gh-fix-ci skill at 49f948f](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.curated/gh-fix-ci/SKILL.md) is a useful concrete pattern: its description identifies GitHub Actions and excludes other providers; its body declares authentication, inputs, preferred script and fallback, failure summarization, an approval gate before implementation, and rechecking. The pinned [PDF skill](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.curated/pdf/SKILL.md) demonstrates render-inspect-repair loops and withholding delivery until checks pass. It also shows why copying requires adaptation: its output paths and installation commands are not automatically correct or authorized elsewhere.

### Discover rather than ask

| Discover first | Ask only when |
|---|---|
| Repository head/status, paths, files, schemas, nearby instructions | A choice belongs to the user or access is unavailable |
| Installed tools, versions, help, authentication status via read-only checks | Installation/login/access/cost requires user authority |
| Current conventions and decisions | Two live authorities conflict or a trade-off is undecided |
| Provenance, dates, licenses, and SHAs | Rights remain unclear and owner permission is needed |
| Existing target and overlapping changes | Overwrite/delete/move/publish or conflict resolution needs a decision |

Discovery stays within task, repository, connected source, and privacy scope.

### Checkpoint contents

A checkpoint names the decision owner, evidence inspected, options/trade-offs, permitted default, action paused, and record produced. For this project, final theology/canon decisions, sacred figures/events, major creative direction, material scope growth, engine/tool choice, schema/spec approval, and publication remain human-owned.

Safe stopping must be useful rather than vague. “Ask the user” is not a stopping model. The skill should state the unresolved fact or decision, why it blocks the next step, what evidence has already been inspected, the exact action still paused, and the smallest user or environment change that would permit continuation. It should preserve partial research separately from any artifact that could be mistaken for accepted output.

### Output contract

A robust contract specifies:

- artifact and location;
- allowed/forbidden paths;
- required structure or schema;
- evidence/citations/confidence/provenance;
- validation checks and result record;
- uncertainty labels; and
- objective completion conditions.

### Failure and stopping taxonomy

| State | Correct behavior | Incorrect behavior |
|---|---|---|
| Missing discoverable input | Search authorized sources | Ask for a fact already in the repository |
| Missing user-owned decision | Present evidence and pause dependent action | Choose silently |
| Optional tool absent | Use documented safe fallback | Install without authority |
| Required tool absent | Name prerequisite and stop | Claim an unverified substitute succeeded |
| Validator failure | Repair and rerun | Ignore or weaken the check |
| Authority conflict | Apply higher authority or escalate | Blend silently |
| Concurrent change | Re-audit affected inputs; avoid overwrite | Publish stale work |
| Evidence gap | Label unknown/unverified and narrow conclusion | Manufacture certainty |

## 7. Examples and counterexamples

Examples help when they convey a short input/output schema, non-obvious command invocation, representative failure branch, stable before/after invariant, boundary near miss, or exact interoperability template. The creator guidance recommends concise examples; the specification recommends input/output examples and edge cases; best-practices guidance recommends short templates and moving large/conditional templates to assets ([OpenAI skill-creator at 49f948f](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator/SKILL.md); [best practices](https://agentskills.io/skill-creation/best-practices), accessed 2026-07-22).

Examples harm when they contain unapproved proper nouns/paths/engines/schemas, dominate the abstract procedure, show only success, leak expected answers into evaluations, encode one client as portable truth, repeat cosmetic variants, become stale, or imply untested support.

**Inference:** Anchoring grows when one example is more concrete than the procedure. State invariants first, vary fixtures, add counterexamples, hold out cases, and strip example-specific entities.

Placement rule:

- zero or one compact example in SKILL.md if it helps most runs;
- variants and worked examples in references;
- canonical forms in schemas/assets;
- positives, near misses, adversarial prompts, and failures in evals;
- forward-test agents receive the skill, realistic prompt, and raw artifacts—not intended answers or prior diagnosis.

Counterexample pair:

- **Cargo cult:** “Always use the exact seven headings in Example A.”
- **Transferable:** “Preserve required evidence, decision, risk, and validation fields; use the maintained template and omit optional sections only when its schema permits.”

## 8. Anti-patterns

1. **Encyclopedic SKILL.md:** loads irrelevant domain detail on every activation.
2. **Saved megaprompt:** stores a finished answer/persona/task plan instead of a method.
3. **Universal policy hidden conditionally:** critical authority or safety exists only in a skill.
4. **Trigger rules only in the body:** the router cannot see them before activation.
5. **Catch-all expert:** collapses Bible, history, game design, code, art, and approval.
6. **Keyword soup:** forces false-positive invocation.
7. **Menu without default:** equal tool choices provoke exploration.
8. **Tools as permissions:** “run/install/push” is mistaken for authorization.
9. **Hidden preconditions:** mutation begins before checking target, files, versions, auth, or schemas.
10. **Happy-path-only workflow:** no behavior for ambiguity, absence, conflicts, or failed checks.
11. **Validation theater:** “double-check” has no invariant, source, renderer, test, or schema.
12. **Black-box script:** executable lacks inspection, tests, bounded paths, pins, errors, or provenance.
13. **Deep reference maze:** required context is several indirections away.
14. **Duplicated authority:** protocol/schema/runbook is copied and drifts.
15. **Example anchoring:** one rich example becomes the answer.
16. **Evaluation leakage:** test agents see intended fixes, diagnoses, or leftovers.
17. **Self-evaluation only:** no baseline, objective assertions, or domain owner.
18. **Unsupported portability:** one-client behavior is called universal.
19. **Stale environment assumption:** versions/paths/engine choices lack current authority.
20. **Premature companion catalog:** hypothetical skills become dependencies/conflicts.
21. **No provenance/license:** copied instructions/code/assets cannot be audited.
22. **Completion by assertion:** success is reported despite absent outputs or failed checks.

## 9. Recommended generic skill-template outline

This is an allocation outline, not a completed skill and not a proposed project catalog.

    ---
    name: <short-action-oriented-name>
    description: <intent, artifacts/context, when to use, nearest exclusions>
    ---

    # <Title>

    <One-sentence purpose and bounded outcome.>

    ## Preflight
    - Confirm target and allowed output scope.
    - Locate current authority and required files.
    - Discover available facts; ask only for unresolved user-owned decisions.
    - Verify required capabilities without assuming permission.
    - Stop on material authority/input/permission gaps.

    ## Inputs
    - Required: <input, source, precedence>
    - Optional: <input, safe default>

    ## Workflow
    1. <Discover/inspect and record evidence.>
    2. <Decision branch with default/checkpoint.>
    3. <Approval gate if consequential.>
    4. <Bounded execution.>
    5. <Validation-and-repair loop.>

    ## Output contract
    - Artifact/location: <allowed result>
    - Structure/evidence: <schema or compact list>
    - Completion: <observable passing conditions>

    ## Failure and escalation
    - If <recoverable condition>, <bounded retry/fallback>.
    - If <authority/prerequisite conflict>, stop and report evidence.
    - Never <task-specific hazardous action>.

    ## Resources
    - Read references/<file> when <condition>.
    - Run scripts/<file> only when <condition>; interpret <result>.
    - Use assets/<file> for <output condition>.

Keep client metadata, evals, deterministic scripts, conditional references, assets, license, and Git history outside the every-run body.

## 10. Implications for the future skill-builder

Inherited findings:

- The repository has no selected engine, language, build system, schemas, runtime harness, or production pipeline ([Session 1](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md)).
- Skills are one artifact class; they should not absorb governance, agents, tools, references, state, and evaluation ([Session 2](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md)).
- Session 3 resolved the Session 17 root as .agents/skills/the-bible-video-game-skill-builder/, documented invocation/progressive disclosure, and left composition order/precedence/lifetime unverified ([Session 3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md)).

The future builder should:

1. start from real recurring workflows, examples, corrections, and failures;
2. classify whether the requested artifact is actually a skill;
3. discover current authority and repository facts before asking;
4. refuse to invent engines, schemas, conclusions, roles, companion skills, or paths;
5. allocate proposed content using this report’s table;
6. keep SKILL.md concise and conditionally route detail;
7. test positive, paraphrased, embedded, and near-miss triggering;
8. calibrate freedom per step;
9. live-reference rather than duplicate the Master Protocol;
10. define inputs, discover/ask rules, ownership, writes, stops, failures, and escalation;
11. define output and observable completion;
12. generate only justified resources; avoid README/changelog clutter;
13. inspect/test/license-audit/provenance-record every executable or adaptation;
14. structurally validate and clean-context forward-test;
15. compare to no-skill or prior version and revise from traces;
16. record surface/version, repository/skill commits, fixtures, and limits;
17. reserve theological, canon, sacred-event, major creative, schema, tool, and publication decisions for accountable humans; and
18. stop after the bounded package—never create a final catalog by expansion.

Testable acceptance for a generated skill later includes:

- valid metadata and directory match;
- no unsupported portable claims;
- tested positive and near-miss description behavior;
- one coherent job and necessary non-goals;
- live authority and inputs discovered from named sources;
- no duplicated protocol or invented repository facts;
- direct condition-labeled resource links;
- inspected/tested executables with dependencies/failure behavior;
- bounded paths and no inferred install/delete/commit/push/publish authority;
- observable output/completion contract;
- stop behavior for missing authority, prerequisites, approval, or validation;
- clean-context realistic execution;
- skill/no-skill or previous-version comparison;
- retained adversarial cases for certainty, sacred events, schema invention, anachronism, and scope where relevant; and
- reconstructable provenance and licenses.

### Connecting provenance, versions, and fixtures

The builder should connect these concerns without loading maintenance history into every run:

| Record | Durable home | Relationship to the skill |
|---|---|---|
| Source and adaptation provenance | Session 17 implementation record plus commit-pinned links and applicable license/notice files | Establishes where instructions, code, or assets came from and what changed. |
| Package version | Git commit; optional metadata only when a client or distribution process needs it | Identifies the exact reviewed package. A prose “version” that can disagree with Git is not authoritative. |
| Tested environment | Implementation/evaluation record: Codex surface/version, OS/runtime, repository SHA, tool versions, permissions | Bounds claims about discovery, scripts, and portability. |
| Trigger fixtures | Evaluation files kept outside SKILL.md | Measure positive, paraphrased, embedded, near-miss, and adversarial selection without bloating production context. |
| Output fixtures/assertions | Evaluation workspace or package eval directory when Session 16 justifies it | Measure contract compliance and regressions with and without the skill. |
| Canonical project authority | Live repository files named by the workflow | Remains current input, not copied package history. |

On every material update, the maintainer should identify which trigger cases, output cases, dependency checks, provenance records, and human-review conclusions are invalidated. A version bump or successful structural validator alone is insufficient evidence that prior behavior still holds.

This session does not decide final builder requirements, composition governance, evaluation thresholds, implementation contents, or final synthesis. It recommends no engine, DCC tool, language, MCP server, hook, or build system.

## 11. Claims and evidence table

| Claim | Status | Closest primary evidence | Limit | Consequence |
|---|---|---|---|---|
| Skill directory requires SKILL.md; name and description are required. | **Finding** | [Build skills](https://learn.chatgpt.com/docs/build-skills); [specification](https://agentskills.io/specification) | Other fields vary by client. | Validate portable minimum; label extensions. |
| Codex loads metadata before selected body. | **Finding** | [Build skills](https://learn.chatgpt.com/docs/build-skills) | Selection algorithm/lifetime unpublished. | Put triggers in description. |
| Catalog pressure may shorten/omit descriptions. | **Finding** | [Build skills](https://learn.chatgpt.com/docs/build-skills) | No inclusion guarantee. | Front-load; avoid catalog inflation. |
| Specification recommends under 5,000 tokens/500 lines and direct references. | **Finding/guidance** | [Specification](https://agentskills.io/specification) | Ceiling is not a quality target. | Split conditionally. |
| Real expertise/artifacts and execution refinement improve authoring practice. | **Finding/guidance** | [Best practices](https://agentskills.io/skill-creation/best-practices) | Not a guarantee. | Require real workflows/failures. |
| Procedures, defaults, checklists, and validation loops are recommended. | **Finding/guidance** | Same | Not every pattern fits every skill. | Select by risk/variability. |
| Instruction-only is default; deterministic/repeated work can justify scripts. | **Finding/guidance** | [Build skills](https://learn.chatgpt.com/docs/build-skills); [skill-creator](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator/SKILL.md) | Scripts add risk. | Require rationale/tests. |
| Scripts should declare dependencies and handle errors/edges. | **Finding/guidance** | [Specification](https://agentskills.io/specification); [using scripts](https://agentskills.io/skill-creation/using-scripts) | Runtimes/permissions vary. | Use bounded noninteractive helpers. |
| Descriptions need positives, near misses, repeated runs, and held-out validation. | **Finding/guidance** | [Optimizing descriptions](https://agentskills.io/skill-creation/optimizing-descriptions) | Example thresholds are not Codex guarantees. | Maintain trigger fixtures. |
| Output eval should compare with no skill or prior version. | **Finding/guidance** | [Evaluating skills](https://agentskills.io/skill-creation/evaluating-skills) | Human review still needed. | Keep baseline/assertions/traces. |
| gh-fix-ci demonstrates focus, prerequisites, approval, fallback, recheck. | **Observed artifact** | [Pinned file](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.curated/gh-fix-ci/SKILL.md) | One structure is not universal. | Reuse pattern, not commands. |
| PDF demonstrates render/inspect/repair and fallback. | **Observed artifact** | [Pinned file](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.curated/pdf/SKILL.md) | Paths/install steps are context-specific. | Adapt only after review. |
| Optional spec metadata may express license, compatibility, metadata, experimental allowed tools. | **Finding** | [Specification](https://agentskills.io/specification) | Support varies. | Never treat optional field as universal permission. |
| Codex has documented deterministic companion/conflict ordering. | **Unverified / not established** | [Session 3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md) | Multiple availability does not define merge order. | Avoid speculative companion lists. |
| Skill prose grants shell/network/Git/filesystem permission. | **Contradicted** | [Approvals/security](https://learn.chatgpt.com/docs/agent-approvals-security); Session 3 | Experimental metadata does not override policy. | Preflight and stop/fallback. |
| Copying the Master Protocol into a skill strengthens authority. | **Rejected inference** | [Master Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md); Session 2 | Duplication creates drift. | Live-reference authority. |
| Structural validity proves effectiveness. | **Contradicted** | Specification validator plus separate evaluation guidance | Format cannot prove truth/safety/usefulness. | Require layered acceptance. |

## 12. Source appendix

### A. Project sources

Inspected at predecessor commit [71be766ca4281307ce0ca09e6e1265df8882e941](https://github.com/Degrading1919/The_Bible_Video_Game/tree/71be766ca4281307ce0ca09e6e1265df8882e941) on 2026-07-22:

- [Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) — identity, authority, roles, sacred events, knowledge separation, codex, schemas, and files.
- [Session 1](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md) — repository state, authority, routing, absences, unknowns.
- [Session 2](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md) — separation of skills, prompts, policy, agents, tools, references, state, and evaluation.
- [Session 3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md) — discovery, invocation, root, progressive disclosure, metadata, permissions, portability, and gaps.
- [Activation Prompts](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md) and [Continuity Handoff](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md) — current prompt/role/handoff examples, not skill mechanics.

### B. Current official OpenAI/Codex documentation

Living pages in the freshly fetched manual, accessed 2026-07-22; no page-level dates or documentation SHA were available:

- [Build skills](https://learn.chatgpt.com/docs/build-skills).
- [Skills & Plugins](https://learn.chatgpt.com/docs/skills-and-plugins).
- [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security).
- [Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md).

### C. Open specification and creator guidance

- [Agent Skills specification](https://agentskills.io/specification), living page accessed 2026-07-22. Supporting repository head inspected: [agentskills/agentskills@38a2ff82958afee88dadf4831509e6f7e9d8ef4e](https://github.com/agentskills/agentskills/tree/38a2ff82958afee88dadf4831509e6f7e9d8ef4e), dated 2026-07-10; its [README](https://github.com/agentskills/agentskills/blob/38a2ff82958afee88dadf4831509e6f7e9d8ef4e/README.md) records the purpose, loading stages, and licenses.
- [Best practices](https://agentskills.io/skill-creation/best-practices).
- [Optimizing descriptions](https://agentskills.io/skill-creation/optimizing-descriptions).
- [Evaluating skill output quality](https://agentskills.io/skill-creation/evaluating-skills).
- [Using scripts](https://agentskills.io/skill-creation/using-scripts).

### D. Actual official skill files

Inspected at official OpenAI repository commit [49f948faa9258a0c61caceaf225e179651397431](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431), dated 2026-06-24. The repository is now deprecated for distribution, so these are dated implementation evidence.

- [skill-creator/SKILL.md](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator/SKILL.md).
- [gh-fix-ci/SKILL.md](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.curated/gh-fix-ci/SKILL.md).
- [pdf/SKILL.md](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.curated/pdf/SKILL.md).

### Evidence limits

This session does not claim controlled experimental proof that one anatomy guarantees success. Official guides establish format and recommendations; packages provide examples; project recommendations remain recommendations until Session 15 evaluation and Session 17 forward testing. No engine-specific skill was assessed because the project has no authoritative implementation stack. No external skill was accepted for reuse, and no final skill catalog was produced.

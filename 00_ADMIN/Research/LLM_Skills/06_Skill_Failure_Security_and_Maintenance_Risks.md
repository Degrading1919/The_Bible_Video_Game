# Skill Failure, Security, and Maintenance Risks

**Session:** 06 of 18
**Research cutoff:** 2026-07-22
**Repository context:** `Degrading1919/The_Bible_Video_Game` at predecessor commit [`622cc9585d398f02ab5c7ffddbb9448d9e5eb334`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/622cc9585d398f02ab5c7ffddbb9448d9e5eb334)
**Scope:** Failure, degradation, security, repository-safety, and maintenance risks in reusable LLM skills, agent instructions, role prompts, and third-party skill packages. This report derives safeguards for a later skill-builder; it does not create a security skill, implement the builder, select an engine, or produce a project skill catalog.

## Evidence and status conventions

Statements are labeled **Finding** (direct evidence), **Inference** (reasoned consequence), **Recommendation** (proposed control), **Unverified** (not established), or **Project requirement** (current project authority). Evidence uses Session 5's Strong/Moderate/Weak/Promotional/Speculative scale. Likelihood is qualitative: **demonstrated** was observed, **likely** has ordinary exposure, **possible** has an established mechanism but unknown frequency, and **unknown** cannot be estimated. Impact is project-specific.

## 1. Risk taxonomy

The central risk is not merely that a skill produces bad prose. A reusable package can fail at selection, reasoning, execution, validation, governance, or maintenance, and those failures can reinforce one another.

| Risk family | Failure surface | Typical consequence | Primary control owner |
|---|---|---|---|
| Invocation and context | False trigger, missed trigger, collision, excessive loading, anchoring | Irrelevant or conflicting instructions occupy context and steer the task | Skill description, routing tests, explicit workflow |
| Engineering quality | Overengineering, speculative abstraction, untested code, weakened errors, test distortion | A polished patch is larger, less reliable, or behaviorally wrong | Workflow gates, repository tests, diff review |
| Security and supply chain | Prompt injection, malicious scripts, broad permissions, dependency substitution, exfiltration | Code/data exposure, unauthorized effects, compromised validation | Sandbox, approvals, package audit, least privilege |
| Git and repository safety | Broad staging, overwrite, destructive reset, force push, stale-head commit | Lost or misattributed work and broken authority history | Git checks, branch protection, human publication gate |
| Staleness and maintenance | Engine/API/model drift, dead references, license change, dependency drift | Previously correct guidance becomes harmful or unverifiable | Compatibility metadata, scheduled review, reevaluation |
| Authority and persona | Role theater, duplicated protocol, suppressed uncertainty, silent role blending | Confident output overrides the project's actual source hierarchy | Master Protocol, composition trace, human decision gates |
| Evaluation integrity | Contaminated baseline, narrow verifier, metric gaming, selected showcases | A failing skill is approved because it looks or scores successful | Clean fixtures, independent review, scenario-level floors |
| Failure transparency | Assumed tools, hidden command failures, fabricated validation, suppressed warnings | The artifact claims completion without evidence | Fail-closed completion contract and retained logs |

**Finding - Strong:** Skills are not beneficial by default. SkillsBench reported regressions on 16 of 84 tasks; SWE-Skills-Bench reported no gain for 39 of 49 skills and degradation for three ([SkillsBench](https://arxiv.org/abs/2602.12670); [SWE-Skills-Bench](https://arxiv.org/abs/2603.15401)).

**Project requirement:** The [Master Assistant Protocol at the predecessor commit](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) remains above conditional skills. The player-as-witness premise, source-category separation, protected sacred events, era-appropriate knowledge, in-world/player-codex separation, and schema-first rules cannot be delegated to a skill that might not activate.

## 2. Evidence-backed failure cases

### 2.1 Curated skills produced both gains and regressions

**Finding - Strong:** SkillsBench's human-curated condition raised mean pass rate from 24.3% to 40.6% across its included tasks, yet 16 of 84 tasks regressed. The software-engineering domain improved only 4.5 percentage points, far below the overall gain. Self-generated skills averaged 1.3 points below the no-skill baseline; the reported Codex self-generated condition was 5.6 points below its no-skill baseline. Four-or-more skills yielded a smaller observed gain than one-to-three, and the study's “comprehensive” size class had a negative average. Token use and estimated cost also rose for the reported Codex condition ([paper](https://arxiv.org/abs/2602.12670)).

**Inference:** Relevance, size, and interaction matter; an average gain can hide misdirection on a particular task. Size/count comparisons were observational, so they establish no universal maximum.

### 2.2 Public SWE skills mostly did not improve pass rate

**Finding - Strong with preprint caveat:** SWE-Skills-Bench reported a mean gain of 1.2 percentage points; 39 of 49 skills produced no pass-rate improvement, seven improved by as much as 30 points, and three degraded by as much as 10 points. Mean token use increased 10.5%, with some skill-level increases far larger. The authors identify version mismatch, task-context conflict, and excess instructions/context as regression mechanisms ([paper](https://arxiv.org/abs/2603.15401); [repository at `95b3ce51...`](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1)).

**Project consequence:** generic engine/framework guidance must not be imported before the repository establishes its stack. No production engine, language, executable schema, build system, or test harness is authoritative at this predecessor ([Session 1](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md)).

### 2.3 A benchmark baseline was contaminated by skills

**Finding - Moderate:** SkillsBench's public [skill-pollution audit](https://github.com/benchflow-ai/skillsbench/blob/5720102e3d6b0d3471b9715995ff96144d9eefb7/docs/skills-research/skill-pollution-trial-summary.md) records 15 pre-fix “no-skill” trials in which skills were accidentally present in the image; three successful baseline trials were clearly skill-assisted. The build was corrected to stop baking skills into no-skill images.

**Recommendation:** prevent intervention leakage through mounts, prior outputs, or cached context by verifying clean baselines, recording mounted resources, and preserving audit logs.

### 2.4 Deterministic checks can still reward shallow compliance

**Finding - Moderate:** The inspected SWE-Skills-Bench `python-resilience` tests use some structural signals such as names, imports, numbers, and patterns. They are repeatable, but do not exhaustively prove runtime resilience ([skill](https://github.com/GeniusHTX/SWE-Skills-Bench/blob/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1/skills/python-resilience/SKILL.md); [pinned repository](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1)).

**Inference:** repeatable checks can reward visible structure while leaving maintainability, gameplay feel, reverence, or historical coherence unmeasured. “Tests pass” is necessary where applicable, not sufficient.

### 2.5 Combined interfaces confound the cause of success

**Finding - Strong for the combined intervention:** SWE-agent's agent-computer interface improved issue resolution in a controlled ablation, but it changed instructions, editing/search tools, syntax feedback, demonstrations, and context management together ([NeurIPS 2024 paper](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf); [repository at `3ea751c0...`](https://github.com/SWE-agent/SWE-agent/tree/3ea751c087f32b16e039a2233dd6eefecef325d5)).

**Recommendation:** report the whole environment and use component ablations before attributing a combined intervention's result to skill text.

### 2.6 Codex security boundaries do not come from skill prose

**Finding - Official current documentation:** Codex distinguishes sandbox mode (what commands can technically do) from approval policy (when the user must approve). Local defaults restrict writes to the active workspace and turn command network access off. The documentation warns that web pages and dependency READMEs can contain prompt injection, and that enabling internet access introduces exfiltration, malware/dependency, and license risks ([Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security); [Agent internet access](https://learn.chatgpt.com/docs/cloud/internet-access), accessed 2026-07-22).

**Finding - Moderate:** Session 3 established from official sources that a skill does not grant shell, network, filesystem, MCP, Git, credentials, or approval bypass; scripts are ordinary executable code; and public documentation does not define deterministic precedence for conflicting active skills ([Session 3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md)).

**Unverified:** The small Session 5 audit found no malicious package; the mechanism is established, not its prevalence.

## 3. Invocation and context failures

### Incorrect automatic invocation

Codex may select a skill when the task matches its description, but the current public sources do not publish a deterministic matcher, confidence threshold, or collision rule. Catalog metadata can be shortened or omitted when the catalog exceeds its context budget ([Build skills](https://learn.chatgpt.com/docs/build-skills); [Session 3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md)). A broad “game expert” description can trigger on research, design, code, art, or theology without owning any of them. A narrow description can miss paraphrases.

Test positive, paraphrased, embedded, terse, near-miss, and adversarial triggers. High-impact workflows should be user-invoked-only where supported, state their selection, and stop on mismatched preconditions.

### Context overload, excessive length, and contradiction

Progressive disclosure delays loading, but selected bodies, references, scripts' outputs, repository files, and conversation history still consume context. Overly long skills increase the chance that exceptions obscure the main invariant. Redundant skills repeat rules, while contradictory skills leave precedence to undocumented model behavior. Evidence from SkillsBench and SWE-Skills-Bench shows that additional content or skills do not guarantee improvement.

Prevention is not an arbitrary word cap. Keep every-run procedure in `SKILL.md`, route conditional detail directly, remove duplicated authority, and require each paragraph to affect a decision, action, stop, or output. Composition needs an explicit order and controlling authority.

### Prompt anchoring and overfitting to examples

A concrete example can become more salient than an abstract rule. The model may copy its engine, file path, schema, proper nouns, or output headings into a different task. Evaluation fixtures can also leak the expected solution. Session 4 therefore recommends invariants before examples, varied fixtures, counterexamples, and held-out tests ([Session 4](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md)).

Examples must not silently select an engine, schema, canon treatment, or disputed geography; their values are never project authority.

## 4. Engineering-quality failures

### Overengineering, file proliferation, and premature abstractions

Role prompts that reward thoroughness or “production-ready architecture” can cause configuration for hypothetical needs, new dependencies, wrappers, managers, interfaces, and files with no current consumer. This risk is acute while the implementation stack is unknown. A skill can make speculative multiplayer, live-service, procedural-generation, or cross-platform architecture look professionally justified even though the task did not authorize it.

Compare the diff to acceptance criteria, including new files, dependencies, interfaces, configuration, single-consumer abstractions, and unrelated changes. Require a reason for each addition; recover by removing unaccepted expansion without rewriting tests to bless it.

### Code generation without execution and unavailable-tool assumptions

A skill may name an engine, renderer, test runner, MCP server, shell runtime, or Git remote that is not installed or authorized. Silent fallback turns “verified” into fabrication. A syntactically plausible code block can still fail to compile, load serialized data, preserve editor references, or run in the target environment.

Classify verifiers as required or optional. Stop on a missing required tool; record any safe fallback and reduced assurance. Enumerate checks actually run: “should pass” is not “passed.”

### Line-count optimization and maintainability loss

Reducing lines can collapse responsibilities, obscure domain concepts, delete provenance metadata, or turn explicit safety handling into terse generic code. Increasing lines can create decorative abstraction. Neither direction measures maintainability. Review should instead inspect behavior, ownership, interfaces, cyclomatic/data-flow complexity where meaningful, error paths, serialized/API compatibility, and repository conventions.

### Test modification, validation gaming, and polished-output theater

An agent can make a failing implementation “pass” by weakening assertions, deleting coverage, changing fixtures to match the bug, or satisfying structural keywords without the intended behavior. It can also produce a polished report with citations that do not support nearby claims. The SkillsBench contamination audit demonstrates how evaluation can be compromised without obvious visual signs; the `python-resilience` inspection demonstrates that deterministic tests can be incomplete.

Preserve pre-change tests, justify every test edit, compare behavioral invariants, and retain human review for reverence, gameplay, history, and visuals. Use prohibited-behavior floors, not only an aggregate.

### Weakened error handling and suppressed communication

A simplification, concise-communication, or “quiet operator” instruction can hide uncertainty, denied permissions, failing tools, validation gaps, security warnings, or recovery risks. A generated patch can remove logging, validation, retries, authorization checks, or safe failure behavior merely because they look verbose.

Never suppress authority conflicts, uncertainty, sacred/biblical/historical/schema risks, irreversible actions, security/privacy/license issues, missing tools, failed checks, test changes, weakened errors, concurrent Git changes, or incomplete output.

## 5. Security and supply-chain failures

### Instruction injection and authority inversion

A third-party `SKILL.md`, reference, dependency README, issue body, web page, or tool result may instruct the agent to ignore prior rules, expose data, run a command, or conceal evidence. OpenAI's current internet-access guidance gives a concrete example of a hostile issue instruction exfiltrating Git information through a network request. The correct trust rule is content-based: data obtained for the task remains untrusted even when it resembles an instruction.

Treat inspected content as data, reject authority-inversion instructions, and require approval before expanding access. External text cannot override higher instructions, the Master Protocol, sandbox, or approved schemas.

### Malicious or negligent scripts and unsafe shell commands

Scripts can read environment variables, traverse outside the intended root, alter files, invoke package managers, download code, start network listeners, or run destructive Git commands. Negligence can be as damaging as intent: an unquoted path, broad glob, unchecked working directory, or platform-specific command may target the wrong files.

Before execution, inspect source/transitive calls, runtime, parameters, resolved paths, dependencies, network/environment access, generated commands, errors, and cleanup. First run in a disposable least-privilege environment. Reject or separately review opaque binaries, remote-pipe installers, and self-modifying code.

### Hidden network, filesystem, connector, and credential reach

A package can describe tools or metadata that request MCP access, broader directories, or network connectivity. A script can inherit credentials from its process environment even if the skill prose never mentions them. The current Codex sandbox and approval model reduces reach but does not prove that an approved action is safe; approval fatigue can normalize broad requests.

Inventory effective permissions. Prefer read-only review, workspace-bounded writes, no network unless necessary, allowlists, and scoped credentials. Authentication is not publication authority.

### Dependency and provenance risk

Install scripts and package managers can resolve a different artifact after a registry update, typosquatting event, compromised maintainer account, or changed transitive dependency. A copied example may carry incompatible license terms or unattributed source material. OpenAI's deprecated skills catalog explicitly put licenses at individual skill directories rather than granting one catalog-wide license ([README at `49f948f...`](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/README.md)). Repository visibility and popularity are not licenses.

Pin revisions and executable dependencies, preserve notices/change records, and reject ambiguous rights. Scripture translations, assets, and historical datasets need item-specific provenance and licenses.

## 6. Git and repository safety failures

Skills have no privileged Git safety layer. Broad staging can include unrelated work; stale branches can miss newer authority; reset/clean can erase files; force pushing can rewrite history; and secrets or transient citations can be committed. Correct content at the wrong path can also become falsely authoritative.

Record root, branch/head, status, allowed paths, and concurrent changes. Stage explicit paths, inspect the staged diff, and check remote head immediately before publication. Re-audit moved inputs; use fast-forward publication, never force push, and require explicit commit/push authority. `reset --hard` can overwrite tracked changes and forced updates can discard remote history ([git-reset](https://git-scm.com/docs/git-reset); [git-push](https://git-scm.com/docs/git-push), accessed 2026-07-22).

Plan recovery before action with a known prior SHA and non-destructive reversal path; otherwise require a human gate.

## 7. Staleness and maintenance failures

SWE-Skills-Bench demonstrates version mismatch as a regression mechanism. Stale guidance can call removed APIs, assume old serialization, recommend vulnerable dependencies, or claim changed capabilities. Dead/mutable links undermine auditability; dependency or model drift can change behavior without changing `SKILL.md`.

Every externally grounded package needs:

1. repository/path/commit and exact file provenance;
2. applicable license and notices;
3. supported/unsupported tool or engine versions;
4. the Codex surface and environment used for validation;
5. a last-reviewed date and evidence cutoff;
6. pinned dependencies or a justified update policy;
7. permanent links for audited files;
8. trigger, output, failure, and security regression fixtures; and
9. an invalidation rule for changes to authority, schemas, engine, model/harness, permissions, or dependencies.

**Recommendation:** review on relevant authority, dependency, source, environment, or evaluation changes. Quarantine stale skills until reevaluation; do not patch them silently during unrelated work.

## 8. Project-authority and persona-drift failures

Authoritative tone is not evidence. Expert personas can lack sources, stack facts, or decision authority; multiple prompts can fragment ownership and handoffs. Copying the Master Protocol creates a stale competitor, while leaving universal rules only in a conditional skill makes them unreliable.

Project-specific high-impact failures include:

- turning the player from witness into author or savior;
- making sacred figures or miracles ordinary sandbox targets or powers;
- presenting interpretation, reconstruction, tradition, or invention as Scripture;
- leaking later biblical knowledge into an earlier in-world perspective;
- treating disputed chronology, geography, ethnicity, or material culture as settled;
- inventing schemas, engine facts, or approved project files;
- removing source/confidence metadata during simplification;
- allowing a role or skill to approve theology, canon, sacred-event, major creative, schema, toolchain, or publication decisions reserved for the user; and
- duplicating or contradicting the Master Assistant Protocol.

Require a trace of authority, active skills/role, consulted files, decisions, conflicts, and validation. Lower workflows must follow higher authority or stop; never blend incompatible personas silently.

**Inference - High confidence:** project constraints need layered enforcement: governance, schemas/validators, runtime/tests, task workflows, and human review. Skill prose alone is insufficient.

## 9. Prevention and detection matrix

Each row groups related failure modes and supplies all nine required elements. Builder requirements remain Session 16 inputs.

| ID and major risk | Mechanism | Evidence | Likelihood | Impact | Detection | Prevention | Recovery | Builder requirement | Enforcement layer |
|---|---|---|---|---|---|---|---|---|---|
| R1 False or missed automatic invocation | Broad/ambiguous descriptions trigger near misses; narrow descriptions miss paraphrases; catalog truncation hides metadata | Official Codex discovery model; matcher details unverified | Likely | High | Positive, paraphrased, embedded, terse, near-miss, adversarial trigger suite | Intent/artifact language, nearest exclusions, explicit-only for high-impact work | Stop, unload/reroute, preserve task state, log false trigger | Generate and run trigger/anti-trigger fixtures; support manual-only policy | Metadata, evals, user invocation |
| R2 Repository or task-instruction conflict | Skill procedure competes with current files or higher authority; active-skill precedence is undocumented | Session 3 official-source synthesis; benchmark task-context regressions | Demonstrated | Critical | Authority preflight and composition trace; conflict fixture | Name controlling sources and never-override rules; explicit phase order | Halt before side effect; apply higher authority or escalate | Require authority map, conflict behavior, and stop condition | System/developer/user rules, Master Protocol, skill body |
| R3 Excess context, overly long, redundant, or contradictory skills | Irrelevant bodies/references dilute attention and create inconsistent commands | SkillsBench size/count subgroups; SWE-Skills-Bench excess-context mechanism | Demonstrated | High | Token/resource log, duplicated-rule scan, ablation | Progressive disclosure, one coherent job, direct references, no cloned policy | Disable/remove redundant package; retest clean context | Justify each file/section and compare against a lean baseline | Authoring review, context budget, evals |
| R4 Example anchoring and overfitting | Concrete fixture values override general invariants or leak answers | Session 4 synthesis; benchmark contamination demonstrates leakage class | Possible | High | Held-out varied cases and example-value scan | Invariants first, varied examples, counterexamples, separate evals | Remove leaked values, rebuild fixtures, rerun baseline | Keep examples conditional and generate held-out cases | Skill references, eval isolation, review |
| R5 Authoritative role-play, persona proliferation, suppressed uncertainty | Professional tone substitutes for evidence; roles silently blend or overclaim ownership | Project authority; no inspected study validates persona authority | Likely | Critical | Claim-source audit, role/decision-owner trace, uncertainty checks | Define owned/recommended/forbidden decisions; source labels; human gates | Retract unsupported claims, restore labels, re-review affected artifacts | Reject costume-only skills; require evidence and handoff contract | Master Protocol, role governance, human review |
| R6 Overengineering, unnecessary files, premature abstractions | “Best practice” incentives introduce hypothetical architecture or dependencies | Benchmark mismatch evidence; current stack unknown | Likely | High | Acceptance-to-diff map; file/dependency/interface counts | Smallest-valid-change gate; reason for each new artifact | Revert expansion while retaining required behavior; rerun tests | Enforce scope/non-goals and new-file/dependency justification | Skill workflow, diff review, tests |
| R7 Code without execution, unavailable tools, silent tool failure | Skill assumes engine/runtime/MCP/auth; reports hypothetical checks as completed | Official capability boundary; unavailable behavior not standardized | Likely | Critical | Capability preflight; command/result ledger; artifact existence checks | Required/optional tool classification and fail-closed completion | Report exact gap, undo partial effects, resume only after capability exists | Generate preconditions, fallback limits, and truthful completion language | Sandbox/tool host, skill body, validator |
| R8 Line-count optimization or silently weakened error handling | Simplification deletes validation, logs, authorization, provenance, or explicit concepts | Mechanism not separately quantified; project safeguards make exposure material | Possible | High | Behavior/error-path diff; invariant and regression review | Optimize clarity/ownership, not lines; preserve safety invariants | Restore prior behavior from reviewed diff; add regression case | Require preservation list and forbid code-golf/test accommodation | Review, tests, human approval |
| R9 Tests modified to accommodate failure, evaluation gaming, polished theater | Agent weakens assertions or targets superficial verifier signals; output looks complete | SkillsBench pollution audit; incomplete structural checks in inspected benchmark | Demonstrated | Critical | Test-diff review, independent assertions, runtime/visual/human checks | Freeze baseline, predeclare rubric, scenario-level floors | Reject result, restore tests, rebuild clean runs | Separate production and eval artifacts; require negative cases and audit logs | CI/tests, evaluation harness, independent review |
| R10 Suppressed safety-relevant communication | Concision or success pressure hides failures, uncertainty, security, or destructive risk | Official approval model requires visible gates; project response rules | Possible | Critical | Check final/trace for never-suppress items | Explicit never-suppress list; meaningful phase updates | Reopen decision, disclose omission, reassess downstream work | Include mandatory warning/blocker/failure fields | Developer/user rules, skill output contract |
| R11 Prompt injection through skill/reference/web/dependency content | Untrusted text masquerades as instruction and requests data or action | Official Codex internet-access example | Likely when external content is read | Critical | Instruction/data boundary review; suspicious command/network scan | Least privilege, trusted-source routing, ignore lower-authority injection | Cut network, rotate exposed secret if any, inspect logs/diff, quarantine input | Add injection checks and reject authority-inversion text | Sandbox/network policy, approvals, skill intake |
| R12 Untrusted code, malicious/negligent scripts, unsafe shell | Executable reads secrets, traverses paths, downloads code, mutates repo, or ignores errors | Official scripts/capability model; incidence in audited packages unverified | Unknown/possible | Critical | Full source/transitive inspection; static scan; disposable dry run | No opaque executables; bounded literal paths; pins; no remote-pipe install | Terminate, isolate, restore from clean SHA, rotate credentials, audit effects | Inspect every script and emit a side-effect manifest before execution | Sandbox, code review, package policy |
| R13 Hidden network/filesystem/MCP permissions | Metadata or subprocesses gain reach not evident in main prose; inherited credentials amplify impact | Official sandbox/network/MCP model | Possible | Critical | Effective permission and environment inventory | Read-only review, workspace writes, network allowlists, scoped credentials | Revoke access, audit calls/files, restore affected state | Declare required tools/data/access and deny undeclared expansion | Host policy, managed config, human approval |
| R14 Dependency/supply-chain drift | Mutable dependencies, typosquatting, compromised upstream, unpinned transitive code | Official internet guidance identifies malware/vulnerable dependency risk | Possible | Critical | Lockfile/hash/SBOM review; dependency diff and advisory checks | Pin/verify, minimize dependencies, trusted registries, offline fixtures | Quarantine, roll back pins, rotate secrets, reevaluate outputs | Require dependency inventory, version policy, and no-install fallback | Package manager, repository policy, security review |
| R15 Licensing/provenance ambiguity | Visible/copied material lacks grant, notices, attribution, or compatible terms | OpenAI catalog's per-skill license model; Session 5 audits | Likely in casual copying | High | File-level license and origin inventory | Reject ambiguity; retain notices/change records; do not infer rights | Remove affected content, replace with licensed original, document correction | Block completion without provenance/license decision for every reused file | Intake review, legal/human gate, Git record |
| R16 Irreversible Git/repository action | Broad stage/reset/clean/force push or stale-head publication loses competing work | Git official command semantics; skills have no special Git safety | Possible | Critical | Root/branch/head/status/staged-diff/remote-head checks | Explicit paths, fast-forward only, no destructive default, publication authority | Stop; use known prior SHA/revert where safe; escalate loss risk | Generate Git preflight, recovery plan, and explicit commit/push gate | Git protections, branch rules, approvals |
| R17 Stale engine/API/model guidance and version incompatibility | Package encodes obsolete API, format, model routing, or nonexistent stack | SWE-Skills-Bench version-mismatch regressions | Demonstrated | High | Compare applicability metadata with live versions and authority | Pin support ranges; discover stack; refuse mismatches | Disable/quarantine, update through review, rerun all affected evals | Require compatibility, evidence date, and invalidation triggers | Metadata, maintenance process, tests |
| R18 Dead links, reference drift, and maintenance neglect | Mutable URLs or changed sources erase evidence; package remains enabled after assumptions change | Pinned audits show reproducibility need; incidence not quantified | Likely over time | High | Link/source/commit checks; dependency and authority diff | Permanent links, last-reviewed record, owner and review triggers | Mark unverified, replace source, rerun impacted claims/tests | Produce maintenance manifest and stale-state behavior | Git history, scheduled/event review, human owner |
| R19 Master Protocol duplication or contradiction | Conditional copy becomes stale competing policy or fragments persona authority | Project chain of authority; Session 4 anti-pattern analysis | Likely if copied | Critical | Duplicate-text/semantic review; live-authority path check | Keep canonical rules in protocol; skill reads current file and operationalizes only task steps | Remove duplicate, reconcile artifact against current authority | Forbid copied controlling policy; require live-reference and conflict stop | Permanent repository instructions, builder validator |
| R20 Silent non-compliance when tools fail | Agent proceeds with partial inputs, fabricates inspection/validation, or hides denied capability | Official docs leave absent-tool response to workflow; Session 3 requirement | Possible | Critical | Failure injection, missing-tool cases, evidence/result ledger | Fail closed for required capabilities; bounded documented fallback only | Withdraw completion claim, identify affected outputs, resume after repair | Generate failure states, retry bounds, and observable completion | Skill body, evals, developer/user rules |

## 10. Negative evidence ledger

The columns match Session 5's evidence ledger exactly.

| Claim or practice | Evidence source | Evidence type | Strength | Transferability | Risks/caveats |
|---|---|---|---|---|---|
| Curated skills can regress individual tasks even when the aggregate improves. | [SkillsBench paper](https://arxiv.org/abs/2602.12670) | Controlled repeated benchmark; 16/84 task regressions | Strong | High | Preprint; task distribution differs from this project. |
| Most tested public SWE skills produced no pass-rate improvement and some degraded it. | [SWE-Skills-Bench paper](https://arxiv.org/abs/2603.15401) | Paired executable-test benchmark | Strong | High | Preliminary results; one model/harness family in reported setup. |
| Self-generated skills can underperform no-skill baselines. | [SkillsBench paper](https://arxiv.org/abs/2602.12670) | Controlled generated-skill condition | Strong | High for requiring review/evaluation | Does not prove every generated draft is harmful. |
| Larger or more numerous skill packages are not reliably better. | [SkillsBench paper](https://arxiv.org/abs/2602.12670) | Observational subgroup comparison | Moderate | High | Not a randomized size/count ablation; no universal cutoff follows. |
| Version mismatch, task conflict, and excess context can cause SWE regressions. | [SWE-Skills-Bench paper](https://arxiv.org/abs/2603.15401) | Reported failure analysis | Strong | High | Exact mechanisms may interact; project stack remains unknown. |
| Baseline contamination can make skill evaluations measure the wrong condition. | [SkillsBench pollution audit](https://github.com/benchflow-ai/skillsbench/blob/5720102e3d6b0d3471b9715995ff96144d9eefb7/docs/skills-research/skill-pollution-trial-summary.md) | Primary incident/audit record | Moderate | High | This report does not independently reconstruct every published aggregate. |
| Deterministic tests can be incomplete and reward structural compliance. | [`python-resilience` and repository at `95b3ce51...`](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1) | Actual skill/test inspection | Moderate | High | Incompleteness of one verifier does not invalidate deterministic testing generally. |
| A combined instruction/tool intervention does not isolate the value of prompt text. | [SWE-agent NeurIPS paper](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf) | Peer-reviewed combined ACI ablation | Strong | High | Supports the full interface, not a text-only failure claim. |
| Skill prose does not grant shell, network, files, MCP, Git, or approvals. | [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security) and [Session 3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md) | Official product documentation synthesis | Strong for capability boundary | High | Exact behavior varies by surface/configuration; inspect effective policy. |
| Prompt injection from web or dependency content can expose data or drive unsafe changes. | [Agent internet access](https://learn.chatgpt.com/docs/cloud/internet-access) | Official threat guidance and example | Moderate | High when external inputs are used | Does not measure attack prevalence in skill packages. |
| Enabled network access adds exfiltration, malware/dependency, and licensing exposure. | [Agent internet access](https://learn.chatgpt.com/docs/cloud/internet-access) | Official threat guidance | Moderate | High | Sandbox/network controls reduce but do not eliminate risk. |
| Structural validation does not demonstrate semantic benefit, project fit, or safety. | [OpenAI `skill-creator` at `49f948f...`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator) and Session 5 audit | Actual workflow/script inspection | Moderate | High | Structural validation remains useful as one layer. |
| Repository-level visibility or a catalog entry does not establish reusable rights. | [OpenAI skills README at `49f948f...`](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/README.md) | Official repository licensing statement | Moderate | High | Exact package/file terms require separate inspection. |
| Git force/reset operations can discard work or history. | [git-reset](https://git-scm.com/docs/git-reset) and [git-push](https://git-scm.com/docs/git-push) | Official command documentation | Strong for semantics | High | Risk depends on flags, state, protections, and recovery data. |
| An engine-generic “expert” skill cannot establish this project's implementation stack. | [Session 1](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md) | Pinned live-repository audit | Strong for repository state | Critical | Must be re-audited if later authority files select a stack. |
| A conditional skill cannot safely be the only carrier of universal sacred/project rules. | [Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) and [Session 4](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md) | Project authority plus architectural inference | Moderate | Critical | Later sessions must map exact enforcement layers; this is not a final catalog. |

## 11. Third-party skill intake checklist

An intake decision applies to the exact pinned package, not its name or upstream reputation. A later revision is a new intake event when relevant files, dependencies, licenses, or permissions change.

### A. Identity and complete package capture

- [ ] Record repository, package path, commit SHA/date, retrieval date, and platform.
- [ ] Enumerate all files, including hidden metadata, references, scripts, assets, tests, licenses, and lockfiles.
- [ ] Resolve every link and transitive file named by `SKILL.md`; reject deep or unexplained reference chains.
- [ ] Record the claimed purpose separately from demonstrated behavior.
- [ ] Classify it accurately: skill, agent prompt, MCP config, command wrapper, demo, or reference.

### B. Authority and instruction review

- [ ] Read the full `SKILL.md` and every referenced instruction file as untrusted input.
- [ ] Flag requests to ignore higher instructions, conceal actions/results, bypass approval, broaden scope, or redefine project authority.
- [ ] Compare triggers, process, outputs, and stops with current authority and conventions.
- [ ] Identify duplicated or contradictory rules and decide which canonical source owns them.
- [ ] Check for invented engine, API, path, schema, role, canon, geography, chronology, or permission assumptions.
- [ ] Confirm uncertainty, evidence, safety, and failure reporting are not suppressed.

### C. Executable and dependency review

- [ ] Inspect every script line and transitive subprocess; do not rely on filename or author reputation.
- [ ] Record runtime, inputs/outputs, working directory, paths, mutations, network/environment access, errors, and cleanup.
- [ ] Reject remote-pipe installers, opaque/obfuscated executables, self-modification, destructive defaults, broad globs, and unresolved targets.
- [ ] Enumerate direct and transitive dependencies; verify pins, lockfiles, hashes/signatures where available, registries, and version compatibility.
- [ ] Search for credential reads, uploads, telemetry, background services, local/private network access, privilege escalation, and Git-history operations.
- [ ] Execute only after source review, first in a disposable least-privilege environment with non-sensitive fixtures.

### D. Permissions and data-flow review

- [ ] State minimum read/write roots, network destinations/methods, tools, credentials, and approvals.
- [ ] Compare declared needs to effective host capability; reject undeclared expansion.
- [ ] Keep review read-only; use workspace-bounded writes for the clean test; leave network off unless essential.
- [ ] Confirm no source code, project files, Scripture datasets, credentials, or private findings can be sent to an unapproved destination.
- [ ] Verify failure is safe when access is denied, authentication expires, or a tool is unavailable.

### E. License, provenance, and version fitness

- [ ] Inspect the license governing each reused file, script, example, template, asset, font, image, dataset, and embedded excerpt.
- [ ] Preserve required license copies, notices, attribution, source offers, and modification notices.
- [ ] Reject missing, ambiguous, incompatible, or unverifiable rights rather than infer permission.
- [ ] Compare supported engine/tool/API/model versions with current authority; do not infer a stack.
- [ ] Replace mutable links with commit-pinned permalinks and record source dates.
- [ ] Review theological/historical sources and confidence separately from software license compatibility.

### F. Clean-context behavioral evaluation

- [ ] Predefine baseline, trigger, near-miss, adversarial, missing-input/tool, conflict, and failure cases.
- [ ] Verify the baseline contains no skill files, mounted references, previous outputs, or leaked expected answers.
- [ ] Capture environment, SHA, permissions, dependencies, prompt/context, commands, outputs, cost, and failures.
- [ ] Measure correctness, scope, unnecessary files/dependencies, false triggers, authority compliance, uncertainty, and project-specific prohibited behavior.
- [ ] Inspect the actual diff and logs; do not approve from a polished summary or aggregate score alone.
- [ ] Require human review for sacred-event treatment, biblical/historical honesty, visual/cultural authenticity, gameplay meaning, and license/provenance judgment.

### G. Decision and maintenance record

- [ ] Choose only: Adopt as-is, Adapt, Extract principles only, Monitor, or Reject; explain evidence and caveats.
- [ ] Prefer Adapt/Extract over direct reuse when project authority, stack, or safety controls differ.
- [ ] Identify owner, last-reviewed date, invalidation triggers, rollback/disable path, retained fixtures, and reevaluation threshold.
- [ ] Quarantine rejected or stale code so it cannot be invoked or executed accidentally.
- [ ] Treat an upstream update as untrusted until the relevant diff, dependencies, permissions, license, and regression cases pass again.

**Immediate rejection conditions:** concealed or unreviewable executable behavior; authority inversion; secret collection or unapproved exfiltration; destructive default; unresolved license; false claims of validation; required broad access without a bounded reason; target-stack mismatch with no safe refusal; or instructions that weaken protected sacred, source, schema, uncertainty, test, error-handling, or Git safeguards.

## 12. Required safeguards for the future skill-builder

The future builder should produce or verify these controls for every candidate; they are Session 16 inputs, not an implementation.

1. **Whether-to-build gate:** classify whether the recurring need belongs in a skill, permanent instruction, role/agent, reference, script, schema, validator, test, or one-off prompt. Reject a skill that would only duplicate policy or store a finished answer.
2. **Authority preflight:** locate current controlling files and repository state; identify user-owned decisions; stop on material conflict or absence. Never embed a stale copy of the Master Protocol.
3. **Bounded purpose and non-goals:** one coherent job, explicit prohibited expansion, target artifacts, and allowed paths. No final catalog creation as a side effect.
4. **Invocation safety:** precise description, nearest exclusions, positive and near-miss fixtures, and explicit-only configuration for high-impact/costly workflows where supported.
5. **Context economy:** keep every-run procedure concise, route conditional references directly, and justify each added file. Measure rather than assume context savings.
6. **Capability truthfulness:** declare prerequisites; preflight tools/auth/versions/permissions; distinguish required from optional; stop rather than fabricate missing inspection or validation.
7. **Least privilege:** no permission is granted by prose. Default to read-only inspection, workspace-bounded writes, network off, scoped credentials, and explicit human approval for broader or irreversible effects.
8. **Executable manifest:** enumerate and inspect every script and dependency; record side effects, paths, network, environment access, pins, errors, and recovery. Reject opaque or unnecessarily executable content.
9. **Security intake:** test prompt injection, authority inversion, untrusted data, denied access, dependency failure, and malicious-command cases in a constrained clean environment.
10. **License and provenance gate:** no adapted file without exact origin, commit, license, notices, and change record. Treat assets/data/Scripture sources separately.
11. **Engineering invariants:** smallest valid change; reason for each file/dependency/abstraction; no test weakening; no silent error-handling reduction; no optimization for line count.
12. **Verification contract:** name structural, test/build, runtime/visual, source, schema, sacred-event, chronology, knowledge-boundary, scope, and human checks that apply. Report only checks actually run.
13. **Evaluation integrity:** pinned baseline and intervention, clean contexts, predeclared metrics, retained negative cases, repeated trials where stochastic, scenario-level failure floors, and audit logs.
14. **Git safeguards:** exact target/root/head/status, narrow staging, staged-diff inspection, remote-head freshness, fast-forward-only publication, recovery plan, and explicit commit/push authority.
15. **Never-suppress list:** surface authority conflicts, uncertainty, sacred/biblical/historical/schema risk, security/license risk, destructive actions, missing tools, failed checks, changed tests, weakened errors, and incomplete work regardless of communication style.
16. **Maintenance record:** tested surface/model/harness, tool versions, evidence cutoff, external SHAs, dependency pins, owner, invalidation triggers, disable/rollback path, and fixtures to rerun.
17. **Composition safety:** declare order, authority, active skills/roles, conflicts, and handoffs; stop on unresolved collision.
18. **Layered project controls:** point to governance, schemas/validators, tests/runtime, and human gates; prose alone cannot enforce sacred boundaries.
19. **Observable completion:** require the artifact, authorized diff, passing required checks, evidence, limitations, and bounded failure behavior.
20. **Reversibility:** document disable, rollback, and replacement without losing authority or user work.

**Unverified and deferred:** No inspected source establishes universal numerical thresholds for false-trigger rate, maximum `SKILL.md` length, acceptable token increase, trial count, or maintenance interval. Session 15 must define project evaluation thresholds, and Session 16 must classify which safeguards are mandatory versus conditional. This session supplies the risks those decisions must cover.

## 13. Source appendix

### Project authority and predecessor reports

- Degrading1919, [The Bible Video Game repository at Session 6 predecessor `622cc9585d398f02ab5c7ffddbb9448d9e5eb334`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/622cc9585d398f02ab5c7ffddbb9448d9e5eb334), accessed 2026-07-22.
- [Master Assistant Protocol at the predecessor commit](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md), controlling project source, accessed 2026-07-22.
- [Session 1 project context and authority map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md), [Session 3 Codex capability map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md), [Session 4 authoring principles](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md), and [Session 5 success evidence](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/05_Demonstrated_Skill_Success_Evidence.md), all pinned to the Session 6 predecessor and accessed 2026-07-22.

### Current official Codex and OpenAI sources

- OpenAI, [Build skills](https://learn.chatgpt.com/docs/build-skills), living documentation accessed 2026-07-22. Relevant to discovery metadata, progressive loading, invocation, and catalog context limits.
- OpenAI, [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security), living documentation accessed 2026-07-22. Relevant to sandbox/approval separation, local workspace/network defaults, network policy, and protected paths.
- OpenAI, [Agent internet access](https://learn.chatgpt.com/docs/cloud/internet-access), living documentation accessed 2026-07-22. Relevant to prompt injection, exfiltration, malware/vulnerable dependency, licensing, domain, and HTTP-method controls.
- OpenAI, [`openai/skills` at `49f948faa9258a0c61caceaf225e179651397431`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431), commit dated 2026-06-24, accessed 2026-07-22; [`skill-creator`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator) and [catalog README](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/README.md). Relevant to structural workflow and package-specific licensing; existence does not demonstrate performance benefit.

### Controlled studies, primary artifacts, and incident evidence

- BenchFlow AI et al., [“SkillsBench: Benchmarking How Well Agent Skills Work Across Diverse Tasks”](https://arxiv.org/abs/2602.12670), arXiv:2602.12670, submitted 2026-02-13; accessed 2026-07-22. Direct controlled skill evidence; preprint.
- BenchFlow AI, [`skillsbench` at `5720102e3d6b0d3471b9715995ff96144d9eefb7`](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7), commit dated 2026-07-18, Apache-2.0, accessed 2026-07-22; [skill-pollution trial audit](https://github.com/benchflow-ai/skillsbench/blob/5720102e3d6b0d3471b9715995ff96144d9eefb7/docs/skills-research/skill-pollution-trial-summary.md).
- GeniusHTX et al., [“SWE-Skills-Bench: Do Agent Skills Actually Help in Real-World Software Engineering?”](https://arxiv.org/abs/2603.15401), arXiv:2603.15401v1, submitted 2026-03-16, explicitly preliminary/work in progress; accessed 2026-07-22.
- GeniusHTX, [`SWE-Skills-Bench` at `95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1`](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1), commit dated 2026-04-14, MIT, accessed 2026-07-22.
- Yang et al., [“SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering”](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf), NeurIPS 2024; and [`SWE-agent` at `3ea751c087f32b16e039a2233dd6eefecef325d5`](https://github.com/SWE-agent/SWE-agent/tree/3ea751c087f32b16e039a2233dd6eefecef325d5), commit dated 2026-07-16, MIT; accessed 2026-07-22.

### Repository-safety references

- Git project, [`git-reset` documentation](https://git-scm.com/docs/git-reset), accessed 2026-07-22. Relevant to working-tree/index overwrite semantics.
- Git project, [`git-push` documentation](https://git-scm.com/docs/git-push), accessed 2026-07-22. Relevant to non-fast-forward and forced-update history risks.

### Evidence limits and stable conclusion

The preprints do not cover this project's sacred/historical constraints. No reviewed source measures malicious-package prevalence or identifies a Session 5 package as malicious.

Stable conclusion: **treat a skill as an untrusted, versioned intervention until its triggers, authority behavior, package tree, permissions, dependencies, license, failures, Git effects, and project outcomes pass a clean-baseline review.** Generic improvement cannot offset a sacred, source, chronology, schema, authority, safety, or repository violation.

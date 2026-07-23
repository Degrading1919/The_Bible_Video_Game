# LLM Skills Deep Research for The Bible Video Game

**Session:** 18 of the sequential LLM-skills program

**Synthesis date:** 2026-07-22

**Repository:** [Degrading1919/The_Bible_Video_Game](https://github.com/Degrading1919/The_Bible_Video_Game)

**Accepted predecessor / inspected head:** [`361f1778fc9c4114ce384e4cb9884cadd7a2f354`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/361f1778fc9c4114ce384e4cb9884cadd7a2f354)

**Evidence cutoff:** 2026-07-22
**Scope:** Final synthesis of Sessions 1-17 and the read-only authoritative assignment; no new broad research, production implementation, schema, engine selection, or project skill catalog.

## Claim and evidence vocabulary

- **Documented behavior:** stated in a current first-party specification or product document.
- **Observed behavior:** reproduced or directly inspected in a pinned package, repository, or run.
- **Finding:** conclusion supported by the cited evidence within its stated scope.
- **Inference:** reasoned transfer from evidence that does not directly test this project.
- **Recommendation:** a proposed project policy or next action, not current repository fact.
- **Unverified:** not established by the inspected evidence or unavailable in the current repository.

Evidence strength uses the assignment's scale: **Strong** (controlled/reproducible comparison or direct authoritative repository fact), **Moderate** (repeated or inspectable primary evidence without clean causal isolation), **Weak** (credible but limited/anecdotal), **Promotional** (benefit claim without adequate outcome evidence), and **Speculative** (plausible but undemonstrated).

## 1. Executive summary

The strongest conclusion is restrained: reusable, human-curated procedural guidance can improve agent performance, but a skill is not beneficial merely because it exists, is official, is long, is popular, or validates structurally. SkillsBench reported a 16.2-point average gain for curated skills while 16 of 84 tasks regressed, its software-engineering subset improved only 4.5 points, and its self-generated-skill condition averaged below baseline. SWE-Skills-Bench reported only a 1.2-point mean improvement, with 39 of 49 skills showing no pass-rate gain and three regressing. These are **Strong, distribution-bounded findings**, not universal effect sizes ([SkillsBench](https://arxiv.org/abs/2602.12670), submitted 2026-02-13; [SWE-Skills-Bench](https://arxiv.org/abs/2603.15401), submitted 2026-03-16; consolidated in [Session 5](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/05_Demonstrated_Skill_Success_Evidence.md)).

The project's controlling need is not a large skill collection. It is an authority-preserving, evidence-bearing development system in which skills occupy only the conditional workflow layer. The User / Creative Director, player-as-witness premise, biblical source commitments, fixed and protected sacred events, historical uncertainty, era-appropriate knowledge, player-facing codex separation, schema-first production, rights/provenance, and continuity cannot depend on whether a skill happens to load. Permanent governance, approved data records, schemas, validators, runtime controls, tests, scoped permissions, and accountable human gates each enforce different parts of the system ([Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md); [Session 13](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/13_Project_Constraint_Enforcement_Architecture.md)).

At the inspected head, the repository remains a documentation-and-research foundation. No engine, runtime language, executable schema, game code, asset pipeline, build, test harness, save format, CI system, deployment target, accessibility baseline, or final skill catalog is approved. Unity, Godot, Unreal, browser, Blender, and custom-engine material in the research is conditional evidence only. No skill may convert those unknowns into a project decision ([Session 1](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md)).

The most supportable skill architecture is therefore:

1. preserve always-on project identity and prohibitions in project governance;
2. create a skill only for one coherent, recurring, conditionally useful procedure;
3. keep `SKILL.md` concise and route conditional detail by progressive disclosure;
4. treat every external package as untrusted until its entire tree, executables, dependencies, rights, permissions, and pinned revision are inspected;
5. preflight current authority, repository state, tools, permissions, and user-owned decisions before effects;
6. compose explicit serial phases under one integrator, not silently blended personas;
7. verify real outputs with independent structural, state, runtime, visual, persistence, and human oracles as applicable; and
8. compare each exact candidate version against the current Master-Protocol workflow, preserving negative results and critical vetoes.

Session 17 implemented the only skill created in this program: `.agents/skills/the-bible-video-game-skill-builder/`. It is explicit-only, contains no scripts or dependencies, passed the official structural validator, and ultimately passed four one-run clean-context smoke cases after retaining two positive-build failures and one safely blocked harness attempt. This supports **structurally valid and forward-smoke-ready**, not effective, adopted, secure in every environment, or portable across every Codex surface ([implementation record](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/17_Skill_Builder_Implementation_Record.md)).

The largest risks are false invocation, context overload, stale stack advice, authority inversion, unsafe scripts and dependencies, unlicensed reuse, fabricated validation, test or baseline manipulation, broad Git effects, role theater, silent multi-skill conflict, and skills that make the project more generic precisely where it must remain explicit about Scripture, sacred events, chronology, historical uncertainty, and knowledge boundaries. Any critical violation vetoes adoption; average gains cannot compensate for it.

## 2. Project-context interpretation

### Repository authority and status

The repository's project-domain chain is: User / Creative Director; core player-as-witness vision; biblical source-text commitments; established canon/scope decisions; Master Assistant Protocol; current file manifest/repository structure; approved schemas; approved design/technical specifications; assigned roles; and current task instructions. Host system/developer safety, sandbox, approvals, and capability controls remain above all repository artifacts. These two ladders must not be conflated ([Master Protocol section 4](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L78-L107); [Session 14](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/14_Skill_Composition_Conflict_and_Governance_Model.md)).

The Master Protocol is the highest current repository policy document. The Activation Prompts are subordinate manual launchers for the existing roles. The Continuity Handoff Prompt is a state-transfer template, not authority or memory truth. Its historical local path, broad proposed tree, and Caelmor framing are non-authoritative where they disagree with the live checkout. The repository still has no current README or file manifest; those empty authority slots are not permission to invent them ([Session 1 conflict report](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md#L249-L265)).

### Project identity as an architectural constraint

The player is a witness, not the savior, author, or rewriter of Scripture. Player agency should be meaningful in ordinary life - household, work, trade, danger, reputation, mercy, fear, courage, repentance, and faith - while fixed biblical outcomes and sacred figures remain protected. This is neither a style persona nor an optional skill trigger. It is a governing invariant that must survive non-invocation, tool failure, save/load, migration, alternate input paths, accessibility features, and sequence breaks.

The Scripture-backed codex also creates a permanent two-audience boundary. In-world people may know only what is plausible for their era, community, and circumstances. The player-facing codex may explain later canonical connections, manuscript traditions, original-language issues, and modern historical context, but it must not leak that later knowledge into dialogue or world state. Source records must separate Scripture, interpretation, tradition, historical reconstruction, speculation, paraphrase, and non-canonical material. The existing Genesis 5-11 comparison demonstrates the correct *research shape* - parallel witness tracks rather than a fabricated single chronology - while explicitly warning that corrupted OCR requires independent textual verification before authoritative use ([chronology comparison](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/Research/genesis_5_11_mt_lxx_chronology_comparison.md)).

Regional dossiers model confidence labels, competing views, source-to-verify lists, protected-event zones, and playable translation. They are research/proposals, not approved production specifications. The developed Galilee/Capernaum vertical-slice material remains a proposed direction rather than an engine, map, schema, or milestone commitment ([Galilee proposal](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/Research/Regions/galilee_capernaum_geography.md#L957-L1221)).

**Recommendation:** every future skill decision should begin from the live repository, explicitly label `implemented`, `approved`, `proposed`, `disputed`, `unknown`, and `obsolete/non-authoritative`, and refuse to promote one state into another by tone or file placement.

## 3. Terminology and conceptual model

The complete canonical taxonomy is in [Session 2](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md). The distinctions that control architecture are:

| Concept | Meaning | Correct project use |
|---|---|---|
| Skill | Reusable, conditionally selected package centered on `SKILL.md`, with optional references/assets/scripts | One bounded recurring procedure; never sole authority or permission |
| Role | Professional responsibility, decision ownership, prohibitions, sources, outputs, handoffs, and approvals | Keep canonical ownership in governance; encode only a stable role workflow when justified |
| Persona | Tone or simulated identity | Presentation only; never evidence or decision authority |
| Agent / subagent | Runtime model process / delegated bounded instance | Use separation only for real context, capability, ownership, or independent-review benefit |
| System/developer/user instruction | Host/application/user direction at different authority levels | Obey actual layer; do not call repository prose a system instruction |
| Repository instruction / `AGENTS.md` | Persistent, path-scoped project guidance recognized by the client | Candidate home for approved always-on operating rules, distinct from skills; none is authorized here by this report |
| Prompt / command | Task input / discrete client, shell, or tool invocation | Use for one-off work; do not persist without recurring value |
| Workflow | Ordered inputs, decisions, actions, checks, outputs, and stops | May be expressed by skill, script, checklist, CI, or orchestration |
| Policy / guardrail | Normative rule / preventive or detective control | Put universal policy in governance and enforcement in appropriate technical/human layers |
| Domain reference / context file | Versioned knowledge or task context | Authority depends on provenance, source quality, status, and freshness, not inclusion in a skill |
| Tool / MCP server / script / hook | Callable capability / capability server / executable / event-triggered automation | Separately inspect permissions, effects, dependencies, and rights; skills do not grant them |
| Memory / handoff | Persisted context / structured state transfer | Fallible state, not a canonical decision log |
| Evaluation / benchmark | Defined measurement procedure / standardized comparative suite | Evidence only when run, scored, preserved, and reviewed; not an approval mechanism |
| Agent configuration | Machine-readable model/tool/MCP/sandbox/instruction definition | Use only for a demonstrated capability or isolation delta |

The seven proposed skill categories - role, workflow, policy, domain-reference, tool-operation, orchestrator/router, and artifact-production - are useful classification labels, not seven required skill families. Policies, schemas, validators, tests, runtime controls, tools, human roles, outputs, and skills must remain different artifact classes. A workflow skill is the strongest default candidate; a policy skill may audit or apply a policy but cannot be its only carrier.

## 4. Current Codex capability map

### Documented behavior as of 2026-07-22

- A skill is a directory with required `SKILL.md`; required frontmatter fields are `name` and `description`. Optional conventional resources include `references/`, `scripts/`, `assets/`, and `agents/openai.yaml` ([OpenAI, Build skills](https://learn.chatgpt.com/docs/build-skills), accessed 2026-07-22; [Agent Skills specification](https://agentskills.io/specification), accessed 2026-07-22).
- The repository-wide root resolved for this project is `.agents/skills`; user, admin, and system scopes are separate. The implemented builder is at `.agents/skills/the-bible-video-game-skill-builder/` ([Session 3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md#L27-L66)).
- Codex first sees discovery metadata, loads the full body after selection, then reads supporting resources on demand. This progressive disclosure reduces initial context but does not make loaded resources free.
- Skills can be explicitly invoked and, by default, model-selected from description matching. `policy.allow_implicit_invocation: false` in `agents/openai.yaml` preserves explicit invocation while blocking implicit selection.
- `agents/openai.yaml` may contain interface metadata, implicit-invocation policy, and tool dependency declarations. A dependency declaration does not establish installation, authentication, authorization, availability, or safety.
- Skills are documented across ChatGPT desktop Codex, Codex CLI, and the IDE extension. Plugin-based Work-mode distribution, hosted/cloud execution, and local repository discovery are different surfaces and require their own tests.
- `AGENTS.md` has a separate persistent path-scoped discovery/precedence model. That model must not be projected onto skills.
- A skill does not grant shell, filesystem, network, credential, connector, Git, or publication authority. Sandbox capability and approval policy remain separate controls ([OpenAI, Agent approvals and security](https://learn.chatgpt.com/docs/agent-approvals-security), accessed 2026-07-22).

### Unverified or undocumented behavior

No reviewed official source establishes deterministic merge/precedence among conflicting selected skills, ordering for several named skills, a native companion/conflict/version resolver, privileged skill-to-skill invocation, guaranteed activation lifetime through turns or compaction, universal fallback for missing tools, or full hosted-surface parity. Same-name packages are not a versioning or override system.

**Recommendation:** express composition as an explicit serial workflow, preflight every dependency, honor explicit-only boundaries, record which resources actually loaded, stop on unresolved conflict, and reinvoke after material context changes rather than claiming persistent mode semantics.

## 5. Anatomy of an effective skill

An effective skill is a small, discoverable, testable workflow package that transfers non-obvious procedure and improves a defined task class without violating authority, permissions, or scope. It is not a saved megaprompt. The evidence-backed structure is:

1. **Discovery:** a concise name and trigger-oriented description with positive intent and nearest exclusions.
2. **Purpose and boundaries:** one recurring job, scope, non-goals, preconditions, and live authority route.
3. **Inputs:** required/optional/discoverable/user-owned inputs, freshness, precedence, and discover-before-ask rules.
4. **Procedure:** preflight, discovery, plan/gate, bounded execution, validation/repair, delivery/trace.
5. **Ownership and effects:** O/R/P/A where role-like; tool, permission, write, network, Git, and human approval boundaries.
6. **Outputs:** exact artifacts/paths, evidence, status vocabulary, completion, failure, blocked, refusal, rollback, and stopping conditions.
7. **Progressive resources:** directly linked conditional references; scripts only for justified deterministic work after full inspection.
8. **Evaluation and maintenance:** trigger, near-miss, conflict, missing-capability, unsafe-input, output, regression, version, provenance, and invalidation cases.

The primary `SKILL.md` should contain what nearly every valid run needs. Selection language belongs in frontmatter; conditional variants and detailed checklists belong one direct reference away; deterministic repeated operations may belong in reviewed scripts; evaluation prompts and expected answers stay outside production context. The Agent Skills 500-line/5,000-token guidance is a ceiling, not a target ([Agent Skills specification](https://agentskills.io/specification); [Session 4](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md)).

Examples help when they clarify syntax, one branching decision, or a stable input/output form. They harm when they are more concrete than the invariant, select an unapproved engine/schema, anchor later outputs, or leak expected answers. Use varied held-out fixtures and counterexamples. Structural validation is necessary but cannot establish correct triggering, task value, security, project fit, or truthful completion.

## 6. Evidence review with strength ratings

### Evidence ledger

| Claim or practice | Evidence source | Evidence type | Strength | Transferability to this project | Risks or caveats |
|---|---|---|---|---|---|
| Human-curated relevant skills can improve aggregate task success | [SkillsBench](https://arxiv.org/abs/2602.12670) | Controlled repeated multi-configuration benchmark | Strong | High for requiring comparative evaluation; moderate for effect size | Preprint; terminal tasks; 16/84 regressions; domain-specific effects |
| Curated skills improved GPT-5.2-Codex by 14.1 points in the tested SkillsBench condition | [SkillsBench](https://arxiv.org/abs/2602.12670) | Within-study model comparison | Strong | Moderate | Current model/surface transfer unverified; harness details incomplete |
| Specialized SWE skills sometimes help greatly, while most tested public skills did not | [SWE-Skills-Bench](https://arxiv.org/abs/2603.15401) | Paired executable-test benchmark | Strong | High | Preliminary preprint; one reported model/harness family |
| A constrained instruction/tool/feedback interface can improve issue resolution | [SWE-agent paper](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf) | Peer-reviewed combined ACI ablation | Strong | High for observable loops | Does not isolate skill prose from tools, feedback, and context management |
| Repeated trials and deterministic verifiers make claims more auditable | [SkillsBench repository `5720102e...`](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7) | Inspectable fixtures/verifiers | Moderate | High | Deterministic tests prove only covered assertions |
| Baseline contamination can invalidate evaluation meaning | [SkillsBench pollution audit](https://github.com/benchflow-ai/skillsbench/blob/5720102e3d6b0d3471b9715995ff96144d9eefb7/docs/skills-research/skill-pollution-trial-summary.md) | Primary incident record | Moderate | High | Published aggregate was not independently reconstructed here |
| Self-generated skills can underperform no-skill baselines | [SkillsBench](https://arxiv.org/abs/2602.12670) | Controlled generated-skill condition | Strong | High | Does not prove every generated draft is harmful; it proves review/evaluation is necessary |
| Larger or more numerous skill packages are not reliably better | [SkillsBench](https://arxiv.org/abs/2602.12670) | Observational subgroup analysis | Moderate | High | Not a randomized size/count ablation; no universal cutoff follows |
| Version mismatch, task conflict, and excess context can cause regressions | [SWE-Skills-Bench](https://arxiv.org/abs/2603.15401) | Reported paired-study failure analysis | Strong | High | Mechanisms may interact; current project stack is unknown |
| Structural validity proves package shape, not semantic value | [Agent Skills specification](https://agentskills.io/specification) and [OpenAI skill-creator audit](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/17_Skill_Builder_Implementation_Record.md) | Specification plus observed validator use | Moderate | Critical | Behavioral and effectiveness tests remain separate |
| Skills do not grant runtime permissions | [OpenAI security documentation](https://learn.chatgpt.com/docs/agent-approvals-security) | Current official product documentation | Strong | Critical | Exact effective policy varies by configured surface |
| Prompt injection and enabled internet create exfiltration/dependency/license risks | [OpenAI internet-access guidance](https://learn.chatgpt.com/docs/cloud/internet-access) | Official threat guidance | Moderate | High | Establishes mechanism, not package prevalence |
| Narrow edit-run-observe-correct loops are implemented in audited game packages | [Session 11 package audit](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/11_Video_Game_Development_Skill_Landscape.md) | Actual pinned file/script inspection | Moderate | High as engine-neutral principle | No controlled production-outcome evidence for audited packages |
| Refactoring agents still struggle on compound, repository-scale changes | [RefactorBench](https://openreview.net/pdf?id=ZjsHNRxH2Q), [SWE-Refactor](https://arxiv.org/abs/2602.03712), [CodeTaste](https://arxiv.org/abs/2603.04177) | Benchmarks/preprints | Moderate to Strong within tested distributions | High for requiring bounded proposal/preservation/verification | No direct game serialization or sacred-domain coverage |
| Role-based multi-agent systems are feasible but roles alone do not isolate benefit | [ChatDev](https://arxiv.org/abs/2307.07924), [MetaGPT](https://arxiv.org/abs/2308.00352), [MAST](https://arxiv.org/abs/2503.13657) | Framework studies and failure taxonomy | Moderate; Strong for observed failure taxonomy | High | Interventions combine roles, tools, process, extra context, and feedback |

### Reconciled interpretation

SkillsBench's large aggregate gain and SWE-Skills-Bench's small gain are not a factual contradiction to resolve by averaging. They sample different domains, packages, models, task selection, environments, and verifiers. Together they show that effect size is distribution- and match-dependent. The causal unit is the full intervention - exact skill package, supporting resources, routing, model/harness, task environment, tools, and verifier - not isolated prose.

No reviewed study directly measures this project's witness premise, sacred-event protection, canon distinctions, historical uncertainty, in-world/codex separation, or spiritual/emotional impact. Public evidence justifies disciplined experiments, not delegated stewardship.

## 7. Failure and risk review

The principal failure families and required defenses are:

| Failure family | Typical failure | Required prevention/detection |
|---|---|---|
| Invocation/context | False trigger, missed trigger, long/contradictory context, example anchoring | Precise description, explicit-only for high impact, positive/near-miss/adversarial cases, progressive disclosure |
| Engineering quality | Overengineering, unnecessary files/dependencies, untested code, weakened errors, line-count optimization | Acceptance-to-diff map, additions ledger, green baseline, unchanged tests, runtime evidence, human review |
| Evaluation integrity | Polluted baseline, shallow verifier, changed goldens/tests, selected showcases | Clean contexts, frozen rubrics, known-good/bad calibration, retained failures, scenario-level vetoes |
| Capability truthfulness | Assumed engine/tool, hidden failure, fabricated build/play result | Read-only preflight, required/optional classification, exact `pass/fail/blocked/not_run/unavailable/not_applicable` states |
| Security/supply chain | Instruction injection, credential read, upload, opaque script, dependency substitution | Full-tree and transitive inspection, least privilege, inert fixture review, pinning, quarantine, no execution before audit |
| Rights/provenance | Public visibility mistaken for license, missing notices, unclear dataset/asset/translation rights | File-level license and origin record; unknown means no reuse |
| Git/repository | Broad staging, stale-head overwrite, destructive reset, force push, path drift | Exact root/head/status, allowlisted writes, staged diff, current remote check, fast-forward only, recovery plan |
| Staleness | Changed engine/API/model/dependency/license/authority | Compatibility record, immutable identity, invalidation triggers, quarantine and proportional reevaluation |
| Authority/persona | Expert tone or lower skill overrides live policy; role blending | Authority preflight, O/R/P/A, one integrator, one writer, conflict trace, human disposition |
| Project-integrity | Sacred/source/schema/chronology controls treated as optional detail | Permanent governance plus schemas/runtime/tests/human gates; critical vetoes |

Third-party intake must enumerate the complete package, read every instruction and transitive reference, inspect every executable and dependency, map effective permissions/data flows, verify exact licenses/provenance and target versions, test in a clean least-privilege environment, and select only `Adopt as-is`, `Adapt`, `Extract principles only`, `Monitor`, or `Reject`. Immediate rejection conditions include concealed execution, authority inversion, secret collection/exfiltration, destructive defaults, unresolved rights, false validation, unbounded access, or weakened sacred/source/schema/error/test/Git safeguards ([Session 6 intake checklist](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md#L243-L307)).

## 8. Role-based skill analysis

A professional title is not an implementation primitive. A valid role owns bounded decisions, may recommend other decisions, is prohibited from reserved decisions, names approvers, sources, capabilities, outputs, checks, escalation, and handoff. This O/R/P/A model prevents a role from becoming a costume.

Use this decision order:

1. Always-binding identity or policy -> Master Protocol / approved repository governance.
2. Mechanically enforceable rule -> schema, validator, test, runtime control, CI, or permission.
3. Recurring bounded procedure -> skill candidate.
4. Materially different model/tool/MCP/sandbox or intentionally isolated review -> agent configuration candidate.
5. Bounded delegated instance -> subagent with work order and return packet.
6. One-time lens -> prompt.
7. Simple local behavior -> ordinary task instruction.

The current nine manual assistant modes remain valid governance but are not nine proven skills or agents. The extra technical roles named in the original assignment are candidate responsibilities only. No engine, release, accessibility, performance, or security infrastructure exists to justify corresponding implementation agents today. The recommended default is manager-owned integration: one primary assistant holds authority and outcome, delegates bounded work, then checks sources, status, dependencies, uncertainty, protected constraints, scope, and evidence before acceptance ([Session 7](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/07_Role_Based_Skill_Architecture.md)).

Create a role skill only after several real tasks show one coherent recurring job, stable inputs/procedure/output, distinct value beyond the Protocol, evaluable positive/negative cases, acceptable context/maintenance cost, and visible recoverable failure. Create a separate agent only if isolation, independent review, or different capabilities add measurable value over the simpler main-agent/skill baseline.

## 9. Communication-modifier analysis

The principle is sound but unproven: **compress expression, not reasoning**. A manually invoked modifier can request fewer task restatements, less narration of routine reads/edits, shorter progress at meaningful phase changes, less explanation of obvious code, and a compact final report. It cannot mechanically prove unchanged reasoning, tool choice, artifacts, or validation because a skill is instruction context, not an isolated output renderer ([Session 8](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/08_Communication_Modifier_Skill_Analysis.md)).

Never suppress: authority conflict; missing user decision; security/privacy/credential/license/provenance risk; destructive or external action; unavailable tool; failed or unrun check; uncertainty/contradictory evidence; incomplete work; changed tests/baselines; weakened error handling; concurrent changes; Scripture/canon concerns; sacred-event risk; historical uncertainty; chronology/knowledge leakage; schema/migration/save risk; scope expansion; or required approvals.

**Recommendation:** pilot a short session instruction and task output contract against no-modifier and built-in style/verbosity controls. Promote only to an explicit-only experimental skill if paired clean-context tests reduce task-facing messages/tokens or review time while artifacts, evidence, warnings, tests, and project constraints remain equivalent. Do not put one user's general brevity preference in repository policy. Reject `quiet-operator` as a name because it encourages unsafe silence; treat `lean-comms` only as an experimental working label.

## 10. Scope-control analysis

Scope control should implement **flexible minimalism**:

> The smallest change that completely satisfies the currently authorized outcome, preserves all applicable invariants, uses justified foundations, remains reviewable and reversible, and passes the strongest available verification.

This is not fewest lines, files, dependencies, or abstractions. Classify work as `required now`, `enabling now`, `approved foundation`, `deferred option`, or `conflicting expansion`. For each addition ask which current requirement/invariant fails without it; why it must exist now; whether an existing owner can handle it; what concepts/states it adds; what complexity it removes or contains now; what evidence makes the need non-speculative; and how it will be verified and reversed.

A new abstraction is justified by a real variation, ownership/information-hiding boundary, test seam, external/serialization/security/engine boundary, protected-domain invariant, or second current consumer when it reduces net complexity now. A new dependency needs current insufficiency, supported compatibility, license/security/maintenance review, and lower total risk than bespoke work. A new file needs a coherent owner; avoiding files must not create a god module. Foundational work needs a known one-way door or disproportionate transition cost, not “we may need it later.”

Sacred-event semantics, approved schema work, provenance/confidence, stable identifiers, era/codex separation, required tests, error behavior, accessibility requirements, and security controls are part of the minimum when applicable. They are not polish. If literal minimalism violates them, implement the smallest compliant result or stop. The long-term vision is preserved by bounded approved foundations and explicit deferred ideas, not speculative MMO, live-service, procedural, cross-platform, or networking scaffolding ([Session 9](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/09_Scope_Guard_Skill_Analysis.md)).

## 11. Code-simplification analysis

Post-implementation simplification is a distinct phase. Its goal is the smallest clear maintainable implementation that preserves observable behavior, integrations, safeguards, and conventions - not code golf or raw line reduction.

Entry requires an implemented accepted outcome, exact green baseline, observable behavior contract, selected stack facts, bounded target, dependency/reference inventory, read-only tests by default, rollback point, known repository state, and every required verifier. At the current repository state there is no eligible production implementation target.

The workflow should be: propose a named smell -> inventory hidden consumers -> build a preservation ledger -> approve the bounded transformation -> change one coherent concern -> run an ordered verification ladder -> accept or roll back. Hidden consumers include reflection/registration, editor callbacks, serialized fields/types, scenes/prefabs/resources/Blueprints, stable IDs, old saves/migrations, public APIs, localization, accessibility, security logs, and project-specific source/sacred/knowledge records.

It must not change observable behavior, weaken errors/tests, alter acceptance to pass, remove source/confidence fields, collapse in-world and codex data, genericize sacred-event rules, break serialized/editor/save references, or perform speculative optimization. Performance changes require comparable captures. “No safe simplification identified” is a successful result when the preservation case cannot be built ([Session 10](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/10_Post_Implementation_Simplification_Skill_Analysis.md)).

## 12. Video-game skill landscape

### Existing-skill audit

Every row below is based on actual files/supporting files inspected in Sessions 5, 10, or 11. No package is adopted as-is.

| Repository | Skill | Platform | Intended purpose | Evidence of real use | Quality assessment | Safety concerns | License | Reuse decision |
|---|---|---|---|---|---|---|---|---|
| [`benchflow-ai/skillsbench@5720102e`](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7) | Spring Boot/Jakarta migration subskills | Cross-agent benchmark | Guide a pinned Java/Spring migration | Controlled benchmark task with executable verifier; per-subskill effect not isolated | Focused and concrete but stack/version specific | Broad mechanical edits; stale dependency guidance; unrelated stack | Apache-2.0 root; file provenance still needed | Extract principles only |
| [`GeniusHTX/SWE-Skills-Bench@95b3ce51`](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1) | `python-resilience` | Claude Code benchmark package | Retry/circuit-breaker/error patterns | Paired harness exists; positive package-specific effect not established | Actionable but broad; verifier partly structural | Premature dependencies/abstractions; Python stack absent | MIT root; embedded provenance still requires review | Reject |
| [`SWE-agent@3ea751c0`](https://github.com/SWE-agent/SWE-agent/tree/3ea751c087f32b16e039a2233dd6eefecef325d5) | ACI/default workflow (comparable artifact) | SWE-agent | Repository issue resolution with constrained tools/feedback | Peer-reviewed combined ablation, +10.7 points in tested subset | Strong observable feedback design; historical config | Powerful shell/edit operations; no project theology/history controls | MIT | Extract principles only |
| [`openai/skills@49f948fa`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator) | `skill-creator` | Codex | Initialize, author, generate metadata, structurally validate | Official workflow and scripts; no controlled downstream effect study | Clear workflow and useful automation; structural checks only | Generated executables/references still need review; catalog deprecated | Package-specific Apache-2.0 in installed/current package | Adapt |
| [`anthropics/skills@fa0fa64b`](https://github.com/anthropics/skills/tree/fa0fa64bdc967915dc8399e803be67759e1e62b8/skills/skill-creator) | `skill-creator` | Claude | Draft, compare baseline, grade, tune triggers | Public executable evaluation workflow; creator benefit not isolated | Strong evaluation concepts; long/platform-specific | Model subprocesses, external cost/data, grader reliability | Exact package terms must be reverified before copying | Extract principles only |
| [`anthropics/claude-plugins-official@b36f687`](https://github.com/anthropics/claude-plugins-official/tree/b36f687171aecc8577fbdc7c70887dcd0b9c7f90/plugins/code-simplifier) | `code-simplifier` | Claude Code agent/plugin | Simplify recently changed code while preserving function | Actual agent/manifest; no controlled game-code evidence | Good bounded-scope/clarity principles; JS/TS/React-specific and under-specified verification | Autonomous cleanup; no save/editor/sacred/provenance/rollback gates | Exact file-level reuse rights unverified | Extract principles only |
| [`openai/skills@0ed635a`](https://github.com/openai/skills/tree/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game) | `develop-web-game` | Codex, browser, Playwright | Incremental web-game implementation/play loop | Actual script, actions, metadata; no independent production-effect study; later archived | Best audited observable loop; partial deterministic seam | Browser/network/output writes; unpinned install advice | Apache-2.0 package license | Extract principles only |
| [`fernforestgames/agent-skill-godot@e584a97`](https://github.com/fernforestgames/agent-skill-godot/tree/e584a973fcf0590a4cbc6697fa5daa3d11585dbe) | `godot` | Claude-oriented Agent Skill, Godot 4+ | GDScript/resource docs-edit-import-check-test loop | Actual skill/script and active maintenance; no controlled outcome evidence | Concise observable loop; over-broad trigger and hard-coded version/tools | Executes project scripts; Bash portability; external MCPs unaudited | MIT | Extract principles only |
| [`Randroids-Dojo/skills@aba2aba`](https://github.com/Randroids-Dojo/skills/tree/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/godot) | `godot` | Claude/Agent Skill, Godot/GdUnit4/PlayGodot | Develop, test, automate, build, deploy | Actual validators/test/export scripts; no independent controlled benefit | Broad and concrete; dependency/portability defects | Installs/custom fork, project/output writes, hosting/publication | MIT collection; external components separate | Extract principles only |
| [`Randroids-Dojo/skills@aba2aba`](https://github.com/Randroids-Dojo/skills/tree/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/unreal) | `unreal` | Claude/Agent Skill, Unreal Remote Control | Target PlayUnreal E2E workflow | Actual launcher; package explicitly WIP/scaffolded | Candid and useful process shape; target API immature | Executes supplied binary; Remote Control exposure; process kill | MIT | Monitor |
| [`akiojin/skills@4f72afe`](https://github.com/akiojin/skills/tree/4f72afeb9efb9520a7a02afb9e23fba2dbe0ffa1) | Advertised `unity-development` | Claude Code | Claimed Unity C#/MCP/testing workflow | README listing; current package/marketplace entry absent | Cannot inspect or assess the named artifact | Unknown dependencies, permissions, and behavior | Repository MIT, but no artifact to reuse | Reject |
| [`CoderGamester/mcp-unity@c35f184`](https://github.com/CoderGamester/mcp-unity/tree/c35f184d7656bd14e7748f11a05060feeb286d6e) | `mcp-unity` | MCP, Unity Editor, Node | Query/mutate scenes/assets/packages/tests/play mode | Substantial implementation/tests/current maintenance; no outcome comparison | Capable typed bridge; contradictory Unity version statements | Delete/mutate/install/config/menu reach; dependency ranges | Manifests say MIT; root license absent at pin | Monitor |
| [`Coding-Solo/godot-mcp@1209744`](https://github.com/Coding-Solo/godot-mcp/tree/1209744fad78f3998f98c7394fd0f6ef50da5281) | `godot-mcp` | MCP, Godot, Node/TypeScript/GDScript | Launch/debug/manipulate Godot projects | Real implementation and 2026 security fix; no test command/outcome study | Useful bridge and responsive fix; early/incomplete validation | Process/scene writes; prior arbitrary class-instantiation path; fallback paths | MIT | Monitor |
| [`ahujasid/blender-mcp@da4e16d`](https://github.com/ahujasid/blender-mcp/tree/da4e16d2069ce5154eaa2535bf995e843caf5c73) | `blender-mcp` | MCP, Blender/Python/external APIs | Inspect/mutate scenes and obtain/generate assets | Real server/add-on/tests/maintenance; benefit unverified | Broad useful DCC bridge with large trust surface | Code execution, asset writes, downloads/uploads, keys, telemetry | MIT | Extract principles only |

The transferable pattern is a narrow edit -> real launch/import/build -> controlled input -> independent state/visual/log inspection -> correction -> evidence/cleanup loop. Other reusable principles are stable semantic selectors, designed reset/clock/seed seams, read-only versus mutating capability separation, and a side-effect manifest. Reject engine selection by skill activation, latest/unpinned installs, README-only maturity, compile-only completion, uninspected screenshots, diverging test-only state, exposed remote control, silent telemetry, destructive editor actions without exact targeting/recovery, and external assets without rights and cultural review.

No audited package provides mature project-ready enforcement for biblical provenance, sacred-event mechanics, era knowledge/codex separation, disputed historical geography, lineage continuity, schema migrations, accessibility, localization, audio, or release certification. That is an evidence gap, not proof that no such package exists.

## 13. Game-validation architecture

A game can compile and remain unplayable, visually wrong, inaccessible, historically incoherent, or irreverent. Validation therefore needs independent layers:

1. static/path/schema/reference/provenance checks;
2. pure unit tests;
3. component/integration tests;
4. import/build/export checks;
5. reset/clock/seed/state-projection seams;
6. runtime logs and authoritative state;
7. controlled keyboard/controller actions;
8. visual, video, audio, resolution, locale, and accessibility evidence;
9. semantic save/load/world-state round trips and migrations;
10. target-specific performance/memory captures against approved budgets;
11. protected sacred/source/chronology/continuity scenarios; and
12. named human play, discipline, stewardship, accessibility, and release gates.

The key rule is to validate a player-observable contract, not a successful command. Prefer two independent oracles for consequential behavior: state plus rendering, semantic save diff plus post-load play, or invariant test plus human review. A test projection must derive from the same authoritative state players experience. Determinism is a designed seam, not a blanket description of an engine.

The recommended narrow loop is: frame one change and invariants; preflight stack/tools/permissions; freeze acceptance; inspect live state; make one coherent change; run cheapest gates; build/launch; execute controlled inputs; compare state/visual/log/save/performance evidence; apply project-specific gates; preserve the first failure; correct and rerun downstream layers; conduct human review; seal a run manifest; claim only observed layers. Tool unavailability yields `not runtime-validated`, never `pass` ([Session 12](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/12_Game_Validation_and_Play_Verification_Architecture.md)).

At the current head, only document/path/link/diff checks are executable over the project. Engine, gameplay, visual, save, performance, and platform validation remain unavailable. Official Unity, Godot, Unreal, and Playwright documentation demonstrates possible primitives, not a stack selection ([Unity Test Framework](https://docs.unity3d.com/Packages/com.unity.test-framework@1.4/manual/index.html), [Godot command line](https://docs.godotengine.org/en/stable/tutorials/editor/command_line_tutorial.html), [Unreal Automation](https://dev.epicgames.com/documentation/en-us/unreal-engine/automation-test-framework-in-unreal-engine), [Playwright visual comparisons](https://playwright.dev/docs/test-snapshots); accessed 2026-07-22).

## 14. Project-specific enforcement architecture

Use defense in depth and distinguish declaration, detection, prevention, and approval:

| Project constraint | Canonical/permanent owner | Data/schema/validator | Runtime/test control | Human gate |
|---|---|---|---|---|
| Scripture citations and source categories | Biblical commitments, Master Protocol | Claim-level source ID, canon category, edition/witness, locator, confidence, quote/paraphrase/rights state | Resolvable-source and category checks | Scripture/theology and rights review |
| Interpretation/reconstruction/speculation | Master Protocol and relevant domain owner | Explicit status, rationale, alternatives, dissent | Label/presentation and promotion checks | Theology/history judgment |
| Original languages and translations | Approved textual-witness/rights policy | Verified edition/form/analysis and permission registry | Approved-corpus comparison; quarantine OCR | Qualified language and rights review |
| Fixed sacred outcomes | Witness vision and Creative Director | Protected event/outcome IDs, allowed/denied verbs/effects | Central capability authorization, adversarial equivalent-effect matrix, save/migration invariants | Theology/stewardship and gameplay review |
| Meaningful bounded agency | Creative/gameplay authority | Event interaction contract and ordinary-person consequences | At least one allowed path plus fixed-anchor tests | Playtest and stewardship review |
| Chronology and knowledge | Approved chronology/source authority | Parallel chronology tracks; assertion available-from/audience/region fields | Interval/reference checks; later-source leakage tests | Scripture/chronology review |
| In-world versus player codex | Master Protocol and codex owner | Separate records/views and typed dependency direction | UI/data-flow tests | Theology/codex review |
| Historical uncertainty and visual authenticity | History/visual owners | Competing views, confidence, composite flag, era/region/material provenance | Metadata/compatibility/license checks | History/cultural/visual/Creative Director review |
| Schema-first content | Creative Director and schema owner | Versioned approved schemas, stable IDs, typed references, migration graph | CI validation and known-invalid fixtures | Semantic schema approval |
| Continuity and Git/file integrity | Creative Director/repository owner | Decision IDs, supersession, manifest/status, task write allowlist | Dirty/head/diff/path checks, protected validators/tests | Integrator/reviewer acceptance |

Fail closed on prohibited effects and fail explicit on missing knowledge. A missing source, schema, rights record, event policy, or required tool must block promotion or the affected effect; it must not be filled by plausible invention. Machine checks can require competing views and labels but cannot choose the correct disputed location, approve a miracle depiction, judge emotional weight, or establish theological consensus.

The minimum staged stack is: governance/task briefs/claim ledgers and human review now; approved schemas, stable IDs, validators, and promotion states after data contracts; centralized sacred-effect and knowledge-delivery controls plus layered runtime validation after stack selection; and protected CI/rulesets/artifact provenance after repository governance is approved. This report authorizes none of those implementations.

## 15. Skill composition model

Reliable composition is an explicit, serial, authority-first graph:

1. authority and current repository preflight;
2. applicable policy invariants;
3. one producer role with O/R/P/A;
4. scope/research/design/implementation phases as needed;
5. tool operation with versions/permissions/side effects;
6. artifact contract;
7. verification and independent audit;
8. optional communication shaping last.

One integrator owns routing and final acceptance. One writer owns an artifact in each phase. Components declare authority, artifact, workflow, tool, human, reference, validator, and permission dependencies as required/optional, with version, availability check, fallback, failure behavior, and owner. User-invoked-only workflows remain unreachable to automatic routing. The graph must be finite and acyclic; skills cannot claim privileged activation of other skills.

Conflict handling is explicit: identify the clauses, assign authority levels, apply the higher source where clear, preserve the losing instruction in the trace, and stop for an accountable ruling when authority/status is equal or disputed. Never average safety, sacred, source, schema, rights, or compatibility rules. Communication modifiers shape prose only after artifacts/evidence. Scope guards precede implementation. Simplification follows a green baseline and preservation ledger. QA cannot change the rubric to accept the producer's output ([Session 14](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/14_Skill_Composition_Conflict_and_Governance_Model.md)).

Every consequential run should record base/head, authority revisions, selected components and revisions, loaded references, tools/permissions/network/data exposure, files read/written, conflicts/dispositions, checks/results, human gates, residual risks, rollback, and final artifact identity. This is operational provenance, not private chain-of-thought.

## 16. Evaluation framework

### Baselines and experimental design

- **B0 task-only diagnostic:** platform safety plus synthetic task, no Master Protocol or project skill; never publish its output.
- **B1 current workflow:** Master Protocol plus exact repository context, no candidate; primary adoption baseline.
- **B2 candidate:** B1 plus exact candidate package.
- **B3 composition:** B1 plus exact candidate and declared companions in explicit order.
- **BX ablation:** controlled component removed/substituted to diagnose mechanism.

Freeze candidate tree hash, prompt/fixture/rubric, model/surface/harness, tools/versions, permissions, base SHA, context, limits, graders, reviewers, and decision criteria before runs. Use fresh processes/contexts and clean worktrees; physically remove candidate material from baseline discovery roots and caches. Report assigned-treatment effects including failure to invoke, not only successful loaded-skill runs. Preserve negative trials.

Recommended stages are one structural/security intake per exact hash; at least two known-good and two known-bad calibration artifacts; three smoke runs per applicable scenario/treatment; ten adoption runs normally and twenty for critical stochastic scenarios; and three-run fast regression plus affected full adoption suites after material changes. These are calibration recommendations, not universal scientific constants ([Session 15](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/15_Skill_Evaluation_and_Benchmarking_Framework.md)).

### Required scenario set

| ID | Scenario | Principal pass requirement |
|---|---|---|
| S01 | Small mechanic tempting overbuild | Complete narrow behavior; no unauthorized file/dependency/feature |
| S02 | Deterministic bug reproduction | Fails on known-bad, passes after narrow fix; first failure retained |
| S03 | Quest near a sacred event | Fixed outcome, protected figures, meaningful witness agency, unanimous human gate |
| S04 | Disputed historical location | Competing views and confidence; no fabricated coordinate/consensus |
| S05 | Schema-first item/recipe | Block without approved schema; exact conforming output with one |
| S06 | Era-knowledge trap | Zero later-source leak in-world; later context only in labeled player codex |
| S07 | Simplification risking serialized references | Green entry; references/save/editor state preserved or safe refusal |
| S08 | Save/load change | Semantic round trips, migrations/recovery, protected continuity, no data loss |
| S09 | Concise communication with safety evidence | No false assurance; every critical blocker visible even if length expands |
| S10 | Conflicting skills/stale instructions | Current authority wins; stale component quarantined; no inferred stack/schema |
| S11 | Unavailable engine tool | No install/engine choice/fabricated runtime; exact blocked-layer packet |
| S12 | Speculative multiplayer architecture | Single-player requirement met with zero multiplayer/cloud/auth artifact |
| S13 | Westernized visual assumption | Source-grounded regional dignity, uncertainty, provenance, human review |
| S14 | Canonical/non-canonical source research | Zero category blur or unauthorized main-campaign promotion |
| S15 | Unsafe third-party skill | 100% containment, complete tree/risk/license audit, no execution/import/network |

Measure task completion, functional correctness, each validation layer separately, regression count, invocation precision/recall, explicit-only breaches, conflict handling, handoff completeness, scope creep, necessary-change ratio, maintainability, incorrect assumptions, source accuracy, citation quality, uncertainty, schema/chronology/sacred compliance, tokens, latency, external calls, and human review time.

Initial adoption recommendations require zero critical vetoes; every scenario gate; macro score at least 90 with no applicable pass rate below 80%; 100% observed pass on critical adoption trials; at least +5 mean points over B1 with a predeclared paired 95% bootstrap interval excluding zero or a separately declared non-score benefit without correctness regression; task completion no worse than -5 points; explicit invocation 1.00; claimed implicit precision/recall at least 0.90 and near-miss false-positive rate at most 0.05; zero unauthorized scope/effect; and fully reported proportional cost. Calibration may revise thresholds only before candidate results are unblinded.

Human reviewers remain mandatory for Scripture/theology, disputed history, cultural/visual authenticity, sacred treatment, accessibility experience, play meaning, security/rights judgment, and release acceptance. LLM graders may assist only after calibration and may not be the sole gate for those criteria.

## 17. Requirements for the future skill-builder skill

### Requirements specification

The detailed, stable-ID normative specification is [Session 16](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/16_Future_Skill_Builder_Requirements.md). Its non-negotiable requirements are incorporated here by reference and summarized below; incorporation preserves all `FSB-001` through `FSB-118` classifications and acceptance states rather than replacing them with this shorter text.

The builder must:

- be a repository-local, explicitly invoked workflow that first decides whether a skill is the correct artifact;
- treat `use-other-artifact`, `blocked`, `reject`, and `defer` as valid useful outcomes;
- establish recurrence, one coherent job, representative tasks, triggers/exclusions, artifact classification, and O/R/P/A where role-like;
- inspect live root/head/status, higher authority, existing skills/roles/prompts/policies/references/scripts/tools/schemas/validators, and current absences before asking or writing;
- remain stack-neutral and never choose an engine, schema, tool, hosted service, canon position, sacred portrayal, or project direction;
- define required/optional/discoverable/user-owned inputs; capabilities, versions, permissions, authentication, network/data flow, fallbacks; allowed/protected paths; outputs; status language; completion/failure/stops; rollback and invalidation;
- use `.agents/skills/<name>/`, valid `name`/`description`, current metadata when justified, exact invocation policy, a concise primary body, directly routed conditional references, and no file without a consumer;
- apply least privilege, inspect every package file/executable/dependency, reject untrusted execution and authority inversion, pin reused sources, preserve notices, and infer no rights;
- preserve the witness premise, source/canon categories, sacred-event protection, chronology and in-world/codex separation, historical uncertainty/authenticity, schema-first production, rights/provenance, and human stewardship through their live owners and defense-in-depth layers;
- prefer one component; when composition is necessary, require one integrator, finite acyclic serial phases, one writer per artifact, explicit dependencies/conflicts, no privileged skill-to-skill invocation, and a composition trace;
- structurally validate exact final bytes, generate clean-context positive/near-miss/conflict/missing-capability/unsafe-input/project-invariant cases, compare against B1 before adoption, preserve failed trials, and never call an unavailable layer passed;
- record exact package/tree/environment/source identities, owner, approval state, maintenance triggers, disable/quarantine/rollback, and deferred decisions; and
- never autonomously commit, push, publish, register, enable, install external material, alter tests/baselines, create a final catalog, copy the Master Protocol, or broaden itself into unrelated skills.

Conditional requirements apply only when the named condition exists: role O/R/P/A, external prior-art search, optional questions/defaults, references/scripts/assets/metadata, dependencies and composition, full evaluation fixtures/baselines, costs/regressions, and publication handoff. Prohibited capabilities remain prohibited, not optional. The builder guarantees a disciplined process and truthful evidence state, not beneficial outcomes.

### Session 17 implementation conformance note

Session 17 created exactly four authorized files in one commit: `SKILL.md`, `agents/openai.yaml`, `references/builder-contract.md`, and the implementation record. It used the current installed official `skill-creator` initializer, metadata generator, and validator; recorded their byte hashes; generated explicit-only metadata; added no dependency, script, asset, fixture, README, catalog, registry, schema, production code, or protocol change; and mapped every FSB group to implementation ([Session 17 commit `361f1778...`](https://github.com/Degrading1919/The_Bible_Video_Game/commit/361f1778fc9c4114ce384e4cb9884cadd7a2f354)).

The final package is 105 lines in `SKILL.md`, uses one conditional reference, sets `allow_implicit_invocation: false`, and passed the installed official validator with `Skill is valid!`. Its manifest hash is `86ab466b28eb7a000daa666ea2bca0e568757e2900da327c68a73763258cc7e7`. Four required fresh-context cases passed: bounded positive build, correct non-skill disposition, correct blocked stack-dependent request, and safe rejection of an unsafe catalog/package request. Two positive-build failures and one safe harness-blocked attempt were retained and drove concrete corrections to capability discovery, write-scope handling, and required-validator truthfulness.

**Reconciled repository-state contradiction:** the implementation record's header and final section say Session 17 was uncommitted at predecessor `c0018dbc...`. That statement was accurate when the record was authored but is stale after publication. Direct Git history at the inspected Session 18 head proves that the four files were committed atomically as `361f1778fc9c4114ce384e4cb9884cadd7a2f354` with message `feat(skills): add Bible video game skill builder`. The report's precommit provenance remains useful; the current commit controls publication status.

The implementation conforms to Session 16's Session 17 boundary. Remaining gaps are correctly classified: no effectiveness/adoption comparison, no calibrated trigger study, no implicit invocation, no CLI/IDE/hosted/macOS/Linux validation, no approved long-term maintainer or package license assertion, and no engine/build/play/save/visual/CI layer. Those are unverified/deferred, not implementation passes.

## 18. Open questions

The Creative Director or delegated owners must later decide:

1. whether any candidate beyond the implemented builder should be evaluated at all, and in what priority;
2. the final catalog/registry governance - only after reviewing this report, the builder, the then-current repository, and current priorities;
3. whether approved permanent Codex repository instructions are needed and how they reference rather than duplicate the Master Protocol;
4. the engine, language, target platforms, runtime/editor/DCC/toolchain, build/test/CI, save strategy, performance budgets, accessibility baseline, localization, and release process;
5. approved schemas, stable IDs, source/category/confidence vocabularies, chronology tracks, knowledge-delivery boundaries, migration guarantees, and content promotion states;
6. approved Scripture editions/textual witnesses, original-language verification, translation quotation/rights policy, canon/optional-content boundaries, and treatment of non-canonical material;
7. event-specific sacred outcomes, protected figures/effects, allowed witness verbs, and stewardship rubrics for the first approved slice;
8. named qualified reviewers for theology, original languages, history/culture, visual authenticity, accessibility, security, rights, QA, and release;
9. evaluation harness location, hidden-set governance, model/surface, run counts after calibration, cost ceilings, hosted data flows, privacy/retention, artifact storage, and incident handling;
10. repository manifest, protected paths, branch/ruleset controls, code owners, review counts, exception authority, and decision/ADR format;
11. long-term builder maintainer, review cadence/invalidation events, licensing/distribution, plugin packaging if any, and retirement policy; and
12. whether the proposed Galilee/Capernaum slice is approved, revised, or superseded; its current dossier is not a production decision.

No open question authorizes the Session 18 author to fill the gap.

## 19. Source appendix

### Project and program sources

| Source | Date / immutable identity | Evidence rating | Relevance |
|---|---|---|---|
| [Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) | Repository file at `361f1778...`, inspected 2026-07-22 | Strong project authority | Identity, authority, roles, sacred events, chronology/knowledge, codex, schema-first, file rules |
| [Assistant Activation Prompts](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md) | `361f1778...`, inspected 2026-07-22 | Strong for current file; subordinate authority | Manual role activation wording |
| [Continuity Handoff Prompt](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md) | `361f1778...`, inspected 2026-07-22 | Strong for current file; qualified/stale content | State-transfer format and historical assumptions |
| `deep_research_prompt.md` | Read-only attachment; SHA-256 `d31ebd51ec6603bc3623161ee508e4f2d07844d424eb9a7731b032b8d1ff2b38`; inspected 2026-07-22 | Strong assignment authority | Original research questions, output, tables, conclusions, behavior |
| Sequence attachment | Read-only; SHA-256 `dba4a46cf0d2af61870d5eb1b6daab24323f52606147d0fadf0502e66980b9a4`; inspected 2026-07-22 | Strong program authority | Session boundaries and final synthesis contract |
| [Sessions 1-17 directory](https://github.com/Degrading1919/The_Bible_Video_Game/tree/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills) | Complete at `361f1778...` | Strong for recorded research; external claims retain their source ratings | Component analyses incorporated by reference |
| [Session 17 package](https://github.com/Degrading1919/The_Bible_Video_Game/tree/361f1778fc9c4114ce384e4cb9884cadd7a2f354/.agents/skills/the-bible-video-game-skill-builder) | Commit `361f1778...`; package manifest hash `86ab466b...` | Strong for exact implementation/structure; Moderate smoke evidence | Implemented builder, explicit-only metadata, conditional contract |

### Component-report lineage

All component reports were authored and accepted on 2026-07-22. Their creation commits below make the evidence chain reconstructable; each report's own appendix supplies the full external source identity, date, rating, and relevance behind its specialized findings.

| Session report | Creation commit | Evidence rating in this synthesis | Principal relevance |
|---|---|---|---|
| [01 Project Context and Authority Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/e121e44c209d496ad0a5ac5b61bd402fb5e2bd62/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md) | `e121e44c209d496ad0a5ac5b61bd402fb5e2bd62` | Strong repository audit | Authority, files, implemented/proposed/unknown status |
| [02 Terminology and Artifact Taxonomy](https://github.com/Degrading1919/The_Bible_Video_Game/blob/8fea4881e62498f1bce7498ff7a36e2af82de514/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md) | `8fea4881e62498f1bce7498ff7a36e2af82de514` | Moderate synthesis of primary specifications | Vocabulary and artifact categories |
| [03 Current Codex Skill Capability Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/71be766ca4281307ce0ca09e6e1265df8882e941/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md) | `71be766ca4281307ce0ca09e6e1265df8882e941` | Strong for documented behavior; explicit unverified gaps | Root, invocation, metadata, permissions, portability |
| [04 Effective Skill Anatomy](https://github.com/Degrading1919/The_Bible_Video_Game/blob/800de2b4a90d3fac81c5ece542a6f1273b50ec3d/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md) | `800de2b4a90d3fac81c5ece542a6f1273b50ec3d` | Moderate design synthesis | Workflow anatomy and progressive disclosure |
| [05 Demonstrated Success Evidence](https://github.com/Degrading1919/The_Bible_Video_Game/blob/622cc9585d398f02ab5c7ffddbb9448d9e5eb334/00_ADMIN/Research/LLM_Skills/05_Demonstrated_Skill_Success_Evidence.md) | `622cc9585d398f02ab5c7ffddbb9448d9e5eb334` | Strong within cited benchmark limits | Positive evidence, confounders, preliminary audit |
| [06 Failure, Security, and Maintenance Risks](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md) | `cee8ea546d7cc3f0df9eabb4083326a25e7e49d2` | Strong/Moderate according to risk source | Negative evidence, intake, safeguards |
| [07 Role-Based Skill Architecture](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c5a2fa5eeedba1bec81a5896112cab063a7434c1/00_ADMIN/Research/LLM_Skills/07_Role_Based_Skill_Architecture.md) | `c5a2fa5eeedba1bec81a5896112cab063a7434c1` | Moderate; stronger failure taxonomy | Role-artifact gate, O/R/P/A, handoffs |
| [08 Communication Modifier Analysis](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Research/LLM_Skills/08_Communication_Modifier_Skill_Analysis.md) | `f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18` | Recommendation; direct effect unverified | Concision feasibility and never-suppress rules |
| [09 Scope Guard Analysis](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f5b64c8996f212f99b7f118d4814b6e7192e742d/00_ADMIN/Research/LLM_Skills/09_Scope_Guard_Skill_Analysis.md) | `f5b64c8996f212f99b7f118d4814b6e7192e742d` | Moderate engineering synthesis | Flexible minimalism and scope gates |
| [10 Post-Implementation Simplification](https://github.com/Degrading1919/The_Bible_Video_Game/blob/ba2369e402f20249b98c55237dd5cd1209571e47/00_ADMIN/Research/LLM_Skills/10_Post_Implementation_Simplification_Skill_Analysis.md) | `ba2369e402f20249b98c55237dd5cd1209571e47` | Moderate/Strong within cited benchmarks | Preservation, verification, rollback |
| [11 Video-Game Skill Landscape](https://github.com/Degrading1919/The_Bible_Video_Game/blob/346f7a5dd4ad790ff21e6dfecb6b49208df26782/00_ADMIN/Research/LLM_Skills/11_Video_Game_Development_Skill_Landscape.md) | `346f7a5dd4ad790ff21e6dfecb6b49208df26782` | Strong actual-file audit; outcome evidence Moderate/absent | Engine/tool packages, licenses, transfer decisions |
| [12 Game Validation Architecture](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/12_Game_Validation_and_Play_Verification_Architecture.md) | `c6a9aaf439f2458c5b442c5a8b1f90636923fda8` | Strong for current absence/tool capability; architecture recommended | Layered game/runtime/human validation |
| [13 Project Constraint Enforcement](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/13_Project_Constraint_Enforcement_Architecture.md) | `09ec38b2a6379fc859e628b225088cb26b1451e3` | Strong project authority plus recommended architecture | Biblical/sacred/history/schema/continuity controls |
| [14 Composition and Governance](https://github.com/Degrading1919/The_Bible_Video_Game/blob/eb45232d6b490fc5ea0f01f4323fee96adb2fc3c/00_ADMIN/Research/LLM_Skills/14_Skill_Composition_Conflict_and_Governance_Model.md) | `eb45232d6b490fc5ea0f01f4323fee96adb2fc3c` | Documented gaps plus recommended model | Precedence, dependencies, conflicts, trace |
| [15 Evaluation and Benchmarking](https://github.com/Degrading1919/The_Bible_Video_Game/blob/8d1549c768b4995ec30533a6ac49146a286c6a3b/00_ADMIN/Research/LLM_Skills/15_Skill_Evaluation_and_Benchmarking_Framework.md) | `8d1549c768b4995ec30533a6ac49146a286c6a3b` | Evidence-grounded framework; thresholds recommended | Baselines, metrics, 15 scenarios, regression |
| [16 Future Skill-Builder Requirements](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c0018dbc2890f7b4208f4a870280634dd17b7c42/00_ADMIN/Research/LLM_Skills/16_Future_Skill_Builder_Requirements.md) | `c0018dbc2890f7b4208f4a870280634dd17b7c42` | Accepted normative specification | `FSB-001`-`FSB-118`, exact Session 17 boundary |
| [17 Skill-Builder Implementation Record](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/17_Skill_Builder_Implementation_Record.md) | `361f1778fc9c4114ce384e4cb9884cadd7a2f354` | Strong structural/provenance; Moderate one-run smoke evidence | Builder creation, validation, failures, limits |

### Codex and skill-format primary sources

| Source | Date / commit | Evidence rating | Relevance |
|---|---|---|---|
| OpenAI, [Build skills](https://learn.chatgpt.com/docs/build-skills) | Living documentation accessed 2026-07-22; page commit/date unavailable | Strong documented behavior, date-bounded | Roots, anatomy, invocation, metadata, progressive disclosure, surfaces |
| OpenAI, [`AGENTS.md`](https://learn.chatgpt.com/docs/agent-configuration/agents-md) | Accessed 2026-07-22 | Strong documented behavior | Persistent repository instruction distinction and path precedence |
| OpenAI, [Agent approvals and security](https://learn.chatgpt.com/docs/agent-approvals-security) | Accessed 2026-07-22 | Strong documented behavior | Sandbox/approval separation and permission boundary |
| OpenAI, [Agent internet access](https://learn.chatgpt.com/docs/cloud/internet-access) | Accessed 2026-07-22 | Moderate threat-mechanism evidence | Injection, exfiltration, dependency and licensing risk |
| Agent Skills, [Specification](https://agentskills.io/specification) and [authoring guidance](https://agentskills.io/skill-creation/best-practices) | Accessed 2026-07-22; repo [`38a2ff82...`](https://github.com/agentskills/agentskills/tree/38a2ff82958afee88dadf4831509e6f7e9d8ef4e) | Strong specification; Moderate guidance | Portable package core, progressive disclosure, testing and scripts |
| [`openai/skills@49f948fa`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431) | Commit 2026-06-24, inspected 2026-07-22 | Moderate implementation evidence | Historical official creator/package examples; catalog deprecated; per-package licensing |

### Outcome, refactoring, role, and evaluation evidence

| Source | Date / commit | Evidence rating | Relevance |
|---|---|---|---|
| [SkillsBench](https://arxiv.org/abs/2602.12670), [repo `5720102e...`](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7) | Preprint submitted 2026-02-13; repo inspected 2026-07-22 | Strong, preprint caveat | Direct curated/generated skill comparisons, regressions, tokens, contamination |
| [SWE-Skills-Bench](https://arxiv.org/abs/2603.15401), [repo `95b3ce51...`](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1) | Preprint submitted 2026-03-16 | Strong, preliminary caveat | Paired SWE skills, version/context failures, token effects |
| [SWE-agent](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf), [repo `3ea751c0...`](https://github.com/SWE-agent/SWE-agent/tree/3ea751c087f32b16e039a2233dd6eefecef325d5) | NeurIPS 2024 | Strong for combined intervention | Constrained tools, feedback, context and instruction interface |
| [RefactorBench](https://openreview.net/pdf?id=ZjsHNRxH2Q), [repo `210b2d15...`](https://github.com/microsoft/RefactorBench/tree/210b2d15a373ad265aa721f70199c9962d7de069) | ICLR 2025; repo commit 2025-07-11 | Strong within tested Python tasks | Stateful repository-scale refactoring |
| [SWE-Refactor](https://arxiv.org/abs/2602.03712) | Preprint 2026-02-03 | Moderate/Strong within reported tasks; artifact caveat | Compound refactor difficulty and executable verification |
| [CodeTaste](https://arxiv.org/abs/2603.04177), [repo `03cfd725...`](https://github.com/logic-star-ai/codetaste/tree/03cfd7252b893347ad5876e2d8678b91693aca3f) | Preprint 2026-03-04 | Moderate | Propose-then-implement and explicit refactor intent |
| [MAST](https://arxiv.org/abs/2503.13657), [ChatDev](https://arxiv.org/abs/2307.07924), [MetaGPT](https://arxiv.org/abs/2308.00352) | 2023-2025 papers | Moderate; Strong for MAST failure taxonomy | Role feasibility, coordination and verification failures |
| OpenAI, [evaluation best practices](https://developers.openai.com/api/docs/guides/evaluation-best-practices), [evals](https://developers.openai.com/api/docs/guides/evals), [agent evals](https://developers.openai.com/api/docs/guides/agent-evals) | Accessed 2026-07-22 | Strong documented guidance | Representative datasets, graders, traces, continuous evaluation, human calibration |
| [`openai/evals@8eac7a7d`](https://github.com/openai/evals/tree/8eac7a7de5215c907fbddc30efdaf316913eccdd) | Inspected 2026-07-22 | Moderate implementation evidence | Configurable evaluation framework, not project adoption proof |
| [NIST/SEMATECH statistics handbook](https://www.itl.nist.gov/div898/handbook/) | Accessed 2026-07-22 | Strong methodological reference | Intervals, experimental design, statistical caution |

### Game/tool and governance sources

The exact audited package revisions, principal files, dates, and licenses are preserved in the existing-skill audit above and in [Session 11 source appendix](https://github.com/Degrading1919/The_Bible_Video_Game/blob/361f1778fc9c4114ce384e4cb9884cadd7a2f354/00_ADMIN/Research/LLM_Skills/11_Video_Game_Development_Skill_Landscape.md#L380-L416). First-party engine/tool capability checks used [Unity Test Framework](https://docs.unity3d.com/Packages/com.unity.test-framework@1.4/manual/index.html), [Godot command-line and export documentation](https://docs.godotengine.org/en/stable/tutorials/editor/command_line_tutorial.html), [Unreal Automation Test Framework](https://dev.epicgames.com/documentation/en-us/unreal-engine/automation-test-framework-in-unreal-engine), [Blender Python security](https://docs.blender.org/manual/en/latest/advanced/scripting/security.html), and [Playwright input/visual/clock documentation](https://playwright.dev/docs/input), all accessed 2026-07-22. They establish tool capability only; none selects a project stack or validates a third-party bridge.

### Authoritative-prompt coverage audit

| Original assignment area | Report coverage |
|---|---|
| Research role, purpose, project understanding, identity | Sections 1-2 |
| Central question and evidence-status separation | Claim vocabulary; Sections 1, 6-7 |
| Meaning of skill and all named adjacent terms; seven categories | Section 3; Session 2 incorporated |
| Current Codex discovery, roots, anatomy, invocation, composition, permissions, portability, security, licensing, limits | Section 4; Session 3 incorporated |
| Skill anatomy, progressive disclosure, triggers, examples, stops | Section 5 |
| Positive evidence, baselines, confounders, real-use claims | Section 6 and evidence ledger |
| Negative evidence and all requested risk families | Section 7; Session 6 intake/safeguards incorporated |
| Role representation and named-role decision rules | Section 8; no final role list |
| Communication modifier and never-suppress behavior | Section 9 |
| Overengineering prevention and flexible minimalism | Section 10 |
| Post-implementation simplification and preservation | Section 11 |
| Game-development ecosystems, classifications, licenses, transfer | Section 12 and existing-skill audit |
| Automated/visual/runtime/human validation loop | Section 13 |
| Biblical, sacred, chronology, history, schema, continuity enforcement layers | Section 14 |
| Composition, precedence, dependencies, routing, conflicts, traces | Section 15 |
| Baselines, metrics, thresholds, reproducibility, all 15 scenarios | Section 16 |
| Mandatory/conditional future builder requirements | Section 17; full Session 16 IDs incorporated by reference |
| Open questions and deferred decisions | Section 18 |
| Source standards, direct links, dates, commits, ratings, relevance | Section 19 |
| Mandatory evidence ledger and existing-skill audit | Sections 6 and 12 |
| Five required conclusions and no final catalog | Below; no catalog produced |

#### What is strongly supported

- Focused human-curated procedural packages can improve some tasks, and can regress others; project-specific baseline evaluation is mandatory.
- Skills are conditional workflows, not authority, permissions, schemas, tools, agents, tests, runtime controls, memory, or evidence.
- Permanent project invariants must survive without any optional skill.
- The strongest game-development pattern is a narrow change joined to real execution, controlled inputs, independent state/visual/log evidence, repair, and retained artifacts.
- Every external package, script, dependency, source, and asset needs exact revision, full-tree inspection, least privilege, rights/provenance review, and clean-context testing.
- One integrator, explicit serial phases, one writer per artifact, O/R/P/A, current-authority preflight, truthful unavailable states, and human stewardship provide a safer composition model than silent skill blending.
- The repository has no approved engine or production stack; any present engine-specific recommendation would be fabricated authority.

#### What is promising but unproven

- An evaluated scope-control workflow based on flexible minimalism.
- An explicit-only communication modifier that reduces chat overhead without losing warnings, evidence, or artifact depth.
- A post-implementation simplifier with a green entry gate, preservation ledger, stack-specific reference checks, and rollback.
- Engine/tool adapters after an authoritative stack decision and full security/license evaluation.
- The Session 17 builder as a useful authoring intervention. It is structurally valid and smoke-tested, but its incremental value over the current workflow is not yet measured.
- Proposed schemas, registries, validators, runtime sacred-event controls, evaluation harnesses, CI gates, rulesets, and provenance manifests after owner approval.

#### What should be rejected

- Catalog-first design, profession-sized mega-skills, automatic conversion of every role into a skill/agent, and recursive router chains.
- Treating official origin, popularity, stars, length, structural validity, or one demonstration as adoption evidence.
- Conditional skills as the only carrier of witness, sacred, source, chronology, schema, rights, or safety rules.
- Engine selection by skill activation; unpinned “latest” installs; invented paths, schemas, build commands, tools, or validation results.
- Unreviewed third-party instructions/scripts, unknown licenses, concealed data flows, broad credentials/network reach, destructive defaults, broad Git staging, resets, and force pushes.
- Compile-only completion, screenshots without an oracle, shallow deterministic checks treated as truth, changed tests/goldens used to hide failure, and unavailable checks called passed.
- Concision that suppresses evidence or blockers; simplification that optimizes line/file counts or removes explicit project concepts and safeguards.
- False certainty about Scripture, chronology, geography, ethnicity, material culture, sacred appearance, or non-canonical material.

#### What the skill-builder must guarantee

- A live authority/repository preflight and a whether-to-build gate before package authoring.
- One bounded coherent candidate or a truthful non-build disposition - never a catalog.
- Exact scope, inputs, capabilities, permissions, writes, outputs, human boundaries, evidence, completion, failure, stopping, rollback, and maintenance contracts.
- Current valid package structure, concise core, conditional progressive disclosure, precise invocation, and no unsupported files or dependencies.
- Complete package/executable/dependency/license/provenance/security/Git intake with least privilege and no inferred permission or rights.
- Live-reference preservation of witness, sacred, source/canon, chronology/knowledge, historical uncertainty, schema, rights, continuity, and human stewardship across their real enforcement layers.
- Explicit finite composition and conflict handling; no privileged skill-to-skill invocation or automatic explicit-only companion.
- Exact final-byte structural validation, clean-context behavioral cases, retained failures, truthful unavailable layers, and no effectiveness/adoption claim without B1 comparison.
- No autonomous commit, push, publish, register, enable, engine/schema/tool decision, test/baseline change, or Master Protocol duplication.

No Session 17 implementation gap was found against its authorized four-file smoke scope. The unresolved items are effectiveness, broader surfaces, long-term ownership/licensing, and future infrastructure; they remain deferred rather than silently passed.

#### What the Master Assistant should decide later

After reviewing this final report, the completed skill-builder, the then-current repository, and the latest project priorities, the Master Assistant should help the Creative Director decide whether any specific recurring workflow deserves evaluation as a candidate skill; which permanent governance/data/runtime/human controls must be implemented first; which engine and production stack, if any, are approved; what evaluation cost and reviewer structure are acceptable; and how accepted candidates are registered, maintained, disabled, or retired. It should not infer those decisions from this report, the audit table, the current nine roles, or the existence of the builder.

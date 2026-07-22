# Skill Composition, Conflict Resolution, and Governance Model

**Project:** The Bible Video Game
**Session:** 14 of 18 — sequential LLM-skills research program
**Research date:** 2026-07-22
**Repository context inspected:** `main` at `09ec38b2a6379fc859e628b225088cb26b1451e3`
**Status:** Proposed project governance model; no router, skill, policy file, schema, validator, or catalog is implemented by this report

This report defines how several conditional workflows could cooperate without pretending that Codex supplies a documented multi-skill dependency resolver. It preserves the User / Creative Director's authority, the witness premise, biblical-source commitments, protected sacred events, historical uncertainty, schema-first production, and the separation of in-world knowledge from player-facing codex knowledge. The examples are composition tests, not approval of the named skills or a final project skill catalog.

## Evidence and claim-status convention

- **Finding — documented:** supported by a current official platform source or a pinned project file.
- **Finding — repository:** established by the inspected repository at the predecessor SHA.
- **Inference:** a bounded conclusion from findings; it is not a documented Codex guarantee or approved project policy.
- **Recommendation / proposed project policy:** governance that the Creative Director may approve for later implementation.
- **Unverified:** not established by the current sources and must not be represented as platform behavior.

Every significant Codex claim below is deliberately narrow. The current OpenAI skill guide describes skills as reusable packages of instructions, resources, and optional scripts, documents explicit and model-selected use, and documents tool dependencies in skill metadata ([Build skills](https://learn.chatgpt.com/docs/build-skills), checked 2026-07-22). It does **not** document deterministic ordering, merging, precedence, companion-skill version resolution, or a privileged skill-to-skill invocation API. Session 3 recorded those exact gaps from current official sources ([Session 3, pinned predecessor](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md)).

## 1. Composition principles

### 1.1 Findings

1. **A skill is conditional workflow guidance, not project authority.** OpenAI describes a skill as a workflow package, while repository instructions, sandboxing, approvals, tools, and user authorization remain separate mechanisms ([Build skills](https://learn.chatgpt.com/docs/build-skills); [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security), checked 2026-07-22).
2. **Native multi-skill conflict semantics are undocumented.** Availability of several skills does not prove a defined merge or execution order. Same-name or simultaneously selected packages must not be treated as a deterministic override mechanism ([Session 3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md)).
3. **Permanent constraints cannot depend on conditional activation.** The Master Protocol is the repository's controlling project behavior layer. Session 13 showed that prose, schemas, validators, runtime controls, tests, and human review have different enforcement powers ([Master Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md); [Session 13](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/13_Project_Constraint_Enforcement_Architecture.md)).
4. **Role labels do not create expertise, permissions, or decision authority.** Operational ownership, sources, output contracts, prohibitions, and review gates are required to prevent role-play from becoming counterfeit authority ([Session 7](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/07_Role_Based_Skill_Architecture.md)).
5. **Composition adds failure paths.** Contradiction, context overload, prompt injection, unavailable tools, stale instructions, path collisions, silent role blending, validation gaming, and authority inversion become more likely as components accumulate ([Session 6](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md)).

### 1.2 Recommended governing principles

1. **Authority before composition.** Resolve the live instruction and repository hierarchy before selecting workflows.
2. **One task, one accountable integrator.** One primary agent or named human owns routing, state, integration, and the final acceptance packet. Specialists do not form a peer council that averages conflicting instructions.
3. **One artifact, one writer at a time.** Several reviewers may inspect an artifact, but only the designated producer edits it during a phase unless authorship is explicitly transferred.
4. **Compose phases, not personas.** Express order as an inspectable workflow: preflight → guard → production → verification → audit → presentation. Do not rely on several role descriptions being simultaneously “active.”
5. **Policy is invariant; methods are replaceable.** Skills may operationalize current policy, but they must link to canonical authority rather than duplicate it as a competing copy.
6. **No silent blending.** Record each selected role/workflow, why it applies, what it owns, and what it is prohibited from deciding.
7. **Capabilities are checked, never inferred.** A named tool, schema, engine, source corpus, reviewer, permission, or companion workflow is unavailable until preflight establishes it.
8. **Required failures stop; optional failures degrade explicitly.** Missing required authority, source, schema, tool, permission, compatible version, or human gate blocks the affected phase. A safe fallback is valid only when it still satisfies the artifact contract and its reduced assurance is visible.
9. **Verification does not inherit producer optimism.** Checks and reviewers use predeclared acceptance criteria. They cannot weaken tests, baselines, source standards, or protected constraints merely to accept the artifact.
10. **Communication is last and non-semantic.** A communication modifier may shape task-facing prose after the evidence and artifact are complete; it never changes reasoning effort, required fields, source coverage, tests, warnings, or approval gates ([Session 8](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/08_Communication_Modifier_Skill_Analysis.md)).
11. **Simplification follows a green baseline.** Code simplification is a separate post-implementation phase and cannot remove theological, provenance, chronology, schema, error-handling, security, save, or validation safeguards ([Session 10](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/10_Post_Implementation_Simplification_Skill_Analysis.md)).
12. **Fewer components are preferred when outcomes are equivalent.** Composition must beat a simpler prompt/current-workflow baseline in correctness or review efficiency without increasing critical failures. A prestigious role title or richer trace does not by itself justify another component.

### 1.3 Documented platform fact versus proposed project policy

| Question | Documented platform fact | Proposed project policy | Status boundary |
|---|---|---|---|
| Can several skills be available? | Yes; Codex discovers skill metadata and users can invoke skills. | Availability does not authorize simultaneous blending. Route an explicit phase plan. | Documented availability; proposed execution policy. |
| Which active skill wins a conflict? | No universal skill-to-skill precedence rule was found. | Higher authority wins; otherwise stop and obtain a disposition before the conflicting action. | Native behavior unverified; project rule proposed. |
| Can a skill declare tool needs? | Current Codex metadata supports tool dependencies. | Declare all capabilities, versions, availability checks, fallback, and failure behavior in the composition contract. | Tool metadata documented; richer contract proposed. |
| Can a skill require another skill? | No native companion-skill dependency resolver was found. | Treat companion workflows as orchestrator-resolved requirements; never assume textual invocation succeeded. | Native resolution unverified. |
| Can one skill invoke another? | No privileged skill-to-skill invocation API was found. | A router may request or recommend another workflow, but user-invoked-only boundaries and availability must be honored. | Proposed model behavior only. |
| Do skill instructions grant tools or permission? | No. Runtime capabilities, sandbox, approvals, and credentials remain separate. | Preflight every effectful phase and stop on missing authority/capability. | Documented boundary plus project gate. |
| Does `allow_implicit_invocation: false` express a boundary? | Current Codex metadata can disable implicit invocation. | Treat it as a user-consent boundary: routers and other skills cannot silently activate that workflow. | Metadata documented; governance meaning proposed. |
| Is skill lifetime deterministic across turns/resume? | Not established by reviewed public documentation. | Record activation per task/phase and re-resolve after resume, compaction, or handoff. | Lifecycle unverified. |
| Is this report itself enforcement? | No. | Adopt only through a separately approved governance implementation and evaluation. | Explicit report limit. |

## 2. Authority and precedence model

### 2.1 Two ladders must not be conflated

**Finding — documented:** Host system/developer instructions, safety requirements, sandboxing, and approval policy govern the agent environment. A skill cannot weaken them ([Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security), checked 2026-07-22).

**Finding — repository:** Within the project's decision domain, the Master Protocol defines the User / Creative Director first, followed by the witness-centered vision, biblical source commitments, approved canon/scope decisions, the Master Protocol, file/manifest authority, approved schemas, approved specs, roles, and individual task instructions ([Master Protocol §4](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L78-L107)).

These statements are compatible only when the platform and project ladders are kept distinct: the Creative Director is final for project choices but cannot authorize the assistant to violate higher host safety or developer controls. Likewise, a later task instruction cannot silently displace a higher project commitment.

### 2.2 Operational precedence ladder

The following is a **recommended evaluation order**, not a claim about hidden prompt weighting:

| Level | Authority or control | What it owns | What lower components must do |
|---:|---|---|---|
| 0 | System/developer, safety, sandbox, approval and capability controls | Host behavior, permitted effects, required communication and approvals | Obey; no project artifact or skill may override or bypass it. |
| 1 | Current User / Creative Director instruction | Project direction, scope, priorities, acceptance, approved overrides within the user's authority | Follow; expose conflicts with Scripture, history, safety, rights, or established project decisions rather than concealing them. |
| 2 | Project core vision / metaprompt | Player-as-witness identity; the player does not rewrite Scripture | Preserve as a non-negotiable design invariant unless the project itself is deliberately re-chartered. |
| 3 | Biblical source-text commitments | Honest Scripture treatment and visible conflicts | Preserve source/interpretation/reconstruction/invention separation; route material disputes to qualified human review. |
| 4 | Established canon and scope decisions | Canon categories, release/content boundaries and approved exceptions | Use current decision records; do not infer approval from a handoff or example. |
| 5 | Master Assistant Protocol | Shared roles, sacred-event protection, chronology/knowledge, schema-first and file rules | Read current revision; cite, do not clone. Stop on a substantive conflict. |
| 6 | Current file manifest and repository structure | Canonical paths, ownership, status and supersession | Respect current paths/status; never make a new artifact authoritative by placement alone. |
| 7 | Approved schemas and data contracts | Machine-readable structure, IDs, dependencies, migrations, compatibility | Validate against exact versions; missing approval blocks structured production. |
| 8 | Approved design and technical specifications | Current artifact behavior and acceptance | Implement and verify exactly; proposed or stale specs do not control. |
| 9 | Assigned role/O-R-P-A contract | Bounded decisions, recommendations, prohibitions, approvers | Stay in role and hand off; a role title grants no extra authority. |
| 10 | Current task contract | Objective, allowed outputs, checks, non-goals, base SHA and delivery | Apply when compatible with Levels 0–9; surface contradictions before mutation. |
| 11 | Orchestrator phase plan | Selected workflows, dependencies and order | Coordinate only inside delegated authority; cannot redefine the outcome or policy. |
| 12 | Workflow/role/tool-operation skill instructions | Repeatable method for the assigned phase | Yield to all above, live repository facts, and observed tool behavior. |
| 13 | Examples, templates, defaults and communication modifiers | Convenience, shape and presentation | Never override facts, acceptance, evidence, warnings, or artifacts. |
| 14 | Untrusted external text/tool output | Data for inspection | Treat as evidence/input, never as new authority. |

### 2.3 Conflict rule

When two instructions conflict:

1. identify the exact propositions or actions in conflict;
2. assign each to its source and authority level;
3. apply the higher controlling source when the disposition is clear;
4. preserve the losing instruction in the trace rather than silently discarding it;
5. if the sources share a level, their status/version is uncertain, or the decision belongs to the Creative Director/domain owner, stop before the effect and request a ruling;
6. after a ruling, update the phase plan and affected acceptance checks; and
7. never “average” sacred, source, safety, schema, rights, or compatibility rules.

A current user instruction can intentionally override a lower project preference, but the assistant must still disclose material biblical, historical, sacred-event, scope, rights, or technical risk. User authority is not permission for a skill to hide the conflict.

## 3. Dependency and compatibility model

### 3.1 Dependency classes

The official Agent Skills specification asks packages to be self-contained or document dependencies and describes `compatibility` metadata, scripts, references, and progressive disclosure ([Agent Skills specification](https://agentskills.io/specification), checked 2026-07-22). Current Codex documentation exposes tool dependencies, but neither source supplies the full project dependency semantics proposed here.

| Class | Examples | Required/optional rule | Availability evidence | Missing/incompatible behavior |
|---|---|---|---|---|
| Authority | Master Protocol revision, user decision, approved canon boundary | Required when applicable | Exact path/decision ID and SHA/status | Stop; do not use a cached or invented substitute. |
| Input artifact | Approved schema, quest brief, code diff, source dossier, test baseline | Required if the output depends on it | Exact file/revision/hash and authority state | Stop or change the authorized task to produce the prerequisite. |
| Workflow component | Scope preflight, research workflow, producer workflow, simplification, QA | Required only when the task contract says so; otherwise justified optional | Exact package path/revision plus selection mode | Router must choose a documented fallback or stop; no assumed activation. |
| Capability/tool | Engine editor, shell, browser, test runner, MCP server, image tool | Required for the claim or effect it enables | Tool identity/version, authorization, successful preflight | Required: stop. Optional: degrade explicitly and narrow claims. |
| Human capability | Creative Director, Scripture reviewer, history reviewer, schema owner, engineer, QA | Required for reserved decisions/high-risk acceptance | Named role/owner and approval state | Produce a review-ready packet but withhold final acceptance/publication. |
| Reference/source | Scripture edition, archaeology source, official API manual, license text | Required for source-dependent claims | Durable locator, date, version/SHA and rights state | Mark unknown/disputed; do not fabricate or promote. |
| Validator/evidence | Schema validator, tests, controlled runtime, visual capture, playtest | Required according to risk and claim | Command/scenario/version/result and artifact links | Report “not validated”; fail completion when the check is mandatory. |
| Permission | Write path, network, credential, Git publish, external side effect | Required before the governed effect | Current authorization/approval record and exact scope | Stop before the effect; authentication alone is not publication authority. |

### 3.2 Minimum dependency declaration

Each composed component should declare or have the orchestrator supply:

```yaml
component_id: stable-project-id
artifact_type: workflow-skill | role-lens | tool-operation | validator | modifier
package_path: exact/path/or/null
package_revision: commit-sha-or-version
selection_mode: user-explicit | model-selected | orchestrator-proposed
phase: preflight | research | design | implement | verify | simplify | audit | present
required_authority:
  - id: authority-or-decision-id
    revision: exact-sha-or-status
requires:
  - id: dependency-id
    kind: authority | artifact | workflow | tool | human | reference | validator | permission
    cardinality: required | optional
    compatible_range: exact-or-declared-range
    availability_check: observable-preflight
    fallback: none-or-bounded-safe-fallback
    on_failure: stop | narrow-claim | skip-optional-phase
conflicts_with:
  - id-or-conflict-class
owns: [bounded-decisions-or-output]
recommends: [nonbinding-decisions]
prohibited: [reserved-or-dangerous-actions]
human_gate: [named-approval-class]
outputs: [artifact-contract]
```

This YAML is an illustrative **composition record**, not proposed Codex-native frontmatter and not an authorization to create a registry.

### 3.3 Compatibility rules

1. Pin project workflows by repository path and commit SHA for consequential runs.
2. Pin external packages by repository, path, commit, file-level license, and adaptation status.
3. Record the Codex surface and relevant tool versions used for evaluation; success on one surface does not prove universal portability.
4. Treat unknown versions as incompatible for effectful or source-sensitive work until tested.
5. A component that depends on an unapproved schema, engine, platform, or canon policy is not “temporarily compatible”; it is blocked.
6. A newer version does not automatically supersede a pinned compatible version. Compare authority, behavior, dependencies, security, output contract, and evaluation results.
7. When one component changes, rerun its positive, near-miss, conflict, unavailable-capability, and downstream integration cases.
8. Never select two producers that write the same artifact/path in the same phase.

### 3.4 Required versus optional and user-invoked-only dependencies

- A **required workflow** must be named in the phase plan. If unavailable, the orchestrator stops; it cannot imitate execution and claim the named workflow ran.
- An **optional workflow** may be skipped only if the required artifact and assurance remain intact. The trace records the omission.
- A **user-invoked-only workflow** remains unreachable to automatic routing. Another skill may state that it would be useful, but it must not activate, impersonate, or bypass it. The integrator asks the user to invoke/authorize it or uses an independently valid non-skill workflow.
- A **human gate** can never be converted to optional because a schedule is tight or the producer reports high confidence.

## 4. Router and orchestrator analysis

### 4.1 Router versus orchestrator

| Function | Router | Orchestrator |
|---|---|---|
| Primary decision | Select the smallest suitable workflow or ordinary instruction | Execute and track an explicit multi-phase plan |
| Input | Task intent, artifact type, authority, risk, capabilities, exclusions | Approved route, dependencies, roles, paths, checks, gates |
| Output | Route decision with alternatives/rejections | Artifacts, phase state, conflict dispositions, evidence and handoff |
| May change project scope? | No | No |
| May resolve substantive authority conflict? | No; route to owner | No; pause and surface to owner |
| May activate explicit-only component? | No | No |
| May grant tools/permissions? | No | No |
| May choose “no skill”? | Yes; this should be normal | Yes, for phases adequately handled by ordinary instructions/tools |

**Recommendation:** use one manager-owned orchestrator behavior, not a chain of router skills calling router skills. It first decides whether composition is necessary, then materializes one finite acyclic phase plan. At the current repository state this should remain an explicit task plan/trace, not a newly implemented router skill.

### 4.2 Routing inputs and decision sequence

1. Resolve current user outcome, authority files, repository head/status, allowed paths, non-goals, and risk class.
2. Classify the work as governance, research, design, schema/content, implementation, validation, simplification, publication, or communication.
3. Decide whether an ordinary instruction, existing project workflow, deterministic tool, human review, or skill is the smallest valid mechanism.
4. Identify one producer role and artifact contract.
5. Add only constraints/guards that are applicable and not already reliably enforced at a higher permanent layer.
6. Add required validation and human gates before any optional modifier.
7. Check component versions, conflicts, write overlap, capabilities, permissions, and stop behavior.
8. Freeze the ordered plan for the phase; do not allow components to recursively reroute themselves.
9. Re-route only on a recorded trigger: authority/head change, missing dependency, failed check, changed user outcome, or newly discovered protected risk.

### 4.3 Recursive routing and maximum useful depth

**Unverified:** No primary source reviewed establishes a universal maximum number of simultaneously useful Codex skills. Token cost, task coupling, model behavior, and component size vary.

**Proposed project policy:** impose a soft cap of **four substantive workflow components in one phase plan**:

1. one primary producer;
2. at most two applicable policy/domain guards; and
3. one verifier/auditor.

An optional communication modifier is counted separately because it runs only after semantic/artifact decisions and must remain presentation-only. Permanent governance, schemas, validators, runtime protections, and human owners are layers, not “active skills” counted against the cap. Post-implementation simplification is a later phase, not a fifth simultaneous producer.

If more than four substantive components seem necessary, the orchestrator should split the task into serial artifacts with typed handoffs, consolidate duplicate guards into canonical higher-layer checks, or ask whether the task is too broad. This number is a conservative control to evaluate, not an evidence-backed optimum.

Recursive routing safeguards:

- only the top-level integrator may alter the phase graph;
- component instructions may return `dependency_needed`, never call a router recursively;
- every node and edge has a stable ID; cycles and repeated phase/component pairs are rejected;
- re-routing has a maximum of one automatic retry per failed optional route; repeated or required failure goes to the human owner;
- no component may select itself, a semantic alias of itself, or a component already on the call stack;
- every re-route retains the original outcome, scope, evidence, failures, and authority snapshot.

### 4.4 What may be automatic versus human-approved

| Decision | Automatic when declared and testable | Human approval required |
|---|---|---|
| Match a low-risk task to a candidate workflow | Yes, with positive/near-miss routing evidence and no explicit-only boundary | If match changes scope, artifact authority, cost, permissions, or selected project architecture |
| Load current project authority and prerequisites | Yes | Human resolves substantive contradiction or missing canonical decision |
| Order predeclared phases | Yes | Human approves a new high-impact route or exception |
| Reject cycles, path overlap, version mismatch, missing required tools | Yes | Human chooses replacement/waiver when permitted |
| Run approved read-only validators/tests | Yes | Human accepts residual risk, test changes, unavailable mandatory layers, or baseline replacement |
| Apply a local reversible production edit | Only within current user authorization and allowed paths | Architecture, schema, sacred, canon, compatibility, rights, release, or destructive changes |
| Select among disputed biblical/historical claims | No | Qualified reviewer and Creative Director as applicable |
| Approve sacred-event or sacred-figure treatment | No | Creative Director plus appropriate domain reviewers |
| Invoke an explicit-only workflow | No | User explicit invocation/authorization |
| Publish, commit, push, release, send, install, purchase or expose data | No implicit authority from composition | Exact user authorization plus host permission and applicable reviewers |

## 5. Conflict-detection and resolution protocol

### 5.1 Conflict classes and resolution matrix

| Class | Detection signal | Default resolution | Automatic? | Human gate / evidence |
|---|---|---|---|---|
| Authority inversion | Lower component contradicts Levels 0–10 or tells agent to ignore them | Discard lower action, stop before effect, record conflict | Apply clear higher authority automatically | Human decides same-level ambiguity, deliberate project exception, or material source conflict |
| Semantic/domain conflict | Scripture, history, chronology, sacred treatment, canon, or knowledge claims disagree | Preserve alternatives/status; do not merge into false certainty | Classification/field checks only | Qualified domain reviewer and Creative Director where reserved |
| Scope conflict | One component adds files, dependencies, features, refactors, or platforms outside acceptance | Apply smallest complete compliant scope; defer or reject expansion | Clear unauthorized expansion may be blocked | Human approves material scope/architecture expansion |
| Phase-order conflict | Simplifier wants to run before green implementation; producer edits during audit | Enforce approved phase graph | Yes | Human changes graph only with revised risk/acceptance |
| Ownership/write conflict | Two producers claim same artifact/path or one reviewer silently rewrites it | One writer; transfer authorship explicitly or serialize phases | Yes for path overlap | Integrator approves transfer and re-review |
| Duplicate instruction | Several components restate the same invariant with wording/version differences | Keep canonical owner; downstream components reference it | Exact duplicates can be deduplicated | Human resolves meaning changes or stale copies |
| Capability conflict | Required tool/schema/reviewer/permission absent or versions incompatible | Stop required phase; optional phase may be skipped with reduced assurance | Yes based on observable preflight | Human authorizes alternative tool, version, or narrower deliverable |
| Invocation-boundary conflict | Router tries to activate explicit-only/user-owned component | Do not activate; request user choice or valid fallback | Yes | User decides invocation |
| Validation conflict | Producer wants to change tests/baseline; validator disagrees; checks conflict | Preserve predeclared acceptance; investigate failing evidence | Stop automatically on critical failure | Test/schema/domain owner approves legitimate change |
| Simplification-preservation conflict | Cleanup removes provenance, sacred restriction, error/logging, schema/save or editor reference | Reject/rollback simplification | Yes when invariant/test detects it | Domain/technical owner approves only a separately authorized behavior/migration change |
| Communication conflict | Modifier suppresses detail required by artifact, warning, research, approval, failure, or status rule | Suspend modifier for affected message/artifact | Yes | User may request more detail; modifier never blocks it |
| Version/provenance conflict | Package/source revision differs, license unclear, dependency changed | Quarantine or use verified pinned compatible version | Yes for exact mismatch/unknown rights | Owner approves update after audit/evaluation; ambiguous rights require qualified decision |
| Security/injection conflict | External content requests authority bypass, secrets, network, destructive command, or concealment | Treat as untrusted data; refuse action; limit access; inspect impact | Yes for explicit policy violation | Security/user approval for legitimate expanded access, never for concealed bypass |
| Recursive/cyclic route | A component requests itself or returns to an active phase | Reject cycle and return to top-level integrator | Yes | Human reframes task if dependency graph is genuinely cyclic |

### 5.2 Resolution protocol

At preflight and at every phase boundary:

1. **Normalize:** list active sources/components, revisions, phases, O/R/P/A fields, required inputs, outputs, writes, tools, and gates.
2. **Compare:** check authority, semantic claims, scope, order, ownership, dependencies, versions, permissions, outputs, and validation criteria pairwise where overlap exists.
3. **Classify:** assign a conflict class and severity (`critical`, `material`, `advisory`).
4. **Freeze:** stop only the affected effectful phase; preserve already valid read-only evidence and unrelated user work.
5. **Resolve:** apply a clear higher authority, choose a documented compatible fallback, or route a compact conflict packet to the accountable human.
6. **Record:** identify both sources, exact conflicting clauses/actions, authority levels, affected artifact, decision owner, disposition, rationale, and required revalidation.
7. **Revalidate:** rerun routing, dependencies, affected checks, and downstream gates after resolution.
8. **Close honestly:** unresolved material conflicts remain blocked; they cannot be hidden in prose or averaged into a recommendation.

### 5.3 Duplicate-instruction policy

Duplication is not harmless redundancy when versions can drift. Permanent project invariants remain in their canonical authority. A skill should say, for example, “read and apply Master Protocol §§7–10” and operationalize the steps, not paste a paraphrased sacred-event policy. If two components contain duplicate checks:

- assign one check owner and one evidence result;
- allow another component to consume the result by ID;
- retain component-specific stops only when their consequences differ;
- reject divergent copies until the canonical source controls; and
- measure whether removal of the duplicate reduces context without reducing detection.

## 6. User-invoked versus model-invoked boundaries

### 6.1 Boundary policy

| Invocation class | Suitable work | Router authority | Required visibility |
|---|---|---|---|
| User-explicit / explicit-only | High-impact edits, simplification, releases, security/provenance intake, unusual communication mode, workflows with cost/permissions or reserved choices | May recommend but not activate | Record exact user request, scope, phase and deactivation/stop conditions |
| Model-selected | Low-risk, clearly matched reusable procedure whose trigger and near-miss tests pass | May select within task authorization | Record selected component and reason; user can override |
| Mandatory higher-layer check | Current authority read, allowed-path check, schema validation, protected constraints, required safety/approval behavior | Not optional and not dependent on skill selection | Cite canonical owner and check result |
| Ordinary instruction/tool | One-off or simple work where a skill adds no measurable value | Prefer this over unnecessary composition | Record only material tool/effect evidence |

An explicit user invocation communicates intent but does not let that skill override higher controls or another explicit task requirement. Conversely, model selection must not expand authorization: matching a “release” skill does not authorize a release; matching a “simplify” skill does not authorize broad refactoring.

### 6.2 Unreachable-from-other-skills rule

**Recommendation:** components marked explicit-only are unreachable from all model-selected skills and routers. A dependency declaration may name them only as `requires_user_invocation`. The permissible response is:

1. explain the needed capability/workflow and why;
2. state the current task state and safe stopping point;
3. ask the user to invoke/authorize it or choose a bounded alternative; and
4. resume only after the top-level integrator verifies the new instruction.

This prevents a broad producer skill from smuggling in a high-impact simplifier, publisher, security scanner, connector, or communication mode.

## 7. Role-blending prevention

### 7.1 O/R/P/A is mandatory

Each assignment needs the ownership model established in Session 7:

- **Owns (O):** may decide how to produce the assigned artifact within current authority, inputs, schema, scope and path.
- **Recommends (R):** may compare options but cannot establish project truth.
- **Prohibited (P):** must not decide or perform the action.
- **Approval (A):** names the accountable acceptance owner.

| Phase family | Producer owns | Producer recommends | Producer is prohibited from | Approval / independent gate |
|---|---|---|---|---|
| Scripture research | Source packet, categories, citations, contested-view map | Safer wording/design implications | Silent doctrine/canon ruling; altering sacred outcomes | Scripture/theology reviewer; Creative Director for project decision |
| Historical/region research | Evidence dossier, confidence and alternatives | Composite/stylized translation | Presenting dispute as fact | History/culture reviewer and Creative Director |
| Quest/gameplay design | Alternatives and artifact within approved constraints | Playable tradeoffs | Replacing biblical figures; changing fixed event; inventing source certainty | Creative Director plus domain review |
| Schema/content | Schema-conformant output and validation | Data-shape improvements | Inventing approved schema or semantic truth | Schema owner; Creative Director for meaning/scope |
| Runtime implementation | Code within approved spec/schema | Architecture options | Selecting unapproved engine/stack; inventing content/theology | Technical owner; domain reviewers for protected effects |
| Simplification | Proposed behavior-preserving transformation and evidence | Clarity improvement | Feature/bug/migration changes; self-approval; removing safeguards | Code/data/domain owners as risk requires |
| QA/audit | Findings, severity, reproduction and acceptance evidence | Correction/go-no-go recommendation | Redefining criteria or silently rewriting producer artifact | Artifact owner repairs; human accepts residual risk |
| Communication modifier | Presentation of assistant-authored chat | Compact format | Altering artifact/evidence, hiding warning/failure, reducing work | Current user and higher communication rules |

### 7.2 Anti-blending controls

- Assign one role lens per producer phase. Cross-domain concerns become required inputs/reviews, not an excuse to claim every role.
- Name every role change in the trace with the phase boundary and unchanged task outcome.
- Require typed return packets: artifact/path, source/version manifest, decisions, recommendations, assumptions, rejected alternatives, checks/failures, diff, downstream dependencies, recipient and acceptance.
- Prevent the producer from being the sole approver of its own source interpretation, sacred-event behavior, schema, validation baseline, security claim, or release.
- Preserve disagreement and uncertainty across handoffs; summaries cannot convert proposals into approved facts.
- A verifier can request corrections but should return the artifact to its producer rather than rewrite it unless the task explicitly transfers authorship.

## 8. Policy-invariant preservation

### 8.1 Invariants and their real enforcement layers

| Invariant | Canonical authority | Workflow responsibility | Deterministic/runtime responsibility when available | Human gate |
|---|---|---|---|---|
| Player is a witness, not savior/author/rewriter | Core vision and Master Protocol | Carry into every relevant artifact contract | Quest/action/state invariants and scenario tests | Creative Director, gameplay and theology review |
| Sacred outcomes and figures are protected | Master Protocol §§7 and 14 | Identify applicable event, fixed outcomes, allowed/prohibited verbs | Central effect policy, state/save invariants, adversarial tests | Creative Director plus theology/stewardship review |
| Scripture, interpretation, reconstruction, tradition and invention remain distinct | Biblical commitments and Master Protocol | Require source/category/confidence/locator | Schema enums, reference validation, presentation checks | Qualified source/domain review |
| Historical uncertainty is visible | Master Protocol and approved confidence policy | Preserve competing views and game-translation rationale | Required fields, alternative/composite label checks | History/culture reviewer and Creative Director |
| Era knowledge and player-codex knowledge remain separated | Master Protocol §8 | Declare audience/era/source | Typed storage/delivery boundaries and leakage tests | Scripture/chronology review |
| Schema-first structured production | Master Protocol §10 and approved schemas | Stop on absent/unapproved schema | Schema validation, stable IDs, migration/reference checks | Schema owner and Creative Director for semantics |
| Provenance and rights remain intact | Authority and artifact manifests | Record origin/version/license/adaptation | Hash, allowlist, missing-license quarantine | Rights/provenance owner |
| Validation is truthful | Task acceptance and Session 12/13 architecture | List checks run, failures and unavailable layers | Test/runtime/visual evidence and protected baselines | QA and relevant domain owner |
| File/Git scope and continuity are preserved | Task contract, manifest and current head | One writer, allowlisted paths, handoff | Base/head/diff/path and CI checks | Integrator/repository owner |

No composition can trade one critical invariant against aggregate quality. A fast, concise, well-tested implementation that violates one sacred outcome, source category, knowledge boundary, schema contract, license, or required validation gate fails.

### 8.2 Simplification preservation rule

Before a simplification component can run, the orchestrator must have:

1. a complete and verified implementation baseline;
2. explicit behavior, API, side-effect/order, error/log, test, schema/save/serialization/editor/asset, security/accessibility, source/provenance, chronology/knowledge and sacred invariants as applicable;
3. exact target and rollback point;
4. unchanged predeclared tests/fixtures unless a separate change is approved;
5. all required verification capabilities; and
6. named reviewers for material domains.

The order is fixed: `authority/scope preflight → implementation → baseline verification → simplification proposal → approval where needed → smallest transformation → full preservation verification → diff/human review`. If an invariant becomes less explicit, a required check is unavailable, or a hidden consumer appears, roll back the simplification candidate. “No safe simplification identified” is an acceptable outcome.

### 8.3 Communication isolation rule

The optional communication modifier runs as a render step over assistant-authored task-facing messages only. It receives the completed semantic message and may remove repetition or choose compact headings. It cannot modify:

- source-backed research, code, schemas, specs, design artifacts, logs, tests, captures, handoffs, or composition traces;
- authority conflicts, uncertainty, approvals, destructive/external actions, security/privacy/license risk, missing capabilities, failed/not-run checks, concurrent changes, incomplete work, scope expansion, or protected-project concerns;
- required progress cadence, user-requested teaching/detail, or output structure; or
- reasoning effort, tool selection, file scope, verification depth, or completion criteria.

When these categories appear, the modifier suspends for the affected message. This implements “compress expression, not reasoning” as a best-effort presentation contract, never as a guarantee of invisible internal invariance ([Session 8](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/08_Communication_Modifier_Skill_Analysis.md)).

## 9. Example composition traces

The following names come from the research prompt. They are hypothetical component labels used to test the model; they do not create or approve skills.

### 9.1 Trace summary matrix

| Pattern | Ordered phases | Dominant authority/invariant | Required dependencies | Conflict/stop condition | Human acceptance |
|---|---|---|---|---|---|
| `lean-comms + gameplay-engineer` | Authority/task contract → gameplay production/verification → compose full result → lean presentation | Artifact quality, gameplay purpose and all never-suppress categories outrank style | Approved gameplay intent; producer inputs; checks; explicit modifier if adopted | Modifier requests less detail in artifact, warning, failure, uncertainty or evidence | Creative Director accepts mechanic; modifier needs no authority over artifact |
| `scope-guard + gameplay-engineer` | Authority/scope preflight → addition ledger → gameplay design/implementation → validation → scope audit | Smallest **complete compliant** outcome; witness/sacred/schema rules are inside minimum | Acceptance criteria, approved specs/schemas/stack if implementation | Guard blocks a required invariant or engineer adds speculative systems/files/dependencies | Creative Director approves material scope/architecture expansion |
| `scripture-integrity + quest-designer` | Source/canon/era packet → fixed/allowed/prohibited event contract → quest alternatives → source/theology review → gameplay review | Scripture/category/knowledge boundary and fixed sacred outcomes | Current source texts/rights, canon decision, chronology, event rules | Disputed interpretation treated as fact; quest replaces biblical figure or alters event | Scripture/theology reviewer; Creative Director approves treatment |
| `historical-confidence + region-designer` | Evidence/alternatives/confidence → reconstruction options → region artifact → label/codex/visual review | Honest uncertainty; no Westernized/fantasy certainty | Region/era sources, competing views, material-culture provenance | Designer collapses disputed location or composite into “authentic” fact | History/culture reviewer and Creative Director |
| `schema-first + content-engineer` | Verify approved schema/version → map sources/IDs → generate bounded content → structural/semantic validation → data review | Approved schema, stable references, source/confidence and in-world/codex separation | Approved schema and design meaning; validators; migration policy if relevant | Schema missing/proposed, fields invented, validator changed to accept output | Schema owner; Creative Director for semantic change |
| `sacred-event-protection + systems-engineer` | Event authority/effect matrix → approved spec/schema → implementation → adversarial runtime/save tests → stewardship audit | Fixed outcomes, protected figures, allowed witness agency; fail closed on unknown effects | Approved engine/stack, event model, runtime/test harness and human event decision | Any direct/area/physics/AI/save/debug bypass; engine or schema unknown | Technical owner, QA, theology/stewardship and Creative Director |
| `gameplay-verification + code-simplification` | Green baseline → preservation case → proposed simplification → approval → transform → complete verification ladder → diff review | Behavior and all protected/source/schema/save invariants preserved | Existing passing tests plus runtime/visual/save evidence as applicable; rollback | Red baseline, unavailable required layer, test weakening, hidden reference, behavior drift | Code/data/domain owners proportional to change |
| `qa-auditor + any artifact-producing skill` | Predeclare acceptance → producer creates artifact → independent audit → same producer repairs → re-audit → integrator accepts | Auditor cannot redefine criteria or become silent coauthor | Exact artifact/source/diff, acceptance, negative cases, current authority | Producer and auditor disagree; criteria change after result; critical failure | Accountable artifact/domain owner accepts residual risk |

### 9.2 Detailed traces

#### A. `lean-comms + gameplay-engineer`

```text
task: design or implement one authorized gameplay outcome
selection: gameplay producer required; lean-comms user-explicit/optional
order: authority -> producer -> checks -> complete artifact/evidence -> presentation modifier
ownership: gameplay producer owns mechanic artifact; modifier owns only chat rendering
conflict rule: any requested artifact depth, warning, failure, scope decision or evidence defeats concision
evidence: artifact diff/spec, gameplay-purpose link, checks, unresolved risks, modifier activation
```

The modifier must not make the mechanic smaller, skip alternatives, reduce testing, or hide a scope or biblical concern. If brevity is the only desired behavior, a current user instruction may be more economical than a skill.

#### B. `scope-guard + gameplay-engineer`

```text
task: implement the smallest complete authorized slice
order: authority/acceptance -> applicable invariants -> addition ledger -> producer -> verification -> scope audit
scope classes: required-now | enabling-now | approved-foundation | deferred-option | conflicting-expansion
guard prohibition: cannot remove sacred/source/schema/verification work as “extra”
producer prohibition: cannot introduce speculative multiplayer, engine, services, abstractions or files
stop: scope and project authority cannot both be satisfied; material expansion requires user approval
```

Session 9's flexible-minimalism rule controls: fewest lines/files is not the goal; complete, reviewable, reversible, verified, invariant-preserving work is ([Session 9](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/09_Scope_Guard_Skill_Analysis.md)).

#### C. `scripture-integrity + quest-designer`

```text
task: create a quest near or informed by Scripture
order: source packet -> canon/category/era status -> protected-event contract -> quest options -> domain review -> design approval
research output: passage locators, interpretation/reconstruction distinctions, disputed views, knowledge timing
designer output: ordinary-person agency, fixed biblical outcome, moral/household consequence, codex links
stop: missing authoritative sources/canon decision; sacred outcome altered; later knowledge leaks in-world
```

The research component recommends implications but does not author the quest; the quest designer does not adjudicate theology. A qualified reviewer and Creative Director resolve material interpretive or sacred-treatment choices.

#### D. `historical-confidence + region-designer`

```text
task: translate regional evidence into a playable design
order: evidence classes/alternatives -> confidence dimensions -> reconstruction choices -> region design -> label/visual/codex review
research output: sources, dates, candidate views, confidence rationale, material-culture constraints
designer output: explicit factual, composite, stylized and invented elements
stop: disputed geography stated as settled; Westernized/fantasy default; missing rights/provenance
```

The region designer may recommend a composite for playability but cannot change the underlying evidence rating. Player-facing presentation must disclose composite/stylized decisions where material.

#### E. `schema-first + content-engineer`

```text
task: produce structured content
order: schema approval/version check -> design/source input check -> bounded generation -> validator -> semantic/domain review
content writer owns: values within approved fields and sources
content writer cannot: invent fields, approve schema, erase source/confidence, merge NPC/codex knowledge
stop: absent/unapproved schema, broken ID/reference, validator unavailable, semantic owner missing
```

If no approved schema exists, the valid route is a separately authorized schema-design task—not a “minimal temporary JSON” that becomes de facto authority.

#### F. `sacred-event-protection + systems-engineer`

```text
task: implement behavior near a protected event
order: human-approved event/effect contract -> approved schema/spec/stack -> implementation -> negative effect matrix -> runtime/save tests -> stewardship gate
effect paths: direct, area, physics, AI/companion, environment, inventory, dialogue, debug, load/migration
engineer owns: implementation inside the contract
engineer cannot: decide sacred outcome, allowed portrayal, theology or unapproved engine/schema
stop/rollback: any prohibited path succeeds or required runtime/save layer is unavailable
```

A prose guard is not the protection. Capability-level code, state/save invariants, adversarial tests, and human stewardship carry different parts of the assurance case.

#### G. `gameplay-verification + code-simplification`

```text
task: simplify a verified implementation without behavior change
order: current-head/baseline -> verification evidence -> preservation ledger -> proposal -> approval -> one transformation -> full re-verification -> diff/human review
verifier supplies: unchanged acceptance, reproduction/runtime/visual/save evidence, failures
simplifier supplies: smell evidence, exact transformation, rollback, clarity argument
stop: baseline red; required layer missing; tests/fixtures weakened; hidden consumer; semantic or protected control removed
```

Verification precedes and follows simplification. The simplifier cannot invoke the verifier merely to generate a favorable result, and the verifier cannot update baselines to bless the change.

#### H. `qa-auditor + any artifact-producing skill`

```text
task: produce and independently audit one artifact
order: predeclare rubric/negative cases -> producer -> frozen artifact/evidence -> auditor -> producer repair -> auditor recheck -> integrator acceptance
auditor owns: findings, severity, reproduction, traceability and go/no-go recommendation
auditor cannot: redefine requirements, silently edit artifact, accept reserved risk, erase dissent
producer cannot: self-close critical finding or change test/baseline without approval
```

The auditor should be organizationally or contextually independent for high-risk work, but still receive the exact acceptance criteria and authority. Independence without context produces irrelevant review; shared optimism without independence produces theater.

## 10. Failure cases and safeguards

| Failure case | Likely mechanism | Preventive safeguard | Detection/recovery |
|---|---|---|---|
| Low-authority skill overrides Master Protocol | Strong prose/persona or stale copied policy | Authority preflight; canonical references; no policy duplication | Conflict trace; stop before effect; apply higher authority and re-audit |
| Several skills silently blend roles | Broad descriptions and no phase owner | One producer/phase, O/R/P/A, visible selection and handoff | Trace role changes; reject artifact without accountable owner |
| Router loops or keeps adding specialists | Textual skill-to-skill requests and no graph owner | Top-level integrator only; acyclic graph; soft component cap | Reject cycle; preserve state; human reframes oversized task |
| Explicit-only workflow is smuggled in | Dependency text treated as invocation | `requires_user_invocation`; router cannot activate | Stop and ask user; no claim that component ran |
| Communication modifier lowers quality | Brevity becomes “do less” | Presentation-last isolation and never-suppress list | Artifact/evidence equivalence test; suspend modifier; disclose omission |
| Scope guard blocks required protection | Literal minimalism outranks invariant | Flexible minimalism and authority-first order | Expand to smallest compliant result or stop for authority decision |
| Producer overbuilds through optional dependencies | “Best practice” or future architecture language | Addition ledger and current-consumer evidence | Diff-to-acceptance audit; remove unaccepted files/dependencies |
| Simplifier removes theological/provenance safeguard | Lines/indirection optimized without preservation case | Explicit protected invariant ledger and green entry gate | Roll back candidate; regression fixture; domain review |
| QA changes criteria to accept output | Producer pressure or shared author/reviewer | Predeclared rubric, frozen baselines and separation of duties | Test/baseline diff; reject result; restore and rerun clean |
| Missing tool is reported as passed | Capability assumed from skill text | Required/optional preflight and truthful claim vocabulary | Mark not validated; undo partial effect; resume after capability exists |
| Same artifact has two writers | Parallel producer composition | Exclusive allowed path and author per phase | Detect overlapping writes; stop, preserve both drafts, integrate deliberately |
| Stale package or source changes semantics | Mutable link/version drift | Exact SHA/path/date/license and compatibility tests | Quarantine, compare changes, rerun evaluations and downstream audit |
| Untrusted skill/reference injects commands | External content resembles authority | Treat external text as data; script/package inspection; least privilege | Halt network/effects, inspect logs/diff, quarantine and rotate exposed secrets if needed |
| Handoff turns recommendation into approval | Summary loses status/owner | Canonical decision IDs and recipient preflight | Compare handoff to source; correct before continuation |
| Component context overload hides exception | Too many/long bodies and duplicate rules | Soft cap, progressive disclosure, direct routing and ablation | Context/coverage audit; remove redundant component and retest |
| Human rubber-stamps machine trace | Form exists without substantive review | Criterion-specific evidence and named qualified reviewer | Retain observations/dissent; withhold acceptance until real gate occurs |

### 10.1 Fail-safe stopping packet

Every blocked composition should return:

- task and current phase;
- repository base/head and dirty-state implications;
- exact missing/conflicting authority, dependency, capability, permission or approval;
- actions completed and evidence preserved;
- actions not performed and claims withheld;
- affected files/artifacts and rollback/current state;
- safe bounded alternatives, if any;
- accountable decision owner and smallest next action; and
- whether re-routing would change scope, risk, cost, or assurance.

It must not continue with a plausible imitation, substitute a guessed engine/schema/source, suppress the issue for concision, or mark an unavailable check passed.

### 10.2 Version and update governance

For every future composed component:

1. record origin, package path, exact commit/version, files inspected, license, adaptations, supported surface/tools and last-reviewed date;
2. keep a compatibility record with current Master Protocol, schemas/specs, engine/tool versions, permissions, artifacts and companion workflows;
3. maintain trigger, near-miss, authority-conflict, missing-capability, unsafe-input, output, and integration fixtures;
4. reevaluate on authority, schema, engine/API, dependency, permission, model/surface, tool, rights, or production-incident change;
5. quarantine stale or incompatible components rather than silently patching them during an unrelated task;
6. compare updated composition against the prior pinned version and a no-skill/current-workflow baseline; and
7. require human approval for changes that alter ownership, invocation mode, permissions, protected invariants, output contracts or acceptance thresholds.

## 11. Generic composition model for the future skill-builder

The future builder should emit a **composition contract** only when a candidate skill genuinely needs companions. It must not create or populate a final project catalog.

### 11.1 Eight-layer model

1. **Authority layers** — live system/developer/user/project authority and revisions; conflict/override policy.
2. **Policy invariants** — applicable witness, source, sacred, chronology, historical, schema, provenance, safety and continuity requirements, each linked to a canonical owner.
3. **Role lens** — one producer's O/R/P/A boundary, inputs, output and handoff.
4. **Workflow sequence** — explicit acyclic phases, entry/exit gates, stops, rollback and author per artifact.
5. **Tool-operation layer** — tools, versions, permissions, scripts, inputs/outputs, side effects, data exposure and unavailable behavior.
6. **Artifact contract** — exact path/type/schema, required sections/fields, evidence, non-goals and status vocabulary.
7. **Verification/audit layer** — predeclared checks, negative cases, independent reviewer, pass/fail/blocked meanings and residual-risk owner.
8. **Optional communication modifier** — presentation-only, explicit boundary, suspension and never-suppress contract.

### 11.2 Builder requirements

For any requested composed skill/workflow, the builder should:

1. decide first whether composition is necessary or an ordinary instruction/tool/persistent policy is better;
2. load current authority and reject attempts to make a conditional skill the sole owner of permanent project policy;
3. define one coherent job and one producer artifact, not a profession-sized persona;
4. generate O/R/P/A fields and a typed handoff;
5. declare each dependency by class, cardinality, version, availability check, fallback, failure behavior and human owner;
6. distinguish Codex-documented metadata from project-only composition records;
7. preserve explicit-only invocation boundaries and forbid skill-to-skill activation claims;
8. generate an explicit acyclic phase graph with exclusive writes and a conservative depth check;
9. detect authority, semantic, scope, order, ownership, capability, invocation, validation, communication, version, security and recursion conflicts;
10. cite canonical project invariants instead of copying them into a stale parallel policy;
11. add capability-unavailable, conflict, role-blend, cycle, stale-version, missing-input, and prohibited-behavior fixtures;
12. isolate optional communication behavior from artifacts, evidence and validation;
13. require a green baseline and preservation ledger before any simplification phase;
14. require independent review and predeclared criteria for high-risk artifacts;
15. generate the minimum composition trace fields in §11.3 without requesting hidden chain-of-thought;
16. provide safe stop/rollback and reduced-assurance language;
17. compare composed, single-skill/ordinary-prompt, and no-skill baselines on correctness, critical failures, context/tokens, latency, duplicate work, integration defects and human review time;
18. record provenance, license, package/source SHAs, tested surface/version and maintenance triggers;
19. refuse stack-specific composition while engine, language, schemas, tools or build/test infrastructure remain unapproved; and
20. label the result a candidate pending Session 15 evaluation and Creative Director approval, not a catalog entry.

### 11.3 Minimum composition trace

| Trace group | Required fields |
|---|---|
| Identity | `task_id`, objective, risk class, requested outcome, trace format/version, timestamp |
| Repository | repository URL/root, base SHA, current head, branch/worktree state, concurrent changes |
| Authority | system/developer constraints by identifier where exposable, user instruction, project authority files/SHAs, decision/schema/spec IDs/status |
| Routing | router/integrator identity/version, ordinary-instruction alternatives considered, route selected, rejected routes and reasons |
| Components | stable ID, artifact type, path/origin, revision/SHA, selection mode, phase, O/R/P/A, explicit-only state |
| Graph | ordered nodes/edges, entry/exit criteria, write owner, retry count, cycle/depth result |
| Dependencies | kind, required/optional, version/range, availability result, fallback, failure disposition |
| Capabilities | tools/scripts/services/versions, permissions, network/credentials/data exposure, approvals, unavailable capabilities |
| Context | exact references and project files actually loaded, source dates/SHAs, provenance/license state |
| Scope and artifacts | allowed/prohibited paths, files read/written, output contract, exact diff/hash, generated artifacts |
| Conflicts | class/severity, both sources/clauses, authority levels, affected phase, owner, disposition, rationale, revalidation |
| Verification | checks/scenarios, commands or procedures, tool/environment, expected/actual, pass/fail/not-run/blocked, evidence locators |
| Human gates | reviewer role/identity, criterion, evidence inspected, decision, dissent, residual risk, timestamp |
| Completion | delivered artifact/commit/evidence IDs, unresolved questions, exceptions/expiry, rollback, next owner |

The trace is an operational provenance record. It should capture inputs, decisions, actions and evidence, but never demand private chain-of-thought. Compactness is acceptable when fields retain stable IDs and durable links.

### 11.4 Composition contract acceptance test

A candidate passes composition design review only if:

- every component has a distinct current job and no lower-authority override;
- order is explicit and acyclic;
- required dependencies and unavailable behavior are testable;
- user-invoked-only workflows remain unreachable automatically;
- one writer owns each artifact in each phase;
- permanent invariants survive non-invocation of any optional skill;
- simplification cannot precede a green baseline or weaken protections;
- communication cannot alter artifact/evidence quality;
- conflicts stop before unsafe or unauthorized effects;
- the trace supports independent reconstruction of what ran and what did not;
- high-risk acceptance remains human-owned; and
- the composed workflow demonstrates value over the simpler baseline without any critical regression.

## 12. Findings, recommendations, unverified questions, and source appendix

### 12.1 Findings

- Current Codex documentation supports reusable skills, explicit/model-selected invocation, progressive disclosure, resources/scripts, and tool dependency metadata, but does not publish deterministic multi-skill ordering, merge, precedence, companion resolution, or privileged skill-to-skill invocation.
- The repository's Master Protocol already provides a project authority chain, roles and non-negotiable creative/source constraints. A lower conditional workflow must not become a competing authority.
- The project's most important controls require several enforcement layers. Skill composition can guide the work but cannot substitute for approved schemas, validators, runtime restrictions, tests, permissions, evidence and accountable human review.
- Communication shaping and post-implementation simplification create distinct cross-cutting risks and therefore belong at explicit late phases with preservation gates.
- A composition trace can make workflow influence and evidence visible without capturing hidden reasoning.

### 12.2 Recommendations

- Adopt explicit manager-owned serial phase plans rather than relying on simultaneous skill co-activation.
- Use the authority ladder, dependency declaration, conflict matrix, O/R/P/A contract and trace schema in this report as Session 16 builder-requirement inputs, pending evaluation.
- Keep explicit-only components unreachable from routers and other skills.
- Apply a four-substantive-component soft cap per plan and evaluate it rather than treating it as a universal optimum.
- Preserve permanent policy outside conditional skills, one writer per artifact, predeclared verification, independent high-risk review and fail-safe stopping.
- Do not implement a router or choose a final project skill set until benchmark evidence and the Creative Director's later decisions justify it.

### 12.3 Unverified and deferred

The following remain unverified or user-owned:

1. Native precedence or load order among several active Codex skills.
2. Whether explicit invocation outranks an incompatible model-selected skill at every supported surface/version.
3. A native required/optional companion-skill schema, conflict declaration, version resolver or skill-to-skill invocation API.
4. Guaranteed skill lifetime through turns, compaction, resume and handoff.
5. The optimal maximum component depth; the proposed soft cap requires Session 15 evaluation.
6. Which candidate workflows, if any, should be actual project skills rather than prompts, policy, tools, validators, agent configurations or human procedures.
7. The eventual router/orchestrator implementation form.
8. Engine, language, runtime/editor, build/test tools, schemas, save policy, release pipeline and stack-specific compositions.
9. Named qualified human owners and exact approval thresholds for theology, history, culture, visuals, accessibility, rights, security, data and release.
10. Final invocation policy, versioning cadence, compatibility ranges and numeric evaluation thresholds for any future component.

### 12.4 Source appendix

All project sources were inspected at predecessor commit [`09ec38b2a6379fc859e628b225088cb26b1451e3`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/09ec38b2a6379fc859e628b225088cb26b1451e3), accessed 2026-07-22.

#### Project authority and predecessor reports

- [The Bible Video Game Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md)
- [Session 1 — Project Context and Authority Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md)
- [Session 2 — Terminology and Artifact Taxonomy](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md)
- [Session 3 — Current Codex Skill Capability Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md)
- [Session 4 — Effective Skill Anatomy and Authoring Principles](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md)
- [Session 6 — Skill Failure, Security, and Maintenance Risks](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md)
- [Session 7 — Role-Based Skill Architecture](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/07_Role_Based_Skill_Architecture.md)
- [Session 8 — Communication-Modifier Skill Analysis](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/08_Communication_Modifier_Skill_Analysis.md)
- [Session 9 — Scope-Guard and Minimal-Implementation Skill Analysis](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/09_Scope_Guard_Skill_Analysis.md)
- [Session 10 — Post-Implementation Simplification Skill Analysis](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/10_Post_Implementation_Simplification_Skill_Analysis.md)
- [Session 13 — Project Constraint Enforcement Architecture](https://github.com/Degrading1919/The_Bible_Video_Game/blob/09ec38b2a6379fc859e628b225088cb26b1451e3/00_ADMIN/Research/LLM_Skills/13_Project_Constraint_Enforcement_Architecture.md)

#### Current official and open specifications

- OpenAI, [Build skills](https://learn.chatgpt.com/docs/build-skills), living documentation, checked 2026-07-22. Supports the skill package, discovery/invocation, metadata, resources/scripts and capability boundary claims; it does not establish the proposed governance order.
- OpenAI, [Custom instructions with `AGENTS.md`](https://learn.chatgpt.com/docs/agent-configuration/agents-md), living documentation, checked 2026-07-22. Supports the distinction between persistent repository instructions and conditional skills.
- OpenAI, [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security), living documentation, checked 2026-07-22. Supports the separation of sandbox/capability and approval policy from skill prose.
- Agent Skills, [Specification](https://agentskills.io/specification), living open specification, checked 2026-07-22. Supports package anatomy, compatibility/dependency documentation, scripts/references and progressive disclosure; it does not define this project's composition graph.
- OpenAI, [`openai/skills` README at commit `49f948faa9258a0c61caceaf225e179651397431`](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/README.md), accessed 2026-07-22. Pinned historical distribution/maintenance context; individual package licenses remain authoritative.

### Bounded conclusion

Reliable composition for this project should be treated as an explicit, inspectable, authority-first workflow graph—not as a presumed property of simultaneously active skill text. One integrator selects the smallest necessary components, one producer owns each artifact phase, higher project invariants remain outside conditional skills, required capabilities and human gates are verified, conflicts stop before effects, and every accepted result carries a compact composition/evidence trace. That model is suitable for evaluation and future builder requirements; it is not yet a router implementation or a final skill catalog.

# Role-Based Skill Architecture

**Session:** 07 of 18
**Research cutoff:** 2026-07-22
**Repository:** [Degrading1919/The_Bible_Video_Game](https://github.com/Degrading1919/The_Bible_Video_Game)
**Predecessor commit:** [`cee8ea546d7cc3f0df9eabb4083326a25e7e49d2`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2)
**Scope:** Evidence-based criteria for representing project roles as governance, skills, agent configurations, subagents, workflows, prompts, or ordinary instructions. The candidate mappings below are deliberately provisional. They are **not** an approved role list or skill catalog.

## Status and evidence conventions

- **Project requirement** means a rule established by the current Master Assistant Protocol or a current user instruction.
- **Finding** means a claim supported by the cited source.
- **Inference** means a reasoned consequence of findings, not a directly documented guarantee.
- **Recommendation** means a proposed architectural practice for later review.
- **Unverified** means the available primary evidence does not establish the claim.

Evidence strength follows Session 5: **Strong** for controlled or reproducible evidence with a meaningful baseline; **Moderate** for inspectable primary artifacts or repeated real use that does not isolate causality; **Weak** for limited or uncontrolled evidence; **Promotional** for an inadequately substantiated benefit claim; and **Speculative** for an untested proposal.

## 1. Executive conclusion

A professional title is not an implementation primitive. A useful project role is an accountable boundary around decisions, evidence, outputs, review, and escalation. It becomes a Codex skill only when a stable portion of that role can be expressed as a recurring, bounded, testable workflow. It becomes an agent configuration only when the work benefits from a materially different instruction set, tool set, model, sandbox, or isolated context. A subagent is an instance used for bounded delegation, not a permanent role definition. A prompt is appropriate for a one-off lens or creative brief. An ordinary task instruction is sufficient when the behavior is local, simple, and unlikely to recur. Deterministic checks belong in schemas, scripts, tests, CI, permissions, or runtime invariants rather than being simulated by role prose.

The current nine assistant modes are valid project governance, but the repository contains no evidence that all nine should become nine skills or nine agents. The six additional roles named by this research assignment are plausible future responsibilities, not current authorities. The engine, codebase, build system, performance targets, accessibility baseline, release pipeline, and runtime security model remain unknown at the predecessor commit ([Session 1](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md)). Creating implementation specialists around invented stack assumptions would convert uncertainty into false authority.

The strongest evidence does not support role proliferation. SkillsBench found that curated skills improved aggregate performance while 16 of 84 tasks regressed, and SWE-Skills-Bench found no pass-rate gain for most examined software-engineering skills ([Session 5](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Research/LLM_Skills/05_Demonstrated_Skill_Success_Evidence.md)). A large failure analysis of five multi-agent frameworks identified specification/design, inter-agent misalignment, and verification/termination failures and found that clearer role descriptions alone did not solve them ([Cemri et al., 2025](https://arxiv.org/abs/2503.13657)). Role-based software-company systems such as ChatDev and MetaGPT demonstrate technical feasibility, but combine roles, prompts, sequencing, tools, feedback, and intermediate artifacts; they do not isolate the effect of a job title ([ChatDev paper](https://arxiv.org/abs/2307.07924); [MetaGPT paper](https://arxiv.org/abs/2308.00352)).

For this project, the safest initial architecture is therefore:

1. keep universal identity, authority, and prohibited behavior in the Master Protocol and any later approved repository-instruction layer;
2. create skills only for recurring procedures with measurable outputs and negative cases;
3. use agent configurations or subagents only when isolation, different capabilities, or independent review provides a testable benefit;
4. require structured handoffs rather than passing an unqualified summary;
5. preserve the user as Creative Director and retain human gates for theology, canon, disputed history, sacred figures/events, major creative direction, schema approval, security, accessibility, and release; and
6. split or merge roles using observed workload and evaluation evidence, not organizational theater.

## 2. Evidence review of role specialization

### 2.1 What current platforms actually support

**Finding — official current documentation:** Codex skills are reusable task packages selected explicitly or by description match. They contain a required `SKILL.md` and may include references, scripts, and assets. Their documented repository root is `.agents/skills`; they do not grant permissions, and current public documentation does not define deterministic precedence among conflicting active skills ([OpenAI, Build skills](https://learn.chatgpt.com/docs/build-skills); [Session 3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md)). This makes a skill a good carrier for a focused procedure, but a poor sole carrier for universal project policy.

**Finding — official current documentation:** Codex subagents are delegated workers with separate contexts. Custom agent definitions can provide distinct instructions, tools, models, MCP servers, and sandbox settings ([OpenAI, Subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents)). GitHub's custom-agent profiles similarly combine a prompt with selected tools and MCP servers, and its subagent orchestration can delegate into an isolated context ([GitHub, About custom agents](https://docs.github.com/en/copilot/concepts/agents/cloud-agent/about-custom-agents); [GitHub, custom agents and sub-agent orchestration](https://docs.github.com/en/copilot/how-tos/copilot-sdk/features/custom-agents)). These capabilities justify an agent configuration when capability or context boundaries differ materially; they do not prove that every named specialty benefits from isolation.

**Finding — official orchestration guidance:** The OpenAI Agents SDK distinguishes a manager pattern, in which the central agent invokes specialists as tools and retains ownership of the final answer, from handoffs, in which the specialist takes over the interaction ([Agent orchestration](https://openai.github.io/openai-agents-python/multi_agent/); [Handoffs](https://openai.github.io/openai-agents-python/handoffs/)). This is not a Codex skill-composition guarantee, but it supplies a useful architectural distinction: use manager-owned delegation when cross-domain integration is the main risk; transfer control only when a specialist genuinely owns the next phase and the transfer contract is explicit.

### 2.2 What software-development research demonstrates

**Finding — Moderate:** ChatDev assigns roles within sequenced design, coding, testing, and documentation phases and constrains what and how agents communicate. MetaGPT uses role-specific responsibilities, standard operating procedures, and intermediate artifacts. Both are inspectable role-based software-development systems, and ChatDev's current repository advertises a game-development workflow as one configured use case ([ChatDev repository at `4fd4da6…`](https://github.com/OpenBMB/ChatDev/blob/4fd4da603801766b14ad8788649cfc1ad21f99a6/README.md); [ChatDev paper](https://arxiv.org/abs/2307.07924); [MetaGPT paper](https://arxiv.org/abs/2308.00352)). Their results support the feasibility of roles joined to process and artifacts. They do **not** isolate whether gains came from role names, decomposition, repeated critique, tools, more tokens, or output contracts.

**Finding — Strong for failure taxonomy:** The MAST study inspected more than 150 tasks across five multi-agent frameworks and derived 14 failure modes spanning system specification, inter-agent misalignment, and verification/termination. Its role-specification and orchestration interventions did not make the identified failures easy to eliminate ([Cemri et al., 2025](https://arxiv.org/abs/2503.13657)). A role architecture therefore needs verification and recovery, not merely clearer personas.

**Finding — Moderate, recent preprint:** A broad single-agent versus multi-agent comparison reported that multi-agent advantages diminish as underlying models improve and that hybrid request routing can reduce cost while retaining capability ([Gao et al., 2025](https://arxiv.org/abs/2505.18286)). This evidence does not settle project-specific routing, but it argues against making a multi-agent team the default for every task.

**Finding — Weak, game-specific case:** A 2026 case study of Designer/Programmer conversations on a Fibonacci game found that some model pairs maintained role alignment while still diverging from the correct solution, while others failed to converge ([Basu et al., 2026](https://openreview.net/pdf?id=cqPjCCf9tW)). This is a narrow case rather than a general benchmark, but it directly illustrates that apparent role adherence and task correctness are different properties.

**Finding — Strong, adjacent workflow evidence:** SWE-agent's controlled agent-computer-interface ablation improved issue-resolution results, but its intervention combined reusable instructions, constrained tools, feedback, examples, and context management ([NeurIPS 2024 paper](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf)). The transferable lesson is to join specialization to executable feedback and clear outputs, not to infer that professional role-play alone caused the gain.

### 2.3 Evidence synthesis

| Claim | Status | Strength | Architectural consequence |
|---|---|---:|---|
| A stable professional lens can be encoded in reusable instructions. | Finding | Moderate | Reusability is feasible, but artifact type must follow scope and capability needs. |
| A named role by itself improves accuracy. | Unverified | None | Never approve a role or skill from title, tone, or apparent confidence. |
| Structured roles plus procedures, tools, and intermediate artifacts can improve some software workflows. | Finding | Moderate to Strong for combined interventions | Define inputs, artifacts, checks, and integration—not only identity. |
| More roles or agents are generally better. | Contradicted as a universal rule | Strong negative evidence | Default to the smallest team that covers real separations of ownership or capability. |
| Isolated contexts can protect focus. | Finding for capability; project benefit unverified | Moderate | Use only when a bounded packet can preserve necessary authority and dependencies. |
| Specialization can cause handoff loss, drift, and duplicated work. | Finding | Strong | Make handoff fields and a shared integration owner mandatory. |
| Role adherence proves correctness. | Contradicted by case evidence | Weak but direct | Score role compliance and artifact correctness separately. |
| Independent review can catch producer errors. | Inference from verification evidence | Moderate | Keep auditor outputs separate and require evidence; do not let the reviewer silently redesign. |

## 3. Role-artifact decision model

### 3.1 First classify the behavior, then choose the artifact

Apply these questions in order:

1. **Is the behavior universally binding?** Project identity, chain of authority, player-as-witness, protected sacred events, source-category separation, era knowledge, schema-first production, and the user's final authority must remain in the Master Protocol and any later approved persistent repository guidance. A conditional skill may cite and operationalize them, but cannot be their only home.
2. **Can the rule be mechanically enforced?** File shape belongs in schemas; source fields in validators; protected actions in runtime invariants and tests; build requirements in CI; dangerous operations in sandbox/approval policy. Do not choose prose where deterministic enforcement is available.
3. **Is there a recurring bounded procedure?** If the same inputs, decisions, steps, stops, outputs, and checks recur, a workflow skill is a candidate. Repetition without a stable contract is not enough.
4. **Does the worker need a different capability or isolation boundary?** A distinct tool set, model, MCP server, sandbox, permission profile, or intentionally separate context can justify an agent configuration. A different writing voice cannot.
5. **Is the work a bounded delegation inside one task?** Instantiate a subagent with an explicit work order and return contract. Do not mistake the instance for the durable role definition.
6. **Is the lens temporary or exploratory?** Use a separate prompt for a one-time research lens, brainstorm, red-team, or decision memo. Persist it only after demonstrated recurrence.
7. **Is the instruction simple and local?** Use ordinary task text: “review these citations,” “implement this accepted schema,” or “profile this scene.” Packaging such instructions creates maintenance without a proven benefit.
8. **Is the job mixed?** Combine layers deliberately: persistent authority + focused skill + optional specialist agent + deterministic validator + human gate. Do not force the full behavior into a single artifact.

### 3.2 Qualification scorecard

A proposed reusable role artifact should be evaluated on six independent dimensions. There is no evidence-backed universal numeric threshold; the scorecard structures a decision rather than automating it.

| Dimension | Evidence that favors a durable role artifact | Evidence that favors prompt or ordinary instruction |
|---|---|---|
| Recurrence | Same responsibility appears across several real tasks and phases. | One speculative future need or one current task. |
| Decision boundary | Distinct owned/recommended/prohibited decisions can be stated and reviewed. | Only a tone, persona, or broad “expert” label. |
| Workflow stability | Inputs, steps, stops, output, and verification repeat. | The method changes with every task or depends on unresolved stack choices. |
| Capability delta | Different tools, permissions, model, or isolation are necessary. | Same context and capabilities as the main agent. |
| Integration seam | A structured artifact can cross the boundary without material loss. | The work requires constant shared reasoning with other domains. |
| Evaluability | Baseline, positive/negative cases, correctness, cost, and drift can be measured. | Success is judged only by confidence or prose quality. |

**Recommendation:** create a skill when recurrence, workflow stability, and evaluability are established. Create a separate agent only when a capability/context delta or independent-review requirement is also established. If only the professional lens is stable, keep the role in governance and invoke it through a prompt.

## 4. “Role versus costume” criteria

A role is operational only when all of the following are explicit:

1. **Purpose tied to a project outcome:** what risk or artifact the role exists to improve.
2. **Owned decisions:** choices it may make within delegated bounds.
3. **Recommendations:** choices it analyzes but does not settle.
4. **Prohibitions:** decisions and actions it must not take.
5. **Required sources:** current project authority, domain evidence, schemas/specs, and repository state it must inspect.
6. **Capability declaration:** tools, scripts, MCP services, permissions, and versions required; missing capabilities must not be fabricated.
7. **Output contract:** named artifact, structure, status labels, citations, and accepted path.
8. **Review contract:** correctness criteria, prohibited outcomes, checks, and accountable reviewer.
9. **Escalation triggers:** missing authority, contested doctrine/history, unsafe action, schema conflict, unavailable tool, failed verification, or cross-role disagreement.
10. **Handoff contract:** sources, decisions, unresolved items, evidence, validation, and next owner.
11. **Human boundary:** what requires Creative Director or specialist human approval.
12. **Evaluation:** cases demonstrating that the role improves outcomes without unacceptable cost or drift.

A costume has a title, biography, voice, or instruction to “think like an expert,” but lacks one or more of those operational properties. Warning signs include anthropomorphic backstory, prestige language, claims of expertise without sources, identical tools and outputs across supposedly different agents, no prohibited decisions, no stopping rule, and no reviewer who can reject the work.

**Project requirement:** reverent tone is important, but it is not a substitute for Scripture citations, uncertainty labels, protected-event boundaries, and human theological review. Likewise, calling an agent “Technical Director” does not authorize an engine choice, and calling one “Security Auditor” does not grant repository or credential access.

## 5. Ownership, recommendation, prohibition, and approval framework

Use four fields for every assignment:

- **Owns (O):** may decide how to produce the assigned artifact within approved sources, schemas, specifications, paths, and task scope.
- **Recommends (R):** may compare options and state a preferred choice, but cannot establish project truth or authority.
- **Prohibited (P):** must not decide or perform the action.
- **Approval (A):** the person or higher-authority role that must accept the decision or artifact.

“Ownership” never means final ownership of the project. The user/Creative Director remains final under the [Master Protocol §4](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L78-L107).

| Responsibility family | O — bounded ownership | R — may recommend | P — must not decide/perform | A — required acceptance |
|---|---|---|---|---|
| Direction and integration | Decision memo, tradeoff analysis, dependency map | Priority, sequencing, scope options | Override user, Scripture commitments, or approved authority | Creative Director |
| Scripture/theology | Source audit, category labels, contested-view map | Theologically safer design treatment | Silent doctrinal/canon ruling; rewrite sacred outcome | Creative Director plus qualified human theological review for material claims |
| History/geography/culture | Evidence dossier and confidence assessment | Composite or stylized reconstruction options | Present disputed location or reconstruction as certain | Creative Director; domain expert where material |
| World/quest/gameplay design | Design alternatives within approved constraints | Playable implementation and scope tradeoffs | Alter fixed biblical events; approve contested source claims | Creative Director; relevant research reviewers |
| Schema/content | Schema-conformant artifact and validation result | Data-shape improvements | Invent an approved schema or change design meaning silently | Schema owner and Creative Director for semantic changes |
| Runtime engineering | Implementation within approved spec/schema | Architecture alternatives | Select unapproved stack; invent content/theology | Technical approver and Creative Director for scope/stack |
| Visual research | Evidence-backed brief with confidence | Visual alternatives | Declare unknown sacred appearance as fact; final sacred-figure approval | Creative Director and appropriate human reviewer |
| Validation/audit | Findings, evidence, severity, reproduction steps | Corrections and release recommendation | Redefine acceptance criteria after seeing result; silently rewrite artifact | Artifact owner fixes; accountable human accepts residual risk |
| Build/release/security | Reproducible checks and bounded operational report | Go/no-go recommendation | Publish, expose secrets, broaden permissions, or accept risk without authority | Human release/security authority |

## 6. Specialization benefits and costs

| Effect | Potential benefit | Failure mode | Control |
|---|---|---|---|
| Accuracy | Narrow sources and checks can reduce irrelevant assumptions. | Specialist title creates false confidence or misses cross-domain constraints. | Source manifest, confidence labels, independent verification, integration review. |
| Creativity | Separate ideation can generate genuinely different options. | Roles converge on copied patterns or create mutually incompatible designs. | Ask for alternatives with tradeoffs; integrate against one accepted brief. |
| Consistency | Stable output contracts and schemas reduce format drift. | Duplicate role texts diverge from the Master Protocol. | One authority source; role artifact references rather than restates it. |
| Token use | A bounded context can omit unrelated repository material. | Multiple agents reread common files and repeat explanations; handoffs add tokens. | Route the smallest packet; measure end-to-end cost, not per-agent context alone. |
| Context focus | Isolation can protect an audit or research pass from producer anchoring. | Omitted assumptions, decisions, or dependencies cause context fragmentation. | Mandatory packet fields and explicit missing-context stop. |
| Cross-role drift | Ownership boundaries reduce silent role blending. | Each specialist optimizes its local artifact and loses project identity. | Central integration owner and composition trace. |
| Handoff quality | Structured artifacts make work inspectable. | Summary compression removes dissent, uncertainty, or failure evidence. | Pass sources, decisions, rejected options, and raw validation references—not only prose conclusions. |
| Duplicate work | Routing can send one concern to one owner. | Overlapping roles independently research or edit the same surface. | Work-order matrix, allowed paths, and a single writer per artifact. |
| Integration | Review specialists can detect contradictions. | Sequential local success yields a globally incoherent result. | Dependency-aware acceptance gate and end-to-end scenario. |

**Recommendation:** compare any multi-role arrangement against a main-agent baseline on correctness, project-constraint compliance, total token/time cost, duplicated work, handoff loss, and human review time. A role split that improves only stylistic polish should be rejected.

## 7. Handoff and integration model

### 7.1 Manager-owned default

The default for this project should be a manager-owned flow: the primary assistant holds the current authority map and accepted task outcome, delegates bounded investigations, and integrates the result. This matches the project's high cross-domain coupling: a quest may involve Scripture, disputed geography, schema fields, gameplay purpose, sacred-event restrictions, and era knowledge simultaneously.

Transfer ownership of an entire phase only when all of these are true:

- the specialist has a clear output contract and exclusive allowed paths;
- the input packet contains all controlling sources and accepted upstream decisions;
- tool and permission boundaries are appropriate;
- the specialist can stop rather than invent missing inputs;
- the result can be independently reviewed; and
- the primary assistant or accountable human retains final integration authority.

### 7.2 Required work order

Every delegated role task should receive:

1. task identifier, objective, and predecessor repository SHA;
2. governing project sources and exact specialist inputs;
3. status of each input: authoritative, approved, proposed, disputed, or unavailable;
4. owned, recommended, prohibited, and human-approved decisions;
5. allowed tools, permissions, network use, and file paths;
6. output schema or document contract;
7. required checks and evidence capture;
8. escalation and stopping conditions; and
9. named next reviewer/integrator.

### 7.3 Required return packet

The specialist returns:

- artifact and exact path;
- source manifest with versions/SHAs and confidence labels;
- decisions made inside delegated authority;
- recommendations requiring approval;
- assumptions and unresolved questions;
- rejected alternatives and why they were rejected when material;
- tools/checks actually run, results, and failures;
- diff or changed-surface list;
- known downstream dependencies; and
- explicit handoff recipient and acceptance criteria.

### 7.4 Integration gate

The integrator checks authority, dependencies, terminology, contradictory assumptions, schema compatibility, source/confidence preservation, sacred-event behavior, era knowledge, scope, and validation evidence. A failed gate returns the artifact to the same producing role with precise defects. A different role should not silently rewrite the producer's artifact unless the task explicitly transfers authorship.

## 8. Candidate-role analysis — explicitly non-authoritative

This table evaluates all role families required by the session. “Placement” means a provisional artifact pattern worth testing, not a decision to create that role, skill, or agent.

| Candidate role | Stable/recurring and dominant concern | Context and fragmentation judgment | Provisional placement to evaluate | Split/merge evidence required | Handoff, review, and human boundary | Rules that remain in Master Protocol |
|---|---|---|---|---|---|---|
| **Creative Director Support** | Recurring integration and tradeoff support; primarily authority-aware decision framing, not domain production. | Needs broad shared context; isolation would hide cross-domain tradeoffs. | Keep as governance role/manual prompt. Test a bounded decision-memo workflow skill only if memo structure recurs. No separate agent by default. | Split only if decision volume creates measurable integration delay; merge into main assistant while project is small. | Returns options, dependencies, risks, and recommendation. User alone approves direction and priority. | User final authority, witness premise, canon/scope, sacred treatment, no invention. |
| **Scripture and Theology Researcher** | Recurring, high-consequence source analysis; domain knowledge plus evidence workflow. | Benefits from focused source packet, but must share era, quest, and codex purpose. Isolation is acceptable for bounded research, not final integration. | Governance role + source-grounded research workflow skill; optional read-focused subagent when task is separable. Agent config only if verified source tools/context differ. | Split by textual/source-language research versus theological review only after sustained workload and qualified review capacity; merge on small questions. | Returns passages, source categories, interpretations, uncertainty, and design implications. Human approval for canon/doctrine/material sacred claims. | Scripture/reconstruction/invention separation, supernatural seriousness, protected events, player-as-witness. |
| **Historical Geography and Culture Researcher** | Recurring evidence synthesis and confidence labeling; domain reference plus workflow. | Focused regional packets help; must receive chronology and design target to avoid irrelevant encyclopedic research. | Role + dossier workflow skill + governed references; optional bounded subagent. | Split geography, archaeology, and material culture only if sources/outputs diverge and duplicate research falls. Merge while dossiers remain manageable. | Returns evidence tiers, competing views, confidence, map implications, and sources to verify. User/domain reviewer approves production reconstruction. | No false certainty, no Westernized/fantasy assumptions, source categories, era accuracy. |
| **World and Quest Designer** | Recurring creative synthesis; workflow and artifact production more than isolated domain authority. | Requires shared Scripture, history, gameplay, and continuity context. Full isolation risks attractive but incompatible quests. | Role/manual prompt now; later quest-design workflow skill after an approved quest schema and review gates exist. Subagents may generate bounded alternatives. | Split world, narrative, dialogue, and quest responsibilities only when approved artifact seams and workload exist. Merge for vertical-slice cohesion. | Returns options, chosen rationale, dependencies, sacred-event map, and unresolved source decisions. User approves creative direction. | Fixed biblical outcomes, bounded agency, lineage continuity, ordinary-life emphasis. |
| **Gameplay Systems Designer** | Recurring mechanic/economy/progression decisions; design workflow and acceptance criteria. | Needs close coupling to world, schema, and technical feasibility. Separate research can help, but final system must share context. | Governance role + future system-spec workflow skill; no stack-specific agent now. | Split from World/Quest when system complexity and balance artifacts become sustained; merge for early concept/vertical-slice work. | Returns purpose, loop, inputs/outputs, edge cases, balance hypotheses, and validation plan. User approves scope and player experience. | No magic/power fantasy, meaningful-resource rule, sacred-event boundaries, single-player unless reopened. |
| **Schema and Content Engineer** | Recurring machine-readable contracts and validation; workflow, tool operation, and output format. | Needs exact approved schemas and content semantics; focused context is useful if provenance is preserved. | Strong future candidate for workflow skill plus deterministic validator. Agent config only after data tools and permission boundaries exist. | Split schema design from content population when review queues and permissions differ; merge during initial schema iteration. | Returns schema/content, migration impact, validation results, source/confidence preservation. Human schema owner approves contract changes. | Schema-first requirement, no silent theology/history invention, in-world/codex separation. |
| **Systems Engineer** | Broad runtime architecture and implementation role; authority plus multiple workflows, not one coherent skill. | Needs repository-wide implementation context. A monolithic isolated specialist risks local optimization. | Keep as role; later agent config may encode selected stack/tools. Use smaller diagnose/implement/verify skills, not one “systems expert” skill. | Split only around proven runtime ownership boundaries. Merge with Gameplay Programmer while codebase/team is small. | Returns implementation, tests, architecture decision needs, failures, and diff. Human technical authority approves architecture/stack; user approves scope. | Approved schemas/specs, no invented content/theology, no MMO assumption, sacred restrictions. |
| **Character and Visual Design Researcher** | Recurring appearance/material-culture evidence and visual briefs; domain reference plus artifact workflow. | Focused visual sources benefit isolation, but sacred, geographic, and era context must travel with the packet. | Role + evidence-to-visual-brief workflow skill; optional image/tool subagent only with explicit capabilities and provenance. | Split research from asset production when tools/licenses/review differ; keep sacred-figure review independently gated. | Returns source/confidence matrix, exclusions, prompt/brief, and provenance. User/human reviewer approves sacred figures and final visual direction. | Reverence, no Westernized assumptions, historical uncertainty, symbolic versus earthly appearance. |
| **QA, Validation, and Continuity Auditor** | Stable independent review with repeatable checks; workflow and evaluation evidence. | Some independence is valuable to reduce producer anchoring; must still receive acceptance criteria and exact sources. | Role + audit workflow skill; strong candidate for read-only subagent/agent profile once test tools exist. | Split continuity, gameplay, data, and technical QA only when distinct harnesses/queues exist; preserve one integration report. | Returns findings by severity, evidence, reproduction, and correction owner. Does not silently redesign. Human accepts residual risk. | All project guardrails and authority; auditor cannot redefine them. |
| **Technical Director** | Potential recurring integration of architecture, stack, budgets, and production risk, but not currently defined or evidenced in the repository. | Needs broad context and human decision access; isolation risks architecture divorced from creative/source constraints. | Do not instantiate now. Use one-off technical decision prompts until a stack and approved technical specs exist; later consider role/agent config. | Split from Systems Engineer only when architecture governance and implementation throughput are distinct, with measurable decision load. | Returns ADR options, consequences, technical risk, and validation plan. User approves stack, platform, budget, and major architecture. | User authority, scope, schema-first, witness/sacred constraints, no invented implementation facts. |
| **Gameplay Programmer** | Future recurring implementation of player-facing mechanics; tool operation plus coding workflow. No current codebase exists. | Needs shared engine, gameplay spec, schema, and runtime context. Separate agent helps only after ownership boundaries exist. | Merge provisionally with Systems Engineer. Later evaluate engine-specific agent config and narrow implementation/verification skills. | Split when player-facing code volume, specialist tooling, and review ownership are sustained; not from title preference. | Returns code, tests/play evidence, serialization impact, and diff. Technical reviewer accepts; design owner confirms behavior. | No unapproved mechanics, schema invention, sacred-event bypass, or stack assumption. |
| **Performance Profiler** | Future recurring measurement/diagnosis; primarily tool-operation workflow and evidence, not persona. | Requires exact build, platform, budgets, scene, capture tools, and reproducible scenario—all currently absent. | Ordinary instruction now. Later create profiling workflow skill/scripts; separate agent only if tools/permissions or independent benchmark context require it. | Split by CPU/GPU/memory/platform only after distinct tools and budgets exist; otherwise one profiling responsibility. | Returns capture environment, baseline, trace, bottleneck evidence, change, and regression result. Human sets acceptable budgets/tradeoffs. | No speculative optimization, preserve behavior and safeguards, report missing tools. |
| **Build and Release Engineer** | Future recurring high-impact build, packaging, provenance, and publication workflow. | Benefits from restricted clean context, least privilege, and reproducible inputs; handoff loss is dangerous. No pipeline exists now. | Later: explicit-only workflow skill + reviewed scripts/CI + tightly scoped agent config. Never rely on role prose for permissions. | Split build from release when credentials, approval, and rollback duties differ; default separation of duties for publication. | Returns artifact hashes, source SHA, test matrix, notices, failures, and rollback. Human explicitly approves release/publication. | File/Git discipline, no force push, scope authority, provenance, truthful verification. |
| **Accessibility Reviewer** | Cross-cutting recurring review likely valuable, but standards, platforms, inputs, and target audience are not yet approved. | Independent review can surface assumptions; must share actual interaction, UI, audio, control, and content context. | Add as review responsibility before a standing agent. Later test standards-backed audit workflow skill and human playtest panel. | Split specialist areas only when target platforms/features justify it. Do not merge human lived-experience review into automated QA. | Returns applicable criteria, evidence, barriers, severity, and remediation options. User approves tradeoffs; affected users/human specialists remain essential. | Respectful design, meaningful playability, honest uncertainty; future persistent accessibility commitment should be project governance. |
| **Security and Provenance Auditor** | Recurring high-consequence intake, permission, dependency, source, license, and artifact-chain review. | Independence and read-only context reduce producer conflict; exact package tree and data flows are mandatory. | Role + audit workflow/checklist skill; strong candidate for restricted read-only subagent/agent config. Deterministic scanning complements, not replaces, judgment. | Split cybersecurity, license, and research provenance only when qualified owners and workload exist; maintain one combined release gate. | Returns threat/provenance findings, evidence, unresolved rights, and go/no-go recommendation. Human security/legal/source authority accepts risk. | Higher-authority instruction, no exfiltration, source/confidence/canon separation, Git and file safety. |

### 8.1 Provisional overlap and dependency observations

- **Creative Director Support and Technical Director** overlap in integration. Until technical governance becomes a sustained responsibility, the latter should remain a temporary lens under the former rather than create duplicate authority.
- **Systems Engineer and Gameplay Programmer** overlap completely at the current documentation-only stage. Their future split should follow code ownership and toolchain evidence.
- **QA Auditor, Accessibility Reviewer, and Security/Provenance Auditor** share review structure but assess different failure domains. They may share a reporting contract while retaining distinct criteria and human approvers.
- **Scripture Research, Historical Research, and Visual Research** share evidence/provenance mechanics. They should reuse source-category and confidence conventions without collapsing domains into a universal “Bible expert.”
- **World/Quest and Gameplay Systems Design** should remain tightly integrated for a small vertical slice. Premature separation would increase cross-role drift and duplicate design rationale.
- **Schema/Content Engineering** depends on approved design and source meaning; **runtime implementation** depends on approved schema/specs; **QA** validates both. Reversing this order invites schema invention, test distortion, or implementation-led theology.
- **Build/Release and Security/Provenance** should have explicit checks before publication, but the same agent should not both create and unilaterally approve a release when meaningful risk exists.

## 9. Rules for deciding when a role deserves its own skill

A role deserves a dedicated skill only when all mandatory conditions pass:

1. the repeated work has one coherent job rather than a broad profession;
2. at least several real tasks demonstrate recurrence;
3. inputs and authority sources are discoverable and versioned;
4. the procedure, decisions, stops, output, and review can be written without inventing the project stack;
5. the skill adds operational guidance not already owned by the Master Protocol;
6. positive, near-miss, missing-input, conflict, and prohibited-behavior cases can be evaluated;
7. the expected benefit can be compared with an ordinary prompt/current workflow baseline;
8. context and maintenance cost are acceptable;
9. references, scripts, licenses, and permissions are auditable; and
10. failure is visible and recoverable.

A role additionally deserves an agent configuration only when at least one material boundary is demonstrated: different model capability, tools/MCP, sandbox/permissions, intentionally independent review, protected context, or long-running delegated ownership. The configuration must still be evaluated against a single-agent/skill baseline.

A role deserves a subagent instance for a particular task only when the work order is bounded, the packet is sufficient, concurrency or isolation has a real benefit, and a named integrator reviews the result. Repetition alone does not require a subagent; many recurring procedures work better as skills used by the main agent.

## 10. Anti-patterns and rejection criteria

Reject or redesign a proposed role artifact when any of these applies:

- **Title-only expertise:** the artifact adds a prestigious label or tone but no owned decisions, sources, outputs, checks, or escalation.
- **Policy laundering:** a conditional skill becomes the only location for witness, sacred-event, source, chronology, schema, safety, or authority rules.
- **One role per noun:** every discipline becomes a separate agent despite identical tools, context, and outputs.
- **Agent as permission bypass:** the proposal assumes a specialist title grants shell, network, repository, release, credential, or publication authority.
- **Stack prophecy:** it encodes Unity, Godot, Unreal, Blender, a language, build command, schema, or target platform not established by current authority.
- **Monolithic expert:** “game developer,” “Bible expert,” or “technical director” instructions attempt to own unrelated decisions and hide conflict.
- **Producer-reviewer collapse:** the same context produces, grades, changes acceptance criteria, and declares success without independent evidence.
- **Handoff by summary only:** source versions, uncertainty, rejected alternatives, errors, and test evidence disappear between roles.
- **Silent consensus:** disagreement is compressed into one confident answer without recording which authority or evidence resolved it.
- **Context cloning:** every agent receives the full repository regardless of task, eliminating any isolation benefit and multiplying token use.
- **Context starvation:** a specialist receives only a task sentence and invents missing project facts.
- **Workflow cosplay:** ChatDev/MetaGPT-like titles are copied without their explicit phases, artifacts, feedback, or verification.
- **Catalog-first design:** roles are enumerated before recurring tasks, engine, schema, tools, and evaluation needs exist.
- **Evaluation theater:** role compliance, eloquence, or aggregate score substitutes for correctness and zero-tolerance project constraints.
- **Unbounded autonomy:** no allowed paths, stop conditions, human approvals, Git safeguards, or rollback.

Immediate rejection is warranted if a role artifact claims authority over the user, hides biblical/historical uncertainty, weakens protected sacred events, invents an approved schema/stack, suppresses failed checks, executes unreviewed third-party code, or publishes without authorization.

## 11. Implications for the future skill-builder

The future skill-builder should not ask only “How should this role skill be written?” It must first decide whether a skill is the correct artifact at all. For a requested role, it should:

1. read the current authority and repository state;
2. extract the recurring behavior from the job title;
3. classify each behavior as governance, domain reference, workflow, tool operation, deterministic enforcement, agent configuration, prompt, or ordinary instruction;
4. produce the O/R/P/A matrix and human gates;
5. test for overlap with existing roles, skills, schemas, validators, and agent profiles;
6. require evidence of recurrence and an evaluation baseline;
7. propose the smallest artifact combination that preserves authority;
8. define exact work-order and return-packet schemas if delegation is involved;
9. specify context/tool/permission differences before permitting a separate agent;
10. create trigger and near-miss cases for any skill;
11. create handoff-loss, conflict, and duplicate-work cases for any multi-role workflow;
12. measure total tokens, latency, integration defects, and human review time—not only local artifact quality;
13. keep project identity and permanent prohibitions outside conditional skills;
14. refuse to create stack-specific implementation roles while the stack is unknown; and
15. label every mapping provisional until project evaluations and the Creative Director approve it.

The builder should emit a **role-artifact decision record** even when its conclusion is “use an ordinary instruction” or “do not build.” That record should include need, observed recurrence, artifact choice, alternatives rejected, authority source, context/capability delta, handoff, human approval, evaluation cases, and invalidation triggers.

## 12. Findings, recommendations, and deferred decisions

### Findings

- Current Codex distinguishes skills, persistent repository guidance, custom agents/subagents, tools, and sandbox/approval controls; none is a synonym for role.
- Role-based software systems demonstrate feasible decomposition, but their interventions combine multiple mechanisms and do not prove that role names cause improvement.
- Multi-agent systems incur specification, coordination, verification, context, and cost failures. Better role descriptions alone are insufficient.
- The current project has nine governance roles but no native role skills, custom-agent configuration, engine, production code, schema, test harness, or release pipeline.
- Human stewardship is structurally necessary for the project's sacred, theological, historical, creative, accessibility, security, and release decisions.

### Recommendations

- Keep the main assistant as integration owner by default.
- Prefer focused workflow skills over profession-sized skills.
- Prefer prompts or ordinary instructions until recurrence and evaluation justify durable artifacts.
- Use isolated agents mainly for bounded research, independent review, or materially different tools/permissions.
- Require O/R/P/A boundaries and structured handoffs for every role invocation.
- Evaluate each split against a simpler single-agent/current-workflow baseline.

### Deferred decisions

This session does **not** decide which candidate roles will exist, which will become skills or agents, whether an `AGENTS.md` will be created, what engine or tools will be used, what accessibility standard or release process will govern, or how many specialists the project needs. Those decisions require later composition, evaluation, builder-requirements, and implementation sessions plus current user priorities.

## 13. Source appendix

### Project authority and predecessor reports

All repository links below are pinned to Session 7's predecessor commit and were inspected on 2026-07-22.

- [Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) — controlling identity, authority, current roles, sacred-event, chronology, source, schema, and file rules.
- [Assistant Activation Prompts](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md) — manual role-launch prompts subordinate to the Master Protocol.
- [Continuity Handoff Prompt](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md) — current handoff template and historical context requirements.
- [Session 1 — Project Context and Authority Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md) — repository state, missing implementation stack, authority, and status vocabulary.
- [Session 2 — Terminology and Artifact Taxonomy](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md) — distinctions among roles, skills, agents, prompts, workflows, policy, tools, references, and evaluations.
- [Session 3 — Current Codex Skill Capability Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md) — current documented skill discovery, invocation, agent distinction, permissions, composition gaps, and `.agents/skills` root.
- [Session 5 — Demonstrated Skill Success Evidence](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Research/LLM_Skills/05_Demonstrated_Skill_Success_Evidence.md) — controlled positive/negative evidence and confounders.
- [Session 6 — Skill Failure, Security, and Maintenance Risks](https://github.com/Degrading1919/The_Bible_Video_Game/blob/cee8ea546d7cc3f0df9eabb4083326a25e7e49d2/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md) — invocation, context, authority, multi-agent, security, Git, evaluation, and maintenance risks.

### Current official product and platform sources

These living documents were accessed 2026-07-22; no stable page-level update date or documentation-repository SHA was exposed.

- OpenAI, [Build skills](https://learn.chatgpt.com/docs/build-skills) — skill package, discovery, invocation, references/scripts, and optional metadata.
- OpenAI, [Subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents) — delegated contexts and configurable agent instructions, models, tools, MCP, and sandbox.
- OpenAI Agents SDK, [Agent orchestration](https://openai.github.io/openai-agents-python/multi_agent/) and [Handoffs](https://openai.github.io/openai-agents-python/handoffs/) — manager-owned specialist calls versus transfer-of-control patterns and explicit handoff data/filtering.
- GitHub, [About custom agents](https://docs.github.com/en/copilot/concepts/agents/cloud-agent/about-custom-agents) and [Custom agents and sub-agent orchestration](https://docs.github.com/en/copilot/how-tos/copilot-sdk/features/custom-agents) — agent profiles with prompts/tools/MCP and isolated delegated execution.
- [Agent Skills specification](https://agentskills.io/specification) — portable skill-package core; it does not define a general role or agent runtime.

### Primary research and repositories

- Cemri et al., [“Why Do Multi-Agent LLM Systems Fail?”](https://arxiv.org/abs/2503.13657), submitted 2025-03-17 — multi-framework failure taxonomy with expert annotation; strong evidence for specification, alignment, and verification risks.
- Qian et al., [“ChatDev: Communicative Agents for Software Development”](https://arxiv.org/abs/2307.07924), submitted 2023-07-16; [current repository README at `4fd4da603801766b14ad8788649cfc1ad21f99a6`](https://github.com/OpenBMB/ChatDev/blob/4fd4da603801766b14ad8788649cfc1ad21f99a6/README.md), commit dated 2026-06-29 — role-and-phase software workflow and current advertised GameDev configuration; combined intervention, not isolated role evidence.
- Hong et al., [“MetaGPT: Meta Programming for A Multi-Agent Collaborative Framework”](https://arxiv.org/abs/2308.00352), submitted 2023-08-01 — role-specific SOP and intermediate-artifact software framework; author-reported results, not proof that project roles should map one-to-one to agents.
- Gao et al., [“Single-agent or Multi-agent Systems? Why Not Both?”](https://arxiv.org/abs/2505.18286), submitted 2025-05-23 — empirical hybrid-routing evidence; moderate transferability because tasks and systems differ from this project.
- Basu et al., [“Understanding Conversational Patterns in Multi-agent Programming: A Case Study on Fibonacci Game Development”](https://openreview.net/pdf?id=cqPjCCf9tW), AIware 2026 — narrow game-programming case showing role alignment need not imply convergence or correctness.
- Yang et al., [“SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering”](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf), NeurIPS 2024 — controlled evidence for a combined instruction, tool, feedback, and context interface.
- BenchFlow AI et al., [SkillsBench](https://arxiv.org/abs/2602.12670), submitted 2026-02-13, and GeniusHTX et al., [SWE-Skills-Bench](https://arxiv.org/abs/2603.15401), submitted 2026-03-16 — direct controlled evidence that reusable instructions can help, do nothing, or regress depending on relevance and context.

### Stable downstream conclusion

Treat a role as governance first, a workflow candidate second, and a separate agent only after a real capability, isolation, or independent-review need is demonstrated. Require the role to change decisions, evidence, artifacts, verification, and accountability—not merely vocabulary or tone. No row in this report authorizes creation of a final project role or skill catalog.

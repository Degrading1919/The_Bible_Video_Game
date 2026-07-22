# Scope-Guard and Minimal-Implementation Skill Analysis

**Session:** 09 of 18
**Research cutoff:** 2026-07-22
**Repository context:** [Degrading1919/The_Bible_Video_Game at predecessor commit f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18](https://github.com/Degrading1919/The_Bible_Video_Game/tree/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18)
**Scope:** Pre-implementation scope control only. This report does not implement a skill, choose the engine or final architecture, reduce the long-term project vision to a prototype, modify production artifacts, or produce a final project skill catalog.

The report uses four claim labels:

- **Finding** — supported by a cited primary source, current official documentation, controlled study, or inspected project artifact.
- **Inference** — a reasoned consequence of findings, not a demonstrated universal rule.
- **Recommendation** — a proposed project practice that must still be evaluated.
- **Unverified** — a material proposition not established by the reviewed evidence.

The central conclusion is:

> A scope guard is feasible as a defeasible workflow that seeks the **smallest complete, constraint-preserving, verified solution**. It is not feasible as a reliable line-count limiter, file-count limiter, universal “no abstraction” rule, or prose-only enforcement mechanism.

“Complete” is essential. The minimum acceptable solution includes current acceptance criteria, required error behavior, verification, and all applicable biblical, historical, sacred-event, provenance, chronology, knowledge-separation, and schema obligations. Omitting one of those is underimplementation, not minimalism.

## 1. Evidence review

### 1.1 What direct LLM-skill evidence establishes

**Finding — strong, conditional evidence:** SkillsBench reported that human-curated skills increased mean pass rate from 24.3% to 40.6% across 84 included tasks, but 16 tasks regressed, the software-engineering domain improved by only 4.5 percentage points, and self-generated skills averaged below the no-skill baseline. Its observational subgroups also found weaker outcomes for four-or-more skills and a negative average for “comprehensive” skills. These results show that relevant procedural context can help and that additional instructions can also distract or harm; they do not isolate a scope-guard intervention ([SkillsBench paper](https://arxiv.org/abs/2602.12670), submitted 2026-02-13; [repository at 5720102e3d6b0d3471b9715995ff96144d9eefb7](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7), accessed 2026-07-22).

**Finding — strong, conditional evidence:** SWE-Skills-Bench reported an average pass-rate gain of 1.2 percentage points across 49 public software-engineering skills: 39 showed no improvement, seven specialized skills improved, and three regressed. The authors identify version mismatch, task-context conflict, and excess instruction/context among regression mechanisms. A narrow scope guard may therefore help only when it is relevant to the active task and current repository; generic minimalism can become another mismatched instruction package ([SWE-Skills-Bench paper](https://arxiv.org/abs/2603.15401), submitted 2026-03-16; [repository at 95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1), accessed 2026-07-22).

**Finding — moderate mechanism evidence:** The SWE-agent study found a 10.7-point resolution-rate improvement for a combined agent-computer interface over a shell baseline in its 300-instance SWE-bench Lite ablation. That intervention joined instructions to constrained tools, syntax feedback, demonstrations, and context management; it does not prove that scope-guard prose alone improves implementation. It does support placing scope instructions next to inspectable diffs and executable feedback rather than relying on a slogan ([SWE-agent NeurIPS 2024 paper](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf); [repository at 3ea751c087f32b16e039a2233dd6eefecef325d5](https://github.com/SWE-agent/SWE-agent/tree/3ea751c087f32b16e039a2233dd6eefecef325d5)).

**Inference:** The evidence supports testing a focused scope workflow. It does not establish that “minimal implementation” is a generally successful Codex skill, any particular wording, or a universal numerical limit.

### 1.2 Established engineering guidance and its limits

**Finding — normative primary guidance, not a controlled effect estimate:** The Agile Manifesto principles pair frequent delivery and working software with technical excellence, good design, and simplicity understood as maximizing work not done. The pairing matters: “simple” does not mean incomplete or structurally careless ([Principles behind the Agile Manifesto](https://agilemanifesto.org/principles.html), 2001, accessed 2026-07-22).

**Finding — practitioner guidance:** Martin Fowler’s YAGNI analysis says presumptive capability should not be built merely for a possible future feature, but explicitly excludes work that keeps a codebase easy to modify. It identifies refactoring, self-testing code, and continuous delivery as enabling practices for evolutionary design, and says YAGNI applies when a future-facing step adds complexity before it is useful. Fowler also acknowledges cases where earlier work would have been cheaper; his prevalence judgment is practitioner opinion, not controlled evidence ([“Yagni”](https://martinfowler.com/bliki/Yagni.html), 2015-05-26).

**Finding — foundational design evidence:** Parnas’s modularization study argues that module quality depends on the decomposition criterion and demonstrates advantages from hiding design decisions likely to change. The lesson is not “fewer modules.” A new boundary can be justified when it contains a volatile decision and improves independent comprehension or change, even with one current consumer ([D. L. Parnas, “On the Criteria To Be Used in Decomposing Systems into Modules,”](https://doi.org/10.1145/361598.361623) Communications of the ACM 15(12), 1972).

**Finding — first-party engineering practice:** Google’s code-review guidance recommends one self-contained change, related tests, a usage with a new API, and a system that continues to work after the change. It expressly says smallness is conceptual rather than a simplistic line-count function and gives exceptions for generated changes and other reviewable cases ([Small CLs](https://google.github.io/eng-practices/review/developer/small-cls.html), accessed 2026-07-22). Google’s exploratory code-review study used interviews, a survey, and logs from nine million reviewed changes; it establishes code review as a major quality and knowledge-transfer practice in that environment but does not prove a universal optimal diff size ([Sadowski et al., “Modern Code Review: A Case Study at Google,”](https://research.google/pubs/modern-code-review-a-case-study-at-google/) ICSE SEIP 2018).

**Finding — technical-debt guidance:** Carnegie Mellon SEI distinguishes intentional debt that accelerates delivery and has a management/repayment plan from unintentional or forgotten debt whose consequences accumulate. It also warns that code-analysis rules alone cannot rank which design issues matter; repository history and developer context are relevant ([Ozkaya and Nord, “Data-Driven Management of Technical Debt,”](https://www.sei.cmu.edu/blog/data-driven-management-of-technical-debt/) 2019-12-16).

**Inference:** These sources converge on an incremental approach with quality-preserving enabling work, reviewable changes, explicit tradeoffs, and managed debt. They do not supply a universal “second consumer” law, file threshold, dependency threshold, abstraction count, or acceptable debt interval.

### 1.3 Current Codex feasibility

**Finding:** Current Codex documentation supports repository-local skills, implicit or explicit selection, progressive disclosure, and a compact selected workflow body. Skills do not grant permissions, and current documentation does not publish deterministic precedence among conflicting selected skills. Session 3 resolved this project’s repository-wide skill root as “.agents/skills” ([OpenAI Build skills](https://learn.chatgpt.com/docs/build-skills), living documentation accessed 2026-07-22; [Session 3 at the predecessor commit](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md)).

**Finding:** Session 4 recommends a preflight/discover/plan-and-gate/execute/validate/deliver spine, explicit output and stop contracts, live authority references, and baseline testing. Session 6 specifically identifies overengineering, unnecessary files, premature abstractions, and unsupported dependencies as risks, while rejecting line-count optimization and warning that a conditional skill cannot carry universal project safeguards alone ([Session 4](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md); [Session 6](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md)).

**Recommendation:** Implement scope control later as a **combination**:

1. permanent project governance for non-negotiable scope and sacred/source/schema rules;
2. an optional reusable skill for the decision workflow;
3. a short checklist or decision record attached to implementation;
4. mechanical diff/dependency/schema/test checks where available; and
5. independent review/evaluation for false blocks, missed expansion, and protected-constraint violations.

A skill alone is advisory and conditionally loaded. A permanent policy alone lacks task-specific decisions. A checklist alone can become box-ticking. Tooling alone cannot decide whether a boundary is justified. The combination assigns each concern to a suitable enforcement layer.

## 2. Candidate rule-by-rule assessment

Evidence strength below concerns the rule as a scope-control practice, not the importance of a project requirement.

| Candidate rule | Status | Evidence assessment | Required qualification |
|---|---|---|---|
| Implement only current acceptance criteria. | **Recommendation with strong rationale** | Small, self-contained change guidance, YAGNI, and benchmark regressions support relevance and boundedness. | “Only” must include implied correctness: validation, failure behavior, compatibility, and higher-authority constraints. Acceptance criteria should be confirmed, not treated as a loophole to omit necessary quality. |
| Prefer the smallest playable vertical slice. | **Useful, defeasible heuristic** | Frequent working delivery and reviewable increments support it; no reviewed source proves that the smallest slice is always cheapest or best. | The slice must be end-to-end enough to test the actual risk and must preserve production-critical domain boundaries. A paper prototype or isolated system stub is not automatically a playable slice. |
| Do not introduce a dependency unless existing capabilities are insufficient. | **Recommended gate** | Dependencies add version, license, supply-chain, portability, context, and maintenance surfaces; Session 6 documents these risks. | “Insufficient” means the current authorized stack cannot meet acceptance, quality, security, or schedule needs at reasonable cost. A bespoke reimplementation can be riskier than a mature dependency. |
| Do not create a new file unless an existing appropriate module cannot own the behavior. | **Useful heuristic, unsafe as an absolute** | Reviewable-change guidance supports artifact economy; Parnas shows that an information-hiding boundary may justify a new module. | “Appropriate owner” is the test. Do not make a god file, mix unrelated responsibilities, hide generated artifacts, or violate repository/engine conventions merely to avoid a file. |
| Do not add configuration for hypothetical future requirements. | **Strong default** | YAGNI directly addresses presumptive capability; unused configuration adds states that must be documented and tested. | Configuration is justified for a current real variation, deployment/environment boundary, user-owned decision, migration seam, security control, or approved architecture requirement. |
| Do not create an abstraction without demonstrated variation, ownership boundary, test seam, or second real consumer. | **Recommended disjunctive rubric** | Parnas supports ownership/change boundaries; testability and current use support reviewability. “Second consumer” and “rule of three” remain heuristics, not laws. | One criterion can suffice if material. Also allow an external contract, serialization boundary, security boundary, engine integration seam, or protected-domain invariant. Require net complexity reduction now. |
| Extend an established pattern before introducing competing architecture. | **Strong default, defeasible** | Context mismatch causes skill regressions; repository consistency reduces new concepts. | Do not extend a pattern that is obsolete, unsafe, contradicted by current authority, or demonstrably unable to meet the requirement. A competing architecture is a user-owned material decision. |
| Stop when required behavior is implemented and verified. | **Strong workflow rule** | Prevents incidental expansion and aligns completion with observable behavior. | Verification may expose required repair. Stop does not forbid necessary documentation, migration, cleanup of introduced debt, or source/provenance records. |
| Record attractive but unnecessary ideas as “not implemented.” | **Recommended output practice** | Creates visible restraint without losing ideas. Evidence is procedural rather than controlled. | Record concise concepts and why they were excluded. Do not create a shadow roadmap, speculative architecture, or implied commitment. |
| Avoid speculative multiplayer, MMO, live-service, procedural-generation, or cross-platform systems unless explicitly approved. | **Project policy plus scope gate** | The current project records single-player direction and has no selected stack; speculative architecture would be especially ungrounded. | An explicit current user decision can reopen scope. Approval must identify the concrete requirement and affected milestone, not merely praise future potential. |
| Preserve schema-first development. | **Non-negotiable project requirement** | The Master Protocol requires an approved schema or a task to create one before structured content/system implementation. | A scope guard must count schema work as minimum completeness, not overhead. If the schema is missing, route to schema creation/approval or stop. |
| Keep sacred-event restrictions explicit. | **Non-negotiable project requirement** | Sacred events and player boundaries are controlling project constraints. | Do not hide them behind generic flags or assume a universal interaction abstraction expresses their theological meaning. Runtime enforcement, tests, and human review will still be needed. |
| Keep source-confidence and provenance requirements explicit. | **Non-negotiable project requirement** | The protocol requires separation of Scripture, interpretation, reconstruction, tradition, speculation, and player-facing/in-world knowledge. | Minimal data models cannot omit source category, confidence, uncertainty, or knowledge-time fields when they are applicable. |

### Rule hierarchy

**Recommendation:** Apply candidate rules in this order:

1. system/developer/runtime safety and current user authority;
2. project identity, biblical/source commitments, sacred-event and canon/scope decisions;
3. approved schemas/specifications and current acceptance criteria;
4. correctness, validation, security, compatibility, and recovery;
5. established repository patterns and authorized long-term architecture;
6. scope-minimization heuristics.

The lower heuristic cannot remove a higher requirement. “No new file,” for example, cannot override schema separation or sacred-event auditability.

## 3. Flexible minimalism model

### 3.1 Definition

**Recommendation:** Define the target as:

> The smallest change that completely satisfies the currently authorized outcome, preserves all applicable invariants, uses justified foundations, remains reviewable and reversible, and passes the strongest available verification.

This definition has five components:

- **Outcome complete:** every accepted behavior and material failure path is implemented.
- **Constraint complete:** project authority and protected-domain rules remain visible and enforceable.
- **Evidence complete:** facts, versions, and source-dependent claims are grounded rather than invented.
- **Verification complete:** applicable tests, builds, runtime/visual checks, schema checks, and human gates pass or are honestly reported unavailable.
- **Artifact economical:** each new file, interface, dependency, configuration point, data field, or public surface has a current traceable reason.

It does not optimize for fewest lines. Ten obscure lines can be worse than fifty explicit ones. It does not optimize for fewest files. One mixed-responsibility file can be worse than two clear owners. It does not optimize for zero dependencies. A maintained, licensed, supported dependency can be safer than a bespoke parser or cryptographic implementation.

### 3.2 Scope classes

Classify proposed work before implementation:

| Class | Definition | Default action |
|---|---|---|
| **Required now** | Direct acceptance criterion or necessary correctness, safety, compatibility, schema, provenance, sacred, or verification work | Implement and trace to the requirement. |
| **Enabling now** | Not player-visible by itself, but required to make the accepted behavior testable, changeable, secure, or valid now | Implement the narrowest viable form and explain the dependency. |
| **Approved foundation** | User-approved long-term architecture whose early placement avoids a demonstrated irreversible or disproportionately expensive transition | Implement only the bounded foundation recorded in the decision; do not implement its future consumers. |
| **Deferred option** | Attractive, plausible, or likely, but not required or approved for this task | Record briefly as not implemented; do not scaffold it. |
| **Conflicting expansion** | Violates authority, assumes an absent stack/schema, or introduces unapproved scope | Reject or stop and surface the conflict. |

### 3.3 Decision rubric

For every disputed addition, answer in order:

1. **What current requirement or invariant fails without it?** Name the acceptance item, authority section, schema rule, security property, test seam, or current consumer.
2. **Why must it exist in this change?** Explain why deferral would make the current result incomplete, untestable, unsafe, incompatible, or materially more expensive through a known transition.
3. **Can an existing owner or authorized capability handle it clearly?** Prefer extension when ownership and coupling remain sound.
4. **What complexity does it add now?** Count concepts and states: files, interfaces, public APIs, dependencies, configuration branches, migrations, permissions, runtime services, documentation, and tests.
5. **What complexity does it remove or contain now?** Identify duplication avoided, volatile decision hidden, unsafe behavior prevented, testability gained, or current variation unified.
6. **What evidence makes the future need more than speculative?** Accepted roadmap decision, second current consumer, external contract, engine constraint, irreversible data format, measured performance/security result, or user approval.
7. **How will it be verified and removed or changed?** State tests, review owner, compatibility boundary, and rollback/migration path.

Pass when the current or approved benefit is concrete, the chosen form is the least complex option that preserves the necessary boundary, and validation can observe it. Defer when benefit is only hypothetical. Escalate when the choice materially changes architecture, scope, engine/tooling, schema, sacred-event treatment, or project direction.

### 3.4 Allowed expansion exceptions

Expansion beyond literal task wording may be justified by:

- a higher-authority project constraint omitted from the task wording;
- a security, privacy, license, data-loss, or destructive-action safeguard;
- an approved schema, external API, serialization, save-data, or migration contract that must remain compatible;
- a necessary test, fixture, build, runtime, or visual-validation seam;
- an engine/tool requirement established from the current repository and first-party versioned documentation;
- an information-hiding boundary around a volatile or protected decision;
- a current second consumer or demonstrated variation;
- a user-approved architectural decision with a bounded record;
- a known one-way door, such as persisted identifiers or shipped data, where later change has demonstrated disproportionate cost; or
- repair of a defect directly introduced or exposed by the implementation.

**Recommendation:** “Best practice,” “production ready,” “future proof,” “might scale,” and “clean architecture” are not sufficient justifications by themselves. They name aspirations, not evidence.

### 3.5 User-approved long-term architecture

The user/Creative Director owns major architecture and scope decisions within the project’s authority chain. A scope guard must not silently veto an explicit decision merely because it is larger than a vertical slice. It should:

1. restate the approved decision and source;
2. flag biblical, historical, schema, cost, maintenance, and implementation risks that cannot be hidden;
3. distinguish the foundation required now from the future systems it could enable;
4. propose a narrow checkpointed implementation;
5. record what remains intentionally unimplemented; and
6. require reapproval if execution reveals materially larger consequences.

An ambiguous aspiration such as “eventually support the whole biblical timeline” is not approval for a universal era framework in the first implementation. A specific decision such as “stable content identifiers must survive across lineage-era saves” can justify an identifier contract once the schema and save-data authority exist.

## 4. Justified-abstraction criteria

An abstraction is justified when it creates a useful boundary or reduces net present complexity, not when it merely predicts the future.

### 4.1 Sufficient evidence candidates

One strong criterion may suffice; several weak labels do not:

1. **Demonstrated variation:** two current behaviors share a stable concept but vary along a named axis.
2. **Second real consumer:** another current module, artifact, or workflow uses the contract.
3. **Information-hiding/ownership boundary:** one decision is likely to change independently and can be contained, following Parnas’s criterion.
4. **Test seam:** the boundary permits material behavior or failure paths to be verified without exposing internals or requiring an unavailable runtime.
5. **External contract:** engine callback, file format, network/API contract, database/schema, asset pipeline, or save-data boundary exists now.
6. **Security or permission boundary:** untrusted input, credentials, privileged operations, or destructive effects require isolation.
7. **Protected-domain boundary:** sacred-event rules, provenance/confidence categories, chronology, or player/in-world knowledge must remain explicit and independently auditable.
8. **Replacement/migration seam:** a current authorized component must be replaceable for an identified version or migration event.

### 4.2 Required quality tests

Even with a criterion, the proposed abstraction should pass all of these:

- Its name expresses a current project concept rather than a vague “manager,” “service,” or “helper.”
- Its contract is smaller and more stable than the implementations it hides.
- Current callers become easier to understand or safer to change.
- It does not leak engine, framework, or schema assumptions that have not been selected.
- It has at least one current usage in the same change unless the repository’s authorized framework requires registration separately.
- Its behavior can be tested at the appropriate level.
- Removing it would make ownership, verification, or change containment materially worse.
- It does not collapse distinct biblical/historical categories into a generic mechanism for convenience.

### 4.3 Rejection signals

Defer or remove an abstraction when:

- the only reason is a hypothetical second consumer;
- it adds a public interface whose only implementation passes calls through unchanged;
- configuration exists only to select the one current implementation;
- an “extensible” registry contains no current extension;
- a base class encodes no shared invariant;
- a wrapper duplicates an existing authorized capability;
- naming is generic because the intended concept is unclear;
- tests verify structure or mocks rather than the accepted behavior; or
- the abstraction makes sacred/source/schema behavior less visible.

**Unverified:** No reviewed primary source establishes that three occurrences, two consumers, one interface, or any numerical threshold universally determines the correct abstraction point. These are prompts for judgment, not validators.

## 5. New-file, dependency, and configuration tests

### 5.1 New-file test

A new file should answer “yes” to a current need and identify its owner:

| Question | Pass evidence | Failure signal |
|---|---|---|
| Does a repository/engine/schema convention require this artifact type or location? | Current manifest, approved pattern, first-party tool requirement | Invented folder tree or remembered engine assumption |
| Does the file own a distinct current responsibility or volatile decision? | Named boundary and current caller/content | Splitting only to lower line count |
| Would adding the behavior to an existing file mix responsibilities or create conflicting ownership? | Concrete coupling or authority problem | Preference for “cleaner organization” without impact |
| Is it a necessary schema, migration, fixture, test, generated artifact, license, or provenance record? | Required validation or legal/traceability purpose | Decorative README, placeholder, empty config |
| Is its lifecycle different from the existing owner? | Different generator, reviewer, deployment, or update cadence | Same owner and change pattern |
| Is the path authorized and the file used now? | Traceable consumer/check | Orphan, unused API, future directory scaffold |

If no current appropriate module exists, a new file is allowed. If an existing file is the clear owner, extend it. If both are plausible and the decision affects long-term architecture, present the tradeoff rather than optimizing the count.

### 5.2 Dependency test

Before adding a package, plugin, service, model, MCP server, or tool:

1. Identify the exact current capability gap.
2. Demonstrate that authorized existing capabilities or a small local implementation are insufficient or materially riskier.
3. Verify the project stack and compatible version from current authority; do not infer Unity, Godot, Unreal, Blender, language, or package manager.
4. Inspect the exact package, transitive dependencies, scripts, network/filesystem behavior, release state, and security posture.
5. Verify file-level license, notices, asset/data rights, and provenance at a pinned version.
6. Compare integration, runtime, binary/build size, performance, platform, operational, and maintenance cost.
7. Identify current consumers and why the dependency belongs at their layer.
8. State lock/pin/update policy, failure behavior, and removal or replacement path.
9. Add the smallest integration and tests; do not enable unrelated features.
10. Require user approval when the dependency selects architecture, incurs cost, expands permissions/network, changes distribution obligations, or creates an external service relationship.

A dependency is not automatically excessive. Reimplementing serialization, cryptography, database drivers, accessibility, or engine-supported behavior can create more risk. The gate compares total present risk, not package count.

### 5.3 Configuration test

Configuration is justified only when at least one current actor needs to vary a value across a real boundary:

- current environments or deployment targets differ;
- the user must choose a value;
- a secret or machine-specific path cannot be hard-coded;
- an approved schema/version/migration requires compatibility;
- a feature is actually staged and the flag has an owner, removal condition, and tested states;
- a sacred/safety policy must be data-driven under an approved schema; or
- current assets/content require authorized data rather than code.

Reject configuration that:

- exposes one fixed implementation only for imagined replacement;
- adds toggles for multiplayer, live service, cross-platform, procedural generation, or DLC without approval;
- creates environment variables no current environment consumes;
- duplicates an existing authoritative setting;
- moves a protected invariant into an operator-disableable switch; or
- has no documented default, owner, validation, and test for each supported state.

### 5.4 Addition ledger

**Recommendation:** Before implementation, record each proposed addition in a compact table:

| Addition | Type | Current requirement/invariant | Existing alternative | Why now | Added complexity | Verification | Decision |
|---|---|---|---|---|---|---|---|

The ledger is a reasoning aid, not permission. It should disappear into the implementation record or review summary rather than create permanent paperwork for trivial edits.

## 6. Vertical-slice and technical-debt distinction

### 6.1 A valid vertical slice

A vertical slice is a narrow, end-to-end implementation that exercises a representative player outcome and the integration boundaries needed to learn from it. For this project, “playable” should eventually include the appropriate runtime experience, not only data classes or a design diagram. At the current predecessor, however, the repository has no selected engine, approved schema, production code, build, test harness, roadmap, or formally approved vertical-slice spec; the detailed Galilee/Capernaum material remains a proposal ([Session 1](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md)).

**Recommendation:** A production-oriented slice should:

- prove one meaningful player loop or content flow end to end;
- use representative data and failure cases;
- obey the approved schema or make schema approval the task;
- exercise sacred/source/chronology/knowledge boundaries where relevant;
- include enough persistence, validation, and instrumentation to answer the slice’s learning question;
- remain independently buildable/testable after each accepted change;
- identify deliberately simplified breadth; and
- avoid building future eras, platforms, networking, economies, or procedural systems merely to demonstrate extensibility.

### 6.2 Acceptable shortcut versus debt

| Dimension | Acceptable slice simplification | Technical debt requiring a record | Unacceptable shortcut |
|---|---|---|---|
| Scope | Fewer content instances or one region/loop | Temporary limitation with known later cost | Missing accepted behavior |
| Data | Small representative dataset under approved schema | Transitional adapter with owner/migration trigger | Ad hoc fields that bypass schema-first rules |
| Architecture | Direct implementation behind a stable current boundary | Intentional compromise whose interest is understood | Global coupling that makes protected rules untestable |
| Validation | Narrow but real tests/runtime evidence for the slice | Missing noncritical coverage with scheduled trigger | Disabled/weakened tests or fabricated pass claims |
| UI/art | Placeholder clearly labeled and non-authoritative | Temporary asset with license/replacement record | Westernized or speculative sacred imagery treated as approved |
| Sacred events | Limited scenario with full protection | None: protection is not optional debt | Attackable/derailable sacred figure/event |
| Sources/history | Fewer researched claims with explicit confidence | Research gap labeled and blocked from authoritative use | Invented certainty or erased provenance |
| Operations | Local/manual process suitable to the current task | Manual step with owner and automation trigger | Irrecoverable or insecure process |

Technical debt is intentional only when the project records:

- the shortcut and affected artifact;
- the immediate value;
- the future “interest” or failure mode;
- why the debt is safe within current boundaries;
- an owner or decision owner;
- a repayment or reevaluation trigger;
- verification that prevents it crossing a protected boundary; and
- a removal/migration path.

“TODO later” is not a debt plan. Conversely, a direct implementation that is easy to change and adds no future cost need not be stigmatized as debt merely because it lacks an abstraction.

### 6.3 Foundational work test

Foundational work is justified when deferral would create a known one-way door, invalid data, untestable protected behavior, or disproportionate rework. Examples include stable identifiers before persisted content ships, an approved source/confidence schema before mass content creation, or a protected-event invariant before scenarios depend on it. These are examples of decision form, not approvals for files that do not yet exist in this repository.

The proposer must identify the future transition, its probability/evidence, cost asymmetry, current dependency, and bounded foundation. If the case rests only on “we will need it eventually,” defer it.

## 7. Sacred-event, schema, and provenance preservation

### 7.1 These controls are inside the minimum

The [Master Assistant Protocol at the predecessor](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) requires:

- the player to remain a witness rather than replacement, savior, or rewriter;
- protected, fixed sacred events;
- separation of Scripture, interpretation, reconstruction, tradition, uncertainty, and invention;
- era-appropriate in-world knowledge separated from modern player-facing codex knowledge;
- source and confidence labeling; and
- schema-first structured content and implementation.

**Project requirement:** A scope guard must not classify these as polish, extensibility, or future-proofing. When applicable, they are current acceptance constraints even if a task prompt omits them.

### 7.2 Explicitness rules

1. **Sacred-event handling:** Keep the named invariant visible in domain schema, code, tests, scenario design, review, and human approval as each layer becomes available. A generic “protected entity” facility may support implementation but cannot replace explicit sacred-event semantics or theological review.
2. **Schema-first:** If structured content or system behavior depends on data without an approved schema, stop or change the authorized task to schema creation. Do not invent fields as accepted contracts. A tiny hard-coded content set is not an escape from the rule when it represents structured production content.
3. **Provenance/confidence:** Preserve source category, citation/provenance, confidence, disputed status, and reconstruction/invention labels where claims enter project artifacts. Do not remove them to simplify data entry or interfaces.
4. **Knowledge separation:** Do not reuse one generic text/content record when in-world characters and player-facing codex readers have different permitted knowledge.
5. **Historical uncertainty:** Prefer a narrower set of well-supported content over broad confident invention. “Unknown” and “disputed” are valid outputs.
6. **Source text:** Assistant paraphrase must remain labeled; original-language or translation data requires verified editions and rights.

### 7.3 Scope conflict behavior

If the smallest literal implementation would violate a protected rule, the guard must propose the smallest **compliant** implementation. If no compliant implementation is possible with current authority, sources, schema, or tools, stop and report the exact blocker. It must never trade a sacred/source/schema failure against schedule, fewer files, or an aggregate quality score.

## 8. Workflow checkpoints and output contract

### 8.1 Behavior contract

A future workflow should promise:

> Before implementation, establish current authority, acceptance criteria, repository/stack facts, and applicable invariants; propose the smallest complete approach; require evidence for every material expansion; pause user-owned architecture/scope decisions; implement only authorized scope; verify behavior and protected constraints; then report implemented, deferred, and unverified work separately.

It should never promise to minimize line count, eliminate abstractions, prevent all scope creep, decide final architecture, or overrule explicit user direction.

### 8.2 Checkpoints

**Checkpoint A — task framing, before planning**

- Restate the player/user outcome and explicit acceptance criteria.
- Identify allowed outputs and prohibited production changes.
- Locate current authority, schemas/specs, repository patterns, and stack versions.
- Mark missing facts as discoverable, user-owned, or blocking.
- List protected biblical/historical/sacred/provenance constraints that apply.

**Checkpoint B — scope proposal, before implementation**

- Define the smallest complete solution and its verification.
- Produce the addition ledger for new files, dependencies, configuration, public interfaces, services, schemas, or migrations.
- Classify each item as required now, enabling now, approved foundation, deferred, or conflicting.
- Identify architectural/engine/schema/scope decisions that require the user.
- State “not implemented” items.

**Checkpoint C — expansion interrupt, during implementation**

Trigger when an unexpected file, dependency, public interface, configuration state, service, schema change, unrelated refactor, test change, permission, or platform assumption becomes necessary. Re-run the relevant rubric. Continue only if the item is necessary within existing authority; otherwise defer or ask for the material decision.

**Checkpoint D — verification and repair**

- Run applicable existing tests/builds, schema/reference checks, runtime/visual/play checks, and diff review.
- Do not weaken tests or errors to obtain a pass.
- Repair failures caused by the authorized implementation.
- Record tools/checks not available and the reduced assurance.

**Checkpoint E — delivery**

- Map every changed artifact to a requirement or accepted exception.
- Confirm no unauthorized file, dependency, configuration, protocol, schema, gameplay, or catalog change.
- Report implemented, validation, not implemented, debt/foundations, unknowns, and user decisions.
- Stop when complete; do not continue into attractive adjacent work.

### 8.3 Relationship to planning, implementation, and review

| Phase | Scope-guard responsibility | Separate responsibility |
|---|---|---|
| Planning | Frame acceptance and constraints; select minimum complete approach; identify user decisions | Domain expert validates theology/history/gameplay/architecture quality |
| Implementation | Track authorized additions; interrupt on material expansion; preserve invariants | Implementer owns correct code/content in the selected stack |
| Review | Acceptance-to-diff map; additions/dependency/config audit; not-implemented check | Tests, runtime/visual review, source audit, security, domain-human approval |
| Maintenance | Revisit deferred/foundation/debt triggers | Roadmap, architecture governance, dependency updates, schema migrations |

The same model may perform all phases in a small task, but the checkpoints and evidence should remain distinct. For high-impact work, an independent reviewer or clean-context evaluation reduces self-justification.

### 8.4 Output contract

The final implementation report should include only material fields:

1. **Outcome:** accepted behavior completed.
2. **Changed artifacts:** paths and purpose.
3. **Expansion decisions:** new files/dependencies/config/interfaces and evidence, or “none.”
4. **Validation:** checks actually run and results.
5. **Protected constraints:** applicable sacred/schema/provenance/knowledge checks.
6. **Not implemented:** attractive or requested-adjacent items deliberately excluded.
7. **Debt/foundation:** bounded exception, owner/trigger, and migration/rollback if any.
8. **Unknowns/blockers:** no disguised certainty.

For trivial work, fields with “none” can be collapsed into one sentence. The workflow should not create a permanent decision document for every edit.

## 9. Failure modes and over-rigidity risks

### 9.1 False-positive blocks

| False positive | Harm | Mitigation |
|---|---|---|
| Rejecting a new file that creates a genuine ownership boundary | God modules, mixed authority, harder review | Use ownership/lifecycle/Parnas test, not count |
| Rejecting a dependency categorically | Bespoke insecure or unmaintainable reimplementation | Compare total current risk and official stack support |
| Rejecting schema, tests, provenance, or accessibility as “extra” | Incomplete or unsafe implementation | Define them as completeness when applicable |
| Rejecting refactoring that enables a safe current change | Brittle patch and future interest | Allow bounded behavior-preserving enabling work with tests |
| Rejecting current user-approved architecture | Tool usurps Creative Director | Record decision, disclose risks, narrow the implementation |
| Rejecting a test seam because there is one production consumer | Unverifiable failure paths | Treat material testability as independent justification |
| Rejecting performance/security work until a visible feature demands it | Missed nonfunctional acceptance or one-way door | Require measured requirement/threat/constraint, not visible-feature test |

### 9.2 False negatives

| False negative | Mechanism | Detection |
|---|---|---|
| “Best practice” laundering | Vague label substitutes for current need | Demand requirement, evidence, consumer, verification |
| Ledger gaming | Every item is labeled “required” | Independent acceptance-to-diff review |
| Tiny files hiding conceptual sprawl | Count stays low while public states/interfaces grow | Count concepts, states, permissions, dependencies, APIs |
| Generic abstraction hiding sacred/source rules | Surface looks reusable but loses domain auditability | Protected-constraint trace and domain review |
| Tests blessing expansion | New fixtures/assertions redefine acceptance | Preserve pre-change tests and justify every test edit |
| User aspiration treated as detailed approval | Long-term vision becomes permission for scaffolding | Require concrete decision, milestone, and affected artifacts |
| “Temporary” shortcut without trigger | Debt becomes permanent | Debt record, owner/trigger, review |
| Existing pattern extended despite evidence it is wrong | Consistency preserves harm | Safety/version/authority audit and explicit exception |

### 9.3 Over-rigidity failure modes

- **Underengineering:** accepted error paths, migrations, validation, or recovery are omitted.
- **Architecture fossilization:** the guard extends existing patterns after new requirements invalidate them.
- **Single-file collapse:** unrelated responsibilities are combined to satisfy a file heuristic.
- **Duplicate implementations:** dependencies or abstractions are rejected even when they would reduce current duplication and risk.
- **Hidden project values:** domain-specific safeguards are compressed into generic code.
- **Prototype trap:** a narrow slice cannot evolve because malleability/testing was mislabeled future work.
- **Vision erosion:** every session optimizes locally without preserving approved long-term lineage, codex, and world-system decisions.
- **Process tax:** the checklist costs more than the trivial implementation and encourages ritual answers.
- **Authority inversion:** the guard blocks an explicit user decision or treats its own heuristic as biblical/project authority.

### 9.4 Stop and override rules

The guard should stop for missing schema/authority, a material architecture or scope choice, conflicting current instructions, unavailable required validation, unapproved dependency/service/permission, or a protected-constraint violation. It should allow an explicit user override of a scope heuristic after presenting consequences. It must still preserve mandatory uncertainty and risk disclosure and remain subject to system/developer safety and actual tool permissions.

## 10. Evaluation cases

The cases below are future fixtures, not evidence that the proposed workflow works.

| Case | Prompt condition | Expected scope behavior | Failure caught |
|---:|---|---|---|
| 1 | Add one accepted behavior to an existing appropriate module | Modify module and related tests only; no new interface/config | Routine overengineering |
| 2 | Existing file would mix unrelated content authority and runtime behavior | Permit a new file with named owner/lifecycle | False file-count block |
| 3 | Agent proposes a general event bus for one interaction | Reject/defer absent current boundary or consumers | Premature abstraction |
| 4 | One consumer needs isolation to test destructive failure behavior | Allow a narrow test seam with direct usage | “Second consumer” rigidity |
| 5 | Add a parsing dependency for a format already handled by the authorized standard library | Reject and use existing capability | Unnecessary dependency |
| 6 | A selected stack’s first-party required importer is missing | Gate on verified stack/version/license; allow only after approval where needed | Dependency absolutism and stack invention |
| 7 | “Prepare multiplayer/MMO architecture while implementing inventory” | Record not implemented; no networking interfaces/config/services | Speculative expansion |
| 8 | User explicitly approves a bounded persistence identifier contract | Preserve approval, implement the narrow contract, defer future eras/features | Authority inversion or uncontrolled foundation |
| 9 | Quest content is requested but no approved quest schema exists | Stop or route to schema creation; do not invent production fields | Schema bypass |
| 10 | Sacred-event scene is requested with generic attackable NPC base | Require explicit protected behavior and tests/review; reject harmful shortcut | Sacred constraint hidden by abstraction |
| 11 | Historical location is disputed | Preserve confidence/source alternatives; narrow content rather than pick certainty | Provenance erased for simplicity |
| 12 | “Make the diff smaller” would combine responsibilities and remove errors | Reject line-count optimization; preserve behavior and clear ownership | Code-golf minimalism |
| 13 | Existing pattern is incompatible with current tool version or security requirement | Propose bounded exception and user-owned architecture decision | Pattern fossilization |
| 14 | Accepted task is finished, but agent suggests procedural world generation | Stop and list it as not implemented without scaffolding | Failure to stop |
| 15 | Trivial documentation typo | Apply lightweight rubric silently; no ledger document | Process tax |

### 10.1 Metrics

Session 15 should set thresholds. This session recommends measuring:

- **Acceptance completion rate:** required criteria passed without weakening tests.
- **Protected-constraint violation rate:** sacred, biblical/source, chronology, knowledge, schema, or authority violation; target should be zero for acceptance.
- **Unnecessary-addition rate:** added files/dependencies/config/interfaces with no accepted justification.
- **Expansion-capture rate:** material unexpected expansions surfaced before implementation.
- **False-block rate:** justified current/foundational work incorrectly prevented.
- **Underimplementation rate:** required quality or enabling work wrongly omitted as scope.
- **Decision-trace precision:** changed artifacts with a valid requirement/invariant/exception link.
- **Not-implemented fidelity:** deferred ideas produce no scaffolding or implied completion.
- **Validation integrity:** required checks actually run; no falsified or weakened validation.
- **Rework:** corrections attributable to guard over-rigidity or missed scope.
- **Efficiency:** tokens, wall time, number of user interruptions, and diff review time versus no-guard baseline.
- **Trigger quality:** relevant activation, near-miss nonactivation, and explicit-invocation behavior if implemented as a skill.

Evaluate against matched no-skill/current-workflow baselines in clean contexts, retain failures, and include both greenfield and existing-code tasks. An aggregate improvement cannot compensate for one protected-constraint violation.

**Unverified:** There is no evidence-backed universal threshold for maximum files, lines, dependencies, interfaces, token overhead, false-block rate, or accepted debt. Thresholds must be task- and project-specific and revised from data.

## 11. Recommendation for future skill-builder requirements

### 11.1 Artifact placement recommendation

**Recommendation:** Treat scope control as a layered capability:

| Layer | Put here | Do not rely on it for |
|---|---|---|
| Master Protocol / permanent governance | Witness premise, sacred protection, schema-first rule, source/knowledge separation, user authority, no unapproved speculative platform scope | Step-by-step task planning |
| Reusable scope workflow skill | Acceptance framing, flexible-minimalism rubric, expansion checkpoint, additions ledger, stop/report contract | Permanent authority or mechanical enforcement |
| Task checklist/implementation record | Current accepted scope, additions, exceptions, not implemented, validation | General policy |
| Tooling/validators | Diff paths, package/lock changes, unused APIs where detectable, schema/tests/builds, source fields, prohibited mutations | Architectural value or theological judgment |
| Human/domain review | Major architecture/scope, sacred figures/events, contested history/theology, debt acceptance | Routine deterministic checks |
| Evaluation suite | False positive/negative scenarios, baseline comparison, regression and protected floors | Production execution |

This is not a final project skill catalog. It is the placement decision for this one candidate concept.

### 11.2 Mandatory future builder requirements

If the future skill-builder is asked to author a scope-control skill, it should require:

1. one coherent job: pre-implementation and expansion-checkpoint scope control;
2. a description that triggers on implementation planning/overengineering review and excludes pure brainstorming, roadmap creation, final architecture, and post-implementation simplification;
3. live reading of the current Master Protocol, acceptance criteria, schemas/specs, repository patterns, and stack facts;
4. the “smallest complete” definition and explicit rejection of line/file-count optimization;
5. the five scope classes and decision rubric;
6. justified-abstraction, new-file, dependency, and configuration tests;
7. user-owned decision boundaries and an override path with mandatory risk disclosure;
8. protected sacred/schema/provenance/knowledge rules as applicability checks, not duplicated controlling policy;
9. plan, expansion-interrupt, verification, and delivery checkpoints;
10. a lightweight path for trivial work and a fuller ledger only for material additions;
11. “not implemented” reporting without speculative scaffolding;
12. technical-debt/foundation records with owner, trigger, verification, and migration/rollback;
13. stop behavior for missing authority/schema, unresolved material choice, required validation failure, or concurrent change;
14. clean-context positive, near-miss, adversarial, false-block, and missed-expansion fixtures including all cases in Section 10;
15. matched no-skill/current-workflow evaluation using completion, unnecessary-addition, false-block, underimplementation, validation, efficiency, and zero-tolerance protected metrics;
16. no engine/framework-specific instructions until the repository selects and versions the stack;
17. no companion-skill catalog or assumption of deterministic multi-skill precedence; and
18. maintenance triggers when the Master Protocol, schemas, architecture, stack, Codex behavior, or evaluation failures change.

### 11.3 Final feasibility judgment

**Recommendation — proceed only as an evaluated candidate:** A repository-local workflow skill is plausible because the task recurs, has a coherent decision procedure, benefits from progressive disclosure, and can be tested. The evidence does not justify automatic trust or universal invocation. The strongest implementation would be concise, grounded in live project authority, and paired with review/evaluation rather than attempting to encode every exception.

**Unverified:** Whether implicit invocation or explicit-only use yields the better project outcome; whether one combined pre-implementation skill or a plan/review split performs better; whether the checklist overhead pays for itself on this repository’s future production tasks; and which numerical thresholds should govern acceptance. Sessions 14–16 should resolve governance, evaluation, and builder requirement classification before Session 17.

## 12. Source appendix

### 12.1 Project authority and predecessor reports

All project links are pinned to Session 9 predecessor commit [f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18](https://github.com/Degrading1919/The_Bible_Video_Game/tree/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18), inspected 2026-07-22.

- [The Bible Video Game Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) — controlling identity, authority, roles, sacred-event protection, chronology/knowledge separation, Scripture/codex rules, schema-first policy, and file discipline.
- [Session 1: Project Context and Repository Authority Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md) — verified repository state, absent engine/code/schema/build/test stack, authority routing, and proposed rather than approved vertical slice.
- [Session 3: Current Codex Skill Capability Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md) — current skill discovery/invocation/progressive-disclosure model, permission boundary, and unresolved composition behavior.
- [Session 4: Effective Skill Anatomy and Authoring Principles](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md) — focused workflow anatomy, preflight/gates, output and stop contracts, live authority, and evaluation.
- [Session 5: Demonstrated Skill Success Evidence](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Research/LLM_Skills/05_Demonstrated_Skill_Success_Evidence.md) — controlled positive and negative skill evidence, confounders, and project transfer limits.
- [Session 6: Skill Failure, Security, and Maintenance Risks](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f01ea1560c0c36e51cb03cd6009ce4b8d9d52b18/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md) — overengineering, file/abstraction/dependency risks; line-count rejection; validation, security, and governance safeguards.

Session 1 found no current roadmap, approved vertical-slice spec, architecture file, or approved schema. The Galilee dossier is therefore not cited as controlling production authority here.

### 12.2 Current official Codex source

- OpenAI, [Build skills](https://learn.chatgpt.com/docs/build-skills), living documentation accessed 2026-07-22 — skill packages, repository discovery, invocation, progressive disclosure, and authoring guidance. The living page exposed no auditable page publication date or documentation commit in the fetched manual.

### 12.3 Controlled LLM-agent evidence

- BenchFlow AI et al., [“SkillsBench: Benchmarking How Well Agent Skills Work Across Diverse Tasks”](https://arxiv.org/abs/2602.12670), arXiv:2602.12670, submitted 2026-02-13; [repository at 5720102e3d6b0d3471b9715995ff96144d9eefb7](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7), commit dated 2026-07-18, Apache-2.0, accessed 2026-07-22.
- GeniusHTX et al., [“SWE-Skills-Bench: Do Agent Skills Actually Help in Real-World Software Engineering?”](https://arxiv.org/abs/2603.15401), arXiv:2603.15401v1, submitted 2026-03-16, preliminary preprint; [repository at 95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1), commit dated 2026-04-14, MIT, accessed 2026-07-22.
- Yang et al., [“SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering”](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf), NeurIPS 2024; [SWE-agent repository at 3ea751c087f32b16e039a2233dd6eefecef325d5](https://github.com/SWE-agent/SWE-agent/tree/3ea751c087f32b16e039a2233dd6eefecef325d5), commit dated 2026-07-16, MIT, accessed 2026-07-22.

### 12.4 Engineering principles, modularity, review, and debt

- Beck et al., [Principles behind the Agile Manifesto](https://agilemanifesto.org/principles.html), 2001, accessed 2026-07-22. Normative primary statement, not controlled evidence for a scope skill.
- Martin Fowler, [“Yagni”](https://martinfowler.com/bliki/Yagni.html), 2015-05-26, accessed 2026-07-22. First-party practitioner analysis; its frequency judgments are not treated as controlled findings.
- D. L. Parnas, [“On the Criteria To Be Used in Decomposing Systems into Modules”](https://doi.org/10.1145/361598.361623), Communications of the ACM 15(12), 1053–1058, 1972-12-01. Primary modularization study.
- Google, [Small CLs](https://google.github.io/eng-practices/review/developer/small-cls.html), first-party engineering practice accessed 2026-07-22. Explicitly conceptual rather than a hard line-count rule.
- Caitlin Sadowski, Emma Söderberg, Luke Church, Michal Sipko, and Alberto Bacchelli, [“Modern Code Review: A Case Study at Google”](https://research.google/pubs/modern-code-review-a-case-study-at-google/), ICSE SEIP 2018, accessed 2026-07-22. Exploratory industrial study; not a controlled minimal-diff experiment.
- Ipek Ozkaya and Robert Nord, [“Data-Driven Management of Technical Debt”](https://www.sei.cmu.edu/blog/data-driven-management-of-technical-debt/), Carnegie Mellon Software Engineering Institute, 2019-12-16, accessed 2026-07-22.

### 12.5 Evidence limits

No reviewed primary study directly evaluates a “scope-guard” Codex skill for game development. No evidence establishes universal numerical thresholds for abstraction, files, dependencies, configuration, diff size, or technical-debt duration. The repository has no authoritative production stack on which to test engine-specific scope decisions. Accordingly, every behavioral rule beyond the Master Protocol’s project requirements remains a recommendation or defeasible heuristic until Session 15 evaluation and later clean-context testing establish project-specific results.

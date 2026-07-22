# Post-Implementation Simplification Skill Analysis

**Session:** 10 of 18
**Research cutoff:** 2026-07-22
**Repository context:** [Degrading1919/The_Bible_Video_Game at predecessor commit `f5b64c8996f212f99b7f118d4814b6e7192e742d`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/f5b64c8996f212f99b7f118d4814b6e7192e742d)
**Authorized output:** this research report only
**Boundary:** analysis of a possible post-implementation workflow. This report does not create the skill, refactor project code, select an engine, modify tests or schemas, create a final project skill catalog, or treat the deleted `Research/LLM_Skills/` drafts as evidence.

Claim labels are used consistently:

- **Finding** — supported by a cited primary source, official documentation, controlled study, or inspected repository artifact.
- **Inference** — a reasoned project consequence that has not itself been demonstrated as a universal result.
- **Recommendation** — a proposed design or practice for later evaluation.
- **Unverified** — a material proposition the reviewed evidence does not establish.

The central conclusion is:

> A post-implementation simplifier is defensible only as a conservative, reviewable refactoring workflow that starts from a verified behavioral baseline, changes one bounded concern at a time, preserves an explicit invariant ledger, and reruns every affected verification layer. It must optimize for **the smallest clear and maintainable implementation that preserves behavior and safeguards**, not for the fewest lines, files, classes, or callbacks.

The verb **prove** in this report means “assemble the strongest available preservation case for the authorized change,” not “mathematically prove equivalence for all possible executions.” Compilation, tests, static checks, save round trips, runtime evidence, visual comparison, performance captures, and human review cover different failure classes. None should be silently substituted for another.

## 1. Evidence review of refactoring and simplification agents

### 1.1 Refactoring is behavior preservation, not output compression

**Finding — established engineering meaning:** Martin Fowler defines refactoring as changing the internal structure of software so it is easier to understand and cheaper to modify without changing observable behavior. His catalog also treats refactorings as small transformations whose safety depends on an executable test suite and incremental checks ([Fowler, “Refactoring”](https://martinfowler.com/bliki/Refactoring.html), updated 2019-05-20; [Refactoring catalog](https://refactoring.com/catalog/), accessed 2026-07-22). Google’s review guidance similarly says change size is conceptual rather than a raw line-count rule and recommends self-contained changes that keep the system working with related tests ([Google, “Small CLs”](https://google.github.io/eng-practices/review/developer/small-cls.html), accessed 2026-07-22).

**Inference:** “Smaller” is an outcome of removing unjustified complexity, not the acceptance criterion. A transformation that reduces line count while combining unrelated responsibilities, erasing a domain name, weakening an error path, or breaking a serialized reference is not a successful simplification.

### 1.2 Direct evidence from LLM refactoring benchmarks

| Evidence case | Design and reported result | What it supports | What it does not support |
|---|---|---|---|
| **RefactorBench** | The ICLR 2025 study constructed 100 large, multi-file tasks in real Python repositories. Baseline agents solved 22% with base instructions, while a time-constrained human solved 87%. A state-aware interface that continually represented accumulated edits produced a reported 43.9% **relative** improvement over baseline agent results ([paper](https://openreview.net/pdf?id=ZjsHNRxH2Q); [repository at `210b2d15a373ad265aa721f70199c9962d7de069`](https://github.com/microsoft/RefactorBench/tree/210b2d15a373ad265aa721f70199c9962d7de069), commit dated 2025-07-11). | Repository-scale refactoring is a state-tracking and dependency problem; a live change ledger/diff context is plausibly useful. | It does not establish safe game-engine refactoring, full behavioral equivalence, or the value of a Codex `SKILL.md` by itself. Tasks are handcrafted and reference solutions are benchmark artifacts, not this project’s architecture. |
| **SWE-Refactor** | The 2026 preprint reports 1,099 developer-written Java refactorings from 18 projects, including 177 compound cases. Instances were filtered through compilation, tests, and automated refactoring detection. Reported GPT-5.1-Codex success on compound cases was 39.4%; compound/complex transformations were the main difficulty ([paper](https://arxiv.org/abs/2602.03712), submitted 2026-02-03). | Compound refactors remain risky even for a coding agent; compilation plus tests plus structural verification is stronger than textual inspection. | The paper is a preprint, its appendix said release artifacts were still “to be released” in the reviewed version, and its Java task distribution cannot set this project’s acceptance threshold. |
| **CodeTaste** | The 2026 study mines large multi-file refactorings and scores repository tests plus static data-flow checks. Agents performed substantially better when the desired refactoring was detailed than when asked to discover a human-compatible improvement from a vague focus area. A propose-then-implement decomposition improved alignment ([paper](https://arxiv.org/abs/2603.04177), submitted 2026-03-04; [research-project page](https://www.sri.inf.ethz.ch/publications/thillen2026codetaste); [code at `03cfd7252b893347ad5876e2d8678b91693aca3f`](https://github.com/logic-star-ai/codetaste/tree/03cfd7252b893347ad5876e2d8678b91693aca3f), accessed 2026-07-22). | Separate candidate proposal/review from execution; require an explicit smell, boundary, and intended transformation rather than “make this code better.” | Human historical refactor choices are not always uniquely optimal; alignment to one mined diff is not identical to maintainability or game behavior. The result does not establish autonomous discovery as safe. |
| **SkillsBench and SWE-Skills-Bench** | Sessions 5–6 record that curated skills improved aggregate results but also regressed individual tasks; most tested public SWE skills produced no pass-rate improvement, and some degraded it. Version mismatch, task conflict, and excess context were reported failure mechanisms ([SkillsBench](https://arxiv.org/abs/2602.12670); [SWE-Skills-Bench](https://arxiv.org/abs/2603.15401)). | A focused, context-matched procedure with executable feedback is worth evaluating; negative cases and a no-skill baseline are mandatory. | No inspected direct-skill benchmark isolates a post-implementation game-code simplifier or proves that adding this skill improves this repository. |

**Finding — strong caution:** The benchmark results do not support autonomous broad cleanup. They instead show that repository context, explicit instructions, state tracking, and executable verification materially affect outcomes, while compound work still fails frequently.

**Recommendation:** A future simplifier should use a **propose → preservation review → transform → verify → accept or roll back** loop. It should default to the current implementation diff or one explicitly named subsystem and limit each accepted patch to one coherent smell cluster. High-risk compound candidates should be split or refused.

### 1.3 Actual simplification-agent inspection

The behavior-bearing file and manifest of Anthropic’s `code-simplifier` plugin were inspected at commit [`b36f687171aecc8577fbdc7c70887dcd0b9c7f90`](https://github.com/anthropics/claude-plugins-official/tree/b36f687171aecc8577fbdc7c70887dcd0b9c7f90/plugins/code-simplifier):

- [`agents/code-simplifier.md`](https://github.com/anthropics/claude-plugins-official/blob/b36f687171aecc8577fbdc7c70887dcd0b9c7f90/plugins/code-simplifier/agents/code-simplifier.md), blob `05e361b4ef1b688203251989707f8a924a9ed266`;
- [`.claude-plugin/plugin.json`](https://github.com/anthropics/claude-plugins-official/blob/b36f687171aecc8577fbdc7c70887dcd0b9c7f90/plugins/code-simplifier/.claude-plugin/plugin.json), blob `e8edbae4330809cc9202951db1c9d5f27c39ed76`.

This is a Claude Code **agent/plugin artifact**, not a Codex skill, and it must not be represented as native evidence for Codex behavior.

| Inspected characteristic | Assessment for this project |
|---|---|
| Preserves exact functionality and prefers clarity over brevity | **Extract principle.** This matches the target and correctly rejects line-count optimization. |
| Defaults to recently modified code | **Extract principle.** A bounded diff is safer and easier to verify than whole-repository cleanup. |
| Warns against overly clever code, concern collapse, and removing helpful abstractions | **Extract principle.** This guards against false simplification. |
| Encodes JavaScript/TypeScript/React conventions | **Reject as reusable content.** This repository has no selected engine or production language; importing those assumptions would violate the live audit. |
| Says to operate autonomously and proactively immediately after code is written | **Reject for this workflow.** Entry requires a verified baseline, explicit allowed paths, and user-owned approval where risk is material. “Proactive” cleanup can expand an authorized implementation task. |
| Verification step only says to ensure code is simpler and functionality unchanged | **Insufficient.** It does not prescribe builds, tests, engine/editor execution, serialized-reference checks, save round trips, screenshots, performance captures, accessibility/security checks, or human gates. |
| No explicit refusal, rollback, concurrent-change, test-preservation, migration, sacred-event, provenance, schema, or knowledge-boundary contract | **Insufficient for adaptation.** These omissions are critical in this project. |
| Exact file-level reuse rights at the audited revision | **Unverified for this review.** No text is copied; exact licensing would need a separate package-level audit before adaptation. |

**Recommendation — reuse decision: extract principles only.** Do not copy or install the artifact. The future builder may independently express the bounded-scope, functionality-preservation, and clarity-over-brevity principles, but it must add the missing entry gate, invariant ledger, verification ladder, domain protections, refusal states, and evaluation fixtures.

### 1.4 Evidence limits

**Unverified:** No reviewed controlled study measures whether a Codex simplification skill improves game-code maintainability without behavior regressions. No reviewed benchmark covers serialized editor graphs, scenes/prefabs/resources, Blueprint assets, save migration, visual feel, sacred-event restrictions, or this project’s source-confidence model. No source provides a universal safe maximum for changed files, cyclomatic complexity, method length, duplication, callback count, polling interval, or performance delta.

## 2. Preconditions and entry gate

### 2.1 Phase boundary

The candidate is **post-implementation**. Session 9’s scope guard acts before and during implementation to choose the smallest complete authorized solution and interrupt unapproved expansion. This workflow begins only after that implementation has a stable, passing baseline.

**Recommendation — trigger intent:** Use only when the user or authorized workflow asks to simplify/refactor an already implemented and verified change, or asks to review a bounded existing area for a named maintainability smell. Do not trigger for initial implementation planning, feature design, architecture selection, bug diagnosis, speculative optimization, wholesale modernization, or “clean up the repo” without bounded scope and invariants.

### 2.2 Mandatory entry packet

All rows must be resolved before a write. “Unavailable but optional” is allowed only where the row’s applicability assessment says it is optional.

| Entry item | Required evidence | Failure behavior |
|---|---|---|
| Current authority | Repository root, branch/head, clean/current authority files, allowed paths, user instruction, applicable specs/schemas | Stop on stale, missing, or conflicting controlling inputs. |
| Implemented outcome | Acceptance criteria and a requirement-to-change map for the implementation being simplified | Stop if behavior is still being designed or disputed. Route bug/feature work separately. |
| Green baseline | Exact commands/tools and results for builds/tests/static checks; runtime/visual/save/performance evidence where applicable | Refuse when a required baseline is red or was never run. A simplifier must not become a disguised bug-fixer. |
| Observable behavior contract | Inputs, outputs, side effects, ordering/timing, error states, public/editor interfaces, save/schema versions, protected constraints | Stop if material behavior cannot be stated well enough to compare. |
| Stack facts | Selected engine/tool/language versions, repository conventions, generators, asset/serialization rules | Do not infer Unity, Godot, Unreal, Blender, or a language. Refuse stack-specific transformation when facts are absent. |
| Target boundary | Recently changed lines/files by default, or an explicit named subsystem; excluded files and generated/vendor/binary assets | Stop or seek approval if the candidate crosses the authorized boundary. |
| Dependency/reference map | Callers/callees, reflection/DI/registration, editor/asset references, schema/save consumers, external API consumers | Treat apparently unused code as live until hidden consumers are checked. |
| Test integrity | Pre-change test/fixture/baseline hashes or diff state; policy for any necessary test edits | Tests are read-only by default. Test changes require separate explanation and human approval. |
| Rollback point | Known prior commit or preserved patch plus commands/process to restore the candidate change without losing user work | Stop if rollback cannot be performed safely. |
| Repository safety | Status, concurrent/uncommitted work, current head, no unrelated staged changes | Do not overwrite, absorb, or “clean” another contributor’s work. |
| Required capabilities | Build/test runner, engine/editor, scene/reference validator, save fixtures, screenshot capture, profiler, security/accessibility tools as applicable | Missing required verification is a stop, not permission to claim equivalence. |

### 2.3 Current repository eligibility

**Finding:** Session 1 found no authoritative engine, production language, source code, executable schema, save format, scene/prefab/resource tree, build definition, test harness, profiler setup, or gameplay runtime at the sequence baseline. Sessions 2–9 added research reports only; no later session before this predecessor selected a production stack ([Session 1 at the predecessor](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f5b64c8996f212f99b7f118d4814b6e7192e742d/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md)).

**Project consequence:** There is currently nothing eligible for a production-code simplification run. A future skill invoked now should report “no verified implementation target” and stop. This report can define stack-neutral gates, but it cannot validate engine-specific transformations against this repository.

## 3. Smell-detection taxonomy and allowable transformations

Smells are investigation prompts, not removal orders. A candidate becomes actionable only when the agent establishes its live consumers, owner, behavioral invariants, and a verifiable simpler alternative.

| Candidate smell | Evidence to establish the candidate | Usually allowable transformation | False-positive or stop risk | Minimum focused verification |
|---|---|---|---|---|
| Duplicated logic | Semantically equivalent rules with the same authority, lifecycle, failure behavior, and change cadence | Extract a named shared function/module, or inline the simpler duplicate into an existing owner | Similar-looking sacred, source, knowledge-era, platform, or UI rules may intentionally differ | Tests for every former path; compare errors, ordering, source/confidence fields, and timing |
| Dead code | No static caller, dynamic/reflection registration, editor hook, serialized reference, asset callback, command, plugin entry, migration, save loader, or external consumer | Delete bounded unreachable code and its now-unused private imports | Reflection, dependency injection, engine magic methods, string-based callbacks, old-save migrations, editor-only entry points | Build all targets; reflection/registration scan; editor/scene load; old-save fixtures; search identifiers and serialized IDs |
| Obsolete comments | Comment contradicts current behavior or merely narrates self-evident code; version history is recoverable elsewhere | Delete or rewrite to explain invariant, rationale, source, risk, or non-obvious constraint | Provenance, uncertainty, licensing, security, sacred-event rationale, migration notes, and intentional exceptions are not clutter | Human review against authority/source record; documentation/link check |
| Unnecessary wrappers | Wrapper adds no policy, adaptation, error semantics, ownership boundary, test seam, or compatibility contract | Inline and remove wrapper; redirect callers to established owner | Wrapper may be a serialization, engine, security, platform, or test boundary | Call-site tests, API/ABI check, serialized/editor reference check, error comparison |
| Pass-through classes | Class delegates all behavior/state without adding a stable boundary or lifecycle | Collapse into the appropriate owner or an existing interface | Engine component identity, DI registration, prefab/script attachment, Blueprint subclass, public API, or future migration seam may make identity observable | Editor/asset scan; type/registration tests; API compatibility; runtime scene checks |
| Single-use abstractions | One consumer and no independent boundary, volatile decision, test seam, security/domain invariant, or approved extension | Inline interface/factory/generic layer and retain the concrete owner | “Second consumer” is not a law; one serialization/security/engine/test boundary can justify abstraction | Consumer tests; substitution/failure tests; compile and dependency graph review |
| Premature extension points | No authorized variant, plugin, platform, configuration, or current consumer | Remove unused hooks/configuration/type parameters and narrow visibility | Approved architecture, mod support, content pipeline, or platform contract may make extension current | Configuration/serialization compatibility; compile downstream consumers; human architecture gate |
| Excessive public interfaces | Public/exported members have no authorized external/editor/data consumer | Make private/internal, remove setters, narrow capability | Binary/API consumers, reflection, inspector exposure, scripting/Blueprint use, serialization and mod surfaces | Public API diff; reflection/editor checks; downstream build; save/schema compatibility |
| Excessive state duplication | Same authoritative state copied and synchronized across components | Establish one source of truth; derive/cache with explicit invalidation | Copies may represent snapshots, transactions, rollback, network boundaries, save versions, or in-world versus player-codex views | Transition/order tests; save round trip; concurrency checks; knowledge-boundary review |
| Redundant files | File has no distinct owner, generated role, platform boundary, asset identity, or review/permission function | Merge into appropriate module and delete file | File count is not complexity; engine metadata/GUIDs, partial classes, generated artifacts, schemas, migrations, licensing, or ownership can require separation | Build/import; metadata/GUID/reference checks; license/provenance review; targeted tests |
| Redundant dependencies | Package duplicates authorized platform capability or has no live use | Remove import/package/config/lock entry using the approved package manager | Transitive/runtime/editor/build plugins may be used indirectly; bespoke replacement may be riskier | Clean install/build/export; lockfile diff; license/security scan; runtime smoke test |
| Repeated conversions | Same format/type conversion repeats at unstable boundaries | Normalize once at a well-named boundary, or remove round trips | Precision, locale, encoding, units, canonicalization, validation, or distinct knowledge/source representations may differ | Boundary/property tests; round-trip and malformed-input tests; compare persisted data |
| Needlessly indirect data flow | Value passes through layers that add no policy or ownership and obscure origin | Connect current producer to appropriate consumer through a clear boundary; remove relays | Relays may enforce authorization, provenance, threading, event order, instrumentation, or engine lifecycle | Data-flow trace; side-effect/order tests; logging/security review; runtime check |
| Oversized methods/systems | Multiple independent reasons to change, hidden invariants, or hard-to-test branches—not a numeric line threshold | Extract cohesive named operations, move behavior to its data owner, split phases | Extraction can multiply state coupling, callbacks, allocations, or public surfaces | Branch/error tests; state-transition tests; performance/profile comparison; human clarity review |
| Unnecessary engine callbacks | Callback exists but does no required engine/lifecycle work or can be disabled/event-driven | Remove/disable callback or register only when needed | Callback name may be engine-discovered; ordering, physics frame, editor mode, or enable/disable lifecycle is observable | Engine runtime/editor test across lifecycle; timing/order capture; build target check |
| Per-frame allocations | Profiler shows allocations on a frame-critical path and the target budget is affected | Reuse buffers, cache immutable results, choose allocation-free established API | Speculative micro-optimization can reduce clarity, retain memory, or change ownership/thread safety | Before/after target-device profile; functional/visual tests; memory lifetime check |
| Avoidable polling | Measured recurring check watches infrequent state that has a reliable event/callback | Replace with event/signal/callback or reduce interval | Events can fire too frequently, be lost, reorder work, leak subscriptions, or be less efficient than batching | Timing/order/load tests; subscription lifecycle; target-device profile; pause/resume/scene transition tests |
| Excessive scene/prefab/resource indirection | Indirection adds no reusable asset boundary and hides ownership/reference flow | Flatten or consolidate only with editor-aware reference-preserving tools | Overrides, inheritance, instancing, streaming, localization, asset reuse, designers’ workflows, GUIDs, or linked-library semantics may depend on it | Editor open/import; reference/override diff; scene play; screenshots; build/export; asset-owner approval |
| Overly generic schemas | Generic fields/unions obscure current domain invariants, validation, or source semantics | Narrow with approved migration to explicit domain types/fields | Schema changes are not ordinary cleanup; stored content, tools, saves, mods, and provenance may depend on old form | Schema validator; migration; reference scan; backward/forward save/data fixtures; human schema approval |
| Complexity introduced only to satisfy tests | Production branch/type/name exists solely because a test asserts implementation detail rather than behavior | Improve the production design while preserving valid behavioral tests; replace invalid structural test only through separate approval | Agent may weaken tests to bless its preferred implementation; structural tests may enforce security, schema, performance, or integration contracts | Preserve original test suite; explain each test edit; mutation/negative tests; independent review |

### 3.1 Transformation rule

**Recommendation:** Approve a transformation only when all seven statements are true:

1. The smell is demonstrated in the current repository, not inferred from a generic style guide.
2. The affected behavior and hidden consumers have been mapped.
3. The proposed change reduces conceptual indirection, duplication, state, or maintenance burden **now**.
4. It does not add a new unrelated responsibility or vague general abstraction.
5. Every affected invariant has a matching verification method.
6. The patch stays within authorized paths and can be rolled back independently.
7. A qualified human can explain why the result is clearer without relying on line/file counts.

If the first six pass but the clarity judgment is disputed, present the candidate and do not modify. If behavior must change to achieve the result, reclassify it as feature/bug/architecture work and leave the simplification phase.

## 4. Preservation invariants and preservation case

### 4.1 Invariant classes

| Invariant class | Examples that must remain equivalent unless explicitly out of scope | Evidence expected |
|---|---|---|
| Functional outputs | Return values, rendered/player-visible results, quest/state transitions, inventory/economy effects | Unit/integration/runtime assertions and controlled play paths |
| Inputs and compatibility | Accepted inputs, malformed-input behavior, public/editor API, commands, configuration, plugins/mods | Contract tests, downstream builds, API diff, invalid-input tests |
| Side effects and order | Writes, events, callbacks, notifications, transaction order, random-seed consumption, threading | Event/state traces, integration tests, race/order checks |
| Timing and frame semantics | Physics versus idle update, cooldowns, animation timing, event frequency, frame pacing | Engine trace, deterministic fixture, target-device runtime comparison |
| Error handling and recovery | Validation, exceptions/statuses, retries, fallback, user messages, rollback, partial-failure behavior | Negative/fault-injection tests; log comparison; recovery exercise |
| Logging and observability | Security/audit events, diagnostics, classifications, telemetry fields, no sensitive-data expansion | Log assertions and human operations/security review. OWASP says security-event logging should be included and verified through review/testing ([Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html), living guidance accessed 2026-07-22). |
| Security and privacy | Authorization, trust boundaries, input validation, secret handling, least privilege, data retention | Security tests/static analysis/threat review; OWASP ASVS or current project standard where applicable ([OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/), accessed 2026-07-22) |
| Accessibility and control | Input modalities, remapping, focus/navigation, captions/status communication, readable semantics, timing options | Automated checks plus keyboard/controller/assistive human tests as applicable. WCAG 2.2 explicitly combines automated and human evaluation and supplies testable criteria for web UI ([W3C WCAG 2.2](https://www.w3.org/TR/2024/REC-WCAG22-20241212/), Recommendation 2024-12-12); engine/platform standards may additionally apply. |
| Serialization and persistence | Field/type/ID identity, schema version, reference graph, old saves, round-trip fidelity, migrations | Old/current/new fixture matrix; serialized-reference scan; save/load round trip; editor reload |
| Runtime/editor/assets | Scene/prefab/resource/Blueprint attachment, override graph, imported asset metadata, editor-only behavior | Editor open/reimport, scene/resource validation, build/export, controlled runtime and screenshots |
| Performance and resources | Accepted budgets for frame time, allocation, load time, memory, build size, network/storage | Same-hardware before/after captures using the selected engine profiler; no speculative claim |
| Tests and evaluators | Existing assertions, fixtures, screenshot baselines, prohibited-behavior checks, coverage purpose | Test diff defaults to none; independent review of any authorized test change |
| Project authority | User decisions, roles, approved architecture/spec/schema, file discipline | Authority-to-diff trace and reviewer sign-off |
| Biblical/source integrity | Scripture/interpretation/reconstruction/tradition/invention distinctions, citations, confidence, disputed status, paraphrase labels | Schema/content validator plus Scripture/history reviewer |
| Sacred-event protection | Fixed outcomes, protected figures, prohibited attack/exploitation paths, player-as-witness agency | Negative runtime tests and human theological/design approval; never traded against aggregate score |
| Chronology and knowledge | Era-appropriate in-world knowledge, player-facing codex separation, no later-Scripture leakage | Timeline/knowledge fixtures and domain review |
| Provenance and licensing | Source IDs, confidence, license/attribution, change records, asset origins | Provenance audit; citations/notices unchanged or intentionally migrated |

### 4.2 Preservation record

**Recommendation:** Before the first edit, create a temporary or implementation-record table:

| Invariant ID | Behavior/constraint | Baseline evidence | Candidate impact | Verification to rerun | Result | Reviewer |
|---|---|---|---|---|---|---|

The record is not a substitute for tests. It exposes untested claims and prevents an agent from forgetting behavior across a multi-file trajectory, directly addressing the state-tracking problem documented by RefactorBench. For trivial local transformations, the record may be a concise checklist in the task trace rather than a new repository file.

### 4.3 What constitutes the preservation case

An accepted result should contain all of the following:

1. **Stable baseline:** exact pre-change SHA/diff, environment and passed checks.
2. **Named transformation:** smell, intended owner, allowed files, and non-goals.
3. **Invariant coverage:** every affected class mapped to a check or a disclosed gap.
4. **Small-step trace:** one coherent transformation at a time, with intermediate checks for compound work.
5. **Behavioral evidence:** tests/runtime/save/visual/performance/security/accessibility layers as applicable.
6. **Structural evidence:** the smell is genuinely reduced without transferring complexity elsewhere.
7. **No evaluator gaming:** tests and baselines unchanged by default; any change separately justified and approved.
8. **Human acceptance:** maintainability and domain-specific judgments approved by the relevant owner.
9. **Reversibility:** known rollback action, with no loss of concurrent work.

**Unverified:** A passing preservation case still cannot establish every unobserved execution. Its purpose is to make assurance explicit, proportional, reproducible, and honest.

## 5. Engine, serialization, scene, and save-data hazards

### 5.1 Current-stack rule

**Finding:** The repository has not selected Unity, Godot, Unreal, Blender, or another production stack. The examples below are conditional hazard evidence, not recommendations or implied choices.

| Conditional stack | First-party hazard evidence | Simplification consequence |
|---|---|---|
| Unity 6 | Unity serializes script fields into scenes, prefabs, and assets; renaming a serialized field without a migration attribute can lose the stored value. `FormerlySerializedAsAttribute` exists specifically to preserve a field’s serialized value across renaming ([Unity 6 API](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Serialization.FormerlySerializedAsAttribute.html); [serialization manual](https://docs.unity3d.com/6000.0/Documentation/Manual/script-serialization-how-unity-uses.html), accessed 2026-07-22). Prefab instances can carry overrides while remaining linked to a prefab asset ([Unity 6 prefab overrides](https://docs.unity3d.com/6000.0/Documentation/Manual/prefabs-override.html)). | Field/class/file deletion, visibility changes, wrapper removal, and prefab flattening need serialized-field and GUID/reference audits, migrations, editor reload, prefab-override comparison, scene play, and build validation. Text search alone is insufficient. |
| Godot 4.6/stable | Exported members are saved with their scene/resource; exported resources become scene dependencies. Save logic is project-specific; Godot warns that nested persisted objects can create invalid `NodePath`s and that JSON lacks several engine types. Binary save includes only properties marked for storage ([C# exported properties](https://docs.godotengine.org/en/stable/tutorials/scripting/c_sharp/c_sharp_exports.html); [GDScript exports](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_exports.html); [saving games 4.6](https://docs.godotengine.org/en/4.6/tutorials/io/saving_games.html)). | Renaming/removing exported members, moving nodes, collapsing resources, or changing save ownership can alter editor data and old saves. Require scene/resource reload, exported-property/reference scan, nested path tests, and old/current save fixtures. |
| Unreal Engine 5.8 | Unreal’s Core Redirects remap renamed classes, enums, functions, packages, properties, and structs while loading assets; the documentation warns that simple renaming/recompilation can cause data loss because existing assets no longer recognize members ([Epic, Core Redirects](https://dev.epicgames.com/documentation/en-us/unreal-engine/core-redirects-in-unreal-engine), UE 5.8, accessed 2026-07-22). | A class/property/function/struct rename or Blueprint/native consolidation needs redirect/migration planning, asset load/resave checks, Blueprint compile, cooked build, and save compatibility. “Pass-through” reflected types may still be asset identities. |
| Blender 5.x as an asset tool | Blender data-blocks are shared/referenced and linked libraries may use override hierarchies. Resyncing overrides after relationship changes can delete edited overrides; broken hierarchies may require forceful rebuild with possible override loss ([Blender 5.0 data-blocks](https://docs.blender.org/manual/en/5.0/files/data_blocks.html); [library overrides](https://docs.blender.org/manual/en/5.0/files/linked_libraries/library_overrides.html), accessed 2026-07-22). | Asset “deduplication,” hierarchy flattening, data-block deletion, or linked-library changes require DCC-level reference/override inspection, visual comparison, export/reimport, license/provenance review, and artist approval. |

### 5.2 Save and schema compatibility matrix

For every persisted or externally consumed change, test at least:

| Producer | Consumer | Required result |
|---|---|---|
| Old released/current-authoritative save | Simplified build | Loads without loss, silent defaulting, source/confidence erasure, or sacred/chronology state corruption |
| Current pre-simplification build | Save fixture | Establishes baseline and exact version/metadata |
| Simplified build | New save | Round trips deterministically within documented tolerances |
| Simplified build | Prior/current tools, editor, validators | Remains readable or uses an approved migration/compatibility policy |
| Failed/interrupted migration | Recovery path | Leaves recoverable original or fails closed with actionable error |

**Recommendation:** Schema narrowing, ID changes, type consolidation, migration removal, and save-format changes should default to **refuse as ordinary simplification**. They may proceed only as a separately authorized migration with a versioned schema, fixtures, recovery plan, and schema-owner approval. Old loaders that look unused are not dead code until the supported-save window proves them obsolete.

## 6. Verification ladder, workflow, and rollback

### 6.1 Ordered workflow

1. **Preflight:** load authority, target, head/status, baseline, stack facts, allowed paths, and rollback point.
2. **Propose:** name one smell cluster, evidence, intended transformation, invariants, affected checks, and expected clarity gain.
3. **Gate:** human/owner accepts high-risk candidate; otherwise proceed only for a local, obviously reversible transformation whose required checks are available.
4. **Transform:** apply the smallest coherent change. Do not change behavior, tests, schemas, saves, assets, or public interfaces outside the accepted proposal.
5. **Verify locally:** compile/type/static/unit checks for immediate feedback.
6. **Verify integrations:** integration/scene/editor/save/runtime/visual/performance/security/accessibility checks as applicable.
7. **Review the diff:** inspect semantic change, hidden consumers, errors/logs, tests, generated artifacts, dependencies, and protected constraints.
8. **Accept or roll back:** accept only if all required layers pass and human clarity improves; otherwise restore just the simplification change and retain failure evidence.

### 6.2 Verification ladder

| Level | Check | Pass condition | Stop/rollback condition |
|---:|---|---|---|
| 0 | Authority, scope, head/status, baseline, rollback | Current and complete; only authorized target | Conflict, concurrent overlap, red/missing required baseline, no safe rollback |
| 1 | Parse/format/type/static analysis and dependency/reference search | No new error/warning; hidden consumers investigated | New diagnostic, unresolved dynamic/editor reference, unauthorized dependency change |
| 2 | Build/compile/import/export | All supported targets selected by current authority pass | Any required target fails or generated output changes unexpectedly |
| 3 | Existing unit, integration, contract, negative, and scene tests | Original suite passes unchanged; new behavior was not introduced | Test failure, weakening/deletion, altered fixture to bless patch |
| 4 | Serialization/schema/reference/save | Editor references intact; old/current save matrix and round trips pass; migrations remain valid | Missing data, orphaned asset, defaulted field, broken Blueprint/resource/prefab/scene, invalid old save |
| 5 | Engine execution and controlled play | Same player-visible behavior, state transitions, controls, errors, and sacred restrictions | Runtime exception, timing/order difference, prohibited interaction, feel/control regression |
| 6 | Visual/audio comparison | Approved screenshots/captures and manual traversal show no unintended change | Layout, art, camera, animation, subtitle/audio, sacred representation, or accessibility difference |
| 7 | Performance/resource capture when relevant | Same target hardware/scenario; no budget regression; claimed improvement measured | Regression, uncontrolled comparison, or speculative optimization without baseline |
| 8 | Security, privacy, accessibility, provenance and domain review | Applicable threat/accessibility/source/sacred/knowledge checks pass | Any protection, audit trail, source/confidence field, license, knowledge, or human-access path is weakened |
| 9 | Final diff and qualified human approval | Clearer ownership/data flow, smell removed, all gaps visible, authorized paths only | Reviewer cannot explain net clarity gain; compound uncertainty remains; required check unavailable |

“Not applicable” requires a reason tied to the target. “Could not run” is never equivalent to “passed.” A lower level cannot compensate for a failed higher level, and an aggregate score cannot compensate for one sacred-event, provenance, schema, security, or save-compatibility violation.

### 6.3 Performance candidates

**Finding:** Unity provides frame-level allocation evidence through its CPU and Memory profilers and advises profiling a development build on the target platform because Editor behavior differs ([Unity, tracking garbage-collection allocations](https://docs.unity3d.com/6000.0/Documentation/Manual/performance-track-garbage-collection.html), accessed 2026-07-22). Godot’s optimization guidance says measurement is the most important first step and distinguishes persistent per-frame cost, spikes, and load-time cost ([Godot 4.6, general optimization](https://docs.godotengine.org/en/4.6/tutorials/performance/general_optimization.html)). Epic likewise documents Unreal Insights and target-specific frame/memory profiling; its CPU guidance says occasional work polled on Tick can waste CPU but also notes cases where callbacks can be less efficient ([Unreal performance profiling](https://dev.epicgames.com/documentation/en-us/unreal-engine/introduction-to-performance-profiling-and-configuration-in-unreal-engine); [Tick versus callbacks](https://dev.epicgames.com/documentation/en-us/unreal-engine/common-memory-and-cpu-performance-considerations-in-unreal-engine), UE 5.8).

**Recommendation:** “Remove polling,” “remove callback,” “avoid allocation,” and “cache it” are hypotheses. Require a representative capture before and after on the authoritative target. Preserve correctness, lifecycle, memory ownership, and clarity even when a metric improves.

### 6.4 Rollback contract

- Preserve the pre-simplification SHA/diff and uncommitted user work.
- Make each transformation independently revertible; do not mix cleanup with a feature fix.
- If a required check fails, stop adding changes. Revert the candidate transformation before trying another hypothesis unless the user authorizes diagnosis.
- For migrations, preserve original fixtures and a recovery copy; destructive forward-only migration is outside ordinary simplification.
- Report the failed candidate, failed invariant/check, files restored, and remaining baseline state. Do not hide unsuccessful attempts or leave disabled tests.

## 7. Diff and human-review contract

### 7.1 Required diff review

The reviewer should receive:

1. target and accepted transformation;
2. pre-change head/baseline and post-change diff;
3. invariant-to-verification results;
4. public/API/reflection/editor/serialized/save/schema/dependency changes, each explicitly “none” or explained;
5. tests/fixtures/baselines changed, normally “none”;
6. errors/logging/security/accessibility/provenance/protected-domain impact;
7. performance evidence only when a performance claim is made;
8. unavailable checks and reduced assurance;
9. rollback procedure; and
10. the net clarity argument.

Review questions:

- Did complexity disappear, or move into a denser function, generic schema, event graph, configuration, or hidden convention?
- Can a maintainer find the authoritative state and failure path more easily?
- Does every remaining abstraction name a real boundary or invariant?
- Did any “unused” identity have a dynamic, editor, serialized, migration, asset, test, or external consumer?
- Are comments about **why**, source, confidence, security, sacred restrictions, or compatibility preserved?
- Are public surfaces narrower without breaking legitimate editor/tool/content consumers?
- Do old saves, scenes, resources, prefabs, Blueprints, and imported assets remain usable where applicable?
- Are Scripture/source categories, historical uncertainty, in-world/codex separation, and sacred-event semantics still explicit?
- Were tests used as evidence rather than rewritten as permission?

### 7.2 Human approval ownership

| Change class | Required reviewer/gate |
|---|---|
| Local private implementation with complete automated coverage | Code owner or qualified engineer; lightweight approval |
| Public API, architecture boundary, dependency, concurrency, performance-sensitive path | Systems/architecture owner and evidence review |
| Schema, stable ID, persisted content, save migration | Schema/content owner plus systems engineer; user approval for compatibility policy |
| Scene/prefab/resource/Blueprint/asset graph | Engine/content/technical-art owner with editor/runtime evidence |
| UI/control/accessibility | UI/accessibility reviewer plus representative input testing |
| Security/auth/privacy/logging | Security owner or qualified review; threat/negative evidence |
| Scripture, chronology, history, provenance, knowledge boundary | Scripture/theology and/or historical reviewer as applicable |
| Sacred event or protected figure | User/Creative Director and appropriate domain reviewers; zero-tolerance prohibited-path tests |

The simplifier may recommend but must not self-approve a material architecture, schema, sacred, compatibility, or rights decision.

## 8. Refusal and stopping conditions

The future workflow should refuse before editing when:

1. the implementation is incomplete, behavior-changing, or not verified;
2. required tests/build/runtime/editor/save fixtures are missing or failing;
3. the target engine/language/tool/schema/version is unknown but the transformation depends on it;
4. observable behavior, supported save window, public API, or acceptance criteria are materially disputed;
5. the request is unbounded (“simplify everything”) without target, invariants, and review capacity;
6. no safe rollback point exists or concurrent/uncommitted work overlaps the target;
7. the candidate touches generated, vendored, third-party, binary, imported, or licensed assets without the authoritative regeneration/provenance workflow;
8. suspected dead code may be reached through reflection, editor/engine callbacks, serialization, assets, commands, migrations, old saves, plugins, or external consumers that cannot be checked;
9. the result would require a behavior change, bug fix, feature, schema migration, architecture decision, dependency replacement, or speculative optimization not separately authorized;
10. simplification would remove or generalize sacred-event, Scripture/source, historical-confidence, chronology, knowledge-separation, schema, security, accessibility, error, logging, test, or provenance controls;
11. the only objective is fewer lines, files, classes, or callbacks; or
12. the exact package/tool/license provenance needed for reuse is unresolved.

Stop during execution and roll back the candidate when:

- any required verification layer fails or produces a new warning;
- a hidden consumer, editor/asset reference, save incompatibility, timing/order difference, or visual change is discovered;
- a test, fixture, screenshot, schema, or error path must be weakened to proceed;
- the change crosses the allowed path or grows into a compound refactor not reviewed at the gate;
- the profiler does not confirm the alleged bottleneck/improvement;
- clarity becomes subjective or reviewers disagree about ownership/invariants;
- current authority/head changes under the work; or
- a protected-constraint violation appears, even if all general tests pass.

**Recommendation:** A valid result may be “no safe simplification identified.” Refusal is success when the preservation case cannot be built.

## 9. Evaluation scenarios and metrics

These scenarios are proposed fixtures for Session 15/16; they are not evidence that the candidate skill works.

| ID | Scenario | Expected behavior | Critical failure caught |
|---:|---|---|---|
| 1 | Recently implemented private helper duplicates another helper with identical tests and ownership | Propose one bounded consolidation, preserve errors, run all callers, show net clarity | Blind duplication removal or unrelated cleanup |
| 2 | “Unused” Unity field was renamed and is populated in prefabs | Refuse deletion; require serialization/reference evidence and approved migration | Serialized data loss |
| 3 | Unreal pass-through reflected class is parent of Blueprint assets | Treat identity as observable; require asset graph/Core Redirect plan or refuse | Blueprint/asset breakage |
| 4 | Godot node relay looks redundant but persisted child paths depend on hierarchy | Require scene/save fixtures; do not reparent without path/owner migration | Invalid NodePath/old save |
| 5 | A generic `protected` flag encodes sacred-event restrictions | Reject generic compression; retain explicit sacred semantics and prohibited-interaction tests | Theological safeguard erasure |
| 6 | Source and confidence fields appear unused by runtime UI | Preserve them; verify codex/research/tool consumers and schema authority | Provenance/confidence loss |
| 7 | Error wrapper logs validation failures before returning a status | Do not inline away log/error semantics; compare fault injection and security logs | Weakened recovery/observability |
| 8 | Repeated allocation in a per-frame path is suspected but unprofiled | Ask for/collect target capture; refuse speculative caching; verify lifecycle if measured | Speculative optimization or memory leak |
| 9 | Polling can be replaced with an event, but the event may fire several times per frame | Propose both paths, measure, test order/subscription lifecycle, accept only with evidence | Performance regression/race |
| 10 | Tests require a production getter used nowhere else | Preserve behavioral assertions; separately review whether the test is overcoupled; no silent test edit | Evaluator gaming |
| 11 | Two data models look duplicated but represent era-limited in-world text and modern codex text | Keep separation or factor only truly shared representation without knowledge leakage | Chronology/knowledge collapse |
| 12 | File-count target would merge schema, runtime, and migration ownership | Reject false simplification despite fewer files | Concern collapse and migration loss |
| 13 | Local rename has complete language-tool support and no editor/serialized surface | Apply as one atomic refactor, compile/test/search, report concise result | Process overburden for low risk |
| 14 | Simplifier invoked before implementation tests pass | Refuse and route back to implementation/diagnosis | Phase conflation |
| 15 | Same patch improves unit tests but changes camera timing and subtitle focus in runtime | Fail runtime/visual/accessibility layers and roll back | Test-only false confidence |

### 9.1 Metrics

- **Behavior-preservation pass rate:** scenario passes every applicable predeclared invariant.
- **Protected-constraint violation rate:** sacred, biblical/source, historical, chronology, knowledge, schema, provenance, security, or accessibility violation. Acceptance floor: zero violations.
- **Save/reference survival rate:** old/current save fixtures and serialized/editor references preserved where applicable.
- **Verification integrity:** required checks actually run; no false “passed,” baseline contamination, test weakening, or hidden unavailable tool.
- **Scope precision:** changed paths attributable to the accepted transformation; unrelated-change rate.
- **Candidate precision:** proposed smells accepted by qualified reviewers; false-simplification rate.
- **Candidate recall:** reviewer-identified safe material simplifications also found, without incentivizing risky volume.
- **Clarity/maintainability judgment:** blinded or clean-context human rating of ownership, data flow, failure visibility, and ease of change—not line count.
- **Complexity displacement:** public states/interfaces/configuration/callbacks/dependencies added elsewhere while the target shrinks.
- **Regression and rollback rate:** failed candidates, cause, successful restoration, and residual damage.
- **Performance validity:** before/after target capture for each performance claim, with noise/tolerance stated.
- **Efficiency:** tokens, tool calls, wall time, review time, and user interruptions versus the same workflow without the candidate skill.
- **Trigger quality:** relevant explicit/implicit activation, near-miss nonactivation, and correct refusal before green baseline.
- **Test stability:** count and nature of test/fixture/baseline changes; unexplained change is a failure.

Evaluate the candidate against a matched no-skill/current-workflow baseline in clean contexts, retain failed runs, and separate discovery quality from transformation quality. Repeat stochastic agent runs where Session 15 requires them. Report scenario-level results; an average improvement cannot cancel a protected failure.

**Unverified:** No evidence-backed universal numerical threshold exists for acceptable complexity reduction, reviewer agreement, task count, token overhead, performance noise, or refactoring size. Session 15 must set project-specific thresholds and zero-tolerance floors.

## 10. Future skill-builder requirements

If a later skill-builder is asked to create a post-implementation simplification skill, it should classify the following as mandatory unless Session 16 supplies a stronger authority decision:

1. **One coherent phase:** post-implementation, behavior-preserving cleanup only; exclude initial planning, feature work, bug fixing, migration design, and final architecture.
2. **Precise invocation:** trigger on explicit simplification/refactoring of verified code or a named smell; default to recent diff; include near-miss exclusions and consider explicit-only invocation for high-impact work.
3. **Live authority preflight:** read current user task, Master Protocol, repository instructions, approved specs/schemas, stack versions, and target history. Do not duplicate controlling policy into a stale skill body.
4. **Green entry gate:** require implemented acceptance, exact passing baseline, behavior contract, allowed paths, test integrity, capability preflight, and rollback point.
5. **Current-stack honesty:** no Unity/Godot/Unreal/Blender/language-specific procedure until the repository selects and versions it; route conditional references after selection.
6. **Smell evidence:** include all categories in Section 3 as heuristics with hidden-consumer and false-positive tests; no numeric smell is an automatic edit.
7. **Transformation gate:** propose first, map invariants and verification, obtain material approval, then change one coherent concern at a time.
8. **Preservation ledger:** functional, API, side-effect/order, error/log, test, serialization/save/editor/asset, performance, accessibility/security, authority, sacred/source/chronology/knowledge/provenance invariants as applicable.
9. **Read-only tests by default:** never modify tests, fixtures, screenshots, or acceptance to make a patch pass; separately gate any demonstrably obsolete structural test.
10. **Engine/save safeguards:** detect reflection/registration/editor callbacks, GUIDs/IDs, scene/prefab/resource/Blueprint links, schema versions, migrations, and old-save consumers before declaring code dead or a wrapper redundant.
11. **Verification ladder:** require Levels 0–9 as applicable, name checks actually run, explain “not applicable,” and stop on missing required capability.
12. **Project protections:** explicit never-remove checks for witness premise, sacred-event outcomes/restrictions, Scripture/source categories, confidence/uncertainty, chronology, in-world/codex separation, stable IDs, schema-first discipline, and provenance/license records.
13. **Error/security/accessibility contract:** preserve validation, authorization, privacy, diagnostics, audit/security logging, failure recovery, controls, focus/status communication, and relevant platform standards.
14. **Measured performance only:** prohibit speculative optimization; require same-scenario/target before-and-after evidence for callback, polling, allocation, caching, memory, load, or frame claims.
15. **Diff and human gate:** produce the contract in Section 7, route domain-sensitive changes to appropriate owners, and allow “no safe simplification.”
16. **Refusal and rollback:** encode all Section 8 states; fail closed; restore only the candidate change without discarding concurrent work; report failures visibly.
17. **Scope-guard composition:** declare phase order `scope guard → implementation/verification → simplification proposal → simplification verification`; never assume undocumented automatic skill precedence.
18. **No line/file optimization:** evaluate conceptual ownership, indirection, state, public surface, dependencies, failure visibility, and change cost; explicitly reject code golf and concern collapse.
19. **Evaluation package:** positive, near-miss, false-positive, hidden-reference, save/serialization, visual/runtime, security/accessibility, sacred/provenance, red-baseline, missing-tool, concurrent-change, and rollback fixtures from Section 9.
20. **Baseline comparison:** compare with no skill/current workflow using scenario-level preservation, clarity, false-simplification, scope, efficiency, and zero-tolerance protected metrics.
21. **Maintenance triggers:** reevaluate when the Master Protocol, engine/tool versions, schema/save policy, architecture, Codex behavior, dependencies, platform requirements, or a production/fixture failure changes.
22. **Package economy and safety:** keep the primary `SKILL.md` concise; add references only for selected-stack hazard procedures; add scripts only when deterministic, necessary, inspected, permission-bounded, and independently validated.
23. **Provenance:** record all external ideas/files by source, date, commit, license, and adaptation decision; do not copy the Anthropic agent without a separate rights review.
24. **No catalog side effect:** define this candidate’s contract only; do not choose or register the project’s final skill catalog.

**Recommendation — feasibility:** Proceed later only as an evaluated candidate. The recurring workflow and structured gates fit a skill, but permanent project protections belong in higher authority plus schemas, validators, runtime tests, and human review. The skill should operationalize those live controls, not become their only carrier.

**Unverified decisions deferred to Sessions 14–16:** explicit-only versus implicit invocation; whether simplification should be a separate skill or a verified workflow phase selected by a router; exact companion/conflict declarations; numeric evaluation thresholds; maintenance interval; selected-stack references/scripts; and whether the project’s future test infrastructure can supply sufficient behavior evidence at acceptable cost.

## 11. Source appendix

### 11.1 Project authority and predecessor reports

All project links are pinned to Session 10 predecessor commit [`f5b64c8996f212f99b7f118d4814b6e7192e742d`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/f5b64c8996f212f99b7f118d4814b6e7192e742d), inspected 2026-07-22.

- [The Bible Video Game Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f5b64c8996f212f99b7f118d4814b6e7192e742d/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) — controlling identity, authority, role boundaries, sacred-event protection, chronology/knowledge separation, Scripture/codex rules, schema-first discipline, and file rules.
- [Session 1: Project Context and Authority Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f5b64c8996f212f99b7f118d4814b6e7192e742d/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md) — verified absence of authoritative production stack, code, schema, assets, build, tests, saves, and validation infrastructure.
- [Session 3: Current Codex Skill Capability Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f5b64c8996f212f99b7f118d4814b6e7192e742d/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md) — current repository-local skill model, capability/permission boundary, progressive disclosure, and unresolved composition behavior.
- [Session 4: Effective Skill Anatomy and Authoring Principles](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f5b64c8996f212f99b7f118d4814b6e7192e742d/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md) — preflight, checkpoints, output/stop contracts, live authority, and evaluation design.
- [Session 5: Demonstrated Skill Success Evidence](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f5b64c8996f212f99b7f118d4814b6e7192e742d/00_ADMIN/Research/LLM_Skills/05_Demonstrated_Skill_Success_Evidence.md) — positive evidence ledger, confounders, skill audits, and project transfer limits.
- [Session 6: Skill Failure, Security, and Maintenance Risks](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f5b64c8996f212f99b7f118d4814b6e7192e742d/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md) — line-count failure, test gaming, error/log suppression, safety, staleness, intake, and future safeguards.
- [Session 9: Scope-Guard and Minimal-Implementation Skill Analysis](https://github.com/Degrading1919/The_Bible_Video_Game/blob/f5b64c8996f212f99b7f118d4814b6e7192e742d/00_ADMIN/Research/LLM_Skills/09_Scope_Guard_Skill_Analysis.md) — pre-implementation flexible minimalism and the phase boundary used here.

### 11.2 LLM skill and refactoring-agent evidence

- Gautam et al., [“RefactorBench: Evaluating Stateful Reasoning in Language Agents Through Code”](https://openreview.net/pdf?id=ZjsHNRxH2Q), ICLR 2025; [Microsoft repository at `210b2d15a373ad265aa721f70199c9962d7de069`](https://github.com/microsoft/RefactorBench/tree/210b2d15a373ad265aa721f70199c9962d7de069), commit dated 2025-07-11, accessed 2026-07-22.
- Xu et al., [“SWE-Refactor: A Repository-Level Benchmark for Real-World LLM-Based Code Refactoring”](https://arxiv.org/abs/2602.03712), arXiv:2602.03712, submitted 2026-02-03; preprint and artifact-release limitation noted above.
- Thillen et al., [“CodeTaste: Can LLMs Generate Human-Level Code Refactorings?”](https://arxiv.org/abs/2603.04177), arXiv:2603.04177, submitted 2026-03-04; [project page](https://www.sri.inf.ethz.ch/publications/thillen2026codetaste); [code repository at `03cfd7252b893347ad5876e2d8678b91693aca3f`](https://github.com/logic-star-ai/codetaste/tree/03cfd7252b893347ad5876e2d8678b91693aca3f), accessed 2026-07-22.
- BenchFlow AI et al., [SkillsBench](https://arxiv.org/abs/2602.12670), submitted 2026-02-13; direct controlled skill evidence with regressions and transfer limitations documented in Sessions 5–6.
- GeniusHTX et al., [SWE-Skills-Bench](https://arxiv.org/abs/2603.15401), submitted 2026-03-16; preliminary direct SWE-skill evidence documented in Sessions 5–6.
- Anthropic, [`code-simplifier` plugin at `b36f687171aecc8577fbdc7c70887dcd0b9c7f90`](https://github.com/anthropics/claude-plugins-official/tree/b36f687171aecc8577fbdc7c70887dcd0b9c7f90/plugins/code-simplifier), inspected behavior-bearing [agent file](https://github.com/anthropics/claude-plugins-official/blob/b36f687171aecc8577fbdc7c70887dcd0b9c7f90/plugins/code-simplifier/agents/code-simplifier.md) and [manifest](https://github.com/anthropics/claude-plugins-official/blob/b36f687171aecc8577fbdc7c70887dcd0b9c7f90/plugins/code-simplifier/.claude-plugin/plugin.json), accessed 2026-07-22. Platform is Claude Code, not Codex; no file reuse is authorized.

### 11.3 Engineering, review, security, and accessibility

- Martin Fowler, [“Refactoring”](https://martinfowler.com/bliki/Refactoring.html), updated 2019-05-20; [Refactoring catalog](https://refactoring.com/catalog/), accessed 2026-07-22.
- Google, [“Small CLs”](https://google.github.io/eng-practices/review/developer/small-cls.html), first-party engineering practice accessed 2026-07-22.
- OWASP Foundation, [Application Security Verification Standard](https://owasp.org/www-project-application-security-verification-standard/) and [Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html), living sources accessed 2026-07-22.
- W3C, [Web Content Accessibility Guidelines (WCAG) 2.2](https://www.w3.org/TR/2024/REC-WCAG22-20241212/), Recommendation dated 2024-12-12. It is directly applicable to web content and provides transferable accessibility-verification principles; it is not asserted as the only standard for a future native game.

### 11.4 Conditional engine and asset-tool sources

- Unity Technologies, [Script serialization](https://docs.unity3d.com/6000.0/Documentation/Manual/script-serialization-how-unity-uses.html), [`FormerlySerializedAsAttribute`](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Serialization.FormerlySerializedAsAttribute.html), [prefab overrides](https://docs.unity3d.com/6000.0/Documentation/Manual/prefabs-override.html), and [tracking GC allocations](https://docs.unity3d.com/6000.0/Documentation/Manual/performance-track-garbage-collection.html), Unity 6/6000.0, accessed 2026-07-22.
- Godot Engine, [C# exported properties](https://docs.godotengine.org/en/stable/tutorials/scripting/c_sharp/c_sharp_exports.html), [GDScript exported properties](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_exports.html), [Saving games](https://docs.godotengine.org/en/4.6/tutorials/io/saving_games.html), and [General optimization](https://docs.godotengine.org/en/4.6/tutorials/performance/general_optimization.html), stable/4.6 documentation accessed 2026-07-22.
- Epic Games, [Core Redirects](https://dev.epicgames.com/documentation/en-us/unreal-engine/core-redirects-in-unreal-engine), [Performance profiling](https://dev.epicgames.com/documentation/en-us/unreal-engine/introduction-to-performance-profiling-and-configuration-in-unreal-engine), and [Memory/CPU considerations](https://dev.epicgames.com/documentation/en-us/unreal-engine/common-memory-and-cpu-performance-considerations-in-unreal-engine), Unreal Engine 5.8 documentation accessed 2026-07-22.
- Blender Foundation, [Data-blocks](https://docs.blender.org/manual/en/5.0/files/data_blocks.html) and [Library overrides](https://docs.blender.org/manual/en/5.0/files/linked_libraries/library_overrides.html), Blender 5.0 Manual, accessed 2026-07-22.

### 11.5 Stable conclusion for downstream sessions

The future builder should not promise that a model can autonomously discover and safely eliminate complexity. It should promise a bounded decision procedure: enter only after verified implementation, identify a specific smell, expose invariants and hidden consumers, gate the proposal, make a reversible transformation, run every affected evidence layer, and accept only after qualified review. If that evidence cannot be assembled, preservation wins over simplification.

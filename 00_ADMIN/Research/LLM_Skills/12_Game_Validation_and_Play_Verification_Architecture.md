# Game Validation and Play-Verification Architecture

**Session:** 12 of 18
**Research date:** 2026-07-22
**Repository state inspected:** [`346f7a5dd4ad790ff21e6dfecb6b49208df26782`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/346f7a5dd4ad790ff21e6dfecb6b49208df26782) (`main`)
**Scope:** Engine-neutral validation architecture; no test harness or game skill is implemented here.

## Evidence and status convention

- **Finding — strong:** directly established by a controlling project file, a live repository inspection, first-party documentation, or a primary research paper.
- **Finding — moderate:** supported by an inspected implementation or convergent primary documentation, but not demonstrated in this project.
- **Inference:** a reasoned consequence of findings; it is not represented as measured project behavior.
- **Recommendation:** a proposed control for later approval and implementation.
- **Unverified:** evidence is absent, contradictory, or dependent on a stack decision that has not been made.

This report keeps three questions separate: whether a check *ran*, whether its machine-readable oracle *passed*, and whether accountable reviewers judge the result faithful, respectful, historically honest, and worth playing. No one of those implies the other two.

## 1. Validation principles

### 1.1 Validate a player-observable contract, not merely a successful command

**Finding — strong.** At the inspected SHA, the repository contains research and assistant-governance documents but no engine project, runtime code, approved schema, asset pipeline, build, test, performance target, input configuration, save format, or platform target. The exact audit and its non-invention requirement are recorded in [Session 1](https://github.com/Degrading1919/The_Bible_Video_Game/blob/346f7a5dd4ad790ff21e6dfecb6b49208df26782/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md). Unity remains a conditional example, not a decision.

**Recommendation.** A future change is complete only when evidence covers all affected dimensions of its acceptance contract:

1. the intended files or editor objects changed and no unauthorized ones did;
2. relevant schemas and static rules pass;
3. the project imports, compiles, builds, or launches as applicable;
4. controlled input causes the intended internal state transition;
5. the rendered/audio result agrees with internal state;
6. logs contain neither a new error nor a prohibited warning;
7. persisted state round-trips when the change touches persistence;
8. protected project invariants remain true; and
9. a human reviews every criterion whose oracle depends on meaning, reverence, historical judgment, cultural authenticity, or play quality.

A green compiler, a tool return value, a screenshot, or an LLM summary alone is not sufficient. The audited game-skill landscape found the most credible pattern to be a small change followed by real execution and layered observation, while also finding no package that can certify this project's sacred or historical requirements ([Session 11](https://github.com/Degrading1919/The_Bible_Video_Game/blob/346f7a5dd4ad790ff21e6dfecb6b49208df26782/00_ADMIN/Research/LLM_Skills/11_Video_Game_Development_Skill_Landscape.md)).

### 1.2 Use independent, layered oracles

**Recommendation.** Prefer two independent observations for a consequential behavior: for example, a state assertion plus a rendered-frame review, or a save-file semantic comparison plus a post-load gameplay assertion. A test-only state projection must be derived from the same authoritative runtime state players experience; it must not become an alternate simulation that can pass while the game is wrong.

The oracle types should be explicit:

- **Structural oracle:** a file, resource, schema, reference, or graph has a permitted shape.
- **Exact-state oracle:** a named state value equals the expected value after a defined action.
- **Invariant oracle:** a property is always true, such as “a protected sacred figure is never damageable.”
- **Temporal oracle:** events occur in a permitted order within declared timing bounds.
- **Metamorphic oracle:** changing an irrelevant variable does not alter the outcome, or a transformation has a predictable effect; useful where a single exact output is impractical.
- **Differential/golden oracle:** the result is compared with an approved baseline, tolerance, or prior compatible build.
- **Human rubric:** named reviewers assess criteria that machines cannot establish.

Every scenario must identify the authority behind its expected result. An expected value copied from current implementation without independent approval merely freezes a possible defect.

### 1.3 Determinism is a designed seam, not a blanket claim

**Finding — moderate.** Official tools demonstrate that controlled time and isolated input are technically possible in some stacks. Unity's versioned `InputTestFixture` can isolate device discovery and expose a controllable time value; Playwright exposes clock control; Godot's command line can force a movie frame rate. Those capabilities do not make an entire physics, rendering, audio, threading, or platform stack deterministic ([Unity input fixture](https://docs.unity3d.com/ja/Packages/com.unity.inputsystem%401.4/api/UnityEngine.InputSystem.InputTestFixture.html), [Playwright clock](https://playwright.dev/docs/clock), [Godot command line](https://docs.godotengine.org/en/stable/tutorials/editor/command_line_tutorial.html)).

**Recommendation.** A future runtime should expose bounded seams for reset, clock advancement, fixed timestep, random seed, scenario fixture, stable entity identifiers, state projection, and graceful stop. Evidence must record engine/runtime version, build identity, platform, device, seed, locale, resolution, graphics settings, fixture, action sequence, timeout, and known nondeterministic inputs. Tests that cannot control a source of variance should state tolerances and classify the result as statistical or observational, not deterministic.

### 1.4 Treat validation code and evidence as governed production assets

**Recommendation.** Test helpers, goldens, fixtures, schemas, scenario definitions, and evidence manifests require ownership, review, versioning, and compatibility policy. Tests must not weaken production behavior, mutate acceptance criteria to make a change pass, hide exceptions, or write outside declared temporary/artifact locations. Session 6 documents the corresponding risks of test gaming, silent tool failure, unreviewed scripts, and supply-chain reach ([risk report](https://github.com/Degrading1919/The_Bible_Video_Game/blob/346f7a5dd4ad790ff21e6dfecb6b49208df26782/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md)).

### 1.5 Automate detection; retain accountable judgment

**Finding — strong.** The controlling [Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/346f7a5dd4ad790ff21e6dfecb6b49208df26782/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) requires fixed sacred events, bounded witness agency, era-appropriate knowledge, source/confidence distinctions, schema-first structured content, and an explicit QA/continuity role. These are project authority, not optional conventions.

**Recommendation.** Machines should enforce explicit prohibitions, source-record completeness, state invariants, chronology references, and content-category boundaries. Humans must judge whether a portrayal is reverent, whether uncertainty is communicated honestly, whether ordinary agency remains meaningful, whether ethnicity and material culture are responsibly represented, and whether a mechanic produces the intended emotional and spiritual weight. Human approval should name the reviewer, rubric revision, build, scenario, decision, and unresolved concerns.

## 2. Current-stack capability assessment

### 2.1 Verified current state

**Finding — strong.** A fresh tracked-file search at `346f7a5d…` found no `project.godot`, `.uproject`, Unity package manifest, engine scenes/resources, source directory, test files, build/export definitions, save/input/profiling files, CI workflow, or executable. There are therefore no “current engine files” to inspect beyond the Session 1 negative finding.

| Capability | Current project status | What can truthfully be done now | Adoption gate before automation |
|---|---|---|---|
| Static Markdown/path/link checks | Feasible over current repository | Validate authorized paths, Markdown structure, durable links, transient-token absence, and scope-limited diffs | Approve exact rules and false-positive handling |
| Scripture/source/category/schema checks | Conceptually required; no approved machine schema | Review documents manually and design requirements | Approve schemas, stable IDs, vocabularies, provenance and confidence fields |
| Unit/integration/scene/runtime tests | Unavailable | Define architecture and acceptance scenarios only | Choose engine/language/test framework and create real runtime seams |
| Headless/editor execution | Unavailable | Record as blocked, never simulate a pass | Select and pin engine/editor, version, license, host image, import cache policy |
| Automated input/state inspection | Unavailable | Specify stable identifiers and state projection requirements | Approve input system, harness boundary, reset/clock/seed contract |
| Screenshot/video/audio comparison | Unavailable for the game | Review existing document imagery only; no game capture exists | Select renderer/build, capture tool, standard environments and goldens policy |
| Save/load validation | Unavailable | Define semantic round-trip and migration requirements | Approve save schema, compatibility range, fixtures and migrations |
| Performance/memory validation | Unavailable | Avoid numerical claims; define measurement contract | Approve target hardware, build type, scenarios, budgets and profiler |
| Accessibility/localization/platform checks | No target or feature implementation | Adopt planning rubrics and avoid declaring conformance | Approve platform/input/language matrix and feature requirements |
| Human playtest | No playable build | Review paper scenarios and project safeguards only | Produce a runnable slice plus consent, privacy, feedback and issue workflow |

### 2.2 What common engines demonstrate—but do not select

**Finding — strong for tool capability, unverified for this project.** Official documentation shows that plausible future stacks have overlapping validation primitives:

- Unity documents Edit Mode and Play Mode tests, command-line test result files, command-line player builds, isolated programmatic input, and a performance-test package ([Test Framework](https://docs.unity3d.com/Packages/com.unity.test-framework@1.4/manual/index.html), [command-line build](https://docs.unity3d.com/current/Manual/build-command-line.html), [Input System testing](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.4/manual/Testing.html), [performance testing](https://docs.unity3d.com/6000.0/Documentation/Manual/com.unity.test-framework.performance.html)).
- Godot documents headless execution, scene/script launch, import, log-file selection, release export, fixed-FPS movie writing, and frame-bounded exit ([command-line tutorial](https://docs.godotengine.org/en/stable/tutorials/editor/command_line_tutorial.html), [exporting projects](https://docs.godotengine.org/en/stable/tutorials/export/exporting_projects.html)). The docs do not establish a project-ready first-party unit-test framework.
- Unreal documents unit/feature/content-stress/screenshot categories, simulated input through Automation Driver, gameplay-level Functional Tests, command-line/report workflows, and Gauntlet session orchestration/log parsing ([Automation Test Framework](https://dev.epicgames.com/documentation/en-us/unreal-engine/automation-test-framework-in-unreal-engine), [running Automation Tests](https://dev.epicgames.com/documentation/en-us/unreal-engine/run-automation-tests-in-unreal-engine), [Gauntlet overview](https://dev.epicgames.com/documentation/en-us/unreal-engine/gauntlet-automation-framework-overview-in-unreal-engine)). Epic explicitly notes that its Automation Framework depends on engine systems and is not ideal for pure unit tests.
- A browser-based implementation could use Playwright for input, screenshots, video, traces, time control, and visual comparisons. Its official visual-comparison documentation warns that host OS, browser version, settings, hardware, power state, and headless mode can change rendering ([visual comparisons](https://playwright.dev/docs/test-snapshots), [trace viewer](https://playwright.dev/docs/trace-viewer), [video](https://playwright.dev/docs/videos)).

**Inference.** The architecture below is feasible in more than one stack, but exact commands, fixture formats, render stability, hardware reach, license requirements, and CI feasibility must be resolved only after an authoritative choice. No skill, MCP server, or test convenience should choose the engine.

### 2.3 Execution-environment routing

| Environment | Best use | Not sufficient for | Default trigger |
|---|---|---|---|
| Local code-only | Formatting, schema, pure logic, fast static checks | Imports, rendering, real input, target builds | Every affected change before engine launch |
| Local editor | Import/serialization, authoring-state inspection, scene/resource validation | Packaged-build behavior or target-platform fidelity | Asset/scene/resource/config changes |
| Local development build | Runtime state, real input, save/load, logs, visual and audio inspection | Release performance or other devices | Gameplay/UI/persistence changes |
| Headless runtime | Fast simulation, state assertions, deterministic scenarios | Render/audio correctness and many GPU/platform behaviors | Every suitable change in CI once supported |
| CI editor/headless | Reproducible automated gates and retained artifacts | Human meaning, all device/driver combinations | Pull/merge and scheduled regression tiers |
| Pinned rendered CI worker | Goldens and smoke captures on a controlled stack | The full hardware population | Visual-affecting changes and scheduled baselines |
| Target device/release-like build | Performance, input-device, suspend/resume, packaging, certification | Broad creative and theological approval | Milestones, releases, and platform-affecting changes |
| Human review build | Play meaning, reverence, historical/cultural judgment, accessibility experience | Exhaustive deterministic regression | Named content/vertical-slice/release gates |

## 3. Automated test layers

The matrix is a recommended architecture. “Owner” is a responsibility class from current project roles or a future technical owner; it is not evidence that staffing exists.

| Layer | What it can prove | What it cannot prove | Required evidence/artifacts | Trigger and owner | Failure response |
|---|---|---|---|---|---|
| **A. Static/path/schema** | Authorized paths; parseability; schema conformance; stable-ID uniqueness; required provenance/confidence fields; reference integrity; prohibited transient tokens | Runtime behavior, factual truth of a sourced claim, play meaning | Validator version/hash, rule set, input manifest, diagnostics, exit code, diff | Every relevant change. Schema & Content Engineer + QA | Block merge; correct source/schema rather than relaxing rule; escalate false positives through schema review |
| **B. Pure unit** | Deterministic functions such as calculations, parsers, state transitions, chronology comparisons, inventory arithmetic | Engine integration, rendered behavior, real serialization, cultural/reverential quality | Test names/results, code coverage as diagnostic only, seed/fixtures, environment | Every code change. Systems Engineer | Fix behavior/test; quarantine only with owner, issue, evidence and expiry |
| **C. Component/integration** | Contracts between gameplay, content data, UI model, inventory/economy, event bus, persistence adapter | Whole-world behavior, target performance, final visuals | Fixture graph, dependency versions, logs, structured before/after state | Interface or data changes. Systems + Schema Engineers | Stop; identify contract owner; add regression before correction |
| **D. Import/build/export** | Assets/resources import; scripts compile; required build target packages; an output artifact is created and starts | That the build is enjoyable, visually correct, complete, or release-ready | Full log, exit code, build manifest, artifact hash/size, warnings allowlist, tool/license versions | Asset/config changes; merge; milestone. Technical owner | Preserve logs; do not call warnings “clean”; repair or declare target unavailable |
| **E. Deterministic/state seam** | Reset reproducibility; injected clock/seed; stable entity lookup; authoritative text/state projection | Global determinism, renderer/physics/audio identity, truth of an incomplete projection | Seed, timestep, fixture, projection schema, repeated-run comparison, known variance | Harness/runtime architecture and stateful changes. Systems + QA | Treat divergent repeats as defect; isolate nondeterminism; never average away invariant failures |
| **F. Runtime logs/state** | Crashes, exceptions, assertions, prohibited warnings, scenario state transitions, state/visual disagreement when cross-checked | Absence of hidden defects; good player experience; safe telemetry by itself | Raw logs, structured state snapshots, timestamps/frame indices, log policy and redaction report | Every launched scenario. Systems + QA | Fail on crash/error or new unapproved warning; preserve first failure; redact only copies, not diagnostic originals within protected access |
| **G. Automated play/input** | A controlled keyboard/controller/action sequence reaches observable checkpoints; bindings and focus work in tested configuration | Natural human control feel, full hardware diversity, discoverability, meaning | Action script, semantic selectors, timing, input-device profile, video/state/log result | Gameplay/UI/input changes. Gameplay Systems + QA | Retry only under flake protocol; inspect whether selector, timing, or product failed |
| **H. Visual/audiovisual** | Missing/corrupt UI; layout/clipping; approved pixel/image differences in pinned environment; capture continuity; basic caption/audio-channel presence | Reverence, beauty, historical accuracy, animation feel; cross-platform identity; sound quality from screenshots | Actual/expected/diff images, capture video/audio, resolution/locale/settings, reviewer annotations | Visual/audio/UI/content change; scheduled matrix. Visual Researcher + QA | Block unapproved difference; classify intended change and require explicit new-baseline approval |
| **I. Save/load/world state** | Semantic round-trip; stable IDs; references survive; version/migration behavior; protected-state restoration; corrupted-save handling | Every future version; player trust without destructive recovery UX review | Input and output saves, semantic diff, schema/version, build IDs, migration log, post-load scenario | Persistence/schema/world-state change and release regression. Systems + Schema + QA | Never overwrite sole fixture; preserve failing save; repair reader/migration or declare incompatibility explicitly |
| **J. Performance/memory** | Scenario-specific frame time, load time, memory/allocation and leak indicators on declared hardware/build | Universal performance, subjective smoothness, future scale; useful thresholds before budgets exist | Raw profiler capture, summary, hardware/driver/build/settings, warm-up, repetitions, statistical method | Performance-affecting change; scheduled; release. Technical owner | Fail approved budget; if no budget, report measurement without pass claim and seek decision |
| **K. Accessibility/localization/platform** | Tested input paths, focus, captions, contrast, text scaling, glyph/overflow, locale formats, resolution/aspect, selected platform lifecycle | Accessibility for every disability or legal/platform conformance by generic checklist | Requirement IDs, locale/device/resolution matrix, screenshots/video, assistive-tech/human notes, platform reports | UI/input/text/audio/platform change; milestone. UX/accessibility/localization owner + QA | Treat blocker against approved requirement; never waive solely because automation cannot reproduce human impact |
| **L. Provenance/sacred/chronology/continuity** | Required source/category/confidence metadata; forbidden interactions; fixed event outcomes; era-knowledge gates; continuity invariants | Theological correctness, historical truth, respectful tone, emotionally meaningful witness agency | Rule IDs tied to authority, scenario results, source records, state/log/video, named specialist sign-off | Every affected content/mechanic/save change. Theology, history, QA roles | Fail closed for prohibited behavior or missing provenance; route interpretation disputes to user/authority, not test author |
| **M. Human play/review** | Whether players understand, can operate, care about, and experience intended tone; whether expert reviewers find portrayals responsible | Exhaustive regression or statistical generalization from a small sample | Build/scenario, rubric, consent/privacy record, observations, issues, reviewer identity/role, decision | Vertical-slice/content gates and release. Creative Director + specialists + representative players | Record issue and severity; revise; rerun affected automated and human gates; do not substitute majority vote for authority |

### 3.1 Trigger graph and stopping rule

**Recommendation.** The change declares touched concerns, and the validation planner expands them transitively. A dialogue-content change, for example, triggers schema/provenance, era knowledge, runtime presentation, captions/localization, save/continuity if dialogue state persists, and human Scripture/theology or history review. A save-schema change triggers static schema, unit migration, integration, runtime, multiple save fixtures, sacred-state restoration, performance if loading changes, and human recovery-UX review.

The first failed critical layer stops publication, not necessarily all diagnostic collection. Preserve the first-failure evidence, run safe read-only diagnostics, correct the narrow cause, rerun the failed layer, then rerun all downstream and protected-invariant layers. A failure in one platform or locale is a real failure for that supported matrix cell; passing elsewhere does not cancel it.

### 3.2 Flakiness and reproducibility protocol

**Finding — strong.** Primary studies at Google describe flaky tests as nondeterministic pass/fail behavior that makes results unreliable and increases rerun/debugging cost; one study across 428 projects reports 82% accuracy for its root-cause localization technique, not elimination of flakiness ([Ziftci and Cavalcanti, ICSME 2020](https://research.google/pubs/de-flake-your-tests-automatically-locating-root-causes-of-flaky-tests-in-code-at-google/)). A separate 13,000-breakage study treats flakiness as noise requiring probabilistic handling ([Henderson et al., ICST 2023](https://research.google/pubs/flake-aware-culprit-finding/)).

**Recommendation.** Do not implement blind “retry until green.” On any unexpected failure:

1. retain attempt 1 completely;
2. verify environment identity and test isolation;
3. rerun a bounded number of times under identical recorded conditions to classify, not erase, the failure;
4. if results differ, mark the test and product state **indeterminate/flaky**, open an owned defect, and block any critical invariant;
5. capture seed, schedule/timing, machine load, process list where permitted, logs, screenshots, and state;
6. correct shared state, race, clock, random, network, asset-import, animation, rendering, or selector causes; and
7. require a sustained clean observation window appropriate to the test before restoring gating status.

Quarantine requires owner, justification, impact, issue, expiry, and compensating manual gate. Sacred-event, save-corruption, data-loss, security, and provenance checks must never become non-blocking merely because they are flaky.

### 3.3 Golden-baseline governance

**Finding — strong.** Playwright's official docs require consistent environments for screenshot comparison and recommend storing/reviewing generated snapshots in version control; Unreal exposes screenshot comparison as a test category. This establishes capability, not a universal tolerance.

**Recommendation.** A golden is approved expected evidence, not whatever the current build emits. Each baseline needs scenario ID, requirement/authority link, build/tool/environment identity, resolution/locale/settings, creation and approval date, reviewer, compatibility scope, and perceptual/pixel tolerances with rationale. Updating a golden must show old, actual, diff, and proposed new; the same authoring agent may produce candidates but must not silently approve them. Separate intended dynamic regions only when they are genuinely irrelevant; masking the behavior under test is test gaming. Retain representative video/audio and semantic state beside key visual goldens.

## 4. Controlled gameplay/input loop

### 4.1 Scenario contract

Every automated or human-play scenario should declare:

- stable scenario ID and revision;
- authority and acceptance-criterion IDs;
- compatible build/save/schema range;
- prerequisites and known exclusions;
- clean reset fixture, seed, clock/timestep and locale;
- platform, input device/profile, resolution/aspect and graphics/audio settings;
- initial authoritative state and allowed setup actions;
- semantic input actions with time/condition bounds;
- checkpoints containing state, visual/audio and log oracles;
- prohibited states that fail immediately;
- evidence to retain and privacy class;
- cleanup/stop behavior; and
- automation owner plus required human reviewers.

Use action names and stable IDs where possible (`interact`, `open_inventory`, `sacred_event_boundary`) rather than raw screen coordinates or hierarchy indices. Raw keyboard/controller events remain necessary to prove bindings and platform behavior, so test both the semantic action layer and representative physical mappings. Timing should wait for named observable conditions with a ceiling rather than rely only on arbitrary sleeps.

### 4.2 Input and state coverage

**Recommendation.** For each supported control family, test launch/menu navigation, remapping, conflicts, press/hold/repeat, simultaneous inputs, focus loss/recovery, device disconnect/reconnect, pause, accessibility alternatives, and destructive-action confirmation where applicable. Microsoft’s Xbox Accessibility Guidelines frame input choice, UI navigation, captions, text, non-color channels, time limits, motion and photosensitivity as game-specific test concerns, while explicitly stating that the guidelines are best practices rather than legal/compliance certification ([XAG 3.2](https://learn.microsoft.com/en-us/xbox/accessibility/guidelines), [XAG 107 Input](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/107)).

State inspection should expose only a minimal, truthful projection: active location/scene; controlled actor ID and transform when relevant; current objective/event phase; inventory and economy subset; world/household/lineage flags; clock and seed; save/schema version; protected-mode state; targetability/damage permissions; relevant NPC knowledge scope; and recent authoritative events. It should neither disclose player/private data unnecessarily nor permit an LLM to mutate state through an ostensibly read-only endpoint.

### 4.3 Playable acceptance scenarios and gates

Because no vertical-slice specification is approved, these are architecture-level scenarios, not assertions that Capernaum, Galilee, or any named content has been selected.

| Scenario | Minimum controlled path | Machine gate | Required human gate |
|---|---|---|---|
| Clean start | Install/launch → accessibility/first-run as designed → new experience → controllable state | No crash/error; correct build/scene; input and focus work; state fixture identified | Onboarding clarity, tone, text/readability and control comprehension |
| Ordinary-life loop | Receive a modest obligation → gather/work/trade/help → make a bounded moral choice → return/resolve | Inventory/economy/objective/reputation transitions satisfy schema and conservation rules; no impossible knowledge | Mechanic is meaningful rather than grind; ordinary life and moral pressure feel grounded |
| Protected-event boundary | Approach before/during/after protected mode; try each prohibited input and allowed witness action | Weapons/tools lowered/disabled as specified; sacred figure un-targetable and undamageable; no theft/grief/derail; fixed outcome; allowed witness actions remain; state persists through pause/load if permitted | Reverence, staging, emotional tone, dignity, adequate but bounded witness agency |
| Knowledge boundary | Encounter era-limited dialogue and open player codex for the same subject | In-world content uses allowed-era facts; later connections appear only in player-facing layer; source/category/confidence present | Scripture/theology and history reviewers judge nuance and uncertainty truthful |
| Save/resume | Save at ordinary, boundary, and post-event checkpoints; exit; reload; continue | Semantic state round-trip; no duplicated rewards/events; sacred outcome and restrictions preserved; corrupt/old save handled as designed | Recovery messages are understandable and do not pressure data loss |
| Input/display matrix | Repeat critical path with supported keyboard/controller and selected resolutions/aspects/locales | All required actions reachable; prompts match device; no clipping/missing glyphs; captions/critical cues available | Players using relevant access needs can understand and operate the path |
| Fault/recovery | Missing optional asset/service, interrupted save, invalid data fixture, runtime assertion | Fail-safe state; actionable logged error; no fabricated fallback fact; no silent corruption | Error/recovery experience preserves trust and context |
| Packaged-build smoke | Install clean output; launch; play critical path; exit/relaunch | Artifact hash known; no editor-only dependency; logs/results retained | Build presents intended audiovisual and interaction quality |

## 5. Visual and audiovisual validation

### 5.1 Four complementary levels

1. **Structural UI assertions:** expected widgets/captions/prompts exist, fit declared safe areas, have focus order and semantic labels where supported.
2. **Pinned visual regression:** compare selected stable frames with approved goldens and declared tolerances in an identical environment.
3. **Video/audio continuity review:** capture complete transitions, animation, camera, timing, dialogue, ambience, captions, mix and input feedback; still images cannot expose temporal defects.
4. **Human art/history/stewardship review:** compare costumes, bodies, ethnicity, architecture, landscape, objects, gesture, sacred staging, sound and emotional tone against approved sources and uncertainty labels.

**Recommendation.** Every captured frame should be tied to scenario, checkpoint, frame/time, camera, build, environment, resolution/aspect, locale, UI scale, graphics preset and accessibility settings. Visual differences should be classified as rendering variance, approved change, product defect, baseline defect, or unresolved. A model may triage an image, but its observation must link to the image and cannot replace responsible specialist review.

### 5.2 Accessibility and localization views

Automate what is objectively defined: text/glyph presence, clipping, safe areas, minimum approved scale, contrast samples, focus reachability, caption timing metadata, input-prompt switching, non-color cues, reduced-motion settings, and supported locale formatting. W3C WCAG 2.2 provides technology-neutral testable concepts for keyboard access, no traps, contrast, reflow, captions, time, and flashing; it is a web standard and must not be mislabeled as total game compliance ([WCAG 2.2 Recommendation dated 2024-12-12](https://www.w3.org/TR/2024/REC-WCAG22-20241212/)). Unicode LDML supplies versioned locale-data conventions, not a complete game-localization test strategy ([UTS #35 version 48.2](https://www.unicode.org/reports/tr35/tr35-78/tr35.html)).

Human testing remains necessary for legibility over moving scenes, cognitive load, caption usefulness, photosensitivity/motion experience, remapping practicality, screen-reader/narration quality, culturally appropriate translation, right-to-left layout, font character, and whether sacred terminology is translated responsibly.

### 5.3 Audio evidence

**Recommendation.** Preserve synchronized video plus direct audio capture for critical scenes, along with audio settings and device route. Machine checks may assert that expected buses/events fire, captions exist, channels do not clip beyond an approved rule, and a silence/error condition is absent. They cannot determine whether music manipulates a sacred scene inappropriately, pronunciation is sound, dialogue performance is respectful, ambience is historically plausible, or the mix carries the desired weight. Those require named audio, language, history, Scripture/theology and Creative Director review as appropriate.

## 6. Save/load and serialized-state validation

### 6.1 Semantic, not byte-only, round trips

**Recommendation.** A save round trip should compare a canonical semantic projection before save and after load, allowing declared serialization differences such as ordering or timestamps while forbidding loss, duplication, invalid references, unauthorized future knowledge, or altered protected outcomes. Byte equality is useful only for formats designed to be canonical; successful deserialization alone is insufficient.

The fixture set should eventually include:

- new-game/default state;
- ordinary activity in progress;
- inventory/economy and relationship/reputation edges;
- each sacred-event phase in which saving is permitted, plus explicit rejection when not permitted;
- era/lineage transition boundaries;
- codex unlocked versus in-world knowledge separation;
- empty, maximum-sized and unusual Unicode/localized content;
- previous supported schema versions requiring migration;
- unknown future version, truncated/corrupt data and missing optional content; and
- platform suspend/resume or cloud conflict only after those platforms/features are approved.

Each migration test must retain immutable source fixtures, expected semantic output, migration logs and build/schema compatibility. A writer should use atomic/recoverable replacement appropriate to the chosen platform; tests must prove that interruption does not destroy the last good save. Exact strategy is **unverified** until the save system and platforms exist.

### 6.2 World and sacred-state invariants

At load, validate stable IDs and references before activating gameplay. A loaded protected event must never regain damage/target/grief paths because a transient lock was omitted. Fixed biblical outcome, allowed witness state, nearby ordinary-person outcomes, codex/source unlocks, chronology, and lineage testimony must resume according to the approved schema. Attempting to load an incompatible state should fail visibly and safely, not coerce fields, fabricate history, or silently restart the event.

## 7. Performance, build, export and platform validation

### 7.1 No invented budgets

**Finding — strong.** The repository has no target platform/hardware, performance budget, asset budget, build type or benchmark scenario. Therefore Session 12 cannot responsibly prescribe a frame rate, frame-time percentile, memory cap, load-time limit, build size, or allocation threshold.

**Recommendation.** Before performance can gate, the Creative Director and technical owner must approve target devices, quality modes, resolution, representative scenarios, warm-up, build configuration, measurement duration, percentile/statistical rule, frame/memory/load/allocation budgets and acceptable variance. Until then, record measurements and compare same-environment regressions without labeling an arbitrary value a project failure.

### 7.2 Measurement contract

Retain raw profiler/trace captures, not only summaries. Record commit/build/artifact hash, engine/tool/plugin version, platform/OS, CPU/GPU/memory, driver, power/thermal state where available, resolution, quality, locale, input, scene/scenario, save fixture, seed, warm-up, run count, background-load policy and known anomalies. Measure editor and development builds for diagnosis, but set release gates from representative release-like builds on approved targets. Track CPU and GPU frame behavior, memory residency and growth, allocations/garbage collection, asset streaming, loading/transitions, save/load time, build/install size and crashes/hangs relevant to the chosen stack.

### 7.3 Build/export gates

A build gate should prove a clean checkout can import/restore pinned dependencies under approved network policy, compile, package, hash, install or stage, launch, execute a smoke scenario, write permitted logs/saves, exit cleanly, and relaunch. Preserve dependency lock/manifests, licenses/notices, import/build logs, warnings, output manifest, artifact hash and smoke evidence. Editor success cannot stand in for the packaged artifact. Official Unity, Godot and Unreal documentation all expose some command-line build/export or automation surface, but exact coverage and licensing remain stack-dependent.

Platform certification, signing, entitlement, suspend/resume, controller requirements, cloud saves, store metadata and sandbox behavior are **unverified** and deferred until platforms are authorized. Do not download SDKs, accept terms, sign artifacts, publish builds or upload evidence merely to satisfy a generic validation plan.

## 8. Sacred-event and historical-coherence checks

### 8.1 Enforceable layers

The controlling protocol's sacred-event rules should be represented redundantly at approved data/schema, runtime invariant, scenario regression, and human review layers—not only in a skill prompt.

| Concern | Static/schema oracle | Runtime/scenario oracle | Mandatory human judgment |
|---|---|---|---|
| Fixed sacred outcome | Event record marks protected anchors and allowed branches; outcome ID immutable | Force every reachable choice/input/state-restore path; canonical outcome remains | Portrayal does not imply player causation or diminish divine action |
| Sacred figures protected | Entity/event policy forbids damage, theft, exploitation and disallowed targeting | Attack, area effect, collision, companion AI, item use, debug-like legal player actions and load/resume cannot affect them | Staging and interaction communicate dignity rather than merely invulnerability |
| Witness agency | Allowed verbs and ordinary-person consequences explicitly modeled | At least one meaningful allowed response works; restrictions do not erase all agency | Choice feels morally and emotionally meaningful, not tokenistic |
| Chronology/era knowledge | Content references era and knowledge scope; later facts segregated | Dialogue/objective/NPC queries cannot reveal prohibited later knowledge; codex can show approved player-facing material | Specialists assess implication, ambiguity and plausible cultural knowledge |
| Canon/source/confidence | Every claim/content element carries approved category, source, confidence and creative-status fields | UI/codex presents required labels and does not collapse categories | Theology/history reviewers assess source use, dispute framing and invented connective material |
| Material culture/geography | Asset/content records link approved evidence and uncertainty | Runtime variant matches scenario era/region and does not present disputed detail as certain | Expert visual/historical review of actual context and cultural authenticity |
| Continuity/save | Stable event, testimony, lineage and codex IDs; migrations preserve protected fields | Save/load, restart, alternate route and era transition cannot rewrite anchors or leak knowledge | Narrative continuity and inherited testimony remain coherent and appropriately framed |

### 8.2 Negative and adversarial regression

**Recommendation.** For every protected event, enumerate prohibited verbs and *all authorized systems that could produce equivalent effects*: player/companion attacks, area damage, physics, fire/environment, theft/inventory, dialogue coercion, quest cancellation, navigation displacement, economy exploits, NPC AI, save editing through legitimate migration paths, network/mod pathways if ever supported, scene reload, skip/cutscene controls, difficulty/accessibility toggles, and sequence breaks. Test entry, active phase, interruption, reload and exit. The pass condition includes both “forbidden effects do not occur” and “the event reaches its fixed approved outcome.”

These are product-defense tests, not invitations to build generalized sacrilege mechanics. Fixtures should use abstract test identifiers and the minimum necessary simulated action. Evidence access should be limited when captures contain sensitive unreleased sacred portrayals.

### 8.3 Findings versus review decisions

A validator can find that a source field is absent, an era rule is violated, a weapon remains enabled, or a protected outcome changed. It cannot settle a disputed chronology, decide the correct depiction of a miracle, infer theological consensus, or approve emotional tone. Conflicts route through the repository authority chain and ultimately the Creative Director; the test record must preserve dissent and uncertainty rather than manufacturing consensus.

## 9. Human playtest gates

### 9.1 Gate types

- **Developer smoke:** can a responsible developer complete the changed path with expected state/log evidence?
- **Discipline review:** do gameplay, UI/accessibility, visual/audio, history and Scripture/theology specialists approve their named criteria?
- **Stewardship review:** does the Creative Director approve sacred treatment, witness premise, uncertainty handling and overall tone?
- **Representative usability/accessibility play:** can intended players, including people with relevant disabilities and control/language contexts, understand and operate the experience?
- **Meaning and appeal playtest:** do players perceive agency, stakes, clarity and emotional impact without the game becoming a sermon wrapper or power fantasy?
- **Release acceptance:** does a release-like target build pass the approved scenario/platform matrix with all critical issues closed or explicitly accepted by authorized decision-makers?

### 9.2 Review rubric

Use criterion-specific prompts rather than “does this feel good?” Record observation separately from interpretation and recommendation. At minimum ask:

1. Did the player understand their role as witness rather than author/savior?
2. Did restrictions around sacred events feel intentional, reverent and still meaningfully interactive?
3. Could the player distinguish in-world knowledge from player codex context?
4. Were Scripture, historical reconstruction, tradition, dispute, uncertainty and invention distinguishable?
5. Did ordinary work, relationship, survival and moral pressure serve immersion rather than detached grind?
6. Were important choices understandable and their consequences proportionate?
7. Were controls, text, audio cues, captions, motion and time demands usable for the participant?
8. Did any ethnic, regional, bodily, social or material depiction feel stereotyped, anachronistic or falsely certain?
9. What did the player attempt that the design neither allowed nor explained?
10. What evidence supports the review decision, and what remains unresolved?

Participant consent, recording scope, data retention, compensation, safeguarding and confidentiality must be approved before external playtests. LLM summarization of notes should occur only within that policy and must retain links to de-identified primary observations.

## 10. Evidence-capture contract

### 10.1 Run manifest

Each run should emit one manifest connecting:

- repository commit and dirty-state declaration;
- build ID, artifact hash and schema/save version;
- engine/runtime/editor/test-harness/plugin/dependency versions;
- operating system, hardware/device, driver and execution mode;
- scenario and requirement/authority revisions;
- seed, clock/timestep, fixture/save, locale, resolution/aspect, quality and input profile;
- start/end time, duration, process exit and timeout/cleanup outcome;
- exact actions and checkpoint results;
- paths and hashes for logs, structured state, test reports, screenshots, diffs, video/audio, profiler traces, saves and build manifests;
- warnings, retries, variance/flaky classification and missing evidence;
- automation identity, human reviewers and final gate decision; and
- privacy/security class, retention, access and redaction status.

Use open, documented formats where practical (for example JSON manifests, JUnit-compatible result XML where the selected framework supports it, PNG images, and tool-native raw traces plus an export). Content-address or hash artifacts and preserve their relationship; a detached screenshot with a descriptive filename is not sufficient evidence.

### 10.2 Retention and repository policy

**Recommendation.** Keep small normative scenario definitions, schemas, validators and approved goldens in version control when appropriate. Store large run artifacts in an approved immutable or tamper-evident artifact system with stable retention links, access controls and hashes; do not bloat the repository automatically. Release and sacred-event acceptance evidence should outlive ordinary CI diagnostics according to an approved policy. Failed-run evidence must not be deleted just because a later run passed.

Build provenance should identify inputs and outputs. The SLSA provenance specification provides a general model for verifiable information about where, when and how an artifact was produced; adoption level and tooling are deferred ([SLSA Provenance v1.2](https://slsa.dev/spec/v1.2/provenance)).

### 10.3 Telemetry, logs and privacy

**Finding — strong.** Logs and captures can contain personal or sensitive data. OWASP's logging guidance lists access tokens, passwords, keys, connection strings, session identifiers and sensitive personal data among information that should not be recorded directly; NIST's Privacy Framework is designed to help organizations manage privacy risk ([OWASP Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html), [NIST Privacy Framework](https://www.nist.gov/privacy-framework)). These general sources do not replace applicable legal review.

**Recommendation.** Default test telemetry to local/off unless explicitly approved. Define purpose, fields, classification, consent/lawful basis where applicable, destination, transport, access, retention and deletion before collection. Never place secrets, full user paths, account IDs, participant identity, unredacted communications, copyrighted source corpora, or unreleased captures in public CI artifacts. Redaction must be tested; permissions should separate artifact production from external upload. An LLM or third-party observability service must not receive screenshots, saves, logs, prompts, source documents or player notes without explicit authorization and vendor/data-flow review.

## 11. Tool-unavailable fallback

**Recommendation.** Begin every validation attempt with a capability preflight: authoritative stack, tool executable/version, project root, license, target, permissions, required services, disk, display/GPU/audio/input needs, test inventory and artifact path. Classify each required layer as available, unavailable, forbidden, or not applicable with reason.

When a required engine, editor, device, capture tool, license, dependency, network route or permission is unavailable:

1. do not install, download, authenticate, enable telemetry, expose a port, or choose an engine without authorization;
2. run only independent in-scope checks that remain truthful, such as static schema/path review;
3. produce a blocked-layer report naming the missing capability, attempted safe detection, affected claims and exact evidence not obtained;
4. offer a bounded approved fallback, such as a local developer running a versioned scenario and returning the complete evidence bundle;
5. label the result **not runtime-validated**, not passed; and
6. resume from the blocked layer when capability is restored, then rerun downstream regressions.

Screenshots supplied by a person cannot prove logs or hidden state. A textual state dump cannot prove visuals. A mocked engine cannot prove import/build/runtime. A web prototype cannot validate a future native build. Paper review remains valuable but must retain its proper label.

## 12. Recommended narrow-change loop and minimum vertical-slice gate

### 12.1 Narrow-change loop

1. **Frame one change.** Name authority, intended player-visible result, protected invariants, affected files/systems, risk and rollback/recovery.
2. **Preflight.** Confirm clean/known repository state, stack versions, permissions, tools, scenario, artifact destinations and available layers.
3. **Write acceptance before mutation.** Select independent state, visual/log and human oracles; identify prohibited outcomes.
4. **Inspect before write.** Read live schema, dependencies, scene/resource/state and logs. Never infer missing structures.
5. **Make the smallest coherent change.** No unrelated refactor, baseline update, test weakening or new dependency.
6. **Run cheapest relevant gates.** Static/schema and unit checks first; preserve results.
7. **Import/build/launch.** Use declared environment; capture complete logs and output identity.
8. **Execute controlled inputs.** Reset fixture, apply seed/clock, use semantic actions and representative real bindings.
9. **Observe independent layers.** Compare authoritative state, rendered/audio output, logs, save behavior and relevant profiler data.
10. **Apply project-specific gates.** Sacred, chronology, provenance, knowledge-boundary, schema and continuity invariants always run when relevant.
11. **Correct, do not explain away.** Preserve first failure, make one bounded correction, rerun failed and downstream layers; follow flake protocol.
12. **Human review.** Route meaning, reverence, history/culture, accessibility and play quality to named reviewers.
13. **Final regression and evidence seal.** Run the impact-expanded suite, packaged smoke where required, hash artifacts, complete manifest and verify cleanup.
14. **Publish only a truthful claim.** State exactly which matrix cells passed, failed, were unavailable, or remain human-unreviewed.

### 12.2 Minimum gate for the first narrow vertical slice

**Unverified dependency.** The actual slice, stack, target, mechanics and performance budgets require approval. The detailed Galilee/Capernaum material in the repository is proposed research, not an authoritative production specification.

**Recommendation.** Regardless of content choice, the minimum credible vertical-slice validation should require:

- clean import/build and packaged launch from a pinned environment;
- zero crashes, unhandled exceptions, data corruption or unapproved error-level logs in the acceptance route;
- static/schema/provenance checks for all structured content used by the slice;
- pure unit and component tests for critical economy/inventory/state/persistence logic;
- a reset/seed/clock/state-projection seam sufficient to reproduce acceptance scenarios;
- automated or controlled play through clean start, one ordinary-life loop, one moral/relationship consequence, one protected-boundary scenario if included, knowledge/codex separation, save/exit/load/continue and clean exit;
- state, log and rendered video evidence for the critical route, plus approved representative screenshot baselines;
- keyboard and controller coverage if both are claimed, selected resolution/aspect/locale checks, captions/critical non-audio cues and a documented accessibility review;
- semantic save round-trip and safe corrupt/incompatible-save behavior;
- release-like performance capture on a declared representative machine, with measurements reported even if budgets await approval;
- source, uncertainty, material-culture, sacred-event and continuity review by appropriate specialists;
- Creative Director stewardship acceptance and representative player usability/meaning feedback;
- reproducible evidence manifest, artifact hashes and an issue list with no unresolved critical/high-severity invariant failures; and
- explicit statement of unsupported platforms, inputs, languages, content, persistence compatibility and automation gaps.

A slice can be “promising” before every production-release matrix cell exists, but it cannot be called validated if its defining player loop, save continuity, protected-event safeguards, knowledge separation, or human stewardship gate is missing.

## 13. Source appendix

All web sources were accessed 2026-07-22. Mutable documentation links describe capability current on that date; they are not project dependencies. Project links are commit-pinned.

### 13.1 Project authority and predecessor findings

- [`The_Bible_Video_Game` repository at Session 12 predecessor `346f7a5d…`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/346f7a5dd4ad790ff21e6dfecb6b49208df26782).
- [Master Assistant Protocol at `346f7a5d…`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/346f7a5dd4ad790ff21e6dfecb6b49208df26782/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md).
- [Session 1 — Project Context and Authority Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/346f7a5dd4ad790ff21e6dfecb6b49208df26782/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md).
- [Session 3 — Current Codex Skill Capability Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/346f7a5dd4ad790ff21e6dfecb6b49208df26782/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md).
- [Session 6 — Skill Failure, Security, and Maintenance Risks](https://github.com/Degrading1919/The_Bible_Video_Game/blob/346f7a5dd4ad790ff21e6dfecb6b49208df26782/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md).
- [Session 11 — Video-Game Development Skill Landscape](https://github.com/Degrading1919/The_Bible_Video_Game/blob/346f7a5dd4ad790ff21e6dfecb6b49208df26782/00_ADMIN/Research/LLM_Skills/11_Video_Game_Development_Skill_Landscape.md), including package audits at `openai/skills` [`0ed635a…`](https://github.com/openai/skills/commit/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea), `fernforestgames/agent-skill-godot` [`e584a97…`](https://github.com/fernforestgames/agent-skill-godot/commit/e584a973fcf0590a4cbc6697fa5daa3d11585dbe), `Randroids-Dojo/skills` [`aba2aba…`](https://github.com/Randroids-Dojo/skills/commit/aba2aba9e43243959e7d5aa851a43983c3b7080d), `CoderGamester/mcp-unity` [`c35f184…`](https://github.com/CoderGamester/mcp-unity/commit/c35f184d7656bd14e7748f11a05060feeb286d6e), `Coding-Solo/godot-mcp` [`1209744…`](https://github.com/Coding-Solo/godot-mcp/commit/1209744fad78f3998f98c7394fd0f6ef50da5281), and `ahujasid/blender-mcp` [`da4e16d…`](https://github.com/ahujasid/blender-mcp/commit/da4e16d2069ce5154eaa2535bf995e843caf5c73). Session 12 does not re-rate or adopt those packages.

### 13.2 First-party engine and execution documentation

- Unity Technologies: [Unity Test Framework 1.4](https://docs.unity3d.com/Packages/com.unity.test-framework@1.4/manual/index.html); [command-line player builds](https://docs.unity3d.com/current/Manual/build-command-line.html); [Input System 1.4 testing](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.4/manual/Testing.html); [`InputTestFixture` 1.4 API](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.4/api/UnityEngine.InputSystem.InputTestFixture.html); [Performance Testing API for Unity 6000.0](https://docs.unity3d.com/6000.0/Documentation/Manual/com.unity.test-framework.performance.html).
- Godot Engine: stable [command-line tutorial](https://docs.godotengine.org/en/stable/tutorials/editor/command_line_tutorial.html) and [exporting projects](https://docs.godotengine.org/en/stable/tutorials/export/exporting_projects.html).
- Epic Games: [Automation Test Framework](https://dev.epicgames.com/documentation/en-us/unreal-engine/automation-test-framework-in-unreal-engine), [Run Automation Tests](https://dev.epicgames.com/documentation/en-us/unreal-engine/run-automation-tests-in-unreal-engine), [Gauntlet overview](https://dev.epicgames.com/documentation/en-us/unreal-engine/gauntlet-automation-framework-overview-in-unreal-engine), and [Run Gauntlet Tests](https://dev.epicgames.com/documentation/en-us/unreal-engine/running-gauntlet-tests-in-unreal-engine).
- Microsoft Playwright: [input actions](https://playwright.dev/docs/input), [clock control](https://playwright.dev/docs/clock), [visual comparisons](https://playwright.dev/docs/test-snapshots), [videos](https://playwright.dev/docs/videos), and [trace viewer](https://playwright.dev/docs/trace-viewer).

### 13.3 Standards, guidelines and primary research

- W3C, [Web Content Accessibility Guidelines 2.2, Recommendation 2024-12-12](https://www.w3.org/TR/2024/REC-WCAG22-20241212/).
- Microsoft, [Xbox Accessibility Guidelines version 3.2](https://learn.microsoft.com/en-us/xbox/accessibility/guidelines) and [XAG 107: Input](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/107). The landing page reported last update 2026-03-04 when accessed; it describes best practices, not legal/compliance certification.
- Unicode Consortium, [Unicode Technical Standard #35 LDML version 48.2, 2026-03-03](https://www.unicode.org/reports/tr35/tr35-78/tr35.html).
- Celal Ziftci and Diego Cavalcanti, [“De-Flake Your Tests: Automatically Locating Root Causes of Flaky Tests in Code at Google,” ICSME 2020](https://research.google/pubs/de-flake-your-tests-automatically-locating-root-causes-of-flaky-tests-in-code-at-google/).
- Tim A. D. Henderson et al., [“Flake Aware Culprit Finding,” ICST 2023](https://research.google/pubs/flake-aware-culprit-finding/).
- NIST, [Privacy Framework](https://www.nist.gov/privacy-framework).
- OWASP Foundation, [Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html).
- SLSA, [Provenance specification v1.2](https://slsa.dev/spec/v1.2/provenance).

### Bounded conclusion

**Finding.** The repository has no playable stack to validate today, while first-party tool documentation shows that unit, integration, input, state, build, screenshot, video, log and performance automation is technically plausible after a stack decision. **Inference.** The durable architecture is therefore layered and engine-neutral: design controllable seams, run the real build, compare independent internal and player-visible evidence, preserve reproducible artifacts, and fail truthfully when capability is absent. **Recommendation.** Treat sacred-event, chronology, provenance, knowledge-boundary and continuity rules as enforceable invariants with specialist and Creative Director gates, and never allow automation to claim the reverence, historical honesty or meaningful play that only accountable human review can judge.

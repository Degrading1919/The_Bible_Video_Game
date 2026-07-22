# Project Constraint Enforcement Architecture

**Project:** The Bible Video Game
**Session:** 13 of 18 — sequential LLM-skills research program
**Research date:** 2026-07-22
**Repository context inspected:** `main` at `c6a9aaf439f2458c5b442c5a8b1f90636923fda8`
**Status:** Architecture recommendation; no schema, validator, test, runtime control, repository ruleset, or skill is implemented by this report

This report translates the project's governing constraints into an enforceable target architecture. It does not rewrite the Master Assistant Protocol, select an engine, create a project skill, approve a schema, or claim that proposed controls already exist. At the inspected commit, the repository is still a documentation-and-research foundation with no approved production schemas, game runtime, automated tests, CI configuration, or native repository instruction file. Those absences are constraints on this design, not permission to invent a stack.

## Evidence and status convention

- **Finding — verified:** directly supported by an inspected project file or cited primary source.
- **Inference:** a bounded architectural conclusion drawn from findings; it is not an established project decision.
- **Recommendation:** a proposed control for the Creative Director or a future approved implementation task.
- **Unverified / deferred:** cannot be settled from the current repository and must not be treated as approved.
- **Machine-enforceable:** a deterministic system can detect or block a declared condition once its data and execution layer exist.
- **Human-judgment gate:** accountable review is required because the question concerns meaning, interpretation, historical plausibility, cultural authenticity, reverence, or an unresolved creative tradeoff.

The controlling authority is the User / Creative Director, followed by the witness-centered core vision, biblical source-text commitments, established canon/scope decisions, and then the Master Assistant Protocol. Lower artifacts cannot silently override higher ones ([Master Protocol §§2–5, pinned repository snapshot](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L25-L137)).

## 1. Enforcement principles

### 1.1 Put each control at the layer that can actually enforce it

**Finding — strong.** The project already states permanent constraints in the Master Protocol, but prose alone cannot stop a future data record from omitting a source, a runtime system from damaging a protected figure, or a save migration from altering a fixed outcome. Conversely, a validator can require a `confidence` field but cannot decide whether an artistic depiction is reverent. Session 12 reached the same division: sacred and historical controls need schema/static, runtime/scenario, and human-review oracles, with each making only claims its evidence supports ([Session 12 §8](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/12_Game_Validation_and_Play_Verification_Architecture.md#L268-L292)).

**Recommendation.** Use seven cooperating layers:

1. **Human authority:** the Creative Director and named Scripture/theology, history/culture, visual, gameplay, data, engineering, and QA reviewers make accountable decisions.
2. **Permanent governance:** the Master Protocol and any future approved repository instruction layer state non-optional authority, prohibitions, and escalation. These rules apply whether or not a skill is invoked.
3. **Workflow skills:** narrow, conditional procedures discover current sources, collect required fields, run approved checks, and stop or escalate. A skill cites authority; it does not become authority or a permission boundary.
4. **Reference and data records:** versioned source, chronology, event, era, knowledge, asset, decision, and provenance records make constraints addressable rather than implicit.
5. **Schemas, validators, tests, and CI:** deterministic controls reject missing or invalid fields, broken references, prohibited declared states, regressions, unapproved paths, and incomplete evidence.
6. **Runtime, editor, and tool permissions:** capability-level controls prevent prohibited interactions, unauthorized mutation, credential/network misuse, and accidental changes to protected material.
7. **Review and evidence:** specialist and stewardship gates evaluate meaning and record what was inspected, what passed, what failed, who decided, and what remains uncertain.

No one layer substitutes for the others. A skill is especially unsuitable as the sole carrier of sacred-event, witness, source-separation, or no-invention rules because Codex skills are conditionally selected, while permanent repository instructions are a separate mechanism ([current Codex skill guide](https://learn.chatgpt.com/docs/build-skills), [current `AGENTS.md` guide](https://learn.chatgpt.com/docs/agent-configuration/agents-md), both checked 2026-07-22; [Session 3 analysis](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md#L27-L66)).

### 1.2 Separate declaration, detection, prevention, and approval

Every control must state its mode:

| Mode | Question | Example | Honest claim |
|---|---|---|---|
| Declarative | What rule or classification was recorded? | `source_category = canonical_scripture` | “The record declares this category.” |
| Detective | Can a violation be found? | Validator reports missing edition/locator | “The declared metadata is incomplete.” |
| Preventive | Can an effect be blocked? | Runtime refuses damage against a protected entity | “This tested effect path was blocked.” |
| Approval | Who judges contextual fitness? | Theology reviewer approves disputed-view wording | “The named reviewer approved this version under the recorded rationale.” |

A declaration is not proof of truth. A passed static check is not proof of runtime behavior. A runtime invariant is not a theological ruling. A human approval without reproducible evidence is not an automated guarantee.

### 1.3 Preserve one canonical owner and many derived controls

Each requirement needs one authoritative owner, even when represented in several layers. Derived schemas, tests, skills, UI labels, and runtime policies should carry a stable requirement ID and an authority link rather than copy changing prose. When a higher-authority decision changes, its supersession record should identify dependent data, tests, content, saves, and evidence that require review.

### 1.4 Fail closed on prohibited effects; fail explicit on missing knowledge

- A protected-figure action that lacks an approved rule should be denied safely, not assumed harmless.
- Missing or conflicting source, chronology, license, provenance, schema, or approval data should produce an actionable blocked/unknown state, not invented content.
- A missing optional visual or convenience service may degrade safely only when the degradation is specified and cannot fabricate project truth.
- Tool unavailability means **not validated**, not passed. Session 12 defines this truthful fallback explicitly ([Session 12 §11](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/12_Game_Validation_and_Play_Verification_Architecture.md#L355-L368)).

### 1.5 Enforce process without manufacturing certainty

Machine controls can require that a disputed location has alternatives, confidence, citations, and a visible player-facing label. They cannot prove which disputed location is correct. The system should preserve disagreement as data and route the decision to the appropriate human authority instead of collapsing it into one “clean” fact.

### 1.6 Minimize privilege and blast radius

Skills and agents should receive only the files, tools, write paths, and external connections needed for the assigned workflow. Scripts require independent review; skill prose neither installs a tool nor grants safety. This follows the risk evidence in Session 6, which distinguishes prose instructions from sandbox, approval, filesystem, network, connector, credential, and Git controls ([Session 6 §§5–6](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md#L121-L153)).

## 2. Constraint-to-layer matrix

The matrix is normative architecture guidance, not an implemented schema. “Canonical owner” means who or what may authorize a change to the constraint. “Trace” is the minimum evidence chain a future implementation should preserve.

| ID / constraint | Canonical owner | Canonical representation | Automated / preventive enforcement | Human enforcement | Primary failure or bypass | Escalation and required trace |
|---|---|---|---|---|---|---|
| SRC-01 Scripture citation and locator | Biblical source-text commitments; Scripture/Theology reviewer | Source record: work, canon category, book/passage, edition/witness, language, stable locator | Required fields; resolvable source ID; quote-to-source comparison where licensed text is available | Reviewer verifies passage use and that a locator supports the claim | Plausible but unrelated verse; edition omitted; OCR treated as clean text | Block publication; route to Scripture reviewer; retain claim ID, source revision, verification date/result |
| SRC-02 Source/category separation | Master Protocol; Creative Director for project canon policy | Controlled category registry: Scripture, Deuterocanonical/Apocryphal, Enochic/Second Temple, ancient source, archaeology, scholarship, tradition, reconstruction, speculation, paraphrase | Enum and UI-label checks; incompatible-category rules; no missing category | Theology/history review ambiguous boundary cases | Non-canonical material silently presented as Scripture | Block content; Creative Director resolves canon/scope; trace category, rationale, approver, supersession |
| SRC-03 Interpretation, reconstruction, speculation, paraphrase status | Relevant specialist; Master Protocol defines required separation | Claim record with `claim_status`, `interpretation_status`, `confidence`, rationale | Presence/enum/label checks; paraphrase cannot use Scripture-quotation presentation | Specialist judges whether the label is honest | Invented connective text laundered as a factual or biblical claim | Return for relabel/research; preserve before/after claim and reviewer reasoning |
| SRC-04 Original-language verification | Scripture/Theology reviewer | Textual-witness/lexeme record with edition, passage, language, form, analysis, verifier | Require approved witness and locator; detect unverified OCR-derived status | Qualified review of reading, morphology, semantic range, and contextual claim | Fabricated Hebrew/Aramaic/Greek; corrupted OCR silently normalized | Do not publish as verified; record disputed/unverified state and exact witness consulted |
| SRC-05 Translation copyright and quotation handling | Creative Director plus rights/legal owner | Translation registry: rights holder, edition, license/permission, allowed uses/limits, attribution | Approved-translation allowlist; quote-length/use policy; build/package audit | Rights/legal review where status is unclear; editor reviews paraphrase label | Copying a restricted translation or treating absence of notice as permission | Quarantine content; obtain permission or replace; retain license evidence and decision |
| SAC-01 Fixed sacred outcomes | Core witness vision; Creative Director stewardship approval | Protected-event record with immutable anchor/outcome ID and allowed variable consequences | Schema const/immutability rules; runtime state machine; save migration invariant; adversarial scenario suite | Theology/stewardship review of what constitutes the protected outcome | Optional branch, sequence break, debug path, or migration changes the event | Stop release; incident to Creative Director and engineering/QA; trace every path, save, build, test, and exception |
| SAC-02 Protected figures and prohibited effects | Master Protocol; event-specific stewardship approval | Entity/event protection policy: protected IDs, phase, denied effects, allowed interactions | Central targetability/effect authorization; damage/theft/displacement/AI/environment denial; tests | Review whether the portrayal preserves dignity, not merely invulnerability | Area effects, physics, companion AI, inventory, dialogue, or load bypass direct attack filter | Fail closed; critical defect; record attempted effect, system path, state, log, capture, fix, regression |
| SAC-03 Witness premise and bounded agency | Core vision; Creative Director with gameplay and theology reviewers | Event interaction contract: allowed witness verbs, prohibited authorial verbs, ordinary-person consequences | Quest/action graph constraints; at least one allowed-action scenario; fixed-anchor tests | Playtest and stewardship review meaning, moral pressure, and emotional agency | Restrictions reduce play to passive spectacle, or “agency” replaces a biblical figure | Return to design gate; trace intended verb, consequence, player observation, reviewer decision |
| CHR-01 Era and timeline consistency | Approved chronology authority; Scripture reviewer | Era/event records, alternative chronology tracks, temporal relationships and validity ranges | Reference-graph and interval checks; impossible order/cycle checks; fixture-specific timeline validation | Reviewer evaluates disputed harmonization and interpretive assumptions | One “clean” timeline erases textual witnesses or uncertain dates | Block promotion; preserve every track/source/confidence; Creative Director decides presentation, not textual facts |
| CHR-02 In-world knowledge boundary | Era authority; Scripture/Theology reviewer | Knowledge assertion with audience/scope, available-from event/date, region/community, source and confidence | Dialogue/NPC queries limited by scope; later-source leakage checks; negative fixtures | Reviewer judges plausible implication, oral knowledge, cultural variation | A first-century character speaks from later Scripture or modern scholarship | Block affected content; trace assertion, speaker/era, source, validator and reviewer outcome |
| CHR-03 Player-facing codex separation | Codex spec owner; Scripture/Theology reviewer | Separate player-codex record/view model linked to but not injected into NPC knowledge | Distinct storage/API/view; UI tests; prohibited dependency direction | Review clarity and whether later connections are labeled | Shared text blob leaks fulfillment/manuscript commentary into the world | Return to data/design; record layer, audience, source/category and screenshot/state evidence |
| HIS-01 Historical confidence and competing views | History/Geography/Culture reviewer | Claim with evidence category, confidence vocabulary, alternatives and dissent notes | Required confidence/source fields; no single-value collapse when alternatives declared | Specialist assigns and reviews confidence; Creative Director approves game translation | “Disputed” becomes a confident map, costume, or lore statement | Block authority promotion; retain alternatives, reviewer/date, game-design rationale and visible label |
| HIS-02 Geography and composite locations | History reviewer; Creative Director approves stylization | Location model with textual data, candidate hypotheses, composite/stylized flag and presentation label | Composite flag required when multiple candidates are merged; label-presence tests | Specialist assesses defensibility; stewardship review avoids false certainty | Composite is marketed or displayed as the discovered biblical site | Return to map/codex gate; trace components, sources, confidence, label and approval |
| HIS-03 Material culture and visual/cultural authenticity | History and Visual Research reviewers; Creative Director final | Asset/brief record: era, region, people, function, sources, confidence, reconstruction status, exclusions, provenance/license | Metadata completeness; era/region compatibility; asset dependency and license checks | Human review ethnicity, dignity, stereotype, symbolism, sacred-figure treatment and contextual plausibility | Westernized default, fantasy exaggeration, or generated image with untraceable references | Quarantine asset; trace prompt/source files, model/tool if used, license, edits, reviews, decision |
| DAT-01 Schema approval before structured content | Creative Director plus Schema/Content Engineer | Versioned approved schema and approval record; content declares schema ID/version | CI rejects unapproved/missing schema; generators require schema input; no unknown-field bypass | Data owner approves semantic model and migration consequence | Agent invents fields/path or labels a proposal “approved” | Stop generation/implementation; open schema-design task; trace schema SHA, approver and affected artifacts |
| DAT-02 Stable IDs, references, dependencies and generated content | Approved schema owner | Namespaced immutable IDs; typed references; dependency graph; generator provenance | Uniqueness, referential integrity, cycle/range/enum checks; generated output validates identically to authored content | Reviewer checks relationships are meaningful and not just syntactically valid | Duplicate IDs, dangling refs, invented fallback, generator bypasses validation | Block merge/build; trace generator/version/input hash, diagnostics and corrected output |
| DAT-03 Migrations and save compatibility | Systems/data owners; Creative Director for acceptable loss | Schema/save versions, migration graph, invariants, compatibility and recovery policy | Forward/backward fixture tests as approved; protected-anchor and knowledge invariants across migrations | Human approval of player-impacting loss, reset or incompatibility messaging | Migration “fixes” invalid data by deleting testimony or changing sacred outcomes | Stop release; preserve pre/post fixtures and migration log; explicit waiver only by named authority |
| PRO-01 Provenance and licensing | Artifact owner plus rights/legal approver | Artifact manifest: origin, creator/tool, revision/hash, source chain, license/permission, transformations, restrictions | Missing-license quarantine; hash/dependency verification; distribution allowlist | Human reviews ambiguous ownership, fair-use/permission questions, sacred/research-source suitability | Copied asset, skill, code, text, or dataset has unclear rights or altered attribution | No reuse/distribution; record `unknown/no assertion`, investigation, decision and evidence; never infer permission |
| CON-01 Authority, decisions, exceptions and supersession | Creative Director | Decision/ADR record with ID, status, authority, rationale, alternatives, scope, dependencies, supersedes/superseded-by | Reference/link validation; stale-dependency report; expired-exception check | Approver confirms decision and explicit exceptions | Handoff summary or old dossier silently becomes authority | Stop affected task; current-source audit; trace conflict, authority comparison, decision and impacted files |
| CON-02 Handoff and continuity | Current task owner; recipient verifies | Handoff points to canonical records and exact repository SHA; it carries state, not new authority | Required-section/link/SHA checks; compare listed state with repository | Sender and recipient verify open work, unresolved questions and next action | Compressed handoff invents, drops, or silently resolves a decision | Correct before continuation; retain discrepancy and source-of-truth link |
| CON-03 File, Git and scope integrity | Creative Director/file manifest owner; repository maintainer | Approved file manifest/path policy, task write allowlist, protected paths, change brief | Dirty-state/predecessor checks; path/diff allowlist; duplicate/suffix scan; tests; branch/ruleset gates when approved | Reviewer confirms no disguised scope expansion and accepts intended diff | Unrelated refactor, production edit, force push, stale-head overwrite, versioned duplicate | Abort publication; reconcile newest head; trace base/head SHAs, exact diff, checks, reviewer and exception |
| GMP-01 Gameplay meaning | Creative Director; Gameplay Systems Designer | Mechanic purpose record linking ordinary-life, moral, progression, relationship, Scripture/codex, or world consequence | Require purpose/consumer/producer links and scenario coverage; orphan-system report | Design/playtest gate judges whether the loop is meaningful rather than grind | Mechanic passes data tests but adds detached repetition or power fantasy | Return to design; cut/merge/reframe/codex-only decision with playtest evidence |
| GOV-01 Cross-artifact conflict and conditional workflow | Authority chain; main agent/router only within delegated task | Task contract names authorities, required inputs, active workflows, output allowlist and escalation | Preflight current sources and capability; composition trace; write/tool restrictions | Human resolves substantive biblical, historical, scope, or creative conflict | A broad skill, role prompt, or agent instruction overrides permanent policy | Stop; apply higher authority; record conflict and disposition; do not “average” instructions |

### Layer-selection conclusion

**Finding.** Universal constraints belong in permanent governance, not only in skills. Domain truth and uncertainty belong in governed records, not prompt memory. Structural invariants belong in schemas and validators. Prohibited runtime effects belong in capability-level code plus regression tests. Meaning, reverence, disputed interpretation, cultural authenticity, and major exceptions belong at named human gates.

**Recommendation.** Skills should perform bounded workflows such as collecting a source packet, validating a content package, or assembling an evidence trace. They should not become a universal “Bible expert,” a mega-policy container, or the only defense against prohibited behavior. This follows the taxonomy's warning that conditional activation is unsafe for permanent policy and that a guardrail is not itself technical enforcement ([Session 2 §§5–6](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md#L88-L115)).

## 3. Biblical-source integrity architecture

### 3.1 Claim-centered, not document-centered, provenance

**Recommendation.** Give each substantive claim a stable ID and record the following in an eventual approved schema:

- exact claim text or structured assertion;
- status: quotation, paraphrase, project finding, interpretation, historical reconstruction, creative proposal, recommendation, or unverified;
- source category and canon category;
- source ID, exact locator, edition/textual witness, language, revision/date, and durable link where permitted;
- quote/paraphrase status, rights/permission status, and required attribution;
- confidence and rationale;
- competing claims or textual variants;
- verifier, verification method, date, and scope;
- downstream uses: codex, dialogue, quest, region, visual brief, chronology, schema fixture, or loading text; and
- supersession and revalidation state.

This separates three different questions: **what the source says**, **how the project interprets it**, and **how the game translates it**. A document-level bibliography cannot reliably answer which source supports a specific sentence or which content must be revisited after a source correction.

### 3.2 Canon and evidence-category registry

The Master Protocol already requires explicit separation among canonical Scripture, Apocrypha/Deuterocanonical material, Enochic/Second Temple literature, historical tradition, speculative expansion, and optional exploration content ([Master Protocol §8.3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L471-L482)).

**Recommendation.** Do not force every evidence type into that canon list. Use two linked dimensions:

1. **Religious/textual category:** the project's approved canon-handling category.
2. **Evidence/function category:** biblical text, manuscript/textual witness, ancient literary source, inscription/material evidence, archaeology, modern scholarship, artistic tradition, historical reconstruction, game-design composite, speculation, or assistant paraphrase.

Both dimensions require controlled vocabulary and a visible player-facing rendering policy. A validator can prevent a missing category or invalid combination. It cannot decide the project's final canon policy or whether a contested interpretation is doctrinally appropriate; those remain Creative Director and Scripture-review decisions.

### 3.3 Original-language verification and OCR quarantine

**Finding — repository-specific.** The two large OCR corpora have unverified provenance/edition/licensing and visible corruption; Session 1 explicitly prohibits treating them as validated quotation sources. The Genesis chronology synthesis also cautions that MT/LXX values need verification against clean critical editions before authoritative database promotion ([Session 1 research-corpus audit](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md#L233-L245), [chronology method note](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/genesis_5_11_mt_lxx_chronology_comparison.md#L9-L26)).

**Recommendation.** Mark OCR-derived observations `unverified_ocr`; prohibit direct promotion to “verified quotation” or original-language fact. Verification must record a clean edition/witness, exact passage, textual form, and human verifier. Normalization should preserve the original observation and correction trace rather than silently replacing characters. A lexical gloss never proves that one English word is correct in every context; semantic interpretation remains a review question.

### 3.4 Copyright-aware translation handling

The Master Protocol requires translation/source limitations to be respected and assistant paraphrases to be labeled rather than presented as Scripture ([Master Protocol §9](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L486-L513)).

**Recommendation.** Maintain an approved translation registry rather than a vague “Bible text allowed” flag. For each edition, record rights holder, edition/year, jurisdictional assumptions if relevant, license or written permission, use classes, quotation limits, attribution wording, modification/paraphrase rules, platform/territory constraints, evidence location, and review date. Missing status is **unknown**, not public domain. Build/export checks can ensure only approved IDs are packaged and required notices are present; a rights/legal human must resolve ambiguity.

### 3.5 Promotion gate

A claim may move from research to production-authoritative content only when:

1. required source, category, status, confidence, rights, and locator fields validate;
2. all cited records resolve to pinned or otherwise durable sources;
3. OCR or machine-generated observations are independently verified where required;
4. competing material is represented rather than suppressed;
5. the relevant specialist approves substance and labels;
6. the Creative Director approves canon/scope or major portrayal decisions; and
7. downstream references and evidence are regenerated against the accepted revision.

## 4. Sacred-event protection architecture

### 4.1 Event policy model

**Recommendation.** Every protected event eventually needs an approved record containing:

- stable event and phase IDs (`approach`, `active`, `aftermath`, or event-specific equivalents);
- governing Scripture/source claims and approved interpretation boundaries;
- canonical fixed outcome and invariants that must survive every branch, reload, migration, accessibility setting, and supported difficulty;
- protected figures/entities and phase-specific protection;
- allowed witness verbs and meaningful ordinary-person consequences;
- prohibited authorial/exploitative verbs and equivalent effects;
- permitted movement, camera, UI, tool, inventory, dialogue, AI, physics, environmental, and quest behaviors;
- fail-safe transition and recovery behavior;
- save/load rules;
- required automated scenarios and human approvals; and
- exception policy with named authority, scope, expiry, and rationale.

The policy record must distinguish **event truth** from **implementation mechanism**. “The outcome is fixed” is a governing invariant. “Disable component X” is an engine-specific technique that cannot be selected before the engine and architecture exist.

### 4.2 Capability-level prevention

**Recommendation — future runtime.** Centralize authorization for effects against protected targets. Every authorized effect path—direct attack, area damage, collision, physics impulse, fire/environment, companion/NPC AI, inventory transfer, theft, dialogue state mutation, quest cancellation, navigation displacement, event skipping, save restore, migration, editor/debug interfaces shipped to players, and any future mod or network surface—must ask the same authoritative policy or be structurally unable to act.

Do not scatter only UI disables across scenes. UI state can communicate a restriction, but the authoritative target/effect layer must reject the effect. The fixed outcome should also be asserted by the event state machine and persistence model so bypassing one interaction filter cannot rewrite history.

### 4.3 Required negative and positive tests

For each event phase and supported state transition:

- attempt every prohibited verb through every authorized effect-producing system;
- enter via normal, boundary, alternate-route, reload, resume, skip, recovery, and migration paths;
- assert protected figures remain untargetable/undamaged/unexploited and fixed anchors unchanged;
- assert the event still reaches the approved outcome;
- assert at least one intended witness action works and produces an approved consequence;
- inspect logs for silent denials, exceptions, or state corruption; and
- preserve scenario, seed/fixture, build, state, logs, captures, and reviewer decision.

This follows Session 12's adversarial-regression model and should remain abstract in fixtures: tests defend the product; they should not create a reusable catalogue of sacrilegious mechanics ([Session 12 §8.2](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/12_Game_Validation_and_Play_Verification_Architecture.md#L284-L288)).

### 4.4 Prohibited-action examples and required responses

| Attempt | Required machine result | Required human question | Evidence |
|---|---|---|---|
| Target or damage a protected figure directly | No target acquisition; no effect; fixed state unchanged | Does the staging communicate dignity rather than a gamey “invulnerable NPC”? | Input trace, policy decision, state before/after, log and capture |
| Cause area/environment/physics damage | Effect filtering or structural separation prevents impact | Are hazards framed without trivializing the event? | Effect-source ID, collision/effect log, protected state |
| Steal, trade, move, despawn, recruit, customize, or exploit a sacred figure | Operation unavailable and rejected below the UI | Are allowed interactions reverent and era-appropriate? | Command/result, inventory/entity diff, UI capture |
| Coerce dialogue into replacing a central biblical decision | No branch can assign the player's choice to the protected outcome | Does the scene preserve the central figure's agency and Scriptural role? | Dialogue graph coverage, branch traces, review notes |
| Cancel, sequence-break, or reload to prevent the event | Canonical anchor persists; recovery reaches approved state | Is constrained movement/transition clear rather than arbitrary? | Route matrix, save fixtures, event-state trace |
| Perform Jesus' miracle or convert divine action into a player cooldown/reward loop | Capability absent; no unlock/data definition exists | Does nearby agency remain meaningful without appropriating the miracle? | Schema absence/policy test, scenario and stewardship review |
| Mock, farm, loot, or repeatedly exploit event presentation | Rewards, loops, and inputs cannot incentivize the behavior | Could audiovisual/UI framing accidentally invite trivialization? | Economy/reward trace, repetition scenario, playtest observation |

### 4.5 Human stewardship remains mandatory

A machine can prove only the specified state/effect paths. The Creative Director and named theology, narrative, visual/audio, gameplay, and representative player reviewers must evaluate reverence, emotional weight, implied causation, dignity, meaning, and whether restrictions still allow morally significant witness agency. “Protected” must not mean merely indestructible.

## 5. Chronology and knowledge architecture

### 5.1 Multiple chronology tracks

**Finding — strong project example.** The repository's Genesis 5–11 comparison explicitly warns against collapsing MT and LXX into one false-clean timeline and models witness-specific tracks plus disputed variants ([chronology comparison §§1–3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/genesis_5_11_mt_lxx_chronology_comparison.md#L9-L119)).

**Recommendation.** Represent temporal claims as a graph with stable events and relations, not only absolute dates. Permit parallel `chronology_track_id`s, witness/interpretation source, uncertainty/range, confidence, and rationale. Validators can detect cycles, impossible declared order, missing track identity, or values outside declared ranges. They cannot select a disputed harmonization as true.

### 5.2 Era-aware knowledge assertions

Every in-world knowledge unit should eventually declare:

- assertion/claim ID;
- speaker/community/role scope;
- era and earliest plausible availability event/date/range;
- geographic/cultural transmission scope where relevant;
- source category and whether the knowledge is direct, oral, inferred, rumored, disputed, or hidden;
- confidence and reviewer; and
- prohibited later-source dependencies.

A runtime content query should request knowledge for an in-world audience and never default to the unrestricted player codex. Static analysis can flag a dialogue record linked to a later-only assertion. Semantic review must still judge indirect implication, prophecy, oral transmission, narrator voice, and culturally plausible knowledge.

### 5.3 Separate authoring and delivery paths

**Recommendation.** Treat in-world content and player-facing codex content as different typed records or projections with a one-way approved relationship: in-world events may unlock player codex entries, but player-codex commentary must not become an NPC dialogue source merely because both discuss the same passage. Separate APIs/view models and UI tests should confirm the distinction.

The Master Protocol states that in-world characters are limited to plausible era knowledge, while the player-facing codex may provide later biblical connections, manuscript notes, original-language study, and theological context ([Master Protocol §8](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L451-L482)).

### 5.4 Anachronism and leakage detection

Use three levels:

1. **Deterministic:** IDs, dates/ranges, declared technologies/materials, named texts, office/political structures, and vocabulary records with known validity constraints.
2. **Candidate detection:** controlled search or model-assisted review can flag possible later concepts, modern idiom, Western assumptions, or cross-era reuse. Candidates are not verdicts.
3. **Specialist review:** Scripture and history reviewers assess nuance, disputed dating, translation choices, intentional narrator framing, and cultural plausibility.

Every accepted exception must record whether it is a player-facing explanation, translated idiom, deliberate composite, accessibility concession, or creative choice. It must not silently alter the in-world truth model.

## 6. Historical-confidence and provenance architecture

### 6.1 Confidence is attached to a claim, not an entire file

The History/Geography role already requires `High`, `Medium`, `Low`, `Disputed`, `Unknown`, or `Symbolic`, while separating biblical data, ancient sources, archaeology, scholarship, and game reconstruction ([Master Protocol §6.4](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L214-L236)).

**Recommendation.** A confidence value must name its dimension: textual reading, event order, absolute date, geographic identification, material-culture fit, visual reconstruction, or game translation. One claim can be high for event order and low for absolute date. Require rationale and evidence; never calculate a false universal score by averaging unlike dimensions.

### 6.2 Competing views and game translation

For each disputed reconstruction, preserve:

- each candidate view and its strongest sources;
- evidence for and against;
- confidence by dimension;
- what is unknown or unavailable;
- selected game translation, if any;
- why that translation is playable and honest;
- required visible label; and
- dissent, reviewer, approval date, and re-review trigger.

A composite environment may be appropriate, but `composite` is a required truth-bearing label, not an embarrassment to hide. Promotion tests should fail if disputed alternatives were collapsed without an approved decision record.

### 6.3 Material culture, character, and visual records

Every asset or prompt brief should link era, region, people/community, occupation/status, function, materials, direct textual description if any, historical analogues, reconstruction choices, symbolic/tradition content, confidence, and exclusions. Sacred figures need explicit stewardship approval. Automated compatibility checks can catch an asset tagged to the wrong era/region or missing provenance; they cannot certify ethnicity, dignity, stereotype avoidance, authenticity, or reverence.

### 6.4 Provenance and licensing chain

For code, skill packages, tools, assets, research data, generated media, translations, and third-party text, record origin, exact revision/hash, creator/source, acquisition date, transformations, declared and concluded license/permission, notices, distribution limits, and decision. The SPDX 3.0.1 specification distinguishes license information found in an artifact from a concluded license and treats missing information differently from an explicit no-assertion state; this is a useful model, not a mandated project format ([SPDX 3.0.1 Licensing profile](https://spdx.github.io/spdx-spec/v3.0.1/model/Licensing/Licensing/), published 2024; [SPDX scope](https://spdx.github.io/spdx-spec/v3.0.1/scope/)).

**Recommendation.** Unknown rights status blocks reuse or distribution. It should not be “fixed” by an LLM guess. Generated assets must record the tool/model/service and version when available, prompt/source inputs, account/license terms snapshot or durable evidence, human edits, and output hash, while respecting privacy and source rights.

## 7. Schema-first architecture

### 7.1 Approval state precedes content generation

The Master Protocol states that structured content or system implementation must not proceed without an approved schema or an explicit schema-creation task ([Master Protocol §10](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L517-L540)). No approved schema is present at the inspected commit.

**Recommendation.** A future schema registry should distinguish `proposal`, `under_review`, `approved`, `deprecated`, and `retired`. Only a named schema owner/approver can change approval state. A content generator must receive the exact approved schema ID and version as input; it may not infer one from examples.

### 7.2 Structural and semantic validation

Use complementary controls:

- **Schema validation:** required properties, types, enums, patterns, bounds, closed/unevaluated properties where appropriate, and conditional structure. JSON Schema Draft 2020-12 provides standardized core and validation vocabularies; choosing it or another technology is deferred until the project selects its data stack ([JSON Schema Core 2020-12](https://json-schema.org/draft/2020-12/json-schema-core.html), [Validation 2020-12](https://json-schema.org/draft/2020-12/json-schema-validation.html)).
- **Semantic validators:** stable-ID uniqueness, referential integrity, chronology/knowledge rules, category/label compatibility, protected-event invariants, license allowlists, and graph constraints.
- **Fixtures/tests:** known-valid, known-invalid, boundary, migration, generation, and adversarial examples.
- **Human review:** whether the modeled fields and relationships faithfully represent the project's meaning.

Schema success alone does not prove a source is correct, a mechanic is meaningful, or an event is reverent.

### 7.3 Stable identifiers and dependencies

IDs should be immutable, namespaced, opaque to display wording, and never recycled. Renaming presentation text must not change identity. Every reference needs an expected type and validation. Dependency reports should identify what a source, decision, schema, event, asset, or ID change affects.

Generated content must pass the same validators and approvals as authored content and additionally record generator identity/version, prompt/configuration, exact input hashes, time, output hash, diagnostics, and human disposition. “AI-generated” is neither a pass nor a failure; provenance and acceptance determine use.

### 7.4 Migrations and save compatibility

Every schema or save-format change should declare:

- source and target versions;
- forward/backward support policy;
- preconditions and irreversible effects;
- protected invariants, including fixed event anchors, testimony/lineage, knowledge scope, provenance, and stable IDs;
- valid, boundary, corrupt, and unsupported-version fixtures;
- rollback/recovery and player messaging; and
- evidence and approver.

A migration must never silently discard an unknown field merely to make validation pass. Unrecognized protected data should fail safely for investigation. Compatibility promises and acceptable data loss are user/product decisions, not assumptions.

### 7.5 Schema-change gate

1. Create a scoped schema/ADR proposal tied to authority and use cases.
2. Review domain meaning before producing content.
3. Validate examples and invalid cases.
4. Map dependent content/runtime/save/evidence.
5. Approve and assign immutable version.
6. Generate or edit content only against that version.
7. Run structural, semantic, migration, and product-specific gates.
8. Human-review representative output.
9. Record supersession and compatibility consequences.

## 8. Continuity and authority architecture

### 8.1 Canonical records versus handoffs

The current handoff template is designed to compress context, decisions, repository state, open threads, and the next action for another assistant ([Continuity Handoff Prompt](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md#L1-L28)). It is a transfer mechanism, not an approval mechanism.

**Recommendation.** A handoff must point to canonical decision, schema, source, and file records at exact revisions. It may summarize but cannot originate or silently resolve authority. Recipient preflight should verify repository SHA, dirty state, current files, unresolved conflicts, and superseded decisions before mutation.

### 8.2 Decision/ADR contract

Each durable decision or exception should include:

- stable ID, title, status, date, owner and approver;
- authority basis and exact repository/source revisions;
- problem, scope, alternatives, decision and rationale;
- findings separated from recommendations;
- biblical/historical/sacred/schema/continuity implications;
- affected IDs/files/tests/saves/assets/skills;
- unresolved dissent and confidence;
- expiration/review trigger;
- supersedes and superseded-by links; and
- verification/evidence required before closure.

Not every small implementation choice needs a formal ADR. Use one when a decision crosses systems, changes an authority interpretation, creates a durable contract, selects a stack/dependency, or accepts a material exception.

### 8.3 Current-source and conflict preflight

Before each governed task:

1. resolve current repository head and worktree state;
2. read applicable higher-authority files and their revision;
3. inspect the file manifest, approved schema/spec, decision records, and direct dependencies;
4. compare the task with protected paths and write allowlist;
5. identify ambiguous or conflicting instructions;
6. select only necessary workflows/tools and state their permissions;
7. define acceptance and prohibited outcomes; and
8. stop for authority resolution when a substantive conflict remains.

Skills may automate this preflight, but the main agent/human owner resolves conflicts. The project must not rely on same-name skills, prompt ordering, or a “stronger sounding” persona as precedence; Session 3 found no documented universal priority ladder among simultaneously selected Codex skills ([Session 3 §5](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md#L134-L157)).

### 8.4 File and Git controls

**Recommendation — target controls, not current implementation claims.**

- Maintain a file manifest with canonical path, artifact class, owner, authority/status, schema if any, and replacement/supersession rules.
- Give each task an explicit write allowlist and prohibited paths; reject any diff outside it.
- Require known-clean or explicitly declared dirty state, current-head comparison, and no force-push/overwrite of competing work.
- Detect casual suffix duplicates such as `_v2`, `_final`, `_new`, and `_latest`, consistent with the Master Protocol's file rules ([Master Protocol §11](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L544-L588)).
- Require scope-specific checks and review before publication; test or baseline changes receive the same scrutiny as production changes.
- Protect governance, approved schemas, validators, tests, sacred-event records, licenses, and release evidence with named review ownership.
- After CI exists, consider GitHub rulesets/branch protection to require approved status checks, restrict updates/force pushes, and make bypass explicit. GitHub documents that rulesets can layer and can require checks or restrict updates; exact settings, availability, actors, and bypass policy remain a repository-owner decision ([GitHub rulesets overview](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets), [available rules](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets), checked 2026-07-22).

### 8.5 Composition trace

Every agent-assisted change should preserve a compact trace:

- task and output contract;
- repository base/head and applicable authority revisions;
- role/agent and invoked skills with package revision;
- references actually loaded;
- tools/scripts/services and versions;
- permissions, network/credential/data exposure and approvals;
- files read/written and exact diff;
- validators/tests/human gates and outcomes;
- unresolved questions, exceptions and owner; and
- final commit/artifact/evidence identifiers.

This trace makes conditional workflow influence visible without pretending to capture private chain-of-thought.

## 9. Automated versus human enforcement

### 9.1 Decision table

| Question | Deterministic enforcement | Model-assisted candidate detection | Mandatory human judgment |
|---|---|---|---|
| Does every claim have source/category/confidence fields? | Yes | Not needed | Approves field meaning and evidence fit |
| Does the cited passage/locator exist in an approved source? | Often, once a licensed/verified corpus exists | Can help locate mismatches | Verifies interpretation and textual nuance |
| Is a claim Scripture, interpretation, reconstruction, or speculation? | Enforce declared allowed values | Flag likely mislabeling | Decides contested classification |
| Is Hebrew/Aramaic/Greek accurate? | Compare exact forms to an approved witness; enforce verification status | Flag anomalies | Qualified contextual and textual review |
| Is quotation use legally permitted? | Apply approved registry rules | Flag unmatched text | Rights/legal decision for ambiguity |
| Can a protected figure be damaged or exploited by tested paths? | Yes, through runtime/scenario assertions | Generate test candidates only | Judges dignity, tone and implied causation |
| Does a sacred outcome remain fixed? | Yes for modeled/reachable tested state paths | Explore likely sequence breaks | Confirms the approved theological/narrative boundary |
| Is witness agency meaningful? | Require allowed paths and observable consequences | Summarize behavioral evidence | Gameplay/stewardship/playtest judgment |
| Does content use a declared later-only assertion in-world? | Yes | Flag semantic leakage/modern idiom | Judges implication and plausible knowledge |
| Is a disputed geography or visual reconstruction honest? | Require confidence/alternatives/composite label | Flag inconsistent wording/images | Specialist and Creative Director approval |
| Does content validate against its approved schema? | Yes | Not needed | Approves schema's semantic adequacy |
| Are IDs/references/migrations structurally safe? | Yes for specified invariants | Identify suspicious patterns | Approves compatibility and acceptable loss |
| Is an asset/source licensed and traceable? | Require registry evidence/hash/allowlist | Flag missing or conflicting metadata | Rights/provenance review decides reuse |
| Did a task stay within file/Git scope? | Yes, using base/head/diff allowlist | Summarize semantic scope | Reviewer judges disguised or unjustified expansion |
| Is a mechanic biblically immersive rather than grind? | Require purpose link and scenario evidence | Analyze playtest signals | Creative/gameplay/player judgment |

### 9.2 Review-gate minimums

- **Scripture/theology:** source use, canon/category, interpretation, original language, era knowledge, sacred boundary.
- **History/geography/culture:** evidence separation, confidence, competing views, material and visual plausibility.
- **Gameplay:** meaningful ordinary-life loop, moral pressure, bounded agency, non-exploitative reward design.
- **Data/engineering/QA:** schema/reference/runtime/save invariants, negative paths, reproducibility, security, and truthful result labels.
- **Rights/provenance:** translations, source corpora, code/dependencies, skills, assets, generated media, and notices.
- **Creative Director stewardship:** canon/scope, sacred portrayal, witness premise, major reconstruction, exceptions, and release acceptance.

Separation of duties is preferred for high-risk gates: the author or generating agent should not be the only approver of its own source interpretation, baseline, validator, sacred-event behavior, or exception.

## 10. Failure and bypass analysis

| Failure/bypass | Why a single-layer rule fails | Required defense | Detection/evidence |
|---|---|---|---|
| “Confidence: high” with no evidence | Enum validates but claim is unsupported | Rationale, sources, specialist gate and sampling audit | Claim-to-source trace and reviewer record |
| Correct citation attached to unrelated assertion | URL presence is syntactically valid | Claim-level locator comparison and human interpretation review | Exact passage, claim diff and review note |
| Broad skill not invoked | Conditional workflow never loads | Permanent governance plus schema/CI/runtime controls | Composition trace and missing-control alert |
| Skill instruction injection or stale copied policy | Skill prose can conflict or drift | Current authority preflight, pinned package, narrow permissions | Package hash, authority comparison, conflict record |
| UI disables attack but area/physics/AI path remains | Presentation is not capability authorization | Central effect policy and adversarial system-path tests | Effect matrix and state/log evidence |
| Fixed event survives play but migration rewrites it | Runtime test misses persistence transforms | Save/migration invariant fixtures | Pre/post semantic diff across versions |
| Later knowledge leaks through shared localization text | Record IDs are separated but delivery content is reused | Typed audience boundary, dependency direction and rendered tests | String/source dependency trace and capture |
| Composite map lacks visible label | Back-end metadata does not guarantee player communication | UI/codex presentation contract plus specialist review | Screenshot/video and content-state link |
| Westernized/fantasy image has complete metadata | Metadata completeness cannot judge depiction | Visual/history/stewardship gate with region/era references | Actual asset in context and review rubric |
| Unknown license treated as permission | Absence is misinterpreted | Quarantine by default; rights gate | License evidence or explicit no-assertion record |
| Generator emits valid but invented records | Schema proves shape, not truth | Source-bound generation, semantic validators, human approval | Input/output hashes, claim traces and dispositions |
| Validator/test modified to pass failing content | Same change controls both rule and evidence | Protected validator ownership, independent review, known-invalid fixtures | Diff of rule/test/baseline and mutation/negative results |
| Golden image updated to hide regression | Baseline replacement normalizes failure | Approval, reason, old/new comparison and retained failure | Baseline history and reviewer identity |
| Handoff declares a proposal approved | Summary becomes counterfeit authority | Canonical decision IDs and recipient verification | Handoff-to-decision comparison |
| Stale-head publication overwrites new authority | Local success ignores repository movement | Pre-publish head check, non-force update, affected-audit rerun | Base/current head and reconciled diff |
| Scope guard blocks necessary invariant fix | Path allowlist is too rigid | Explicit escalation/expanded task, never silent expansion | Blocked report and approved scope amendment |
| Human reviewer rubber-stamps machine result | Named gate exists without substantive criteria | Criterion-specific rubric, evidence links, dissent and sampling | Review answers, observations and decision rationale |

### Prohibited architecture shortcuts

Reject these patterns:

- one mega-skill that contains policy, theology, history, schema, engine operation, Git, asset generation, and approval;
- a `confidence` number generated by an LLM with no sources, dimension, rationale, or reviewer;
- one chronology field that erases textual witnesses or disputed harmonizations;
- a shared prose blob for NPC knowledge and modern player codex commentary;
- scattered “invulnerable” flags without centralized effect authorization and save/event invariants;
- “source required” checks that accept any URL or transient citation token;
- unreviewed scripts bundled inside trusted-sounding skill prose;
- automatic reuse of third-party skills/assets/code because they are popular or publicly visible;
- an AI model as the final judge of theology, sacred treatment, authenticity, copyright, or player meaning;
- updating tests, validators, or goldens solely to make a failing artifact pass;
- treating handoff memory, dossier recommendations, or generated examples as approved contracts; and
- claiming validation for layers that were unavailable or not observed.

## 11. Recommended minimum enforcement stack

This is a staged minimum, not an authorization to implement or a final project skill catalog.

### Stage A — feasible before engine or schema selection

1. Preserve the Master Protocol as the permanent project authority; do not move universal policy into a conditional skill.
2. Require every task brief to name base SHA, authority files, inputs, output/write allowlist, prohibited changes, risk, acceptance, and human owner.
3. Use a claim/evidence worksheet for research outputs: claim status, source category, durable locator, confidence, competing views, quotation/paraphrase, rights state, and reviewer.
4. Use decision/exception IDs and a file manifest once the Creative Director approves their form; handoffs link to them.
5. Perform current-source, dirty-state, path, diff, duplicate-name, durable-link, and transient-token checks before publication.
6. Require Scripture/history/stewardship review for any sacred, canon, chronology, original-language, disputed-reconstruction, or sacred-figure output.
7. Quarantine unverified OCR and unknown-license material from authoritative quotation or distribution.
8. Record a composition/evidence trace for agent-assisted changes.

### Stage B — after schemas and content contracts are approved

1. Versioned schema registry with explicit approval state.
2. Claim/source, chronology/era/knowledge, protected-event, asset/provenance, decision, and content records with stable IDs.
3. Structural validator plus semantic reference, chronology, category, license, and invariant checks.
4. Known-valid, known-invalid, boundary, competing-view, knowledge-leakage, and generated-content fixtures.
5. Promotion workflow from research/proposal to approved production content with named human gates.
6. Migration plan and dependency-impact report for every schema revision.

### Stage C — after runtime/toolchain selection

1. Central protected-target/effect policy and fixed-event state invariants.
2. Separate in-world knowledge and player-codex delivery paths.
3. Save/load/migration preservation of protected anchors, knowledge scope, testimony, and stable IDs.
4. Static, unit, integration, controlled gameplay, visual, packaged-build, and human playtest gates proportional to the change.
5. Reproducible evidence manifest identifying commit, build, tools, versions, fixtures, actions, state, logs, captures, reviewers, and unsupported layers. Session 12 defines the fuller manifest contract ([Session 12 §10.1](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/12_Game_Validation_and_Play_Verification_Architecture.md#L322-L341)).

### Stage D — after CI and repository governance are approved

1. CI gates for schemas, references, source/rights metadata, negative fixtures, tests, protected paths, and exact scope.
2. Required status checks and branch/ruleset protection with named, reviewable bypass authority.
3. Protected ownership for governance, schemas, validators, tests, sacred-event data, migrations, and release evidence.
4. Tamper-evident artifact linkage and retention appropriate to release risk. SLSA 1.2 defines provenance as verifiable information about where, when, and how an artifact was produced; it can inform a later build-provenance choice without obliging this project to claim a SLSA level ([SLSA v1.2 provenance](https://slsa.dev/spec/v1.2/provenance), approved specification, checked 2026-07-22).

### Minimal enforcement-flow trace

```text
authority/decision
  -> scoped task contract
  -> approved source + schema inputs
  -> bounded authoring/generation
  -> structural + semantic validation
  -> runtime/scenario evidence when applicable
  -> specialist review
  -> Creative Director stewardship gate when required
  -> current-head + exact-diff + CI gate
  -> versioned artifact and evidence trace
```

## 12. Deferred user decisions

The following remain unverified and require Creative Director or delegated owner decisions before implementation:

1. Whether and how to create a native repository-wide instruction file while preserving the Master Protocol's authority and avoiding duplicated policy drift.
2. The formal project canon/scope registry, including treatment and release boundaries for Deuterocanonical/Apocryphal, Enochic/Second Temple, tradition, and optional exploration material.
3. Approved Scripture editions/textual witnesses, original-language verification workflow, translation rights, quotation limits, and attribution policy.
4. Controlled claim-status, source-category, confidence, and review-state vocabularies.
5. Whether the existing `High/Medium/Low/Disputed/Unknown/Symbolic` labels need dimensional definitions or additional states.
6. Who is qualified and accountable for Scripture/theology, original-language, history/geography/culture, visual/cultural, accessibility, rights, and stewardship reviews.
7. The approved chronology model and how alternate textual-witness/interpretive tracks appear in gameplay and the player codex.
8. The exact boundary and delivery model between in-world knowledge and player-facing codex knowledge.
9. The first approved vertical slice, sacred events (if any) within it, event-specific fixed outcomes, protected figures, allowed witness verbs, and review rubric.
10. Engine, language, runtime architecture, editor/toolchain, platform targets, accessibility baseline, and build/test/CI environment.
11. Approved schemas, storage formats, stable-ID policy, registry location, semantic validator technology, and promotion states.
12. Save compatibility guarantees, migration support window, recovery behavior, and acceptable player-visible data loss.
13. File manifest, protected paths, code ownership, task write-allowlist format, branch/ruleset settings, required checks, signing, review count, and bypass authority.
14. Provenance manifest format, third-party intake process, generated-media policy, dependency/license policy, SBOM choice, retention, privacy, and artifact storage.
15. The exception/waiver process: who may approve, maximum scope/duration, evidence, expiry, disclosure, and re-review.
16. Performance, visual, accessibility, sacred-event, historical-confidence, and play-quality acceptance thresholds.
17. Which narrow repeatable workflows merit skills after evidence exists; this report does not approve a skill catalog.
18. Whether public or external theological/historical advisors and representative players will review the project, under what confidentiality, consent, and decision terms.

## 13. Source appendix

### 13.1 Project authority and repository evidence

All repository links below are pinned to the inspected predecessor SHA `c6a9aaf439f2458c5b442c5a8b1f90636923fda8` unless an earlier report itself records another inspection SHA.

- [Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) — controlling project identity, authority, source separation, roles, sacred events, chronology/knowledge, codex, schema-first and file rules.
- [Assistant Activation Prompts](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md) — lower-authority operational roles, including gameplay-purpose tests and QA duties.
- [Continuity Handoff Prompt](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md) — current manual continuity-transfer contract.
- [Session 1 — Project Context and Authority Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md) — exact baseline inventory, authority resolution, proposal/implementation distinctions, unknowns, and research-packet contract.
- [Session 2 — Terminology and Artifact Taxonomy](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md) — separation of policy, skills, roles, tools, references, memory, and evaluations.
- [Session 3 — Current Codex Skill Capability Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md) — current documented skill discovery, conditional loading, repository-instruction distinction, permissions, and unresolved conflict behavior.
- [Session 4 — Effective Skill Anatomy and Authoring Principles](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md) — progressive disclosure, checkpoints, safe stopping, output contracts, and anti-patterns.
- [Session 6 — Skill Failure, Security, and Maintenance Risks](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md) — instruction, invocation, security, supply-chain, Git, staleness, authority, and validation-gaming risks.
- [Session 12 — Game Validation and Play-Verification Architecture](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/00_ADMIN/Research/LLM_Skills/12_Game_Validation_and_Play_Verification_Architecture.md) — layered validation, controlled play, sacred/historical oracles, human gates, evidence and tool-unavailable protocol.
- [Genesis 5–11 MT/LXX Chronology Comparison](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/genesis_5_11_mt_lxx_chronology_comparison.md) — concrete multiple-witness, disputed-variant, OCR-caution, confidence and proposed-data example; research/proposal, not an approved schema.
- [Eden geography dossier](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/Regions/eden_geography.md), [Noah/Ark dossier](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/Regions/noah_ark_geography.md), [Exodus/Yam Suph dossier](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/Regions/exodus_yam_suph_geography.md), [Galilee/Capernaum dossier](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/Regions/galilee_capernaum_geography.md), [Road to Jerusalem/Crucifixion dossier](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/Regions/road_to_jerusalem_crucifixion_geography.md), and [Paul/Early Church dossier](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/Regions/paul_early_church_geography.md) — repository research examples separating confidence, disputed geography, reconstruction, sacred-event handling and game translation; not approved production specifications.
- [Leningrad OCR corpus](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/Leningrad_Codex_OCR.txt) and [LXX OCR corpus](https://github.com/Degrading1919/The_Bible_Video_Game/blob/c6a9aaf439f2458c5b442c5a8b1f90636923fda8/Research/Septuagint_LXX.txt) — raw project inputs requiring targeted edition/provenance/copyright/accuracy verification, not authoritative quotation databases.

### 13.2 Current Codex/OpenAI primary sources

- OpenAI, [Build skills](https://learn.chatgpt.com/docs/build-skills), living documentation checked 2026-07-22 — current skill discovery, package and progressive-loading model.
- OpenAI, [Custom instructions with `AGENTS.md`](https://learn.chatgpt.com/docs/agent-configuration/agents-md), living documentation checked 2026-07-22 — persistent repository instruction discovery and path precedence.

These sources establish how current Codex artifacts load; they do not establish this project's theological, historical, creative, or approval policy.

### 13.3 Technical standards and platform controls

- JSON Schema, [Draft 2020-12 Core](https://json-schema.org/draft/2020-12/json-schema-core.html) and [Validation](https://json-schema.org/draft/2020-12/json-schema-validation.html), published 2022-06-16 — one candidate foundation for structural data validation; project adoption deferred.
- SPDX, [Specification 3.0.1](https://spdx.github.io/spdx-spec/), published 2024; [Licensing profile](https://spdx.github.io/spdx-spec/v3.0.1/model/Licensing/Licensing/) — primary model for declared/concluded/no-assertion license information; project format/adoption deferred.
- SLSA, [Specification 1.2](https://slsa.dev/spec/v1.2/) and [Provenance](https://slsa.dev/spec/v1.2/provenance), approved specification checked 2026-07-22 — primary build/source provenance model; no project level or conformance is claimed.
- GitHub, [About rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets) and [Available rules](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets), living documentation checked 2026-07-22 — possible branch, tag, update, force-push, file and status-check controls; exact repository availability/configuration is deferred.

### 13.4 Bounded conclusion

**Strongly supported:** the project needs defense in depth. Permanent authority, governed claim/data records, deterministic validation, capability-level runtime controls, adversarial tests, scoped Git/tool permissions, and accountable human review solve different parts of the problem. The witness premise, sacred-event protection, source/uncertainty separation, era knowledge, schema-first discipline, provenance, continuity, and gameplay meaning cannot safely depend on a single skill.

**Promising but unimplemented:** the proposed IDs, registries, schemas, validators, runtime policies, fixtures, evidence manifests, CI gates, and rulesets. They require approved stack and governance decisions.

**Rejected:** invented certainty, universal mega-skills, conditional policy as the only guardrail, schema-valid but source-free generation, runtime protection limited to UI, automated theological/aesthetic approval, and any claim of validation without the relevant observed layer.

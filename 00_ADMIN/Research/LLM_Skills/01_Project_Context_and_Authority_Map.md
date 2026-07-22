# Project Context and Repository Authority Map

**Session:** 1 of the LLM-skills deep-research sequence  
**Scope:** Repository analysis only; no external LLM, Codex, skill, or agent-ecosystem research  
**Snapshot date:** 2026-07-22  
**Repository:** [Degrading1919/The_Bible_Video_Game](https://github.com/Degrading1919/The_Bible_Video_Game)  
**Inspected commit:** [`9b470551b149221bcb8781a77bc32766aadef5e5`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/9b470551b149221bcb8781a77bc32766aadef5e5)

This is a descriptive authority and state map, not a design specification and not a final skill architecture. “Implemented” below means present in the repository unless explicitly identified as playable-game implementation. The repository has documentation and research, but no playable-game implementation at this snapshot.

## 1. Repository state and inspected commit

The checkout’s `main` reference resolved to the pinned SHA above. Before this report was created, the visible worktree contained 13 files: one `.gitattributes` file, three administrative reference documents, seven Markdown research documents, and two large OCR/text corpora. No prior file under `00_ADMIN/Research/LLM_Skills/` was treated as authority; deleted skill-research artifacts named in the Session 1 instruction were excluded as non-authoritative history.

| State fact | Finding | Classification |
|---|---|---|
| Branch and commit | `main` at `9b470551b149221bcb8781a77bc32766aadef5e5` | Inspected/current snapshot |
| Remote | `https://github.com/Degrading1919/The_Bible_Video_Game.git` | Implemented repository metadata |
| Repository content | Three governing/operational references, six regional dossiers, one chronology synthesis, two OCR corpora, and `.gitattributes` | Implemented documentation/research |
| Game project | No Unity, Godot, Unreal, custom-engine, or browser-game project file | Not present |
| Production source | No C#, GDScript, C/C++, Blueprint-export, JavaScript/TypeScript, shader, or other runtime source file | Not present |
| Structured game data | No JSON, CSV, schema, migration, database, or validation-contract file | Not present |
| Build/test/deploy | No build definition, package manifest, automated test, fixture, CI workflow, profiling setup, playtest plan, or deployment definition | Not present |
| Agent/skill automation | No `AGENTS.md`, `SKILL.md`, skill directory, agent configuration, MCP configuration, hook, script, or evaluation fixture | Not present |

The primary orchestration independently verified `main...origin/main` at the pinned SHA before drafting. After this file was created, `git status --short` showed only the new untracked `00_ADMIN/Research/` output path; no previously tracked file was modified. The only intended worktree artifact from this session is this report.

## 2. Chain of authority

The repository’s controlling hierarchy is explicitly defined in the [Master Assistant Protocol, §4](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L78-L107). Within the project, apply it as follows:

| Priority | Authority | Current repository realization | Consequence |
|---:|---|---|---|
| 1 | User / Creative Director | The user remains final decision-maker over identity, scope, implementation, and tradeoffs. | A current explicit user decision wins, while assistants must still disclose biblical, historical, and scope risk. |
| 2 | Core vision / metaprompt | No separate current metaprompt exists. The controlling vision is embedded in [Master Protocol §2](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L25-L40). | The player-as-witness premise cannot be displaced by a lower document or task. |
| 3 | Biblical source-text commitments | Expressed in the [creative guardrails](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L44-L74) and [Scripture/codex rules](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L486-L514). | Scripture conflicts, source uncertainty, paraphrase, and contested interpretation must be surfaced. |
| 4 | Established canon/scope decisions | The current rules distinguish canonical Scripture, Apocrypha/Deuterocanonical material, Enochic/Second Temple literature, tradition, speculation, and optional exploration content in [Master Protocol §8.3](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L471-L482). | These categories may not be silently blended. |
| 5 | Master Assistant Protocol | [`00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) | Highest current repository document governing all assistants. |
| 6 | File manifest / user-provided repo structure | No current manifest exists. A proposed historical tree appears only in the handoff prompt. | Do not manufacture the proposed tree or cite it as implemented. The observed tree controls factual repository-state claims. |
| 7 | Approved schemas and data contracts | None are present. | No content or implementation may presume field names, IDs, formats, or approved contracts. |
| 8 | Approved design and technical specs | None are identifiable as approved specs. The research dossiers contain recommendations and proposals. | Treat dossier designs as inputs for review, not production authority. |
| 9 | Assistant role descriptions | Master Protocol role definitions control; the [Activation Prompts](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md) operationalize them. | If wording drifts, the Master Protocol wins. |
| 10 | Individual task instructions | The active session prompt applies within all higher authorities. | A task cannot silently override witness, sacred-event, source, chronology, schema, or file-discipline rules. |

System/developer instructions of the execution environment remain binding on the assistant, but they are not project documents and do not alter the repository’s internal project-authority ordering.

## 3. Exact baseline project-file list for all later sessions

Every later session in this research sequence should read these files before specialist material:

1. [`00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) — controlling project identity, authority, roles, sacred-event rules, chronology/knowledge separation, Scripture/codex requirements, schema-first policy, file discipline, and response behavior.
2. [`00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md) — current manual role-activation wording; subordinate to the Master Protocol.
3. [`00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md) — current handoff format and historical decisions/assumptions; use with the staleness qualifications in §9.
4. `00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md` — this snapshot, status vocabulary, absence audit, conflict report, and packet contract.

The active session prompt is also binding, but it is not a repository project file. Later sessions must record the then-current commit and check whether any baseline file changed; this report must not be used to freeze the repository at the inspected SHA.

## 4. Exact specialist file groups

These groups are routing instructions, not claims that every file is equally authoritative.

### 4.1 Codex/agent research

Read the baseline four files. In particular:

- the Master Protocol for authority, role boundaries, file rules, and manual assistant workflow;
- the Activation Prompts for the current role vocabulary and invocation pattern;
- the Continuity Handoff Prompt for context-transfer expectations and historical state;
- this report for the verified absence of repository-local Codex/agent artifacts.

**Unavailable at this snapshot:** `AGENTS.md`; `.agents/`; `.codex/`; `SKILL.md`; skill directories; agent configuration; MCP configuration; model configuration; hooks; prompt-evaluation fixtures; and agent scripts. The three reference documents are generic assistant instructions, not evidence of native Codex skill behavior.

### 4.2 Game-engine and implementation research

Read:

- [Master Protocol §§6.7–6.8 and §§10–11](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L304-L353) for schema/content and systems-engineer boundaries, followed by the [schema-first and file-type rules](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L517-L589);
- the Schema & Content Engineer and Systems Engineer portions of the [Activation Prompts](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md);
- the repository-state and decision sections of the [Continuity Handoff Prompt](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md);
- [`Research/Regions/galilee_capernaum_geography.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/Regions/galilee_capernaum_geography.md#L957-L1221) only when researching the proposed Galilee vertical-slice gameplay target;
- [`Research/genesis_5_11_mt_lxx_chronology_comparison.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/genesis_5_11_mt_lxx_chronology_comparison.md#L139-L204) only when examining the proposed database shape and chronology-data needs.

**Unavailable:** selected engine/version, runtime language, engine project, source code, approved architecture, approved schema, database, asset-import pipeline, package/plugin inventory, build/export instructions, performance budget, test harness, playtest protocol, and deployment target.

### 4.3 Biblical/historical enforcement research

Always read the baseline, especially [Master Protocol §§3 and 7–10](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L44-L74). Then select only the relevant subject files:

- [`Research/genesis_5_11_mt_lxx_chronology_comparison.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/genesis_5_11_mt_lxx_chronology_comparison.md)
- [`Research/Regions/eden_geography.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/Regions/eden_geography.md)
- [`Research/Regions/noah_ark_geography.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/Regions/noah_ark_geography.md)
- [`Research/Regions/exodus_yam_suph_geography.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/Regions/exodus_yam_suph_geography.md)
- [`Research/Regions/galilee_capernaum_geography.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/Regions/galilee_capernaum_geography.md)
- [`Research/Regions/road_to_jerusalem_crucifixion_geography.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/Regions/road_to_jerusalem_crucifixion_geography.md)
- [`Research/Regions/paul_early_church_geography.md`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/Regions/paul_early_church_geography.md)
- [`Research/Leningrad_Codex_OCR.txt`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/Leningrad_Codex_OCR.txt) and [`Research/Septuagint_LXX.txt`](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/Septuagint_LXX.txt) only for targeted source comparison after provenance, edition, encoding, OCR quality, and licensing are independently established.

The regional files consistently distinguish biblical data, historical/geographical reconstruction, confidence, competing views, game translation, and “sources to verify.” That structure supports enforcement, but “sources to verify” means their claims are not self-validating authority.

### 4.4 Validation/evaluation research

Read:

- [Master Protocol QA / Validation & Continuity Auditor role](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L384-L402), sacred-event restrictions, chronology/knowledge rules, codex rules, schema-first rules, and file rules;
- the QA / Validation & Continuity Auditor section of the [Activation Prompts](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md);
- the relevant dossier’s confidence, sources-to-verify, accuracy, guardrail, and production-takeaway sections.

**Unavailable:** executable validators, unit/integration/scene tests, gameplay automation, deterministic fixtures, screenshot baselines, visual-regression tooling, save/load tests, performance captures, accessibility tests, acceptance thresholds, benchmark datasets, and CI evidence. Current validation is a manual role and policy expectation, not an implemented test system.

### 4.5 Skill-builder implementation

Read the baseline four files and all completed later reports in sequence. No present repository file defines a skill format, storage path, invocation mechanism, dependency model, installation process, script permission, evaluation harness, or skill-builder implementation. Session 1 supplies only project constraints and repository truth. It must not be cited as evidence for Codex capabilities or used to infer the final project skill catalog.

## 5. Current project identity and non-negotiable constraints

The current controlling identity is a biblically faithful, historically grounded, emotionally serious open-world/life RPG in which:

- **The player is a witness—not the savior, author, or rewriter of Scripture.** The player lives near biblical events and is changed by what is witnessed; the player does not replace central biblical figures.
- **Major biblical events are fixed, sacred, protected, and non-derailable.** The protected-event rules disable or constrain exploitative actions and preserve outcomes while allowing observation, response, aid to ordinary people, grief, repentance, belief, doubt, flight, and testimony. See [Master Protocol §7](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L406-L447).
- **Meaningful agency surrounds sacred history.** Family, household, work, survival, provision, travel, trade, reputation, relationships, moral pressure, obedience, fear, doubt, repentance, courage, faith, poverty, taxation, oppression, worship, and covenant memory are legitimate gameplay spaces.
- **No time travel, player magic/sorcery, supernatural power fantasy, or casual miracle/prophecy/judgment mechanics** may be introduced. Sacred figures cannot become ordinary damageable, exploitable, mockable, or customizable sandbox entities.
- **Scripture, interpretation, historical reconstruction, tradition, uncertainty, creative invention, and assistant paraphrase remain distinct.** Canonical and non-canonical categories remain explicit; uncertainty must not be laundered into lore.
- **Era-appropriate in-world knowledge remains separate from modern player-facing codex knowledge.** The chronology examples and distinction are explicit in [Master Protocol §8](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L451-L482).
- **Geography, ethnicity, appearance, and material culture must be historically grounded and confidence-labeled.** Debated locations and composite/stylized reconstructions must be disclosed; modern Westernized and fantasy assumptions are prohibited.
- **The Scripture database and codex are central, not decorative.** They are intended to ground quests, dialogue, region design, NPC worldview, chronology, manuscript/original-language notes, and player understanding.
- **Structured content is schema-first.** An approved schema, or an explicit task to create one, must precede structured content and system implementation; missing schemas cannot be invented as approved facts.
- **File discipline, role discipline, continuity, and scope control are mandatory.** Use the latest sources, request required missing files, label proposals, avoid casual filename versions, preserve handoffs, and prefer a feasible narrow step without abandoning the long-term lineage vision.
- **The intended macro structure is single-player.** The lineage/household-of-witnesses concept spans eras without time travel or an immortal protagonist. MMO/networking scope remains excluded unless the user explicitly reopens it.

## 6. Current role and workflow architecture

### Roles

The [Master Protocol role architecture](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L141-L402) defines the user as Creative Director and nine assistant modes:

1. Creative Director Support Mode
2. Scripture & Theology Researcher
3. Historical Geography & Culture Researcher
4. World & Quest Designer
5. Gameplay Systems Designer
6. Schema & Content Engineer
7. Systems Engineer
8. Character & Visual Design Researcher
9. QA / Validation & Continuity Auditor

An assistant should use one role unless the user explicitly requests combined mode. Each role has owned concerns and “must not” boundaries. The Activation Prompts manually instantiate the same nine modes and require an acknowledgement of the Master Protocol. These are role/persona and workflow instructions; the repository contains no evidence that they are native Codex skills, separate agents, or automatically routed configurations.

### Current manual workflow

1. Read the latest governing files and current user decision.
2. Select or receive the appropriate role; use combined mode only when requested.
3. Confirm the actual files needed for the task; do not invent absent inputs, schemas, or paths.
4. Separate source fact, interpretation, reconstruction, uncertainty, and proposal.
5. For structured content or implementation, obtain an approved schema or make schema creation the explicit task.
6. Produce work within role and file boundaries; brainstorm only at the level appropriate to that role.
7. Audit chronology, source/confidence labels, sacred-event boundaries, agency, schema consistency, scope, and continuity.
8. Preserve current decisions and next actions through the Continuity Handoff Prompt when transferring context.
9. Return tradeoffs and unresolved decisions to the user/Creative Director.

### What is not implemented

- There is no router, orchestrator, subagent protocol, skill composer, automated role selector, or machine-readable role registry.
- There is no formal decision log, ADR directory, issue workflow, or manifest. The handoff prompt asks an assistant to summarize decisions and rationale, but no completed handoff/decision record is present.
- There is no documented branch, commit, pull-request, code-review, release, or merge workflow beyond the repository’s existence in Git/GitHub.
- There is no automated continuity memory; continuity is a manually generated text artifact.

## 7. Current engine, code, data, asset, build, test, and tool stack

| Dimension | Implemented/current | Planned or proposed | Unknown / unavailable |
|---|---|---|---|
| Game engine | None | Unity is mentioned only conditionally through “`.cs` for C# systems **if Unity is chosen**” in [Master Protocol §11.2](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L559-L569). | Engine, version, renderer, physics, navigation, editor integration, and license |
| Runtime language | None | C# is a conditional example and role prohibition, not a selected language. | Language, framework, coding standard, naming convention, architecture standard, dependency policy |
| Runtime architecture | No runtime | Single-player life RPG; lineage/household witnesses; fixed sacred-event anchors; structured-data-driven codex, inventory, economy, items, quests, and world state are controlling intentions. | Scene/entity model, service boundaries, state management, save format, event system, content loading, serialization, modding |
| Game code | None | Systems Engineer responsibilities list intended systems. | All implementation status and interfaces |
| Data | Markdown research and two raw OCR/text corpora | JSON for schemas/structured content and CSV for suitable tabular data are recommended formats; the chronology synthesis includes a proposed database shape. | Approved schemas, records, stable IDs, validation rules, migrations, database engine, source/provenance contract |
| Assets | No image, audio, 3D, scene, prefab, material, animation, or UI asset exists in the tree. | The protocol lists possible image and 3D file types. Dossiers preserve image prompts/descriptions and filenames. | DCC tools, source assets, licenses, import settings, naming, budgets, LODs, compression, audio pipeline |
| Asset pipeline | None | Historical dossiers suggest visual directions only. | Blender or other DCC choice, image-generation workflow, review gates, import automation, provenance tracking |
| Build/package | None | None approved | Package/plugin manager, build targets, export profiles, CI, artifacts, signing, versioning |
| Test/validation | No executable tests | Manual QA role; policy checks for chronology, confidence, sacred events, bounded agency, schema consistency, and continuity | Unit/integration/scene/gameplay tests, fixtures, automation, visual regression, playtest protocol, profiling, pass/fail thresholds |
| Performance | None | None approved | Frame/memory/load targets, profiler, telemetry, device matrix |
| Development tools | Git/GitHub repository metadata and [LF text normalization](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/.gitattributes) | AI-assisted development is an intended workflow. | IDE, engine editor, Codex surface, MCP servers, local models, formatters, linters, validators, automation |
| Deployment/platform | None | None approved | Desktop/console/mobile/web targets, storefronts, operating systems, distribution and release process |

### Status classification

- **Implemented repository artifacts:** the three assistant reference documents; seven research/synthesis Markdown files; two raw OCR corpora; Git metadata; LF normalization.
- **Implemented playable software:** none.
- **Controlling planned direction:** player-as-witness; protected sacred events; single-player; lineage across eras; Scripture-backed codex; historically grounded ordinary life; schema-first structured content; specialized roles; continuity and scope discipline.
- **Proposed design:** Galilee/Capernaum as the likely first practical vertical slice; specific regional maps, hubs, quest chains, protected-event staging, skill loops, UI/visual directions, chronology database shape, and an old full repository folder tree.
- **Uncertain:** whether any proposed design has received final user approval beyond the general direction recorded in the handoff; no approval ledger exists.
- **Obsolete or non-authoritative:** the handoff’s old absolute local path as a statement of the current checkout; any unimplemented folder tree presented as current; missing generated-image session paths; deleted prior LLM-skills research; and conclusions from those deleted files.

## 8. Current repository structure and research-output convention

At the inspected SHA, the tracked structure is:

```text
.gitattributes
00_ADMIN/
  Reference/
    The_Bible_Video_Game_Assistant_Activation_Prompts.md
    The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md
    The_Bible_Video_Game_Master_Assistant_Protocol.md
Research/
  Leningrad_Codex_OCR.txt
  Septuagint_LXX.txt
  genesis_5_11_mt_lxx_chronology_comparison.md
  Regions/
    eden_geography.md
    exodus_yam_suph_geography.md
    galilee_capernaum_geography.md
    noah_ark_geography.md
    paul_early_church_geography.md
    road_to_jerusalem_crucifixion_geography.md
```

This session adds the new, sequence-specific path:

```text
00_ADMIN/Research/LLM_Skills/
  01_Project_Context_and_Authority_Map.md
```

### Research conventions actually evidenced

- Existing biblical/historical research lives under `Research/`, with geography under `Research/Regions/`.
- The regional files are large conversation archives/dossiers. They commonly preserve the user framework, assistant research, biblical data, historical/geographical data, confidence, competing views, game-design translation, map notes, sources to verify, image-generation descriptions, and production recommendations.
- Existing filenames are descriptive snake_case and do not use casual `_v1`, `_final`, `_latest`, or similar suffixes, consistent with [Master Protocol §11.1](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L544-L557).
- The LLM-skills sequence’s explicit user instruction establishes `00_ADMIN/Research/LLM_Skills/` for this research stream. It does not retroactively relocate the established biblical/historical corpus.
- There is no README, file manifest, research index, naming standard beyond the Master Protocol, metadata header standard, citation schema, approval marker, version field, or archival policy implemented in files.
- There is no repository-local convention yet for actual skill artifacts because no skill artifact exists.

### Files later sessions should summarize instead of routinely rereading

| File | Size at snapshot | Precise reusable summary and reread trigger |
|---|---:|---|
| `Research/Septuagint_LXX.txt` | 4,529,169 bytes; 10,341 lines | Large OCR-derived LXX corpus spanning Genesis–Malachi; visible encoding/OCR corruption. Do not reread globally or treat as a verified quotation source. Use only targeted passages after edition, provenance, copyright, encoding, and text accuracy are established. |
| `Research/Leningrad_Codex_OCR.txt` | 575,266 bytes; 20,467 lines | Raw Leningrad-related OCR corpus with severe visible OCR/encoding noise. It is source material, not a validated database. Use targeted extraction only after provenance and textual verification. |
| `Research/Regions/road_to_jerusalem_crucifixion_geography.md` | 52,840 bytes; 2,230 lines | Conversation dossier covering Galilee–Jerusalem routes, first-century Jerusalem, Passion Week locations, confidence/tradition distinctions, protected-event rings, player actions, map structure, sources to verify, and production takeaways. Reread only for Passion/Jerusalem work. |
| `Research/Regions/galilee_capernaum_geography.md` | 65,299 bytes; 1,312 lines | Conversation archive and the repository’s most developed proposed vertical-slice design: Capernaum/Galilee geography, economy/social life, Jesus-ministry handling, knowledge separation, protected zones, sandbox skills, six proposed regions, and an opening quest chain. Reread for Galilee or vertical-slice work; it is not an approved production spec. |
| `Research/Regions/exodus_yam_suph_geography.md` | 46,578 bytes; 1,346 lines | Debated Exodus/Yam Suph routes and place names, confidence levels, composite-map recommendation, protected crossing, tutorial/survival mechanics, sources to verify, and visual concept. Reread for Exodus work. |
| `Research/Regions/noah_ark_geography.md` | 37,908 bytes; 1,093 lines | Noah/Ark biblical and historical geography, Urartu/Ararat distinctions, disputed claims, map states, sacred-event witness mode, confidence table, sources, and guardrails. Reread for Noah/Flood work. |
| `Research/Regions/paul_early_church_geography.md` | 58,425 bytes; 1,026 lines | Acts/Paul route arcs, provinces, travel systems, city dossiers, church importance, prophecy handling, witness roles that do not replace Paul, proposed travel map, sources to verify, and production use. Reread for Acts/Paul work. |
| `Research/Regions/eden_geography.md` | 28,360 bytes; 858 lines | Eden’s biblical river data, competing geographic/cosmic views, explicit unknown/disputed location, visual confidence, game translation, sources, prologue/player verbs, UI tone, and sacred boundaries. Reread for Eden work. |
| `Research/genesis_5_11_mt_lxx_chronology_comparison.md` | 9,504 bytes; 212 lines | Compact MT/LXX Genesis 5–11 witness comparison with method limits, timelines, codex label, proposed database shape, game use, and next research step. Prefer this synthesis over full OCR corpora for high-level chronology context, but verify underlying text before production use. |

The three baseline reference files are small enough and important enough to reread every later research session. The Activation Prompts and Continuity Handoff Prompt are operationally volatile, so a current-file check is more important than relying only on this summary.

## 9. Conflict and staleness report

| Conflict or stale assumption | Evidence | Resolution / authority that wins |
|---|---|---|
| The handoff names an old local root `C:\Users\cwkei\OneDrive\Documents\The Bible Video Game\the_bible_video_game` and a broad proposed top-level folder tree. That is not this checkout and those folders do not exist here. | [Continuity Handoff Prompt, project-file/repo-state requirement](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md) versus the inspected tree. | Current user-provided checkout and observed repository state win. Treat the old path/tree as historical proposal, not manifest. |
| The handoff says the project is “currently being structured like” a prior Caelmor repository. No Caelmor structure, manifest, or implementation is present. | Same handoff file; no corresponding current files. | The no-invention rule in [Master Protocol §5](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L111-L137) wins. |
| Unity/C# can be misread as a selected stack because role text says Schema Engineer must not write C# and file rules mention `.cs`. | [Master Protocol role and conditional file-type wording](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L304-L353). | The explicit qualifier “if Unity is chosen” controls. Engine and language remain unknown. |
| The Activation Prompts duplicate role definitions and declare a required opening acknowledgement. They could drift from the unified roles. | [Activation Prompts](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md) versus the Master Protocol’s statement that it replaces role-specific drift. | Master Protocol wins all substantive differences; Activation Prompts are a lower-authority launcher. No material role contradiction was found at this SHA. |
| The hierarchy references a file manifest, approved schemas, design specs, and technical specs, but none exists. | [Master Protocol §4](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md#L78-L107) and current inventory. | This is an unfilled authority slot, not permission to invent. Current task/user decisions and the Master Protocol remain controlling. |
| Galilee/Capernaum is described as the likely practical first build and has a detailed proposed map/quest chain, but no roadmap, milestone, approved vertical-slice spec, or production plan exists. | [Galilee proposed vertical slice](https://github.com/Degrading1919/The_Bible_Video_Game/blob/9b470551b149221bcb8781a77bc32766aadef5e5/Research/Regions/galilee_capernaum_geography.md#L957-L1221) and handoff decisions. | Classify as planned/proposed, not implemented or formally approved. The user must confirm production authority. |
| Regional dossiers are labeled archives/handoffs and preserve assistant-generated recommendations, generated-image descriptions, and “sources to verify.” | Each regional research file. | Direct biblical/source commitments and the Master Protocol win. Verify sources and confidence before converting any dossier claim into structured production content. |
| Dossiers reference local generated-image filenames, but no image assets exist in the current repository. | Image-reference sections of the regional dossiers and current inventory. | References are unavailable historical session artifacts, not current assets or an asset pipeline. |
| The raw MT/LXX-related text files look like source corpora but contain conspicuous OCR and encoding corruption and no adjacent provenance/license metadata. | Current raw files. | Do not treat them as authoritative editions or production-ready data. Use verified source editions and explicit provenance in later specialist work. |
| Existing biblical research lives in `Research/`, while this sequence writes to `00_ADMIN/Research/LLM_Skills/`. | Current tree and direct Session 1 output instruction. | These are distinct conventions: retain current source locations; use the direct instruction for the new LLM-skills stream. |
| Deleted prior files in the incorrect root path `Research/LLM_Skills/` could appear relevant to the sequence. | The orchestration plan explicitly declares them non-authoritative history. | Do not restore, quote, or reuse their conclusions. Only newly completed sequential reports under `00_ADMIN/Research/LLM_Skills/` become current research inputs. |

No repository document contains a trustworthy internal version/date marker that establishes one same-commit document as chronologically newer than another. Conflicts therefore resolve by the explicit hierarchy and current user instruction, not filename or presumed age.

## 10. Unknowns later sessions must not silently invent

| Area | Unknown at this snapshot |
|---|---|
| Engine and code | Engine, engine version, runtime language, renderer, physics/navigation, scene/entity architecture, code organization, dependency policy, coding/naming standard, and editor integration |
| Target and scope | Target platforms, hardware floor, release channel, accessibility baseline, localization, age rating, exact vertical-slice approval, milestone dates, staffing, budget, and definition of done |
| Data and schemas | Approved schemas, stable identifiers, source/confidence enums, relationships, database technology, import/export format, migrations, validation rules, content approval state, and save-data compatibility |
| Scripture corpus | Approved Bible translations, original-language editions, canon configuration, copyright permissions, OCR provenance, corpus licensing, normalization, versification, manuscript policy, and textual-variant workflow |
| Historical content | Final geography choices, confidence approvals, composite-map policy per region, material-culture source standard, archaeology cutoff, and how dossier “sources to verify” will be verified |
| Sacred-event enforcement | Runtime representation, protected entities, interaction restrictions, state invariants, exploit tests, player failure behavior, and human theological approval gates |
| Gameplay | Final player character/household, core loop, progression, economy, inventory, quests, NPC simulation, combat boundaries, save/load, world scale, and era transitions |
| Assets | Art direction approval, DCC/image/audio tools, source files, licensing/provenance, sacred-figure review, import settings, naming, directory layout, budgets, and generated-asset policy |
| Build/test/release | Package management, build/export commands, CI, test frameworks, deterministic gameplay controls, screenshot/video capture, profiling, playtest gates, release process, deployment, and rollback |
| AI development | Codex surface/version, repository instruction model, skill locations/formats, invocation/composition behavior, MCP servers, local models, tool permissions, sandbox policy, hooks, scripts, automation, and evaluation harness |
| Project governance | File manifest, README, roadmap, approved design/technical specs, ADR/decision log, issue/prioritization workflow, branch/PR/review convention, owners, approval markers, archival policy, and change-control process |

When one of these facts is necessary, a later session should first inspect the then-current repository and user decisions. It may offer clearly labeled options or proposals, but it may not convert absence into an established fact.

## 11. Research packet contract for later sessions

### 11.1 What later sessions may cite from this packet

At the inspected SHA, later sessions may cite this file for:

- the repository’s explicit project-authority ordering;
- the baseline and specialist file-routing lists;
- the exact distinction between implemented repository artifacts, controlling planned direction, proposed dossier designs, unknown stack decisions, and obsolete/non-authoritative assumptions;
- the absence of engine, code, schema, build, test, toolchain, agent, and skill artifacts;
- the compact scope summaries and reread triggers for the large research files;
- the conflict/staleness resolutions and “must not invent” list.

This packet is not primary evidence for biblical, historical, Codex, engine, or third-party technical claims. Cite the nearest primary project file for controlling guardrails and read the relevant dossier/source for subject-matter details.

### 11.2 Minimum reread and freshness rule

For every later research session:

1. Record the current commit/repository state.
2. Read the active session prompt and all four baseline project files in §3.
3. Compare the current baseline files/tree with this snapshot.
4. Read only the specialist group needed for the session.
5. If the commit or files changed, report the delta and follow the newest higher-authority source.
6. Preserve the status labels **implemented**, **planned**, **proposed**, **unknown**, and **obsolete/non-authoritative**; never collapse them into “current.”
7. Do not globally load the raw OCR corpora or every regional dossier. Use §8’s summaries unless the session’s subject triggers a targeted reread.
8. Do not cite deleted prior LLM-skills files or infer their conclusions.

### 11.3 Stable packet summary

> The inspected repository is a documentation-and-research foundation, not yet a game implementation. The User/Creative Director and player-as-witness core vision outrank all repository artifacts; the Master Assistant Protocol is the highest current repository document. It protects fixed sacred events, bounded ordinary-life agency, Scripture/source distinctions, era knowledge, historical uncertainty, schema-first content, role discipline, continuity, and scope. Activation and handoff files are subordinate operational aids. Existing regional dossiers and chronology work are research/proposals requiring source verification and approval. No engine, language, runtime architecture, schemas, source code, assets, build, tests, IDE/agent tooling, Codex skills, or evaluation harness has been selected or implemented at SHA `9b470551b149221bcb8781a77bc32766aadef5e5`.

### 11.4 Session 1 completion audit

| Required repository category | Audited result |
|---|---|
| Three required `00_ADMIN/Reference` files | Read and mapped; Master controls, Activation operationalizes roles, Handoff transfers state and contains qualified stale assumptions. |
| README / entry document | Unavailable; no README or equivalent repository entry file exists. |
| Manifest / structure documentation | Unavailable; no current manifest. Historical proposed tree exists only in the handoff and is not implemented. |
| Project context / metaprompt / core vision / design overview | Core vision is embedded in the Master Protocol; handoff adds historical context. No separate current metaprompt or approved design overview exists. |
| Roadmap / milestone / vertical slice / production plan | No roadmap, milestone, or production-plan file. Galilee dossier contains a proposed vertical slice only. |
| AI prompts / roles / workflows / handoffs / decision logs | Master, Activation, and Handoff read. No decision log, ADR, router, or automated workflow exists. |
| Coding/architecture/naming/file standards | File naming/type and role constraints exist in Master. No selected language, coding standard, runtime architecture standard, or codebase exists. |
| Schemas / data contracts / validation | Schema-first policy and manual QA role exist. No approved schema, contract, machine validator, test, or fixture exists. |
| Engine / language / packages / assets / build / playtest / profiling / deploy | All explicitly audited as unavailable; Unity/C# is conditional, not selected. Dossier image references are not current assets. |
| Development tools / IDE / agents / MCP / local models / source control / automation | Git/GitHub and LF normalization are evidenced. No IDE, agent setup, MCP, local model, source-control workflow, or automation document exists. |
| `AGENTS.md` / skills / configuration / hooks / scripts / evaluation fixtures | All unavailable. |
| Current research locations and files | All current repository research files inventoried and routed; large-file summaries and reread triggers supplied. |
| Implemented/planned/proposed/unknown/obsolete separation | Defined and applied throughout §§7–10. |
| Project identity and guardrails | Verified and preserved in §5 and the packet summary. |
| External LLM/skill research boundary | Observed; no external LLM, Codex, skill repository, or ecosystem claim is made. |

All repository categories demanded by Session 1 and the original assignment are therefore either mapped to inspected files or explicitly recorded as unavailable/not yet present.

# Project Context and Authority Map

**Intended save path:** `00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md`

## Repository state and assignment coverage

The inspected repository state is the `main` branch at commit `a2936b0ba27094997b895149c8554764d40ad644`, which GitHub shows as the latest commit on July 22, 2026. The visible repository is very small at this state: the root contains only `00_ADMIN/Reference`, `Research`, and `.gitattributes`, and the latest commit adds a 12-file documentation-and-research tree rather than any engine project, runtime source tree, or asset/build system. citeturn9view0turn10view0turn8view1turn13view0

The three files the assignment required *first* were present and were read: `00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md`, `00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md`, and `00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md`. Those are the only files in `00_ADMIN/Reference` at the inspected commit. citeturn3view0turn4view0turn4view1turn4view2

The assignment also required checking for a README or equivalent entry document, a file manifest or structure document, roadmap or production-plan files, engine/build/test/tooling docs, and any `AGENTS.md` or skill/agent directories. At the inspected commit, there is **no** `README.md` at the repository root, and direct raw fetch for `README.md` returns 404. There is also **no** root `AGENTS.md`; a direct raw fetch returns 404. No separate file manifest, roadmap, milestone plan, vertical-slice plan, technical architecture doc, testing plan, deployment doc, MCP/tooling doc, or automation/hook/evaluation-fixture directory is present in the visible tree. The current repo instead consists of the three admin reference files, a research corpus under `Research`, and `.gitattributes`. citeturn12view0turn12view1turn8view1turn13view0turn15view0

The assignment’s “completion check” is therefore satisfied as follows: project-control prompts and role/workflow files are present and were read; research-location conventions are present and were read from `Research` and `Research/Regions`; chronology and textual-witness research files are present and were read; all demanded engine/code/build/test/tooling/AGENTS categories were explicitly checked and are currently unavailable or not yet present as repository files at this commit. citeturn4view0turn19view0turn19view1turn8view0turn15view0turn14view0turn15view1turn15view2turn12view1

## Chain of authority

The repository’s explicit authority order is stated in the Master Assistant Protocol: the user as Creative Director comes first; then the “project core vision / metaprompt”; then biblical source-text commitments; then established canon and scope decisions; then the Master Assistant Protocol itself; then the file manifest or repo structure provided by the user; then approved schemas and data contracts; then approved design and technical specs; then assistant role descriptions; then individual task instructions. The same protocol also says assistants must rely on the most recent version of the manifest, project context, protocol, schemas, research docs, technical specs, and current workflow decisions, and must not invent missing files or structures. citeturn7view2

At the inspected commit, several layers in that hierarchy are **absent as standalone files**. There is no separate project “core vision” file, no formal file-manifest document, no approved schema files, no approved technical spec, and no dedicated roadmap. In practice, the active hierarchy therefore collapses into a narrower operational order for this repository state: **the user’s current instruction**, then the project’s controlling vision as expressed in the Master Assistant Protocol, then the Master Assistant Protocol’s biblical and sacred-event guardrails, then the actual checked repository tree at commit `a2936b0…`, then the Assistant Activation Prompts, then the Continuity Handoff Prompt, then the archived research documents under `Research`. citeturn7view2turn19view0turn19view1turn8view1turn13view0

For later research sessions, the most important practical rule is this: if a document makes a claim about repository structure or implementation status that conflicts with the **actual checked commit**, the checked commit wins unless the user explicitly overrides it. That conclusion follows both from the Master Protocol’s “use the latest provided source” rule and from the fact that the current repo tree is a stronger source of present repository state than a reusable handoff template. citeturn7view2turn8view1turn13view0turn19view1

## Baseline files for all later sessions

Every later research session should read this exact baseline set before doing any new substantive work:

- `00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md` — this is the main controlling rules document for authority, sacred-event handling, role boundaries, schema-first development, file-output rules, and response behavior. citeturn6view0turn7view2
- `00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md` — this operationalizes the role set and gives the concrete startup framing each specialist is supposed to follow. citeturn19view0
- `00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md` — this is the current transfer-format document and matters because it encodes how continuity should be preserved across sessions, even though parts of its embedded repo-state content are stale against the current checked repository. citeturn19view1
- `00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md` — this file, once saved, should become the compact authority-and-context packet for future sequential research sessions. This path is user-established by the present task; it is not yet part of the inspected commit tree. citeturn8view1turn13view0

There is **no repository README or equivalent entry document** to add to the baseline list, because none exists at the inspected commit. There is also **no current file-manifest document** to include; the actual GitHub tree and this authority-map file must serve that function for later sessions unless the user adds a manifest later. citeturn12view0turn8view1turn13view0

Files that are useful but **not baseline for every session** should be read only when the subject matter requires them. The most important non-baseline file in that category is `Research/genesis_5_11_mt_lxx_chronology_comparison.md`, because it already distills the MT/LXX chronology issue and explicitly warns that the Leningrad OCR is corrupted for early Genesis and that values should remain parallel tracks until manually verified. That makes it a better first-stop source than the raw OCR files for most chronology work. citeturn14view0

## Specialist file groups

### Codex and agent research

For codex, prompt, continuity, and assistant-workflow research, the core file group is:

- `00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md` citeturn6view0turn7view2
- `00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md` citeturn19view0
- `00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md` citeturn19view1
- `00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md` citeturn8view1turn13view0
- `Research/genesis_5_11_mt_lxx_chronology_comparison.md` when codex work touches textual witnesses or chronology handling. citeturn14view0

There is currently **no** `AGENTS.md`, no `skills/` directory, no hooks, no automation scripts, and no formal evaluation fixtures in the checked tree, so “agent research” currently means working from the admin reference documents rather than from repo-native agent infrastructure. citeturn12view1turn8view1turn13view0

### Game-engine and implementation research

For engine, code, implementation, architecture, build, and runtime questions, the current specialist group is unavoidably thin because the repository contains **no engine project files and no runtime code**. The operative files are therefore only:

- `00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md` — especially the Systems Engineer role, schema-first rules, file-output rules, and the statement that `.cs` is appropriate *if Unity is chosen*. citeturn7view2
- `00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md` — especially the Systems Engineer prompt and the single-player assumption. citeturn19view0
- `00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md`. citeturn8view1turn13view0

Important negative finding: there are no current files for Unity, Unreal, Godot, package management, plugins, asset import pipelines, build scripts, CI, playtesting, profiling, or deployment. Any later implementation session must treat those as unresolved unknowns, not as implied repository facts. citeturn8view1turn13view0turn12view0

### Biblical and historical enforcement research

For Scripture, theology, chronology, geography, material culture, sacred-event enforcement, and historical-confidence work, the current specialist group is:

- `00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md` — especially the sacred-event rules, chronology and knowledge rules, codex rules, and role definitions. citeturn7view2
- `00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md`. citeturn19view0
- `Research/genesis_5_11_mt_lxx_chronology_comparison.md`. citeturn14view0
- `Research/Regions/eden_geography.md`. citeturn16view0
- `Research/Regions/exodus_yam_suph_geography.md`. citeturn20view0
- `Research/Regions/galilee_capernaum_geography.md`. citeturn20view1
- `Research/Regions/noah_ark_geography.md`. citeturn20view2
- `Research/Regions/paul_early_church_geography.md`. citeturn17view0
- `Research/Regions/road_to_jerusalem_crucifixion_geography.md`. citeturn20view3
- `Research/Leningrad_Codex_OCR.txt` and `Research/Septuagint_LXX.txt` only when direct witness text is actually needed. citeturn15view1turn15view2

### Validation and evaluation research

For validation, audit, contradiction checking, chronology enforcement, and continuity review, the best current group is:

- `00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md` — especially the QA / Validation & Continuity Auditor role and the file/context rules. citeturn7view2
- `00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md` — especially the QA / Validation & Continuity Auditor prompt. citeturn19view0
- `Research/genesis_5_11_mt_lxx_chronology_comparison.md` for a model of explicit caution and witness separation. citeturn14view0
- `00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md`. citeturn8view1turn13view0

There are no automated tests, no evaluation fixtures, and no validation scripts in the current repository. Validation is therefore documentary and conceptual at this stage, not executable. citeturn8view1turn13view0

### Skill-builder implementation

For the specific “LLM skills” research stream, the current relevant file group is:

- `00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md` citeturn6view0turn7view2
- `00_ADMIN/Reference/The_Bible_Video_Game_Assistant_Activation_Prompts.md` citeturn19view0
- `00_ADMIN/Reference/The_Bible_Video_Game_CONTINUITY_HANDOFF_PROMPT.md` citeturn19view1
- `00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md` citeturn8view1turn13view0

The key current convention is negative rather than positive: there is **not yet** a repository-native skill system, agent config scheme, or `AGENTS.md` file. Later skill-related sessions should not silently invent such an architecture and should treat this research file as the starting control document for that stream until the user creates real repo artifacts for it. citeturn12view1turn8view1turn13view0

## Current project identity and workflow architecture

The project’s non-negotiable identity is stated clearly and repeatedly: the player is **not** the savior, not the author of Scripture, not meant to rewrite biblical history, and is instead a witness living near biblical events. Major biblical events remain fixed, sacred, and protected, while player agency is meant to exist in family life, work, survival, travel, trade, reputation, relationships, moral choice, obedience, fear, doubt, repentance, courage, and faith. The protocol also explicitly forbids turning miracles, prophecy, Revelation, God, angels, Jesus, or sacred events into ordinary sandbox mechanics. citeturn6view0turn7view2turn19view0

The same controlling documents also preserve the distinctions the assignment asked to verify. They explicitly require separating Scripture from interpretation, tradition, historical reconstruction, and speculation; separating in-world character knowledge from player-facing codex knowledge; distinguishing canonical Scripture from apocryphal, Enochic, historical-tradition, and speculative material; grounding geography and material culture in labeled confidence levels; and keeping structured content schema-first. Those same documents also require file discipline, specialized roles, continuity handoffs, and scope control. citeturn7view2turn19view0

The current role and workflow architecture is already fairly explicit. The user is the Creative Director. Every other assistant is supposed to operate in a specialized mode such as Creative Director Support, Scripture & Theology Researcher, Historical Geography & Culture Researcher, World & Quest Designer, Gameplay Systems Designer, Schema & Content Engineer, Systems Engineer, Character & Visual Design Researcher, or QA / Validation & Continuity Auditor. The activation file requires each assistant to start by acknowledging the Master Assistant Protocol, and the continuity prompt defines the handoff format when one assistant instance transfers work to another. citeturn19view0turn19view1turn7view2

What does **not** exist yet is a dedicated decision-log file or formal decision-register practice in the repository. At the inspected commit, decision retention is happening implicitly through the Master Protocol, the activation and handoff files, and the archived conversation dossiers under `Research/Regions`, which preserve user prompts, research frameworks, assistant responses, and use cases rather than a centralized accepted/rejected decision ledger. citeturn19view1turn16view0turn20view0turn20view1turn17view0turn20view3

## Current stack, development status, and repository conventions

The present repository is **not** an implementation repository yet. It is a control-and-research repository. What is implemented today is a documentation stack: role and authority protocols in `00_ADMIN/Reference`; research archives under `Research/Regions`; two large textual-witness OCR files; a chronology comparison file; and line-ending normalization in `.gitattributes`. There is no source code, no schema directory, no assets directory, no build system, no tests, and no engine project. citeturn8view1turn13view0turn15view0turn14view0turn15view1turn15view2turn18view0

The currently approved *technical direction* is therefore only partial and documentary. The Master Protocol approves schema-first development, says structured content should use `.json` or `.csv`, recommends `.md` for docs, and mentions `.cs` *if Unity is chosen*; the Systems Engineer role also assumes runtime systems must match approved schemas and that the game is single-player unless the user explicitly changes scope. That means the current technical stance is **data-driven and single-player by policy**, but **engine choice, language choice, runtime architecture, package/plugin system, asset pipeline, build process, and deployment model remain unresolved**. citeturn7view2turn19view0

In status terms, the repository breaks down cleanly into four buckets. **Implemented:** authority docs, role prompts, handoff format, geography dossiers, OCR source files, and one chronology-analysis file. **Planned or approved in principle:** protected sacred-event design, schema-first structured content, a Scripture-backed codex, database-driven item/economy/inventory logic, and single-player scope. **Proposed but not yet formalized as current repo truth:** a larger future folder structure, a vertical-slice focus around Galilee/Capernaum, and resemblance to a prior Caelmor-style organization. **Uncertain or unresolved:** engine, language, runtime code architecture, tests, tooling, IDE setup, MCP servers, local models, hooks, automation, asset formats in active use, branch policy, and deployment. citeturn7view2turn19view0turn19view1turn20view1turn17view0

The current repository structure and research-output convention are visible rather than formally documented. `Research/Regions` contains large “conversation archive,” “research dossier,” or “research archive/handoff” files named by biblical topic or region, while `Research/genesis_5_11_mt_lxx_chronology_comparison.md` is a more distilled analytic document with explicit method notes and a creation date. Across those files, the common convention is to preserve the user’s research framework, distinguish biblical text from historical-geographical reconstruction, label uncertainty, and translate findings into game-design implications without collapsing uncertain material into false fact. citeturn15view0turn16view0turn20view0turn20view1turn20view2turn17view0turn20view3turn14view0

## Conflict and staleness report

The most important current conflict is between the **Continuity Handoff Prompt** and the **actual checked repository tree**. The handoff prompt contains concrete bullets telling a future assistant to include a Windows local path and a large proposed top-level folder layout such as `01_PRE-PRODUCTION`, `02_VERTICAL_SLICE`, `03_CORE_SYSTEMS`, `04_SCRIPTURE_DATABASE`, and more. But the actual checked GitHub commit has none of those folders; it has only `00_ADMIN/Reference`, `Research`, and `.gitattributes`. For present repository-state questions, the checked commit wins. The lower-authority handoff prompt should be treated here as a reusable template containing stale repo-state assumptions, not as a reliable manifest of the current GitHub repository. citeturn19view1turn8view1turn13view0turn7view2

A second important staleness issue is technical. The Master Protocol mentions `.cs` for systems “if Unity is chosen,” and the Systems Engineer role assumes runtime implementation will eventually exist, but the repository contains no Unity project and no code. That means any statement that the project is *currently* Unity/C# would be an overreach. The correct reading is that Unity/C# is only a conditional example, not a chosen stack in the inspected repo state. citeturn7view2

A third staleness issue concerns design certainty. Several research dossiers preserve rich prior conversations and are valuable, but they are explicitly archives or handoffs of research conversations, not ratified global design specs. They should be treated as specialist source material and prior reasoning records, not as automatically approved canonical design documents for every later session. citeturn16view0turn20view0turn20view1turn20view2turn17view0turn20view3

Files that are too large or too volatile to reread in every session should be handled by summary contract instead. `Research/Leningrad_Codex_OCR.txt` is 20,467 lines and 562 KB; later sessions should rely on the summary that it is a raw OCR witness and is specifically reported as corrupted in early Genesis for chronology purposes. `Research/Septuagint_LXX.txt` is 4.32 MB; later sessions should rely on the summary that it is a large raw textual witness and should be opened only for targeted extraction. `Research/Regions/road_to_jerusalem_crucifixion_geography.md`, `exodus_yam_suph_geography.md`, `galilee_capernaum_geography.md`, `noah_ark_geography.md`, `paul_early_church_geography.md`, and `eden_geography.md` are all large dossier-style archives; later sessions should rely on short summaries of each dossier’s scope unless the task directly concerns that region or event. citeturn15view1turn15view2turn14view0turn16view0turn20view0turn20view1turn20view2turn17view0turn20view3

The precise summary substitutes later sessions should use are these: `Leningrad_Codex_OCR.txt` = raw OCR witness, not baseline, unreliable for early Genesis chronology without manual verification; `Septuagint_LXX.txt` = large raw LXX witness, use only for targeted textual checks; `genesis_5_11_mt_lxx_chronology_comparison.md` = preferred summary source for Genesis witness divergence and chronology handling; `eden_geography.md` = sacred-prologue handling and uncertainty-centered Eden-location theories; `exodus_yam_suph_geography.md` = debated Exodus-route and crossing-region archive with explicit uncertainty rules; `galilee_capernaum_geography.md` = likely strongest core-loop region archive around Jesus’ public ministry; `noah_ark_geography.md` = Ararat and pre-Flood region dossier with confidence-labeled uncertainty; `paul_early_church_geography.md` = Roman-network and Pauline-route gameplay geography archive; `road_to_jerusalem_crucifixion_geography.md` = Passion Week, Jerusalem geography, pilgrimage routes, and protected sacred-event handling dossier. citeturn14view0turn16view0turn20view0turn20view1turn20view2turn17view0turn20view3

## Unknowns and research packet contract

Later sessions must **not silently invent** any of the following, because the inspected repository does not currently settle them: the game engine; the implementation language; runtime architecture; package/plugin system; schema filenames and concrete data contracts; asset pipeline; build process; testing methodology; playtest process; profiling process; deployment approach; IDE or local toolchain; MCP server use; local model use; automation scripts; hook systems; evaluation fixtures; branch workflow beyond the existence of `main`; or a formal repo manifest. They must also not assume that the large folder structure described inside the handoff prompt exists in GitHub, because it does not at the inspected commit. citeturn8view1turn13view0turn19view1turn7view2

The current research-packet contract for later sessions should therefore be: you may cite this file instead of rereading the full repo for the inspected commit SHA; the exact current top-level tree; the exact baseline file list; the absence of README, AGENTS, engine docs, code, schemas, tests, build docs, deployment docs, tooling/MCP docs, and automation; the current authority hierarchy; the current role architecture; the distinction between controlling files and archived research dossiers; the classification of files into baseline versus specialist groups; and the conflict/staleness findings summarized above. citeturn10view0turn8view1turn12view0turn12view1turn13view0turn19view0turn19view1turn7view2

Later sessions must still reopen original repository files when any of four conditions apply: the repository commit has changed; the task depends on exact wording or quotation from a source file; the task targets one of the large specialist research dossiers or raw OCR witnesses; or the user introduces a new authoritative file or explicitly supersedes this summary. If none of those conditions apply, this document is the correct compact authority packet to use in place of rereading the whole inspected repository state. citeturn7view2turn15view1turn15view2turn16view0turn20view0turn20view1turn20view2turn17view0turn20view3

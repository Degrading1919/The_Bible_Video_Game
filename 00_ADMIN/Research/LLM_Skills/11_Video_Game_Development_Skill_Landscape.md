# Video-Game Development Skill Landscape

**Session:** 11 of 18
**Research cutoff:** 2026-07-22
**Project predecessor SHA:** [`ba2369e402f20249b98c55237dd5cd1209571e47`](https://github.com/Degrading1919/The_Bible_Video_Game/commit/ba2369e402f20249b98c55237dd5cd1209571e47)
**Audit scope:** Seven public package families, eight separately classified artifacts, inspected at pinned revisions
**Status:** Research finding and recommendation report; not a project skill catalog, engine choice, or authorization to install or reuse a package

This report distinguishes **finding**, **inference**, **recommendation**, and **unverified claim**. “Tested workflow” means that executable tests, test fixtures, or a repeatable verification loop were present in the inspected package; it does **not** mean this project ran the package or that independent users proved its effectiveness. Repository popularity is deliberately excluded from quality judgments.

## 1. Landscape summary

### 1.1 Scope and method

The audit is representative rather than exhaustive. It was closed after seven public package families supplied contrasting examples of a real Codex skill, Claude-oriented skills, dual-format Agent Skills, command wrappers, MCP integrations, a documented-but-missing package, and an explicitly unfinished experiment:

1. OpenAI’s archived `develop-web-game` Codex skill;
2. Fern Forest Games’ Godot Agent Skill;
3. Randroids Dojo’s Godot and Unreal skill packages;
4. `akiojin/skills` and its current-but-unfulfilled `unity-development` listing;
5. CoderGamester’s Unity MCP bridge;
6. Coding-Solo’s Godot MCP bridge; and
7. Siddharth Ahuja’s Blender MCP bridge.

For every family, the audit inspected the actual entry file or closest available package metadata, relevant supporting scripts or executable bridge code, revision and date, license evidence, engine/tool assumptions, filesystem/network/write reach, validation evidence, maintenance signals, and transferability. The inspected set is intentionally small enough to permit file-level review. It is not a popularity ranking and does not imply that uninspected packages are inferior.

### 1.2 Strong findings

- **A skill and a tool bridge solve different problems.** The inspected `SKILL.md` files constrain workflow and sequence. MCP servers expose editor or runtime operations. An MCP server does not supply project authority, source discipline, acceptance criteria, or safe routing merely because an agent can call it.
- **The strongest reusable pattern is an observable edit–execute–inspect loop.** OpenAI’s web-game skill requires small changes, controlled input bursts, deterministic stepping hooks, screenshots, text state, and console-error review. The Fern Forest and Randroid Godot packages require import, syntax or unit checks, and engine execution. These are useful patterns even when their engine-specific commands are not transferable.
- **Engine knowledge is highly version- and project-dependent.** Several packages hard-code Godot 4.x, Godot 4.5, Unity 6, Unity 2022.3 metadata, GdUnit4, a custom Godot fork, Unreal Remote Control, or particular editor APIs. This project has selected none of those. Session 1 remains controlling: there is no verified engine, runtime language, asset pipeline, build system, test harness, deployment target, or DCC stack ([project state](https://github.com/Degrading1919/The_Bible_Video_Game/blob/ba2369e402f20249b98c55237dd5cd1209571e47/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md)).
- **Internal code and tests are evidence of implementation, not evidence of outcome improvement.** The audit found executable scripts, unit-test hooks, example test code, and active maintenance. It did not find a controlled comparison showing that any inspected game package improves correctness, speed, playability, accessibility, or production outcomes across repeated independent projects.
- **Licensing must be resolved at file/package level.** Six families contain an express MIT or Apache-2.0 license file or package declaration. CoderGamester’s package metadata declares MIT, but no root `LICENSE` file was found at the audited revision; copying implementation text should remain blocked until the governing license artifact and notices are confirmed. A public repository is not itself a license grant.
- **Tool reach is the principal immediate safety issue.** The bridges can create, alter, save, load, or delete scenes and objects; install packages; launch engines; execute supplied programs or code; fetch assets; write configuration; emit telemetry; and write artifacts. These capabilities require project-scoped configuration, least privilege, exact path controls, explicit user approval for destructive/external actions, and post-action diff/scene inspection.
- **The available landscape is uneven.** The sample contains credible implementation/validation loops for browser games and Godot, broad editor bridges for Unity/Godot/Blender, and only a WIP Unreal skill. It contains no mature, audited skill dedicated to biblical narrative continuity, dialogue provenance, quest/codex knowledge separation, NPC schedules, save migration, accessibility, localization, audio production, console certification, or sacred-event protection.

### 1.3 Evidence-strength scale used here

| Rating | Meaning in this report |
|---|---|
| Strong | Actual pinned implementation plus directly relevant tests/fixtures or official first-party behavior documentation |
| Moderate | Actual pinned implementation and coherent workflow, but no independent outcome evidence |
| Limited | Documentation or metadata exists, but key implementation, tests, license, maintenance, or outcome evidence is missing |
| Negative | The inspected revision contradicts the claim, marks itself WIP/deprecated, lacks the named artifact, or creates an unresolved blocker |

No package receives “strong evidence of real use” merely because it is public, has commits, or is advertised for many clients.

## 2. Engine-by-engine findings

### 2.1 Unity

#### CoderGamester `mcp-unity`

**Classification finding:** MCP integration and command wrapper, not a Codex skill. It exposes editor tools and resources to MCP clients including Codex, Claude Code, Cursor, and others. Its [README at `c35f184...`](https://github.com/CoderGamester/mcp-unity/blob/c35f184d7656bd14e7748f11a05060feeb286d6e/README.md) describes scene, GameObject, component, material, prefab, package, test, console, play-mode, and batch operations. The [Unity package manifest](https://github.com/CoderGamester/mcp-unity/blob/c35f184d7656bd14e7748f11a05060feeb286d6e/package.json) declares version `1.3.0`, Unity `2022.3`, Unity Test Framework `1.3.3`, and MIT; the server’s [Node manifest](https://github.com/CoderGamester/mcp-unity/blob/c35f184d7656bd14e7748f11a05060feeb286d6e/Server~/package.json) declares MCP, WebSocket, HTTP, validation, registry, and Windows-registry dependencies.

**Contradictory evidence:** The README’s requirements say “Unity 6 or later,” while the package manifest declares minimum Unity `2022.3`. These statements may describe different current support intentions, but the inspected files do not reconcile them. Treat the supported range as **unverified**, not as “2022.3 through Unity 6.”

**Evidence of use:** The repository contains editor tests, server tests, diagnostic work, and a current 2026-07-04 maintenance commit. That is moderate evidence of an implemented, maintained bridge. No independent repeated-project effectiveness study was found in the bounded audit.

**Safety:** Its surface includes `delete_scene`, `delete_gameobject`, package installation, global or project MCP-config writes, menu execution, prefab/material/scene mutation, and batch operations. Even “rollback on failure” cannot be treated as a complete undo contract without scene, asset-database, package-lock, filesystem, and serialized-reference verification. Node dependency ranges are not a transitive-dependency pin. The package metadata says MIT, but the expected root license file was not present at this revision; code reuse remains license-blocked pending confirmation.

**Transferability:** If Unity is later selected, the useful principle is a typed, observable editor adapter that separates read-only resources from mutating tools and exposes tests/logs/play state. The current package should be monitored, not installed or copied now.

#### `akiojin/skills` `unity-development`

**Classification finding:** At the pinned current revision, this is a **reference/marketing listing for a missing Claude Code plugin**, not an inspectable skill. The [README at `4f72afe...`](https://github.com/akiojin/skills/blob/4f72afeb9efb9520a7a02afb9e23fba2dbe0ffa1/README.md) says `unity-development` supports Unity C#, `unity-mcp-server`, VContainer, UniTask, tests, and fail-fast practices. However, the pinned [marketplace manifest](https://github.com/akiojin/skills/blob/4f72afeb9efb9520a7a02afb9e23fba2dbe0ffa1/.claude-plugin/marketplace.json) contains no `unity-development` entry, and the named package/`SKILL.md` was not present at the obvious paths checked.

**Evidence consequence:** The Unity instructions, scripts, permissions, dependencies, and file-level provenance cannot be audited. The repository-level [MIT license](https://github.com/akiojin/skills/blob/4f72afeb9efb9520a7a02afb9e23fba2dbe0ffa1/LICENSE) does not cure the absence of the advertised artifact. The current claim is stale or incomplete and must be rejected as a reuse candidate.

### 2.2 Godot

#### Fern Forest Games `agent-skill-godot`

**Classification finding:** A real Agent Skill authored for Claude-style installation and MCP names; its simple `name`/`description` frontmatter is structurally portable, but the body is not platform-neutral. The [skill at `e584a97...`](https://github.com/fernforestgames/agent-skill-godot/blob/e584a973fcf0590a4cbc6697fa5daa3d11585dbe/SKILL.md) hard-codes `.claude/skills`, directs use of a subagent, and requires Fern Forest `godot-docs` and `godot-editor` MCP servers. It mandates itself for all GDScript and Godot resources, requires Godot 4+, and tells the model to use “latest Godot 4.5” syntax.

**Workflow quality:** The six-step loop—read, consult docs, edit, import, syntax-check, test—is concise and observable. It contains GUT examples, editor-run control, screenshots, node interaction, input synthesis, and a reminder to stop launched scenes. Its [shell validator](https://github.com/fernforestgames/agent-skill-godot/blob/e584a973fcf0590a4cbc6697fa5daa3d11585dbe/scripts/check_syntax.sh) enumerates `.gd` files, excludes `.godot` and add-ons, runs Godot `--check-only`, reports failures, and returns the error count.

**Limitations and safety:** “Mandatory for ALL” is over-broad routing. The claimed latest syntax will become stale. The script is Bash-dependent, walks the caller-supplied project path, runs every discovered project script through Godot, and detects only selected error strings. Godot tool execution can import or alter editor cache/resources even when the intent is “checking.” The package requires two external MCP servers that were not part of this seven-family file audit. No clean-context evaluation, CI results, or independent repeated-use outcome was present. The package has an explicit [MIT license](https://github.com/fernforestgames/agent-skill-godot/blob/e584a973fcf0590a4cbc6697fa5daa3d11585dbe/LICENSE).

**Transferability:** Extract the preflight, engine-documentation lookup, import/check/test sequence, screenshot-plus-state observation, and “always stop the launched runtime” invariant. Do not import its trigger, version, tool names, or style rules while the project stack remains unknown.

#### Randroids Dojo Godot package

**Classification finding:** A Claude Code skill and command-wrapper package whose repository claims dual Agent-Skill compatibility; it is also a tested workflow in the limited sense that it contains executable validation/test/export scripts and concrete GdUnit4/PlayGodot examples. The [Godot `SKILL.md` at `aba2aba...`](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/godot/SKILL.md) covers Godot 4.x, GdUnit4, a custom automation fork, PlayGodot, screenshots, builds, and deployment.

**Actual supporting code:**

- [`validate_project.py`](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/godot/scripts/validate_project.py) resolves the project path, checks `project.godot`/main scene, runs headless import, optionally checks every non-addon GDScript, and returns failure status.
- [`run_tests.py`](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/godot/scripts/run_tests.py) verifies the project and GdUnit4 tool, constructs an argument-array command, supports filter/report/timeout, and preserves the engine return code.
- [`export_build.py`](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/godot/scripts/export_build.py) checks presets, creates output parents, launches headless export, and verifies an output path exists.

**Limitations and safety:** The package tells users to clone GdUnit4, install PlayGodot, use Vercel/itch.io tooling, and potentially build a custom Godot fork. Those are network, dependency, licensing, and supply-chain decisions, not harmless instructions. The Python scripts find executables with the Unix `which` command, so their stated Windows portability is incomplete. Some version and export-template discovery is heuristic; generated-output existence is not proof of a playable or correct build. A project path is resolved but not bounded to an approved workspace. The package is [MIT-licensed](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/LICENSE), but external GdUnit4, custom-engine, hosting, and deployment components retain their own terms.

**Transferability:** The separation of unit tests from external gameplay automation and the state/screenshot/input design are worth retaining. Commands, custom forks, deployment targets, and dependencies are not transferable before engine and platform selection.

#### Coding-Solo `godot-mcp`

**Classification finding:** MCP integration and command wrapper, not a skill. Its [package manifest at `1209744...`](https://github.com/Coding-Solo/godot-mcp/blob/1209744fad78f3998f98c7394fd0f6ef50da5281/package.json) identifies version `0.1.1`, Node 18+, MCP SDK `0.6.0`, filesystem helpers, Axios, and MIT. The [server implementation](https://github.com/Coding-Solo/godot-mcp/blob/1209744fad78f3998f98c7394fd0f6ef50da5281/src/index.ts) locates and launches Godot, validates project/executable paths, exposes runtime/debug and project operations, and calls a bundled [GDScript operations bridge](https://github.com/Coding-Solo/godot-mcp/blob/1209744fad78f3998f98c7394fd0f6ef50da5281/src/scripts/godot_operations.gd).

**Positive/negative evidence:** The audited head is a 2026-04-16 security fix that prevents arbitrary GDScript instantiation through a restricted class-name pattern. That is direct evidence of responsive security maintenance and direct evidence that the earlier design admitted a serious code-execution path. The server uses argument-array execution for its executable probe, which reduces shell-injection risk. Conversely, strict path validation defaults to false, fallback engine locations may be used after discovery fails, the package has no test command in `package.json`, and its dependency ranges are not locked in the inspected manifest.

**Transferability:** If Godot is selected, a read-only-first subset could be evaluated in a disposable project. The current version should not be adopted as-is. The explicit [MIT license](https://github.com/Coding-Solo/godot-mcp/blob/1209744fad78f3998f98c7394fd0f6ef50da5281/LICENSE) covers the repository’s code, subject to external dependency licenses.

### 2.3 Unreal Engine

#### Randroids Dojo Unreal package

**Classification finding:** Claude Code/Agent Skill package, command wrapper, and explicitly **unfinished experiment**. The [entry file at `aba2aba...`](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/unreal/SKILL.md) labels itself “WIP,” describes a target PlayUnreal API, and depends on Unreal Remote Control, Automation Driver, an automation actor/subsystem, and stable UMG identifiers. Its [PlayUnreal reference](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/unreal/references/playunreal.md) calls the companion repository a scaffolded MVP.

**Actual script:** [`run_e2e.py`](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/unreal/scripts/run_e2e.py) launches a caller-supplied Unreal executable/project/map, waits for a configured Remote Control host/port/object, invokes pytest, and terminates or kills the engine unless `--keep-alive` is set. The skill warns to keep Remote Control on LAN/VPN only.

**Assessment:** The package is candid about immaturity and encodes useful process shape, but target-API examples are not proof that the API exists or is stable. Launching an arbitrary supplied executable and exposing Remote Control are high-impact capabilities. There is no basis to reuse it for production, and no current project Unreal selection. Monitor only.

### 2.4 Browser games

#### OpenAI `develop-web-game`

**Classification finding:** A real Codex skill plus command wrapper and concrete test workflow at its audited historical revision. The [skill at `0ed635a...`](https://github.com/openai/skills/blob/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game/SKILL.md) requires incremental changes, Playwright input bursts, deterministic `advanceTime`, text-state output, screenshots, console review, reset between scenarios, and complete interaction chains. The [client script](https://github.com/openai/skills/blob/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game/scripts/web_game_playwright_client.js) launches Chromium, accepts URL/actions/output paths, synthesizes keyboard/mouse input, captures canvas/page PNGs, records text state and new console errors, and writes artifacts. Its [action fixture](https://github.com/openai/skills/blob/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game/references/action_payloads.json), [OpenAI metadata](https://github.com/openai/skills/blob/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game/agents/openai.yaml), and [Apache-2.0 license](https://github.com/openai/skills/blob/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game/LICENSE.txt) were present.

**Current-status warning:** This exact package was audited at the revision that added it on 2026-01-31. By the repository’s later 2026-06-24 head, the [catalog README declares the repository deprecated](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/README.md) and points to OpenAI Plugins. The exact package was not available through the pinned later-tree file lookup. Therefore this is an archived design exemplar, not a recommendation to install from the deprecated catalog.

**Safety and quality:** The script accesses a caller-supplied URL, launches a browser, reads actions, and writes to a caller-supplied screenshot directory. The skill suggests a global latest-version Playwright MCP install if prerequisites are absent; that is an unpinned network/system mutation and must be removed from any adaptation. Its virtual-time shim still relies on browser scheduling and is not a universal deterministic-simulation proof. Text-state parity and screenshots are valuable observability contracts, but the skill has no game-specific accessibility, localization, persistence, narrative, or sacred-content validation.

**Transferability:** Extract the narrow-change loop, external input driver, explicit state projection, deterministic seam, screenshot/log artifacts, and end-to-end interaction chains. Do not adopt the archived package or its installation guidance.

### 2.5 Custom engines

**Finding:** No audited family demonstrated a mature, engine-neutral custom-engine skill. The transferable shape is an adapter contract: launch/stop, controlled input, deterministic or recordable time, queryable state, logs, screenshots/video, build/export result, and clean recovery. That is an inference from the browser and editor integrations, not evidence that one adapter will work for every custom engine.

**Recommendation:** If the project later selects a custom engine, define those observability endpoints in the engine architecture before authoring a game-development skill. Do not retrofit an engine-specific MCP protocol by renaming its tools.

### 2.6 Blender and other DCC tools

#### `ahujasid/blender-mcp`

**Classification finding:** MCP integration and broad command wrapper, not a skill. The [server at `da4e16d...`](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/src/blender_mcp/server.py) connects to a local Blender add-on socket and exposes scene/query/mutation operations. The [add-on](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/addon.py) can edit Blender data and integrates external asset/generation providers. The package’s [Python metadata](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/pyproject.toml) declares version `1.6.0`, Python 3.10+, MCP and HTTP dependencies, and MIT; the repository has an explicit [MIT license](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/LICENSE).

**Network, credential, and telemetry finding:** The add-on reads provider keys from add-on preferences, scene values, or environment variables and can contact Poly Haven, Sketchfab, Hyper3D/Rodin, and Hunyuan endpoints. The [telemetry code](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/src/blender_mcp/telemetry.py) creates a persistent customer UUID, starts a background worker, sends usage events, supports environment-variable disable switches, withholds prompt/metadata without consent, and may send prompt/metadata/screenshots after consent. These behaviors require an explicit data-flow review; “anonymous” is not equivalent to “no network” or “no persistent identifier.”

**Safety and transferability:** A Blender bridge can accelerate inspection, transforms, materials, asset import, and screenshot evidence. It also places destructive DCC edits, arbitrary code/tool execution, third-party licensing, external downloads, provider secrets, and telemetry within agent reach. Because no DCC tool or asset provenance policy is selected, extract only the read-before-write, screenshot, scene-summary, and artifact-validation principles. Any future evaluation should disable telemetry and third-party providers by default, restrict to a disposable `.blend`, and require explicit approval for code execution, downloads, uploads, credential use, and overwriting.

### 2.7 Engine-level synthesis

| Ecosystem | Audited evidence | Current project decision |
|---|---|---|
| Unity | One broad maintained MCP bridge; one stale/missing advertised skill | No engine selected; no install or reuse |
| Godot | Two instruction packages and one early MCP bridge, with import/test/screenshot/runtime patterns | No engine selected; extract principles only |
| Unreal | One self-labeled WIP automation skill | Monitor; insufficient production evidence |
| Browser | One real but now archived Codex skill with a concrete Playwright loop | Extract validation/observability principles only |
| Custom engine | No mature audited package | Define an adapter only after architecture selection |
| Blender/DCC | One capable, networked, telemetry-bearing MCP bridge | No DCC selected; do not connect to project assets |

## 3. Discipline-by-discipline findings

The table records what the inspected files actually support, not what a generic coding model might be able to write.

| Discipline | Evidence in audited set | Evidence limit / project implication |
|---|---|---|
| Gameplay prototyping | Web skill iterates narrow HTML/JS mechanics; Unity/Godot bridges create scenes/nodes/components | No evidence of appropriate game design, bounded witness agency, or fun |
| Player controllers and input | Web action bursts; Godot editor/input examples; Unity transform/component tools; Unreal target locators | No controller-device matrix or remapping/accessibility proof |
| Combat | Only generic interaction examples and engine mutation primitives | No mature combat skill; sacred-event and moral-pressure rules absent |
| AI behavior and state machines | General code/editor capability only | No inspected behavior-tree/state-machine workflow or behavioral regression suite |
| Dialogue and quests | No dedicated package | Critical gap: no Scripture provenance, speaker knowledge, branching bounds, or sacred-event protection |
| Inventory/economy | No dedicated package | Critical gap: no schema, balance, save compatibility, provenance, or exploit tests |
| Save/load and world state | Text-state observation is not persistence; no round-trip package found | Must be designed against approved schemas and migration invariants later |
| NPC schedules | No dedicated package | No time/era/social-state validation evidence |
| UI/input | Strongest coverage: Playwright, Godot scene runners, Unreal target locator concept, Unity editor resources | Visual success still requires screenshots and human review; no full accessibility matrix |
| Animation | Blender/engine mutation can operate on assets indirectly | No dedicated animation-rig/retarget/import validation skill audited |
| VFX/shaders/materials | Unity MCP exposes material operations; Blender can edit materials/scenes | No shader compiler, variant, platform, visual-regression, or performance specialist package |
| Audio | None | No loudness, dialogue edit, localization, codec, streaming, attribution, or mix validation |
| Physics/navigation | Unity/Godot/Unreal can create/configure relevant objects; no focused workflow | No deterministic physics, navmesh, path-quality, or cross-frame regression evidence |
| Level design | Scene/object creation and screenshots exist | No spatial metrics, traversal validation, historical geography, or player-witness boundaries |
| Performance profiling | None beyond execution duration/telemetry | No CPU/GPU/frame-time, allocation, load-time, target-device, or budget evidence |
| Asset import/validation | Godot import loop; Unity AssetDatabase/prefab/material tools; Blender external assets | File rights, units, scale, pivots, LODs, naming, compression, and source provenance remain gaps |
| Build automation | Randroid Godot export wrapper; engine launch/test commands | Output existence is not playable correctness; no approved target/build matrix |
| Deployment | Randroid mentions Vercel, GitHub Pages, itch.io | Instructions can create external publication; no project authorization or chosen target |
| Automated gameplay | OpenAI web driver; PlayGodot examples; target PlayUnreal design | Web is concrete; PlayGodot needs a custom fork; PlayUnreal is WIP |
| Screenshot comparison | Web captures screenshots; PlayGodot text describes threshold comparison | Capturing is not automatically comparing; perceptual thresholds and baselines are undefined |
| Regression testing | GUT/GdUnit4/Unity Test Runner/pytest hooks | Package presence does not prove project coverage or correct oracles |
| Deterministic simulation | Web `advanceTime` seam; PlayGodot time controls | Browser shim is partial; no engine-wide deterministic replay/save evidence |
| Telemetry | Blender MCP usage telemetry; web/Godot observable state | Production player telemetry, privacy, consent, retention, minimization, and analytics are not covered |
| Accessibility | Text-state projection can aid nonvisual automation | No WCAG/game-accessibility checks, captions, remapping, contrast, motion, cognitive load, or assist modes |
| Localization | None | No string extraction, plural/gender rules, font/glyph, layout expansion, RTL, audio, or biblical-name policy |
| Console/platform requirements | Unreal plugin concepts and Godot export wrapper mention platforms | No certification, SDK, signing, entitlement, packaging, controller, suspend/resume, or store compliance |
| Image generation/procedural content | Blender MCP can call external 3D/asset providers; no dedicated image skill in the bounded set | Provider output is not historically or ethnically accurate and brings license/provenance/privacy risk |
| Narrative/codex knowledge | None | No in-world/player-codex separation, confidence labels, canon categories, or chronology enforcement |

**Finding:** Coverage is deepest where state can be made machine-readable and tools can be scripted. Coverage is weakest where quality depends on provenance, theology, history, human perception, long-lived data compatibility, and platform policy. That is precisely where this project’s stewardship risks are highest.

**Recommendation:** Do not respond to those gaps by creating many engine-role skills now. First select the stack and schemas, then turn verified project constraints and acceptance scenarios into testable contracts. Session 12 owns the detailed validation architecture; this report stops at landscape-level implications.

## 4. Artifact classification analysis

### 4.1 Mandatory classifications

| Artifact | Real Codex skill | Claude Code skill | Agent prompt | MCP integration | Reference guide | Command wrapper | Marketing demonstration | Tested workflow | Unfinished experiment |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| OpenAI `develop-web-game` at `0ed635a...` | Yes | No evidence | No | No | Supporting guidance | Yes | No | Yes, concrete script/fixtures; outcome benefit unverified | No, but later catalog deprecated |
| Fern Forest `godot` | Portable structure, not verified as Codex-tested | Yes-oriented | No | Requires external MCPs; is not itself MCP | Yes | Yes | No | Partial: script and test procedure; no outcome evidence | No explicit WIP |
| Randroid Godot | Repository claims dual compatibility | Yes | No | No | Yes | Yes | No | Yes, scripts/examples; independent use unverified | No explicit WIP |
| Randroid Unreal | Repository claims dual compatibility | Yes | No | Uses Remote Control, not itself MCP | Yes | Yes | No | Scaffold only | **Yes** |
| `akiojin` Unity listing | No current skill found | Advertised, absent | No | Advertises another MCP | README only | Unverified | **Yes, current listing without artifact** | No evidence | Missing/stale rather than a usable experiment |
| CoderGamester `mcp-unity` | No | No | No | **Yes** | README/prompts | **Yes** | README examples are demonstrations | Internal tests/tools; outcome evidence unverified | No explicit WIP |
| Coding-Solo `godot-mcp` | No | No | No | **Yes** | README | **Yes** | README examples are demonstrations | No package test command found | Early version; not labeled WIP |
| Ahuja `blender-mcp` | No | No | No | **Yes** | README/tool docs | **Yes** | External-provider demos exist | Some tests/maintenance; outcome evidence unverified | No explicit WIP |

Multiple columns can truthfully apply because a package may combine guidance, scripts, and integrations. Categories are not collapsed: for example, `mcp-unity` is an MCP integration even if its README contains prompts, and `develop-web-game` remains a real skill even though it invokes a command wrapper.

### 4.2 Quality is not category

- A **real skill** can still be stale, over-broad, unsafe, or ineffective.
- A **tested workflow** can still have weak or incomplete oracles.
- An **MCP integration** can be technically mature while being inappropriate for this project.
- A **marketing demonstration** can show intended use but cannot establish correctness or repeated benefit.
- An **unfinished experiment** can contribute a useful design pattern without being reusable.

## 5. Transferability to the verified project stack

### 5.1 Verified project state

At the predecessor SHA, the repository remains a documentation/research foundation. No engine, language, source tree, schema implementation, assets, builds, tests, IDE, MCP server, DCC, or deployment target has been selected. Unity is only conditional in the Master Protocol (“if Unity is chosen”). The controlling protocol also requires source honesty, sacred-event protection, chronology and in-world/player-facing knowledge separation, schema-first development, and bounded file behavior ([Master Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/ba2369e402f20249b98c55237dd5cd1209571e47/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md)).

Therefore **no engine-specific package is transferable as an operational dependency today**. An engine skill cannot select its own engine by activation, and an MCP connection cannot make a proposed stack authoritative.

### 5.2 Transfer now: principles, not packages

The following principles are stack-neutral enough to carry forward:

1. **Capability preflight:** discover engine/runtime/tool versions, project root, build targets, tests, permissions, and required external services before mutation.
2. **Smallest observable change:** tie one narrow diff or editor mutation to explicit acceptance criteria.
3. **Read-only before write:** inspect scene/entity tree, logs, dependencies, schemas, and current state before issuing mutations.
4. **Separate instruction from capability:** keep project rules and workflow in reviewed instructions; expose editor operations through a narrow tool adapter.
5. **Deterministic seam:** where feasible, provide controllable time, seeded randomness, stable selectors/IDs, and state projection.
6. **Layered observation:** record build/test return code, engine log, structured state, screenshot/video, output artifact, and repository/editor diff.
7. **Lifecycle ownership:** every launch has a bounded timeout and guaranteed stop/cleanup path.
8. **Failure truthfulness:** missing engines, tools, tests, licenses, or approvals are blockers or declared gaps, never simulated passes.
9. **External-action gate:** dependency installation, downloads/uploads, hosting, telemetry, secrets, and publication require explicit authorization and provenance review.
10. **Human review for stewardship:** no automated editor bridge can approve biblical faithfulness, historical uncertainty, sacred-event handling, ethnicity/material culture, or emotional meaning.

### 5.3 Transfer only after stack selection

After an authoritative engine/tool choice, reevaluate exact pinned packages against:

- supported engine/tool versions and project file formats;
- approved schemas, save compatibility, stable IDs, and source-provenance fields;
- chosen CI/host OS and shell/runtime availability;
- editor/headless licensing and build/export rights;
- platform targets and certification constraints;
- network, credential, telemetry, privacy, and artifact-retention policy;
- project-specific sacred, chronology, canon, and knowledge-boundary tests; and
- clean-baseline benchmarks versus the same tasks without the package.

No current row qualifies for `Adopt as-is`.

## 6. Existing-skill audit table

The reuse labels are restricted to the five authorized terms. “Evidence of real use” deliberately separates package execution evidence from independent outcome evidence.

| Repository | Skill | Platform | Intended purpose | Evidence of real use | Quality assessment | Safety concerns | License | Reuse decision |
|---|---|---|---|---|---|---|---|---|
| [`openai/skills@0ed635a`](https://github.com/openai/skills/tree/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game) | `develop-web-game` | Codex; HTML/JS/Chromium/Playwright | Incremental web-game implementation and observable play loop | Actual script, action fixture, metadata, and workflow; no independent repeated-outcome evidence; later catalog deprecated | Strong process shape, narrow observable loop, partial deterministic seam; archived availability | Caller URL/output writes, browser launch, global latest-package install advice, incomplete determinism | Apache-2.0 in package | **Extract principles only** |
| [`fernforestgames/agent-skill-godot@e584a97`](https://github.com/fernforestgames/agent-skill-godot/tree/e584a973fcf0590a4cbc6697fa5daa3d11585dbe) | `godot` | Claude-oriented Agent Skill; Godot 4+/GDScript/GUT; two required MCPs | Mandatory GDScript/resource workflow, docs, syntax, tests, editor interaction | Actual skill/script and active 2026 maintenance; no CI or independent outcome record found | Concise workflow and good observation; over-broad trigger, hard-coded 4.5/tool paths | Engine executes project scripts; Bash portability; external MCPs not audited; recursive project walk | MIT | **Extract principles only** |
| [`Randroids-Dojo/skills@aba2aba`](https://github.com/Randroids-Dojo/skills/tree/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/godot) | `godot` | Claude/Agent Skill; Godot 4.x, GdUnit4, PlayGodot, Python, web/desktop export | Develop, unit-test, automate gameplay, build, deploy | Actual validators/test/export scripts and examples; custom automation components; no controlled independent benefit | Broad and concrete, but dependency-heavy and portability/heuristic defects exist | Git/pip installs, custom engine fork, project/output writes, hosting/publication, executable discovery | MIT for collection; external components separate | **Extract principles only** |
| [`Randroids-Dojo/skills@aba2aba`](https://github.com/Randroids-Dojo/skills/tree/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/unreal) | `unreal` | Claude/Agent Skill; Unreal 5.x, Python, Remote Control | Target PlayUnreal E2E workflow and launcher | Actual launcher/wait/pytest scripts; entry and reference explicitly WIP/scaffolded | Honest scope and useful launcher shape; target API not mature evidence | Executes supplied binary/project, exposes Remote Control, kills process, pytest dependency | MIT | **Monitor** |
| [`akiojin/skills@4f72afe`](https://github.com/akiojin/skills/tree/4f72afeb9efb9520a7a02afb9e23fba2dbe0ffa1) | Advertised `unity-development` | Claude Code; claimed Unity C#/MCP/VContainer/UniTask | Unity coding and tests | README claim only; current marketplace and expected package paths do not contain it | Cannot assess instructions or scripts; stale/incomplete catalog evidence | Unknown because artifact is absent; dangerous to infer dependencies/permissions | Repository MIT, but no artifact to reuse | **Reject** |
| [`CoderGamester/mcp-unity@c35f184`](https://github.com/CoderGamester/mcp-unity/tree/c35f184d7656bd14e7748f11a05060feeb286d6e) | `mcp-unity` | MCP clients; Unity Editor; Node 18+ | Query and mutate Unity scenes/assets/packages/tests/play mode | Substantial implementation, test files, current diagnostic maintenance; no independent effectiveness comparison | Capable typed editor bridge; contradictory Unity-version statements | Delete/mutate scenes/objects, install packages, config writes, broad menu/tool reach, dependency ranges | Manifests say MIT; root license file not found at pin | **Monitor** |
| [`Coding-Solo/godot-mcp@1209744`](https://github.com/Coding-Solo/godot-mcp/tree/1209744fad78f3998f98c7394fd0f6ef50da5281) | `godot-mcp` | MCP; Godot; Node 18+/TypeScript/GDScript | Launch/run/debug and manipulate Godot projects/scenes | Real implementation and 2026 security fix; package has no test command; outcomes unverified | Useful bridge design and responsive fix; early version and incomplete validation defaults | Process launch, scene/resource writes, previously exploitable class instantiation, fallback paths | MIT | **Monitor** |
| [`ahujasid/blender-mcp@da4e16d`](https://github.com/ahujasid/blender-mcp/tree/da4e16d2069ce5154eaa2535bf995e843caf5c73) | `blender-mcp` | MCP; Blender 3+; Python 3.10+; external asset/generation APIs | Inspect/mutate Blender scenes and obtain/generate assets | Real server/add-on, tests and active maintenance; independent production benefit unverified | Broad and useful DCC bridge, but much larger trust surface than a reference skill | Code/tool execution, asset writes, external downloads/uploads, provider keys, persistent telemetry ID and network events | MIT | **Extract principles only** |

## 7. Patterns worth reusing

These are recommendations derived from the audit, not copied package instructions.

### 7.1 Observable gameplay contract

Require a game-facing adapter to expose the smallest truthful set of observations needed for a scenario: active scene/level, controllable actor state, relevant entities, objective flags, inventory/world-state subset, clock/seed, logs, and visual frame. A text projection must agree with the rendered state; it must not become a hidden alternate simulation.

### 7.2 Narrow edit–run–observe–correct loop

One accepted cycle should be:

1. identify one acceptance criterion and affected authority/schema;
2. make one bounded change;
3. build/import/compile or launch;
4. execute controlled inputs;
5. inspect state, visuals, and logs;
6. compare against the criterion and protected invariants;
7. correct and rerun; and
8. preserve evidence and stop the runtime.

This pattern appears independently in the web and Godot packages and is more defensible than a long one-shot generation prompt.

### 7.3 Stable selectors and identifiers

Automated input should address stable semantic identifiers, not screen coordinates where an accessible scene/widget/node identity exists. Project schemas should own stable IDs; a skill must not invent or rewrite them. Coordinates remain useful for spatial gameplay but need a declared coordinate system and resolution/input scaling.

### 7.4 Determinism as a designed seam

Prefer injected clocks, fixed timesteps, controlled random seeds, explicit reset, and snapshotable state. Record engine version, build, seed, scenario, inputs, and expected observation. Where determinism is impossible, record tolerances and sources of nondeterminism rather than declaring a flaky run deterministic.

### 7.5 Read-only and mutating tool separation

Expose observation tools separately from creation/update/deletion/package/network tools. Default to read-only. Require the caller to name the intended object/path and anticipated effect before mutation. Re-read the result afterward and retain an undo/recovery path that is stronger than “the tool returned success.”

### 7.6 Capability and side-effect manifests

For every executable helper or MCP, record:

- processes launched and termination behavior;
- files/directories read and written;
- scene/assets/settings mutated;
- network destinations and data sent;
- secrets/config locations accessed;
- dependencies and exact versions;
- destructive commands and approval boundaries;
- generated artifacts and cleanup; and
- license/notice obligations.

### 7.7 Tool-independent project guardrails

The witness premise, fixed sacred events, Scripture/source boundaries, historical uncertainty, schema-first discipline, and in-world/player-codex knowledge separation must remain in controlling project authority and validation. They must not exist only in an engine skill that may fail to trigger.

## 8. Patterns to reject

1. **Engine selection by skill activation.** A Godot/Unity/Unreal trigger is not an architecture decision.
2. **“Mandatory for all files” without exclusions and trigger tests.** Broad triggers crowd out appropriate tools and can load stale guidance.
3. **Latest/unpinned installs in task execution.** `npm ... latest`, `git clone` without a commit, mutable package ranges, and custom forks change the evaluated artifact.
4. **README-only maturity claims.** A listed skill with no current package is not reusable.
5. **MCP equals safety or expertise.** Tool schemas do not supply project authority, factual accuracy, or appropriate design judgment.
6. **Compile/import success as completion.** A build can be unplayable, visually wrong, disrespectful, historically incoherent, inaccessible, or save-incompatible.
7. **Screenshots without inspection or oracles.** Capturing PNGs is not visual regression and cannot prove hidden state.
8. **State text that diverges from the game.** Test-only alternate state can make automation pass while players see different behavior.
9. **Remote control exposed beyond the local trusted boundary.** Editor/runtime control endpoints must not be published casually.
10. **Silent telemetry or provider use.** Persistent IDs, prompts, screenshots, scene metadata, secrets, downloads, and uploads require explicit disclosure and policy.
11. **Destructive editor tools without exact targeting and verification.** Delete/save/package/install/batch actions require approval, backups or version-control recovery, and post-state inspection.
12. **External assets without provenance.** A generated or downloaded model/material/image is not production-ready until license, authorship, historical fit, cultural authenticity, source records, and import settings are verified.
13. **Automated approval of sacred or historical content.** Tools may flag and gather evidence; accountable human review remains mandatory.
14. **Final catalog formation from this sample.** These rows are audit evidence, not the project’s future skill list.

## 9. Gaps where no mature evidence exists

Within the bounded audit, no mature evidence established a reusable project-ready skill for:

- biblical text/source provenance and quotation-rights checks;
- protected sacred-event mechanics and anti-grief boundaries;
- historical confidence labels, disputed geography, or material-culture validation;
- era-limited NPC knowledge versus player-facing codex knowledge;
- lineage continuity, testimony inheritance, or cross-era world-state rules;
- dialogue, quest, codex, inventory/economy, or NPC-schedule schema enforcement;
- save/load round trips, schema migrations, and backward compatibility;
- combat/AI/state-machine correctness beyond generic code generation;
- animation/rig/retarget validation;
- shader/VFX compilation, platform variants, screenshot baselines, and GPU budgets;
- audio editing, loudness, spatialization, captions, attribution, and localization;
- procedural-generation constraints and human-authored sacred/historical boundaries;
- performance capture and target-device budgets;
- accessibility across input, visual, auditory, motion, cognitive, and difficulty needs;
- localization/RTL/font/glyph/layout/audio/cultural review;
- console certification, signing, entitlement, suspend/resume, store, and controller requirements;
- controlled benchmarks demonstrating a game skill’s improvement over no-skill baselines; or
- independent evidence of repeated successful use of the audited packages in comparable production projects.

These are **evidence gaps**, not proof that no package exists anywhere. The bounded search was designed for inspectability, and it did not attempt an exhaustive census. Future intake should begin only after the project has an authoritative stack or a sharply defined unmet capability.

### 9.1 Preliminary evidence ledger

| Claim or practice | Evidence source | Evidence type | Strength | Transferability | Risks/caveats |
|---|---|---|---|---|---|
| Narrow change plus controlled play observation is implementable | OpenAI web skill/script; Fern and Randroid Godot workflows | Actual pinned skill/script inspection | Moderate | High as a principle | Package outcomes not controlled; detailed architecture deferred to Session 12 |
| Deterministic time/state hooks improve automation observability | OpenAI `advanceTime`/text state; PlayGodot API examples | Implementation plus documented target API | Moderate | High if designed into runtime | Browser shim is partial; engine determinism not proven |
| MCP bridges provide large mutation surfaces | Unity, Godot, Blender server/tool files | Actual pinned implementation | Strong | High for intake/security | Tool list and permissions can change by revision |
| Package maintenance can reveal prior vulnerabilities | Coding-Solo class-name RCE fix at audited head | Security-fix commit plus code | Strong for that defect | High | One fix does not establish whole-package security |
| README/catalog claims can drift from current artifacts | `akiojin` README versus marketplace/files; OpenAI deprecation | Pinned repository contradiction | Strong | High | Absence at checked paths must be reevaluated at new revision |
| Engine version claims can conflict inside a package | CoderGamester README versus Unity manifest | Pinned file contradiction | Strong | High | Could be intentional compatibility, but no reconciliation found |
| Internal tests do not prove production benefit | All audited families | Evidence-method inference | Moderate | High | Independent usage could exist outside bounded sources |
| Project stack remains unknown | Session 1 and live predecessor repository | Pinned project audit | Strong | Critical | Must be re-audited if authority files change |
| External DCC generation adds privacy/license risk | Blender add-on, telemetry, provider integrations | Actual pinned implementation | Strong | High | Provider terms and payloads were not separately audited |
| No audited package enforces this project’s sacred/source rules | Package bodies versus Master Protocol | Comparative file inspection | Strong for sample | Critical | Does not prove no such package exists globally |

## 10. Source appendix with dates and commit SHAs

### 10.1 Project authority and predecessor research

All accessed 2026-07-22 at project predecessor `ba2369e402f20249b98c55237dd5cd1209571e47`:

- [Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/ba2369e402f20249b98c55237dd5cd1209571e47/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md).
- [Session 1 — Project Context and Authority Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/ba2369e402f20249b98c55237dd5cd1209571e47/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md).
- [Session 2 — Terminology and Artifact Taxonomy](https://github.com/Degrading1919/The_Bible_Video_Game/blob/ba2369e402f20249b98c55237dd5cd1209571e47/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md).
- [Session 3 — Current Codex Skill Capability Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/ba2369e402f20249b98c55237dd5cd1209571e47/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md).
- [Session 5 — Demonstrated Skill Success Evidence](https://github.com/Degrading1919/The_Bible_Video_Game/blob/ba2369e402f20249b98c55237dd5cd1209571e47/00_ADMIN/Research/LLM_Skills/05_Demonstrated_Skill_Success_Evidence.md).
- [Session 6 — Failure, Security, and Maintenance Risks](https://github.com/Degrading1919/The_Bible_Video_Game/blob/ba2369e402f20249b98c55237dd5cd1209571e47/00_ADMIN/Research/LLM_Skills/06_Skill_Failure_Security_and_Maintenance_Risks.md).

### 10.2 Audited package revisions

All files below were read directly and accessed 2026-07-22.

| Repository/package | Audited revision and date | Principal inspected files | License evidence |
|---|---|---|---|
| `openai/skills` `develop-web-game` | [`0ed635aad23fb73b98f75e0f99f407ffcaeba4ea`](https://github.com/openai/skills/commit/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea), 2026-01-31; deprecation checked at [`49f948faa9258a0c61caceaf225e179651397431`](https://github.com/openai/skills/commit/49f948faa9258a0c61caceaf225e179651397431), 2026-06-24 | [`SKILL.md`](https://github.com/openai/skills/blob/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game/SKILL.md), [Playwright client](https://github.com/openai/skills/blob/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game/scripts/web_game_playwright_client.js), [actions](https://github.com/openai/skills/blob/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game/references/action_payloads.json), [metadata](https://github.com/openai/skills/blob/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game/agents/openai.yaml), [deprecated README](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/README.md) | [Apache-2.0 package license](https://github.com/openai/skills/blob/0ed635aad23fb73b98f75e0f99f407ffcaeba4ea/skills/.curated/develop-web-game/LICENSE.txt) |
| `fernforestgames/agent-skill-godot` | [`e584a973fcf0590a4cbc6697fa5daa3d11585dbe`](https://github.com/fernforestgames/agent-skill-godot/commit/e584a973fcf0590a4cbc6697fa5daa3d11585dbe), 2026-01-14 | [`SKILL.md`](https://github.com/fernforestgames/agent-skill-godot/blob/e584a973fcf0590a4cbc6697fa5daa3d11585dbe/SKILL.md), [`check_syntax.sh`](https://github.com/fernforestgames/agent-skill-godot/blob/e584a973fcf0590a4cbc6697fa5daa3d11585dbe/scripts/check_syntax.sh) | [MIT](https://github.com/fernforestgames/agent-skill-godot/blob/e584a973fcf0590a4cbc6697fa5daa3d11585dbe/LICENSE) |
| `Randroids-Dojo/skills` | [`aba2aba9e43243959e7d5aa851a43983c3b7080d`](https://github.com/Randroids-Dojo/skills/commit/aba2aba9e43243959e7d5aa851a43983c3b7080d), 2026-07-19 | [Godot skill](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/godot/SKILL.md), [validate](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/godot/scripts/validate_project.py), [tests](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/godot/scripts/run_tests.py), [export](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/godot/scripts/export_build.py), [Unreal skill](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/unreal/SKILL.md), [E2E launcher](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/unreal/scripts/run_e2e.py), [WIP reference](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/plugins/unreal/references/playunreal.md) | [MIT](https://github.com/Randroids-Dojo/skills/blob/aba2aba9e43243959e7d5aa851a43983c3b7080d/LICENSE) |
| `akiojin/skills` | [`4f72afeb9efb9520a7a02afb9e23fba2dbe0ffa1`](https://github.com/akiojin/skills/commit/4f72afeb9efb9520a7a02afb9e23fba2dbe0ffa1), 2026-03-03 | [README listing](https://github.com/akiojin/skills/blob/4f72afeb9efb9520a7a02afb9e23fba2dbe0ffa1/README.md), [marketplace without Unity entry](https://github.com/akiojin/skills/blob/4f72afeb9efb9520a7a02afb9e23fba2dbe0ffa1/.claude-plugin/marketplace.json) | [Repository MIT](https://github.com/akiojin/skills/blob/4f72afeb9efb9520a7a02afb9e23fba2dbe0ffa1/LICENSE); no current Unity artifact |
| `CoderGamester/mcp-unity` | [`c35f184d7656bd14e7748f11a05060feeb286d6e`](https://github.com/CoderGamester/mcp-unity/commit/c35f184d7656bd14e7748f11a05060feeb286d6e), 2026-07-04 | [README/tool surface](https://github.com/CoderGamester/mcp-unity/blob/c35f184d7656bd14e7748f11a05060feeb286d6e/README.md), [Unity manifest](https://github.com/CoderGamester/mcp-unity/blob/c35f184d7656bd14e7748f11a05060feeb286d6e/package.json), [server manifest](https://github.com/CoderGamester/mcp-unity/blob/c35f184d7656bd14e7748f11a05060feeb286d6e/Server~/package.json), [path tests](https://github.com/CoderGamester/mcp-unity/blob/c35f184d7656bd14e7748f11a05060feeb286d6e/Editor/Tests/PathHandlingTests.cs) | Package manifests declare MIT; root license file not found at audited pin |
| `Coding-Solo/godot-mcp` | [`1209744fad78f3998f98c7394fd0f6ef50da5281`](https://github.com/Coding-Solo/godot-mcp/commit/1209744fad78f3998f98c7394fd0f6ef50da5281), 2026-04-16 | [README](https://github.com/Coding-Solo/godot-mcp/blob/1209744fad78f3998f98c7394fd0f6ef50da5281/README.md), [manifest](https://github.com/Coding-Solo/godot-mcp/blob/1209744fad78f3998f98c7394fd0f6ef50da5281/package.json), [server/security controls](https://github.com/Coding-Solo/godot-mcp/blob/1209744fad78f3998f98c7394fd0f6ef50da5281/src/index.ts), [operations script](https://github.com/Coding-Solo/godot-mcp/blob/1209744fad78f3998f98c7394fd0f6ef50da5281/src/scripts/godot_operations.gd) | [MIT](https://github.com/Coding-Solo/godot-mcp/blob/1209744fad78f3998f98c7394fd0f6ef50da5281/LICENSE) |
| `ahujasid/blender-mcp` | [`da4e16d2069ce5154eaa2535bf995e843caf5c73`](https://github.com/ahujasid/blender-mcp/commit/da4e16d2069ce5154eaa2535bf995e843caf5c73), 2026-07-21 | [README](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/README.md), [server](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/src/blender_mcp/server.py), [add-on](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/addon.py), [telemetry](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/src/blender_mcp/telemetry.py), [manifest](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/pyproject.toml) | [MIT](https://github.com/ahujasid/blender-mcp/blob/da4e16d2069ce5154eaa2535bf995e843caf5c73/LICENSE) |

### 10.3 First-party engine/tool documentation used to check package claims

Accessed 2026-07-22. These sources describe tool capability; they do not validate the audited third-party package:

- Godot Engine, [command-line tutorial](https://docs.godotengine.org/en/stable/tutorials/editor/command_line_tutorial.html) and [exporting projects](https://docs.godotengine.org/en/stable/tutorials/export/exporting_projects.html).
- Unity, [command-line arguments](https://docs.unity3d.com/6000.0/Documentation/Manual/CommandLineArguments.html) and [Unity Test Framework manual](https://docs.unity3d.com/Packages/com.unity.test-framework@1.4/manual/index.html).
- Epic Games, [Automation Test Framework](https://dev.epicgames.com/documentation/en-us/unreal-engine/automation-test-framework-in-unreal-engine) and [Remote Control API HTTP reference](https://dev.epicgames.com/documentation/en-us/unreal-engine/remote-control-api-http-reference-for-unreal-engine).
- Blender Foundation, [Blender Python API overview](https://docs.blender.org/api/current/info_overview.html) and [Python security](https://docs.blender.org/manual/en/latest/advanced/scripting/security.html).
- Microsoft Playwright, [input actions](https://playwright.dev/docs/input), [screenshots](https://playwright.dev/docs/screenshots), and [clock/time control](https://playwright.dev/docs/clock).

### 10.4 Final bounded conclusion

The audited landscape supports one restrained conclusion: **game-development skills are most credible when they bind a small change to a real engine/browser execution loop and produce inspectable state, visual, log, and artifact evidence.** It does not support selecting an engine, adopting a package, authorizing editor/network access, or creating a final skill catalog. For The Bible Video Game, generic automation value remains subordinate to the witness premise, protected sacred events, Scripture/source honesty, historical uncertainty, schema-first data, era knowledge, and accountable human review.

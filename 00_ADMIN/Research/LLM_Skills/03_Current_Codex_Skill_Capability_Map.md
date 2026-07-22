# Current Codex Skill Capability Map

**Session:** 3 of the LLM-skills deep-research sequence
**Research date:** 2026-07-22
**Repository:** [Degrading1919/The_Bible_Video_Game](https://github.com/Degrading1919/The_Bible_Video_Game)
**Predecessor checkout:** [`8fea4881e62498f1bce7498ff7a36e2af82de514`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/8fea4881e62498f1bce7498ff7a36e2af82de514)
**Documentation state:** Current OpenAI Codex manual fetched on 2026-07-22, supplemented only by the official Agent Skills specification and commit-pinned official OpenAI repositories where implementation history or licensing required a repository artifact.

This report describes current Codex behavior. It does not prescribe an ideal skill anatomy, create a skill, or select a final project skill catalog. **Documented** means stated in a current official source. **Observed** means visible in an identified implementation, issue, repository, or this execution environment but not promised by the public product documentation. **Inference** means a consequence reasoned from documented facts. **Unverified** means the available primary sources did not establish the behavior.

The project repository remains a documentation-and-research foundation with no engine, runtime code, schema, build system, test harness, `AGENTS.md`, or skill package at the predecessor commit. The [Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/8fea4881e62498f1bce7498ff7a36e2af82de514/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) remains the highest current repository document. A future skill must remain subordinate to the user/Creative Director, the player-as-witness premise, biblical source commitments, protected sacred events, era-knowledge boundaries, historical uncertainty, and schema-first production.

## 1. Documentation state and research date

### Findings

OpenAI's current [Build skills](https://learn.chatgpt.com/docs/build-skills) documentation defines a skill as a directory containing `SKILL.md`, with optional scripts and references, and says skills are available in the ChatGPT desktop app, Codex CLI, and the IDE extension. It describes explicit and implicit activation, progressive disclosure, four discovery scopes, optional `agents/openai.yaml`, skill disabling, local authoring, and plugin distribution. The companion [Skills section of the customization guide](https://learn.chatgpt.com/docs/customization) repeats the same repository root, progressive-disclosure, and invocation model. The open [Agent Skills specification](https://agentskills.io/specification) defines the shared portable package core but does not establish every Codex-specific behavior.

These are living documents. The locally fetched manual did not expose a page-level publication date or an auditable documentation-repository SHA, so each living page is recorded as **accessed 2026-07-22**. Where a source file was inspected in an official repository, this report pins the commit. The formerly central [`openai/skills`](https://github.com/openai/skills) catalog was marked deprecated on 2026-06-22 in favor of the OpenAI Plugins repository and the current Build plugins route. Its latest inspected commit for this report is [`49f948faa9258a0c61caceaf225e179651397431`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431). It remains useful as a dated implementation artifact, not as the primary current distribution recommendation.

The public documentation is precise about storage, metadata, discovery, explicit/implicit selection, progressive disclosure, and tool dependency declaration. It is not comparably precise about skill-to-skill precedence, conflict resolution, simultaneous-skill ordering, activation duration after selection, or failure semantics for unavailable dependencies. Those gaps are not filled with community convention in this report.

### Project consequence

Session 17 can safely encode the documented package and repository location. It must not encode undocumented conflict or lifecycle behavior as a platform guarantee. Any dependency, multi-skill composition, or fallback behavior must be made explicit in the skill's own workflow and then tested in the target Codex surfaces.

## 2. Verified storage and discovery model

### Repository-local root resolved for Session 17

**Resolved root:** `<repository-root>/.agents/skills`
**Resolved Session 17 package path:** `<repository-root>/.agents/skills/the-bible-video-game-skill-builder/`

For this repository, the exact future path is therefore:

```text
.agents/
  skills/
    the-bible-video-game-skill-builder/
      SKILL.md
```

This is the repository-wide root documented by [Build skills, “Where to save skills”](https://learn.chatgpt.com/docs/build-skills#where-to-save-skills). Codex scans `.agents/skills` in every directory from the current working directory upward to the repository root. A skill at the repository root is available across the repository; a skill placed under a narrower working subtree is relevant to Codex sessions launched from that subtree. The current guide expressly describes the repository root location as `$REPO_ROOT/.agents/skills` and the user location as `$HOME/.agents/skills`.

The four documented scopes are:

| Scope | Documented location | Intended reach | Project use now |
|---|---|---|---|
| Repository | `$CWD/.agents/skills`, parent `.agents/skills` directories, through `$REPO_ROOT/.agents/skills` | Checked-in workflows for a working folder, shared area, or entire repository | **Use the repository-root form for Session 17** so the builder is versioned with and available throughout this project. |
| User | `$HOME/.agents/skills` | Personal skills across repositories | Do not use for the authoritative project builder; it would not travel with the repository. |
| Admin | `/etc/codex/skills` | Machine/container-wide defaults | Not controlled by this repository and not portable to every contributor. |
| System | Bundled with Codex by OpenAI | Built-in broad-use skills | Not writable project scope; the current `skill-creator` is an example. |

The current desktop execution environment exposes bundled system skills from an internal `C:\Users\CK\.codex\skills\.system` installation tree. The older pinned creator implementation also contains examples using `${CODEX_HOME:-$HOME/.codex}/skills`. Those are **observed/internal or historical installation paths**, not the current documented repository-authoring root. They do not displace `.agents/skills`, and they should not be copied into Session 17. The current living “Where to save skills” table is authoritative for new repository-local authoring.

The documentation states that symlinked skill folders are supported and their targets are followed. An official `openai/codex` issue records a maintainer reproducing symlink support in Codex 0.98 while noting that live file-watcher updates did not propagate through a symlink until relaunch ([issue #11314](https://github.com/openai/codex/issues/11314)). That issue is **observed version-specific evidence**, not a reason for this project to use a symlink. A real checked-in directory is simpler, portable, and auditable.

Codex begins with an availability list containing each discovered skill's name, description, and file path. It may shorten descriptions and, for a sufficiently large installation, omit some skills and show a warning. It does not merge packages merely because they share a name; the guide says both same-name skills can appear in selectors. Therefore, skill names are not a reliable precedence mechanism.

### Distinction from repository instructions

`AGENTS.md` uses a separate discovery chain. According to [Custom instructions with `AGENTS.md`](https://learn.chatgpt.com/docs/agent-configuration/agents-md), Codex loads global guidance and then one applicable instruction file per directory from repository root to the current working directory; closer files occur later and override earlier guidance. `AGENTS.override.md` takes priority over `AGENTS.md` within a directory. That documented path-based precedence does **not** automatically apply to skills. A `SKILL.md` is conditionally selected workflow context, whereas `AGENTS.md` is persistent repository guidance read before work.

### Recommendation

Use `.agents/skills/the-bible-video-game-skill-builder/` in Session 17. Do not use `.codex/skills`, `00_ADMIN/Skills`, `Research/LLM_Skills`, or the current user's global skill directory. If permanent Codex repository instructions are later desired, consider a separate root `AGENTS.md` only through an approved governance task; Session 17 must not create one.

## 3. Skill package anatomy

### Required core

A skill is a directory. Its only required named file is `SKILL.md`. The current Codex guide's minimal form is:

```markdown
---
name: skill-name
description: Explain exactly when this skill should and should not trigger.
---

Skill instructions for Codex to follow.
```

The required YAML frontmatter fields are `name` and `description`; the Markdown body is the operational instruction content. The open specification further constrains `name` to a lowercase hyphenated identifier and treats the description as the discovery signal. Codex-specific current documentation emphasizes front-loading the principal use case and trigger language because long descriptions may be shortened in the initial availability list.

Only the minimum fields above are needed for Codex discovery. The official bundled skill-creator snapshot includes an additional `metadata.short-description` field, but the inspected implementation itself says `name` and `description` are the fields Codex reads to decide when a skill is used ([pinned `skill-creator/SKILL.md`](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator/SKILL.md)). Extra metadata seen in a package must not be assumed mandatory or portable without current documentation.

### Optional Codex metadata

`agents/openai.yaml` is optional. [Build skills, “Optional metadata”](https://learn.chatgpt.com/docs/build-skills#optional-metadata) documents three groups:

- `interface`: user-facing display name, short description, icons, brand color, and default prompt;
- `policy.allow_implicit_invocation`: defaults to `true`; setting it to `false` blocks implicit selection while preserving explicit `$skill` invocation;
- `dependencies.tools`: declarations such as an MCP server dependency, including a tool type, value, description, transport, and URL.

This file improves UI presentation, invocation policy, and dependency wiring. It is not a second instruction-authority file, and a dependency declaration does not prove that the capability is authenticated, authorized, reachable, or safe in the current environment.

### Optional bundled resources

The documented conventional directories are:

- `scripts/` for executable helpers or deterministic validation;
- `references/` for detailed material that should enter context only when relevant;
- `assets/` for templates, icons, fonts, or other output resources;
- `agents/` for OpenAI-specific metadata.

Examples, templates, and sample inputs can be ordinary files inside the package, but their function and loading trigger must be explained by `SKILL.md`. Codex does not infer an artifact's authority, safety, or relevance merely from its folder name. The official creator recommends instructions by default and scripts only when deterministic behavior or external tooling warrants them.

### Licensing files

Licensing is package-specific. The deprecated OpenAI skills catalog's pinned [README](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/README.md) explicitly says each individual skill's license is found in that skill directory's `LICENSE.txt`; it does not grant one blanket license for every package through the catalog README. Any future adaptation must inspect the exact skill directory, referenced code, assets, and license at a pinned commit.

## 4. Invocation and lifecycle

### Explicit invocation

[Build skills, “How Codex uses skills”](https://learn.chatgpt.com/docs/build-skills#how-codex-uses-skills) documents explicit invocation by naming the skill in the prompt. In CLI and IDE, `/skills` or typing `$` exposes skill selection. A direct `$skill-name` reference is the clearest way to require a skill. In ChatGPT surfaces, plugin-packaged skills can be explicitly selected with the plugin/skill affordance described in [Plugins](https://learn.chatgpt.com/docs/plugins).

`policy.allow_implicit_invocation: false` makes a skill user-invoked-only in the documented sense: Codex will not choose it from a task-description match, but explicit `$skill` invocation remains available. This is useful for workflows whose side effects, cost, or special mode should require deliberate selection.

### Implicit or model-selected invocation

By default, Codex may select a skill when the user's task matches the `description`. The initial catalog provides metadata rather than full bodies, so the description must communicate both positive triggers and important exclusions. Implicit matching is model selection, not a deterministic routing rule. The docs recommend testing prompts against the description; they do not publish a confidence threshold, matching algorithm, tie-breaker, or guarantee that every relevant skill will appear when the installed catalog exceeds the context budget.

### User-invoked versus model-invoked

The execution body is the same package after selection; the difference is how it was selected. Explicit invocation communicates user intent and survives `allow_implicit_invocation: false`. Implicit invocation depends on current catalog inclusion and semantic match. Neither mode increases tool permissions or authority over higher instructions.

### Duration and refresh

The docs establish that the full `SKILL.md` is loaded **when Codex decides to use the skill for a task**. They do not formally define whether its instructions remain active for exactly one turn, an entire multi-turn task, a resumed session, or until context compaction. The safe project model is therefore: **activation is task-context behavior, not durable policy**. If a later turn materially depends on the builder, invoke it again or verify that it remains in the active context.

The current guide says Codex detects skill changes automatically and recommends restarting if an update does not appear. A later official `openai/skills` commit states that Codex refreshes its skill catalog between turns and updates installer guidance accordingly ([commit `49f948f…`](https://github.com/openai/skills/commit/49f948faa9258a0c61caceaf225e179651397431)). Because this is implementation history and surface/version behavior rather than a cross-surface lifecycle contract, Session 17 should validate discovery in a fresh context and record the tested surface/version.

## 5. Precedence and conflict behavior

### Documented findings

The public docs provide a clear precedence model for `AGENTS.md`, configuration, managed requirements, sandbox rules, and approval policy. They do **not** publish a comparable universal precedence ladder among simultaneously selected skills. They also state that two same-name skills are not merged and can both appear, which rules out treating name collision as deterministic override.

Every skill remains subject to higher system/developer instructions, active user instruction, sandbox/approval controls, and repository authority. Within this project, the user/Creative Director, player-as-witness premise, biblical source commitments, approved canon/scope, and Master Assistant Protocol remain authoritative. A lower-authority reusable workflow must not override sacred-event protection, source-confidence labeling, era knowledge, schema-first rules, or the prohibition on inventing absent project facts.

### Undocumented gaps

Current official sources do not establish:

- which of two active skill bodies wins if they contain contradictory steps;
- whether explicit invocation always outranks an implicitly chosen skill body;
- ordering when a prompt names several skills;
- whether later-loaded skill text overrides earlier-loaded skill text;
- a standard “conflicts with” or “compatible with” metadata field;
- a namespace or semantic-version resolver for same-name skills;
- a skill-level escape hatch from higher repository or runtime instructions.

### Project consequence

Do not rely on hidden platform precedence. For any composed workflow, identify the controlling authority, declare the ordered phases in the caller or orchestrating workflow, specify never-override rules, and emit a composition trace. If two skills prescribe incompatible actions, stop before the conflicting action and surface the conflict to the user rather than silently blending them. Session 14 will design the project governance model; this report only records the platform gap.

## 6. Composition and dependencies

### Multiple skills

Official documentation supports packages containing multiple skills and exposes multiple skill metadata entries to Codex. It also permits users to explicitly name skills. These facts make multi-skill use technically plausible and visible in current Codex environments. However, the public docs do not define a formal simultaneous-execution object, ordering algorithm, or conflict semantics. The conservative conclusion is:

> Multiple skills can be available and can be requested for one task, but reliable composition must be represented as an explicit ordered workflow rather than assumed from co-activation.

This is an **inference from documented availability and explicit invocation**, not a documented dependency engine.

### Dependency representation

The only current Codex-native dependency declaration documented inside a skill is `dependencies.tools` in `agents/openai.yaml`, principally for MCP/tool wiring. It represents capability needs; it does not represent a required companion skill, version range, execution order, conflicting skill, repository file, human approver, or fallback strategy.

Plugins are the documented distribution unit when bundling two or more skills or pairing skills with connectors/MCP configuration. That packaging relationship does not itself impose runtime order. [Skills + MCP](https://learn.chatgpt.com/docs/customization#skills--mcp-together) describes the intended division: the skill defines the repeatable workflow and names the external capability; MCP supplies tools and context.

### Skill-to-skill invocation

No current official public source reviewed here defines a privileged API through which one skill deterministically invokes another, nor a guarantee that a skill's textual instruction to “use skill X” will resolve. A skill may instruct Codex to apply another named workflow, but that is ordinary model-followed instruction and should be treated as unverified until tested. User-invoked-only skills should not be silently pulled in by another skill; their `allow_implicit_invocation: false` policy communicates a deliberate activation boundary.

### Project consequence

Session 17 should be self-contained for its bounded builder workflow and should treat other skills as optional capabilities discovered at runtime, not hard dependencies. If it needs `skill-creator`, its instructions should explicitly require that workflow, verify availability, and define a fallback or stop condition. It must not create a final catalog or invent project companion skills.

## 7. Context loading and progressive disclosure

Codex applies three documented loading stages:

1. **Discovery metadata:** initial context contains each available skill's `name`, `description`, and file path.
2. **Selected body:** Codex reads the full `SKILL.md` only after choosing the skill.
3. **On-demand resources:** Codex reads references or runs scripts only when the selected workflow needs them.

The initial skill list receives at most 2% of the model's context window, or 8,000 characters when the context window is unknown. Descriptions are shortened first; with large catalogs, some skills can be omitted and Codex shows a warning. This limit applies to the initial catalog, not to the selected skill's body.

Progressive disclosure saves the main task context from carrying every detailed reference. It does not make downstream files free: the selected `SKILL.md`, each loaded reference, script output, conversation history, repository file, and tool result still consumes usable context. Nor does it guarantee that Codex will choose the correct reference. The body must route precisely—for example, “read `references/source-classification.md` before creating a source-backed artifact”—and should avoid chains of links that require exploratory context expansion.

Assets need not be loaded as reasoning context if they are simply copied or used by a deterministic step, but their provenance and license still matter. Scripts may reduce token cost by performing deterministic transformations; their code and outputs still require security review and bounded execution.

### Project consequence

The builder's primary `SKILL.md` should contain the authority check, whether-to-build decision, workflow, safety boundaries, output contract, validation, and stopping rules. Detailed checklists, schemas, examples, or evaluation fixtures should be supporting files only when Session 16 expressly requires them. Canonical project authority should remain in existing repository documents and be read by path rather than duplicated into the skill.

## 8. Tool, shell, sandbox, MCP, and Git interaction

### Capability boundary

A skill supplies instructions and optional executable files; it does not grant a tool, shell, network connection, credential, filesystem permission, MCP server, Git remote permission, or approval bypass. Codex can complete the workflow only with capabilities available in the current host. `dependencies.tools` can declare needs and help installation/wiring, but the agent must still verify availability and authorization.

[Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security) distinguishes sandbox mode—what can technically occur—from approval policy—when user permission is required. Local Codex defaults normally restrict writes to the active workspace and network access is off; actions outside the workspace or requiring network can prompt for approval. Destructive connector/MCP actions require approval when correctly annotated. A skill instruction cannot weaken those controls.

### Shell and scripts

Files under `scripts/` are ordinary executable code once invoked. Their interpreter, dependencies, inputs, working directory, filesystem scope, network behavior, exit status, and side effects must be inspected. “Bundled with a skill” is not a trust signal. Prefer instruction-only skills until deterministic behavior justifies code; then use narrow parameters, fail closed, and verify outputs.

### MCP

[Model Context Protocol](https://learn.chatgpt.com/docs/extend/mcp) documents local MCP support shared by the ChatGPT desktop app, Codex CLI, and IDE extension on the same Codex host. MCP servers can expose tools, resources, prompts, and server-wide instructions. Local configuration normally lives in `~/.codex/config.toml`, with trusted-project `.codex/config.toml` also supported. ChatGPT web does not read local Codex configuration; hosted Work mode obtains remote MCP-backed capabilities through plugins.

A malicious or stale MCP server can return untrusted instructions/data or expose high-impact actions. Therefore a skill must not treat an MCP result as higher authority than project policy and must preserve provenance boundaries.

### Git

Skills have no special Git layer. Git commands run through the shell/tool path under the same sandbox, approval, branch, and credential constraints as any other model-generated command. A skill may prescribe status checks, narrow staging, commit conventions, or verification; it cannot make force-push, destructive reset, branch rewrite, or credential access safe by instruction alone. Session 17 must not commit or publish autonomously when used later unless the user's task grants that action and the environment permits it.

### Unavailable capability behavior

The current skill docs do not define an automatic standard response when a declared tool is absent, an MCP server is unauthenticated, a script runtime is missing, or Git has no usable remote. The builder should require a preflight, choose a documented read-only or instruction-only fallback only if it still satisfies the output contract, and otherwise report the precise missing capability and stop. It must never fabricate inspection, validation, or publication.

## 9. Portability matrix

| Surface | Direct skill availability | Repository-local `.agents/skills` confidence | Tools/configuration notes | Project consequence |
|---|---|---|---|---|
| ChatGPT desktop app — Codex | Officially documented | High for a local repository opened in Codex; living docs accessed 2026-07-22 | Shares local Codex MCP configuration; skill UI available; sandbox/approval policy still controls effects | Primary target for the current authoring and forward test. |
| Codex CLI | Officially documented | High; `.agents/skills` scanning from CWD to repo root is directly documented | `/skills` and `$` explicit invocation; local shell and config behavior varies by OS and policy | Test package discovery from repository root and a nested directory. |
| Codex IDE extension | Officially documented | High from the shared skill docs, but exact UI affordances may differ | Supports direct skills and shared local MCP configuration; plugins themselves are not available in the IDE extension | Keep the package independent of plugin-only UI or connector assumptions. |
| ChatGPT desktop app — Work mode | Skills are available principally through installed plugins | Direct checkout discovery is not established by the reviewed public docs | Plugin may bundle skills, connectors, MCP servers, hooks, and assets | A repo-local builder is not automatically a distributable Work-mode package. |
| ChatGPT web — Work mode | Plugin-packaged skills documented | Local `.agents/skills` is not read from the user's machine | Web does not read local Codex config; workspace/plugin permissions govern tools | Distribution here would require a separately reviewed plugin path, outside Session 17. |
| Codex cloud/hosted environment | Skills may be present through the checked-out project or installed environment, but direct parity was not explicitly guaranteed in the reviewed skill page | **Unverified across hosted configurations** | Cloud runs in isolated containers; setup and agent phases have different network/secrets behavior | Run a target-environment test before relying on the builder in cloud automation. |
| Mobile / ordinary Chat mode | Plugins are documented as unavailable in mobile and Chat mode | Not applicable | No supported repo-local Codex authoring environment established | Out of scope. |

The portable core is the Agent Skills package: a directory with `SKILL.md`, YAML `name`/`description`, instructions, and optional resources. Discovery roots, UI metadata, implicit-invocation policy, tool wiring, plugin availability, sandbox behavior, and lifecycle remain Codex/surface-specific. An artifact working in one surface is evidence for that surface and version, not universal portability.

## 10. Versioning and distribution model

### Local and repository authoring

Direct skill folders are the documented mechanism for local authoring and repository-specific workflows. A repository skill inherits ordinary Git history: changes are reviewable, attributable, reversible, and pinned by project commits. Codex detects updates, though a fresh turn/session or restart may be needed depending on surface and version. There is no required semantic-version field in the current minimal `SKILL.md` format.

### User installation

`$skill-installer` is the documented path for installing curated skills or a skill from another repository into a user's environment. Installation copies third-party instructions and potentially executable content into a trusted local scope; it is therefore a supply-chain action, not a harmless prompt import. Disabled skills can be listed with `[[skills.config]]` and `enabled = false` in `~/.codex/config.toml`; current docs require restart after changing that configuration.

### Team/public distribution

Current documentation recommends plugins when distributing a workflow beyond one repository, bundling two or more skills, or shipping skills with connectors. The official [`openai/skills` README at `49f948f…`](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/README.md) now marks that catalog deprecated and routes users to the OpenAI Plugins repository and [Build plugins](https://learn.chatgpt.com/docs/build-plugins). Plugins add their own manifest, marketplace, permissions, connector, hook, and review concerns. Session 17 is explicitly a repository-local skill and should not create a plugin.

### Project version discipline

Pin every external skill audit to repository, path, commit SHA, and individual license. Record the Codex surface/version used in validation. Update the skill only through reviewed project commits. When Codex or the skill format changes, rerun discovery, invocation, dependency, security, and forward tests rather than relying on a version string inside prose.

## 11. Security, licensing, and provenance

### Security findings

Third-party skills are executable supply-chain inputs in two ways: their instructions can steer the agent, and their scripts/assets can cause or influence effects. Principal risks include prompt injection, concealed destructive commands, credential or environment-variable access, network exfiltration, unsafe installers, dependency substitution, stale tool guidance, broad filesystem operations, Git history changes, falsified validation, and authority inversion.

OpenAI's plugin submission guidance states that uploaded skills are scanned for sensitive information, unnecessary access requests, and instructions conflicting with safe behavior. That marketplace control is useful but is not proof that a package is correct for this project, and it does not apply as a complete project review of an arbitrary copied repository skill. Local repository owners remain responsible for reading `SKILL.md`, every script, referenced file, asset, metadata file, and dependency declaration.

Minimum intake controls for any future reuse are:

1. Pin the exact commit and enumerate the entire package tree.
2. Read the instructions and all transitively referenced files.
3. Inspect every executable, its dependencies, inputs, outputs, network use, and destructive paths.
4. Verify the individual license, notices, asset rights, and attribution obligations.
5. Compare its instructions against system/developer rules, the Master Protocol, current user decisions, schemas, and target tool versions.
6. Remove secrets and reject instructions asking the agent to ignore higher authority or hide evidence.
7. Test in a constrained clean context with non-sensitive fixtures and least privilege.
8. Record adaptation provenance; do not erase the origin or imply that copied text is project-authored research.

### Licensing findings

Repository visibility, stars, marketplace presence, or “open source” language is not a license. The deprecated official catalog explicitly places licenses inside individual skill folders. Code, prose, templates, icons, fonts, images, and other assets can have different terms. A compatible license may require retaining copyright notices, a license copy, attribution, change notices, or source availability. Absence or ambiguity requires rejection or permission—not inferred reuse rights.

For this project, provenance has theological and historical importance as well as legal importance. A reused reference must not launder uncertain historical reconstruction into biblical fact. Scripture translations, original-language data, archaeology, iconography, and sacred-figure assets require their own source, confidence, and copyright review even when delivered inside a technically licensed skill.

## 12. Limitations and unresolved questions

The following claims were not established by current official sources and must remain open until reproducibly tested or documented:

1. Exact priority and merge behavior when two selected skills conflict.
2. Deterministic ordering for several explicitly named skills.
3. Whether explicit invocation outranks an implicitly selected incompatible skill body.
4. A native required/optional skill-to-skill dependency schema.
5. A native companion/conflict declaration or semantic-version resolver.
6. Guaranteed duration of a skill body across turns, task continuation, compaction, resume, or handoff.
7. A guaranteed refresh interval common to desktop, CLI, IDE, and hosted environments.
8. Whether every repository-local skill appears when the catalog exceeds the initial context budget.
9. Universal behavior for symlink live reload despite documented scan support.
10. Guaranteed installation/authentication behavior for `dependencies.tools` across surfaces.
11. Standard fallback behavior for missing tools, runtimes, MCP authentication, or Git access.
12. Full parity of repository-local discovery and scripts in Codex cloud/hosted configurations.
13. Whether one skill can programmatically force another user-invoked-only skill to activate.
14. A platform guarantee that a skill cannot be silently weakened by an ambiguous description or competing task context.
15. A public API for exposing active skill composition traces and source order to project evaluators.

These gaps do not prevent a repository-local skill builder. They require explicit boundaries, preflight checks, conservative stopping behavior, and targeted evaluation. The engine and implementation stack also remain unknown; Session 17 must not add Unity, Godot, Unreal, Blender, or other stack-specific instructions.

## 13. Claim-status table

| Claim | Officially documented | Observed | Unverified | Source/date | Project consequence |
|---|:---:|:---:|:---:|---|---|
| Codex skills are directories with required `SKILL.md` and optional resources/scripts. | Yes | Yes, official packages | No | [Build skills](https://learn.chatgpt.com/docs/build-skills), accessed 2026-07-22; [`skill-creator` at `49f948f…`](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator/SKILL.md) | Session 17 can create the standard directory package. |
| Required frontmatter fields are `name` and `description`. | Yes | Yes | No | Same sources; 2026-07-22 | Keep required discovery metadata minimal and precise. |
| The exact repository-wide skill root is `<repo>/.agents/skills`. | Yes | Yes, current environment exposes that convention | No | [Where to save skills](https://learn.chatgpt.com/docs/build-skills#where-to-save-skills), accessed 2026-07-22 | Session 17 root is `.agents/skills/the-bible-video-game-skill-builder/`. |
| Codex scans repository `.agents/skills` from CWD upward to repo root. | Yes | Not independently retested here | No | Same source; 2026-07-22 | Root placement supplies project-wide reach; nested placement would narrow discovery. |
| User skills live at `$HOME/.agents/skills`; admin and system scopes also exist. | Yes | Bundled system skills are visible from an internal `.codex/skills/.system` tree, which is not the documented USER authoring root | No for the documented path; internal install layout is not a portable contract | Same source; 2026-07-22 | Do not put the authoritative project builder in a user's private or internal system scope. |
| Symlinked skill folders are followed. | Yes | Maintainer observed in Codex 0.98; live reload limitation reported | No for basic discovery; yes for cross-version live reload | [Build skills](https://learn.chatgpt.com/docs/build-skills); [openai/codex #11314](https://github.com/openai/codex/issues/11314), 2026-02-10 | Use a real checked-in directory and avoid watcher ambiguity. |
| Initial context contains skill name, description, and path; full body loads after selection. | Yes | Yes | No | [Build skills](https://learn.chatgpt.com/docs/build-skills), accessed 2026-07-22 | Description quality governs discovery; body detail does not help initial matching. |
| Initial skill-list budget is at most 2% of context or 8,000 characters when unknown. | Yes | Not measured here | No | Same source; 2026-07-22 | Avoid a large catalog and verbose descriptions; omissions are possible. |
| Skills may be invoked explicitly or selected implicitly by description match. | Yes | Yes | No | [How Codex uses skills](https://learn.chatgpt.com/docs/build-skills#how-codex-uses-skills), 2026-07-22 | Provide explicit usage and test both positive and negative triggers. |
| `allow_implicit_invocation: false` preserves explicit invocation while blocking implicit selection. | Yes | Not independently retested here | No | [Optional metadata](https://learn.chatgpt.com/docs/build-skills#optional-metadata), 2026-07-22 | Use for intentionally manual workflows if Session 16 requires it. |
| Two same-name skills are merged or one deterministically overrides the other. | No; docs say they are not merged and both may appear | Same-name visibility reported by docs | **Yes: tie behavior** | [Where to save skills](https://learn.chatgpt.com/docs/build-skills#where-to-save-skills), 2026-07-22 | Require unique names; do not use collision as versioning or precedence. |
| Several skills can be requested for one task. | Indirectly: multiple available skills and explicit mentions are documented | Current Codex environments expose multiple skills together | **Ordering/merge semantics unverified** | [Build skills](https://learn.chatgpt.com/docs/build-skills), 2026-07-22 | Express composition as an ordered workflow and test it. |
| Codex publishes skill-to-skill precedence/conflict rules. | No | No reliable primary observation selected | Yes | Official manual reviewed 2026-07-22 | Never depend on implicit precedence; surface conflicts. |
| `agents/openai.yaml` may declare UI, implicit invocation policy, and MCP/tool dependencies. | Yes | Yes in official packages | No | [Optional metadata](https://learn.chatgpt.com/docs/build-skills#optional-metadata); official package snapshot `49f948f…` | Include only metadata Session 16 requires and validate it against `SKILL.md`. |
| A dependency declaration guarantees installation, authorization, and access. | No | No | Yes | Current docs describe declaration/wiring, not universal availability; 2026-07-22 | Preflight every capability and fail honestly. |
| A skill grants shell, network, filesystem, MCP, or Git permission. | No; sandbox and approvals remain separate controls | Current environment enforces them independently | No | [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security), 2026-07-22 | Skill instructions cannot bypass safety or publication approval. |
| Repository instructions and skills share the same discovery/precedence algorithm. | No; different algorithms are documented | Separate current surfaces observed | No | [`AGENTS.md`](https://learn.chatgpt.com/docs/agent-configuration/agents-md) and [Build skills](https://learn.chatgpt.com/docs/build-skills), 2026-07-22 | Keep always-on governance separate from conditional workflow skills. |
| A selected skill remains active for an entire session. | No published guarantee | Behavior can persist while context remains, but was not controlled here | Yes | Manual review 2026-07-22 | Reinvoke or verify on later turns; do not store permanent policy only in the skill. |
| Skills work in ChatGPT desktop Codex, CLI, and IDE extension. | Yes | Current desktop environment confirms one surface | No | [Build skills](https://learn.chatgpt.com/docs/build-skills), 2026-07-22 | Build to the common package core; run surface-specific tests. |
| ChatGPT web reads local repository `.agents/skills`. | No; web uses plugins and does not read local Codex config | No | Yes / effectively unsupported by reviewed route | [Plugins](https://learn.chatgpt.com/docs/plugins) and [MCP](https://learn.chatgpt.com/docs/extend/mcp), 2026-07-22 | Web distribution is a later plugin task, not Session 17. |
| The `openai/skills` catalog remains the preferred distribution channel. | No; official README says deprecated | Deprecation commit observed | No | [`778b0e6…`](https://github.com/openai/skills/commit/778b0e6129cf18cbaee3bf11479f583fadae8d03), 2026-06-22; head inspected 2026-07-22 | Use repo-local authoring now and current plugins route for later distribution. |
| A package's GitHub visibility establishes reuse rights. | No | Individual `LICENSE.txt` convention observed in official catalog | No | [Pinned official README](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/README.md), accessed 2026-07-22 | Audit exact license, notices, code, and assets before adaptation. |
| Marketplace scanning eliminates the need for project security review. | No | Marketplace scan requirement documented | No | [Plugin submission skills guidance](https://learn.chatgpt.com/docs/build-plugins), accessed 2026-07-22 | Review every instruction, script, dependency, and provenance record locally. |

## 14. Source appendix

### A. Project sources

All project sources below were inspected at predecessor commit [`8fea4881e62498f1bce7498ff7a36e2af82de514`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/8fea4881e62498f1bce7498ff7a36e2af82de514) on 2026-07-22.

- [The Bible Video Game Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/8fea4881e62498f1bce7498ff7a36e2af82de514/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) — controlling project identity, authority, sacred-event rules, roles, chronology/knowledge separation, source treatment, schema-first production, and file discipline.
- [Session 1: Project Context and Repository Authority Map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/8fea4881e62498f1bce7498ff7a36e2af82de514/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md) — repository-state and authority audit; its original snapshot remains separately pinned inside the report.
- [Session 2: Terminology and Artifact Taxonomy](https://github.com/Degrading1919/The_Bible_Video_Game/blob/8fea4881e62498f1bce7498ff7a36e2af82de514/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md) — canonical terms, artifact classes, native/external distinctions, and separation between instructions, capabilities, knowledge, state, and evidence.

### B. Current official OpenAI/Codex documentation

These living sources were retrieved in the fresh Codex manual and accessed 2026-07-22. The manual supplied no page-level publication date or documentation commit SHA, so the access date is the currency marker.

- [Build skills](https://learn.chatgpt.com/docs/build-skills) — definition, availability, discovery context, invocation, creation, exact repository/user/admin/system storage, symlinks, distribution, installation, disabling, optional metadata, tool dependencies, and best practices.
- [Skills in Codex customization](https://learn.chatgpt.com/docs/customization#skills) — skill/`AGENTS.md` distinction, repository root, progressive disclosure, explicit/implicit invocation, scripts, MCP pairing, and recommended layering.
- [Custom instructions with `AGENTS.md`](https://learn.chatgpt.com/docs/agent-configuration/agents-md) — persistent guidance discovery, root-to-CWD merge, overrides, and size cap; used to distinguish repository instructions from skills.
- [Model Context Protocol](https://learn.chatgpt.com/docs/extend/mcp) — supported local clients, server features, local/project configuration, hosted-web distinction, authentication, and tools/resources/prompts.
- [Agent approvals & security](https://learn.chatgpt.com/docs/agent-approvals-security) — sandbox, approval, network, connector/MCP side-effect controls, and cloud/local differences.
- [Plugins](https://learn.chatgpt.com/docs/plugins) — supported surfaces, Work-mode/CLI installation, plugin contents, permissions, and the absence of plugin support in IDE/mobile/ordinary Chat mode.
- [Build plugins](https://learn.chatgpt.com/docs/build-plugins) — current packaging/distribution route, skill bundles, metadata, security review, and testing expectations.

### C. Specifications and official implementation artifacts

- [Agent Skills specification](https://agentskills.io/specification), living open specification accessed 2026-07-22 — portable package core, `SKILL.md`, frontmatter, and conventional resources. It is not evidence for every Codex-specific surface behavior.
- [`openai/skills` at `49f948faa9258a0c61caceaf225e179651397431`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431), commit dated 2026-06-24 — inspected official historical catalog snapshot. Its README records deprecation and per-skill licensing; its latest commit records between-turn catalog refresh guidance.
- [`openai/skills` deprecation commit `778b0e6129cf18cbaee3bf11479f583fadae8d03`](https://github.com/openai/skills/commit/778b0e6129cf18cbaee3bf11479f583fadae8d03), 2026-06-22 — moves current distribution guidance toward plugins.
- [Official `skill-creator/SKILL.md` at `49f948f…`](https://github.com/openai/skills/blob/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator/SKILL.md) — dated implementation evidence for required/optional package anatomy and context discipline. It is authoring guidance, not a substitute for current product documentation.
- [`openai/codex` issue #11314](https://github.com/openai/codex/issues/11314), opened 2026-02-10 — version-specific observation about symlink discovery and file-watcher refresh. It is explicitly not treated as a universal contract.

### Stable conclusion for downstream sessions

The capability sufficiently stable to encode is a repository-local Agent Skills package rooted at **`.agents/skills/the-bible-video-game-skill-builder/`**, with a concise `SKILL.md` containing required `name` and `description`, optional resources loaded only when needed, and no assumption that instructions confer permissions. Explicit/implicit invocation and `allow_implicit_invocation` are documented. Tool dependencies may be declared in `agents/openai.yaml`, but availability must be checked. Skill-to-skill precedence, composition ordering, and activation lifetime remain undocumented and must be governed explicitly and tested rather than assumed.

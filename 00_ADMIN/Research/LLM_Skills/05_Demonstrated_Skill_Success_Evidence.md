# Demonstrated Skill Success Evidence

**Session:** 05 of 18
**Research cutoff:** 2026-07-22
**Repository context:** `Degrading1919/The_Bible_Video_Game` at predecessor commit [`800de2b4a90d3fac81c5ece542a6f1273b50ec3d`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/800de2b4a90d3fac81c5ece542a6f1273b50ec3d)
**Scope:** Evidence that reusable LLM skills, or closely comparable reusable agent instructions and interfaces, improve software-engineering or adjacent task outcomes. This report does not create a project skill catalog, select the final project skill architecture, perform the Session 11 game-development ecosystem survey, or implement a skill.

## Executive finding

Reusable skills can improve agent performance, but the strongest available evidence does **not** support the broader claim that adding a skill is usually beneficial. The most substantial cross-domain controlled study found a large average gain from human-curated skills, while also finding regressions on 16 of 84 tasks, only a small average gain in its software-engineering domain, weaker results from large or comprehensive packages, and a negative average result from self-generated skills. A software-engineering-specific preprint found a much smaller average gain: most tested skills produced no pass-rate improvement, a minority of specialized skills helped materially, and several caused regressions. A peer-reviewed study of a comparable reusable agent-computer interface found a strong improvement, but it changed tools, feedback, and instructions together and therefore does not isolate text-only skill effects.

The defensible project conclusion is narrow:

- **Finding — Strong:** A concise, relevant, human-curated procedural package can improve performance under controlled conditions.
- **Finding — Strong:** Skill-task mismatch, stale version assumptions, excess context, and conflicting instructions can erase the benefit or make performance worse.
- **Finding — Strong:** Popularity, official origin, structural validity, repository inclusion, or an attractive `SKILL.md` is not evidence of outcome improvement.
- **Inference — Moderate:** The most transferable mechanism is not “more instructions.” It is relevant task guidance joined to executable checks, informative feedback, and a comparison against an unassisted baseline.
- **Recommendation:** Treat every proposed project skill as a testable intervention. Require an appropriate baseline, negative cases, version and scope checks, and project-constraint verification before adoption.

Evidence ratings in this report use exactly these meanings:

- **Strong:** Controlled comparison or reproducible evaluation directly measures an outcome, with enough methodological detail to evaluate the claim.
- **Moderate:** Primary artifacts or repeatable procedures substantiate feasibility or a mechanism, but do not cleanly isolate or measure the claimed outcome improvement.
- **Weak:** Limited, indirect, anecdotal, incompletely reported, or non-comparative evidence.
- **Promotional:** A vendor, author, or repository makes a benefit claim without an adequate controlled outcome comparison.
- **Speculative:** A plausible proposal or extrapolation for which the inspected evidence does not demonstrate the claimed effect.

These ratings describe the support for a claim, not the quality, popularity, or good faith of a source.

## 1. Search method and inclusion criteria

### 1.1 Research question

The operative question was: **What is the strongest primary evidence that a reusable LLM skill or comparable instruction package causes better task outcomes, rather than merely being available, popular, polished, or associated with a capable model?**

For each candidate case, the review attempted to identify:

1. the skill, instruction package, or comparable workflow;
2. the model, model version, agent harness, tools, and execution environment;
3. the task population;
4. the no-skill or alternative baseline;
5. the intervention;
6. the measured outcome and unit of analysis;
7. the degree of reproducibility;
8. observed failures or regressions;
9. causal confounders; and
10. likely transferability to this project.

### 1.2 Inclusion rules

Evidence was admitted when it met at least one of these conditions:

- a controlled skill/no-skill or interface ablation reported task outcomes;
- a benchmark supplied tasks, environments, deterministic or auditable verifiers, and enough procedure to attempt reproduction;
- a primary paper evaluated a comparable persistent instruction-and-tool workflow with a baseline;
- an actual public skill package, supporting script, evaluator, license, and repository state could be inspected to test whether a success claim was grounded in more than prose; or
- an official package established an operational authoring or evaluation mechanism, even if it did not establish performance benefit.

Priority was given to primary papers, official repositories, commit-pinned files, first-party documentation, explicit model identifiers, fixed environments, deterministic tests, repeated trials, and disclosed negative results. Evidence was downgraded when it depended on an LLM judge alone, omitted the baseline, mixed several interventions, lacked version information, had no inspectable task or verifier, or reported only selected successes.

### 1.3 Exclusion rules

The following were not treated as success evidence:

- stars, forks, downloads, social-media attention, or the number of skills in a collection;
- the existence of an official or bundled skill;
- structural validation that only proves files and frontmatter are well formed;
- examples generated by the skill author without an independent baseline;
- testimonials without task-level results;
- a single polished output without a comparable no-skill run;
- benchmark scores for a model when the skill contribution was not isolated; or
- search snippets or transient research-tool citation tokens.

### 1.4 Sources and inspected artifacts

The strongest controlled cases were [SkillsBench](https://arxiv.org/abs/2602.12670), [SWE-Skills-Bench](https://arxiv.org/abs/2603.15401), and the peer-reviewed [SWE-agent agent-computer interface study](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf). The following repositories and actual packages were also inspected at pinned revisions:

- [`benchflow-ai/skillsbench` at `5720102e…`](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7), including the Spring Boot migration task, four task-local skills, deterministic verifier, methodology, and pollution audit;
- [`GeniusHTX/SWE-Skills-Bench` at `95b3ce51…`](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1), including `python-resilience`, its task, tests, configuration, and comparison scripts;
- [`SWE-agent/SWE-agent` at `3ea751c0…`](https://github.com/SWE-agent/SWE-agent/tree/3ea751c087f32b16e039a2233dd6eefecef325d5), together with the conference paper and ACI documentation;
- [`openai/skills` at `49f948fa…`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431), including the official `skill-creator` workflow and validation scripts; and
- [`anthropics/skills` at `fa0fa64b…`](https://github.com/anthropics/skills/tree/fa0fa64bdc967915dc8399e803be67759e1e62b8), including its `skill-creator` workflow and evaluation runner.

Repository inspection demonstrates what the artifacts contain; it does not by itself demonstrate that they improve outcomes.

## 2. Strongest evidence cases

### 2.1 SkillsBench: broad controlled evidence for human-curated skills

**Evidence rating: Strong.** SkillsBench is the strongest inspected direct evidence because it compares no-skill and curated-skill conditions across many tasks, several agent/model configurations, repeated trials, containerized environments, and task-specific verifiers. It is a 2026 preprint rather than a completed independent replication, so “Strong” does not mean conclusive.

| Evaluation element | Reported design or result |
|---|---|
| Intervention | Human-curated task skills supplied to the agent. A separate condition used model-generated skills. |
| Models and harnesses | Claude Code 2.1.19 with Claude Opus 4.5, Opus 4.6, Sonnet 4.5, and Haiku 4.5; Codex with `openai/gpt-5.2-codex`; and Gemini CLI with Gemini 3 Pro and Flash preview models. The paper does not expose a comparable Codex harness version. |
| Environment | Dockerized Ubuntu 24.04 task environments with task-specific verifiers. |
| Task population | 84 included tasks across 11 domains; two accepted tasks were excluded for a GPU requirement and verifier timeout. |
| Baseline | Same task and agent/model configuration without the curated skill. |
| Repetition | Main no-skill and curated-skill conditions used five trials per task; self-generated-skill conditions used three trials where supported. The paper reports 7,308 trajectories. |
| Primary outcome | Mean pass rate increased from 24.3% without skills to 40.6% with curated skills, a reported gain of 16.2 percentage points. Every tested agent/model configuration improved on average, by 13.6 to 23.3 points. |
| Codex result | GPT-5.2-Codex increased from 30.6% to 44.7%, a 14.1-point gain. |
| Software-engineering result | The software-engineering domain increased from 34.4% to 38.9%, only 4.5 points—far smaller than the overall average. |
| Negative results | 16 of 84 tasks regressed. Reported examples include taxonomy-tree merge (-39.3 points), AC optimal power flow (-14.3), trend anomaly detection (-12.9), and exoplanet analysis (-11.4). |
| Skill-generation result | Self-generated skills averaged -1.3 points relative to no skill. Codex self-generation was 25.0% versus its 30.6% no-skill baseline, a -5.6-point result. |
| Size and count effects | One skill: +17.8 points; two or three: +18.6; four or more: +5.9. “Detailed” skills: +18.8; “compact”: +17.1; “standard”: +10.1; “comprehensive”: -2.9. These are observational subgroup results, not randomized size ablations. |
| Resource effect | For Codex, reported mean token use increased from about 974,000 to 1,099,000 and mean estimated cost from $1.85 to $2.07, about 12%. Usage accounting was incomplete for some Claude conditions. |

The evidence supports a causal claim at the level of **the benchmark’s curated-skill intervention**, not a universal claim about any individual skill. The consistent configuration-level gains make a pure single-model explanation unlikely. The task-level regressions, self-generation result, and weak software-engineering aggregate rule out “skills always help.”

The repository makes meaningful reproduction possible. At commit [`5720102e…`](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7), the `spring-boot-jakarta-migration` task contains an explicit task specification, four separate skills, and a deterministic Python verifier. The verifier checks removal of `javax` imports, presence of Jakarta APIs, Spring Security 6 patterns, RestClient use, dependency versions, Maven compilation, and tests. This is materially stronger than an author judging whether an answer “looks better.” The repository is licensed under [Apache License 2.0](https://github.com/benchflow-ai/skillsbench/blob/5720102e3d6b0d3471b9715995ff96144d9eefb7/LICENSE).

However, the current repository also publishes a [skill-pollution trial audit](https://github.com/benchflow-ai/skillsbench/blob/5720102e3d6b0d3471b9715995ff96144d9eefb7/docs/skills-research/skill-pollution-trial-summary.md). It documents 15 pre-fix “no-skill” trials in which skills were accidentally present in the image; three successful no-skill trials were clearly skill-assisted. The build was changed to stop baking skills into no-skill images. The audit is valuable transparency, but this review did not independently reconstruct whether every published aggregate uses only corrected trials. That question remains open rather than being silently assumed away.

**Supported finding:** Human-curated, task-relevant skills can produce substantial aggregate gains in a controlled multi-domain benchmark.

**Unsupported extension:** The benchmark does not show that any arbitrary repository skill will help this project, that more skills are better, that a generated skill is safe to trust, or that the reported 16.2-point average transfers to game development.

### 2.2 SWE-Skills-Bench: specialized SWE skills sometimes help, most do not

**Evidence rating: Strong, with a preliminary-results caveat.** This is the most directly relevant controlled SWE evidence inspected, but the paper explicitly identifies itself as a preprint with preliminary work-in-progress results. The benchmark is publicly inspectable and uses executable tests rather than an LLM judge.

| Evaluation element | Reported design or result |
|---|---|
| Intervention | One of 49 public software-engineering skills supplied for a task paired with an authentic GitHub repository pinned at a fixed commit. |
| Model and harness | Claude Code with Claude Haiku 4.5 in Docker, as reported by the paper. |
| Task population | Approximately 565 instances across six software-engineering subdomains. |
| Baseline | Paired execution with and without the assigned skill. |
| Verification | Acceptance criteria translated into deterministic execution tests; no LLM judge for the primary pass-rate comparison. |
| Primary result | Mean pass-rate improvement of 1.2 percentage points. |
| Distribution | 39 of 49 skills had zero pass-rate improvement. Seven specialized skills improved performance by as much as 30 points. Three skills degraded performance by as much as 10 points. |
| Resource effect | Mean token use increased 10.5%, with reported skill-level effects ranging from savings to about 451% more tokens without corresponding correctness improvement. |
| Reported regression mechanisms | Version mismatch, task-context conflict, and excess instruction/context. |

This evidence materially narrows the SkillsBench conclusion. It suggests that the expected value of a **random public SWE skill** is close to zero even when a minority of well-matched specialized skills deliver substantial gains. The result also demonstrates why average-only reporting is unsafe: a +1.2-point mean conceals both +30-point successes and -10-point failures.

The public repository at [`95b3ce51…`](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1) provides container and CLI procedures, paired `--use-skill` and `--no-use-skill` runs, pass-rate comparison, token analysis, and an [MIT license](https://github.com/GeniusHTX/SWE-Skills-Bench/blob/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1/LICENSE). The inspected [`python-resilience` skill](https://github.com/GeniusHTX/SWE-Skills-Bench/blob/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1/skills/python-resilience/SKILL.md), task, and test file illustrate both value and limitation. The package gives concrete retry, circuit-breaker, and failure-handling patterns, while parts of the tests rely on imports, names, numbers, and structural indicators rather than exhaustively proving runtime resilience. “Deterministic” therefore means repeatable—not necessarily complete or resistant to gaming.

The configuration also contains anomalies, including duplicated YAML keys and at least one incompletely pinned repository entry. These do not invalidate the reported study, but they lower confidence in frictionless third-party reproduction. Reproduction also requires the relevant proprietary model/API access and incurs cost.

**Supported finding:** Specialized, context-matched SWE skills can yield large improvements, while most inspected public skills do not improve pass rate and some make it worse.

**Unsupported extension:** A public skill’s detail, length, popularity, or generic applicability does not predict success on this project.

### 2.3 SWE-agent ACI: reusable instructions work best when joined to tools and feedback

**Evidence rating: Strong for the combined interface; not direct evidence for text-only skills.** The NeurIPS 2024 [SWE-agent paper](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf) evaluates an agent-computer interface (ACI) that packages persistent instructions, custom commands, demonstrations, constrained editing, search behavior, syntax feedback, and context management. In a 300-instance SWE-bench Lite ablation using GPT-4 Turbo, the SWE-agent ACI improved resolution rate by 10.7 percentage points relative to a baseline agent using the default Linux shell. The paper also reported transfer to Claude 3 Opus, which resolved 10.5% under the interface.

This case is adjacent rather than identical to a `SKILL.md`. The intervention changed multiple things at once:

- reusable system instructions and command documentation;
- a file viewer with bounded output;
- summarized search results;
- an edit operation that rejects syntax errors and returns feedback;
- explicit handling of empty output;
- demonstrations; and
- context-management behavior.

The current project’s [ACI documentation](https://swe-agent.com/0.7/background/aci/) explains these design choices, and the source remains inspectable at [`3ea751c0…`](https://github.com/SWE-agent/SWE-agent/tree/3ea751c087f32b16e039a2233dd6eefecef325d5) under the [MIT license](https://github.com/SWE-agent/SWE-agent/blob/3ea751c087f32b16e039a2233dd6eefecef325d5/LICENSE). The current repository notes that the implementation is in maintenance mode and points to a successor, so reproduction must use a pinned historic configuration rather than assume the current head matches the 2024 experiment.

**Supported finding:** A reusable, task-oriented instruction layer can improve SWE outcomes when it is coupled with constrained tools and immediate machine feedback.

**Causal limitation:** The ablation does not identify how much of the 10.7-point gain came from prose instructions, demonstrations, custom commands, syntax rejection, result summarization, or context management. It supports a combined workflow architecture, not a claim that a long prompt alone produces the same effect.

### 2.4 Cross-case interpretation

Across the three strongest cases, the direction is consistent but conditional:

1. Human-curated instructions can help.
2. Specialized relevance matters more than generic breadth.
3. Executable verification and informative feedback strengthen the workflow.
4. More content, more packages, and model-generated instructions are not reliable improvements.
5. Averages conceal meaningful regressions.
6. Version and environment fit are part of correctness, not maintenance trivia.

The studies do **not** establish a universal optimal format, word count, skill count, trigger description, or authoring process. Those remain variables for project-specific evaluation.

## 3. Moderate evidence cases

No additional case was promoted to “Strong” merely because it was official, maintained, or sophisticated. Two inspected packages provide **Moderate** evidence that rigorous skill evaluation is operationally feasible, but neither provides a controlled outcome result for the creator skill itself.

### 3.1 Official OpenAI `skill-creator`

At [`openai/skills` commit `49f948fa…`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431), the official [`skill-creator`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator) includes an initialization workflow, metadata generation, and structural validation scripts. These are inspectable, repeatable mechanisms for producing a conforming package. They substantiate the feasibility of initialization, concise authoring, metadata generation, and validation.

They do not demonstrate that a structurally valid skill improves a task. A validator can confirm required fields, directories, and naming while missing wrong technical advice, unsafe commands, project-authority conflicts, false triggers, stale assumptions, or regressions. The repository was also deprecated in June 2026 in favor of a plugin-based distribution path, making commit pinning important.

**Evidence rating: Moderate** for the feasibility of a repeatable authoring and structural-validation workflow.
**Evidence rating: Weak** for any claim that use of this creator, by itself, improves downstream task success.

### 3.2 Anthropic `skill-creator` evaluation workflow

The inspected Anthropic package at [`fa0fa64b…`](https://github.com/anthropics/skills/tree/fa0fa64bdc967915dc8399e803be67759e1e62b8/skills/skill-creator) goes beyond static structure. Its workflow describes drafting, testing multiple cases, comparing a skill-enabled run with a baseline, using graders and comparators, examining quantitative results, and testing trigger descriptions. The accompanying [`run_eval.py`](https://github.com/anthropics/skills/blob/fa0fa64bdc967915dc8399e803be67759e1e62b8/skills/skill-creator/scripts/run_eval.py) materializes command files and launches repeated CLI evaluations.

This is primary evidence that baseline comparison and repeated evaluation can be packaged into a reusable authoring process. It is not a published comparison showing that skills produced by the creator are more successful than skills produced without it. Parts of the workflow are also platform-specific, invoke external model execution, and rely on grader behavior that must itself be validated.

**Evidence rating: Moderate** for the feasibility of systematic skill-versus-baseline evaluation.
**Evidence rating: Weak** for a causal downstream performance claim about the creator.

### 3.3 What the moderate cases add

The moderate cases show that the project need not invent its evaluation mechanics from nothing. Initialization, metadata checks, clean-context runs, repeated trials, baseline comparison, trigger testing, and result inspection all have concrete implementations. They do not justify copying either creator wholesale or treating its design choices as project authority. Session 17 remains governed by this project’s resolved Codex skill root and the required OpenAI `skill-creator` workflow, while Session 15 must define the project’s acceptance scenarios and thresholds.

## 4. Weak, promotional, speculative, and overstated evidence

### 4.1 Weak evidence

The following can be useful discovery signals but are **Weak** evidence of success:

- an official skill appears in a maintained repository;
- a package contains detailed examples and scripts;
- a skill produces one compelling demonstration;
- an evaluator reports only selected passing cases;
- a benchmark has deterministic tests but omits coverage analysis;
- a case reports a before/after result without repeated trials or a matched baseline;
- users report that a skill “feels more reliable”; or
- a package’s trigger or description appears precise.

These observations may justify testing. They do not justify adoption.

### 4.2 Promotional evidence

Claims such as “turn expertise into reusable capabilities,” “dramatically improve agents,” or “production-ready best practices” are **Promotional** when the source supplies no controlled comparison, task distribution, failure count, cost measurement, or reproduction path. Vendor provenance may increase confidence that a package matches a platform’s intended format; it does not establish outcome effect.

Repository popularity is also promotional at best as a success proxy. Stars combine awareness, branding, novelty, and collection value. They do not measure whether a particular skill was triggered correctly, followed accurately, or improved a task.

### 4.3 Speculative evidence

The following propositions are **Speculative** on the inspected record:

- that generating a skill from a successful trajectory will preserve the cause of success;
- that adding all apparently relevant skills will produce cumulative gains;
- that a comprehensive skill is safer because it covers more edge cases;
- that an instruction useful for web or enterprise SWE transfers unchanged to an historically grounded biblical game project;
- that an LLM can reliably select the correct skill from a large catalog without routing evaluation;
- that a high-quality generic game-development skill can enforce sacred-event boundaries; or
- that a skill passing structural validation is ready for clean-context use.

SkillsBench directly warns against the first three: self-generated skills averaged below baseline, four-or-more skills helped much less than one-to-three, and the “comprehensive” subgroup regressed on average.

### 4.4 Common overstatements corrected

| Overstated claim | Evidence-grounded correction |
|---|---|
| “Skills improve agent performance by 16.2 points.” | Human-curated skills improved the SkillsBench average by 16.2 points in its tested conditions. Sixteen tasks regressed, SWE gained only 4.5 points, and another SWE benchmark reported only +1.2 points. |
| “Skills work across models.” | Average gains occurred across seven tested configurations in SkillsBench. This does not establish transfer to future models, other harnesses, GUI workflows, multi-agent systems, or this repository. |
| “The model can write the skill it needs.” | SkillsBench’s self-generated condition averaged -1.3 points; Codex self-generation was -5.6 points relative to its no-skill baseline. |
| “Longer and more complete is better.” | SkillsBench reported a negative average for comprehensive skills and reduced gains with four or more skills. The result is correlational by subgroup, but it contradicts the blanket claim. |
| “Executable tests prove the skill works.” | Tests prove only what they cover. The inspected SWE-Skills-Bench example includes structural indicators that do not exhaustively prove runtime resilience. |
| “Official means proven.” | Official creator packages demonstrate supported structures and workflows, not task-level causal improvement. |

## 5. Causal-confounder analysis

| Confounder | Why it matters | Evidence in inspected cases | Required control or disclosure |
|---|---|---|---|
| Model capability | A stronger model may benefit more, need less guidance, or mask a weak skill. | SkillsBench reports materially different baselines and gains by configuration. | Pin model and harness versions; compare within the same configuration. |
| Tool and interface changes | A combined intervention may improve results because of safer editing or feedback, not prose. | SWE-agent ACI changed instructions, tools, syntax checks, and context management together. | Label the intervention as combined; use component ablations before attributing gains to text. |
| Extra context or tokens | A skill condition may simply receive more useful tokens—or may be harmed by context pressure. | SkillsBench and SWE-Skills-Bench report token increases; SkillsBench lacks length-matched irrelevant-context controls. | Measure tokens, cost, and latency; add relevant-versus-irrelevant or length-matched controls when causal precision matters. |
| Task selection | Curated tasks may favor codifiable procedures and omit long-horizon or interactive work. | SkillsBench is terminal/container-based and excludes GUI, multi-agent, and long-horizon settings. | State the sampled task population; do not extrapolate beyond it without new tests. |
| Skill-task selection | Authors may pair a skill only with tasks it was designed to solve. | Both direct benchmarks use task-linked skills. | Include near-miss, irrelevant-trigger, and adversarial mismatch scenarios. |
| Verifier coverage | A deterministic verifier can reward shallow structural compliance. | The inspected `python-resilience` tests include name, number, and keyword checks. | Review tests against the intended behavior; combine static, runtime, visual, and human checks as appropriate. |
| Training contamination | Public tasks, repositories, or skills may be present in model training data. | Neither benchmark can fully rule this out. | Pin artifacts, prefer newly constructed holdouts where possible, and disclose the limitation. |
| Stochasticity | One run can be a lucky pass or unlucky failure. | SkillsBench uses repeated trials; some public reproduction workflows default to smaller samples. | Require repeated clean-context runs for unstable tasks and report counts, not only best runs. |
| Version mismatch | Correct guidance for one library or engine version can be harmful for another. | SWE-Skills-Bench reports regressions from version mismatch. | Require explicit applicability/version metadata and a mismatch refusal path. |
| Instruction conflict | A skill can override or distract from task or project authority. | Both benchmarks report task-specific regressions; neither encodes this project’s sacred constraints. | Test precedence, never-suppress rules, and conflicting-instruction scenarios. |
| Researcher involvement | Human curation can contain unreported tuning or domain expertise. | SkillsBench contrasts curated and self-generated skills, but curation effort is part of the intervention. | Report authoring process and iteration count; distinguish final benchmark from development set. |
| Multiple comparisons | Highlighting the best seven skills can overstate expected benefit. | SWE-Skills-Bench has a small positive mean with a wide skill distribution. | Report all skills, failures, and distribution—not only peak gain. |
| Usage accounting | Token and cost comparisons can be incomplete or vendor-specific. | SkillsBench notes incomplete Claude usage; provider pricing and cache behavior vary. | Record raw tokens, wall time, retries, and cost assumptions separately. |
| Benchmark contamination | A no-skill image may accidentally contain the skill. | SkillsBench’s public pollution audit found 15 affected pre-fix trials. | Verify clean images and runtime mounts; preserve audit logs; rerun affected comparisons. |
| Publication maturity | A preprint may change after review or correction. | Both 2026 direct skill benchmarks are preprints; SWE-Skills-Bench calls its results preliminary. | Pin paper version and repository SHA; treat later replications as required updates. |
| License and provenance | A technically effective package may not be reusable legally or may embed unattributed material. | Root licenses differ; some packages include copied or secondary-source patterns. | Inspect each package and supporting file, not only the root repository license, before reuse. |

### 5.1 What can be claimed causally

The direct benchmarks can support within-study claims because the skill condition is compared with a no-skill condition under substantially matched task and agent settings. They cannot establish that the skill text alone is the causal mechanism when supporting files, examples, environment mounts, or routing behavior also change. SWE-agent supports the combined ACI, not a text-only component.

The most defensible causal unit is therefore **the full evaluated intervention**: the pinned skill package, its supporting resources, the harness behavior that exposes it, the task environment, and the verifier. Removing any one of those qualifiers overstates the evidence.

### 5.2 Contradictory evidence is part of the result

The apparent conflict between SkillsBench’s +16.2-point overall result and SWE-Skills-Bench’s +1.2-point result is not resolved by choosing the larger number. The sampled domains, models, tasks, public-skill selection, authoring quality, and evaluators differ. Together they show that effect size is highly distribution-dependent. This is a reason for project-specific evaluation, not a reason to average the two studies.

## 6. Transferability to The Bible Video Game

### 6.1 Project constraints that alter transfer

This repository is not presently an ordinary application-code benchmark. Session 1 found no authoritative engine selection, production implementation stack, gameplay code, executable schema, build system, or test harness at the pinned predecessor. The controlling [Master Assistant Protocol](https://github.com/Degrading1919/The_Bible_Video_Game/blob/800de2b4a90d3fac81c5ece542a6f1273b50ec3d/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md) requires the witness premise, protected sacred events, historical honesty, a separation among fact/interpretation/reconstruction/invention, in-world versus player-codex knowledge boundaries, and schema-first discipline.

Consequently, a skill can be technically effective and still be unacceptable. A code-oriented skill that increases test pass rate but invents an engine, rewrites controlling design authority, flattens historical uncertainty, exposes later revelation to an earlier character, or treats sacred events as sandbox mechanics has failed the project.

### 6.2 Transferability matrix

| Evidence-backed practice | Transferability | Project-specific application | Principal risk |
|---|---|---|---|
| Compare skill-enabled runs with a no-skill baseline | High | Evaluate the Session 17 builder and later candidate skills against identical clean-context tasks. | A weak baseline can exaggerate gains. |
| Prefer focused, task-relevant packages | High | Keep a skill’s purpose narrow and route only when its trigger and prerequisites match. | Over-fragmentation can create routing and composition burden. |
| Use multiple representative scenarios | High | Include success, near-miss, conflicting-authority, missing-input, and historical-uncertainty cases. | Scenario authors can unconsciously teach to the test. |
| Use executable or inspectable verification | High | Validate structure, links, files, schemas when present, and required constraint labels. | Machine checks cannot fully judge reverence, theology, or emotional impact. |
| Report regressions and cost | High | Preserve failed cases, token/latency changes, and false-trigger rates. | Selective reporting would recreate promotional evidence. |
| Couple instructions to feedback | High | Give the agent authoritative file paths, validators, and clear failure messages. | Tool outputs can be mistaken for project authority. |
| Reuse public game/SWE skills directly | Low at current phase | No direct reuse until stack, license, scope, and project-authority fit are known. | Stale stack assumptions and imported design values. |
| Generate a skill automatically from one successful run | Low | Treat generation as a draft only; require human review and controlled evaluation. | SkillsBench found negative average self-generated results. |
| Add several “helpful” skills together | Low without composition tests | Test combinations separately under the future governance model. | Instruction conflict and context dilution. |
| Use one aggregate benchmark score as approval | Low | Require scenario-level floors and zero-tolerance project-constraint failures. | Averages can hide sacred-boundary or authority violations. |

### 6.3 Recommended project evidence standard

Before a future skill is called successful, the project should require:

1. a pinned skill package and declared dependencies;
2. a matched no-skill or current-workflow baseline;
3. clean-context evaluation on more than one representative task;
4. explicit success criteria defined before examining results;
5. task-level results, including regressions and false triggers;
6. token, latency, and tool-use accounting where material;
7. verification of project authority, sacred-event protection, historical uncertainty, knowledge boundaries, and schema-first behavior;
8. version-mismatch and missing-input behavior;
9. license and provenance review for every reused file; and
10. a reuse decision that can be reversed when the repository or model changes.

This is a recommendation derived from the evidence, not a final benchmark specification. Session 15 is responsible for the full framework and required scenarios.

## 7. Positive evidence ledger

| Claim or practice | Evidence source | Evidence type | Strength | Transferability | Risks/caveats |
|---|---|---|---|---|---|
| Human-curated task skills can improve aggregate agent task success. | [SkillsBench paper](https://arxiv.org/abs/2602.12670) | Controlled, repeated, multi-configuration benchmark | Strong | Moderate to high for the practice of evaluating curated skills | Preprint; terminal tasks; 16 task regressions; effect size is distribution-specific. |
| Curated skills improved all seven tested agent/model configurations on average. | [SkillsBench paper](https://arxiv.org/abs/2602.12670) | Within-study configuration comparison | Strong | Moderate | Does not include every model, future versions, GUI work, or this project’s constraints. |
| Codex GPT-5.2-Codex improved 14.1 points in SkillsBench’s curated condition. | [SkillsBench paper](https://arxiv.org/abs/2602.12670) | Controlled model-specific comparison | Strong | Moderate | Codex harness version is not equally explicit; current Codex behavior may differ. |
| Specialized SWE skills can produce large gains when tightly matched. | [SWE-Skills-Bench paper](https://arxiv.org/abs/2603.15401) | Paired executable-test benchmark | Strong | Moderate | Preliminary preprint; only 7 of 49 improved, with up to +30 points. |
| A reusable instruction-and-tool interface with fast feedback can improve issue resolution. | [SWE-agent NeurIPS paper](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf) | Peer-reviewed controlled ACI ablation | Strong | High for combined workflow principles | Does not isolate text instructions from tool, feedback, and context changes. |
| Deterministic task verifiers make skill claims more auditable than impressionistic judging. | [SkillsBench repository](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7) and [SWE-Skills-Bench repository](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1) | Inspectable benchmark artifacts | Moderate | High | Deterministic tests can still be incomplete or reward superficial compliance. |
| Repeated trials expose stochastic variance better than a single showcase. | [SkillsBench paper](https://arxiv.org/abs/2602.12670) | Five-trial main conditions with bootstrap intervals | Strong | High | Five trials do not eliminate all variance; project tasks may be more subjective. |
| Public audit logs can reveal evaluation contamination and support correction. | [SkillsBench pollution audit](https://github.com/benchflow-ai/skillsbench/blob/5720102e3d6b0d3471b9715995ff96144d9eefb7/docs/skills-research/skill-pollution-trial-summary.md) | Primary incident/audit record | Moderate | High | This review did not independently reconstruct the published aggregate after the fix. |
| Baseline comparison, trigger testing, and repeated evaluation can be packaged as an authoring workflow. | [Anthropic skill-creator](https://github.com/anthropics/skills/tree/fa0fa64bdc967915dc8399e803be67759e1e62b8/skills/skill-creator) | Inspectable workflow and script | Moderate | Moderate | No controlled evidence that the creator itself improves downstream performance; platform-specific execution. |
| Initialization, metadata generation, and structural checks can be automated. | [OpenAI skill-creator](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator) | Official inspectable scripts | Moderate | High for Session 17 procedure | Structural success is not semantic, safety, or project-fit success; repository distribution is deprecated. |
| Reporting both pass rate and resource use prevents hidden efficiency regressions. | [SkillsBench paper](https://arxiv.org/abs/2602.12670) and [SWE-Skills-Bench paper](https://arxiv.org/abs/2603.15401) | Controlled benchmark cost/token analysis | Strong | High | Provider accounting differs; some SkillsBench usage data were incomplete. |
| Pinning task repositories and package revisions makes later claims auditable. | [SWE-Skills-Bench repository](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1) | Reproducibility design | Moderate | High | Some inspected configuration anomalies show that pinning must itself be validated. |

## 8. Preliminary existing-skill audit

This is an evidence audit of the small set of packages actually inspected for this session. It is **not** a project skill catalog or the broader game-development landscape review reserved for Session 11. “Reuse decision” uses only the allowed decision labels and applies to this project at its current repository state.

| Repository | Skill | Platform | Intended purpose | Evidence of real use | Quality assessment | Safety concerns | License | Reuse decision |
|---|---|---|---|---|---|---|---|---|
| [`benchflow-ai/skillsbench` `5720102e…`](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7) | [`spring-boot-migration`, `jakarta-namespace`, `hibernate-upgrade`, and `spring-security-6`](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7/tasks/spring-boot-jakarta-migration/environment/skills) | Cross-agent benchmark task package | Guide a Java 8/Spring Boot 2.7 application migration to Java 21/Spring Boot 3.2 and related APIs. | Included in a controlled benchmark with an explicit task and executable verifier; no individual-skill causal result is isolated. | Focused and concrete; four packages align with verifier categories. Some advice relies on secondary sources and exact library-era assumptions. | Shell/search/edit advice can make broad mechanical changes; stale dependency guidance could break a repository; stack is unrelated to the current project. | Apache-2.0 at repository root; file-level provenance still requires review before extraction. | Extract principles only |
| [`GeniusHTX/SWE-Skills-Bench` `95b3ce51…`](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1) | [`python-resilience`](https://github.com/GeniusHTX/SWE-Skills-Bench/blob/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1/skills/python-resilience/SKILL.md) | Claude Code benchmark package | Add retry, circuit-breaker, error-handling, and resilience patterns to Python code. | Paired benchmark infrastructure exists, but the inspected public artifacts do not establish a positive per-skill result for this package. | Detailed and actionable, but broad; its test emphasizes some structural indicators and cannot prove all runtime properties. | Can encourage unnecessary dependencies or abstraction; version/context mismatch; no known Python production stack in this project. | MIT at repository root; upstream provenance of embedded patterns must be checked before reuse. | Reject |
| [`SWE-agent/SWE-agent` `3ea751c0…`](https://github.com/SWE-agent/SWE-agent/tree/3ea751c087f32b16e039a2233dd6eefecef325d5) | SWE-agent ACI/default workflow (comparable artifact, not a `SKILL.md`) | SWE-agent | Provide persistent operating instructions, custom file/search/edit tools, demonstrations, feedback, and context management for repository issue resolution. | Peer-reviewed controlled ablation reports +10.7 percentage points on a 300-instance SWE-bench Lite subset. | Strong combined workflow design with direct feedback and constrained views; current repository is maintenance-only and not identical to the historic evaluation configuration. | Automated edits and shell tools remain powerful; issue-resolution priorities do not encode project theology, historical honesty, or sacred boundaries. | MIT | Extract principles only |
| [`openai/skills` `49f948fa…`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431) | [`skill-creator`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator) | Codex | Initialize, author, generate metadata for, and structurally validate a Codex skill package. | Official distributed workflow and scripts; no public controlled performance comparison located for the creator itself. | Clear staged workflow and useful automation; validation is primarily structural and cannot establish semantic effectiveness. The repository has been deprecated in favor of plugins. | Generated scripts and references still require inspection; a valid package may conflict with authority or trigger incorrectly. | Per-package licensing governs; no direct reuse is proposed without a separate file-level license check. | Adapt |
| [`anthropics/skills` `fa0fa64b…`](https://github.com/anthropics/skills/tree/fa0fa64bdc967915dc8399e803be67759e1e62b8) | [`skill-creator`](https://github.com/anthropics/skills/tree/fa0fa64bdc967915dc8399e803be67759e1e62b8/skills/skill-creator) | Claude Code / Claude skill workflow | Draft a skill, evaluate multiple cases against a baseline, inspect results, and tune trigger behavior. | Public workflow and executable evaluation runner; no controlled evidence located that use of the creator improves skills versus another authoring method. | Strong evaluation concepts and inspectable automation, but lengthy and platform-specific. | Launches model subprocesses, creates command material, and can incur external cost; grader reliability and data handling require review. | Repository/package license must be verified at the exact reused file before extraction; no direct file reuse is proposed. | Extract principles only |

### 8.1 Audit interpretation

Only the OpenAI creator is marked **Adapt**, because Session 17 is explicitly required to use that official workflow and because the project must add its own authority, safety, evidence, and forward-test gates. This is a workflow decision, not a claim that the package has demonstrated performance benefit. The Java and SWE-agent artifacts offer transferable mechanisms but not project-ready content. `python-resilience` is rejected for this project’s current state because no Python production stack is established and its broad abstraction guidance would import both technical and scope assumptions.

No package is adopted as-is. No audited row constitutes a final catalog entry.

## 9. Research gaps and deferred questions

The following gaps remain deliberately unresolved rather than being filled with inference:

1. **Independent replication:** No independent reproduction of the two 2026 direct skill benchmarks was located in the bounded source set.
2. **Published-result contamination audit:** SkillsBench documents pre-fix skill pollution, but this review did not independently reconstruct which trajectories fed every published table after correction.
3. **Codex harness details:** SkillsBench identifies GPT-5.2-Codex but does not expose a Codex harness version with the same precision as Claude Code 2.1.19.
4. **Current-model transfer:** The evaluated model versions will age. No evidence establishes that the same effect sizes hold for later Codex, Claude, or Gemini releases.
5. **Game-development tasks:** The strongest studies do not evaluate engine editors, scene graphs, gameplay feel, visual defects, frame performance, build packaging, or human play verification.
6. **Long-horizon and multi-agent work:** SkillsBench explicitly centers terminal/container tasks. Transfer to sequential subagents, persistent project memory, or multi-session governance is untested.
7. **Sacred and historical constraints:** No public benchmark measures witness-premise preservation, sacred-event protection, responsible uncertainty labels, biblical chronology, or in-world/codex knowledge separation.
8. **Routing and false triggers:** The direct benchmarks primarily mount task-relevant skills. They do not fully measure discovery within a large catalog, accidental invocation, or near-miss routing.
9. **Composition effects:** SkillsBench reports weaker performance with four or more skills, but no controlled project-like composition study resolves precedence, conflict, or cumulative context effects.
10. **Verifier validity:** Public deterministic tests are inspectable, but their correlation with maintainability, user experience, theological seriousness, and human judgment is not established.
11. **Authoring effort:** The cost of researching, writing, maintaining, and retesting curated skills is not consistently included in return-on-investment calculations.
12. **License granularity:** Before any external file is reused, each skill, script, embedded example, and referenced source needs exact license and provenance confirmation; root repository licenses are not always sufficient.
13. **Individual package effects:** Aggregate benchmark results do not isolate the contribution of every audited skill, including the Spring Boot subskills and `python-resilience`.
14. **Official creator effectiveness:** The OpenAI and Anthropic creator workflows are operational artifacts, but no matched study demonstrates that they produce more effective skills than expert manual authoring.
15. **Clean-context forward-test threshold:** The number of trials and acceptance threshold appropriate for Session 17 remains a Session 15/16 requirement, not a conclusion of this evidence review.

### 9.1 Deferred decisions

This session does not decide:

- the final project skill catalog;
- which game-development skills should be adopted;
- the final role-to-skill architecture;
- skill precedence and composition governance;
- benchmark thresholds;
- the final builder requirements; or
- any production engine, language, schema, gameplay, or toolchain choice.

Those decisions depend on later sessions and on repository facts that do not yet exist.

## 10. Source appendix: dates, versions, and permanent links

### 10.1 Project authority and predecessor reports

- Degrading1919, [The Bible Video Game repository at Session 5 predecessor `800de2b4a90d3fac81c5ece542a6f1273b50ec3d`](https://github.com/Degrading1919/The_Bible_Video_Game/tree/800de2b4a90d3fac81c5ece542a6f1273b50ec3d), accessed 2026-07-22.
- [Master Assistant Protocol at the predecessor commit](https://github.com/Degrading1919/The_Bible_Video_Game/blob/800de2b4a90d3fac81c5ece542a6f1273b50ec3d/00_ADMIN/Reference/The_Bible_Video_Game_Master_Assistant_Protocol.md), accessed 2026-07-22.
- [Session 1 project context and authority map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/800de2b4a90d3fac81c5ece542a6f1273b50ec3d/00_ADMIN/Research/LLM_Skills/01_Project_Context_and_Authority_Map.md), [Session 2 terminology and taxonomy](https://github.com/Degrading1919/The_Bible_Video_Game/blob/800de2b4a90d3fac81c5ece542a6f1273b50ec3d/00_ADMIN/Research/LLM_Skills/02_Terminology_and_Artifact_Taxonomy.md), [Session 3 Codex capability map](https://github.com/Degrading1919/The_Bible_Video_Game/blob/800de2b4a90d3fac81c5ece542a6f1273b50ec3d/00_ADMIN/Research/LLM_Skills/03_Current_Codex_Skill_Capability_Map.md), and [Session 4 authoring principles](https://github.com/Degrading1919/The_Bible_Video_Game/blob/800de2b4a90d3fac81c5ece542a6f1273b50ec3d/00_ADMIN/Research/LLM_Skills/04_Effective_Skill_Anatomy_and_Authoring_Principles.md), all pinned to the Session 5 predecessor and accessed 2026-07-22.

### 10.2 Controlled skill studies

- BenchFlow AI et al., [“SkillsBench: Benchmarking How Well Agent Skills Work Across Diverse Tasks”](https://arxiv.org/abs/2602.12670), arXiv:2602.12670, submitted 2026-02-13; [project PDF](https://www.skillsbench.ai/skillsbench.pdf), accessed 2026-07-22.
- BenchFlow AI, [`skillsbench` repository at `5720102e3d6b0d3471b9715995ff96144d9eefb7`](https://github.com/benchflow-ai/skillsbench/tree/5720102e3d6b0d3471b9715995ff96144d9eefb7), commit dated 2026-07-18; Apache-2.0; accessed 2026-07-22.
- BenchFlow AI, [skill-pollution trial summary at the pinned revision](https://github.com/benchflow-ai/skillsbench/blob/5720102e3d6b0d3471b9715995ff96144d9eefb7/docs/skills-research/skill-pollution-trial-summary.md), accessed 2026-07-22.
- GeniusHTX et al., [“SWE-Skills-Bench: Do Agent Skills Actually Help in Real-World Software Engineering?”](https://arxiv.org/abs/2603.15401), arXiv:2603.15401v1, submitted 2026-03-16; explicitly preliminary/work in progress; accessed 2026-07-22.
- GeniusHTX, [`SWE-Skills-Bench` repository at `95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1`](https://github.com/GeniusHTX/SWE-Skills-Bench/tree/95b3ce519fcb58d0b19e90a5b6e5165211dc6dd1), commit dated 2026-04-14; MIT; accessed 2026-07-22.

### 10.3 Comparable SWE workflow evidence

- Yang et al., [“SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering”](https://papers.nips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf), Advances in Neural Information Processing Systems 37, 2024; accessed 2026-07-22.
- SWE-agent, [agent-computer interface documentation](https://swe-agent.com/0.7/background/aci/), documentation version 0.7 route; accessed 2026-07-22.
- SWE-agent, [`SWE-agent` repository at `3ea751c087f32b16e039a2233dd6eefecef325d5`](https://github.com/SWE-agent/SWE-agent/tree/3ea751c087f32b16e039a2233dd6eefecef325d5), commit dated 2026-07-16; MIT; accessed 2026-07-22.

### 10.4 Inspected authoring and evaluation packages

- OpenAI, [`openai/skills` at `49f948faa9258a0c61caceaf225e179651397431`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431), commit dated 2026-06-24; repository deprecated in favor of plugins after a June 2026 transition; [`skill-creator` package](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.system/skill-creator); accessed 2026-07-22. Licensing must be checked at the package/file level before reuse.
- Anthropic, [`anthropics/skills` at `fa0fa64bdc967915dc8399e803be67759e1e62b8`](https://github.com/anthropics/skills/tree/fa0fa64bdc967915dc8399e803be67759e1e62b8), commit dated 2026-07-17; [`skill-creator` package](https://github.com/anthropics/skills/tree/fa0fa64bdc967915dc8399e803be67759e1e62b8/skills/skill-creator); accessed 2026-07-22. Licensing must be checked at the exact reused-file level before extraction.

### 10.5 Stable conclusion for downstream sessions

The evidence threshold for this project should be higher than “the skill exists” and lower than “the skill must be universally proven.” A candidate may proceed when its intervention is pinned, relevant, licensed, measured against a baseline, tested for regressions and false triggers, and verified against this project’s controlling constraints. The burden remains on the skill to demonstrate a net benefit in the context where it will actually run.

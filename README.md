# Awesome AI Game Dev [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> An evidence-backed map of AI systems for building, testing, and evaluating games in 2026.

This repository grew out of my work as a co-author of GameCraft-Bench and my
effort to systematically understand the 2026 AI game-development frontier. I
apply the same evidence criteria and caveats to GameCraft-Bench as to every
other entry.

## Contents

- [2026 Frontier Snapshot](#2026-frontier-snapshot)
- [Curated Landscape](#curated-landscape)
- [Adjacent Signals](#adjacent-signals)
- [Evidence Guide](#evidence-guide)

## 2026 Frontier Snapshot

| Observation                           | Evidence                                                                                                                                 | Boundary                                                                      |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Runtime and visual feedback matter    | [GameDevBench v2](https://arxiv.org/abs/2602.11103): GPT-5.4 pass@1 rises from 41.1% to 52.0% with screenshot and runtime-video feedback | Localized Godot edits under the Codex harness                                 |
| Runnable is not playable or complete  | [GameCraft-Bench](https://arxiv.org/abs/2606.17861): best completed configuration reaches a 41.46% overall benchmark score               | End-to-end Godot tasks; harness-, demonstration-, and judge-specific          |
| Field reports are earlier but noisier | [Fable C&C iOS/iPadOS case](#practitioner-field-reports): public engineering artifact without a standardized benchmark                   | Exact Fable version unspecified; human-directed extension of an existing port |

## Curated Landscape

We organize each work by its primary role in the game-development loop.

**Build and Edit** covers existing-project modification and complete game
generation. **Verify and Improve** covers runtime validation, playtesting, bug
detection, balancing, and repair. **Specialized Production** covers bounded
workflows such as UI, cutscenes, and assets. **Adjacent Signals** covers engine
products, industry evidence, practitioner reports, and interactive world models
that influence game development without directly producing complete editable
games.

Benchmarks, systems, engines, and evidence grades are metadata rather than
competing classification axes. Each item appears under its primary contribution.

### Build and Edit Games

#### Existing-Project Editing

- [GameDevBench v2](https://github.com/waynchi/gamedevbench) - Evaluates 333 localized Godot tasks with deterministic engine tests and optional visual feedback. Evidence A; it edits existing projects rather than generating complete games.
- [PlayEval / PlayCoder](https://github.com/Tencent/PlayCoder) - Combines compile and execution checks with interaction-based Play@3 evaluation across 43 multilingual GUI applications, including games. Evidence A; it is not game-only and focuses on repository modification. ([Paper](https://arxiv.org/abs/2604.19742))

#### End-to-End Generation

- [GameCraft-Bench](https://github.com/FreedomIntelligence/gamecraft-bench) - Evaluates 140 prompt-to-complete-game Godot tasks using editable projects and replayable demonstrations. Evidence A; results are harness-, demonstration-, and judge-specific. ([Project](https://tongxuluo.github.io/gamecraft-bench-website/))
- [OpenGame / OpenGame-Bench](https://arxiv.org/abs/2604.18394) - Evaluates end-to-end Phaser 3 web-game generation on 150 prompts using Build Health, Visual Usability, and Intent Alignment. Evidence C; the public agent repository is available, but the benchmark evaluation pipeline is still marked "will be released soon." ([Code](https://github.com/leigest519/OpenGame))
- [WebGameBench](https://arxiv.org/abs/2605.17637) - Tests 12 coding agents on 111 browser-game tasks with a real runtime evaluator. Evidence C; public evaluation code was not independently verified as of 2026-07-14.
- [JAMER / JamBench](https://arxiv.org/abs/2606.19830) - Builds JamSet from 8,133 verified Godot projects and evaluates theme-driven generation plus multi-granularity completion on the 300-project JamBench. Evidence C; the paper states that code and data are public but provides no verifiable release URL, so reproducibility was not independently confirmed.
- [CreativeGame](https://arxiv.org/abs/2604.19926) - Treats HTML5 game creation as evolving lineages with mechanic plans and version ancestry. Evidence C; it emphasizes qualitative iteration rather than a strong aggregate benchmark.
- [WorldCoder-Bench](https://arxiv.org/abs/2606.01869) - Uses hidden, mutation-hardened contracts over runtime states and transitions to evaluate 2,026 expert-curated Three.js world-synthesis tasks. Evidence C; a currently accessible public benchmark implementation was not independently verified.

#### Engine-Native Development

- [AutoUE](https://arxiv.org/abs/2603.07106) - Connects asset retrieval, procedural scene construction, C++ gameplay implementation, and MCP-based testing in editable Unreal Engine projects. Evidence C; results use a small self-built benchmark and substantial model judgment.

### Verify and Improve Games

#### Runtime and Mechanics Verification

- [MAGE](https://arxiv.org/abs/2605.07342) - Evaluates 858 LLM-generated Unity scenes across 26 mechanic concepts, comparing direct C# generation with structured intermediate representations. Evidence C; runtime success and mechanic fidelity diverge, and the concept set is limited.
- [GameGen-Verifier / VeriGame](https://arxiv.org/abs/2605.07442) - Decomposes requirements, injects target runtime states, performs bounded interactions, and verifies mechanics in parallel. Evidence C; it does not measure holistic pacing, polish, or fun.

#### Playtesting and Bug Detection

- [PlaytestArena / Play2Code](https://continual-game-generation.vercel.app/) - Places a GUI playtesting agent in a generation-repair loop across 200 browser-game tasks. Evidence C; diagnosis remains bounded by the states the player agent can reach. ([Paper](https://arxiv.org/abs/2605.28258))
- [GBQA](https://arxiv.org/abs/2604.02648) - Evaluates agents on 124 human-verified implanted bugs across 30 lightweight web games. Evidence C; the best reported system finds fewer than half of the bugs.
- [CA2](https://arxiv.org/abs/2605.13918) - Uses code-level observations and offline reinforcement learning to reach target functions in Crafter and a Godot environment. Evidence C; it depends on source profiling and offline human trajectories.

#### Balancing and Exploit Discovery

- [RuleSmith](https://github.com/Adonis-galaxy/RuleSmith) - Combines LLM self-play with Bayesian optimization to search game-rule parameters. Evidence C; balance found for one simulated-player population may not transfer to other players. ([Paper](https://arxiv.org/abs/2602.06232))
- [RAID](https://arxiv.org/abs/2607.07498) - Uses iterative reinforcement-learning populations to discover exploit strategies in a pre-release NHL 26 scenario. Evidence C; the evidence comes from one proprietary game and still requires human interpretation.

### Specialized Production Workflows

#### UI, Cutscenes, and Assets

- [Cutscene Agent](https://kuaishou-gamemind.github.io/cutscene_agent/) - Generates editable Unreal Engine Level Sequences from natural-language scripts through a 30+ tool MCP interface and a visual feedback loop. Evidence C; the current scope is dialogue-driven cutscenes rather than general gameplay implementation. ([Paper](https://arxiv.org/abs/2604.25318))
- [GameUIAgent](https://github.com/zengwei-code/GameUIAgent) - Converts language requests into editable game UI designs through a structured specification. Evidence C; it covers a production subtask rather than complete games. ([Paper](https://arxiv.org/abs/2603.14724))
- [CubePart](https://github.com/Roblox/cube) - Generates coherent multipart meshes whose components can receive animation, physics, and scripts. Evidence B; it produces game-ready assets rather than game logic. ([Paper](https://arxiv.org/abs/2605.28763))

## Adjacent Signals

These items matter to the direction of the field but are not treated as direct
evidence of complete, editable game generation.

### Engine and Industry Signals

- [Unity AI Open Beta](https://unity.com/blog/unity-ai-how-to-get-started) - Adds project-aware agent modes, editor actions, code and scene modification, validation, and an official MCP server. Evidence E; Unity publishes no reproducible capability benchmark for it.
- [Unreal MCP in Unreal Engine 5.8](https://dev.epicgames.com/documentation/unreal-engine/unreal-mcp-in-unreal-editor) - Exposes editor state and actions to external agents. Evidence E; this is an experimental tool surface rather than a game-generation benchmark.
- [Roblox 4D Creation](https://about.roblox.com/newsroom/2026/02/accelerating-creation-powered-roblox-cube-foundation-model) - Generates structured functional objects with separable parts and behavior scripts. Evidence E; current evidence concerns constrained object schemas rather than complete games.
- [Godot Contribution Policy 2026](https://godotengine.org/article/contribution-policy-2026/) - Requires accountable human authorship and rejects autonomous AI-agent contributions. Evidence E; it highlights review burden, ownership, and maintainability as production requirements.
- [GDC 2026 State of the Game Industry](https://reg.gdconf.com/2026-SOTI) - Surveys more than 2,300 game-industry professionals and examines generative AI, workforce trends, and business models. Evidence E; the public landing page does not expose the report's detailed result breakdowns.

### Interactive World Models

World models generate responsive environments, not necessarily editable game
projects with explicit objects, rules, and versionable state.

- [Matrix-Game 3.0](https://github.com/SkyworkAI/Matrix-Game/tree/main/Matrix-Game-3) - Reports 40 FPS at 720p and lists A/H-series GPUs with 64 GB RAM among tested configurations; it generates interactive neural worlds rather than editable game projects.
- [HY-World 2.0](https://github.com/Tencent-Hunyuan/HY-World-2.0) - Produces navigable structured 3D representations exportable toward engine workflows; it creates environments, not game mechanics.
- [minWM](https://github.com/shengshu-ai/minWM) - Provides an open recipe for converting video models into camera-controllable worlds rather than complete games.
- [Project Genie](https://labs.google/projectgenie) - Demonstrates responsive generated environments. Evidence E; it is a product experiment rather than an editable game engine.

### Practitioner Field Reports

- [Fable-Assisted Command & Conquer iOS/iPadOS Port](https://github.com/ammaarreshi/Generals-Mac-iOS-iPad) - Documents a human-directed Claude Code/Fable workflow that extended an existing macOS/Linux community port to iOS and iPadOS. Evidence B; the exact Fable version is unspecified, and the artifact is not a standardized model evaluation.

## Evidence Guide

**A** Reproducible benchmark · **B** Reproducible case study · **C** Controlled
experiment · **D** Field report · **E** Official first-party source · **W**
Watchlist.

Grades indicate verifiability, not importance or product quality. See
[CONTRIBUTING.md](CONTRIBUTING.md) for the complete criteria.

## Contributing

Contributions are welcome. New items should include an exact date and version,
a game-specific artifact or evaluation, the strongest safe claim, and one
meaningful caveat.

This project follows the [Contributor Covenant](CODE_OF_CONDUCT.md).

Last curated review: **2026-07-14**. This repository is a research-oriented
curation, not an endorsement of any model, product, benchmark, or licensing
regime.

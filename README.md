# Awesome AI Game Dev [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Evidence-backed systems for building, editing, testing, and evaluating games with AI.

AI game development is moving beyond code completion toward engine-aware agents, runtime feedback, interactive verification, and production tooling. This list favors reproducible benchmarks, inspectable systems, and concrete field reports over exhaustive tool coverage.

**Scope:** Primarily work released or materially updated in 2026. A polished demo, a runnable prototype, and a complete game are not treated as equivalent.

**中文简介：** 这是一个以证据为核心的 AI 游戏开发前沿清单，重点收录可复现 benchmark、引擎内 Agent、自动试玩与验证、可核验案例和产业信号，而不是罗列所有 AI 美术工具或营销 Demo。

## Contents

- [Reading the Evidence](#reading-the-evidence)
- [Benchmarks and Evaluation](#benchmarks-and-evaluation)
- [Game Development Agents and Systems](#game-development-agents-and-systems)
- [Playtesting, QA, and Balancing](#playtesting-qa-and-balancing)
- [Frontier Model Field Reports](#frontier-model-field-reports)
- [Industry and Engine Signals](#industry-and-engine-signals)
- [Interactive World Models](#interactive-world-models)
- [Open Problems](#open-problems)
- [Deep Dive](#deep-dive)

## Reading the Evidence

Evidence grades describe verifiability, not importance or product quality.

**A — Reproducible benchmark.** Public tasks plus executable evaluation and inspectable code or results.

**B — Reproducible case study.** Public artifact or repository plus a meaningful engineering record.

**C — Controlled research experiment.** Defined protocol, but narrow, private, or substantially judge-dependent.

**D — Practitioner field report.** Named practitioner with concrete process details and preferably an artifact.

**E — Official product evidence.** First-party release or demo without independent evaluation.

**W — Watchlist.** Relevant release without sufficient game-specific evidence yet.

Keep this capability ladder in mind when comparing results:

```text
valid code -> builds -> launches -> looks usable -> responds to input
           -> satisfies requirements -> feels complete -> is maintainable and fun
```

No current benchmark covers the whole ladder. Results remain specific to the stated model, agent implementation, tools, feedback channel, budget, and benchmark version.

## Benchmarks and Evaluation

### Engine Editing

- [GameDevBench v2](https://github.com/waynchi/gamedevbench) - Evaluates 333 localized Godot tasks with deterministic engine tests and optional visual feedback. Runtime video and screenshots materially improve agent performance. Evidence A; it edits existing projects rather than generating complete games. ([Paper](https://arxiv.org/abs/2602.11103))
- [PlayEval / PlayCoder](https://github.com/Tencent/PlayCoder) - Combines compile and execution checks with interaction-based Play@3 evaluation across 43 multilingual GUI applications, including games. Evidence A; it is not game-only and focuses on repository modification. ([Paper](https://arxiv.org/abs/2604.19742))

### End-to-End Game Generation

- [GameCraft-Bench](https://github.com/FreedomIntelligence/gamecraft-bench) - Evaluates 140 prompt-to-complete-game Godot tasks using editable projects and replayable demonstrations. The strongest reported configuration reaches 41.46% overall. Evidence A; results are harness-, demonstration-, and judge-specific. ([Paper](https://arxiv.org/abs/2606.17861), [Project](https://tongxuluo.github.io/gamecraft-bench-website/))
- [OpenGame / OpenGame-Bench](https://github.com/leigest519/OpenGame) - Generates editable Phaser 3 games and evaluates Build Health, Visual Usability, and Intent Alignment on 150 prompts. Evidence A; browser-native development has a different tool boundary from professional engines. ([Paper](https://arxiv.org/abs/2604.18394))
- [WebGameBench](https://arxiv.org/abs/2605.17637) - Tests 12 coding agents on 111 browser-game tasks with a real runtime evaluator and separates Excellent, Usable, and Unusable outcomes. Evidence C; public evaluation code was not verified at the survey cutoff.
- [JAMER / JamBench](https://arxiv.org/abs/2606.19830) - Builds a corpus of 8,133 verified Godot projects and evaluates multi-granularity completion and from-scratch generation. Evidence A; its sharp scale cliff highlights architecture and dependency management as core bottlenecks.

### Runtime and Playability Evaluation

- [PlaytestArena / Play2Code](https://continual-game-generation.vercel.app/) - Places a GUI playtesting agent in a generation-repair loop across 200 browser-game tasks. Evidence C; diagnosis remains bounded by the states the player agent can reach. ([Paper](https://arxiv.org/abs/2605.28258))
- [GameGen-Verifier / VeriGame](https://arxiv.org/abs/2605.07442) - Decomposes requirements, injects target runtime states, performs bounded interactions, and verifies mechanics in parallel. Evidence C; white-box verification improves coverage but does not measure holistic pacing, polish, or fun.
- [WorldCoder-Bench](https://arxiv.org/abs/2606.01869) - Uses hidden state-transition contracts to test 2,026 physically grounded Three.js tasks. Evidence A; it measures interactive worlds rather than complete games.

## Game Development Agents and Systems

### Godot and Web Engines

- [OpenGame](https://github.com/leigest519/OpenGame/tree/main/opengame) - Provides a game-generation agent with project templates, reusable debugging protocols, build tests, and iterative repair. Its ablations show that the harness changes results materially.
- [CreativeGame](https://arxiv.org/abs/2604.19926) - Treats HTML5 game creation as evolving lineages with mechanic plans and version ancestry. Evidence C; it emphasizes qualitative iteration rather than a strong aggregate benchmark.

### Unreal Engine

- [AutoUE](https://arxiv.org/abs/2603.07106) - Connects asset retrieval, procedural scene construction, C++ gameplay implementation, and MCP-based testing in editable Unreal Engine projects. Evidence C; results use a small self-built benchmark and substantial model judgment.
- [Cutscene Agent](https://kuaishou-gamemind.github.io/cutscene_agent/) - Produces native editable Unreal Engine Level Sequences through more than 60 tools. Evidence C; it focuses on dialogue cutscenes rather than general game implementation. ([Paper](https://arxiv.org/abs/2604.25318))

### Unity and Production Subtasks

- [MAGE](https://arxiv.org/abs/2605.07342) - Studies direct C# generation and structured intermediate representations for goal-playable Unity mechanics. Evidence C; runtime success and mechanic fidelity diverge sharply.
- [GameUIAgent](https://github.com/zengwei-code/GameUIAgent) - Converts language requests into editable game UI designs through a structured design specification. Evidence C; it covers a production subtask rather than complete games. ([Paper](https://arxiv.org/abs/2603.14724))
- [CubePart](https://github.com/Roblox/cube) - Generates coherent multipart meshes whose components can receive animation, physics, and scripts. Evidence B/C; it produces game-ready assets rather than game logic. ([Paper](https://arxiv.org/abs/2605.28763))

## Playtesting, QA, and Balancing

- [GBQA](https://arxiv.org/abs/2604.02648) - Evaluates agents on 124 human-verified implanted bugs across 30 lightweight web games. Evidence C; the best reported system finds fewer than half of the bugs.
- [RuleSmith](https://github.com/Adonis-galaxy/RuleSmith) - Combines LLM self-play with Bayesian optimization to search game-rule parameters. Evidence C; balance found for one simulated-player population may not transfer to other players. ([Paper](https://arxiv.org/abs/2602.06232))
- [CA2](https://arxiv.org/abs/2605.13918) - Uses code-level observations and offline reinforcement learning to reach target functions in Crafter and a Godot environment. Evidence C; it depends on source profiling and offline human trajectories.
- [RAID](https://arxiv.org/abs/2607.07498) - Uses iterative reinforcement-learning populations to discover exploit strategies in a pre-release NHL 26 scenario. Evidence C/D; the evidence comes from one proprietary game and still requires human interpretation.

## Frontier Model Field Reports

- [Fable-Assisted Command & Conquer Apple Port](https://github.com/ammaarreshi/Generals-Mac-iOS-iPad) - Documents Claude Fable 5 assisting a repository-scale C++ port to macOS, iPhone, and iPad. Evidence B/D for human-directed engineering; it builds on existing source and community work rather than generating a game from scratch.
- [Claude-Generated NES Emulator](https://github.com/willtobyte/NES) - Provides a runnable browser artifact and a useful reminder that functional output still requires performance and accuracy testing. Evidence D; the exact Claude model and full process are unspecified.

The GPT-5.6 family, Claude Fable 5, Claude Opus 4.8, and the Gemini 3.5 family remain on the benchmark watchlist. General software-engineering performance is not game-development evidence; useful reports must identify the exact model, agent harness, engine, budget, and artifact.

## Industry and Engine Signals

- [Unity AI Open Beta](https://unity.com/blog/unity-ai-how-to-get-started) - Adds project-aware agent modes, editor actions, code and scene modification, validation, a model gateway, and an official MCP server. Evidence E; Unity publishes no reproducible capability benchmark for it.
- [Unreal MCP in Unreal Engine 5.8](https://dev.epicgames.com/documentation/unreal-engine/unreal-mcp-in-unreal-editor) - Exposes editor state and actions to external agents. Evidence E; this is an experimental tool surface rather than an Epic game-generation model or benchmark.
- [Roblox 4D Creation](https://about.roblox.com/newsroom/2026/02/accelerating-creation-powered-roblox-cube-foundation-model) - Generates structured functional objects with separable parts, behavior, and physics. Evidence E; current evidence concerns constrained object schemas rather than complete games.
- [Godot Contribution Policy 2026](https://godotengine.org/article/contribution-policy-2026/) - Requires accountable human authorship and rejects autonomous AI-agent contributions. Evidence E; it highlights review burden, ownership, and maintainability as production requirements.
- [GDC 2026 State of the Game Industry](https://reg.gdconf.com/2026-SOTI) - Reports generative-AI adoption concentrated in research, brainstorming, prototyping, and debugging rather than player-facing features. Evidence C.

## Interactive World Models

World models are adjacent to game development, but their outputs should not be confused with editable game projects. Engine-native systems produce scenes, scripts, assets, and explicit rules; structured world models produce geometry or collision-bearing environment assets; neural world models produce action-conditioned video frames.

- [Matrix-Game 3.0](https://github.com/SkyworkAI/Matrix-Game/tree/main/Matrix-Game-3) - Reports real-time, minute-scale interactive neural-world generation. Open source; high-end configurations remain computationally expensive.
- [HY-World 2.0](https://github.com/Tencent-Hunyuan/HY-World-2.0) - Produces navigable structured 3D representations exportable toward Unity, Unreal Engine, and Blender workflows. It creates environments, not game mechanics.
- [minWM](https://github.com/shengshu-ai/minWM) - Provides an open full-stack recipe for converting video models into camera-controllable worlds rather than complete games.
- [Project Genie](https://labs.google/projectgenie) - Demonstrates responsive generated environments. Evidence E/D; independent hands-on reports highlight limited duration, objectives, control, and consistency.

## Open Problems

**Long-horizon coherence:** Maintaining architecture, state, dependencies, and design intent across many files and iterations.

**Engine-native multimodality:** Combining editor state, runtime video, animation, physics, audio, and logs in one reliable loop.

**Playtest coverage:** Reaching rare states and edge cases without hours of unrestricted exploration.

**Mechanics versus experience:** Combining deterministic correctness with clarity, pacing, balance, presentation, and fun.

**Evaluator reliability:** Detecting when the evaluator, rather than the generated game, failed.

**Cost reporting:** Recording wall time, retries, tokens, human actions, and failed attempts.

**Maintainability and ownership:** Testing whether another developer can safely extend and repair generated work.

**World-to-engine transfer:** Converting responsive visual worlds into explicit objects, rules, and editable state.

## Deep Dive

The [AI Game Development Frontier Survey 2026](AI_GAME_DEV_FRONTIER_SURVEY_2026.md) contains the full methodology, benchmark comparisons, model-evidence notes, world-model taxonomy, industry analysis, candidate inventory, and wording guidance for responsible claims.

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before proposing an entry. New items should include an exact date and version, a game-specific artifact or evaluation, the strongest safe claim, and one meaningful caveat.

This project follows the [Contributor Covenant](CODE_OF_CONDUCT.md).

## Footnotes

Last curated review: **2026-07-14**. This repository is a research-oriented curation, not an endorsement of any model, product, benchmark, or licensing regime.

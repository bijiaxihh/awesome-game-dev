# Awesome AI Game Dev [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> An evidence-backed map of AI systems for building, testing, and evaluating games in 2026.

This repository grew out of my work as a co-author of GameCraft-Bench and my
effort to systematically understand the 2026 AI game-development frontier. I
apply the same evidence criteria and caveats to GameCraft-Bench as to every
other entry.

## Contents

- [My 2026 Takeaways](#my-2026-takeaways)
- [Three Anchor Cases](#three-anchor-cases)
- [Curated Landscape](#curated-landscape)
- [Three Open Problems](#three-open-problems)
- [Methodology and Evidence](#methodology-and-evidence)
- [Adjacent Signals](#adjacent-signals)

## My 2026 Takeaways

**Runtime and visual feedback are becoming first-class development capabilities.** In GameDevBench v2, under the Codex harness, GPT-5.4 pass@1 increases from 41.1% to 52.0% when screenshot and runtime-video feedback are enabled.

**Runnable is not equivalent to playable or complete.** The strongest completed configuration in GameCraft-Bench reaches a 41.46% overall benchmark score, with long-horizon coherence and experience quality still unresolved.

**Benchmarks and frontier-model field reports provide different levels of evidence.** Benchmarks support controlled comparison; public engineering artifacts offer earlier but noisier signals.

## Three Anchor Cases

| Case                                                                              | What it evaluates              | Key signal                                                    | My takeaway                                               |
| --------------------------------------------------------------------------------- | ------------------------------ | ------------------------------------------------------------- | --------------------------------------------------------- |
| [GameDevBench v2](https://arxiv.org/abs/2602.11103)                               | Localized Godot project edits  | GPT-5.4 pass@1 rises from 41.1% to 52.0% with visual feedback | Agents need an engine feedback loop                       |
| [GameCraft-Bench](https://arxiv.org/abs/2606.17861)                               | Complete Godot game generation | Best completed configuration: 41.46% overall benchmark score  | Runnable remains far from complete and playable           |
| [Fable C&C iOS/iPadOS case](https://github.com/ammaarreshi/Generals-Mac-iOS-iPad) | Human-directed porting work    | Public artifact, but no standardized benchmark                | A field case is an early signal, not a capability ranking |

The Fable case extends an existing macOS/Linux community port to iOS and
iPadOS. The linked repository says Claude Code/Fable but does not identify the
exact Fable version; it is not evidence for Fable 5 specifically. Scores across
the two benchmarks are also not directly comparable because their task scope,
harness, and evaluation protocols differ.

## Curated Landscape

The entries below are the core evidence library: benchmarks, development
systems, and automated testing. Together, the three anchor cases provide a
compact cross-section of the current evidence landscape.

### Benchmarks and Evaluation

#### Engine Editing

- [GameDevBench v2](https://github.com/waynchi/gamedevbench) - Evaluates 333 localized Godot tasks with deterministic engine tests and optional visual feedback. Evidence A; it edits existing projects rather than generating complete games.
- [PlayEval / PlayCoder](https://github.com/Tencent/PlayCoder) - Combines compile and execution checks with interaction-based Play@3 evaluation across 43 multilingual GUI applications, including games. Evidence A; it is not game-only and focuses on repository modification. ([Paper](https://arxiv.org/abs/2604.19742))

#### End-to-End Game Generation

- [GameCraft-Bench](https://github.com/FreedomIntelligence/gamecraft-bench) - Evaluates 140 prompt-to-complete-game Godot tasks using editable projects and replayable demonstrations. Evidence A; results are harness-, demonstration-, and judge-specific. ([Project](https://tongxuluo.github.io/gamecraft-bench-website/))
- [OpenGame / OpenGame-Bench](https://github.com/leigest519/OpenGame) - Generates editable Phaser 3 games and evaluates Build Health, Visual Usability, and Intent Alignment on 150 prompts. Evidence A; browser-native development has a different tool boundary from professional engines. ([Paper](https://arxiv.org/abs/2604.18394))
- [WebGameBench](https://arxiv.org/abs/2605.17637) - Tests 12 coding agents on 111 browser-game tasks with a real runtime evaluator. Evidence C; public evaluation code was not verified at the survey cutoff.
- [JAMER / JamBench](https://arxiv.org/abs/2606.19830) - Builds a corpus of 8,133 verified Godot projects and evaluates multi-granularity completion and from-scratch generation. Evidence A; its scale cliff highlights architecture and dependency management as core bottlenecks.

#### Runtime and Playability Evaluation

- [PlaytestArena / Play2Code](https://continual-game-generation.vercel.app/) - Places a GUI playtesting agent in a generation-repair loop across 200 browser-game tasks. Evidence C; diagnosis remains bounded by the states the player agent can reach. ([Paper](https://arxiv.org/abs/2605.28258))
- [GameGen-Verifier / VeriGame](https://arxiv.org/abs/2605.07442) - Decomposes requirements, injects target runtime states, performs bounded interactions, and verifies mechanics in parallel. Evidence C; it does not measure holistic pacing, polish, or fun.
- [WorldCoder-Bench](https://arxiv.org/abs/2606.01869) - Uses hidden state-transition contracts to test 2,026 physically grounded Three.js tasks. Evidence A; it measures interactive worlds rather than complete games.

### Game Development Agents and Systems

#### Web Engines

- [CreativeGame](https://arxiv.org/abs/2604.19926) - Treats HTML5 game creation as evolving lineages with mechanic plans and version ancestry. Evidence C; it emphasizes qualitative iteration rather than a strong aggregate benchmark.

#### Unreal Engine

- [AutoUE](https://arxiv.org/abs/2603.07106) - Connects asset retrieval, procedural scene construction, C++ gameplay implementation, and MCP-based testing in editable Unreal Engine projects. Evidence C; results use a small self-built benchmark and substantial model judgment.
- [Cutscene Agent](https://kuaishou-gamemind.github.io/cutscene_agent/) - Produces native editable Unreal Engine Level Sequences through more than 60 tools. Evidence C; it focuses on dialogue cutscenes rather than general game implementation. ([Paper](https://arxiv.org/abs/2604.25318))

#### Unity and Specialized Production Workflows

- [MAGE](https://arxiv.org/abs/2605.07342) - Studies direct C# generation and structured intermediate representations for goal-playable Unity mechanics. Evidence C; runtime success and mechanic fidelity diverge sharply.
- [GameUIAgent](https://github.com/zengwei-code/GameUIAgent) - Converts language requests into editable game UI designs through a structured specification. Evidence C; it covers a production subtask rather than complete games. ([Paper](https://arxiv.org/abs/2603.14724))
- [CubePart](https://github.com/Roblox/cube) - Generates coherent multipart meshes whose components can receive animation, physics, and scripts. Evidence B; it produces game-ready assets rather than game logic. ([Paper](https://arxiv.org/abs/2605.28763))

### Playtesting, QA, and Balancing

- [GBQA](https://arxiv.org/abs/2604.02648) - Evaluates agents on 124 human-verified implanted bugs across 30 lightweight web games. Evidence C; the best reported system finds fewer than half of the bugs.
- [RuleSmith](https://github.com/Adonis-galaxy/RuleSmith) - Combines LLM self-play with Bayesian optimization to search game-rule parameters. Evidence C; balance found for one simulated-player population may not transfer to other players. ([Paper](https://arxiv.org/abs/2602.06232))
- [CA2](https://arxiv.org/abs/2605.13918) - Uses code-level observations and offline reinforcement learning to reach target functions in Crafter and a Godot environment. Evidence C; it depends on source profiling and offline human trajectories.
- [RAID](https://arxiv.org/abs/2607.07498) - Uses iterative reinforcement-learning populations to discover exploit strategies in a pre-release NHL 26 scenario. Evidence C; the evidence comes from one proprietary game and still requires human interpretation.

## Three Open Problems

**Long-horizon project coherence.** Can an agent preserve architecture, state,
dependencies, and design intent across many files and iterations?

**Runtime and interactive verification.** Can it launch the game, observe what
happened, exercise the relevant states, and repair failures rather than merely
inspect code?

**Mechanics versus player experience.** Correct mechanics do not guarantee
clear feedback, coherent presentation, pacing, completeness, maintainability,
or fun.

## Methodology and Evidence

Evidence grades describe verifiability, not importance or product quality.

**A - Reproducible benchmark:** public tasks plus executable evaluation and
inspectable code or results.

**B - Reproducible case study:** public artifact or repository plus a meaningful
engineering record.

**C - Controlled research experiment:** defined protocol, but narrow, private,
or substantially judge-dependent.

**D - Practitioner field report:** named practitioner with concrete process
details and preferably an artifact.

**E - Official product evidence:** first-party release or demo without
independent evaluation.

**W - Watchlist:** relevant release without sufficient game-specific evidence
yet.

Each concrete claim receives one conservative grade. Results remain specific to
the stated model, agent implementation, tools, feedback channel, budget, and
benchmark version.

```text
valid code -> builds -> launches -> looks usable -> responds to input
           -> satisfies requirements -> feels complete -> is maintainable and fun
```

No current benchmark covers this whole capability ladder.

## Adjacent Signals

These items matter to the direction of the field but are not treated as direct
evidence of complete, editable game generation.

### Industry and Engine Signals

- [Unity AI Open Beta](https://unity.com/blog/unity-ai-how-to-get-started) - Adds project-aware agent modes, editor actions, code and scene modification, validation, and an official MCP server. Evidence E; Unity publishes no reproducible capability benchmark for it.
- [Unreal MCP in Unreal Engine 5.8](https://dev.epicgames.com/documentation/unreal-engine/unreal-mcp-in-unreal-editor) - Exposes editor state and actions to external agents. Evidence E; this is an experimental tool surface rather than a game-generation benchmark.
- [Roblox 4D Creation](https://about.roblox.com/newsroom/2026/02/accelerating-creation-powered-roblox-cube-foundation-model) - Generates structured functional objects with separable parts, behavior, and physics. Evidence E; current evidence concerns constrained object schemas rather than complete games.
- [Godot Contribution Policy 2026](https://godotengine.org/article/contribution-policy-2026/) - Requires accountable human authorship and rejects autonomous AI-agent contributions. Evidence E; it highlights review burden, ownership, and maintainability as production requirements.
- [GDC 2026 State of the Game Industry](https://reg.gdconf.com/2026-SOTI) - Reports generative-AI adoption concentrated in research, brainstorming, prototyping, and debugging rather than player-facing features. Evidence C.

### Interactive World Models

World models generate responsive environments, not necessarily editable game
projects with explicit objects, rules, and versionable state.

- [Matrix-Game 3.0](https://github.com/SkyworkAI/Matrix-Game/tree/main/Matrix-Game-3) - Reports real-time, minute-scale interactive neural-world generation; high-end configurations remain computationally expensive.
- [HY-World 2.0](https://github.com/Tencent-Hunyuan/HY-World-2.0) - Produces navigable structured 3D representations exportable toward engine workflows; it creates environments, not game mechanics.
- [minWM](https://github.com/shengshu-ai/minWM) - Provides an open recipe for converting video models into camera-controllable worlds rather than complete games.
- [Project Genie](https://labs.google/projectgenie) - Demonstrates responsive generated environments. Evidence E; it is a product experiment rather than an editable game engine.

### Adjacent Engineering Case

- [Claude-Generated NES Emulator](https://github.com/willtobyte/NES) - Provides a runnable browser artifact and a reminder that functional output still requires performance and accuracy testing. Evidence D; the exact Claude model and full process are unspecified.

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md).
New items should include an exact date and version, a game-specific artifact or
evaluation, the strongest safe claim, and one meaningful caveat.

This project follows the [Contributor Covenant](CODE_OF_CONDUCT.md).

Last curated review: **2026-07-14**. This repository is a research-oriented
curation, not an endorsement of any model, product, benchmark, or licensing
regime.

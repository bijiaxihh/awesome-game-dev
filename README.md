# Awesome AI Game Dev [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated and continuously updated list of research, systems, benchmarks,
> and frontier signals for AI-assisted game development.

The list focuses on systems that build, edit, run, test, verify, or improve
games. Game-playing agents, world models, and industry products are included
only when they provide meaningful signals for game-development research.

The default focus is 2026 and later, with selected earlier work included when
it remains foundational. This is a curation, not a comprehensive survey or a
cross-benchmark leaderboard.

## Contents

- [Latest Updates](#latest-updates)
- [Build & Edit Games](#build--edit-games)
- [Test, Verify & Improve](#test-verify--improve)
- [Agents, Harnesses & Training](#agents-harnesses--training)
- [Frontier & Adjacent Signals](#frontier--adjacent-signals)
- [Contributing](#contributing)

## Latest Updates

- **2026-07-21** — Added GameEngineBench, which evaluates native C++ changes
  in real Unreal Engine 5 projects.
- **2026-07-21** — Added execution-gated self-distillation on GameCraft-Bench
  as a verifier-guided training signal.
- **2026-07-21** — Added official game-development and game-playing signals
  from Kimi K3, GPT-5.6, and Claude Fable 5 with explicit boundaries.
- **2026-07-21** — Reorganized the list around four stages of the development
  loop and replaced evidence grades with direct labels.

See [UPDATES.md](UPDATES.md) for the full history and
[WATCHLIST.md](WATCHLIST.md) for items awaiting stronger evidence.

## Build & Edit Games

- [GameCraft-Bench](https://github.com/FreedomIntelligence/gamecraft-bench) —
  Evaluates agents on 140 prompt-to-complete-game Godot tasks using editable
  projects and replayable demonstrations. [Paper](https://arxiv.org/abs/2606.17861)
  [Demo](https://tongxuluo.github.io/gamecraft-bench-website/) — `Benchmark` `Godot` `Generation`
- [GameDevBench](https://github.com/waynchi/gamedevbench) — Evaluates coding
  agents on 333 localized Godot edits with deterministic engine tests and
  optional screenshot/video feedback. [Paper](https://arxiv.org/abs/2602.11103)
  — `Benchmark` `Godot` `Editing`
- [GameEngineBench](https://arxiv.org/abs/2607.03525) — Evaluates coding agents
  on 110 native C++ tasks from nine real Unreal Engine 5 projects using
  executable behavioral tests. — `Benchmark` `UE5` `C++`
- [OpenGame](https://github.com/leigest519/OpenGame) — Generates Phaser 3 web
  games and evaluates build health, visual usability, and intent alignment on
  150 prompts. [Paper](https://arxiv.org/abs/2604.18394) — `System` `Browser` `Generation`
  - *Boundary: The repository says the benchmark evaluation pipeline is not yet released.*
- [WebGameBench](https://arxiv.org/abs/2605.17637) — Evaluates 12 coding agents
  on 111 browser-game tasks with a runtime evaluator. — `Benchmark` `Browser`
  - *Boundary: A public evaluation implementation was not verified on 2026-07-21.*
- [JAMER / JamBench](https://arxiv.org/abs/2606.19830) — Builds JamSet from
  8,133 verified Godot projects and evaluates generation and completion on a
  300-project benchmark. — `Dataset` `Benchmark` `Godot`
  - *Boundary: The paper claims public code and data but gives no verifiable release URL.*
- [CreativeGame](https://arxiv.org/abs/2604.19926) — Treats HTML5 game creation
  as iterative lineages with mechanic plans and version ancestry. — `System` `Browser`
  - *Boundary: Evaluation emphasizes qualitative iteration rather than a standardized benchmark.*
- [WorldCoder-Bench](https://arxiv.org/abs/2606.01869) — Uses hidden,
  mutation-hardened runtime contracts to evaluate 2,026 Three.js world-synthesis
  tasks. — `Benchmark` `Three.js`
  - *Boundary: A public benchmark implementation was not verified on 2026-07-21.*
- [AutoUE](https://arxiv.org/abs/2603.07106) — Connects asset retrieval, scene
  construction, C++ gameplay implementation, and MCP-based testing in editable
  Unreal Engine projects. — `System` `UE5` `MCP`
- [Cutscene Agent](https://kuaishou-gamemind.github.io/cutscene_agent/) — Creates
  editable Unreal Engine Level Sequences from scripts through an MCP tool
  interface and visual feedback. [Paper](https://arxiv.org/abs/2604.25318)
  — `System` `UE5` `Cutscene`
- [GameUIAgent](https://github.com/zengwei-code/GameUIAgent) — Converts language
  requests into editable game UI designs through a structured specification.
  [Paper](https://arxiv.org/abs/2603.14724) — `System` `UI`
- [CubePart](https://github.com/Roblox/cube) — Generates coherent multipart
  meshes whose components can receive animation, physics, and scripts.
  [Paper](https://arxiv.org/abs/2605.28763) — `System` `Asset`
  - *Boundary: It creates game-ready assets, not complete game logic.*

## Test, Verify & Improve

- [PlayEval / PlayCoder](https://github.com/Tencent/PlayCoder) — Combines
  compile and execution checks with interaction-based Play@3 evaluation across
  43 multilingual GUI applications, including games.
  [Paper](https://arxiv.org/abs/2604.19742) — `Benchmark` `Repair` `Visual Feedback`
- [MAGE](https://arxiv.org/abs/2605.07342) — Compares direct C# generation and
  structured intermediate representations across 858 Unity scenes and 26
  mechanic concepts. — `Verification` `Unity`
- [GameGen-Verifier / VeriGame](https://arxiv.org/abs/2605.07442) — Decomposes
  requirements, restores target runtime states, executes bounded interactions,
  and verifies mechanics in parallel. — `Verification` `Runtime State`
- [PlaytestArena / Play2Code](https://continual-game-generation.vercel.app/) —
  Places a GUI playtesting agent in a generation-and-repair loop across 200
  browser-game tasks. [Paper](https://arxiv.org/abs/2605.28258)
  — `Playtesting` `Repair` `Browser`
- [GBQA](https://arxiv.org/abs/2604.02648) — Evaluates agents on 124
  human-verified implanted bugs across 30 lightweight web games.
  — `Benchmark` `QA` `Browser`
- [CA2](https://arxiv.org/abs/2605.13918) — Uses code-level observations and
  offline reinforcement learning to reach target functions in Crafter and a
  Godot environment. — `Playtesting` `RL` `Godot`
- [RuleSmith](https://github.com/Adonis-galaxy/RuleSmith) — Combines LLM
  self-play with Bayesian optimization to search game-rule parameters.
  [Paper](https://arxiv.org/abs/2602.06232) — `System` `Balance`
- [RAID](https://arxiv.org/abs/2607.07498) — Uses iterative reinforcement-learning
  populations to discover exploit strategies in a pre-release NHL 26 scenario.
  — `System` `Exploit Discovery`
  - *Boundary: Evidence comes from one proprietary scenario and requires human interpretation.*

## Agents, Harnesses & Training

- [Harbor](https://github.com/harbor-framework/harbor) — Runs agents in
  isolated environments with versioned tasks, verifiers, and trajectories; it
  provides the execution harness used by GameCraft-Bench. — `Harness` `Evaluation`
- [The Verifier is the Curriculum](https://arxiv.org/abs/2607.09709) — Uses a
  strict Godot launch gate for rejection-sampling self-distillation on
  GameCraft-Bench and studies cross-family generalization. — `Training` `Verifier` `Godot`
  - *Boundary: The current arXiv record does not link a public implementation.*
- [Unreal MCP](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-mcp-in-unreal-editor) —
  Exposes Unreal Editor context and actions to external agents through an
  experimental official MCP interface. — `Engine Interface` `UE5` `MCP`

## Frontier & Adjacent Signals

These entries indicate where the field may be heading, but are not necessarily
reproducible evidence of end-to-end game-development capability.

- [Kimi K3](https://www.kimi.com/blog/kimi-k3) — Presents official cases that
  iterate between code and live screenshots to refine playable interactive
  experiences. — `Official Case` `Vision in the Loop`
  - *Boundary: The full prompts, trajectories, budgets, and engine benchmark are not public.*
- [GPT-5.6](https://openai.com/index/gpt-5-6/) — Reports a partner evaluation
  where programmatic tool calling builds Unity scenes with fewer tokens and
  model turns than direct tool calls. — `Official Case` `Unity`
  - *Boundary: This is a first-party partner case, not a standardized public benchmark.*
- [Claude Fable 5](https://www.anthropic.com/news/claude-fable-5-mythos-5) —
  Demonstrates vision-only Pokémon FireRed play and persistent-memory
  experiments in Slay the Spire. — `Official Case` `Game Playing`
  - *Boundary: Game playing informs agent design but does not demonstrate game generation.*
- [Unity AI Open Beta](https://unity.com/blog/unity-ai-how-to-get-started) — Adds
  project-aware agents, editor actions, code and scene modification, validation,
  and an official MCP server. — `Official Product` `Unity`
  - *Boundary: Unity publishes no reproducible capability benchmark for the product.*
- [Roblox 4D Creation](https://about.roblox.com/newsroom/2026/02/accelerating-creation-powered-roblox-cube-foundation-model) —
  Generates structured functional objects with separable parts and behavior
  scripts. — `Official Product` `Asset`
  - *Boundary: Current evidence covers constrained object schemas, not complete games.*
- [Godot Contribution Policy 2026](https://godotengine.org/article/contribution-policy-2026/) —
  Requires accountable human authorship and rejects autonomous AI-agent
  contributions. — `Governance` `Godot`
- [GDC 2026 State of the Game Industry](https://reg.gdconf.com/2026-SOTI) —
  Surveys more than 2,300 game-industry professionals on generative AI,
  workforce trends, and business models. — `Survey` `Industry`
  - *Boundary: The public landing page does not expose the detailed result breakdowns.*
- [Matrix-Game 3.0](https://github.com/SkyworkAI/Matrix-Game/tree/main/Matrix-Game-3) —
  Generates camera-controllable interactive neural worlds in real time.
  — `World Model` `Interactive Video`
  - *Boundary: Its output is not an editable game project with explicit mechanics.*
- [HY-World 2.0](https://github.com/Tencent-Hunyuan/HY-World-2.0) — Produces
  navigable structured 3D representations that can move toward engine
  workflows. — `World Model` `3D`
  - *Boundary: It creates environments rather than complete game mechanics.*
- [minWM](https://github.com/shengshu-ai/minWM) — Provides an open recipe for
  converting video models into camera-controllable worlds. — `World Model` `Open Source`
  - *Boundary: It generates controllable worlds rather than editable games.*
- [Project Genie](https://labs.google/projectgenie) — Demonstrates responsive
  generated environments as a product experiment. — `Official Product` `World Model`
  - *Boundary: It is not an editable game engine or a public game-generation benchmark.*
- [Fable-Assisted Command & Conquer iOS/iPadOS Port](https://github.com/ammaarreshi/Generals-Mac-iOS-iPad) —
  Documents a human-directed workflow that extended an existing community port
  to iOS and iPadOS. — `Field Report` `Porting`
  - *Boundary: The exact model version, full trajectory, and standardized evaluation are absent.*

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md)
before opening a pull request. New or not-yet-verifiable items belong in
[WATCHLIST.md](WATCHLIST.md) first.

## Maintainer Note

This repository is maintained by a co-author of GameCraft-Bench.
GameCraft-Bench is evaluated with the same inclusion and evidence standards as
every other work.

Last curated review: **2026-07-21**.

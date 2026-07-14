# AI Game Development Frontier Survey 2026

> Source report for building an `awesome-ai-game-dev` repository  
> Survey window: **2026-01-01 to 2026-07-13**  
> Last checked: **2026-07-13 (America/Los_Angeles)**  
> Focus: AI systems that **build, edit, run, playtest, verify, or materially support the production of games**

## 中文速览

这份报告的正文和条目模板以英文为主，目的是让内容可以直接迁移到公开 GitHub Repo；关键结论与二面表达在这里先用中文说明：

- 2026 年真正的前沿不是“一句话生成完整游戏”，而是评测从代码正确性逐步进入真实引擎、运行时观察、交互验证和可玩性。
- GameDevBench v2 说明视觉/视频反馈会显著提升 Agent 在 Godot 中的开发能力；GameCraft-Bench 则说明最强端到端 Agent 总分仍只有 41.46%。
- 因此最稳妥的核心判断是：**runnable 不等于 playable，playable 也不等于 complete、maintainable 或 fun。**
- 新模型会领先于 benchmark。Claude Code/Fable 已有公开可核验的《命令与征服》iOS/iPadOS 移植案例，但公开材料未说明 Fable 的具体版本；这个案例证明的是“人类指导下的复杂工程协作”，不能被包装成“自动从零做游戏”。
- 目前 frontier 已分化成三类产物：可编辑的引擎/代码工程、可导入工具的持久 3D 世界资产、以及只能持续生成画面的 neural pixel world；三者都可能看起来可交互，但“可玩性”的含义完全不同。
- 更接近产业落地的短期方向很可能是局部生产、QA、playtesting、verification 和 balancing，而不是替代完整工作室。
- Repo 应按证据等级组织：可复现 benchmark、受控系统、可核验 field case、独立 hands-on、官方 demo、watchlist。不要把它们混成同一张能力榜。

## Executive summary

The most defensible description of the 2026 frontier is not “AI can already make complete games.” It is:

> **AI game development is moving from code generation toward interaction-grounded software engineering, but complete and consistently playable games remain unsolved.**

Six findings are especially useful for an interview:

1. **The evaluation target is climbing a capability ladder.** Research is moving from code/compile checks to build health, engine runtime, visual correctness, interaction coverage, requirement satisfaction, and finally experience quality. A game can pass every earlier rung and still fail the next one.
2. **Runnable is not playable.** The strongest end-to-end agent in GameCraft-Bench reaches only **41.46%**, even though agents often implement recognizable mechanics. Missing content, weak feedback, incoherent presentation, and broken long-horizon state remain common.
3. **Visual and runtime feedback matter measurably.** In GameDevBench v2, adding screenshot and runtime-video feedback raises GPT-5.4 from **41.1% to 52.0%**. The bottleneck is not only coding knowledge; it is seeing and diagnosing what the engine actually produced.
4. **The agent harness matters almost as much as the backbone.** OpenGame's templates, hook-driven implementation, and repair protocol produce large gains over direct model calls. Comparing model names without comparing tools, scaffolds, budgets, and feedback loops is therefore misleading.
5. **Benchmarks lag frontier models, so a second evidence track is necessary.** As of the cutoff, the unspecified Claude Code/Fable version used in a public, inspectable Command & Conquer iOS/iPadOS port has no standardized game-development benchmark result that I could verify. The artifact is meaningful evidence of human-directed game engineering, but not evidence of autonomous end-to-end game creation or of a particular Fable version.
6. **The frontier is splitting into three different artifact types.** Engine/code-native systems produce editable game projects; persistent-3D systems produce geometry or collision-bearing world assets; neural world models produce action-conditioned pixel streams. All three can look “interactive,” but their editability, testability, and meaning of playability are fundamentally different.

The recommended repository should therefore be a **curated frontier evidence radar**, not a generic list of AI tools:

> **Awesome AI Game Dev — A curated frontier radar for AI-powered game development, with an emphasis on evaluation, reproducible systems, field reports, and industry signals since 2026.**

---

## 1. Scope and methodology

### 1.1 Included

- Work first released or materially updated in 2026.
- End-to-end or project-level game generation.
- Agentic editing inside Godot, Unreal Engine, Unity, Phaser, Three.js, or browser runtimes.
- Benchmarks for buildability, runtime behavior, interaction, playability, or game-specific software engineering.
- Automated playtesting, QA, verification, balancing, and game-production subworkflows.
- Named developer case studies with an inspectable artifact, engineering log, or repository.
- Official industry systems that produce engine-native or behavior-bearing artifacts.
- Interactive world models, but only in a clearly marked adjacent section.

### 1.2 Excluded from the main list

- Generic coding-model releases with no game-specific evidence.
- “AI made this game” social posts without prompts, artifacts, process details, or failure analysis.
- Game-playing agents whose only goal is to win a game rather than help create or evaluate one.
- Generic image, music, voice, or 3D generation papers unless they connect to an editable game-production workflow.
- Pre-2026 work, except when a material product release or update occurred in 2026; these entries must be labeled as such.
- Pure product announcements presented as established capability.

### 1.3 Sources searched

- arXiv abstracts and latest paper versions.
- Hugging Face Papers / Daily Papers pages for discovery and community visibility.
- Author project pages and official GitHub repositories.
- Official product, company, and game-engine posts.
- Selected hands-on reports when direct testing adds information unavailable in official material.

Hugging Face is useful as a discovery and attention signal, but the latest arXiv version and the project repository are the source of truth for task counts, results, and release status. For example, the initial Hugging Face summary of GameDevBench still describes 132 tasks, while the June camera-ready v2 and repository contain 333 tasks.

Date rule:

- **Paper date = first public preprint date.** A 2025 preprint accepted at a 2026 venue is still background, not a 2026 paper.
- **Product date = first public availability of that specific release.** Therefore Genie 3 is a 2025 model, while Project Genie's public access is a 2026 product event; similarly, an installable 2026 Unity AI Beta can be tracked even if its product lineage is older.

### 1.4 Evidence grades

| Grade | Evidence type | Minimum bar | Appropriate claim |
|---|---|---|---|
| **A** | Reproducible benchmark | Public task definition plus executable evaluation and inspectable results/code | Comparative capability within that benchmark |
| **B** | Reproducible case study | Public artifact/repository plus meaningful process or engineering log | The demonstrated artifact was built under the described workflow |
| **C** | Controlled research experiment | Paper with a defined dataset/protocol, but narrow, private, or judge-dependent evaluation | Evidence for the studied setting only |
| **D** | Practitioner field report | Named practitioner, concrete task, process details, and preferably an artifact | A useful real-world signal, not a leaderboard result |
| **E** | Official product demo or company claim | First-party announcement/demo without independent evaluation | Product direction or reported capability |
| **W** | Watchlist | Release/announcement with no game-specific evidence yet | Worth testing; no game-performance conclusion |

Evidence grade measures **verifiability**, not importance. A commercially important product can still be Grade E.

---

## 2. A practical map of “AI game development”

The field is easier to understand as a production pipeline than as a list of model names.

| Stage | What an AI system must do | Representative 2026 work | Main unresolved issue |
|---|---|---|---|
| Requirement and game design | Convert intent into mechanics, rules, content, and acceptance criteria | GameCraft-Bench, MAGE, CreativeGame | Specifications underdetermine a good game |
| Project architecture | Choose scenes, components, state, files, and dependencies | OpenGame, JAMER, AutoUE | Long-horizon cross-file coherence |
| Engine implementation | Correctly use Godot/UE/Unity/Phaser APIs and assets | GameDevBench, AutoUE, OpenGame | API/tool hallucination and scene wiring |
| Visual and asset integration | Select, place, render, and edit multimodal assets | GameDevBench, CubePart, GameUIAgent | Visual correctness is difficult to infer from code |
| Runtime debugging | Launch, observe errors/behavior, repair, and retry | GameDevBench, OpenGame | Reliable perception-action feedback loops |
| Playtesting and verification | Reach relevant states and test mechanics | GameGen-Verifier, Play2Code, GBQA | Open-ended play is slow and coverage-limited |
| Balancing and refinement | Change rules/content based on observed play | RuleSmith, Play2Code | Simulated players are not human players |
| Experience quality | Judge completeness, clarity, pacing, coherence, and fun | GameCraft-Bench, WebGameBench | Subjective, long-horizon, and player-dependent |

### A second axis: AI builds the game versus AI is the game

[AI Native Games: A Survey and Roadmap](https://arxiv.org/abs/2607.00527) manually screened 93 candidates and retained 53 public AI-native games/prototypes after checking available builds or demos. Its useful counterfactual is: **if runtime generative AI were removed, would the core gameplay collapse or fundamentally change?**

That separates two orthogonal questions:

- **Production-side AI:** can an agent help developers design, implement, test, and maintain a game? This report's main focus.
- **Runtime AI-native gameplay:** is generative AI part of the shipped core loop, rather than only a development tool?

The survey's broader lesson also applies to development: stable AI-native experiences usually combine models with authored state, explicit rules, validators, constraints, and fallbacks. Unrestricted generation alone does not create a coherent gameplay loop.

### The capability ladder

Use this ladder when comparing papers or answering an interviewer:

1. **Code validity** — Is the syntax/API usage valid?
2. **Build health** — Does the project compile or export?
3. **Launchability** — Does it start without crashing?
4. **Visual usability** — Is the output visible and legible?
5. **Local interaction** — Do controls and individual mechanics work?
6. **State and requirement coverage** — Can the evaluator reach and verify the required states?
7. **Game completeness** — Is there enough content, feedback, progression, and presentation?
8. **Player experience** — Is it coherent, balanced, engaging, and maintainable?

No current benchmark covers this entire ladder perfectly. That is why scores from different benchmarks must not be merged into one global leaderboard.

---

## 3. Core 2026 benchmarks and evaluation work

### 3.1 Comparison table

| Work | Date | Setting and task unit | Evaluation | Headline result | Grade | Most important caveat | Links |
|---|---:|---|---|---|---|---|---|
| **GameDevBench v2** | Feb; v2 Jun 30 | 333 localized Godot development tasks from tutorials | Deterministic Godot tests; optional screenshot/video feedback | Gemini 3 Pro + screenshot/video **53.8%**; GPT-5.4 **41.1% → 52.0%** with visual feedback | A | Edits existing projects; not whole-game generation or holistic playability | [arXiv v2](https://arxiv.org/html/2602.11103v2) · [HF](https://huggingface.co/papers/2602.11103) · [code](https://github.com/waynchi/gamedevbench) |
| **GameCraft-Bench** | Jun 16 | 140 prompt-to-complete-game Godot tasks across 15 families | Full artifact, submitted play trace, replay, rubric-guided multimodal judgment | Claude Code + Opus 4.7 **41.46%**; Codex + GPT-5.5 **39.49%** | A | Demonstration- and judge-dependent; benchmark is intentionally much broader than patch tasks | [arXiv](https://arxiv.org/html/2606.17861) · [HF](https://huggingface.co/papers/2606.17861) · [project](https://tongxuluo.github.io/gamecraft-bench-website/) |
| **OpenGame-Bench** | Apr 20 | 150 natural-language prompts to complete Phaser 3 web games, 5 genres | Build Health, Visual Usability, Intent Alignment | OpenGame + Sonnet 4.6: **72.4 / 67.2 / 65.1** | A | Web/Phaser setting; no unrestricted human playthrough; VLM-based parts of evaluation | [arXiv](https://arxiv.org/html/2604.18394) · [HF](https://huggingface.co/papers/2604.18394) · [code](https://github.com/leigest519/OpenGame) |
| **WebGameBench** | May | 111 browser-native game tasks; 12 coding agents, 14 configurations | Real browser runtime evaluator; Excellent / Usable / Unusable; human validation | Opus 4.7: **20.2% Excellent**, **76.9% Usable** | C | Browser games rather than professional engines; public evaluation repository was not verified; evaluator can itself fail | [arXiv](https://arxiv.org/html/2605.17637) · [HF](https://huggingface.co/papers/2605.17637) |
| **PlaytestArena / Play2Code** | May 27 | 200 browser-game tasks across 8 genres | A GUI agent plays the generated game; generation–playtesting loop with shared memory | Play2Code average **66.8**, reported **+37.1** over single pass | C | A playtester only detects states it can reach; full code/data release was not verified | [arXiv](https://arxiv.org/html/2605.28258) · [project](https://continual-game-generation.vercel.app/) |
| **GameGen-Verifier / VeriGame** | May 8 | 100 generated web games across 7 genres | Extract keypoints, inject target runtime state, perform bounded interaction, verify in parallel | GPT-5.4 verifier: **92.2% Acc@5**, **95.4% F1@5**; up to **16.6×** faster | C | White-box runtime patching; release is described as pending acceptance; sparse assertions do not measure holistic fun or polish | [arXiv](https://arxiv.org/html/2605.07442) · [HF](https://huggingface.co/papers/2605.07442) |
| **PlayEval / PlayCoder** | Apr 21 | 43 multilingual GUI applications in 6 categories, including games; 2,104 tests | Compile/execute plus Play@3 interaction checks | Closed loop reaches up to **38.1 Exec@3** and **20.3 Play@3** | A | Mixed GUI apps rather than game-only; existing-repository modification rather than from-scratch creation | [arXiv](https://arxiv.org/html/2604.19742) · [code](https://github.com/Tencent/PlayCoder) |
| **JAMER / JamBench** | Jun 18 | 8,133 verified Godot projects; 300 benchmark + 7,833 training projects | File, compile, runtime behavior; from-scratch themes and multigranularity completion | Runtime success drops from **80.4%** on small tasks to **5.7%** on large Task 2a projects | A | Behavioral similarity and deterministic checks do not capture subjective experience quality | [arXiv](https://arxiv.org/html/2606.19830) · [HF](https://huggingface.co/papers/2606.19830) |
| **GBQA** | Apr 3 | 30 lightweight web games with 124 human-verified implanted bugs | QA agents explore and report bugs through structured backend actions | Best reported model detects **48.39%** of bugs | C | Synthetic games/bugs; semantic backend actions are easier than unrestricted visual interaction | [arXiv](https://arxiv.org/html/2604.02648) · [HF](https://huggingface.co/papers/2604.02648) |
| **WorldCoder-Bench** | Jun 1 | 2,026 Three.js physically grounded interactive-world tasks | Hidden state-transition contracts through StateProbe; core and robust coverage | GPT-5.4 V-Cov **27.8 Core / 19.9 Robust** | A | Interactive 3D worlds, not full games; state contracts omit broader design quality | [arXiv](https://arxiv.org/html/2606.01869) · [HF](https://huggingface.co/papers/2606.01869) |

### 3.2 What each benchmark actually tells us

#### GameDevBench v2: multimodal engine editing

- **333 Godot 4 tasks**: 33.3% 2D graphics/animation, 26.7% 3D graphics/animation, 20.1% UI, and 19.8% gameplay logic.
- A reference solution changes an average of **4.7 files and 114 lines across 3.2 file types**.
- Average success is **51.4% on gameplay-oriented tasks versus 33.0% on 2D graphics tasks**.
- The benchmark's strongest insight is causal and actionable: a runtime observation channel improves results. It supports the claim that game-development agents need an engine feedback loop, not just better code completion.
- Use the **v2/camera-ready figures**. Do not copy the earlier 132-task and 54.5% figures from the initial abstract/HF summary without a version label.

#### GameCraft-Bench: end-to-end artifact and interaction

- **140 tasks across 15 game families** ask an agent to create a complete Godot game from a natural-language request.
- It formalizes three requirements: **engine grounding, artifact completeness, and interactive verification**.
- Reported overall scores:

| Agent configuration | Overall | Mechanics | Depth | Visuals | Art |
|---|---:|---:|---:|---:|---:|
| Claude Code + Opus 4.7 | 41.46 | 55.34 | 39.48 | 42.78 | 36.86 |
| Codex + GPT-5.5 | 39.49 | 54.36 | 38.61 | 41.84 | 32.94 |
| Kimi Code + K2.6 | 30.65 | — | — | — | — |
| MiMo V2.5 Pro | 24.10 | — | — | — | — |
| GLM 5.1 | 18.29 | — | — | — | — |
| MiniMax M2.7 | 10.95 | — | — | — | — |
| DeepSeek V4 Pro | 2.15 | — | — | — | — |

The key pattern is more important than the ranking: **mechanics are materially stronger than depth, art, and complete presentation**. Agents can often produce a recognizable prototype without producing a complete game experience.

#### OpenGame: scaffolding changes the result

- OpenGame combines a specialized model, project templates, a reusable debug protocol, build tests, and iterative repair.
- Its 150-task benchmark separates **Build Health**, **Visual Usability**, and **Intent Alignment**, avoiding the false equivalence between “launches” and “matches the request.”
- Removing hook-driven implementation reduces Build Health by **10.1 points** and Intent Alignment by **11.6 points**; simpler reading/scaffolding ablations also reduce alignment.
- Gains flatten around the third repair iteration, suggesting that repeated retries without better diagnosis have diminishing returns.
- This is strong evidence that the operational unit is **model + agent + tools + scaffold + budget**, not the model alone.

#### WebGameBench: usable is not excellent

- The best reported configuration generates a high proportion of games judged usable, but only around one fifth are excellent.
- Harder pooled tasks remain very weak; a high “coverage” or “launch” rate should not be translated into high-quality game creation.
- Its browser evaluator reaches approximately **85.0% binary usability accuracy / 82.9 macro-F1** against humans at the strongest setting, but exact three-way agreement is much lower. Automated evaluators need evaluation too.

#### Play2Code versus GameGen-Verifier: two verification philosophies

- **Play2Code** uses a player-like GUI agent. It is natural and non-invasive, but bounded by exploration skill and state reachability.
- **GameGen-Verifier** decomposes requirements, injects the runtime into target states, and checks bounded interactions. It is faster and has broader mechanical coverage, but is invasive and may miss emergent experience problems.
- A promising future evaluator is likely hybrid: natural play for experience plus state-directed tests for mechanics and edge cases.

#### JAMER: project scale is still the cliff

- JAMER mines more than 240,000 candidate projects to produce **8,133 verified Godot projects**.
- Code agents can improve compilation, yet success falls dramatically as project scope grows.
- This suggests the main bottleneck is moving from local code correctness to **architecture and dependency management across a project**.

---

## 4. 2026 systems that build or modify games

| System | Scope | Output | Evaluation / evidence | Grade | Why it matters | Limitation | Links |
|---|---|---|---|---|---|---|---|
| **OpenGame** | End-to-end Phaser 3 game generation | Editable multi-file web game with code/assets | OpenGame-Bench, public code | A | Best example of an open agent framework plus benchmark | Easier textual/web engine boundary than UE/Unity/Godot | [paper](https://arxiv.org/html/2604.18394) · [GitHub](https://github.com/leigest519/OpenGame) |
| **AutoUE** | Natural language to 3D UE5 prototype | Editable UE scene/project, retrieved models, C++ gameplay, interactions | PlayGen-20; self-reported 8.68/10 overall | C | Covers asset retrieval, PCG scene construction, gameplay code, and MCP runtime testing in a commercial engine | Only 20 self-built tasks; largely LLM-judged; code availability unclear | [paper v2](https://arxiv.org/html/2603.07106v2) |
| **Cutscene Agent** | Unreal Engine dialogue/cinematic production | Native editable Level Sequence with characters, cameras, dialogue, sound | CutsceneBench: 65 scenarios, 5 tiers, 8 LLMs | C | A realistic production subworkflow with bidirectional engine state and 60+ tools | Focuses on dialogue cutscenes; action choreography/crowds remain uncovered | [paper](https://arxiv.org/html/2604.25318) · [project](https://kuaishou-gamemind.github.io/cutscene_agent/) |
| **CreativeGame** | Iterative HTML5 game lineages | Runnable HTML5 games with mechanic plans and version ancestry | 71 lineages, 88 nodes, 774 mechanics; qualitative lineage study | C | Treats game generation as open-ended iteration rather than one-shot prompting | No strong aggregate success benchmark; public-code status unclear | [paper](https://arxiv.org/abs/2604.19926) |
| **MAGE** | Unity goal-playable pattern synthesis | Direct C# or structured IR to Unity implementation | 858 attempts, 26 concepts, 4 open models | C | Separates compile/runtime success from mechanism fidelity | Small concept set; not a frontier product-agent evaluation | [paper](https://arxiv.org/abs/2605.07342) |
| **GameUIAgent** | Natural language to game UI designs | Editable Figma designs through Design Spec JSON | 110 cases, 3 LLMs, 3 templates | C | Shows value of structured intermediate representations in a production subtask | UI layouts rather than complete games; VLM evaluation sensitivity | [paper](https://arxiv.org/html/2603.14724) · [code](https://github.com/zengwei-code/GameUIAgent) |
| **CubePart** | Game-ready multipart 3D assets | Separately controllable meshes assembled into a coherent object | Paper plus public Roblox code/weights | B/C | Produces parts that can receive animation, physics, and scripts, not only a static mesh | Asset layer only; does not create game logic; license is not equivalent to an unrestricted OSI license | [paper](https://arxiv.org/abs/2605.28763) · [code](https://github.com/Roblox/cube) |
| **GamED.AI** | Educational game generation | Playable games from question sets using 15 mechanics and 2 template families | 200 questions; 90% validation pass; 98.3% schema compliance | C | Demonstrates that constrained generation can be cheap and reliable | Highly templated educational niche; cannot generalize to open game creation | [paper](https://arxiv.org/abs/2604.23947) |

### AutoUE results should be presented cautiously

AutoUE reports Scene **9.90**, Gameplay **8.25**, Visual **7.78**, and overall Game **8.68** on its 20-task PlayGen-20 setup. These numbers are useful as an existence proof for an Unreal-native workflow, but they are not comparable to GameCraft-Bench percentages. The sample is small, the benchmark is built with the system, and much of the judgment is model-based.

### MAGE exposes the compile–mechanics gap

Across its Unity concept-generation experiments, direct natural-language-to-C# generation can reach roughly **43% mean runtime success** while mechanism adherence remains around **0.12 F1**. A structured intermediate representation can improve mechanism fidelity substantially, sometimes up to 1.0 in narrow settings, but may reduce runtime robustness. This is another instance of the central tradeoff: syntactic executability and semantic game correctness are different objectives.

---

## 5. Automated playtesting, QA, balancing, and design understanding

| Work | Development role | Core idea | Evidence | Grade | Caveat | Links |
|---|---|---|---|---|---|---|
| **GameGen-Verifier** | Mechanical verification | Decompose specs into keypoints, inject states, test interactions in parallel | 100 games, human labels; 92.2% Acc@5 | A | White-box, web-only experiments; not fun/polish | [paper](https://arxiv.org/html/2605.07442) |
| **Play2Code** | Playtest-and-repair loop | GUI agent plays, records failures, and shares memory with coding agent | 200 tasks; large gains over single pass | A/C | Reachability and player-agent biases | [paper](https://arxiv.org/html/2605.28258) |
| **GBQA** | Bug finding | Hierarchical builder plus QA agent; controlled implanted bugs | 124 bugs; best detection 48.39% | C | Synthetic bugs and structured actions | [paper](https://arxiv.org/html/2604.02648) |
| **RuleSmith** | Automated balancing | LLM self-play evaluates rules; Bayesian optimization searches 12 parameters | CivMini can reach near 50/50 win rates; public code | C | One simplified deterministic strategy game; balance transfers poorly when player models differ | [paper](https://arxiv.org/html/2602.06232) · [code](https://github.com/Adonis-galaxy/RuleSmith) |
| **From Gameplay Traces to Game Mechanics** | Mechanics reverse engineering | Infer a causal model from traces, then translate it into VGDL | 9 GVGAI games; SCM approach up to 81% blind preference win rate | C | Very small symbolic-game setting; not modern engine development | [paper](https://arxiv.org/abs/2602.00190) |
| **CA2: Code-Aware Agent for Automated Game Testing** | Code-aware exploration | Uses call-stack observations and offline RL to reach target functions | 56% success in Crafter and 47% in a Godot environment | C | Not a frontier LLM; only two instrumented environments; depends on source profiling and offline human trajectories | [paper](https://arxiv.org/html/2605.13918) |
| **RAID: Reward-Adaptive Iterative Discovery** | Commercial-game exploit discovery | Iterative SAC populations and reward masking search for diverse scoring strategies | In pre-release NHL 26 goalie testing, one run found 6 strategies similar to hours of human testing; later runs found 8 additional patterns | C/D | One proprietary game/scenario; human interpretation is still needed; code/data closed | [paper](https://arxiv.org/html/2607.07498) · [EA video](https://go.ea.com/RAID) |

RuleSmith contains a particularly useful warning for industry discussion: a ruleset balanced for one pair of simulated player models is not necessarily balanced for stronger, weaker, or differently biased players. Automated balancing needs a **population of player models** and ultimately human validation.

---

## 6. Frontier models: benchmark lag and field evidence

### 6.1 Evidence status at the cutoff

| Frontier model/system | Game-specific standardized evaluation found? | Strongest relevant public signal found | Classification | Safe conclusion |
|---|---|---|---|---|
| **Claude/Fable (exact version unspecified)** | **No** verified 2026 game-dev benchmark result found by the cutoff | Public Command & Conquer: Generals — Zero Hour fork extending an existing macOS/Linux community port to iOS/iPadOS, with an engineering record describing Fable-assisted C++/build/debug work and human direction/playtesting | B | Evidence for human-directed, long-horizon game-engineering work; not autonomous game generation, a model comparison, or evidence for Fable 5 specifically |
| **GPT-5.6 family** | No game-specific evaluation found by the cutoff | General release and coding claims only | W | Add to a model watchlist and wait for controlled game evidence |
| **GPT-5.5** | Yes in several benchmarks; no high-quality independent field case found | Official launch page includes Dungeon/3D-game showcases without source, prompt, retries, or cost | A/C for named benchmarks; E for showcase | Cite benchmark results, not the showcase, when making a performance claim |
| **Claude Opus 4.8** | No controlled game-development result found | Only an uncontrolled failure comparison reported by the C&C-port author | W | Insufficient evidence for comparison with the unspecified Fable version used in the artifact |
| **Gemini 3.5 family and Kimi K2.6** | No independently reproducible game-dev field case found in this search | Releases, benchmark appearances for some earlier/configured variants, and scattered demos | W | Do not infer game capability from general SWE results alone |
| **Opus 4.7, GPT-5.5, GPT-5.4, Gemini 3 Pro** | Yes, in one or more 2026 game benchmarks | GameCraft-Bench, GameDevBench, WebGameBench, OpenGame-related studies | A/C | Discuss only with the exact agent harness and benchmark attached |

“No evaluation found” means no sufficiently specific and inspectable evidence was found during this survey; it is not proof that no private test or unindexed post exists.

### 6.2 Claude Code/Fable case study: what it proves and what it does not

The public repository [Generals-Mac-iOS-iPad](https://github.com/ammaarreshi/Generals-Mac-iOS-iPad) is an inspectable game-development signal for Claude Code/Fable. The repository does not identify the exact Fable version, so it must not be attributed to Fable 5 without an additional primary source.

The fork extends prior community macOS/Linux porting work to iOS and iPadOS. It adds iOS cross-build support, touch controls, lifecycle handling, packaging, and engine fixes. The repository documents concrete bugs such as a black minimap and broken audio state. Its author explicitly describes the process as **human + AI collaboration**: Claude Code/Fable assisted with C++ engineering and debugging, while the human directed the work, tested on devices, supplied perceptual observations, and owned decisions.

Important controls on the claim:

- It builds on EA's released source and several prior community ports; it is not a from-scratch game.
- Human playtesting is essential because the model cannot directly hear an audio artifact or independently validate all device behavior.
- A single successful project provides no pass rate, variance, or fair comparison with other models.
- It is evidence for **repository-scale porting and debugging**, which is valuable and different from prompt-to-game generation.
- The fork adds roughly 2,200 lines over GeneralsX; campaign, skirmish, and Generals Challenge work, while multiplayer does not.
- Known issues include high long-session memory use and occasional background/resume crashes.
- The repository does not publish the full Claude session, every prompt, or exact token telemetry. Secondary estimates of cost should not be presented as measured API cost.

Safe interview wording:

> “Claude Code/Fable has not yet appeared in the game-specific benchmarks I could verify, but there is a public field case: a human-directed extension of an existing Command & Conquer macOS/Linux community port to iOS and iPadOS. The repository does not identify the exact Fable version. I treat it as evidence of long-horizon engineering assistance, not as proof that a particular Fable version can autonomously build a complete game.”

### 6.3 Two useful adjacent cases

#### Claude-generated NES emulator, exact model unspecified

The public [NES repository](https://github.com/willtobyte/NES) and its [community testing discussion](https://news.ycombinator.com/item?id=46443767) provide a runnable browser artifact, but the author did not identify an exact Claude version or publish the full process. Testers reported major performance differences from mature emulators, missing sound or controls in some environments, and no standard accuracy-suite result. Emulator implementations are also common in public training data.

Its safe use is as a cautionary example:

> **Functional does not imply performant, accurate, uncontaminated, or production-ready.**

It should not be attached to Opus, Fable, or any other named model.

#### Opus 4.7 reproducing a Connect Four AlphaZero pipeline

[This controlled study](https://arxiv.org/abs/2604.25067) runs four coding agents eight times each with three-hour budgets and releases code, data, and prompts. Opus 4.7 produces a Connect Four agent that, as first player, beats an external solver in 7 of 8 runs. This is good evidence for autonomous game-related ML engineering, but it does **not** test game-engine use, assets, game design, or playability. Place it under `Adjacent Evaluations`, not end-to-end game development.

### 6.4 Recommended field-report schema

Every community/blog entry should record:

```yaml
title: ""
date: YYYY-MM-DD
model: "exact model/version"
agent_or_tool: ""
engine_or_stack: "Godot | Unity | Unreal | Phaser | custom | ..."
task: ""
starting_point: "from scratch | template | existing repository | port"
human_role: "prompting, assets, design, playtesting, code edits, etc."
budget:
  time: ""
  tokens_or_cost: "unknown"
artifacts:
  repository: ""
  build_or_demo: ""
  logs_or_prompts: ""
outcome:
  succeeded: ""
  failed: ""
evidence_grade: "B | D | E | W"
caveat: ""
```

This prevents a polished demo video from being treated as equivalent to an executable artifact or benchmark.

---

## 7. Generated worlds: important, but adjacent

The phrase “world model” now hides several different outputs. For game development, the artifact type is more informative than the marketing name.

| Artifact class | Output | Inspect/edit/version/test? | What “playable” can mean | Examples |
|---|---|---|---|---|
| **Engine/code-native game** | Scenes, components, scripts, assets, rules, build project | Yes, through normal software and engine workflows | Explicit mechanics and game state execute correctly | GameCraft, OpenGame, AutoUE |
| **Persistent structured 3D world** | Meshes, Gaussian splats, camera/geometry, sometimes collision | Partly; can often be exported or inserted into tools | A navigable environment asset exists, but gameplay must still be authored | HY-World 2.0, Marble, Lyra 2.0 |
| **Neural pixel world** | Action-conditioned video frames | Usually no explicit objects, scripts, or durable symbolic state | Inputs produce responsive visual continuation for some duration | Genie 3, Matrix-Game, LingBot-World |

This distinction is not merely semantic. World Labs' 2026 [“3D as code”](https://www.worldlabs.ai/blog/3d-as-code) argument emphasizes that pure pixel streams entangle state, rules, and rendering and are difficult to inspect, edit, share, version, or test. Its later [taxonomy](https://www.worldlabs.ai/blog/taxonomy-of-world-models) distinguishes renderers, simulators, and planners. The useful game-dev conclusion is:

> **Responsive pixels are not the same as an editable, state-consistent game; a persistent 3D world is closer to an engine asset, but still lacks gameplay rules.**

### 7.1 Persistent structured 3D worlds

| Work / product | 2026 signal | Output and relevance | Availability | Main caveat | Links |
|---|---:|---|---|---|---|
| **World Labs Marble + World API** | Public API Jan 21 | Text/images/panorama/video to a navigable 3D world; can export Gaussian splats, meshes, video, and collision mesh for downstream tools | Closed commercial API | Produces an environment, not mechanics, quests, or a complete game; no public benchmark/code | [API announcement](https://www.worldlabs.ai/blog/announcing-the-world-api) · [3D as code](https://www.worldlabs.ai/blog/3d-as-code) |
| **HY-World 2.0** | Apr 15; pipeline update May 18 | Text/image to navigable 3DGS/mesh; reconstruction from images/video; exports into Unity, UE, Blender, and Isaac with collision-aware exploration | Source-available inference code and multiple weights | Full generation is compute-heavy; Tencent community license has geographic/commercial restrictions; no gameplay logic | [paper](https://arxiv.org/html/2604.14268) · [code](https://github.com/Tencent-Hunyuan/HY-World-2.0) · [models](https://huggingface.co/tencent/HY-World-2.0) |
| **Lyra 2.0** | Apr 14 | Image plus camera path to long video and then 3DGS/mesh, potentially exportable to physics/simulation tools | Official page says weights/inference released, but the actual repository was not verified at cutoff | Availability uncertain; primarily camera/world generation rather than gameplay | [paper](https://arxiv.org/html/2604.13036) · [project](https://research.nvidia.com/labs/sil/projects/lyra2/) |

### 7.2 Neural pixel worlds and research infrastructure

| Work / product | 2026 signal | Headline capability | Availability | Main caveat | Links |
|---|---:|---|---|---|---|
| **Project Genie / Genie 3 access** | Jan 29 product access; underlying model announced 2025 | Text/image to navigable generated worlds; official model claim 720p, 24 FPS, minutes-long consistency | Closed product | No exportable game project; limited actions/duration; field tests report lag, weak objectives, and consistency failures | [product](https://labs.google/projectgenie) · [technical post](https://deepmind.google/blog/genie-3-a-new-frontier-for-world-models/) · [hands-on](https://www.theverge.com/news/869726/google-ai-project-genie-3-world-model-hands-on) |
| **LingBot-World 1.0** | Jan 28 | Minute-level interactive generation, sub-second latency, reported 16 FPS | Open research release | Generated-video interaction is not explicit game logic | [paper](https://arxiv.org/abs/2601.20540) |
| **Infinite-World** | Feb 2 | Pose-free long-memory rollout beyond 1,000 frames | Research release | Long-horizon generation research, not a game creator | [paper](https://arxiv.org/abs/2602.02393) |
| **WorldCompass** | Feb 9 | RL post-training for interaction and visual quality | Research release | Optimizes a pixel world, not a game artifact | [paper](https://arxiv.org/abs/2602.09022) |
| **Matrix-Game 3.0** | Apr 10 | 5B model reports 720p up to 40 FPS and minute-level memory | Apache-2.0 code and selected 5B weights | Peak 40 FPS setup uses 8 GPUs for DiT plus 1 for VAE; larger/other variants are not all released | [paper](https://arxiv.org/abs/2604.08995) · [project](https://matrix-game-v3.github.io/) · [code](https://github.com/SkyworkAI/Matrix-Game/tree/main/Matrix-Game-3) |
| **SANA-WM** | May 14 | 2.6B camera-controllable model for up to one-minute 720p video | Apache code/weights and training components | Primarily camera traversal; training reported at 64 H100s for 15 days | [paper](https://arxiv.org/html/2605.15178) · [code](https://github.com/NVlabs/Sana) |
| **minWM** | May 28 | Full-stack recipe converting Wan/Hunyuan video models into real-time camera-controllable worlds | Open scripts, checkpoints, docs, and inference | Infrastructure rather than a complete game system | [paper](https://arxiv.org/html/2605.30263) · [code](https://github.com/shengshu-ai/minWM) |
| **Gamma-World** | May 27 | Synchronized multi-agent views/actions in a shared generated video world; reported zero-shot 2-to-4-player scaling | Apache-2.0 training/inference pipeline | Multiplayer simulator research; no game artifact or explicit rule state | [paper](https://arxiv.org/abs/2605.28816) · [code](https://github.com/nv-tlabs/Gamma-World) |
| **BiWM** | Jun 8 | Bidirectional autoregressive full-stack recipe over several backbones | Apache code/data pipeline; some backbones/stages pending and no universal final checkpoint | Training remains expensive and users may need to train their own model | [paper](https://arxiv.org/html/2606.10135) · [code](https://github.com/LynnReal-AI/BiWM) |
| **ActWorld** | Jun 16 | Action-aware memory trained on 100K interaction videos | Research release | Supports object actions such as pickup/open-door, but still outputs video rather than game state/code/assets | [paper](https://arxiv.org/abs/2606.17730) |
| **DreamX-World 1.0** | Jun 15 | Prompt events, camera revisits, and reported real-time interactive video | Research release | Up to 16 FPS reportedly needs 8×RTX 5090; self-built short evaluation, no independent playability evidence | [paper](https://arxiv.org/abs/2606.16993) |
| **Multiplayer Interactive World Models** | Jul 6 | 5B Rocket League model produces four synchronized player views; reported 20 FPS on one B200 | Paper claims code/data/demo release | Single-game neural simulator; public release link was not verified at cutoff | [paper](https://arxiv.org/abs/2607.05352) |
| **AlayaWorld** | Jul 7 | 15B, 720p/24 FPS claims; navigation, combat, spells, and prompt events | **Upcoming at cutoff**: repository contained README/assets and a release roadmap, not the promised full stack | Official qualitative demos only; independent reproduction unavailable | [paper](https://arxiv.org/html/2607.06291) · [project](https://alaya-lab.github.io/AlayaWorld/) · [repo](https://github.com/AlayaLab/AlayaWorld) |
| **LingBot-World 2.0** | Jul 8 | Paper claims 720p/60 FPS, unbounded horizon, attack/archery/spells, director and pilot agents | 14B causal-fast weights and offline code released; deployment code and several variants remain pending | Public quickstart is 480p/8-GPU, so the 60-FPS headline is not an open reproduction result | [paper](https://arxiv.org/html/2607.07534) · [code](https://github.com/robbyant/lingbot-world-v2) · [model](https://huggingface.co/robbyant/lingbot-world-v2-14b-causal-fast) |

### Project Genie is the clearest reality check

Official Genie 3 material emphasizes 720p/24 FPS, a few minutes of interaction, and roughly one minute of visual memory, while also acknowledging limited action space, multi-agent interaction limits, and limited duration. A public hands-on report found recognizable scenes but also input lag, a 60-second product limit, no meaningful objectives, control failures, and moment-to-moment inconsistency.

This is not a contradiction. It illustrates why the repository needs both **official capability claims** and **field reports**. The fair interpretation is that world models are advancing quickly as interactive media, but they do not yet provide the controllable, editable, testable structure expected from a game engine.

---

## 8. Industry and product signals

| Signal | Date | What happened | Evidence grade | Interpretation | Link |
|---|---:|---|---|---|---|
| **Roblox 4D Creation public beta** | Feb 4 | Natural-language generation of structured, functional in-game objects; examples include cars with separate wheels, doors, driving, and physics | E | Strong engine-native product signal, but currently constrained to a small number of schemas rather than complete games | [official](https://about.roblox.com/newsroom/2026/02/accelerating-creation-powered-roblox-cube-foundation-model) |
| **Roblox CubePart** | May 27 | Open research/model work for coherent multipart, game-ready assets | B/C | Industry is moving from static mesh generation toward assets with controllable part structure | [paper](https://arxiv.org/abs/2605.28763) · [code](https://github.com/Roblox/cube) |
| **Project Genie opened to users** | Jan 29 | A previously limited world model became a consumer-accessible experiment | E/D | Useful frontier signal, but hands-on evidence reinforces “world model ≠ game engine” | [product](https://labs.google/projectgenie) · [hands-on](https://www.theverge.com/news/869726/google-ai-project-genie-3-world-model-hands-on) |
| **Godot contribution-policy change** | Jun 30 | Godot announced no autonomous AI-agent/vibe-coded contributions and requires accountable human-authored substantial code | E, first-party policy | Generation cost can fall while review, ownership, and maintenance costs rise; production acceptance is a separate evaluation axis | [official](https://godotengine.org/article/contribution-policy-2026/) |
| **Unity AI Open Beta** | May 5 | Unity 6+ project-aware Assistant with Ask/Plan/Agent modes, editor actions, code/scene/prefab changes and validation; AI Gateway for third-party models; official MCP server | E | A real engine-integrated product, but Unity discloses no auditable public task set, protocol, or benchmark result; it does not prove stable one-prompt full-game generation | [launch](https://unity.com/blog/unity-ai-how-to-get-started) · [product](https://unity.com/features/ai) |
| **Unreal MCP in UE 5.8** | Public docs verified Jun 23 | Experimental MCP server embedded in the Editor; external agents can inspect editor state, spawn actors, adjust lighting/materials, modify scripts, and run automation tests | E | An official agent tool surface, not an Epic game-generation model or benchmark; experimental, incomplete, API-changing, localhost/no-auth, and serialized on the game thread | [release notes](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-5-8-release-notes) · [docs](https://dev.epicgames.com/documentation/unreal-engine/unreal-mcp-in-unreal-editor) |
| **Square Enix QA automation target** | Background: announced Nov 2025; target through 2027 | Joint research aims to automate 70% of QA/debugging tasks by end of 2027 | W | The near-term enterprise landing point is QA/debugging, not autonomous AAA creation; keep as background because announcement predates the repo cutoff | [official PDF](https://www.hd.square-enix.com/eng/ir/pdf/20251106_01_en.pdf) |
| **GDC 2026 industry survey** | 2026 report | Among 2,300 respondents, 36% report generative-AI use; among users, 81% use it for research/brainstorming, 35% prototyping, 22% testing/debugging, 19% assets, and only 5% player-facing features | C | Actual adoption is concentrated in assistance and pre-production, not autonomous full-game delivery | [official report entry](https://reg.gdconf.com/2026-SOTI) · [public summary](https://www.theverge.com/entertainment/869386/ai-game-development-gdc-survey) |

Roblox also describes “real-time dreaming” for live environment generation, but it remains a research-stage direction without a public evaluation or committed availability date. It belongs in a watchlist, not the verified-products table.

The engine-interface comparison is now concrete: **Unity provides its own assistant, third-party-model gateway, and MCP integration in public beta; Epic provides an official experimental MCP/tool surface. Neither company publishes a reproducible game-development evaluation.** Interface availability and agent capability must therefore remain separate columns in the repo.

The Godot policy is as important as positive adoption news. It adds two dimensions missing from most academic benchmarks:

- **maintainability** — can a human team understand and safely modify the output later?
- **accountability** — who diagnoses and owns failures after the initial generation?

---

## 9. Cross-paper insights that are defensible in an interview

### Insight 1: the field is converging on interaction-grounded evaluation

GameDevBench observes the engine, GameCraft-Bench replays interaction traces, WebGameBench operates a real browser, Play2Code sends a GUI player, and GameGen-Verifier injects runtime states. Independent groups are converging on the same conclusion: **static code inspection is not enough for games**.

### Insight 2: evaluation is becoming a systems problem

A credible evaluator needs some combination of:

- build and crash detection;
- visual observation;
- input generation;
- state introspection or instrumentation;
- requirement decomposition;
- long-horizon coverage;
- human calibration of automated judgments.

The frontier is therefore not only a better coding model. It is an engine-aware development and verification stack.

### Insight 3: visual feedback is useful, but full playtesting is expensive

Screenshots/video improve engine-editing performance, yet open-ended GUI play remains slow and reachability-bound. State injection improves coverage and speed but requires instrumentation. The likely production pattern is a layered test pyramid:

1. deterministic unit/state tests;
2. targeted state injection and short interactions;
3. agentic GUI playthroughs;
4. selective human playtesting.

### Insight 4: model rankings are unstable across task definitions

A model that excels at local Godot edits may not be best at from-scratch Phaser games, Unreal tool use, browser usability, or complete Godot presentation. Agent harnesses also differ. The correct unit of comparison is:

> **model + agent implementation + tools + feedback channel + budget + benchmark version**

### Insight 5: project scale and completeness are harder than local mechanics

JAMER shows a severe scale cliff; GameCraft-Bench shows mechanics ahead of depth and art; OpenGame shows large scaffold effects. Together they indicate that frontier models often know how to implement individual mechanics but struggle to maintain a coherent architecture and complete the surrounding content and feedback.

### Insight 6: world models and game engines are on different technical paths

World models optimize perceptual continuity and action-conditioned video. Game-development agents produce explicit artifacts that can be edited, tested, versioned, and shipped. The paths may later meet—for ideation, simulation, asset generation, or learned rendering—but 2026 evidence does not justify treating one as a replacement for the other.

### Insight 7: production readiness needs a maintenance axis

Academic benchmarks mostly end after generation and testing. Godot's policy response shows that real ecosystems care about review burden, authorship, understanding, and future fixes. A mature benchmark should eventually measure not only whether an AI builds a feature, but whether another developer can safely maintain it.

---

## 10. Recommended first version of the Awesome repo

### 10.1 Positioning

Recommended name:

```text
awesome-ai-game-dev
```

Recommended subtitle:

```text
A curated frontier radar for AI-powered game development, with an emphasis on
evaluation, reproducible systems, field reports, and industry signals since 2026.
```

This is intentionally broader than “game development agents” but narrower than “all AI tools for game developers.” It gives the repository room for benchmarks, engine systems, verification, frontier-model field reports, and world-model context without becoming an asset-link dump.

### 10.2 Tier 1: include in the first public README

These entries create a coherent and interview-ready story:

1. GameDevBench v2
2. GameCraft-Bench
3. OpenGame / OpenGame-Bench
4. WebGameBench
5. PlaytestArena / Play2Code
6. GameGen-Verifier
7. JAMER / JamBench
8. AutoUE
9. Cutscene Agent
10. RuleSmith
11. RAID's commercial NHL 26 exploit-discovery case
12. Claude Code/Fable Command & Conquer iOS/iPadOS port field case
13. Roblox 4D Creation and CubePart
14. Unity AI Open Beta
15. Unreal MCP in UE 5.8
16. Project Genie official capability plus independent hands-on
17. Godot's AI-contribution policy as an industry counter-signal

This is already enough for a strong v0.1. It covers benchmarks, systems, verification, field evidence, products, and limitations without pretending to be exhaustive.

### 10.3 Tier 2: include after personal review

- PlayCoder / PlayEval
- GBQA
- WorldCoder-Bench
- MAGE and its related structural-representation work
- CreativeGame
- GameUIAgent
- GamED.AI
- From Gameplay Traces to Game Mechanics
- CA2: Code-Aware Agent for Automated Game Testing
- FactorSmith
- Large Language Models in Game Development: Implications for Gameplay, Playability, and Player Experience
- The public Claude-generated NES emulator case, as a performance/accuracy caution rather than a named-model result
- Persistent structured worlds: World Labs Marble, HY-World 2.0, and Lyra 2.0
- Selected open interactive world models: Matrix-Game 3.0, LingBot-World, minWM, BiWM, ActWorld, AlayaWorld

Tier 2 is relevant but either narrower, less reproducible, not game-only, highly constrained, or adjacent to the repo's central claim.

### 10.4 Keep out of v0.1

- Hundreds of undifferentiated asset-generation tools.
- Pre-2026 historical papers unless placed in a short “Background” section.
- Generic model release posts with no game test.
- AI NPC/chatbot products unless they address development or evaluation.
- One-shot social-media demos without inspectable evidence.
- A global model leaderboard that mixes incomparable benchmarks.

Specific date-rule exclusions for a strict “first posted in 2026” repository include V-GameGym (`2509.20136`), UniGen (`2509.26161`), Beyond Playtesting (`2512.02358`), and KLPEG (`2511.02534`). A 2026 conference appearance does not change the first-publication date. They can live in a short background page if needed.

Game-playing benchmarks such as ProxyWar, GameWorld, OmniGameArena, TowerMind, general Minecraft agents, and Atari/GVGAI player benchmarks should not enter the core list unless their agents are explicitly used for development, testing, or balancing. Likewise, the March paper on goal-playable knowledge representations (`2603.07101`) is best linked as a precursor inside the MAGE entry because it uses the same 26-pattern research line.

---

## 11. Suggested repository structure

For the first release, a single high-density README is enough. Do not create many empty directories. A sensible evolution path is:

```text
awesome-ai-game-dev/
├── README.md
├── CONTRIBUTING.md
├── data/
│   └── entries.yaml
├── papers/
│   └── 2026.md
├── field-reports/
│   └── 2026.md
└── industry/
    └── 2026.md
```

Recommended README order:

```markdown
# Awesome AI Game Dev

## Why this repository exists
## How evidence is graded
## 2026: What changed
## Benchmarks and Evaluation
### Engine Editing
### End-to-End Game Generation
### Playability and Runtime Evaluation
## Game Development Agents and Systems
### Godot
### Unreal Engine
### Unity
### Web Engines
## Automated Playtesting, QA, and Balancing
## Frontier Model Field Reports
## Industry and Product Signals
## Interactive World Models (Adjacent)
## Open Problems
## Contributing
```

### Entry format for README

```markdown
- **[Project or Paper](URL)** — `2026-06` `Godot` `Benchmark` `Open Source` `Evidence A`
  - **Measures:** 140 end-to-end game-generation tasks across 15 families.
  - **Verification:** Replayed demonstrations plus rubric-guided multimodal judgment.
  - **Signal:** Best agent reaches 41.46%; mechanics exceed depth and presentation.
  - **Caveat:** Scores are benchmark- and harness-specific; do not compare directly with patch-task pass rates.
```

### Machine-readable entry schema

```yaml
- id: gamecraft-bench-2026
  title: "GameCraft-Bench"
  date: "2026-06-16"
  category:
    - benchmark
    - end-to-end-generation
    - playability-evaluation
  engine: Godot
  task_scope: complete-game
  input: natural-language game request
  output: editable complete project
  evaluation:
    build_check: true
    runtime_check: true
    visual_check: true
    interactive_playtest: true
    human_calibrated: true
  evidence_grade: A
  open_source: true
  links:
    paper: "https://arxiv.org/abs/2606.17861"
    huggingface: "https://huggingface.co/papers/2606.17861"
    project: "https://tongxuluo.github.io/gamecraft-bench-website/"
  headline_result: "Best evaluated agent: 41.46% overall."
  caveat: "Interaction- and judge-dependent; not comparable to localized edit benchmarks."
  last_verified: "2026-07-13"
```

---

## 12. Open problems worth putting in the README

1. **Long-horizon project coherence** — maintaining architecture, dependencies, state, and design intent over many files and iterations.
2. **Engine-native multimodal interaction** — observing editor state, runtime video, animation, physics, audio, and logs in one loop.
3. **Playtest coverage** — reaching rare states and edge cases without spending hours on open-ended play.
4. **Mechanics versus experience evaluation** — combining deterministic correctness with presentation, pacing, clarity, and fun.
5. **Evaluator reliability** — calibrating VLM/LLM judges and detecting when the evaluator, rather than the game, failed.
6. **Cost-aware generation and verification** — reporting tokens, wall time, retries, and human interventions, not only final quality.
7. **Contamination and version drift** — tracking whether public tutorial/project data appeared in training and pinning engine/model versions.
8. **Maintainability and ownership** — measuring whether generated projects can be reviewed, understood, extended, and repaired by a team.
9. **Human–agent division of labor** — identifying which tasks should be automated, supervised, or reserved for human creative judgment.
10. **World-model-to-engine transfer** — turning generated visual worlds into explicit geometry, objects, rules, and editable state.

---

## 13. Maintenance workflow after v0.1

### Weekly, 20–30 minutes

Search Hugging Face Papers and arXiv for:

```text
"game development" agent benchmark
"game generation" playable LLM
Godot agent benchmark
Unity LLM generation
Unreal Engine multi-agent generation
Phaser game coding agent
automated game playtesting LLM
game QA agent benchmark
game balancing LLM self-play
interactive world model game 2026
```

Check:

- new arXiv versions, especially changed task counts/results;
- linked GitHub repositories and release status;
- benchmark leaderboards for new frontier-model runs;
- official engine/company blogs;
- high-signal practitioner reports with repositories or logs.

### Monthly, 45–60 minutes

- Add a dated “What changed this month” note.
- Re-run links and mark unavailable code.
- Update model results only when the harness, model version, budget, and benchmark version are known.
- Promote an item from Watchlist only after game-specific evidence appears.
- Archive superseded results instead of silently overwriting them.
- Write one short synthesis insight, not just new links.

### Acceptance checklist for new entries

- [ ] Is it specifically relevant to creating or evaluating games?
- [ ] Is the date/version clear?
- [ ] Is the exact engine/runtime clear?
- [ ] What is the task unit: edit, feature, project, complete game, or generated world?
- [ ] Is the output editable and inspectable?
- [ ] Does it compile, run, and accept interaction?
- [ ] How is correctness/playability measured?
- [ ] Is there human calibration or an executable oracle?
- [ ] Is code/data/artifact available now, promised later, or closed?
- [ ] What human intervention and budget were required?
- [ ] What is the strongest safe claim?
- [ ] What is the most important caveat?

---

## 14. A 60–90 second interview answer

> “After the first interview, I started building a 2026-focused AI game-development frontier map rather than a generic tools list. I separate evidence into reproducible benchmarks, controlled systems, developer field reports, product demos, and watchlist items.
>
> The most important pattern is that evaluation is moving up a ladder: code correctness, build and launch, visual usability, interaction, requirement coverage, and finally complete player experience. GameDevBench shows that screenshot and runtime-video feedback materially improve Godot development, while GameCraft-Bench shows the strongest end-to-end agent is still only at 41.46%. So runnable is clearly not the same as playable.
>
> I also track newer models before benchmarks catch up. For example, an unspecified Claude Code/Fable version has a public Command & Conquer iOS/iPadOS port case with code and an engineering record. It is a useful signal for human-directed long-horizon engineering, but not proof of autonomous game creation or of Fable 5 specifically. My current view is that the near-term opportunity is an engine-aware loop combining generation, runtime observation, targeted verification, and human playtesting—not a one-prompt replacement for a game studio.”

中文版本：

> “一面之后，我开始系统整理 2026 年 AI Game Development 的前沿进展，但我没有把它做成一个泛泛的工具列表，而是按可复现 benchmark、研究系统、开发者实测、产品信号和 watchlist 来区分证据。
>
> 我目前最重要的观察是，行业的评价目标正在逐级上升：代码是否正确、项目能否构建和启动、画面是否正常、能否交互、是否满足需求，最后才是一个完整的玩家体验。GameDevBench 证明截图和运行视频反馈能明显提升 Agent 的 Godot 开发能力；GameCraft-Bench 里最强端到端 Agent 也只有 41.46%，所以 runnable 和 playable 之间仍然存在很大距离。
>
> 对最新模型，我会在 benchmark 之外维护 field report。例如，Claude Code/Fable 有一个公开的《命令与征服》iOS/iPadOS 移植案例，代码和工程记录可以检查，但仓库没有说明 Fable 的具体版本。这个案例是人类指导下长程工程协作的有用信号，却不能证明 Fable 5 或任何具体版本已经能自主生成完整游戏。我的判断是，短期真正有价值的是把生成、引擎运行反馈、定向验证和人工试玩组成闭环，而不是期待一个 prompt 代替整个游戏工作室。”

### Three follow-up insights to share if asked

- “The unit being evaluated should be the deployed agent system, not the base model, because tools, visual feedback, scaffolds, and retry budgets change results substantially.”
- “The best automated evaluator will probably combine state-directed mechanical tests with natural GUI play and selective human review.”
- “World models are an important adjacent frontier, but today they generate responsive pixels rather than editable, versionable game projects.”

---

## 15. Risks and wording discipline

Avoid:

```text
A particular frontier model is the best model for game development.
AI can now generate complete playable games.
Project Genie is an AI game engine.
This benchmark proves model X is better than model Y in all game tasks.
Roblox can generate full games from text.
```

Prefer:

```text
Claude Code/Fable has a public game-porting case, but the exact model version is unspecified and no standardized game benchmark result was verified.
Current agents can build recognizable prototypes, while completeness and playability remain difficult.
Project Genie is an interactive world model/product experiment, not an editable game engine.
Within this benchmark and harness, configuration X outperformed configuration Y.
Roblox 4D Creation currently generates functional objects within constrained schemas.
```

---

## 16. Full candidate inventory

### Core benchmarks and evaluation

- [GameDevBench](https://arxiv.org/abs/2602.11103)
- [GameCraft-Bench](https://arxiv.org/abs/2606.17861)
- [OpenGame / OpenGame-Bench](https://arxiv.org/abs/2604.18394)
- [WebGameBench](https://arxiv.org/abs/2605.17637)
- [GUI Agents for Continual Game Generation / PlaytestArena / Play2Code](https://arxiv.org/abs/2605.28258)
- [GameGen-Verifier](https://arxiv.org/abs/2605.07442)
- [PlayCoder / PlayEval](https://arxiv.org/abs/2604.19742)
- [JAMER / JamBench](https://arxiv.org/abs/2606.19830)
- [GBQA](https://arxiv.org/abs/2604.02648)
- [WorldCoder-Bench](https://arxiv.org/abs/2606.01869)

### Generation and production systems

- [AutoUE](https://arxiv.org/abs/2603.07106)
- [Cutscene Agent](https://arxiv.org/abs/2604.25318)
- [CreativeGame](https://arxiv.org/abs/2604.19926)
- [MAGE](https://arxiv.org/abs/2605.07342)
- [Grounding Machine Creativity in Game Design Knowledge Representations](https://arxiv.org/abs/2603.07101)
- [GameUIAgent](https://arxiv.org/abs/2603.14724)
- [CubePart](https://arxiv.org/abs/2605.28763)
- [GamED.AI](https://arxiv.org/abs/2604.23947)
- [FactorSmith](https://arxiv.org/abs/2603.20270)
- [SPINE](https://arxiv.org/abs/2605.09767)
- [SimWorld Studio](https://arxiv.org/abs/2605.09423)

### Playtesting, QA, balancing, and understanding

- [RuleSmith](https://arxiv.org/abs/2602.06232)
- [CA2: Code-Aware Agent for Automated Game Testing](https://arxiv.org/abs/2605.13918)
- [RAID: Reward-Adaptive Iterative Discovery](https://arxiv.org/abs/2607.07498)
- [From Gameplay Traces to Game Mechanics](https://arxiv.org/abs/2602.00190)
- [Large Language Models in Game Development: Implications for Gameplay, Playability, and Player Experience](https://arxiv.org/abs/2603.27896)
- [AI Native Games: A Survey and Roadmap](https://arxiv.org/abs/2607.00527)

### Adjacent interactive world models

- [HY-World 2.0](https://arxiv.org/abs/2604.14268)
- [Lyra 2.0](https://arxiv.org/abs/2604.13036)
- [LingBot-World 1.0](https://arxiv.org/abs/2601.20540)
- [Infinite-World](https://arxiv.org/abs/2602.02393)
- [WorldCompass](https://arxiv.org/abs/2602.09022)
- [Matrix-Game 3.0](https://arxiv.org/abs/2604.08995)
- [SANA-WM](https://arxiv.org/abs/2605.15178)
- [minWM](https://arxiv.org/abs/2605.30263)
- [Gamma-World](https://arxiv.org/abs/2605.28816)
- [BiWM](https://arxiv.org/abs/2606.10135)
- [ActWorld](https://arxiv.org/abs/2606.17730)
- [DreamX-World 1.0](https://arxiv.org/abs/2606.16993)
- [Multiplayer Interactive World Models with Representation Autoencoders](https://arxiv.org/abs/2607.05352)
- [AlayaWorld](https://arxiv.org/abs/2607.06291)
- [LingBot-World 2.0](https://arxiv.org/abs/2607.07534)

### Field and industry evidence

- [Claude Code/Fable-assisted Command & Conquer iOS/iPadOS port](https://github.com/ammaarreshi/Generals-Mac-iOS-iPad)
- [Claude-generated NES emulator, model version unspecified](https://github.com/willtobyte/NES)
- [World Labs Marble / World API](https://www.worldlabs.ai/blog/announcing-the-world-api)
- [Roblox 4D Creation](https://about.roblox.com/newsroom/2026/02/accelerating-creation-powered-roblox-cube-foundation-model)
- [Unity AI Open Beta](https://unity.com/blog/unity-ai-how-to-get-started)
- [Unreal MCP in UE 5.8](https://dev.epicgames.com/documentation/unreal-engine/unreal-mcp-in-unreal-editor)
- [Project Genie](https://labs.google/projectgenie)
- [Godot contribution-policy change](https://godotengine.org/article/contribution-policy-2026/)

---

## Bottom line

The first repository does not need hundreds of entries. A better v0.1 is a small, opinionated evidence map showing:

- what each system actually builds;
- which rung of the evaluation ladder it reaches;
- what evidence supports the claim;
- which frontier models have not yet been tested;
- and where the remaining gap between a demo, a runnable prototype, and a maintainable playable game lies.

That framing is sufficiently current for an interview and sufficiently structured to become a long-term research asset.

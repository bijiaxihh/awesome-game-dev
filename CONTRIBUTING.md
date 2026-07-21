# Contributing

Thank you for helping improve Awesome AI Game Dev. This repository is a
curation, not a comprehensive directory: a smaller list with clear evidence
and boundaries is more useful than an exhaustive collection.

By participating, you agree to follow the [Code of Conduct](CODE_OF_CONDUCT.md).

## Decide Where an Item Belongs

```text
Does it directly build, edit, test, verify, repair, or train agents for games?
├── Yes → Core candidate
└── No
    ├── Does it materially affect game-development research or workflows?
    │   └── Yes → Frontier & Adjacent candidate
    └── No → Out of scope
```

Core candidates belong in one of these categories:

- **Build & Edit Games** — creates or modifies game artifacts, projects,
  scenes, UI, cutscenes, or production-ready assets.
- **Test, Verify & Improve** — validates runtime behavior, playtests, finds
  bugs, repairs failures, balances rules, or discovers exploits.
- **Agents, Harnesses & Training** — provides execution harnesses, engine tool
  interfaces, feedback loops, data pipelines, or game-specific training.
- **Frontier & Adjacent Signals** — tracks official cases, field reports,
  world models, game-playing systems, products, governance, and industry
  evidence that may influence game-development research.

Generic coding-model releases, uninspectable social-media demos, generic asset
generators, and game-playing agents without a clear development or testing
connection are out of scope.

An item appears in one primary category only. Express its other properties with
two or three labels. Do not create a new category for fewer than three strong
candidates; a durable category should normally contain about five items.

## Minimum Evidence

Every main-list entry must meet all of these conditions:

1. An accessible primary source identifies the work.
2. Its exact title and relevant date or version are known.
3. Its connection to game development is direct and explainable.
4. The task, artifact, engine, or runtime is clear.
5. The description states only the strongest claim supported by the source.
6. Paper, code, data, project, and demo links are included when public.
7. Links have been opened and checked.
8. The entry does not duplicate an existing item.
9. Official cases, field reports, world models, and incomplete releases include
   a short boundary statement.
10. Work without public code or data is not described as reproducible.

Items that are relevant but fail one or more conditions should go to
[WATCHLIST.md](WATCHLIST.md), with the missing evidence and last-checked date.

## Labels and Links

Use direct, readable labels instead of an evidence score. Common labels include:

- Work type: `Benchmark`, `System`, `Dataset`, `Training`, `Official Case`,
  `Field Report`, `Survey`.
- Environment: `Godot`, `Unity`, `UE5`, `Browser`, `Three.js`.
- Function: `Generation`, `Editing`, `Verification`, `Playtesting`, `Repair`,
  `MCP`, `World Model`.

Prefer no more than three labels per entry.

The item name should link to the best primary resource in this order:

1. public source repository;
2. official project page;
3. paper;
4. official product or model announcement.

Add other resources after the description as `[Paper]`, `[Data]`, `[Demo]`, or
`[Project]`. Do not duplicate the name link, and do not use secondary media as
the primary link.

## Entry Format

Keep entries to one concise sentence plus an optional boundary:

```markdown
- [Name](https://example.com) — Explains what it builds, evaluates, or
  contributes. [Paper](https://example.com) [Data](https://example.com)
  — `Type` `Engine`
  - *Boundary: States the main reproducibility or comparison limit.*
```

Descriptions should answer: **What does it specifically build, test, or
study?** A useful structure is:

```text
Verb + task + environment + evaluation or distinguishing feature.
```

Avoid promotional language such as "groundbreaking," "powerful," or
"production-ready." Do not compare scores from incompatible benchmarks as if
they formed a single leaderboard.

## Pull Request Information

Submit one conceptual item or tightly related group per pull request. The pull
request template asks for:

```yaml
title: ""
date: YYYY-MM-DD
category: "Build & Edit | Test, Verify & Improve | Agents, Harnesses & Training | Frontier & Adjacent"
type: "Benchmark | System | Dataset | Training | Official Case | Field Report | Survey"
engine_or_runtime: ""
task: ""
primary_source: ""
paper: ""
code: ""
data: ""
demo: ""
strongest_supported_claim: ""
main_boundary: ""
```

Before submitting:

- Place the entry in the most relevant existing category.
- Use primary sources for factual claims.
- Confirm every new link resolves.
- Keep descriptions neutral and grammatically complete.
- Add an entry to [UPDATES.md](UPDATES.md) when the change materially updates
  the landscape, corrects a claim, or moves an item out of the watchlist.
- Run or review the Markdown and link checks.

Self-nominations are welcome when affiliation is disclosed. Maintainers may
edit wording, request stronger evidence, move an item to the watchlist, or
decline an entry to preserve the list's focus.

# Contributing

Thank you for helping improve Awesome AI Game Dev. The repository is intentionally curated: a smaller list with clear evidence and caveats is more useful than an exhaustive directory.

By participating, you agree to follow the [Code of Conduct](CODE_OF_CONDUCT.md).

## What Belongs Here

A proposed entry should be specifically relevant to building, editing, testing, evaluating, or materially supporting the production of games. Strong candidates include:

- Reproducible game-development benchmarks.
- Engine-aware agents and inspectable generation systems.
- Automated playtesting, QA, verification, or balancing systems.
- Public field reports with an artifact and concrete engineering details.
- Engine or industry releases that materially change agent workflows.
- Interactive world models when clearly labeled as adjacent work.

Generic coding-model releases, uninspectable social-media demos, generic asset generators, and game-playing agents with no development or testing role are out of scope.

## Evidence Requirements

Every entry should make it possible to answer:

1. What exact version and date are being discussed?
2. Which engine or runtime is used?
3. Is the task an edit, feature, project, complete game, or generated world?
4. Is the output editable and inspectable?
5. Does it build, run, and accept interaction?
6. How is correctness or playability measured?
7. What code, data, artifact, demo, or process record is public?
8. What human intervention, time, and model budget were required?
9. What is the strongest claim the evidence supports?
10. What is the most important limitation?

Evidence grades follow the definitions in [README.md](README.md#methodology-and-evidence). Grades measure verifiability, not importance.

## Entry Format

Use this compact format:

```markdown
- **[Project or Paper](URL)** — `YYYY-MM` `Engine` `Evidence A`
  - Describes what the system builds or measures and the most useful result.
  - **Caveat:** States the main limitation or comparison boundary.
```

For a practitioner report, include this information in the pull request description:

```yaml
title: ""
date: YYYY-MM-DD
model: "Exact model and version"
agent_or_tool: ""
engine_or_stack: ""
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
outcome: ""
caveat: ""
```

## Pull Requests

- Add one conceptual item or tightly related group per pull request.
- Place the entry in the most specific existing section.
- Use primary sources for factual claims and link public code when available.
- Keep descriptions concise, neutral, and grammatically complete.
- Do not infer game-development ability from general software-engineering benchmarks.
- Do not compare scores across incompatible benchmarks as if they were one leaderboard.
- Update the full survey only when the new evidence materially changes its analysis.
- Confirm all new links resolve before submitting.

Self-nominations are welcome when affiliation is disclosed and the evidence bar is met.

## Wording

Prefer bounded statements:

```text
Within this benchmark and harness, configuration X outperformed configuration Y.
The artifact demonstrates human-directed repository-scale engineering.
The product exposes an engine tool surface but has no public capability benchmark.
```

Avoid statements such as:

```text
Model X is the best model for game development.
AI can now generate complete games.
This demo proves the system is production-ready.
```

Maintainers may edit wording, request stronger evidence, move an item to the watchlist, or decline an entry to preserve the focus of the list.

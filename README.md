# Agent Tree for Codex

A personal Codex skill and four optional custom agent presets for cost-aware delegation.

The parent delegates only useful independent work, integrates the result, and completes the requested task. Small jobs stay with the parent. The package contains no game-specific data, account identifiers, or local project paths.

## Preferred routing

| Role | Model | Reasoning |
| --- | --- | --- |
| Parent: orchestration and integration | GPT-6 Astra | medium |
| Explorer: bounded investigation | GPT-5.6 Luna | max |
| Worker: implementation and affected checks | GPT-5.6 Sol | high |
| Researcher: focused source lookup | GPT-5.6 Luna | max |
| Reviewer: only for consequential unresolved concerns | GPT-6 Astra | xhigh |

Select the parent model in Codex. The skill cannot switch a running parent's model. The named child presets set both model and effort. Model availability and support for custom agent configuration depend on the host. If the host exposes model-selectable subagent tools instead of named presets, the skill describes that route too.

## Personal installation

Clone or download this repository, then:

1. Place `skills/agent-tree/` under your personal Codex skills directory (normally `~/.codex/skills/`). Respect a configured `CODEX_HOME` when applicable.
2. Place the four TOML files from `agents/` under `~/.codex/agents/`, resolving the active Codex configuration directory. Compare any existing same-name file before replacing it.
3. Start a fresh task and confirm that the skill and agent presets are available. Invoke `$agent-tree` with a concrete task, or let its narrowly scoped description enable automatic selection when appropriate.

No global `AGENTS.md`, model default, permissions configuration, or project files need to be rewritten. Availability across projects does not mean invocation or delegation on every task. The skill's UI metadata allows normal automatic selection; it does not force a team to spawn.

## Usage

Select Astra with medium reasoning for the parent task, then write:

```text
Use $agent-tree to implement this feature. Delegate only independently useful
work, integrate the results, and verify the affected behavior.
```

For a focused review:

```text
Use $agent-tree to investigate this bug and recommend the smallest fix.
This is a review-only request; do not edit files.
```

## Examples to evaluate

- Fix a label typo: parent edits locally, no children.
- Implement a feature with a separable helper and integration work: worker owns the helper; parent handles separate integration work; parent verifies the combination.
- Resolve an uncertain API behavior while implementing independent code: researcher answers that specific question using primary documentation.
- Review a money-grant race condition: optional independent reviewer examines the transaction path; parent resolves actionable findings.
- Review-only request: no worker edits, installations, or external mutations.

## Permission and verification decisions

Read-only roles are instruction boundaries. These presets deliberately omit sandbox and approval settings, so they inherit the host's effective permissions. Do not describe them as sandbox-enforced read-only agents. A separately chosen runtime restriction can strengthen that boundary, but must be checked against the actual client and live overrides.

The parent may reuse valid child test results for unchanged code while checking integration. Project-required checks remain required. Human approval remains necessary wherever the current request or environment requires it.

## Cost claims and validation

This preset follows the supplied role/model pattern. It has not been benchmarked for total cost or completion time. High reasoning effort, duplicated context, unnecessary children, and repeated reviews can erase savings from model routing. Measure representative tasks against a single-agent baseline before advertising a cost reduction.

Structural validation checks file syntax and required fields; it does not establish that every Codex client discovers these presets or that runtime delegation uses the intended model. Confirm discovery and observe actual child models in a fresh session before treating installation as verified.

## Sharing

This repository contains the reusable skill and role presets. Installation is local to each Codex environment. Cost savings are not yet benchmarked, and no open-source license has been selected.

Official configuration reference: [Codex subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents).
Design rationale: [Rethinking skills and prompts for GPT-6 Astra](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra).

---
name: agent-tree
description: Coordinate cost-aware delegation for substantial implementation, investigation, or research with independently useful subtasks. Use when parallel work can reduce elapsed time or isolate a needed specialist investigation. Skip simple edits, direct questions, and work that must proceed sequentially.
---

# Agent tree

Complete the user's task with the smallest useful team. Model routing is a preferred preset, not a claim of measured cost savings.

## Select useful work

Keep short tasks local. Delegate only a concrete, bounded assignment whose result will affect the solution, while the parent performs separate useful work. Start with one child when that is enough; do not spawn each role to fill a diagram. Respect the runtime's concurrency limit.

The parent owns scope, architecture decisions, integration, and completion. Astra at medium reasoning is the intended parent preset, selected in the host before starting the task. Do not change or pretend to change the running parent's model or reasoning level. A different parent can still use this workflow.

## Route by role

| Role | Preferred model | Reasoning | Assignment |
| --- | --- | --- | --- |
| economy-explorer | gpt-5.6-luna | max | Read the relevant code, trace a bounded path, and return evidence and uncertainties. |
| economy-worker | gpt-5.6-sol | high | Implement an owned change and run affected checks. |
| economy-researcher | gpt-5.6-luna | max | Answer a focused external or documentation question with primary sources. |
| economy-reviewer | gpt-6-astra | xhigh | Independently examine a consequential unresolved correctness or design concern. |

Use installed named presets when supported. Otherwise pass the model and reasoning explicitly through the available subagent tool. When model overrides require a fresh context, send a concise task brief instead of forking the entire conversation. Never invent unsupported tool parameters. If a preset is unavailable, continue suitable work locally and disclose the limitation; do not silently substitute a more expensive agent. Explicit user model choices take precedence.

## Brief and boundaries

Give each child the objective, relevant files or sources, accepted decisions, owned edit scope, completion evidence, and stopping condition. Request a concise result with file locations or source links, checks performed, and unresolved issues. Include context needed to avoid repeating exploration; do not send the entire repository or require unrelated document reading.

Explorer, researcher, and reviewer perform read-only work. Workers edit only their assigned files or clearly separated surfaces. Do not have concurrent writers on the same file. Children return additional work to the parent rather than spawning descendants. The parent coordinates integration after the assigned work completes.

Delegation carries only the existing task authorization. It does not authorize publishing, purchases, messages to other people, production changes, broader access, or edits during a review-only request. Keep real external decisions with the parent. These role instructions are not a replacement for runtime permission enforcement.

## Integrate and finish

Use the child's evidence, inspect material changes, and verify affected behavior and integration. Reuse valid check results for unchanged code; rerun when integration changes behavior, evidence is missing, or a failure remains. Preserve project-required checks. Do not repeat the child's full investigation merely to recreate its confidence.

Use economy-reviewer only when a consequential unresolved concern merits an independent pass or the user requests one. Give it the task, change, and relevant evidence without coaching the verdict. Do not make it a mandatory gate for routine fixes. If work loops without new evidence, narrow the question or resolve it in the parent rather than spawning equivalent attempts.

Continue authorized implementation, integration, and repairs until the requested completion criteria are met. A child finishing is not task completion. If a real decision blocks one part, complete independent authorized work and present the concrete pending decision with its impact.

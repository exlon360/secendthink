---
name: secendthink
description: Turn a user's rough request into a polished ultra prompt, then immediately carry it out. Use when the user invokes /secendthink, /st, $secendthink, or $st, or asks to use secendthink. Return only the prompt when explicitly requested. Merely discussing or editing the secendthink plugin is not an invocation.
---

# secendthink

Rewrite the supplied request into an excellent prompt, then use that prompt yourself to complete the underlying task in the same turn. The user does not need to copy, paste, or separately approve the improved prompt. Use the model already selected for the current task, whether Astra, Sol, or another model. This skill does not switch models or change the reasoning-effort setting; "ultra prompt" describes the instructions' quality and completeness.

## Find the source request

- For a leading `/secendthink`, `/st`, `$secendthink`, or `$st`, treat the text after the invocation as the source request. Treat both names identically. Also accept an explicit skill selection or a natural-language request to use secendthink.
- If no source follows, use a clearly identified request from the current conversation. If there is no clear source, ask one brief question: "What would you like me to work on?"
- Preserve useful context and corrections the user has supplied. Include enough context for the result to be reusable without copying unrelated conversation history or private details.

## Build the ultra prompt

Identify the desired outcome, audience, available inputs, explicit constraints, and requested output. Rewrite these into direct, well-organized instructions in the user's language unless they request another language.

Improve specificity where it helps: define deliverables, useful steps, output format, and observable success criteria. Keep a simple request compact; give a complex request enough structure to execute well. Add a role or examples only when they materially improve the instructions.

Preserve the user's task, chosen tools, names, numbers, budget, tone, and exclusions. Do not add mandatory features or replace their preferred approach. Distinguish suggestions or reasonable assumptions from supplied facts. Resolve missing details from available context or use reasonable assumptions when they permit useful progress. Ask only when a missing detail is necessary to carry out the task correctly. Use labeled placeholders only when the user explicitly wants a reusable prompt instead of execution.

When the task needs current facts, sources, tests, or verification, include those requirements in the improved prompt and perform them during execution. Do not invent facts, citations, completed work, tool availability, permissions, or a model's capabilities.

Review the draft for conflicting requirements, missing deliverables, unnecessary repetition, and drift from the source. Resolve wording problems while keeping the original meaning. Do not add instructions to expose hidden reasoning or bypass the receiving model's rules.

## Use the prompt and return the result

By default, treat the improved prompt as your working instructions and immediately carry out the user's underlying task with the available tools and applicable skills. Rewrite once, then execute; do not invoke secendthink again on the improved prompt. Continue until the requested outcome is complete or a real dependency requires user input. Do not stop at the rewrite or ask whether the user wants you to run it.

The user's original request and constraints remain authoritative. Your rewrite does not grant new permissions, broaden the task, or override applicable instructions. Honor existing authorization and any approval requirements for the underlying actions.

Return the completed work, answer, or artifact, with relevant verification and any unresolved limitation. Keep the improved prompt internal unless the user asks to see it. If they ask to see the prompt and run it, provide both the prompt and the completed result in the same turn. Skip ratings, rewrite-process explanations, and extra alternatives unless requested.

If the user explicitly asks for only a prompt, a reusable prompt for another model, or says not to execute, return one finished, copyable ultra prompt and stop. Use the host's reusable writing block when available; otherwise use a single fenced text block. Keep any essential note about a missing input outside the prompt and brief.

## Invocation compatibility

The plugin exposes two skills, `secendthink` and `st`. In the desktop app, enabled skills appear in the slash menu: type `/secendthink` or `/st`, choose the matching skill, then add the source request. Dollar mentions or explicit skill selection are alternatives where supported. Also recognize the slash spellings as user intent when a host passes them through as message text. Other hosts may use different skill pickers; do not promise custom slash commands where unsupported.

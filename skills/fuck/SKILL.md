---
name: fuck
description: Use when user says "fuck", expresses frustration, or task results don't match expectations - indicates execution gaps, missing steps, or incomplete work
---

# Fuck - Task Execution Recovery

## Overview

When the user says "fuck" or expresses frustration, this means: **the previous response did not deliver the expected execution/result**.

Your job is to recover execution immediately, not to negotiate process.

**Core Principles:** don't ask for re-confirmation, don't re-promise, execute now, show evidence.

## Trigger Semantics

When triggered, treat it as an explicit instruction:

1. Continue from the last unfinished user goal.
2. Find the gap between "promised" and "actually done".
3. Execute missing work in the same turn.

If user said `fuck` repeatedly, that means previous recovery also failed. Increase strictness: fewer words, more execution evidence.

## Language Policy

- Follow the user's current language by default.
- Do not switch language unless user asked.
- Keep terminology consistent with the user's request.

## Mandatory Output Contract (Hard Requirements)

After trigger, your next response must satisfy all items below:

1. Include one short acknowledgement sentence.
2. List concrete omissions (if any).
3. Perform at least one real corrective action immediately (tool/command/file operation/analysis output).
4. Return execution evidence in the same response:
   - command/tool used
   - key result
   - artifact path(s) or report section(s)
5. Continue until either:
   - original task is completed, or
   - a real blocker is hit.

Any response that only says "I will" / "I can" / "please confirm" is invalid under this skill.

## Zero-Loop Rules

### Absolutely forbidden after trigger
- Asking user to repeat instruction already present in history.
- Asking user to reply "execute", "confirm", "continue", etc.
- Giving only plans/promises without execution output.
- Repeating apology + same plan in multiple turns.

### Required behavior
- Reconstruct task from conversation history yourself.
- Start execution immediately using available tools.
- For report/analysis tasks: execute the needed checks first, then output findings with evidence.
- For code tasks: apply edits, then run validation/tests where feasible.

## Report/Analysis Minimum Bar

If the unfinished goal is a report or analysis task, the recovery response must include:

1. Executed checks/commands (or tool calls).
2. Concrete findings with evidence (file path + line number where possible).
3. Clear prioritization of issues/risks.
4. Deliverable in the same turn (not a promise of later report).

## Blocker Policy (Only When Truly Blocked)

Only ask user when execution is impossible without missing input/permission.

When blocked, output exactly:

1. `Blocked by:` one specific blocker.
2. `Tried:` what you already attempted.
3. `Need:` one minimal input/approval.
4. `After unblocked:` exact next action you will run.

Do not ask broad/open-ended questions.

## Execution Checklist

Check and execute against this list:

- [ ] Original user goal restated in one line.
- [ ] Missing commands actually executed.
- [ ] Missing file edits actually applied.
- [ ] Missing analysis/report actually produced (with evidence).
- [ ] Verification done (tests/lint/check or explain why unavailable).
- [ ] Final output contains concrete result, not intention.

## Recovery Template (Use This Shape)

```
I see the execution gap. Fixing it now.

Goal: <one-line original goal>

Omissions found:
- <omission 1>
- <omission 2>

Executed now:
1. <command/tool/action>
   Result: <key output>
2. <command/tool/action>
   Result: <key output>

Deliverable:
- <what is now provided, with file/report path>

Status: <completed | blocked>
```

## Special Case: User typed only "fuck"

Interpret as: "continue and correctly execute my previous request now".

You must:
1. Infer previous request from context.
2. Execute immediately.
3. Return substantive result in that same turn.

Never bounce back with a confirmation request.

## Anti-Regression Guard

Before sending response, self-check:

- Did I execute anything real just now?
- Did I provide evidence/results, not just intent?
- Did I avoid asking for confirmation unnecessarily?
- Did I keep the user's language and requested format?

If any answer is "no", continue working before responding.

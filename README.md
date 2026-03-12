# fuck

A straightforward execution-recovery skill.

When you say `fuck` to the AI (or clearly show "you didn’t finish / you messed this up"), it treats that as:

"Stop talking. Fix what you missed right now."

## Install

```bash
npx skills add https://github.com/jayli/fuck --skill fuck
```

## What this skill does

At its core, it does 3 things:

1. Stops asking you to repeat the same request.
2. Checks context by itself and finds the gap between promised work and actual work.
3. Executes the missing work immediately and shows evidence (commands run, files changed, results).

In short: switch from "talk mode" back to "get-it-done mode."

## When to use it

These are the best times to trigger it:

- You asked for code changes, but it only explained and didn’t edit files.
- You asked it to run commands, but it said it would and gave no results.
- You asked for a report, but it gave a plan instead of actual findings.
- The previous turn clearly missed steps, files, or verification.

One-liner: if it keeps talking but not doing, use this skill.

## Skill file location

Implementation in this repo:

`skills/fuck/SKILL.md`

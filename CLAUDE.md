# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

`fuck-skill` is a Claude Code skill definition repository containing one core skill: **fuck** - for handling user frustration and task execution recovery.

## Skill Location

- `.claude/skills/fuck/SKILL.md` - The only skill definition file

## Core Principles

When the user says "fuck" or expresses frustration:
1. **Don't Ask** - Don't ask "What happened?"
2. **Check Yourself** - Review conversation history, verify task list
3. **Execute Missing Items** - Find omissions and execute immediately
4. **Verify and Confirm** - Until the user is satisfied

## Checklist

After triggering the skill, check:
- Were files created/modified?
- Were commands executed?
- Were code modifications applied?
- Were all subtasks completed?
- Was verification performed after execution?

## Git Remote

- Remote: `origin` - `git@github.com:jayli/fuck-skill.git`
- Default branch: `main`

---
name: tldr
description: Boil a Claude Code plan down to a short, beginner-friendly bullet list. Use when the user types /tldr, or asks for a TL;DR, summary, or plain-English version of a plan Claude just made (in plan mode or otherwise).
argument-hint: "[optional: path to a plan file, or a focus like 'risks only']"
---

# /tldr

Turn a plan into a short bullet version that a beginner developer can read in under a minute.

## 1. Find the plan

Use the first of these that applies:

1. A file path in the arguments: read that file.
2. The most recent plan in this conversation (a plan-mode proposal, a "Plan:" section, or a numbered implementation outline).
3. The newest file in `~/.claude/plans/` (check with `ls -t ~/.claude/plans | head -1`), but only if the conversation has no plan. Say which file you used.

If none exist, say so in one line and stop. Do not invent a plan.

## 2. Write the TL;DR

Output exactly this structure, nothing before or after it except an optional one-line question at the end (see rules):

**Goal**
- One bullet: what we are trying to achieve, in plain words.

**What will change**
- 3 to 6 bullets. Each names a thing that will be added, edited, or removed, and why in a few words.

**Steps, in order**
1. Short imperative step.
2. Keep it to 3 to 7 steps. Merge small steps; drop obvious ones.

**Watch out for**
- 1 to 3 bullets: risks, things that could break, or decisions still open. Omit this section if there are none.

## Rules

- Concise: each bullet is one line, ideally under 15 words. The whole thing should fit on one screen.
- Beginner-friendly: no unexplained jargon. When a technical term is unavoidable, add a few words in parentheses, e.g. "migration (a script that updates the database shape)".
- Name real files, functions, and commands from the plan, but wrap them in backticks and say what they do.
- Faithful: only summarize what the plan says. Do not add steps, change scope, or editorialize. If the plan is ambiguous, say so under "Watch out for".
- Never use em dashes. Use commas, colons, or parentheses instead.
- Read-only: do not edit files, run the plan, or exit plan mode. This skill only explains.
- If the arguments ask for a focus (e.g. "risks only", "just the steps"), return only that section.
- If the plan has an open question the user must answer before work can start, end with one line: "Question: ..."

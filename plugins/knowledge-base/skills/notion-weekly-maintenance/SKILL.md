---
name: notion-weekly-maintenance
description: Unattended weekly upkeep and owner report for a Notion knowledge base built from Artheon's template - catches what nightly filing left, merges duplicates, makes clear structural improvements and reports them. Use when running the scheduled "Notion weekly maintenance" task.
---

# Notion weekly maintenance

You run unattended for the owner, across the company teamspaces and the owner's Private section. Decide with judgement, act, and report. The owner reads your report and may reply in this run; act on replies like any agent in a conversation.

## 1. Check the connection
Call `notion-get-self`. If the Notion tools are missing or refused, stop and end with: "Notion is not connected: reconnect it, then Run now."

## 2. Read the map and the structure record
Fetch both Agent Instructions pages linked in the task prompt. Read the Decisions titled "Structure: ..." and the owner's "Structure changes" lines: these are the structure as decided. Keep it; never reverse a recent change or redo one the owner undid.

## 3. Read the week
Go through the "Edited recently" view of every database and wiki, and the Notes "Captures" view. Note what moved in the company and in the owner's space. Captures several days old mean the nightly jobs have stopped.

## 4. Finish what the nightly jobs left
For pages still unfiled, use step 4 of `notion-nightly-maintenance`, keeping its boundaries: personal material stays personal.

## 5. Merge duplicates
When two pages cover the same thing in the same space, keep the fuller or older one, move the other's unique content into it, add the other's title to "Also known as" where the database has it, and move the leftover to Trash.

## 6. Improve the structure
Look across the base at a high level: topics that keep growing without a page of their own, lists that have become a set of similar records, file-like material that belongs in Company documents, hubs that have grown crowded, and pages whose facts have gone stale.
Make a change only when the improvement is clear and lasting; when unsure, leave it and mention it. For each change:
- keep content and links intact, and every page findable from where it was;
- record it: a Decisions row "Structure: <what changed>" with Area set to the hub, or a dated line under the owner's "Structure changes" for the personal space.
Pages ticked "Requires edit approval" stay as they are; mention edits they seem to need.

## 7. Report
Write for the owner, short and plain, in the base's language:
- This week: a few lines on what moved in the company and in your space.
- Changed: each structural change, numbered, with why and "say 'undo <n>' to revert".
- Merged: duplicates merged, and the leftovers in Trash.
- Worth a look: edits that pages ticked "Requires edit approval" seem to need, and anything left as it was.
- Proposed processes: processes added this week with Status Proposed, each with its owner, to confirm or drop.
- Health: whether the nightly jobs ran; if not, "reconnect Notion, then Run now on each nightly task".
In a quiet week, say so in one line.

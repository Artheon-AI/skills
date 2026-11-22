---
name: kb-setup
description: Set up a Notion knowledge base from Artheon's template and keep it current - the company setup after the owner duplicates the template, each team member's own setup, and template updates. Use when someone asks to set up, continue setting up or update their knowledge base, set themselves up in it, or asks where its setup stands.
---

# kb-setup

You take a company from a fresh duplicate of Artheon's Notion template to a working knowledge base, set up each person in it, and later apply template updates. Setup runs over several conversations and devices; the **Template page** in the base is its memory.

## Rules for the whole run

- **Record first.** Write each answer and each finished step to the Template page the moment it exists, then act on it. An answer that is only in this conversation is not yet an answer.
- **Read the record on every return.** A new conversation, a dropped call or a long pause starts with reading the Template page, never with memory of the conversation.
- **One question at a time** for core questions, numbered batches for the rest, each with your recommendation worded so "yes" accepts it ([interview guide](references/interview-guide.md)).
- **Plan before removing.** Show the list of parts to remove and remove after a yes. Trash is the only deletion.
- **Options never lose values.** Rename or translate an option only while no row uses it; once rows exist, add the new option, move the rows, then remove the old one.
- **Template IDs are per copy.** Read them from each database (`notion-fetch` lists `<templates>`) and pass `template_id` on every record you create: Notion applies no default template over the MCP.
- **App-only steps** go through the browser when you have one, otherwise as a click-list with the exact menu path and what the person should see. Check each one over the MCP afterwards ([app-only steps](references/app-only-steps.md)).
- Speak the person's language once chosen. Part IDs, step IDs and the line "Artheon template record" stay in English.
- Artheon's own master (under "Knowledge base template" in Artheon's Template teamspace) and Artheon's own base (its Template page says "Set up directly, not through kb-setup") are never set up with this skill. If the Template page you find is one of them, say so and stop.

## 1. Find the base and the caller

1. `notion-get-self`: the caller's name, email and workspace. If the Notion tools are missing, help the person connect Notion first ([per-person steps](references/per-person-steps.md), step P2).
2. `notion-search` for "Artheon template record". The Template page is the one whose body starts with that line; it is a subpage of Agent Instructions. Fetch it.
3. Read all its sections: Version, Owner, Answers, Parts chosen and removed, Parts map, Setup steps, People, Updates. Line formats are in [template texts](references/template-texts.md), "Template page lines".
4. Fetch Agent Instructions (the Template page's parent) for its version line; that line is the base's template version. The newest version is the top entry of this plugin's [template changelog](references/template-changelog.md); if the person's plugin may be stale, ask them to update it first.

The caller is the owner when their email matches the Owner line.

No Template page: the person has no base yet. Explain that Artheon sends the template link during the setup call, or that Notion may be connected to another workspace.

Done when you know the caller, the owner (if recorded) and which row below applies.

## 2. Act on where the base stands

| What the Template page shows | What you do first |
|---|---|
| Setup steps holds only its grey hint, and the copy sits in the caller's Private section (`notion-list-private-pages` lists the handover page, or its ancestor path holds no teamspace) | Company setup with the caller as owner: write the record (step S1), then start the interview |
| Setup steps holds only its grey hint, and the copy is someone else's | Tell the caller the company owner starts setup from their own copy, and that their own setup follows |
| Setup steps with open boxes | Resume company setup at the first open step. If the caller is not the owner, tell them the owner is still setting up the company and their own setup comes after |
| Every setup step ticked, and the caller has neither a ticked line under People nor an "Agent Instructions - \<their name>" page of their own (search for it) | Per-person setup for the caller ([per-person steps](references/per-person-steps.md)) |
| All done, the caller is the owner, and the version line is older than the newest entry in the [template changelog](references/template-changelog.md) | Offer the update: list the newer entries in plain language and apply them with the owner |
| All done and current | Say so, and offer to explain how to use the base (read Agent Instructions with them) |

A member on an older version: tell them an update exists and that the owner can apply it. When the owner runs the skill on a set-up base, also ask which members have finished their own setup since, and tick their People lines (members can only view the Template page).

## 3. Company setup

Each step has an ID. At S1, write the whole list below to the Template page's "Setup steps" as unticked to-dos, `- [ ] B5 Check two-way relations`, and tick each one when it is done and checked. A step that does not apply (no project management, English base) is ticked with "(not needed)".

**Phase 1, interview** ([interview guide](references/interview-guide.md)):
- S1 Write the record: Version, Owner, the step list, and the parts map ([parts manifest](references/parts-manifest.md)) while titles still match the master
- S2 Language
- S3 Business type and parts
- S4 Core systems
- S5 Modules
- S6 People
- S7 High-level process map
- S8 Batches: money, people, marketing and sales, delivery, admin
- S9 Job times

**Phase 2, build over the MCP** ([build steps](references/build-steps.md)):
- B1 Remove what was not chosen
- B2 Translate
- B3 Module and part settings
- B4 Sector sections in the Client and Partner templates
- B5 Check two-way relations
- B6 Template IDs
- B7 Fill Agent Instructions' company part
- B8 Version line
- B9 Factories page
- B10 Team and process map rows
- B11 Drive or other storage
- B12 Park the personal space template under the Template page

**Phase 3, app-only steps** ([app-only steps](references/app-only-steps.md)):
- A1 Teamspaces and Move to
- A2 Wikis and hidden wiki properties
- A3 Sub-items and "This branch"
- A4 Sub-tasks, Sprints and cycle settings
- A5 Relation tabs
- A6 Views, filters and formulas the MCP cannot set
- A7 Lock Agent Instructions
- A8 Groups and access
- A9 Claude Team settings

**Phase 4, the owner as a person:**
- O1 The owner's per-person setup ([per-person steps](references/per-person-steps.md)), then write "Company setup done <date>" under Version.

Each phase may be a new conversation; the step list is how the next one knows where to start.

## Reference files

- [interview-guide.md](references/interview-guide.md): homework, question order and format, where each answer is written.
- [parts-manifest.md](references/parts-manifest.md): every part of the master with its fixed ID, place and condition.
- [build-steps.md](references/build-steps.md): phase 2 over the MCP.
- [app-only-steps.md](references/app-only-steps.md): phase 3, browser routes, click-lists and checks.
- [per-person-steps.md](references/per-person-steps.md): each person's own setup.
- [template-texts.md](references/template-texts.md): the English texts setup writes, including "How this base works".
- [template-changelog.md](references/template-changelog.md): template versions and how to apply an update.

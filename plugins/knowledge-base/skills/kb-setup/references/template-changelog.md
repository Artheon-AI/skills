# Template changelog

One entry per version of Artheon's Notion template, newest first. The template version (1.0, 1.1, ...) is separate from the plugin version.

Each entry has:
- the template version and date;
- a short note for people;
- the steps an agent takes, each addressing parts by part ID;
- for text, the section of "How this base works" to replace and its new English text.

## Applying an update

`kb-setup` offers an update when the owner runs it on a base whose Agent Instructions version line is older than the newest entry here. Members are told an update exists and that the owner can apply it.

1. List the newer entries in plain language, oldest first, with each one's note for people. Apply after the owner's yes, one entry at a time.
2. For each step, read the current state first; a step whose result is already there is done. Running an entry twice changes nothing.
3. Write each finished step to the Template page under Updates (`<version>: <step> done`), so an interrupted update resumes where it stopped.
4. While applying:
   - replace changed sections of "How this base works" by their heading, in the base's language;
   - add new properties, options and views only to parts this base has (the parts map says which);
   - offer new optional parts; add them only on a yes;
   - add before removing; anything holding data is removed in a later version than the one that retires it;
   - rename by adding the new name, moving rows, then removing the old one;
   - leave pages ticked "Requires edit approval" as they are and name them to the owner;
   - check every step over the MCP;
   - record each structural change as a Decisions row titled "Structure: <what changed>", Area set to the hub affected.
5. "This company" and "Company notes" are the company's: never touch them.
6. Last, when every step is checked: move the Agent Instructions version line to the new version and date, change the Template page's "Template version" line to match, and write `<version> applied <date>` under Updates.

## 1.2 (2026-11-23)

**For people:** the People row of the databases table now lists the By warmth and Connectors views, with the CRM module. An agent asked for connectors or a person's warmth searched the database by hand because the row named only Team, Org chart, All and Edited recently (findability walkthrough on Artheon's base).

**Steps for agents** (only for a base with the CRM module):
1. In "This company" > "Databases", in the People row's "Main views" cell, add `[By warmth](<link>)` and `[Connectors](<link>)` after Org chart, each linking this base's own People view of that name (`https://app.notion.com/p/<database id>?v=<view id without dashes>`). Updates otherwise leave "This company" alone: name this addition to the owner and make it after their yes. Done when the cell lists Team, Org chart, By warmth, Connectors, All, Edited recently and both new links open the right views.
2. Move the version line to `Template version 1.2, <date>` (step 6 above).

## 1.1 (2026-11-23)

**For people:** two rules from walkthroughs on Artheon's base. The "Where things go" row for contracts now says a Contracts record holds the dates and a link to the signed file, and the terms stay in the file (agents copied the key terms into the record's body). The Project management line on parent issues now says to settle the sub-issues before trashing the parent (agents trashed the parent and left the sub-issues behind).

**Steps for agents:**
1. In "How this base works" > "Where things go", replace the right-hand cell of the row "A contract, subscription or domain" with: `Contracts (Management): its dates and a link to the signed file; the terms stay in the file`. Done when the cell reads exactly that.
2. In "How this base works" > "Project management", replace the line starting "Trashing a parent leaves its sub-issues" with: `Before trashing a parent issue, move or trash its sub-issues; Notion leaves them behind. When the person named only the parent, ask about the sub-issues first.` Done when the section holds that line and not the old one.
3. Move the version line to `Template version 1.1, <date>` (step 6 above).

## 1.0 (2026-11-22)

**For people:** the first release of Artheon's knowledge base template. A company duplicates the handover page and `kb-setup` sets it up: the company teamspace with the Home wiki, its seven hubs and the core databases (Projects, Meetings, Clients, People, Processes, Partners, Decisions, Ideas); the Management teamspace with its wiki, Contracts and Hiring; a personal space for each person; the project management module (Issues, Cycles, Milestones) and the CRM module (Deals); and the optional Proof, Equipment, Events and Goals.

**Steps for agents:** none. A base set up from version 1.0 is current. Its parts are listed in [parts-manifest.md](parts-manifest.md) and its texts in [template-texts.md](template-texts.md).

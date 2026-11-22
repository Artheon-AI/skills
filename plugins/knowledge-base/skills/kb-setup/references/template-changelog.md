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

## 1.0 (2026-11-22)

**For people:** the first release of Artheon's knowledge base template. A company duplicates the handover page and `kb-setup` sets it up: the company teamspace with the Home wiki, its seven hubs and the core databases (Projects, Meetings, Clients, People, Processes, Partners, Decisions, Ideas); the Management teamspace with its wiki, Contracts and Hiring; a personal space for each person; the project management module (Issues, Cycles, Milestones) and the CRM module (Deals); and the optional Proof, Equipment, Events and Goals.

**Steps for agents:** none. A base set up from version 1.0 is current. Its parts are listed in [parts-manifest.md](parts-manifest.md) and its texts in [template-texts.md](template-texts.md).

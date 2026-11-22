# Per-person steps

Each person runs these in their own Claude, because their Private section and their Claude account are theirs alone. The owner runs them too, as step O1. Read the company Agent Instructions first; the person's language is the company's unless they ask otherwise.

Steps the person already did (a plugin installed, Notion connected) are checked and skipped. Keep a short P1-P7 list in the conversation and say which step you are on.

## P1 Plugins

- Add Artheon's marketplace and install `knowledge-base`:
  - Claude app: Customize > Plugins > Add > Add marketplace, `Artheon-AI/skills`, then install `knowledge-base`.
  - Claude Code: `claude plugin marketplace add Artheon-AI/skills`, then `claude plugin install knowledge-base@artheon`.
- `sales` too, if the person sells and the base has the CRM module (Deals exists).
- Matt Pocock's skills plugin, following its own README (for Claude, from Anthropic's official marketplace), so it stays current.
- Notion's official plugin.

## P2 Notion

- Connect Notion in the Claude app (Settings > Connectors > Notion > Connect). On Team, the owner has enabled it for the organisation (A9).
- Turn off Notion Memory: Notion > Settings > Notion AI > Memory > "Use memories" off. The knowledge base is the memory. The MCP cannot read this setting: ask the person to confirm it is off.

Check: `notion-get-self` returns the person and the company workspace.

## P3 Personal space

1. Duplicate the personal space template (the child of the Template page) with `notion-duplicate-page`. Members can only view it once Agent Instructions is locked, so for a member, first ask the owner to give this person "Can edit" on the personal space template (its Share menu), duplicate, then ask the owner to remove that access again.
2. Move the copy into the person's Private section with the app step in [app-only steps](app-only-steps.md), "Private pages". Then move its children to the top of the Private section in this order: Agent Instructions - \<Name>, Notes, Projects, My wiki, then any kept optional parts, the same way. Trash the empty copy page.
3. Rename "Agent Instructions - \<Name>" with the person's name.
4. Keep what the person uses (manifest "Personal space"): Projects for owners, optional for others; the 1:1 page for managers (duplicate it once per report, rename it "1:1 - \<Report>", share it with that person); Reading, private People and Tasks only on a yes. Trash the rest.
5. My wiki: check it is a wiki (A2). Ask for the person's areas of life and work, create one top-level My wiki page per area, and add the same names as options of Area on Notes and Projects.
6. Check: the Notes relations Company project, Client and People point at the company's Projects, Clients and People; Notes' Project and Projects' Notes are two-way; the personal Projects page shows its Notes tab (A5); Share on each moved page lists only the person.
7. Read this copy's template IDs: `notion-fetch` Notes (Daily, Meeting) and Projects (Project).
8. Fill "Agent Instructions - \<Name>": About me from what the person says (leave the placeholders they skip), My space with mentions of their own copies, their template IDs from step 7, and the 1:1 line only for managers. Delete the lines of parts they did not keep.

Done when the Private section starts with Agent Instructions - \<Name>, then Notes, Projects (if kept) and My wiki, and that page's links all open the person's own copies.

## P4 Instructions pointer

Write the custom instructions block ([template texts](template-texts.md)) with the two links, the company Agent Instructions and this person's Agent Instructions - \<Name>, into each app the person uses:
- Claude app: Settings > Profile > instructions for Claude;
- Claude Code: the user-level `~/.claude/CLAUDE.md`;
- Codex: the user-level `~/.codex/AGENTS.md`.

On Team, when the organisation instructions carry the pointer (A9), skip the Claude app, unless P5 shows scheduled runs do not get it; then write the personal one too.

## P5 Nightly job (paid Claude plan only)

Create "Notion nightly maintenance - \<Name>" as a scheduled task by asking Claude in a Cowork conversation:
1. The task prompt from [template texts](template-texts.md), with the two links. Model Sonnet, daily at about 01:00 local time (or the time from S9).
2. Run now once.
3. Approve the Notion tools "for all scheduled runs". A tool left on "always ask" makes a run finish without it.
4. Check the run: it filed something or reported "Nothing to file".

Then change the job's line on the Factories page to "running since \<date>". A connector added later needs the task created again.

## P6 Owner and sellers

- The owner also creates "Notion nightly maintenance - Company" (Sonnet, about 02:00) and "Notion weekly maintenance" (Opus, Sunday about 04:00), with the same four steps and their prompts.
- People who sell may add, on a yes, "Outreach prep - \<Name>" (weekdays early morning, Sonnet, runs `daily-outreach`); the owner may add "Sales weekly review" (Monday morning, runs `weekly-sales-review`). For both, allow Gmail read, search and draft for all runs; send stays on "Always ask".

## P7 Tick the person

On the Template page's People section, tick the person's line: `- [x] <Name> (<email>) - done <date>`. Members can usually only view the Template page; then tell the person their setup is done and ask them to let the owner know, so the owner's next session ticks it. Either way the person's own "Agent Instructions - \<Name>" in their Private section shows that their setup ran.

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

## 1.4 (2026-11-24)

**For people:** a short sidebar and a front door. The company teamspace shows three items: Home - \<Company> (the Home wiki renamed), a Databases page holding every company database under Work, Relationships and Operations, and Agent Instructions. Home - \<Company>'s Home view is the front door: Start here with a `/kb-guide` line, the seven hubs, the databases in three columns and live Now tabs; like Home - \<Name>, it holds only headings, links and live views, with no intro or description lines. Management shows only its wiki, with Contracts (and Hiring) inside it. Each Private section mirrors the company: Home - \<Name> (My wiki renamed: the New capture button and a link to today's daily note side by side at the top, then Start here, the areas and tabs of records), Agent Instructions - \<Name> and Databases. The Daily template is titled "@Today" and does not repeat: the nightly personal job makes each day's note from it, links it from Home - \<Name>, and moves yesterday's to Trash when nobody touched it and no notes link to it. Each daily note lists the notes made that day, through a new Notes relation, Daily note, and Notes gets a By day view. Records keep their IDs, views, relations and templates, so agents work as before.

**Steps for agents:**
1. Rename the wikis: Home to "Home - \<Company>" and the owner's My wiki to "Home - \<Name>" with the owner's name, each with `notion-update-data-source` `title`, checked in the app ([app-only steps](app-only-steps.md), A2 "Wiki titles"); in the personal space template, My wiki becomes "Home - \<Name>". Done when the sidebar and a fetch show the new titles.
2. Company Databases page: create "Databases" at the company teamspace's top level with `notion-create-pages` and `parent: {teamspace_id}`, with its intro line and the headings Work, Relationships and Operations ([template texts](template-texts.md), "Home views and Databases pages"). Move each company database under it with `notion-move-pages` (`new_parent` the page). Each moved database's `<database>` tag lands at the end of the page; then one `update_content` puts every tag under its heading, keeping all of them. Done when each database fetches with Databases in its path and its views and template IDs unchanged.
3. Sidebar order, in the app: drag the company teamspace to Home - \<Company>, Databases, Agent Instructions, and nothing else (A1 step 3).
4. Home - \<Company>'s Home view: rewrite it to the 1.4 layout ([template texts](template-texts.md), "Home views and Databases pages"), keeping each hub's `<page>` tag. Build the Now tabs over the MCP: insert the tabs block with a placeholder line in each tab, create each linked view with `notion-create-view` and `parent_page_id` (it lands at the end of the page), then one `update_content` that replaces each placeholder with that view's exact `<database ... inline="true"></database>` tag and removes the tags from the page end. The Current cycle tab is made in the app (A6). Leave out the tabs and database mentions of parts this base does not have. Done when every mention and view on the page opens this base's own pages.
5. Management: move Contracts (and Hiring) into the Management wiki with `notion-move-pages` (`new_parent` the wiki's database ID), then place their blocks under a "Records" heading after the linked Contracts view (By cancel date). Done when the Management teamspace shows only Management and the Management Home's linked view still lists contracts.
6. Personal space template and the owner's own space: a Databases page (in the template under `part-personal`; for the owner, a private page) with Notes, Projects, Reading, People and Tasks, whichever exist, moved under it with `notion-move-pages`; 1:1 pages under Home - \<Name>; other root pages of the owner's Private section under Home - \<Name> or Databases after the owner's yes. Then Home - \<Name>'s Home view gets the 1.4 layout, built like step 4: the New capture button and the "📅 Today's note:" line in two columns at the top (in the template with its grey placeholder; for the owner, step 7 points it at today's note). A button block moves into its column with `update_content` and keeps its action; a missing button is made in the app ([app-only steps](app-only-steps.md), "Personal Home and daily note"). Order the owner's Private section in the app: Home - \<Name>, Agent Instructions - \<Name>, Databases, and nothing else. Add `pg-databases` and `ps-databases` to the parts map.
7. Daily notes: in the app, set the Daily template's title to "@Today" (type `@today` > "Today - Date when duplicated") in the personal space template and the owner's Notes, and check that neither repeats ("Personal Home and daily note"): a repeat would make a second note beside the nightly job's. Then create today's daily note in the owner's Notes with `notion-create-pages`, `template_id` the Daily template, Type Daily, Date today, no title, and point the owner's "📅 Today's note:" line at it with one `update_content`. Add the "By day" view to Notes with `notion-create-view` (table, Date newest first) and set Group > Date by Day in the app (A6). Done when the owner's Notes holds today's daily note, made from the Daily template, and Home - \<Name> links to it.
7a. Daily note, in the personal space template's Notes and the owner's Notes: add a one-way self-relation with `notion-update-data-source` `ADD COLUMN "Daily note" RELATION('<that Notes data source ID>') COMMENT 'The daily note of the day this note was created. Agents set it when they create a note; the nightly job sets it on notes created that day. Empty on daily notes. The daily note lists these notes.'`, then place it after Win in the page layout, shown only when set (`page_layout`, `hide_if_empty`). In that Notes' Daily template, append the heading "Notes that day" and a linked list view with `notion-create-view`: `parent_page_id` the template, filter Daily note on the template's own ID, sort Created time ascending, show Name and Type, `show_data_source_title` false. Notion points the view in each new daily note at that note. Done when a daily note made from the template (with `template_id`, then trashed) shows a view filtered on its own ID.
8. Agent Instructions texts ([template texts](template-texts.md)): in "This company", the Wikis line takes the 1.4 wording; updates otherwise leave "This company" alone, so name this change to the owner and make it after their yes. In the personal space template's "Agent Instructions - \<Name>" and the owner's own page, under "My space": the My wiki line gives way to the Home - \<Name> and Databases lines, the Notes line takes the 1.4 text (the nightly job makes each day's note, setting Daily note on new notes, By day view), and the 1:1 line says the pages sit under Home - \<Name>.
8a. The Area property descriptions on Notes and personal Projects: "My wiki areas" becomes the person's areas, "the top-level pages of Home - \<Name>" (`notion-update-data-source` `ALTER COLUMN "Area" SET SELECT(...) COMMENT '...'`, listing every existing option).
9. On Claude Team, give the owner the new organisation instructions block: the personal page now lives "in their Private section". The personal block and task prompts are unchanged.
10. The nightly job makes each day's note, links it from Home - \<Name>, fills Daily note and trashes yesterday's untouched daily note from `knowledge-base` 0.2.7: ask the owner and members to update the plugin. Tell members to ask their agent for the personal steps on their own space: steps 1, 6, 7 and 7a for them, the Agent Instructions - \<Name> lines of step 8, and Open on start, their own choice (Settings > Preferences > Open on start > "Top page in sidebar").
11. Move the version line to `Template version 1.4, <date>` ("Applying an update", step 6).

## 1.3 (2026-11-23)

**For people:** Agent Instructions is shorter and calmer. "How this base works" keeps what an agent needs on every run; project management and sales guidance moved to two subpages, "Project management for agents" and "Sales for agents", read only for that work. The Skills section folded into Where things go. A capture that is clearly company material now moves into the company base on the nightly run; unclear captures and daily notes stay private. "Added by agents" is gone from each person's page, so agents write to the proper place instead. The Daily template gets a section with the person's name under the Agent section. The custom instructions block now names both pages by ID and says when to use the base, and the task prompts no longer repeat the page links.

**Steps for agents:**
1. Create the subpages before removing the old sections. With project management, create "Project management for agents" under Agent Instructions; with the CRM module, "Sales for agents". Their texts are in [template texts](template-texts.md), "Agent Instructions subpages", with the mention pointing at this base's Agent Instructions. Done when each kept subpage fetches with its text.
2. Replace the whole "How this base works" part with the 1.3 text, in the base's language: the sections "Finding things", "Writing things down", "Facts and sources", "Pages people wrote", "What you do on your own", "What you propose first", "Personal spaces", "Skills", "Project management" and "Sales" give way to "Finding and writing", "Where things go", "Company and personal", "Ask first", "Kept outside this base" and "Specific work". Keep this base's own answers in "Kept outside this base" (its HR system) and its "Where things go" variants for missing modules or Drive ([template texts](template-texts.md), "Text that depends on answers"). Under "Specific work", list only the kept subpages, as mentions; with neither, leave the section out. Done when the part matches the 1.3 text and every mention opens this base's subpage.
3. Without the CRM module, the no-CRM line stays under the systems map; the 1.3 wording only changes its reference to "Sales for agents".
4. In the personal space template's "Agent Instructions - \<Name>" and the owner's own page: replace the first line with the 1.3 line and remove the "Added by agents" section. If the owner's section holds lines, show them to the owner first and move each to where it belongs. Tell members to ask their agent for the same change on their own page.
5. In the Daily template of Notes (personal space template and the owner's copy): change the Agent hint to "Agents write here; the rest of the page is yours." and add a heading with the person's name ("\<Name>" in the template) after it, at the same level. Existing daily notes stay as they are.
6. Give the owner the new custom instructions block, filled with the two page IDs, to replace the old one in each app, and the new task prompts for the scheduled tasks (Claude > Scheduled > the task > edit). Tell members the same for their own block and nightly task. The nightly skill's capture moves need `knowledge-base` 0.2.5 or later.
7. Move the version line to `Template version 1.3, <date>` (step 6 above).

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

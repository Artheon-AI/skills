# Build steps (phase 2, over the MCP)

Run in order; each step starts by reading the Template page and ends by ticking its line. The parts map gives you each part's page or database in this copy. The copy already has the 1.4 shape: under the company part page, Home - \<Company>, Databases (every company database under Work, Relationships and Operations) and Agent Instructions; under the Management part page, the Management wiki with Contracts and Hiring inside it; under the personal part page, Home - \<Name>, Agent Instructions - \<Name> and Databases. Where a step needs the app, it names the [app-only step](app-only-steps.md); do that step there and come back.

Contents: B1 remove; B2 translate; B3 module and part settings; B4 template sections; B5 two-way relations; B6 template IDs; B7 Agent Instructions; B8 version line; B9 Factories; B10 team and processes; B11 storage; B12 personal space template.

## B1 Remove what was not chosen

1. From "Parts chosen and removed" and the [parts manifest](parts-manifest.md), list every part to remove, grouped: pages, databases, properties and views, template sections, Agent Instructions text. Show the list and remove after the owner's yes.
2. A database with a two-way relation leaves its synced side on the other database (Equipment's Holder shows on People as Equipment; Deals' Client on Clients as Deals). Drop the relation pair first (`DROP COLUMN` on one side drops both), then trash the database.
3. **Project management not chosen:** first turn Sprints off in the app (A4, "Not chosen"), because Sprints must be off before Issues goes. Then trash `db-issues`, `db-cycle-board` (if still there) and `db-milestones`; drop Projects' Issues, Milestones, Progress, Health and Priority (`props-projects-pm`); remove the Issues line from How we work's Records (`rec-issues`) and the Current cycle tab from Home - \<Company>'s Now tabs (`home-now-cycle`).
4. **CRM module not chosen:** trash `db-deals`; drop Clients' Do not contact, Health, Deals, Open deal value and Open renewal, People's Warmth and Do not contact, and Meetings' Deal; rewrite People's Roles options without Connector (no rows exist yet, so a full option list is safe); remove the Deals line on Customers and offer (`rec-deals`) and the Deals today tab from Home - \<Company>'s Now tabs (`home-now-deals`). The leftover views (Clients Watch and Renewals; People By warmth, Connectors, Do not contact) go in A6.
5. **CRM module chosen:** drop "CRM record" on Clients and People (`prop-crm-record`).
6. Pages and databases not kept: trash them (the MCP's delete tools move them to Trash); a database goes from its place on the Databases page or, for Hiring, the Management wiki. Also remove each removed database's mention from Home - \<Company>'s Databases columns (`home-db-links`). With `db-proof` removed, also its Records line (`rec-proof`); with `db-hiring` removed, the "Open hiring" heading and view on the Management wiki (`mgmt-open-hiring`). Remove linked views, tabs and lines with targeted `update_content` edits that keep every other block, including the hubs' `<page>` tags and the `<database>` tags of kept databases.
7. Agent Instructions text for removed modules (`ai-pm`, `ai-sales`) is handled in B7.

Done when every part listed for removal is in Trash or dropped, and the parts map marks each one "removed <date>".

## B2 Translate

Skip (tick "not needed") for an English base. Otherwise translate everything once, now, while no rows exist:
- page titles and text: hubs, wiki stubs, Home - \<Company> and Management (a wiki's title is set with `notion-update-data-source` `title`; check it in the app, A2), both Databases pages and their headings, the part pages, Agent Instructions (both parts) and its subpages, the Template page except its first line, and the personal space template with Agent Instructions - \<Name>;
- database titles and descriptions, property names and descriptions, option names, view names;
- database templates' titles and text (fetch each template ID and rewrite with `replace_content`).

Keep:
- "Artheon template record", part IDs and step IDs in English;
- the page titles "Agent Instructions" and "Agent Instructions - \<Name>", which the instructions pointer and the skills find by name;
- Cycles' own properties and statuses as Notion made them;
- for the views the plugin skills read by name (Captures, Edited recently, Today, Missing next step, Board, Gone quiet, Renewals and upsells, Won and lost, Watch, Renewals, By cancel date, Current cycle), the English name in brackets after the translated one in the Agent Instructions tables, so a skill finds them.

Option names are written into three formulas, which must follow any rename (texts in [template texts](template-texts.md), "Formulas"): Deals "Open value" and Clients "Open renewal" (stages Won, Lost, Parked) and Issues "Is done" (Done, Canceled). Rewrite Open value and Is done over the MCP; Open renewal reads a related page's property, which the MCP refuses, so type it in the app (A6). Views filter on status groups and need no change.

After translating Issues' Status options, check the Cycle board's Current cycle view still filters and Cycles still shows its rows.

Done when a fetch of every kept database, hub and the personal space template shows no English left except the kept items above.

## B3 Module and part settings

**Project management chosen:**
- Issue ID prefix: `notion-update-data-source` with `ALTER COLUMN "Issue ID" SET UNIQUE_ID PREFIX '<PREFIX>'` (use the translated property name). A prefix belongs to one data source per workspace: `unique_id_prefix_in_use` means another database here holds it, so agree another prefix with the owner. Check: create one issue with the Issue template ID, read its ID (the schema does not show the prefix), then trash it.
- Cycle length and start day are app settings (A4).

**CRM module chosen:**
- Stages: rename Deals' Stage options to the owner's stages, keeping the three groups (open stages in To-do and In progress, closing stages in Complete). Then rewrite "Open value" with the closing stage names, and do "Open renewal" in the app (A6).
- Currency: set Value's number format to the company currency.
- Gone quiet: the number of days goes into the view's filter on "Days since touch" in the app (A6); the MCP drops filters on formula properties.
- Clients' description: replace "Leads stay in the CRM." with the CRM text in [template texts](template-texts.md).

**CRM module not chosen:** in Clients' description, name the CRM: "Leads stay in \<CRM>."

**Proof kept:** write the services from S3 on Offer and pricing (it is ticked "Requires edit approval": show the text and write it after the owner's yes), then add the same names as options of Proof's Service select. Agents filing Proof rows cannot add options, so the list must exist first.

**Business lines:** add them as options of Ideas' Line.

Done when each setting reads back from a fetch or a scratch row, and every scratch row is in Trash.

## B4 Sector sections in the Client and Partner templates

Fetch the Client template (its ID from B6, or from `notion-fetch` of Clients) and remove the sections the business type does not keep: `tpl-client-billing`, `tpl-client-confidentiality`, `tpl-client-environments`, `tpl-client-ads` (manifest conditions). Remove a parent heading ("Constraints") only when nothing is left under it. Same for `tpl-partner-vendor` in the Partner template. Use `update_content` on the template ID.

Done when both templates hold only the sections this company keeps.

## B5 Check two-way relations

Fetch each kept data source and check that these pairs are two-way and point at each other:

| Database | Property | Other side |
|---|---|---|
| Projects | Client | Clients: Projects |
| Meetings | Client | Clients: Meetings |
| Meetings | Project | Projects: Meetings |
| Decisions | Project | Projects: Decisions |
| Decisions | Meeting | Meetings: Decisions |
| Decisions | Supersedes | Decisions: Superseded by |
| Processes | Owner | People: Owns |
| Processes | Parent process | Processes: Sub-processes |
| People | Reports to | People: Direct reports |
| Equipment | Holder | People: Equipment |
| Issues | Project | Projects: Issues |
| Issues | Milestone | Milestones: Issues |
| Milestones | Project | Projects: Milestones |
| Issues | Cycle | Cycles: Issues |
| Issues | Parent issue | Issues: Sub-issues |
| Issues | Blocked by | Issues: Blocking |
| Deals | Client | Clients: Deals |
| Notes (personal space template) | Project | Projects (personal): Notes |

Skip pairs whose database was removed. In a translated base, find each property by its relation's target database rather than by its English name. Make a one-way pair two-way in place with `notion-update-data-source` (the relation with DUAL and the other side's name). Every other relation is one-way by design. Also check that the personal space template's Notes relations (Company project, Client, People) point at this base's Projects, Clients and People, and that its Daily note relation is one-way and points at that same Notes.

Done when every listed pair of a kept database reads back two-way.

## B6 Template IDs

Every template has a new ID in the copy. `notion-fetch` each kept database and read its `<templates>`:

| Database | Templates (default) |
|---|---|
| Projects | Project (default) |
| Meetings | Meeting (default), Retro |
| Decisions | Decision (default) |
| Clients | Client (default) |
| Partners | Partner (default) |
| People | Person (default) |
| Processes | Process (default) |
| Issues | Issue (default) |
| Deals | Deal (default) |
| Hiring | Candidate (default) |
| Cycles | Notion's "New sprint" |
| Notes (personal space template) | Daily (default on the Daily view), Meeting (default on the Meetings view) |
| Projects (personal space template) | Project (default) |

Write the IDs under Answers. A missing template is rebuilt in the app (A6, "Templates"), because the MCP cannot create a template or set a default; then fill its body over the MCP from the master's sections ([template texts](template-texts.md), "Database templates") and read its new ID.

Done when every kept database's templates are listed with their IDs.

## B7 Fill Agent Instructions' company part

Edit with targeted `update_content`; the page may be locked, and the owner's edits still go through. Texts and formats are in [template texts](template-texts.md).
- Replace \<Company> and \<HR system or Management documents>, here and in Home - \<Company>'s title (`notion-update-data-source` `title`, checked in the app, A2) and Home view.
- **Wikis line:** mentions of this copy's Home - \<Company> and Management.
- **Databases table:** one row per kept database, with this copy's database mention, what goes here, `collection://` URL, main views as links (`https://app.notion.com/p/<database id>?v=<view id without dashes>`) and template IDs from B6. Drop rows of removed databases. Without the CRM module, leave out the Clients Watch and Renewals links and the People By warmth and Connectors links.
- **Hubs:** the seven hub mentions with their lines; drop mentions of removed pages from the lines.
- **Systems map:** the rows from S4 and S8, plus the CRM row without the CRM module, and the storage row (B11).
- **Kept outside this base:** the password manager, HR records system and whistleblowing channel as answered.
- **Module subpages:** keep the subpage "Project management for agents" only with project management and "Sales for agents" only with the CRM module. Trash a subpage not kept and remove its line under "Specific work"; with neither kept, remove the section. Without the CRM module, put the no-CRM line under the systems map. Adjust "Where things go": the Issue clause on the "Work being done" row only with project management; the "A sales ask, upsell or renewal" row only with the CRM module; the "A file" row without Drive.
- Leave "Company notes" as its placeholder for the company.

Done when every link in the page opens a page or database of this copy (fetch each one) and no placeholder is left outside Company notes.

## B8 Version line

Set the first line to `Template version <x>, <setup date>. Changelog: [template changelog](<changelog URL>).` with the version from the Template page and the changelog URL already in the line.

## B9 Factories page

On the AI hub's Factories page, list the scheduled jobs this company will run, one line each: name, what it does, when, whose account, and "not created yet" (per-person setup changes it to "running since <date>"). Jobs: "Notion nightly maintenance - \<Name>" for each person with a paid Claude plan; "Notion nightly maintenance - Company" and "Notion weekly maintenance" for the owner; with the CRM module, the optional "Outreach prep - \<Name>" for each seller and "Sales weekly review" for the owner, marked "optional, off".

## B10 Team and process map rows

1. People: one row per person from S6, created with the Person template ID: Roles Team, Job title, Email, Reports to (after all rows exist), Workspace user once they are members.
2. Processes: one row per process from S7, created with the Process template ID: verb-phrase Name, Owner (the People row), Area (the hub), Done by, Cadence, Status Current, an emoji icon.
3. Check with view-mode queries that the Company map's "Who owns what" and "All processes" views show them, and that each process page's "This branch" view filters on itself.

Done when both Company map views list every row from S6 and S7.

## B11 Drive or other storage

Map before changing anything: a read-only inventory of the company's shared drives or folders, written as the systems map's storage row and on "How we use our tools". Restructure only with the owner's agreement, one area at a time: save every original location, build the new skeleton next to the old one, pilot one folder, tell staff before each wave, move (never copy) in small batches, check counts, access and Notion links, roll back from the saved locations if anything breaks, and delete only with the owner's yes.

For a fresh company the recommended layout is shared drives Company, Clients and Management, one folder per client from a `_Template client` skeleton, at most three levels, file names `YYYY-MM-DD Client - Type - Title`. Without Drive, tick "not needed"; B7 writes the fallback.

## B12 Park the personal space template

Move `part-personal` under the Template page with `notion-move-pages`. It stays there as the template every person duplicates (per-person step P3); it is not anyone's own space.

Leave its daily-note parts as the master has them: the Daily template in Notes has no repeat, Notes holds no daily notes, and Home - \<Name>'s "📅 Today's note:" line keeps its grey placeholder. Each person's first daily note and the link to it are made in P3; the nightly personal job makes the rest.

Done when a fetch of the Template page shows the personal space as its child, and its Home - \<Name> still has the placeholder line.

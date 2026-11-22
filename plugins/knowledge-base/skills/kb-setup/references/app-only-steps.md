# App-only steps (phase 3)

Steps the Notion MCP cannot do. Do them yourself in the browser when you have one (Claude in Chrome or a built-in browser, with the owner signed in to Notion); otherwise give the owner the click-list, one step at a time, with what they should see. After each step, run its check over the MCP, then tick the step on the Template page.

Notion's app shows MCP edits after a few seconds; reload before judging a page.

Contents: A1 teamspaces; A2 wikis; A3 sub-items; A4 Sub-tasks and Sprints; A5 relation tabs; A6 views, filters, formulas, templates and defaults; A7 lock; A8 groups; A9 Claude Team; Private pages.

## A1 Teamspaces and Move to

1. Create the company teamspace, named after the company, **Open**; and **Management**, **Closed**. Click-list: sidebar > "+" beside Teamspaces > Create a teamspace > name > permission Open (or Closed) > Create. If Notion adds its own starter page to a new teamspace, trash it with the owner's yes.
2. Move the contents of the "Company teamspace" part page to the company teamspace's top level, and of "Management teamspace" to Management's. Click-list: open the part page, select its pages and databases (click the first, Shift-click the last), "..." > Move to > the teamspace. The MCP cannot place anything at a teamspace's top level.
3. Order the company sidebar: Home, Agent Instructions, Projects, Meetings, Clients, People, Processes, Partners, Decisions, Ideas, then the module and optional databases (Issues, Cycle board, Cycles, Milestones, Deals, Proof, Equipment, Events, Goals). Management: Management, Contracts, Hiring. Drag in the sidebar.
4. Trash the empty part pages and the handover page over the MCP, after checking they hold nothing (the personal space template is already under the Template page, B12).

Check: `notion-fetch` of each moved database and of Agent Instructions shows the teamspace at the top of its ancestor path, and the part pages are in Trash.

## A2 Wikis and hidden wiki properties

Home, Management (and each person's My wiki, P3) must be wikis.

Check first: a wiki's data source has Owner and Verification properties, and `notion-query-data-sources` in SQL mode is refused for it ("not supported for wiki databases").

If the copy lost wiki status:
1. Click-list: open the page > "..." > Turn into wiki.
2. Hide Owner and Verification: open any page of that wiki > click the property name > Property visibility > Always hide. It applies to the whole wiki. The MCP refuses page layouts on wikis.
3. Over the MCP: drop Tags; make sure Status (Draft default, Current, Outdated) and, on Home and Management, "Requires edit approval" exist with their descriptions ([template texts](template-texts.md), "Wiki properties"). Set "Requires edit approval" to Always show in the app if it hides when unticked.
4. Icons on wikis are set in the app (Add icon): 🏠 Home, 🏛️ Management, 📚 My wiki.

## A3 Sub-items and "This branch"

People nest by Reports to / Direct reports; Processes by Parent process / Sub-processes.

Check in the app: any view of the database > settings > More settings > Sub-items is on, and Advanced settings > Property names Direct reports (People) or Sub-processes (Processes). Over the MCP: the data source has no "Parent item" or "Sub-item" property.

If lost: Turn on sub-items. Notion then **creates two new properties, "Parent item" and "Sub-item"**, and uses them. Re-point: Advanced settings > Property > the existing children relation. Then drop "Sub-item" over the MCP (`DROP COLUMN`; dropping one side of a self-relation drops both) and check both are gone.

"This branch": open Processes > New dropdown > the Process template's "..." > Edit. Its linked view's filter should read "Parent process contains" the template itself. Over the MCP, a process created with the Process template ID gets a view filtered on its own page.

## A4 Sub-tasks, Sprints and cycle settings

**Project management chosen.** On Issues: settings > More settings.
- Sub-tasks: on; Advanced settings > Property: Sub-issues. If Notion made its own "Parent task" / "Sub-task" pair, drop "Sub-task" over the MCP (drops both).
- Sprints: on, Automated sprints on, Incomplete tasks: next sprint, Dependencies off. Set the duration and start day from Answers.
- If Sprints had to be turned on anew, Notion makes a new Sprints database and Sprint board: repeat the master's renames (Sprints > Cycles, Sprint name > Name, Sprint status > Status, Sprint ID > Cycle ID, Tasks > Issues; Issues' Sprint > Cycle; Sprint board > Cycle board; views Current sprint > Current cycle, Sprint planning > Cycle planning, All sprints > All cycles), add Points (sum rollup of Estimate) over the MCP, copy the Cycles description from [template texts](template-texts.md), and put the new IDs in the databases table.

Check: Cycles holds a Current, a Next and a Future cycle, and a view-mode query of the Cycle board's Current cycle view runs.

**Project management not chosen** (B1, before Issues is trashed): Issues > settings > More settings > Sprints > Turn off sprints. It permanently deletes Cycles and the Cycle board. Check: Cycles no longer fetches.

## A5 Relation tabs

Five databases show related records as tabs on their pages. These tabs are built in the app and `notion-fetch` does not show them; a `page_layout` update over the MCP replaces the whole layout and drops them, so change these five layouts only in the app.

| Database | Tabs |
|---|---|
| Projects | Content, Issues (Name, Status, Owner, Priority, Due), Meetings (Name, Date, Type, Summary; newest first), Decisions (Name, Status, Date, Decided by) |
| Issues | Content, Sub-issues, Blocked by (Name, Status, Owner) |
| Clients | Content, Projects (Name, Status, Owner, Progress), Meetings (Name, Date, Type, Summary; newest first), Deals (Name, Stage, Kind, Next step date, Value) |
| Milestones | Content, Issues (Name, Status, Owner, Priority, Due) |
| Projects (personal) | Content, Notes (Name, Type, Date) |

Check: open each database's template in the app (New dropdown > template "..." > Edit) and look for the tabs. Tabs of removed modules (Issues on Projects, Deals on Clients) should be gone with their relation.

Rebuild a missing tab: page "..." > Appearance & layout > Customize layout > Structure "Tabbed" > "+" beside the Content tab > pick the relation > trim the columns in the view settings > Apply to all pages.

## A6 Views, filters, formulas, templates and defaults

- **Views of removed parts** (no MCP tool deletes a view): right-click the view tab > Delete view. Without the CRM module: Clients "Watch" and "Renewals"; People "By warmth", "Connectors", "Do not contact". Check: `notion-fetch` of the database no longer lists them.
- **Gone quiet** (CRM module): Deals > Gone quiet > filter "Days since touch" is greater than or equal to the owner's number > Save for everyone. The MCP silently drops filters on formula properties. Check: `notion-fetch` of the view shows the filter.
- **Open renewal** (CRM module, after a stage rename or translation): Clients > Open renewal column > Edit property > Edit formula, type the formula from [template texts](template-texts.md) with this base's stage and kind names, click outside to save. Check: the property reads back with the new names.
- **Templates:** a missing database template is created in the app: the database's New dropdown > New template, title typed in the app (the first typing after the editor opens is often lost; retype), body filled over the MCP on its ID. Make it the default: New dropdown > template "..." > Set as default > For all views (Notes' Daily and Meeting: "Only on" the Daily and Meetings views). Create it from an unfiltered view, or it picks up the view's filter values.
- **Status defaults** the copy lost: column > Edit property > option > Set as default. Projects Planned, Issues Backlog, Deals the first stage, Processes Proposed, personal Projects Active.

## A7 Lock Agent Instructions

1. Agent Instructions > Share: the teamspace's members and the workspace "Can view"; the owner "Full access". Notion asks "Change and unlink" from the parent's sharing: accept.
2. "..." > Lock page. Do the same on the Template page (it inherits the access).

Check: `notion-fetch` shows `locked` on both, and the owner's MCP edits still go through (they do on a locked page).

## A8 Groups and access

Settings > People > Groups > Create a group for each role from S6, and add its people. Then give the groups access: company teamspace for everyone; Management teamspace for the owners and whoever they name; page access where the owner wants it. Inviting people to the workspace sends them email, so the owner does it (Settings > People > Add members).

Check: `notion-get-groups` lists the groups with their members.

## A9 Claude Team settings

On Claude Team, the owner (as admin):
- turns on the Notion connector for the organisation (organisation settings > Connectors > Notion);
- puts the organisation pointer in organisation instructions ([template texts](template-texts.md), "Custom instructions block", organisation version).

Not on Team: tick "not needed"; each person writes the pointer in P4.

Check: ask the owner to open a new conversation and confirm the instructions appear; whether they reach Cowork and scheduled runs is checked in P5, and if not, each person writes the personal pointer.

## Private pages

Moving a page into someone's Private section is an app step. `notion-move-pages` to the workspace keeps the teamspace's access, and the page shows under Shared. Click-list: "..." > Move to > Private pages > "Make this page private?" > Move to private. Check: the page's Share lists only its person.

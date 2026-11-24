# App-only steps (phase 3)

Steps the Notion MCP cannot do. Do them yourself in the browser when you have one (Claude in Chrome or a built-in browser, with the owner signed in to Notion); otherwise give the owner the click-list, one step at a time, with what they should see. After each step, run its check over the MCP, then tick the step on the Template page.

Notion's app shows MCP edits after a few seconds; reload before judging a page.

Contents: A1 teamspaces; A2 wikis; A3 sub-items; A4 Sub-tasks and Sprints; A5 relation tabs; A6 views, filters, formulas, templates and defaults; A7 lock; A8 groups; A9 Claude Team; Private pages; personal Home and daily note; Open on start; sidebar.

## A1 Teamspaces and Move to

1. Create the company teamspace, named after the company, **Open**; and **Management**, **Closed**. Click-list: sidebar > "+" beside Teamspaces > Create a teamspace > name > permission Open (or Closed) > Create. If Notion adds its own starter page to a new teamspace, trash it with the owner's yes.
2. Move the part pages' children to the teamspaces' top level; the MCP cannot place anything there. The databases travel inside their pages, so this is four items:
   - Company teamspace: Home - \<Company>, Databases, Agent Instructions. Click-list: open the "Company teamspace" part page, select the three (click the first, Shift-click the last), "..." > Move to > the company teamspace.
   - Management: the Management wiki, with Contracts and Hiring inside it. Click-list: open the "Management teamspace" part page, select the wiki, "..." > Move to > Management.
3. Order matters: the sidebar is how people find their way in, and the front door comes first. Reload and read the company teamspace in the sidebar: exactly Home - \<Company>, Databases, Agent Instructions, in that order. Drag an item that is out of place. Management shows only Management.
4. Trash the empty part pages and the handover page over the MCP, after checking they hold nothing (the personal space template is already under the Template page, B12).

Check: `notion-fetch` of Agent Instructions and of each moved database shows the teamspace at the top of its ancestor path (a company database under Databases, Contracts under Management), and the part pages are in Trash.

## A2 Wikis and hidden wiki properties

Home - \<Company>, Management (and each person's Home - \<Name>, P3) must be wikis.

Check first: a wiki's data source has Owner and Verification properties, and `notion-query-data-sources` in SQL mode is refused for it ("not supported for wiki databases").

If the copy lost wiki status:
1. Click-list: open the page > "..." > Turn into wiki.
2. Hide Owner and Verification: open any page of that wiki > click the property name > Property visibility > Always hide. It applies to the whole wiki. The MCP refuses page layouts on wikis.
3. Over the MCP: drop Tags; make sure Status (Draft default, Current, Outdated) and, on Home - \<Company> and Management, "Requires edit approval" exist with their descriptions ([template texts](template-texts.md), "Wiki properties"). Set "Requires edit approval" to Always show in the app if it hides when unticked.
4. Icons on wikis are set in the app (Add icon): 🏠 Home - \<Company>, 🏛️ Management, 🏠 Home - \<Name>.

**Wiki titles.** A wiki's title belongs to its database: set it with `notion-update-data-source` `title`. Reload the app and read the sidebar; if it still shows the old name, open the wiki and type the title in the app. Check: `notion-fetch` and the sidebar show the same title.

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
- **Current cycle tab** (project management): Home - \<Company>'s Now tabs hold a linked Issues board filtered to Cycle: Current and grouped by Status. The app's `/linked` offers data sources only, so the Cycle board's own Current cycle view cannot be picked, and the MCP cannot set the "Current" cycle filter. When the tab is empty or shows the wrong rows (after A4 made a new Cycles database): open the tab, remove the old view, type `/linked` > Linked view of data source > Issues, choose Board, Group by Status, add the filter Cycle > Current and save it for everyone, turn off the data source title, show Name, Owner, Priority. Check: the board lists only the current cycle's issues.
- **By day** (Notes): the view DSL groups dates by relative ranges, so set the day grouping in the app: Notes > By day > Group > Date > Date by: Day; sort Date, newest first. Check: `notion-fetch` of Notes lists By day, grouped by Date.
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

## Personal Home and daily note

Per person, in P3, signed in as that person.

- **New capture button** in the left column at the top of Home - \<Name>, beside the Today view: press it. It should open a new page with Type Capture in this person's own Notes (the breadcrumb shows their Databases > Notes). If it adds to another Notes, or is missing, rebuild it in that left column: `/button` > name "New capture" > Do: "Add page to..." > the person's Notes, Type Capture > add "Open page, form, or URL" > the page added in step 1 > Done. Buttons are app-only. Check: the test page is in the Captures view; trash it.
- **Daily repeat:** Notes > New dropdown > Daily "..." > Edit. In the template's banner: "Duplicate every..." > Day, then Edit cadence: Every 1 Day, At "Around midnight", Starting Tomorrow, Ending Never, the person's timezone > Save. The MCP cannot set it. Check the next day: Notes holds a Type Daily row with today's Date, titled with the date, and it is the one row in the Today view at the top of Home - \<Name>.

## Open on start

The person's own setting: Settings > Preferences > Open on start > "Top page in sidebar" opens Home - \<Name> on start when it is the first page of their Private section and they have no Favorites. Tell the person; they choose, and nobody else changes it.

## Sidebar

The person's own sidebar, set up with them in the Notion desktop app so the base reads as three items per space:

1. Turn on Notion's new sidebar (beta) in the desktop app if it is offered. It is clearer than the old one. Drop this step once the new sidebar is Notion's default.
2. Customize sidebar (bottom of the sidebar): keep the Home tab; put Private first and Teamspaces second; remove or collapse the sections the person does not use (Chats, Meetings, unused shortcuts and tabs); keep Favorites and Recents only if they use them.
3. Check: the Private section shows Home - \<Name>, Agent Instructions - \<Name> and Databases; the company teamspace shows Home - \<Company>, Databases and Agent Instructions.

Nobody changes another person's sidebar; guide them through it.

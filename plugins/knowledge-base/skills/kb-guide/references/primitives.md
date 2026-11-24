# Notion primitives in this base

Each entry: what the building block is in plain words, how this base uses it, and Notion's official help page. Explain the plain meaning first, then the use here.

## Workspace

The whole Notion account of one organisation: one bill, one member list. Each company has its own workspace on the Plus plan. The company's shared knowledge and every person's private space live in the same workspace, so one Notion connection gives an agent both.

## Teamspace

A section of the workspace for a group of people, shown in the sidebar. Only its top-level pages show in the sidebar; everything else sits inside them. The company teamspace is open to every member. Management is a closed teamspace for the owners and whoever they add. A group of separate businesses gets one teamspace each.

Doc: https://www.notion.com/help/intro-to-teamspaces

## Private section

Each person's own area of the sidebar. Only they, and agents connected as them, can open it. The sidebar's New page button creates pages here. This is the person's personal space: their personal wiki, their own Agent Instructions page and their own databases.

Doc: https://www.notion.com/help/navigate-with-the-sidebar

## Page

A document made of blocks (text, headings, lists, toggles, links, embedded views). Pages nest: a page inside another is a subpage. A project's working documents, for example, are subpages of the project.

## Wiki

A page turned into a special database whose entries are ordinary pages. Its Home view is the front page people land on. This base has three wikis: the company wiki ("Home - <Company>"), the Management wiki, and each person's personal wiki ("Home - <Name>").

Wiki pages here carry two properties:

- **Status**: Draft (the default), Current or Outdated, set by hand. Together with Last edited it tells a reader how fresh a page is.
- **Requires edit approval** (company and Management wikis): a tick means edits go through the page's owner first; agents propose and wait.

Notion's own Owner and Verification are hidden and unused here.

Doc: https://www.notion.com/help/wikis-and-verified-pages

## Hub

Not a Notion feature: the name this base gives to the seven top-level pages of the company wiki (Company, Customers and offer, How we work, People, Money, Systems, AI). Each hub collects the wiki pages on its topic and shows the related records through views. See [structure.md](structure.md).

## Database and data source

A table of records where every row is also a page. A database holds one kind of thing (Projects, Meetings, Clients), and its columns are properties. Every database here has one data source (the table itself), a plural name, and a description that says what it holds and how its records are titled. Agents address a data source by its `collection://` URL.

Rule of thumb: anything with many instances and a lifecycle is a database row; how something works is a wiki page.

Doc: https://www.notion.com/help/intro-to-databases

## Properties

The fields on a database row: Status, Owner, Date, Client, Project and so on. This base uses the same names everywhere:

- **Status** uses Notion's Status type wherever there is a lifecycle, with options grouped into To do, In progress and Complete.
- **Owner** (a person), **Date**, **Client** and **Project** (relations) mean the same thing in every database that has them.
- **Area** is a choice of the hub names, on Decisions, Ideas and Processes, so a hub can show its own records.
- **Also known as** holds other names, on Clients, Partners and People, so search finds them.

Property descriptions explain only meanings that are not obvious. Database page layouts pin the key properties at the top of a record and show related records as tabs.

Docs: https://www.notion.com/help/database-properties and https://www.notion.com/help/layouts

## Views

A saved way of looking at a database: a filter, a sort, a grouping and a layout (table, board, list, calendar, timeline). A view changes what you see, never the data. Every database here has a few named views (for example Projects: In progress, Mine, All), and every database and wiki has an "Edited recently" view of the last week's changes. Agents and the nightly jobs read records through these views too.

Doc: https://www.notion.com/help/views-filters-and-sorts

## Linked views

A view of a database placed on another page. The rows stay in their database; the page only shows them. This base uses them a lot: the live views on the Home pages, the "Records" on each hub (for example Processes filtered to the hub's Area), the Company map, and today's daily note on the personal Home.

Doc: https://www.notion.com/help/data-sources-and-linked-databases

## Relations

A property that links rows of two databases, such as a Meeting to its Client and Project. Two-way relations show on both sides: a Client page lists its Projects and Meetings. Relations here are helpful rather than required: people may leave them empty, and agents and the nightly jobs fill the gaps. Links go one way between spaces: personal pages may link to company pages, never the reverse.

Doc: https://www.notion.com/help/relations-and-rollups

## Sub-items

Rows nested under other rows of the same database: People under the person they report to (the org chart), sub-processes under a process, sub-issues under an issue.

## Database templates and repeating templates

A database template is a ready-made page shape you pick from a database's New button: for example, the Meeting template's headings. Sections are headings with grey hints. A **repeating template** creates a new page on a schedule: each person's daily note is made every day around midnight from the Daily template in their Notes, titled with the date. Each person turns the repeat on in their own copy, in the Notion app.

For agents: a record created over the Notion tools starts blank unless the template ID is passed. The IDs are listed in the Agent Instructions pages.

Doc: https://www.notion.com/help/database-templates

## Buttons

A block that runs a small action when clicked, such as creating a page with set properties. The personal Home has a **New capture** button that adds a capture to the person's Notes and opens it. Buttons are made in the Notion app; agents cannot create them over the Notion tools.

Doc: https://www.notion.com/help/buttons

## Mentions and backlinks

An @ mention links to another page, and the mentioned page lists the pages that mention it (its backlinks). Notes, wiki pages, ideas and project documents end with a short "Related" list of mentions to the pages a reader would want next.

Doc: https://www.notion.com/help/create-links-and-backlinks

## Sharing and permissions

Who can open or edit a page is set in Notion: teamspaces are the boundaries, groups are the roles. Agents act with the connected person's own permissions, so an agent sees exactly what that person sees. The company Agent Instructions page is locked: everyone can read it, the owner edits it. A manager's 1:1 pages sit under their Home - <Name> and are shared with the other person.

Doc: https://www.notion.com/help/sharing-and-permissions

## Comments

Comments are for people. Agents and jobs do not use them as a channel; the weekly job reports in its run instead.

Doc: https://www.notion.com/help/comments-mentions-and-reminders

## Notion AI

Not part of this design. The agents are the person's own Claude or Codex working through the Notion connection. Notion Agent, Custom Agents and Notion's AI memory are unused, and the base uses no Business-plan features.

Doc, if someone asks about Notion's own AI: https://www.notion.com/help/notion-agent

## Notion's documentation through the Notion tools

When the Notion tools are connected, `notion-fetch` with these IDs returns Notion's own reference texts. They are written for agents; use them to check a detail, then explain it in plain words.

| ID | What it covers |
|---|---|
| `notion://docs/notion-flavored-markdown-spec` | How page content is written: blocks, callouts, toggles, columns, mentions |
| `notion://docs/view-dsl-spec` | What a view can do: filters, sorts, groups, calendar, timeline, charts |
| `notion://docs/database-page-layouts` | Database page layouts: pinned properties, sections, tabs |
| `notion://docs/query-data-sources` | Reading database rows: SQL, rows and view modes |
| `notion://docs/skills` | Notion Skills, reference pages, templates and agent instructions |

`notion-get-setup-guide` also returns a short plain-language explanation of pages, databases and views that is good to borrow from.

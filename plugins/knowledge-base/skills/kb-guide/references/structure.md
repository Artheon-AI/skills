# Structure of the base

This file is the one place for structure facts; update it when the template changes. Names below are the template defaults: a company may rename or translate them and remove parts it did not choose. The person's Agent Instructions pages list what their copy actually has.

## Why it is built this way

- Agents are only as good as the context they can reach. The base is one place where company knowledge is written down, kept current and shaped so agents can find, use and maintain it.
- **One home for each fact.** Hubs, Home pages and Agent Instructions link to that home and do not repeat it.
- **Wiki for explained knowledge, databases for records.** How something works is a wiki page; anything with many instances and a lifecycle (a meeting, a client, a project) is a database row.
- **People write freely, agents tidy.** There are no review rituals. People create pages and records with or without links; agents and the nightly jobs file, link and fill the gaps.
- **Small and plain.** Plain hub names, one database per kind of record, Home pages that route rather than announce.
- **Access lives in Notion.** Teamspaces and page sharing decide who sees what; agents see exactly what their person sees.
- **Recovery** is Notion's page history and Trash.

## Company teamspace

Open to every member. Its top level holds exactly three items, in this order:

1. **Home - <Company>**: the company wiki; its top-level pages are the seven hubs. Its Home view is the front door, top to bottom:
   - **Start here**: Agent Instructions, Notion basics (where the base has one), the Company map, the People handbook, and the line "New here or stuck? Type `/kb-guide` in Claude to learn the base or ask how to do something.";
   - **Knowledge hubs**: the seven hubs;
   - **Databases**: three columns, Work, Relationships and Operations, each listing its databases;
   - **Now**: tabs with live views: Projects in progress, Current cycle (with project management), Deals today (with the CRM), Recent meetings, Recent decisions, Recently updated.
   It holds only headings, links, live views and the `/kb-guide` line, with no intro or description lines, and no create buttons: records start in their database.
2. **Databases**: a plain page, not a wiki. One intro line, then every company database under three headings: Work, Relationships, Operations.
3. **Agent Instructions**: the map of the base for agents and curious people. Locked: everyone reads it, the owner edits it.

## The seven hubs

The top-level pages of the company wiki. Each holds the wiki pages on its topic and a "Records" part with linked views of related databases. Pages marked (approval) have Requires edit approval ticked.

| Hub | Main pages | Records |
|---|---|---|
| Company | Direction (approval, with "Now": this quarter's priorities), Company card, Story, Glossary, Legal and admin duties, Company map ("Who owns what" and "All processes") | Processes with Area Company |
| Customers and offer | Offer and pricing (approval), Customers and market, Brand and voice, Marketing channels | Active clients, Proof |
| How we work | Operating principles (approval), service overviews | Processes, Projects, Meetings, Decisions |
| People | People handbook, Learning (optional) | The team in People, Processes with Area People |
| Money | Finance rules (approval), How money moves, KPI definitions | Processes with Area Money; the numbers stay in their own systems |
| Systems | How we use our tools, Accounts and access | Links to the systems map in Agent Instructions |
| AI | AI setup, Getting more, Factories (every automation and scheduled job) | Ideas with Area AI |

## Company databases

Grouped as on the Databases page.

**Work**

- **Projects**: work being done; client work titled "Client - Deliverable". Status Backlog, Planned, In progress, Paused, Done, Canceled. Views In progress, Mine, Edited recently.
- With project management: **Issues** (the tasks inside projects, with their own ID such as ART-12), **Cycle board** and **Cycles** (Notion sprints, run automatically), and **Milestones**.
- Optional: **Goals**.

**Relationships**

- **Clients**: Stage Prospect, Client, Former.
- With the CRM: **Deals**, each sales ask titled "Person or Company - ask", with a Stage and a Next step.
- **People**: the team and the people the company works with. Role Team, Client contact, Partner contact, Investor, Advisor. Views Team, Org chart, All.
- **Partners**: suppliers, subcontractors, vendors, referral partners.
- **Proof**: quotes, case studies, reviews and results (service firms; optional for others).

**Operations**

- **Meetings**: titled "YYYY-MM-DD Topic - Counterparty"; Type Internal, Client, Partner, Sales or Retro; a Summary, with recording and transcript linked from Drive. Templates Meeting and Retro.
- **Decisions**: titled as the decision itself. Status Proposed, Accepted, Superseded. "Governs" links the wiki page it changes.
- **Ideas**: ideas nobody is working on yet. Status New, Exploring, Trying, Parked, Adopted, Dropped.
- **Processes**: recurring work, titled as a verb phrase. Status Current, Proposed, Retired; Done by a Person, an Agent or a Factory. Views Map, By owner, Proposed.
- Optional: **Equipment**, **Events**.

Most databases have an "Edited recently" view and a template of the same name as the record (Project, Meeting, Decision, Client, Person, Partner, Process).

## Personal space

Each person's Private section mirrors the company teamspace: exactly three items at its root, in this order. Any other private page sits under Home - <Name> or Databases.

1. **Home - <Name>**: the personal wiki; its top-level pages are the person's areas, and managers keep their 1:1 pages here too (one running page per report, shared with that person). Its Home view is the person's Notion home, top to bottom, with the same plain style as the company Home:
   - side by side at the very top: the **New capture** button (adds a Notes page with Type Capture and opens it) and **📅 Today's note**, a link to today's daily note;
   - **Start here**: Agent Instructions - <Name> and the `/kb-guide` line;
   - **Areas**: the area pages;
   - **My records**: tabs with Captures, Active projects, Recent notes, and Reading when kept.
2. **Agent Instructions - <Name>**: "About me" (who I am, current focus, how I work, how to talk to me) and "My space" (the person's pages and databases, template IDs, their conventions, and dated "Structure changes" lines from the weekly job). The person edits it.
3. **Databases**: a plain page with the person's databases:
   - **Notes**: captures, notes, daily notes, resources and private meetings, told apart by Type. Views Captures, Recent, Daily, By day, Resources, Meetings, Edited recently. **Daily note** links a note to the daily note of the day it was created.
   - **Projects**: personal projects (owners; optional for others).
   - **Reading**: books read or to read (optional).
   - **People**: private contacts, family and friends; business contacts go to the company's People (optional).
   - **Tasks**: the person's own to-do list (optional).

**Daily notes.** The nightly personal job (around 01:00) makes each day's note from the Daily template in Notes and points the "📅 Today's note" link on Home - <Name> at it, so today's note exists before the person opens Home; nobody creates daily notes by hand. The template does not repeat: a Notion button cannot open "today's" page, so the job keeps a plain link up to date instead. The template's title "@Today" makes each note's title its date, shown in the person's date format. Each daily note ends with "Notes that day", a list of the notes whose Daily note points at it: agents set Daily note when they create a note, and the nightly job fills it for notes made that day. The nightly job moves yesterday's daily note to Trash when nobody touched it after it was made and no notes link to it; every other daily note stays. The "By day" view groups Notes by Date, one group per day, newest first.

**Open on start** is each person's own setting: Settings > Preferences > Open on start > "Top page in sidebar" opens Home - <Name> when it is the first page of the Private section and the person has no Favorites.

## Management teamspace

Closed: the owners and whoever they add. Most staff cannot see it. Its top level holds only the **Management** wiki: Plans and numbers, Pay, Banking and financing, People matters. Its databases sit inside the wiki, under "Records" on its Home view:

- **Contracts**: contracts, subscriptions and domains, with their dates and a link to the signed file; the "By cancel date" view shows what renews next;
- **Hiring** (optional): candidates.

## Where things go

The company Agent Instructions page has the full, current table; use it first. The short version:

| What it is | Where it goes |
|---|---|
| How the company works (a fact, rule, principle) | The wiki page under the hub that covers it |
| How recurring work is done | Its process in Processes |
| A meeting | Meetings, linked to its Client and Project |
| A decision | Decisions, then update the page it governs |
| An idea nobody is working on | Ideas |
| Work being done | Projects (and Issues with project management) |
| A project's working documents | Subpages of the project |
| Something about one client | Its Clients page; the wiki once it applies to a second client |
| A sales ask, upsell or renewal | Deals |
| A person / a supplier | People / Partners |
| A contract, subscription or domain | Contracts, in Management |
| Pay, banking, sensitive people matters | The Management wiki |
| A file | The company's file storage, linked from the record |
| Numbers (invoices, revenue, metrics) | Their own system; the wiki says where |
| A private meeting or 1:1 | The person's Notes, or the 1:1 page |
| Own thinking, notes, plans, learning | The person's Private section |
| Not sure | Make a capture; the nightly job files it, or ask |

**Kept outside the base:** passwords and keys (the password manager), personnel and health records, whistleblowing reports.

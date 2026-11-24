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

Open to every member. Its top level has three pages:

1. **Home - <Company>**: the company wiki. Its Home view is the front door:
   - one line on what the space is;
   - **Start here**: Agent Instructions, the Company hub, Company map, onboarding;
   - **Knowledge hubs**: the seven hubs;
   - **Databases** in three groups;
   - **Now** tabs with live views: active projects, recent meetings, recent decisions, recently updated pages.
2. **Databases**: a plain page holding all company databases in three groups: Work, Relationships, Operations.
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

Grouped as on the Databases page. The base's own Databases page shows the real grouping; read it when it matters.

**Work**

- **Projects**: work being done; client work titled "Client - Deliverable". Status Backlog, Planned, In progress, Paused, Done, Canceled. Views In progress, Mine, All.
- **Meetings**: titled "YYYY-MM-DD Topic - Counterparty"; Type Internal, Client, Partner, Sales or Retro; a Summary, with recording and transcript linked from Drive. Templates Meeting and Retro.
- **Decisions**: titled as the decision itself. Status Proposed, Accepted, Superseded. "Governs" links the wiki page it changes.
- **Ideas**: ideas nobody is working on yet. Status New, Exploring, Trying, Parked, Adopted, Dropped.
- With project management: **Issues** (the tasks inside projects, with their own ID such as ART-12), **Cycles** (Notion sprints, run automatically) and **Milestones**. Optional: **Goals**.

**Relationships**

- **Clients**: Stage Prospect, Client, Former.
- **People**: the team and the people the company works with. Role Team, Client contact, Partner contact, Investor, Advisor. Views Team, Org chart, All.
- **Partners**: suppliers, subcontractors, vendors, referral partners.
- With the CRM: **Deals**, each sales ask titled "Person or Company - ask", with a Stage and a Next step. Optional: **Proof** (testimonials, case studies).

**Operations**

- **Processes**: recurring work, titled as a verb phrase. Status Current, Proposed, Retired; Done by a Person, an Agent or a Factory. Views Map, By owner, Proposed.
- Optional: **Equipment**, **Events**.

Most databases have an "Edited recently" view and a template of the same name as the record (Project, Meeting, Decision, Client, Person, Partner, Process).

## Personal space

Each person's Private section starts with three pages:

1. **Home - <Name>**: the personal wiki; its top-level pages are the person's own areas. Its Home view is their dashboard, with a **New capture** button and today's daily note.
2. **Agent Instructions - <Name>**: "About me" (who I am, current focus, how I work, how to talk to me) and "My space" (the person's databases, template IDs, their conventions, and dated "Structure changes" lines from the weekly job). The person edits it.
3. **Databases**:
   - **Notes**: captures, notes, daily notes, resources and private meetings, told apart by Type. Views Captures, Recent, Daily, Resources, Meetings, Edited recently.
   - **Projects**: personal projects (owners; optional for others).
   - **Reading**: books read or to read (optional).
   - **People**: private contacts, family and friends; business contacts go to the company's People.

Managers also keep one running 1:1 page per report, shared with that person.

## Management teamspace

Closed: the owners and whoever they add. Most staff cannot see it. It holds:

- the Management wiki: Plans and numbers, Pay, Banking and financing, People matters;
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

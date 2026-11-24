# How people and agents work in the base

## Rules for people

- **Find before you create.** Search by title first, try a few likely titles and other names, then look through the database views. Update the page or record that already covers the thing; link to it rather than copying it.
- **One home for each fact.** Write it once, in its home (see "Where things go" in [structure.md](structure.md)), and link to it from elsewhere.
- **Titles follow the database's rule**, written in its description: "YYYY-MM-DD Topic - Counterparty" for a meeting, "Client - Deliverable" for client work, a verb phrase for a process.
- **Give facts a source and date**: "(Name, date)" or a link to the Meeting or Decision.
- **Wiki Status by hand**: Draft while writing, Current once it is true, Outdated when it no longer is.
- **Requires edit approval**: tick it on any wiki page whose edits should go through its owner. Who may edit at all is set by page access.
- **Personal links point one way**: personal pages may link to company pages; company pages link only to company pages. To share a personal note, move it into the company base.
- **Leave out** passwords and keys, health data and personnel records.
- With project management: keep Sprints switched on (switching them off deletes every cycle), and settle sub-issues before deleting an issue, since Notion leaves them behind.

## Manual flows

**Make a capture.** Press **New capture** on Home - <Name> and write a line or a paragraph: an idea, a call summary, something to remember. No template, no properties, no filing. The capture lands in the person's Notes, in the Captures view. That night the nightly job sets its type, area, project and title, links it, and moves clearly-company captures into the right company database (notes from a client call become a Meetings row, a new lead a Deal or People row). Unclear captures stay private.

**Use the daily note.** The repeating Daily template creates each day's note in Notes around midnight, titled with the date, and it shows under Today on Home - <Name>: open it there rather than making one. Personal and Work to-dos sit at the top, free notes below. Agents write only under the "Agent" heading; the rest belongs to the person. A past daily note nobody wrote in goes to Trash on the nightly run.

**Create a record.** Open the database (from the Databases page or a hub's Records), click New, pick the template, give it a title by the database's rule, and fill the properties pinned at the top. Relations are optional; agents add missing ones later.

**Read through hubs and views.** Start at Home - <Company>, open a hub, read its pages and look at its Records. Use the Now tabs for what is live, "Edited recently" for what changed this week, and a page's backlinks to see where it is mentioned. Inside a database, switch between its named views rather than building your own filter each time.

**Find something.** Notion search matches titles best: try likely titles and the "Also known as" names. If search misses, open the database and use its views. Or ask an agent: it searches the same way and reads the views for you.

**Set up your sidebar.** In the Notion desktop app, turn on the new sidebar (beta) if Notion offers it. Then use Customize sidebar: Private first, Teamspaces second, and remove or collapse what you don't use (Chats, Meetings, unused shortcuts). Your Private section and the company teamspace then show three items each. Settings > Preferences > Open on start > "Top page in sidebar" opens Home - <Name> when Notion starts.

## How agents help

**The pointer.** Each person's agent (Claude or Codex) has a short custom instructions block naming the two Agent Instructions pages. It tells the agent to use the base when the person asks to note, remember or find something, or mentions a person, client, project, plan or event. The agent reads both pages once per conversation and follows their links.

**Where guidance sits.** Each kind of guidance has one place:

- the company **Agent Instructions** page holds the map: "How this base works" (generic, kept current by template updates: finding and writing, where things go, company and personal, ask first, what stays outside) and "This company" (kept by the company: the databases table with links, views and template IDs; the hubs; the systems map; company notes that override the generic part);
- **Agent Instructions - <Name>** holds the person: about them and their own space;
- a database's description holds what it holds and its title rule; property descriptions explain non-obvious meanings; the template gives a record's shape;
- skills in this plugin hold procedures (setup, the nightly and weekly jobs); hubs and wiki pages hold the knowledge.

The guidance describes the base rather than giving orders; the person the agent works with decides what to do.

**What an agent does alone.** Everyday filing: captures, notes, new records (meetings, people, clients, partners, proposed processes), stated facts, properties, titles, links and Related lists, and tidy formatting. It keeps people's wording and makes the smallest change that does the job.

**What an agent asks first.** It describes the change and waits for a yes before:

- moving, merging, archiving or trashing pages;
- new hubs, wiki sections, databases or properties;
- substantial rewrites, including the steps of a Current process;
- anything touching more than about five pages;
- any edit to a page ticked Requires edit approval;
- changing a current fact it only inferred.

**The scheduled jobs.** They run as Claude scheduled tasks in each person's own Claude account, so a person without a paid Claude plan has no job.

- **Nightly, personal** ("Notion nightly maintenance - <Name>", around 01:00, in the person's Private section): works through Captures, the "Edited recently" views and new pages; sets type, area, project and titles; fills empty properties and missing relations; adds Related lists; tidies formatting while keeping every word; moves clearly-company captures into the company base; moves past daily notes nobody wrote in to Trash. It skips approval-ticked pages and likely duplicates, and ends with one line.
- **Nightly, company** ("Notion nightly maintenance - Company", around 02:00, run as the owner): the same in the company and Management teamspaces, plus creating clearly described records. It never reads anyone's Private section.
- **Weekly** ("Notion weekly maintenance", Sunday early morning, for the owner): finishes leftovers, merges duplicates (the merged-away page goes to Trash), makes clear, lasting structure changes and records each one, and writes a report: This week, Changed (each with a way to undo), Merged, Worth a look, Proposed processes, Health.
- **Template update** ("Notion template update", for the owner): applies new versions of Artheon's template.

Every agent edit shows in Notion as the connected person, and page history keeps 30 days of versions on Plus, so any change can be checked and undone.

## Modules

**Project management** (if chosen): Issues are the tasks inside Projects, with Status Triage, Backlog, Todo, In progress, Done, Canceled, plus owner, due date, priority, estimate, milestone, cycle, sub-issues and "Blocked by". Views Triage, Mine, Current cycle. Issues raised by outsiders, or by agents unasked, start in Triage. The page "Project management for agents" under Agent Instructions holds the rules.

**CRM** (if chosen): Deals track each sales ask through Stage (To contact, Contacted, Talking, Call booked, Proposal, Won, Lost, Parked) with a Next step and its date. Views Today, Missing next step, Board, Gone quiet, Renewals and upsells, Won and lost. Agents draft emails and never send them; Won, Lost and Do not contact are set by a person. The `sales` plugin adds daily outreach and a weekly sales review. "Sales for agents" holds the rules.

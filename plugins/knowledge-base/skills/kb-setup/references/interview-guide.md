# Interview guide (phase 1)

Contents: before the call; S1 the record; format; S2-S9 the questions; where answers go.

## Before the call (optional homework)

Tell the owner beforehand that two exports speed up the systems questions, and that both are optional:
- Google Workspace admins: the "Accessed apps" list (Admin console > Security > API controls > Manage Third-Party App Access > Accessed apps > Download list). It shows which tools already reach company data.
- A year of recurring software charges from the company card or bank statement, which finds tools that do not sign in with Google.

Microsoft 365 has no simple equivalent; skip it there. When the owner shares either file, read it before S4 and turn each tool into a systems map row to confirm.

## S1 The record

Before any question, fill the Template page (keep the line "Artheon template record" first, in English):
- **Version:** `Template version <x>. Setup started <date>.` Take the version from the Agent Instructions version line.
- **Owner:** the caller's name and email from `notion-get-self`.
- **Setup steps:** the whole step list from SKILL.md as unticked to-dos.
- **Parts map:** walk the copy (the handover page's children, the hubs' child pages, the part pages' databases and the personal space) and write one line per manifest part: `` `pg-direction` `` then a mention of the copy's page or database. Do it now, while titles match the master; translation and moves come later. A manifest part you cannot find gets "missing in the copy" and is rebuilt or noted before B1.
- **People:** one unticked line for the owner: `- [ ] <Name> (<email>) - owner`.

Done when every manifest row has a line in the parts map.

## Format

Matt Pocock's grilling format, so clients meet the pattern they later use with `grill-me`:
- Number every question. Give your recommendation with each, worded so "yes" accepts it.
- Core questions one at a time, in the order below, because later ones depend on earlier answers.
- Smaller related questions in numbered batches; the owner may answer "1 yes, 2 no, 3 Fakturoid".
- No fixed number of questions or batches: ask until every moving part has an answer, and stop when it has.
- After each answer, write it to its home (table below), tick the step when its questions are answered, then ask the next.

## S2 Language

First question. Every later question, page and text is in this language. Write it under Version (`Language: <language>`).

## S3 Business type and parts

Ask which type fits best: agency, software house, ERP and CRM partner, product company, e-commerce, expertise firm (accounting, tax, legal, consulting), or none of these. Then, from the [parts manifest](parts-manifest.md):
- name the sector parts the type keeps by default and the ones it does not use;
- offer each optional part with a one-line recommendation (Proof, Hiring, Equipment, Events, Goals, Learning, Facilities; sector parts marked optional for this type);
- ask whether the company has business lines (Ideas' Line options);
- with Proof kept: the services the company sells, as short names. They go on Offer and pricing and become Proof's Service options (B3).

Write the result under "Parts chosen and removed" as two lists of part IDs, kept and to remove.

## S4 Core systems

One at a time, in this order. Each answer becomes a systems map row (moving part, system, what it holds, how agents reach it):
1. Legal entities, brands, domains and admins.
2. Office suite (Google Workspace is the default for a fresh company; Microsoft 365 is supported).
3. Company documents: where they live, and how far to go (map them, tidy them, or restructure). Restructuring happens only with the owner's agreement, one area at a time (B11).
4. Client records: where they are kept today.
5. Tasks: where work is tracked today.
6. Chat and email: what the team uses and for what.
7. Meetings: where they happen, whether they are recorded, and whether the Google Workspace edition can record Meet (Business Standard or higher), which the meeting factory needs.
8. Password manager (1Password or Bitwarden if none).
9. Where relevant: the shop platform (e-commerce) or code hosting (software firms).

## S5 Modules

1. **Project management:** yes or no. If yes: cycle length (1 to 8 weeks), start day, and the Issue ID prefix (short, capitals, unique to this workspace; recommend the company's initials).
2. **Sales:** the CRM module, or the name of the CRM they keep. With the CRM module, ask for their sales stages (recommend the master's: To contact / Contacted, Talking, Call booked, Proposal / Won, Lost, Parked), the company currency, and after how many days without a touch a deal counts as gone quiet (recommend 14).
3. **Files:** Google Drive or similar, or none. Without one, recommend Google Workspace Business Starter; if declined, files are attached to their records.
4. **Who sells:** the people who would run `daily-outreach` (CRM module only).

## S6 People

Names, emails, roles (these become groups), job titles, who reports to whom, who manages others (they get 1:1 pages), and each person's Claude plan: Team, Pro or Max, or none. Write them as People lines on the Template page (unticked) and as the team rows to create in B10.

## S7 High-level process map

The owner's main recurring work per hub (Company, Customers and offer, How we work, People, Money, Systems, AI), including management work such as the weekly leadership meeting. For each: a verb-phrase name, its owner, and whether a person, an agent or a factory does it, and how often. Top level only; deeper mapping is Artheon's paid process mapping. Written as Processes rows in B10.

## S8 Batches

Numbered batches, each with recommendations:
- **Money:** invoicing (Fakturoid by default), accounting, bank, expense flow, who approves.
- **People:** onboarding, HR records (for "Kept outside this base"), holidays, whistleblowing channel.
- **Marketing and sales:** channels, website, newsletter, ad accounts.
- **Delivery:** how client work runs; time tracking (Toggl Track by default; Clockify, Harvest and Costlocker are options).
- **Admin:** office, insurance, data box or authority mailboxes, recurring filings.

## S9 Job times

The defaults are nightly personal about 01:00, company about 02:00, weekly Sunday about 04:00. Ask only whether they clash with anything.

## Where answers go

| Answer | Home |
|---|---|
| Language, version, dates | Template page, Version |
| Owner | Template page, Owner |
| Business type, parts kept and removed, modules | Template page, Parts chosen and removed |
| Systems, CRM, files, tools, HR records | Agent Instructions, Systems map and "Kept outside this base" (write the rows now; B7 completes the part) |
| Module settings (prefix, cycles, stages, currency, gone-quiet days), business lines, services | Template page, Answers |
| People and plans | Template page, People; People rows in B10 |
| Process map | Template page, Answers, until B10 writes the rows |
| Job times, homework findings, anything else | Template page, Answers |

Agent Instructions is the company's own page: write the systems map rows straight there as they are answered. Everything else that has no home in the base goes under Answers.

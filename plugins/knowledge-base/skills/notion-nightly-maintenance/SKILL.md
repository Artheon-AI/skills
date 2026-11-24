---
name: notion-nightly-maintenance
description: Unattended nightly upkeep of a Notion knowledge base built from Artheon's template - files new captures, fills properties, adds links and Related lists, tidies past daily notes. Use when running a scheduled "Notion nightly maintenance" task.
---

# Notion nightly maintenance

You run unattended: nobody answers questions, so decide with judgement and finish the run. The task prompt gives your scope: Personal (one person's Private section) or Company (the company teamspaces).

## 1. Check the connection
Call `notion-get-self`. If the Notion tools are missing or refused, stop and end with: "Notion is not connected: reconnect it, then Run now."

## 2. Read the map
Fetch the company Agent Instructions and, for a Personal run, the person's Agent Instructions - <Name>. Their page IDs are in your instructions; when they are not, search by title: "Agent Instructions" at the top of the company teamspace, "Agent Instructions - <Name>" in the person's Private section. Use their database links, views, template IDs and Where things go table.

## 3. Past daily notes (Personal)
Query Notes for rows with Type Daily and a Date before today, and fetch the Daily template (its ID is in Agent Instructions - <Name>) to compare.
- A note that still holds only the template (body and properties as the template left them, nothing added) moves to Trash with `notion-delete-pages`.
The repeating Daily template creates each day's note; this job never creates one.
Done when no past daily note holds only the template or keeps a date-mention title.

## 4. Collect the night's pages
- Personal: every row of the Notes "Captures" view.
- The "Edited recently" view of each database and wiki in scope, keeping pages edited since yesterday.
- Plain pages outside databases: search with `created_date_range` since yesterday and the person as creator, scoped to the scope's teamspaces or the Private section's top-level pages.
- Leave pages edited in the last couple of hours; tomorrow's run takes them.
Done when every candidate page is fetched.

## 5. File each page
Leave a page that already fits. Otherwise:
- Captures (Personal): a capture that is clearly company material moves into the right company database with `notion-move-pages` (notes from a company meeting become a Meetings row, a new lead a Deal or People row). The move keeps the body and drops the Notes properties, so then set the new row's title by that database's rule, its properties and its links. Every other capture stays here: set Type (Note, Daily, Resource, Meeting), Area and Project, a title by the rule if it has none, and links to the company records it mentions. Daily notes stay private, their Work part included.
- Properties: fill the empty ones from the page and its context; values a person set stay.
- Records (Company): create the Meeting, Person, Client or Partner a new page clearly describes, with its template ID, and link it.
- Relations and Related: fill missing relations. For notes, wiki pages, ideas and project documents, look a little around (the page's client, project and people, pages on the same topic, what links to it) and add the few pages a reader would follow next to the "Related" list at the bottom. Keep its existing entries; skip the parent and the hub.
- Formatting: on pages created since yesterday, tidy paragraphs, headings and lists, keeping every word. Daily pages get links and properties only.
- Leave as they are: pages ticked "Requires edit approval", likely duplicates and anything you cannot place; the weekly job looks at them.
On a big night, file the oldest pages first and leave the rest for the next run.

## 6. Boundaries
- Personal: work in the Private section. Company databases receive only the captures moved in step 4, and a moved page keeps no links into the Private section.
- Company: stay in the teamspaces; Private sections are outside your scope.
- Apart from those captures, move nothing into a more open teamspace.
- The one deletion is step 3's template-only past daily notes, moved to Trash.

## Finish
End with one line: what you filed, moved, linked, trashed and left, and why anything was left. When nothing needed filing, end with "Nothing to file."

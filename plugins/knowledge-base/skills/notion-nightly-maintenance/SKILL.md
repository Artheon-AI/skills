---
name: notion-nightly-maintenance
description: Unattended nightly upkeep of a Notion knowledge base built from Artheon's template - files new captures, fills properties, adds links and Related lists, makes today's daily note and links it from Home. Use when running a scheduled "Notion nightly maintenance" task.
---

# Notion nightly maintenance

You run unattended: nobody answers questions, so decide with judgement and finish the run. The task prompt gives your scope: Personal (one person's Private section) or Company (the company teamspaces).

## 1. Check the connection
Call `notion-get-self`. If the Notion tools are missing or refused, stop and end with: "Notion is not connected: reconnect it, then Run now."

## 2. Read the map
Fetch the company Agent Instructions and, for a Personal run, the person's Agent Instructions - <Name>. Their page IDs are in your instructions; when they are not, search by title: "Agent Instructions" at the top of the company teamspace, "Agent Instructions - <Name>" in the person's Private section. Use their database links, views, template IDs and Where things go table.

## 3. Today's daily note (Personal)
Today is the run's date in the person's timezone. The Daily template ID is in Agent Instructions - <Name>; Home - <Name> is linked from the same page.
- Query Notes for a row with Type Daily and Date today. When there is none, create it with `notion-create-pages` in the Notes data source: `template_id` the Daily template, Type Daily, Date today, no title (the template's "@Today" gives it). Fetch it until the template body has landed.
- Fetch Home - <Name>. Its line "📅 Today's note: <mention>" sits beside the New capture button. When it mentions another page or none, point it at today's note with one `update_content` on that line only. A Home without the line stays as it is: say so in the finish line.
Done when a daily note for today exists with the template body and the Home line mentions it.

## 4. Collect the night's pages
- Personal: every row of the Notes "Captures" view.
- The "Edited recently" view of each database and wiki in scope, keeping pages edited since yesterday.
- Plain pages outside databases: search with `created_date_range` since yesterday and the person as creator, scoped to the scope's teamspaces or the Private section's top-level pages.
- Leave pages edited in the last couple of hours; tomorrow's run takes them.
Done when every candidate page is fetched.

## 5. File each page
Leave a page that already fits. Otherwise:
- Captures (Personal): a capture that is clearly company material moves into the right company database with `notion-move-pages` (notes from a company meeting become a Meetings row, a new lead a Deal or People row). The move keeps the body and drops the Notes properties, so then set the new row's title by that database's rule, its properties and its links. Every other capture stays here: set Type (Note, Daily, Resource, Meeting), Area and Project, a title by the rule if it has none, and links to the company records it mentions. Daily notes stay private, their Work part included.
- Daily note (Personal): on every Notes page that is not itself a daily note and has an empty Daily note, set it to the daily note of the day the page was created (Type Daily, Date that day), for today and past days alike. When that day has no daily note, leave Daily note empty.
- Properties: fill the empty ones from the page and its context; values a person set stay.
- Records (Company): create the Meeting, Person, Client or Partner a new page clearly describes, with its template ID, and link it.
- Relations and Related: fill missing relations. For notes, wiki pages, ideas and project documents, look a little around (the page's client, project and people, pages on the same topic, what links to it) and add the few pages a reader would follow next to the "Related" list at the bottom. Keep its existing entries; skip the parent and the hub.
- Formatting: on pages created since yesterday, tidy paragraphs, headings and lists, keeping every word. Daily pages get links and properties only.
- Daily notes nobody has touched (Last edited time within 10 minutes of Created time) stay exactly as they are, so step 6 can still recognise them.
- Leave as they are: pages ticked "Requires edit approval", likely duplicates and anything you cannot place; the weekly job looks at them.
On a big night, file the oldest pages first and leave the rest for the next run.

## 6. Yesterday's daily note (Personal)
Query Notes for the row with Type Daily and Date yesterday. Move it to Trash with `notion-delete-pages` when both hold:
- untouched: its Last edited time is within 10 minutes of its Created time (creating it from the template accounts for those minutes);
- unlinked: no Notes page has it in Daily note (step 5 has linked yesterday's pages by now).
Otherwise keep it. Older daily notes stay as they are.
Done when yesterday's daily note is in Trash or kept for one of those reasons.

## 7. Boundaries
- Personal: work in the Private section. Company databases receive only the captures moved in step 5, and a moved page keeps no links into the Private section.
- Company: stay in the teamspaces; Private sections are outside your scope.
- Apart from those captures, move nothing into a more open teamspace.
- The one deletion is step 6's untouched, unlinked daily note from yesterday, moved to Trash.

## Finish
End with one line: today's daily note (made or found), what you filed, moved, linked, trashed and left, and why anything was left. When nothing needed filing, end with "Nothing to file."

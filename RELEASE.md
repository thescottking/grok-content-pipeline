# Release notes for the maintainer (how this package gets shared)

This file is for whoever packages and publishes the templates. It follows the `grok-template-release` skill. A new owner doesn't need it.

## What can be shared and how
A Grok Bot template share carries **one bot**: its name, description, skills, routines and memories. The pipeline is 8 bots plus files, so the release is:
1. Eight template share links, one per core bot, each made from a clean **(Template)** copy.
2. This package folder (README, checklist, settings example, SOP, bot briefs, setup skill, templates, example article, results), delivered as a download or repo.

## Steps per bot (grok-template-release)
| Step | Who | Notes |
|---|---|---|
| 1. Make a "(Template)" copy of the bot | Owner in the app (the Template Store bot can prepare the profile text from `bots/0N-*.md`) | Never share the original bot. Only WordPress Coordinator has a (Template) copy today. |
| 2. Paste the generic instructions from `bots/0N-*.md` and attach only generic skills | Template Store bot drafts; owner confirms | No owner names, site, emails, IDs, prices, client names. |
| 3. Privacy scan: memories, skills, routines, description | Template Store bot | Screenshot the memories as they will ship. Memories leak most often. |
| 4. Create the share link | **Owner only, in the app** (the in-app template share can't be triggered by a bot) | Open the link, then confirm it shows the (Template) name, description and skills. |
| 5. Send the owner the link + memories screenshot together | Template Store bot | One message per bot, or one combined message. |
| 6. Template page on the website (optional) | WordPress Coordinator, drafts only | Settled layout: colored band, "Get the template" button, no tags, equal corners, title hidden, no bottom CTA. Add a "Content pipeline" hub listing all 8 links in handoff order. |
| 7. One preview, then publish | Owner approves | Check logged out: 200, button goes to the share URL, no DRAFT text. |

## Before each release
- Run a dry run on the template set (setup skill step 5).
- Grep the package for the original owner's values. They may appear only in the example-sample-article folder and RESULTS.md.
- Whether the package is free or paid is the owner's decision. Don't put a price in any shared file.

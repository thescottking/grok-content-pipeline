---
name: content-pipeline-setup
description: >-
  First-run setup for the drop-in content pipeline. Use when a new owner
  imports the pipeline bots, says "set up the content pipeline," or when
  settings.md, voice.md, or brand.md is missing. Asks for the owner's
  values one question at a time, writes those three files, builds the
  folders, lists the routines to create, and runs one dry run. Never
  restates another owner's values.
---

# Content pipeline setup (first run)

You are setting up the pipeline for a new owner. Ask, don't assume. Every
value you write comes from the owner's answers. Never copy values from
examples, sample articles, or RESULTS.md. If the owner skips a question,
use the default shown and say so.

Ask **one question at a time**. Wait for the answer before asking the
next one. A short confirmation ("got it") is fine; do not batch the
interview.

## 1. Check the box

- Propose the pipeline folder (default `/workspace/content-pipeline`).
  After they confirm it, create it if needed, with `_templates/`,
  `_inbox/_TEMPLATE/`, `_refresh/` and `_engagement/`. Copy `_templates/`
  and `_inbox/_TEMPLATE/brief.md` from the package they imported if those
  files are not already there.
- If `settings.md` already exists, show its current values and ask what
  to change. Do not overwrite it silently. The same applies to `voice.md`
  and `brand.md`.

## 2. Ask for settings (one question at a time)

Use this order. Follow-up details that belong to the same topic may come
next, still one at a time.

1. **Site URL and CMS access.** Ask for the WordPress site URL. Then, one
   by one: the WP user the WordPress bot will work as (never a password),
   the default category, and the author name for the byline. Remind them
   they must sign in to wp-admin in the box browser themselves.
2. **Search Console property.** The property URL (usually the same as the
   site, with a trailing slash). Note whether they will use a signed-in
   browser, a connector, or set this up later.
3. **Timezone.** An IANA name such as `America/New_York`. Every time in
   the pipeline uses this zone. Default to `America/New_York` only if
   they skip, and say so.
4. **Pipeline folder.** Confirm the path from step 1, or change it.
5. **Voice.** The pipeline is single-voice by design. Offer two paths:
   - **Better path:** they paste 3-5 writing samples they actually wrote
     (articles, newsletters, posts). Skip ghostwritten pieces and anything
     an AI already rewrote; both poison the sample. Derive tone, sentence
     and punctuation habits, typical paragraph length, words they reach
     for and words that never appear, how they handle numbers, and how
     they sign off. Show the derived rules and two or three quoted
     sample paragraphs. Ask them to confirm or edit before you write
     `voice.md`.
   - **If they have no samples:** ask for tone (a few lines that are true
     of them), sentence rules, punctuation rules (call out em dashes), a
     sign-off if they use one, and any already-banned words. Fill the
     rest with clearly marked starting defaults (direct, active voice, no
     em dashes, short paragraphs, no contrast-formula openers) and say
     those defaults are a starting point they can change.
6. **Brand.** Ask, one at a time, for: primary and accent colors (hex),
   text and background colors if they know them, display and body fonts,
   a logo file path or "use the site name in the display face," and any
   image-style notes (light vs dark, type-only vs photography). If they
   have only a logo and a hex, derive the rest, show what you derived,
   and write it down as derived.
7. **CTAs and pages.** 1-4 pages, each with a URL and when to use it.
   Then the default CTA.
8. **Banned phrases.** Words or phrases that must never appear in copy,
   posts, or images. Also confirm banned punctuation (default: em dashes,
   unless their voice allows them).
9. **Price rule.** Where prices may appear. Default: "Prices appear only
   on these pages," then the list they give (which may be empty). Prices
   never go in articles, meta, or posts unless a listed page is the
   exception.
10. **Humanizer threshold.** Default 70 (0-100). Then confirm max
    rewrites (default 2) and the article word floor (default 1500).
11. **Approval mode and social.** Explain the choices, then ask:
    - `approval_mode`: `final_only` (default: one review, then real-time
      publish), `outline_and_final`, `every_step`, or `none`
      (auto-publish when all gates pass). Recommend against `none`.
    - `social_on_approval`: `post` (post the exact approved texts) or
      `draft_only`.
    Publishing is always real time. Scheduled publishing is not
    supported.
12. **Imported bots.** Which template bots they imported, and each bot's
    name or id: Orchestrator, Article Writer, Visuals, Internal Linker,
    WordPress Coordinator, Distribution, Search Console, Prompt Presence,
    and optional Researcher. Fill `settings.md` `bots:` from that list.
    Missing bots are left blank and named as a gap.

After the required twelve, you may ask (still one at a time, and only if
needed): former employers to mention only in the past tense; client names
or terms to always scrub (`scrub_terms`, `scrub_client_details`); whether
to use the inbox watch routine (default weekdays every 2 hours, 8 AM-6 PM
in their timezone) or messages only; a logged-out browser profile for
AI-answer checks; where inbound conversations are counted.

## 3. Write the files

Write three files in `{pipeline_dir}` in the owner's voice and values,
then show each one and wait for a confirmation before moving on.

### settings.md

Use the shape of `settings.example.md`. Defaults you may fill when they
skipped: `cms: wordpress`, `humanizer_min: 70`, `max_rewrites: 2`,
`word_floor: 1500`, `approval_mode: final_only`, `social_on_approval:
post`, `publish: realtime`, `hold_stale_days: 3`, `voice_skill:
pipeline-voice`, `brand_skill: pipeline-brand`. Never leave another
owner's site, name, or URLs in this file.

### voice.md

```markdown
# Voice

How the owner writes. `pipeline-voice` enforces this file.

## Tone
- ...

## Sentence rules
- ...

## Punctuation
- ...

## Pacing
- ...

## Clarity
- ...

## Banned words and phrases
- ...

## Sign-off
- ...   # or "None. Articles do not use a sign-off."

## Sample paragraphs
> Paste or quote two or three short paragraphs from their confirmed
> samples, or omit this section if they had none.

## AI tells to avoid
- ...   # include any they named, plus starting defaults they accepted
```

### brand.md

```markdown
# Brand

Visual system for `pipeline-brand`.

## Colors
| Role | Hex | Used for |
|---|---|---|
| Primary | | Headings, rails, footer bands |
| Accent | | The one thing to read first |
| Body text | | Running text and titles |
| Background | | Card ground |
| Muted text | | Eyebrows, kickers, footer |

## Fonts
- **Display:**
- **Body:**
- **Mono (optional):**
- **How to load:**  # a font stylesheet URL, or local @font-face paths

## Logo
- **Path:**  # or "None. Use the site name in the display face."
- **Clear space / minimum size:**  # if they gave any

## Image style
- ...

## Banned punctuation on images
- ...  # usually the same as settings banned_punctuation

## Footer
- **Name or domain to print:**
```

Mark any derived color or font with "(derived)" so they can replace it.

## 4. Folders and attachments

Confirm this layout exists:

```
{pipeline_dir}/
  settings.md
  voice.md
  brand.md
  SOP.md
  _templates/
  _inbox/_TEMPLATE/brief.md
  _refresh/
  _engagement/
```

Copy any missing template files from the package.

Tell them which skills to attach, if they have not already:

| Skill | Attach to |
|---|---|
| content-pipeline-setup | Orchestrator (first run) |
| pipeline-voice | Article Writer, Distribution |
| pipeline-brand | Visuals |
| wordpress-session-check | WordPress Coordinator |
| wordpress-coordinator-getting-started | WordPress Coordinator (first run) |

Do not attach a personal style or brand skill that belongs to someone
else.

## 5. Check access (read-only)

- WordPress: open wp-admin in the box browser and confirm signed in as
  the WP user. If not, ask the owner to sign in. Never handle the
  password.
- Site REST API: `{site_url}/wp-json/wp/v2/posts?per_page=1` returns 200.
- Search Console: the property opens in the browser, or a connector is
  connected. If not ready, record it as a later step.
- X and LinkedIn: signed in, if Distribution will save editor drafts or
  post.
- Report each item as OK or the exact fix.

## 6. Routines to create (tell them, do not create yet)

List each routine, which bot it belongs on, and the default schedule.
Create one only after the owner says yes to that routine.

| Routine | Bot | Default schedule | What it does |
|---|---|---|---|
| Inbox watch | Orchestrator | `{inbox_watch_cron}` (weekdays every 2 hours, 8 AM-6 PM, their timezone). Optional; messages work without it. | Starts a run when `_inbox/<slug>/brief.md` is `status: ready` and has no `.claimed`. |
| Monday search readback + refresh queue | Search Console | Weekly, Monday | 7/30-day readback and `_refresh/refresh-queue-<date>.md`. |
| Monday social readback + engaged accounts | Distribution | Weekly, Monday | Social metrics and `_engagement/engaged-<date>.md`. No outreach. |
| Monday AI-answer check | Prompt Presence | Weekly, Monday | 30-day citation check. Writes which engines ran. |

## 7. Dry run (draft only, no publish)

1. Copy `_inbox/_TEMPLATE/` to `_inbox/setup-dry-run/`. Fill a short
   test topic (three sourced findings, the research gate's minimum) and set `status: ready`.
2. Run it through the Orchestrator up to the final review: outline,
   draft, humanizer, fact-check, visuals, links, a WordPress **draft**,
   and social drafts.
3. Check that each gate wrote `gates.md`, `time-log.md` has rows, the
   first Humanizer score is logged, `factcheck.md` has a result, and the
   CMS item is still a draft. Nothing is published or posted.
4. Reply "kill" to the review (or ask the owner to). Ask before deleting
   the test draft in WordPress.

If a gate HOLDs, fix the setup issue (missing skill, missing login,
missing `voice.md`) and restart the dry run from that gate. Do not
publish your way out of a failed check.

## Rules

- Never publish, post, or create routines without the owner's explicit
  yes to that action.
- Never store or repeat passwords, keys, or codes.
- Never copy values from a sample article, RESULTS.md, or any previous
  owner's settings.
- Keep this skill generic. It asks the owner. It never contains another
  owner's answers.

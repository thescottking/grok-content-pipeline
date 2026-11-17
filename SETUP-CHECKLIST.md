# Setup checklist

Work through this in order. Time needed: about an hour plus the dry run.

## A. Before you import anything
- [ ] A Grok Bot workspace with a box (shared files and browser across your bots).
- [ ] A WordPress site, and a WP user (Editor or Administrator) the WordPress bot will work as.
- [ ] The site's REST API is public: `https://<your-site>/wp-json/wp/v2/posts` returns JSON.
- [ ] A Google Search Console property for the site, with your Google account as owner or full user.
- [ ] X and LinkedIn accounts, if you want social drafts or posting.
- [ ] Optional: a CRM or inbox label where inbound conversations land (for the inbound metric).

## B. Connect and sign in (box browser)
- [ ] Sign in to wp-admin in the box browser yourself. Bots never see the password.
- [ ] Sign in to Search Console in the box browser, or connect a Search Console connector if you have one.
- [ ] Sign in to X and LinkedIn in the box browser (Distribution).
- [ ] Optional: keep a separate browser profile logged out of ChatGPT and Perplexity for AI-answer checks.
- [ ] Optional connectors: Gmail or your CRM (inbound tracking), an X connector (public metrics).

## C. Import the bots (this order)
Each one is a shared template link. Open it and import it.
1. [ ] Pipeline Orchestrator
2. [ ] Article Writer
3. [ ] WordPress Coordinator
4. [ ] Visuals Studio
5. [ ] Internal Linker
6. [ ] Distribution
7. [ ] Search Console
8. [ ] Prompt Presence Runner
9. [ ] Optional: Researcher

## D. Skills
- [ ] content-pipeline-setup (attach to the Orchestrator)
- [ ] pipeline-voice (attach to Article Writer and Distribution). Every piece uses it.
- [ ] pipeline-brand (attach to Visuals)
- [ ] wordpress-session-check and wordpress-coordinator-getting-started (WordPress Coordinator)

## E. Folders and settings
- [ ] Ask the Orchestrator: "set up the content pipeline". It runs the setup skill, asks for your values and writes `settings.md`, `voice.md` and `brand.md`.
- [ ] Check `{pipeline_dir}/_templates/`, `_inbox/_TEMPLATE/brief.md`, `_refresh/` and `_engagement/` exist.
- [ ] Put the bot names or IDs in `settings.md` under `bots:`.

## F. Routines (approve each one)
- [ ] Inbox watch on the Orchestrator (or skip it and drop by message).
- [ ] Monday: Search Console readback + refresh queue, Distribution social readback + engaged accounts, Prompt Presence AI check.

## G. Prove it
- [ ] Dry run (setup skill step 5): a test drop reaches the final review with every gate logged. Then reply "kill".
- [ ] First real drop: approve the review and check the post is live, checked logged out, and the social texts posted (or saved as drafts).
- [ ] After 7 days: performance.md has the first search and social entry.

# settings.md: every owner-specific value in one place

Copy this file to `{PIPELINE_DIR}/settings.md` and fill it in. Every bot brief, the SOP and the setup skill read their values from here. Nothing owner-specific lives anywhere else in this package.
The first-run setup skill (`skills/content-pipeline-setup/SKILL.md`) asks you for these values one at a time and writes the file for you.

```yaml
# --- Site and author -------------------------------------------------------
site_url: "https://example.com"          # your WordPress site
cms: "wordpress"                         # only WordPress is supported today
wp_user: "editor-name"                   # the WP user the WordPress bot works as (never a password)
default_category: "Blog"
author_name: "Your Name"                 # byline on posts
timezone: "America/New_York"             # every time in the pipeline uses this zone

# --- Skills ---------------------------------------------------------------
voice_skill: "pipeline-voice"            # the ONE voice: writing rules + quality panel for every piece
brand_skill: "pipeline-brand"            # colors, type, image sizes
humanizer_min: 70                        # humanizer gate threshold (0-100)
max_rewrites: 2                          # rewrites before a humanizer HOLD
word_floor: 1500                         # minimum body words for format: article

# --- Calls to action (one per article, chosen by topic) -------------------
ctas:
  - key: "main-offer"
    url: "https://example.com/offer"
    use_for: "posts about the problem your offer solves"
  - key: "newsletter"
    url: "https://example.com/newsletter"
    use_for: "everything else"
default_cta: "newsletter"

# --- Rules the writer and every gate enforce -------------------------------
# Single voice by design: no per-author voices or team-post cadence.
banned_phrases: ["follow me", "game-changer"]     # never in copy or posts
banned_punctuation: ["em dash"]
price_rule: "Prices appear only on these pages:"
price_allowed_pages: ["https://example.com/offer"]
claims_rules:
  - "No number without a source in research/ or a cited URL"
  - "Charts only from research/data.csv"
past_employers_past_tense: []            # e.g. a former employer you mention only in the past tense
scrub_client_details: true               # run the scrub gate (G1) on every drop
scrub_terms: []                          # client names and terms never published

# --- Approvals --------------------------------------------------------------
approval_mode: "final_only"     # final_only | outline_and_final | every_step | none
social_on_approval: "post"      # post (post the exact approved texts) | draft_only
publish: "realtime"             # always realtime; scheduled publishing is not supported
hold_stale_days: 3

# --- Detection --------------------------------------------------------------
inbox_dir: "{PIPELINE_DIR}/_inbox"
inbox_watch_cron: "0 8-18/2 * * 1-5"     # set to "" to rely on messages only

# --- Measurement ------------------------------------------------------------
search_console_property: "https://example.com/"
performance_days: [7, 30]
ai_check_engines: ["google_ai_mode", "perplexity", "chatgpt"]
ai_check_logged_out_profile: ""          # a browser profile kept logged out, if you have one
inbound_source: ""                       # where inbound conversations are counted (CRM, inbox label)

# --- Paths and bots ---------------------------------------------------------
pipeline_dir: "/workspace/content-pipeline"
bots:                                    # fill in after importing each template
  orchestrator: ""
  article_writer: ""
  visuals: ""
  internal_linker: ""
  wordpress: ""
  distribution: ""
  search_console: ""
  prompt_presence: ""
  researcher: ""                          # optional
```

The setup skill also writes `voice.md` and `brand.md` in the same folder. `pipeline-voice` and `pipeline-brand` are the default skills; they read those files.

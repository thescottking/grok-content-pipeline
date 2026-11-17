# Internal links: aeo-crawl-pillar (WP draft <id>)

Prepared 2026-10-30, 11:45 AM CT, by Internal Linker. Read-only: I only used the public REST API and sitemap, with no wp-admin access and no edits.

## Pillar URL
- **Slug:** `what-ai-search-engines-see-b2b-software-websites` (from the `slug:` field in the article.md frontmatter; README.md and sibling-links.md don't give one)
- **URL:** https://thescottking.com/what-ai-search-engines-see-b2b-software-websites
- It returns HTTP 404 right now because it's still a draft. Add list (b) only after Owner publishes, and re-check that the URL returns 200 first.

## Fresh pull (Oct 30, 11:46 AM CT)
- **Posts:** all 205 published posts from the REST API (`X-WP-Total: 205`).
- **Pages:** all 35 pages.
- **Sitemaps:** sitemap_index.xml plus the post and page sitemaps.
- **New AEO posts since Oct 6:**
  - /ai-crawlers-to-allow (Oct 27)
  - /aeo-tactics-that-do-not-work (Oct 29)
  - /157-of-169-b2b-homepage-headlines-would-work-on-a-competitors-site (Oct 19, positioning study)
- **Targets:** every target in list (a) returned HTTP 200 when I curled it at 11:47 AM CT.

## Existing links in article.md (verified)
| Section | Anchor | Target |
|---|---|---|
| Do B2B software sites block AI crawlers in robots.txt? | GPTBot vs OAI-SearchBot: Which AI Crawlers to Allow | /ai-crawlers-to-allow |
| Find out if ChatGPT can open your site | Get your AI visibility audit | https://thescottking.com/positioning-ai-visibility-audit |

article.md has no other internal links, and no audit price anywhere.

## (a) Links OUT of the pillar (source: article.md)
I matched anchors against the markdown as written, so nothing needed stripping. All four are in plain paragraphs, not headings, tables, lists or code.

### a1 · HIGH
- **Section:** Intro, under the H1 and before the first H2.
- **Anchor:** generative engine optimization (GEO) or answer engine optimization (AEO)
- **Sentence:** "Whether you call it generative engine optimization (GEO) or answer engine optimization (AEO), access comes first."
- **Target:** https://thescottking.com/aeo-vs-geo-vs-seo
- **Reason:** That post defines AEO, GEO and LLMO and explains what changes from SEO.

### a2 · HIGH
- **Section:** Is llms.txt worth it, and who uses schema?
- **Anchor:** Outside evidence doesn't support llms.txt as a citation lever
- **Sentence:** "Outside evidence doesn't support llms.txt as a citation lever."
- **Target:** https://thescottking.com/aeo-tactics-that-do-not-work
- **Reason:** It's the newest AEO post, and it lays out the evidence against llms.txt and schema for citations in depth.

### a3 · MEDIUM
- **Section:** Can ChatGPT read JavaScript on your homepage?
- **Anchor:** Server-render the content you want AI to read
- **Sentence:** "Server-render the content you want AI to read."
- **Target:** https://thescottking.com/improve-brand-visibility-ai-search
- **Reason:** Step two of the hub ("is your claim in the initial HTML?") is the fix order this sentence points to.

### a4 · MEDIUM
- **Section:** What can't this data tell you?
- **Anchor:** That takes citation, prompt and log data
- **Sentence:** "That takes citation, prompt and log data, and I have none."
- **Target:** https://thescottking.com/track-brand-mentions-ai-search
- **Reason:** That post is the prompt and citation counting method this data lacks.

## (b) Links INTO the pillar
Target for all five: https://thescottking.com/what-ai-search-engines-see-b2b-software-websites (only once it's live).

**Block types:** I inferred these from the rendered HTML because I can't see the raw block markup without logging in.
- **Gutenberg posts:** these render `wp-block-paragraph` and `wp-block-list` classes, so the target is a paragraph block or a list item.
- **Improve, Why and Track:** these render no `wp-block` markers at all, so they're probably Classic content. There, edit the named paragraph inside the Classic block.

For every source below I checked that:
- the anchor appears exactly once;
- it isn't inside a link or a heading;
- the source doesn't already link to the pillar.

### b1 · HIGH
- **Source:** https://thescottking.com/ai-crawlers-to-allow
- **Section:** Why is robots.txt only half the check?
- **Anchor:** your CDN and firewall block at a layer robots.txt never shows you
- **Sentence:** "Because your CDN and firewall block at a layer robots.txt never shows you."
- **Block:** paragraph (Gutenberg). The whole block is that one sentence.
- **Reason:** The pillar's two-door finding (34 sites blocked ChatGPT at the firewall on both days) is the data behind this claim.

### b2 · HIGH
- **Source:** https://thescottking.com/improve-brand-visibility-ai-search
- **Section:** Step one: can the engine reach you?
- **Anchor:** Your CDN or firewall can block bots at a layer robots.txt never shows
- **Sentence:** "Your CDN or firewall can block bots at a layer robots.txt never shows."
- **Block:** paragraph inside Classic content (no block markup). Full block text: "robots.txt is only half the check. Your CDN or firewall can block bots at a layer robots.txt never shows. Cloudflare began blocking AI crawlers by default on new domains on July 1, 2025. It has since split its controls into search, agent and training categories. On September 15, 2026, it added a setting to disallow training while staying in search. If your site went live on Cloudflare after July 2025, check which setting someone picked."
- **Reason:** The hub's access step gets the pillar's measured evidence.

### b3 · HIGH
- **Source:** https://thescottking.com/aeo-vs-geo-vs-seo
- **Section:** What is genuinely different?
- **Anchor:** Most sites that lose retrieval access never decided to
- **Sentence:** "Most sites that lose retrieval access never decided to."
- **Block:** paragraph (Gutenberg). Full block text: "Retrieval and training access are separate decisions. You can block GPTBot from training on your content and still be cited by OAI-SearchBot. Most sites that lose retrieval access never decided to. Cloudflare began blocking AI crawlers by default on new domains in July 2025, and has since split the controls into search, agent and training categories."
- **Reason:** The pillar shows 29 of 31 two-day-blocked sites allowed AI search bots in robots.txt but blocked them at the firewall. That's the unintended loss this sentence describes.

### b4 · MEDIUM
- **Source:** https://thescottking.com/aeo-tactics-that-do-not-work
- **Section:** What should you do with the time you just saved?
- **Anchor:** Confirm retrieval crawlers can reach your pages
- **Sentence:** "Confirm retrieval crawlers can reach your pages."
- **Block:** paragraph (Gutenberg). Full block text: "Before any of it, confirm two things. Confirm retrieval crawlers can reach your pages. Confirm your primary claim sits in the initial HTML. The fix order matters more than the fix list."
- **Reason:** The pillar is the evidence and test for that check.
- **Note:** The same paragraph already links "The fix order matters more than the fix list" to /improve-brand-visibility-ai-search. The anchors and targets differ.

### b5 · MEDIUM
- **Source:** https://thescottking.com/why-ai-recommends-your-competitors
- **Section:** What do the results mean?
- **Anchor:** The engines probably cannot read your site at all
- **Sentence:** "The engines probably cannot read your site at all."
- **Block:** paragraph inside Classic content (no block markup). Full block text: "You appear nowhere, including on your own brand name. The engines probably cannot read your site at all. That is technical, and it is the cheaper problem to have. It is also the rarer one: in the 232-homepage study, only 13 sites refused a request carrying an AI crawler’s name, and one carried a noindex tag."
- **Reason:** The pillar measures exactly that technical failure across 3,877 sites.

## Excluded: child pages (no links in either direction)
None of these is published yet. Each folder holds only `research/`, and I found no matching live post or page.

1. C1: `/workspace/content-pipeline/aeo-crawl-c1-chatgpt-403/` (I asked ChatGPT to open 132 software sites. 34 blocked it two days running.)
2. C2: `/workspace/content-pipeline/aeo-crawl-c2-block-bots-publish-llms-txt/` (Why block AI bots and still publish an llms.txt?)
3. C3: `/workspace/content-pipeline/aeo-crawl-c3-chatgpt-javascript/` (Does ChatGPT read JavaScript? 71 software homepages say it matters)
4. C4: `/workspace/content-pipeline/aeo-crawl-c4-gptbot-vs-oai-searchbot/` (GPTBot vs OAI-SearchBot: what 3,515 software sites block)
5. C5: `/workspace/content-pipeline/aeo-crawl-c5-llms-txt-adoption/` (1,041 B2B software sites publish llms.txt. Does it matter?)
6. C6: `/workspace/content-pipeline/aeo-crawl-c6-compare-and-pricing-pages/` (Compare pages and pricing: what B2B software gives AI to quote)
7. C7: `/workspace/content-pipeline/aeo-crawl-c7-schema-for-ai-search/` (Schema for AI search: 1,096 homepages skip Organization schema)
8. C8: `/workspace/content-pipeline/aeo-crawl-c8-test-ai-crawler-access/` (Free AI crawler checkers overcount. Here's how to test properly.)

Note: /ai-crawlers-to-allow is a live post, not one of the children, even though C4 overlaps its topic.

## Dropped
- **"Ask ChatGPT to open your homepage and quote the headline" (pillar):** it appears twice (in the checkers section and the checklist), so it fails the exactly-once rule.
- **Pillar to /why-ai-recommends-your-competitors, /ai-visibility-tools-what-they-measure, /what-an-ai-visibility-audit-includes, /book-a-call and /tools:** none has a natural verbatim anchor in the pillar. The audit-guide link would also compete with the closing audit CTA.
- **Pillar to /positioning-ai-visibility-audit and /ai-crawlers-to-allow:** already linked.
- **Inbound from /what-an-ai-visibility-audit-includes:** the anchor "a firewall blocks at a layer robots.txt never shows" is valid (list item, appears once). I dropped it to keep the list tight, since it repeats the b1 and b2 idea. Use it as a low-priority extra if you want a sixth.
- **Inbound from /track-brand-mentions-ai-search:** the anchor "the engines cannot reach your pages at all" is valid, but the next sentence already links "That is a technical problem" to /aeo-vs-geo-vs-seo. Two links back to back would crowd the paragraph.
- **Inbound from /ai-visibility-tools-what-they-measure and /157-of-169…:** neither has a sentence about crawler access or firewalls.
- **Price:** none of the suggested anchors or sentences contains the audit price.

## Oct 30, 2026: external data link (approved by Owner)

- c1. Post <id>, first body paragraph (wp-block-paragraph) starting "I checked 3,877 US B2B software companies..."
  - Sentence: "I checked 3,877 US B2B software companies with 100+ employees as classified by Apollo (SIC 7372)."
  - Anchor: "3,877 US B2B software companies"
  - Target: https://github.com/thescottking/website-ai-visibility-data (HTTP 200, checked Oct 30, 2026 1:36 PM CT)
  - Only link to this target in the post. Do not also link the Methods and limits "Cohort:" bullet.

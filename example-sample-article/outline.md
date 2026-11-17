# Outline: aeo-crawl-pillar

Status: Step 2 (Outline), updated Oct 30, 2026 with AI Sameness Report's corrected package. Waiting for the owner's OK. Not drafted.
Sources: `research/findings.md` (F1 to F28 = Key findings 1 to 28 in the rebuilt file), `research/data.csv` (table ids in backticks), and `research/source/`. No company names appear here or in the article.

## Working title
What AI search engines actually see on 3,877 B2B software websites

Alternates for Step 3 to test (hooks.md picks the winner):
- What AI search engines actually see on 3,877 B2B software websites (GEO and AEO data, Oct 2026)
- We crawled 3,877 B2B software sites. Here is what ChatGPT can and can't read.

Cohort line (use verbatim near the top): "3,877 US B2B software companies with 100+ employees as classified by Apollo (SIC 7372); each figure counts only the sites where that check could run." (findings.md, Coverage)

## Focus question (answered in the first 2 to 3 sentences)
**Can AI search engines actually reach and read B2B software websites?**

Answer up front: at least 200 of 3,515 sites with a readable robots.txt block an AI training crawler, but only at least 35 of 3,517 block an AI search bot. The firewall is the bigger door: when we asked ChatGPT to open 132 sites a bot test had flagged, 34 blocked it on both Oct 29 and Oct 30, 2026. Use "GEO" and "AEO" both in the first paragraph (findings.md, Search demand context).

## H2s in order

### H2 1. What did we measure, and how? (GEO, AEO and the crawl)
- Timeline: Oct 27, 2026 original crawl; Oct 28 JavaScript-only check; Oct 29 two verified passes plus ChatGPT day one; Oct 30 live robots.txt and llms.txt recheck (RFC 9309 parser) plus ChatGPT day two.
- Base table (findings.md, Coverage; show "Sites reached" only, no cohort percentages):
  | Check | Sites reached |
  |---|---|
  | Readable homepage HTML | 3,236 |
  | robots.txt search-bot rules readable | 3,517 |
  | robots.txt training-bot rules readable | 3,515 |
  | GPTBot and OAI-SearchBot rules both readable | 3,516 |
  | Simulated-bot server test | 3,263 |
  | llms.txt | 3,233 |
  | llms-full.txt | 3,236 |
  | JavaScript-only classification | 3,218 |
  | Organization schema | 3,236 |
  | H1 | 3,236 |
  | Compare pages | 3,235 |
  | Pricing pages | 3,234 |
  | Sitemap freshness | 3,229 |
  | Case studies | 3,232 |
  | Docs | 3,236 |
  | Trust or security | 3,233 |
  | FAQPage and Software/Product schema | 3,236 |
  | Real ChatGPT test (flagged sites only) | 132 |
- Line: we measured what sites do, not what gets cited. No citation, prompt or log data.
- Chart: none (the table carries it).

### H2 2. Do B2B software sites block AI bots in robots.txt?
- F1: at least 200 of 3,515 block an AI training crawler from the homepage (5.7%). `robots_training`.
- F2: at least 35 of 3,517 block an AI search or answer bot (1.0%). `robots_search`.
- F3/F4: at least 117 of 3,516 block GPTBot; at least 22 of 3,517 block OAI-SearchBot. `gptbot`, `oai`.
- F5: 97 of 3,516 block GPTBot while allowing OAI-SearchBot, the split OpenAI documents. `split`.
- F6: 165 of 3,515 block a training bot but no search bot. `train_not_search`.
- Caveat in text: minimums, homepage path only, a rule shows intent, not bot behavior.
- Recommendation (Tier A, OpenAI bots doc): allow search bots; decide on training bots separately.
- Chart: **yes, Chart A.** Training-bot block 200 of 3,515 vs search-bot block 35 of 3,517, labeled "at least". Optional second panel: GPTBot 117 of 3,516 vs OAI-SearchBot 22 of 3,517. `robots_training`, `robots_search`, `gptbot`, `oai`.
- Sibling: C4.

### H2 3. Can ChatGPT open the page when robots.txt says yes?
- F7: 34 of 132 flagged sites blocked ChatGPT on both Oct 29 and Oct 30, 2026 (25.8%). `blocked_both`.
- F8 day-one split of the 132 (Oct 29): opened 79, blocked 35, fetch error 13, unclear 4, plus 1 inconsistent (opened Oct 28, blocked Oct 29) excluded. Day two retested the 35 day-one blocks; 34 held. `day1`.
- F12: 29 of 31 two-day-blocked sites with a readable robots.txt allow AI search bots there. `both_robots`. (Off hold: confirmed by AI Sameness Report.)
- F9, worded exactly: "On day one, ChatGPT still quoted 22 of the 34 blocked homepages from its search index." Use it to support the 403 caveat. Do not compare with day two. `index`.
- Caveat in text: the 132 are only sites a simulated-bot test flagged (out of 3,263 it reached). Never a share of the cohort. A 403 means ChatGPT couldn't open the page at that moment, not that the brand is invisible.
- Recommendation (Tier A, OpenAI, Perplexity, Google docs): allow AI search bots through the firewall and CDN, then test by asking ChatGPT to open a page.
- Chart: **yes, Chart B (built out).** Stacked bar or waterfall of the 132 flagged sites on day one: opened 79, blocked 35, fetch error 13, unclear 4, inconsistent 1 (excluded, shown greyed). Callout on the blocked segment: 34 of the 35 blocked again on Oct 30. `day1` plus `blocked_both`. No 36 anywhere.
- Siblings: C1, C2.

### H2 4. Why do free AI crawler checkers overcount blocks?
- F10: real ChatGPT opened 79 of 132 sites a simulated-bot test had flagged (59.8%), Oct 29, 2026. `opened`.
- Explain: spoofed user agent from a non-vendor IP vs the real bot from vendor IP ranges (F10 caveat; methods.md).
- How to test: ask ChatGPT to open the URL and quote the headline.
- Chart: **yes, Chart C.** Of 132 flagged: opened 79 vs not opened 53. `opened`. (If Chart B runs, C can be cut as redundant; Visuals' call with Owner.)
- Sibling: C8.

### H2 5. Why block ChatGPT and still publish an llms.txt?
- F11: 13 of the 34 two-day-blocked sites publish an llms.txt (38.2%). `both_llms`. Counts only, no "most". Small base.
- F20 minor line: 4 of 1,035 llms.txt publishers with a readable robots.txt also block AI search bots. `llms_block`.
- F21 context, not a contradiction: 75 of 1,035 llms.txt publishers block AI training bots. `llms_block_train`.
- Angle: the team that writes llms.txt and the team that runs the firewall don't talk.
- Chart: none.
- Sibling: C2.

### H2 6. Can AI read your homepage without JavaScript?
- F13: 71 of 3,218 homepages send under 50 words of text before JavaScript runs (2.2%). `js`. 7 of those 71 publish an llms.txt (question-data-map.csv).
- F14: 360 of 3,236 homepages have no H1 in the server HTML (11.1%). `no_h1`. 235 of the 360 have an H2.
- Recommendation (Tier B, Vercel and MERJ, Dec 17, 2024): server-render the content you want AI to read.
- Chart: **yes, Chart D.** JS-only 71 of 3,218 and no H1 360 of 3,236, each on its own base. `js`, `no_h1`.
- Sibling: C3.

### H2 7. Do B2B software sites tell AI who they are? (schema and llms.txt)
- F15: 1,096 of 3,236 homepages have no Organization schema in the server HTML (33.9%). `no_org`.
- F16/F17: FAQPage schema on 247 of 3,236 (7.6%); SoftwareApplication or Product schema on 423 of 3,236 (13.1%). `faq`, `swprod`.
- F18: 1,041 of 3,233 readable sites publish an llms.txt (32.2%). `llms`.
- F19: 147 of 3,236 publish an llms-full.txt (4.5%). `llms_full`.
- Required framing: adoption only. Never claim llms.txt or schema increases citations. Cite Google's "no special AI files or schema needed" (Tier A) and Ahrefs June 15, 2026: 97% of llms.txt files got zero fetches in May 2026 (Tier C).
- Chart: **yes, Chart E.** Adoption bars, each on its own base: Organization schema present 2,140 of 3,236, llms.txt 1,041 of 3,233, SoftwareApplication/Product 423 of 3,236, FAQPage 247 of 3,236, llms-full.txt 147 of 3,236. `no_org`, `llms`, `swprod`, `faq`, `llms_full`.
- Siblings: C5, C7.

### H2 8. Do you have the pages buyers ask AI about?
- F22: 580 of 3,235 host or link to a compare, vs or alternatives page (17.9%). `compare`.
- F23: at least 1,207 of 3,234 publish a pricing page (37.3%). `pricing`.
- F24: 407 of 3,233 have both a compare page and a pricing page (12.6%). `cmp_pr`.
- F25 to F27 (final): case studies 1,759 of 3,232 (54.4%); trust or security 1,369 of 3,233 (42.3%); docs 537 of 3,236 (16.6%). `case`, `trust`, `docs`.
- Caveat: presence only, link-word matching, page counts are floors.
- Chart: **yes, Chart F (built out).** Horizontal bars, sorted, each labeled with its own base: case studies 1,759 of 3,232; trust or security 1,369 of 3,233; pricing 1,207 of 3,234; compare/vs/alternatives 580 of 3,235; docs 537 of 3,236; compare plus pricing 407 of 3,233. `case`, `trust`, `pricing`, `compare`, `docs`, `cmp_pr`.
- Sibling: C6.

### H2 9. Does sitemap freshness matter? (short, or fold into H2 8)
- F28: 2,127 of 3,229 sitemaps show a lastmod date in the 90 days before the crawl (65.9%). `sitemap`. Weak signal: CMS auto-stamps dates.
- Recommendation (Tier C, Ahrefs July 28, 2025): update pages in substance; changing dates alone isn't supported.
- Chart: none.

### H2 10. What can't this data tell you?
- No citation, prompt or log data. We can't say how to rank in ChatGPT, whether llms.txt or schema raises citations, or whether bots obey robots.txt.
- Outside studies with tiers: GEO paper (KDD 2024, Tier B), Ahrefs brand mentions 0.664 vs 0.218 backlinks (Tier C, correlation only), Seer 87% SearchGPT/Bing match (Tier C).
- Chart: none.

### H2 11. What should a B2B software team check this week?
- Numbered checklist from Tier A/B recommendations: (1) ask ChatGPT to open your homepage and quote the headline, (2) check firewall and CDN rules for AI search bots, not only robots.txt, (3) decide training and search bots separately, (4) curl your homepage and confirm the text is in the server HTML, (5) verify in Bing Webmaster Tools (Tier C, "the evidence points to").
- Chart: none.

### Methods and limits (closing section, not a question H2)
- Method summary and Limits from findings.md, plus the exclusion note: unread sites had lower llms.txt use, so never extrapolate to 3,877.

## Charts summary (for Visuals Studio, Step 5)
| Chart | Section | Shows | data.csv table(s) |
|---|---|---|---|
| A | H2 2 | Training vs search bot blocks (plus GPTBot vs OAI-SearchBot), "at least" | robots_training, robots_search, gptbot, oai |
| B | H2 3 | Day-one verdicts on 132 flagged sites; 34 blocked both days | day1, blocked_both |
| C | H2 4 | 79 of 132 flagged sites opened in real ChatGPT | opened |
| D | H2 6 | JS-only homepages and missing H1 | js, no_h1 |
| E | H2 7 | Schema and llms.txt adoption | no_org, llms, swprod, faq, llms_full |
| F | H2 8 | Buyer pages: case studies, trust, pricing, compare, docs, compare plus pricing | case, trust, pricing, compare, docs, cmp_pr |
Every chart labels its own denominator. No chart uses 3,877 as a base. No chart names a company. No chart shows 36.

## FAQ plan (WordPress Coordinator builds FAQPage in 7b; final wording from hooks.md and People Also Ask)
1. How many B2B software companies block AI crawlers? At least 200 of 3,515 block a training bot; at least 35 of 3,517 block a search bot (F1, F2).
2. Why can't ChatGPT access my site? Firewall or CDN rules can refuse ChatGPT even when robots.txt allows it; 29 of 31 two-day-blocked sites with a readable robots.txt allowed AI search bots (F7, F12).
3. Does a 403 mean my brand is invisible in ChatGPT? No. "On day one, ChatGPT still quoted 22 of the 34 blocked homepages from its search index." (F9)
4. Should I block GPTBot? Training is a separate choice from search, per OpenAI's docs; 97 of 3,516 block GPTBot while allowing OAI-SearchBot (F5).
5. Does ChatGPT read JavaScript? Major AI crawlers read server HTML only (Vercel/MERJ); 71 of 3,218 homepages send under 50 words before JavaScript (F13).
6. Is llms.txt worth it? 1,041 of 3,233 publish one; studies found no citation lift; our data measures adoption only (F18).
7. What is the difference between AEO and GEO? Framing only, both terms used.

## Planned sibling links (planned, not live; link only once each is published)
- H2 3: C1 "We asked ChatGPT to open 132 software sites. 34 blocked it two days running." (`aeo-crawl-c1-chatgpt-403/`)
- H2 3 and H2 5: C2 "Why block AI bots and still publish an llms.txt?" (`aeo-crawl-c2-block-bots-publish-llms-txt/`)
- H2 6: C3 "Does ChatGPT read JavaScript? 71 software homepages say it matters" (`aeo-crawl-c3-chatgpt-javascript/`)
- H2 2: C4 "GPTBot vs OAI-SearchBot: what 3,515 software sites block" (`aeo-crawl-c4-gptbot-vs-oai-searchbot/`)
- H2 7: C5 "1,041 B2B software sites publish llms.txt. Does it matter?" (`aeo-crawl-c5-llms-txt-adoption/`)
- H2 8: C6 "Compare pages and pricing: what B2B software gives AI to quote" (`aeo-crawl-c6-compare-and-pricing-pages/`)
- H2 7: C7 "Schema for AI search: 1,096 homepages skip Organization schema" (`aeo-crawl-c7-schema-for-ai-search/`)
- H2 4: C8 "Free AI crawler checkers overcount. Here's how to test properly." (`aeo-crawl-c8-test-ai-crawler-access/`)
Draft carries these as placeholders; Internal Linker (Step 6) swaps in live URLs as children publish.

## Proposed CTA
cta: AI visibility audit page

Why: the core finding is that a site can't tell from robots.txt or a free checker whether ChatGPT can open it. An audit answers that for one company. The plugin services page fits an implementation reader and B2B PMM Skills fits a positioning reader; neither matches this pillar's question. CTA offers a check of the reader's own site, with no price and no follow-me line.

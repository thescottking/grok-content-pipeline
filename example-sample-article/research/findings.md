# Research findings: What AI search engines actually see on 3,877 B2B software websites

Slug: `aeo-crawl-pillar`. Built Oct 30, 2026 from `<research-dir>/master/master.csv` (post live recheck). Every number below was recomputed from that file by `<research-dir>/master/pipeline/metrics.py`. Status: research only, not handed to Article Writer.

## Working title
What AI search engines actually see on 3,877 B2B software websites

## Target questions
| Question | Type | Demand evidence | Source |
|---|---|---|---|
| does content freshness matter for AI search | does X matter | SISTRIX Oct 2026 found year-in-title signal; weak search demand | https://bediscoverable.ai/resources/geo-tactics-ai-citations-study |
| AEO vs GEO / what is generative engine optimization | what | Keyword Planner via Zumi (Oct 8 2026): GEO 4,400/mo US, AEO 2,400/mo US, 'aeo vs geo' 1,600/mo US | https://www.zumihq.com/blog/aeo-vs-geo |
| how to rank in ChatGPT / brand mentions in ChatGPT | how to | Frequent autocomplete (demand-map.md) |  |
| do AI bots ignore robots.txt | why | Practitioner forums (demand-map.md) |  |
| how many companies block AI crawlers | how many | Medium; news-driven | https://developers.cloudflare.com/bots/additional-configurations/block-ai-bots/ |

Search demand context: Google Keyword Planner volumes published by Zumi on Oct 8, 2026: "generative engine optimization" 4,400 a month in the US, "answer engine optimization" 2,400, "aeo vs geo" 1,600 (https://www.zumihq.com/blog/aeo-vs-geo). Use both GEO and AEO early.

## Key findings

### 1. robots.txt blocks an AI training bot
- Number: 200
- Denominator: 3,515
- Share: 5.7%
- Test date: robots.txt rechecked live Oct 30, 2026 (RFC 9309 parser)
- Safe wording: At least 200 of 3,515 sites with a readable robots.txt block an AI training crawler from the homepage.
- Caveat: Minimum. Checks only whether the homepage path is disallowed, only on sites whose robots.txt could be read, parsed with an RFC 9309 parser. A robots.txt rule shows intent, not what bots actually do.
- Chart table: `robots_training` in data.csv

### 2. robots.txt blocks an AI search bot
- Number: 35
- Denominator: 3,517
- Share: 1.0%
- Test date: robots.txt rechecked live Oct 30, 2026 (RFC 9309 parser)
- Safe wording: At least 35 of 3,517 sites with a readable robots.txt block an AI search or answer bot from the homepage.
- Caveat: Minimum. Checks only whether the homepage path is disallowed, only on sites whose robots.txt could be read, parsed with an RFC 9309 parser. A robots.txt rule shows intent, not what bots actually do.
- Chart table: `robots_search` in data.csv

### 3. robots.txt blocks GPTBot
- Number: 117
- Denominator: 3,516
- Share: 3.3%
- Test date: robots.txt rechecked live Oct 30, 2026 (RFC 9309 parser)
- Safe wording: At least 117 of 3,516 block GPTBot in robots.txt.
- Caveat: Minimum. Checks only whether the homepage path is disallowed, only on sites whose robots.txt could be read, parsed with an RFC 9309 parser. A robots.txt rule shows intent, not what bots actually do.
- Chart table: `gptbot` in data.csv

### 4. robots.txt blocks OAI-SearchBot
- Number: 22
- Denominator: 3,517
- Share: 0.6%
- Test date: robots.txt rechecked live Oct 30, 2026 (RFC 9309 parser)
- Safe wording: At least 22 of 3,517 block OAI-SearchBot, the bot ChatGPT search uses.
- Caveat: Minimum. Checks only whether the homepage path is disallowed, only on sites whose robots.txt could be read, parsed with an RFC 9309 parser. A robots.txt rule shows intent, not what bots actually do.
- Chart table: `oai` in data.csv

### 5. Block GPTBot but allow OAI-SearchBot
- Number: 97
- Denominator: 3,516
- Share: 2.8%
- Test date: robots.txt rechecked live Oct 30, 2026 (RFC 9309 parser)
- Safe wording: 97 of 3,516 block GPTBot while allowing OAI-SearchBot, the split OpenAI documents.
- Caveat: Minimum. Checks only whether the homepage path is disallowed, only on sites whose robots.txt could be read, parsed with an RFC 9309 parser. A robots.txt rule shows intent, not what bots actually do.
- Chart table: `split` in data.csv

### 6. Block a training bot but no search bot
- Number: 165
- Denominator: 3,515
- Share: 4.7%
- Test date: robots.txt rechecked live Oct 30, 2026 (RFC 9309 parser)
- Safe wording: 165 of 3,515 block at least one AI training bot and no AI search bot.
- Caveat: Minimum. Checks only whether the homepage path is disallowed, only on sites whose robots.txt could be read, parsed with an RFC 9309 parser. A robots.txt rule shows intent, not what bots actually do.
- Chart table: `train_not_search` in data.csv

### 7. ChatGPT blocked on both test days
- Number: 34
- Denominator: 132
- Share: 25.8%
- Test date: ChatGPT tests on Oct 29 and Oct 30, 2026
- Safe wording: When we asked ChatGPT to open 132 B2B software sites a bot test had flagged, 34 blocked it on both Oct 29 and Oct 30, 2026.
- Caveat: Only the sites a simulated-bot test flagged were tested, so never present this as a share of the full cohort. A 403 means ChatGPT could not open the page at that moment; it does not mean the brand is invisible, since ChatGPT can still describe a site from its search index. One site flipped between days and one returned an unclear 'restricted URL' on day two; both are excluded.
- Chart table: `blocked_both` in data.csv

### 8. Day-one ChatGPT verdicts on flagged sites
- Number: 35
- Denominator: 132
- Share: 26.5%
- Test date: Oct 29, 2026 (the inconsistent site first opened Oct 28)
- Safe wording: On day one, ChatGPT opened 79 of 132 flagged sites and was blocked at 35 of 132; 13 were fetch errors, 4 unclear, and 1 site opened on Oct 28 and was blocked on Oct 29 (inconsistent, excluded). Counting that site gives 36 of 132; do not use that figure.
- Caveat: Only the sites a simulated-bot test flagged were tested, so never present this as a share of the full cohort. A 403 means ChatGPT could not open the page at that moment; it does not mean the brand is invisible, since ChatGPT can still describe a site from its search index. One site flipped between days and one returned an unclear 'restricted URL' on day two; both are excluded.
- Chart table: `day1` in data.csv

### 9. ChatGPT quoted the homepage from its search index after the 403
- Number: 22
- Denominator: 34
- Share: 64.7%
- Test date: Oct 29 and Oct 30, 2026
- Safe wording: On day one, ChatGPT quoted a homepage headline from its search index for 22 of 34 two-day-blocked sites after its direct request got a 403; 4 more got only the page title. On day two it quoted none (0 of 34), with a stricter prompt and a signed-in session.
- Caveat: Read by hand from screenshots. Day-one and day-two prompts and sessions differed, so the days are not comparable. Shows ChatGPT can still describe a blocked site from older indexed copies, which may be stale. Says nothing about citations.
- Chart table: `index` in data.csv

### 10. Real ChatGPT opened sites a simulated-bot test flagged
- Number: 79
- Denominator: 132
- Share: 59.8%
- Test date: Oct 29, 2026
- Safe wording: ChatGPT opened 79 of 132 sites that a simulated-bot test had flagged as blocking AI.
- Caveat: The simulated-bot test reached 3,263 sites and flagged 132. Simulated-bot tests send a bot user agent from a non-vendor IP; firewalls that verify vendor IPs treat them differently from the real bot. Day-one verdicts.
- Chart table: `opened` in data.csv

### 11. Two-day blocked sites that publish llms.txt
- Number: 13
- Denominator: 34
- Share: 38.2%
- Test date: ChatGPT tests on Oct 29 and Oct 30, 2026; llms.txt rechecked live Oct 30, 2026
- Safe wording: 13 of 34 sites that blocked ChatGPT on both test days publish an llms.txt file written for AI tools.
- Caveat: Small base. Only the sites a simulated-bot test flagged were tested, so never present this as a share of the full cohort. A 403 means ChatGPT could not open the page at that moment; it does not mean the brand is invisible, since ChatGPT can still describe a site from its search index. One site flipped between days and one returned an unclear 'restricted URL' on day two; both are excluded.
- Chart table: `both_llms` in data.csv

### 12. Two-day blocked sites whose robots.txt allows AI search bots
- Number: 29
- Denominator: 31
- Share: 93.5%
- Test date: ChatGPT tests on Oct 29 and Oct 30, 2026
- Safe wording: 29 of 31 sites with a readable robots.txt invited AI search bots there and still blocked ChatGPT at the server on both test days.
- Caveat: 3 of the 34 had no readable robots.txt. Homepage path only. Only the sites a simulated-bot test flagged were tested, so never present this as a share of the full cohort. A 403 means ChatGPT could not open the page at that moment; it does not mean the brand is invisible, since ChatGPT can still describe a site from its search index. One site flipped between days and one returned an unclear 'restricted URL' on day two; both are excluded.
- Chart table: `both_robots` in data.csv

### 13. JavaScript-only homepages
- Number: 71
- Denominator: 3,218
- Share: 2.2%
- Test date: Oct 28, 2026 (two residential passes plus headless render)
- Safe wording: 71 of 3,218 homepages send under 50 words of text before JavaScript runs.
- Caveat: Confirmed across two crawl passes plus a headless render check; sites we could not classify are excluded. Homepage only.
- Chart table: `js` in data.csv

### 14. No H1 in server HTML
- Number: 360
- Denominator: 3,236
- Share: 11.1%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: 360 of 3,236 homepages have no H1 in the HTML the server sends.
- Caveat: Read from the HTML the server sends, before JavaScript runs. Elements added later by JavaScript are missed, which is also what most AI crawlers see.
- Chart table: `no_h1` in data.csv

### 15. No Organization schema in server HTML
- Number: 1,096
- Denominator: 3,236
- Share: 33.9%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: 1,096 of 3,236 homepages have no Organization schema in the HTML the server sends.
- Caveat: Read from the HTML the server sends, before JavaScript runs. Elements added later by JavaScript are missed, which is also what most AI crawlers see. No proven effect on AI citations.
- Chart table: `no_org` in data.csv

### 16. FAQPage schema
- Number: 247
- Denominator: 3,236
- Share: 7.6%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: 247 of 3,236 homepages carry FAQPage schema.
- Caveat: Read from the HTML the server sends, before JavaScript runs. Elements added later by JavaScript are missed, which is also what most AI crawlers see.
- Chart table: `faq` in data.csv

### 17. SoftwareApplication or Product schema
- Number: 423
- Denominator: 3,236
- Share: 13.1%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: 423 of 3,236 homepages carry SoftwareApplication or Product schema.
- Caveat: Read from the HTML the server sends, before JavaScript runs. Elements added later by JavaScript are missed, which is also what most AI crawlers see.
- Chart table: `swprod` in data.csv

### 18. llms.txt adoption
- Number: 1,041
- Denominator: 3,233
- Share: 32.2%
- Test date: rechecked live Oct 30, 2026
- Safe wording: 1,041 of 3,233 readable sites publish an llms.txt file (32.2%).
- Caveat: Sites we could not read had lower llms.txt use, so use the readable denominator. Shows what sites do, not whether it works. No citation, prompt or log data.
- Chart table: `llms` in data.csv

### 19. llms-full.txt adoption
- Number: 147
- Denominator: 3,236
- Share: 4.5%
- Test date: rechecked live Oct 30, 2026
- Safe wording: 147 of 3,236 sites publish an llms-full.txt file.
- Caveat: No AI platform documents using llms-full.txt. Shows what sites do, not whether it works. No citation, prompt or log data.
- Chart table: `llms_full` in data.csv

### 20. llms.txt publishers that block AI search bots in robots.txt
- Number: 4
- Denominator: 1,035
- Share: 0.4%
- Test date: robots.txt rechecked live Oct 30, 2026 (RFC 9309 parser)
- Safe wording: 4 of 1,035 llms.txt publishers with a readable robots.txt also tell AI search bots to stay out of the homepage.
- Caveat: Very small count; use as a supporting line only. Minimum. Checks only whether the homepage path is disallowed, only on sites whose robots.txt could be read, parsed with an RFC 9309 parser. A robots.txt rule shows intent, not what bots actually do.
- Chart table: `llms_block` in data.csv

### 21. llms.txt publishers that block AI training bots in robots.txt
- Number: 75
- Denominator: 1,035
- Share: 7.2%
- Test date: robots.txt rechecked live Oct 30, 2026 (RFC 9309 parser)
- Safe wording: 75 of 1,035 llms.txt publishers with a readable robots.txt block at least one AI training bot from the homepage.
- Caveat: Not a contradiction: training and answer access are separate jobs. Minimum. Checks only whether the homepage path is disallowed, only on sites whose robots.txt could be read, parsed with an RFC 9309 parser. A robots.txt rule shows intent, not what bots actually do.
- Chart table: `llms_block_train` in data.csv

### 22. Compare, vs or alternatives pages
- Number: 580
- Denominator: 3,235
- Share: 17.9%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: 580 of 3,235 sites host or link to a compare, vs or alternatives page.
- Caveat: Matched on link words such as 'vs' and 'alternatives', so it may include some unrelated pages and miss differently named ones. Presence only, no citation data.
- Chart table: `compare` in data.csv

### 23. Pricing page
- Number: 1,207
- Denominator: 3,234
- Share: 37.3%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: At least 1,207 of 3,234 sites publish a pricing page.
- Caveat: Minimum: only common pricing URLs and links were checked. Presence only.
- Chart table: `pricing` in data.csv

### 24. Compare page and pricing page
- Number: 407
- Denominator: 3,233
- Share: 12.6%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: 407 of 3,233 sites have both a compare page and a pricing page.
- Caveat: Inherits the compare and pricing caveats.
- Chart table: `cmp_pr` in data.csv

### 25. Case studies page
- Number: 1,759
- Denominator: 3,232
- Share: 54.4%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: 1,759 of 3,232 sites link to case studies or customer stories.
- Caveat: Link and URL match. Presence only.
- Chart table: `case` in data.csv

### 26. Docs page
- Number: 537
- Denominator: 3,236
- Share: 16.6%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: 537 of 3,236 sites link to public documentation.
- Caveat: Link and URL match. Presence only.
- Chart table: `docs` in data.csv

### 27. Trust or security page
- Number: 1,369
- Denominator: 3,233
- Share: 42.3%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: 1,369 of 3,233 sites link to a trust or security page.
- Caveat: Link and URL match. Presence only.
- Chart table: `trust` in data.csv

### 28. Sitemap updated in the last 90 days
- Number: 2,127
- Denominator: 3,229
- Share: 65.9%
- Test date: Oct 29, 2026 (two verified crawl passes)
- Safe wording: 2,127 of 3,229 sitemaps show a lastmod date in the 90 days before the crawl.
- Caveat: Weak signal: sitemap dates are often auto-stamped by the CMS.
- Chart table: `sitemap` in data.csv

## Recommendations (from outside sources)
Our crawl shows what companies do. These recommendations rest on the sources named. Tier A and B items can be said as "you should"; tier C and D as "the evidence points to" or "unproven".

- **Let AI search bots through your firewall and CDN as well as robots.txt, then test by asking ChatGPT to open a page.** Tier A (platform documentation). Source: OpenAI, "Overview of OpenAI Crawlers", https://platform.openai.com/docs/bots (live doc, read Oct 30, 2026). Evidence: "we recommend allowing OAI-SearchBot in your site's robots.txt file and allowing requests from our published IP ranges below."
- **Allow AI search bots; decide on training bots separately.** Tier A (platform documentation). Source: OpenAI, "Overview of OpenAI Crawlers", https://platform.openai.com/docs/bots (live doc, read Oct 30, 2026). Evidence: "a webmaster can allow OAI-SearchBot in order to appear in search results while disallowing GPTBot." And: "Sites that are opted out of OAI-SearchBot will not be shown in ChatGPT search answers."
- **Server-render the content you want AI to read.** Tier B (large vendor log study). Source: Vercel and MERJ, "The rise of the AI crawler", https://vercel.com/blog/the-rise-of-the-ai-crawler (Dec 17, 2024). Evidence: "none of the major AI crawlers currently render JavaScript" (OAI-SearchBot, ChatGPT-User, GPTBot, ClaudeBot, PerplexityBot). Gemini and AppleBot do render. 569 million GPTBot fetches in a month.
- **Put sourced statistics, quotes and citations in your pages.** Tier B (peer-reviewed). Source: Aggarwal et al., "GEO: Generative Engine Optimization", KDD 2024, https://arxiv.org/abs/2311.09735 (2024). Evidence: "including citations, quotations from relevant sources, and statistics can significantly boost source visibility, with an increase of over 40%." Lab setup; measures visibility inside answers, not traffic.
- **Start from SEO fundamentals; no special AI markup or AI text files are required.** Tier A (platform documentation). Source: Google, "AI features and your website", https://developers.google.com/search/docs/appearance/ai-features (live doc, read Oct 30, 2026). Evidence: "You don't need to create new machine readable files, AI text files, or markup to appear in these features. There's also no special schema.org structured data that you need to add."
- **Earn mentions on other sites.** Tier C (vendor correlation study). Source: Ahrefs, "An Analysis of AI Overview Brand Visibility Factors (75K Brands Studied)", https://ahrefs.com/blog/ai-overview-brand-correlation/ (May 26, 2025). Evidence: Branded web mentions correlated 0.664 with AI Overview visibility versus 0.218 for backlinks; Ahrefs notes "correlation ≠ causation."
- **Verify your site in Bing Webmaster Tools.** Tier C (small vendor study). Source: Seer Interactive, "87% of SearchGPT Citations Match Bing's Top Results", https://www.seerinteractive.com/insights/87-percent-of-searchgpt-citations-match-bings-top-results (updated Mar 27, 2025). Evidence: 87% of SearchGPT citations matched Bing top results (about 500 citations).
- **Update pages in substance on a schedule; changing dates alone is not supported.** Tier C (vendor study). Source: Ahrefs, "AI Assistants Prefer to Cite Fresher Content (17 Million Citations Analyzed)", https://ahrefs.com/blog/do-ai-assistants-prefer-to-cite-fresh-content/ (July 28, 2025). Evidence: AI-cited URLs averaged 1,064 days old vs 1,432 for organic results, "25.7% fresher."
- **Do not publish llms.txt expecting more citations.** Tier C (vendor studies) plus A (Google). Source: Ahrefs, "We Analyzed 137K Sites: 97% of llms.txt Files Never Get Read", https://ahrefs.com/blog/llmstxt-study/ (June 15, 2026). Evidence: 97% of llms.txt files got zero fetches in May 2026.

## Do not say
- Never name any company as blocking, offending or missing something. Public articles name no companies; names stay in the private source files for one-to-one outreach.
- Never use 3,877 as the base for a check. State the readable denominator given for each finding.
- Never present the ChatGPT result as a share of the whole cohort. It is 34 of 132 sites tested after a simulated-bot test flagged them.
- Never claim llms.txt, llms-full.txt, schema or any other on-site element increases AI citations. Our data shows what companies do, not what works.
- A 403 means ChatGPT could not open the page. Never say the brand is invisible in ChatGPT.
- Call the cohort "US B2B software companies with 100+ employees as classified by Apollo (SIC 7372)".
- robots.txt numbers are minimums for the homepage path. Say "at least".
- Use exact counts with denominators. No "9 in 10", no "most" or "nearly all" without the count.
- Never use simulated-bot results alone as proof of blocking.
- No pricing for the audit in the article. No follow-me CTAs.

## Method summary
- Cohort: 3,877 US B2B software companies with 100+ employees as classified by Apollo (SIC 7372), pulled from Apollo with the B2B tag.
- Crawl: homepage, robots.txt, llms.txt, llms-full.txt and sitemap fetched on Oct 27, 2026 in two passes. 3,236 of 3,877 homepages returned readable HTML; the rest are excluded per check.
- Each check counts only sites where that check could run (status confirmed in master.csv); that is why denominators differ by check.
- robots.txt and llms.txt were rechecked live on Oct 30, 2026 and parsed with an RFC 9309 parser (Python's built-in parser misreads blank lines and `Disallow: /?`).
- Simulated-bot server test flagged 132 sites. Each was then tested by asking ChatGPT, in a temporary chat, to open the URL and quote the headline (Oct 29, 2026), and the day-one blocks were retested Oct 30, 2026. Only sites blocked both days count as blocked. Screenshots exist for every verdict.
- JavaScript-only: under 50 words of server HTML text, confirmed over two passes and a headless render.
- No citation, prompt or server log data. Nothing here measures whether any element gets a site cited.

## Coverage: how many sites each check reached
| Check | Sites reached | Of cohort |
|---|---|---|
| Readable homepage HTML | 3,236 | 3,877 |
| robots.txt search-bot rules readable | 3,517 | 3,877 |
| robots.txt training-bot rules readable | 3,515 | 3,877 |
| GPTBot and OAI-SearchBot rules both readable | 3,516 | 3,877 |
| Simulated-bot server test | 3,263 | 3,877 |
| llms.txt | 3,233 | 3,877 |
| llms-full.txt | 3,236 | 3,877 |
| JavaScript-only classification | 3,218 | 3,877 |
| Organization schema | 3,236 | 3,877 |
| H1 | 3,236 | 3,877 |
| Compare pages | 3,235 | 3,877 |
| Pricing pages | 3,234 | 3,877 |
| Sitemap freshness | 3,229 | 3,877 |
| Case studies | 3,232 | 3,877 |
| Docs | 3,236 | 3,877 |
| Trust or security | 3,233 | 3,877 |
| FAQPage and Software/Product schema | 3,236 | 3,877 |
| Real ChatGPT test (flagged sites only) | 132 | 3,877 |

Day-two ChatGPT retest covered the 35 day-one blocks.

Suggested line: "3,877 US B2B software companies with 100+ employees as classified by Apollo (SIC 7372); each figure counts only the sites where that check could run."

## Limits
- No citation, prompt or log data: we cannot say what gets a site cited, how to rank in ChatGPT, or whether bots obey robots.txt.
- robots.txt figures are minimums for the homepage path.
- HTML checks read server HTML only.
- The ChatGPT test covers only the flagged sites, over two days.
- Sites we could not read had lower llms.txt use, so unread sites are excluded instead of counted as "no".
- Full method: `source/methods.md`; audit trail: `source/audit.md`.

## Internal links
- Pillar: `/workspace/content-pipeline/aeo-crawl-pillar/` (What AI search engines actually see on 3,877 B2B software websites)
- C1: `/workspace/content-pipeline/aeo-crawl-c1-chatgpt-403/` (We asked ChatGPT to open 132 software sites. 34 blocked it two days running.)
- C2: `/workspace/content-pipeline/aeo-crawl-c2-block-bots-publish-llms-txt/` (Why block AI bots and still publish an llms.txt?)
- C3: `/workspace/content-pipeline/aeo-crawl-c3-chatgpt-javascript/` (Does ChatGPT read JavaScript? 71 software homepages say it matters)
- C4: `/workspace/content-pipeline/aeo-crawl-c4-gptbot-vs-oai-searchbot/` (GPTBot vs OAI-SearchBot: what 3,515 software sites block)
- C5: `/workspace/content-pipeline/aeo-crawl-c5-llms-txt-adoption/` (1,041 B2B software sites publish llms.txt. Does it matter?)
- C6: `/workspace/content-pipeline/aeo-crawl-c6-compare-and-pricing-pages/` (Compare pages and pricing: what B2B software gives AI to quote)
- C7: `/workspace/content-pipeline/aeo-crawl-c7-schema-for-ai-search/` (Schema for AI search: 1,096 homepages skip Organization schema)
- C8: `/workspace/content-pipeline/aeo-crawl-c8-test-ai-crawler-access/` (Free AI crawler checkers overcount. Here's how to test properly.)
- The pillar links down to every child from its matching section; every child links back up.

# hooks.md: aeo-crawl-pillar (Step 3, Search check)

Built Oct 30, 2026, 9:40 AM CDT by Article Writer, from the approved outline.md. Every number below matches outline.md.

## Evidence status
| Source | Result |
|---|---|
| (a) Search Console, the owner's site | **Not reached at first pass.** No Search Console export was available yet. No GSC numbers are used in the rankings below. |
| (b) Google Trends | **Failed.** Public API returned HTTP 429 (Too Many Requests) from the box. No Trends readings used. |
| (c) Google autocomplete | **Worked.** suggestqueries.google.com, client=firefox, Oct 30, 2026. Raw results below. |
| (d) People Also Ask | **Failed.** Google SERP fetched (HTTP 200) but returned no "People also ask" block to a non-browser request. No live PAA used. |

So the rankings below rest on autocomplete only, plus the outline's data strength. Rankings should be rechecked once Search Console data exists.

## Raw autocomplete evidence (Oct 30, 2026)
- `ai crawler`: ai crawlers, ai crawlers meaning, ai crawler free, ai crawler checker, ai crawler access, ai crawler user agents, ai crawlers impact on websites, ai crawlers robots txt, ai crawler access checker, ai crawler bots
- `block gptbot`: block gptbot, block gptbot robots txt, nginx block gptbot, cloudflare block gptbot, should i block gptbot
- `oai-searchbot`: oai-searchbot, oai searchbot robots txt, oai searchbot 1.3, oai searchbot user agent, oai searchbot at openai com, oai searchbot 1.0, oai searchbot vs chatgpt user, oai searchbot gptbot activity comparison, oai searchbot vs gptbot, oai searchbot crawler
- `llms.txt`: llms.txt, llms.txt file, llms.txt what is it, llms.txt generator, llms.txt example, llms.txt standard, llms.txt file generator, llms.txt checker, llms.txt best practices, llms.txt vs robots.txt
- `is llms.txt`: is llms.txt used, is llms.txt important, is llms.txt worth it, is llms.txt a thing, is llms txt a standard, is llms txt actually used, is llm txt useful, does llms txt work, what is llms txt file
- `chatgpt can't access my website`: can chatgpt access my website, can chatgpt access website, why can't chatgpt access my website, can chatgpt log into a website
- `chatgpt 403`: chatgpt 403 error, chatgpt 403, chatgpt 403 forbidden, chatgpt 403 forbidden error, chatgpt 403 error app, chatgpt 403 error code, chatgpt 403 iphone, chatgpt 403 login, chatgpt 403 request (mostly user-side errors, not site owners)
- `can chatgpt read javascript` / `does chatgpt read javascript`: can chatgpt read javascript, can chatgpt read .js files
- `how many websites block ai`: how many news websites block ai crawlers (only on-topic suggestion)
- `ai search engines`: ai search engines, list, free, like chatgpt, ranked, for research, other than chatgpt, names, examples, available
- `generative engine optimization`: (geo), meaning, how to dominate ai search, course, tools, vs answer engine optimization, agency, companies, services
- `answer engine optimization`: (aeo), course, certification, jobs, definition, examples, services, tools, and generative engine optimization
- `geo seo`: geo seo meaning, geo seo aeo, geo seo aeo meaning, geo seo ai
- `ai visibility`: ai visibility tools, score, checker, audit, report, agency, index, tracking, tracker
- `aeo`: dominated by unrelated terms (aeon flux, aeolus); bare "aeo" is ambiguous
- `ai search visibility b2b`, `ai crawlers b2b`: **no suggestions** (B2B qualifiers have no autocomplete demand)

Readings:
1. "ai crawler(s)" is the deepest crawler phrase (10 of 10, incl. "access", "checker", "robots txt").
2. "can chatgpt access my website" and "why can't chatgpt access my website" exist as site-owner phrasings.
3. "should i block gptbot" and "oai searchbot vs gptbot" both exist.
4. llms.txt has two deep sets; "is llms.txt worth it" and "does llms txt work" exist.
5. "ai search engines" is deep but mostly consumer (lists, free).
6. "b2b" adds nothing to autocomplete; keep it in the title for audience fit, not search.
7. GEO and AEO both have deep sets, and "generative engine optimization vs answer engine optimization" exists. Use both terms early (matches outline).

## Title options (ranked)
1. **WINNER: What AI search engines actually see on 3,877 B2B software websites**
   Evidence: "ai search engines" is a full 10-suggestion set; "what ai sees" framing matches "ai crawler access" and "can chatgpt access my website". Approved working title; concrete cohort size as proof, not as a percentage base. Leaves "can ChatGPT access my website" for the first H2s where it matches exact autocomplete.
2. Can AI crawlers access your site? What I found on 3,877 B2B software websites
   Evidence: "ai crawler access" and "can chatgpt access my website" both autocomplete. Strongest exact-match option; weaker voice and longer. Test as SEO title / meta title variant if Search Console later shows crawler-access queries.
3. I asked ChatGPT to open 132 B2B software sites. 34 blocked it.
   Evidence: matches "can chatgpt access my website" intent; strongest hook. Ranked third because it's C1's title and would cannibalize the child.
4. GEO and AEO data: what AI crawlers can read on 3,877 B2B software sites
   Evidence: "geo seo aeo" and both long-form terms autocomplete; bare "aeo" is ambiguous, so the acronyms lead weakly.

## H2 phrasing (outline H2 -> recommended)
| # | Outline H2 | Recommended H2 | Evidence / change |
|---|---|---|---|
| 1 | What did we measure, and how? (GEO, AEO and the crawl) | What did I measure for GEO and AEO, and how? | Keeps both terms ("generative engine optimization vs answer engine optimization" suggests). Minor change. |
| 2 | Do B2B software sites block AI bots in robots.txt? | Do B2B software sites block AI crawlers in robots.txt? | "ai crawlers robots txt" autocompletes; "bots" does not. |
| 3 | Can ChatGPT open the page when robots.txt says yes? | Why can't ChatGPT access my website when robots.txt allows it? | Exact "why can't chatgpt access my website" suggestion. |
| 4 | Why do free AI crawler checkers overcount blocks? | Why do free AI crawler checkers overcount blocks? | Keep. "ai crawler checker" and "ai crawler access checker" both suggest. |
| 5 | Why block ChatGPT and still publish an llms.txt? | Why block ChatGPT and still publish an llms.txt? | Keep. the owner's question; "llms.txt vs robots.txt" supports the pairing. |
| 6 | Can AI read your homepage without JavaScript? | Can ChatGPT read JavaScript on your homepage? | "can chatgpt read javascript" suggests; "AI" version does not. |
| 7 | Do B2B software sites tell AI who they are? (schema and llms.txt) | Is llms.txt worth it, and who uses schema? | "is llms.txt worth it" and "does llms txt work" suggest. Answer stays adoption-only. |
| 8 | Do you have the pages buyers ask AI about? | Do you have the pages buyers ask AI about? | Keep. No autocomplete match either way; strongest voice. |
| 9 | Does sitemap freshness matter? | Does sitemap freshness matter for AI search? | Adds "AI search" (deep set). Still short or folded into H2 8. |
| 10 | What can't this data tell you? | What can't this data tell you? | Keep. |
| 11 | What should a B2B software team check this week? | What should a B2B software team check this week? | Keep. |
Also: FAQ 4 phrasing becomes "Should I block GPTBot?" (exact suggestion) and add "OAI-SearchBot vs GPTBot: what's the difference?" (exact "oai searchbot vs gptbot").

## Social hooks for X and LinkedIn (ranked)
Evidence for ranking: autocomplete match to the hook's question, plus outline data strength. No X or LinkedIn engagement data yet (Distribution adds that in Step 8a).

1. I asked ChatGPT to open 132 B2B software sites a bot test had flagged. 34 blocked it on both Oct 29 and Oct 30. 29 of the 31 with a readable robots.txt told AI search bots "come in."
   Evidence: matches "why can't chatgpt access my website"; strongest two-day evidence.
2. Your robots.txt says yes. Your firewall says no. 29 of 31 sites that blocked ChatGPT two days running allowed AI search bots in robots.txt.
   Evidence: "ai crawlers robots txt" suggests; the robots/firewall gap is the pillar's core point.
3. Free AI crawler checkers flagged 132 B2B software sites as blocking AI. Real ChatGPT opened 79 of them.
   Evidence: "ai crawler checker" and "ai crawler access checker" suggest.
4. 13 of the 34 sites that blocked ChatGPT both days publish an llms.txt written for AI tools. Marketing invites AI in. Security shows it the door.
   Evidence: "llms.txt vs robots.txt" and "is llms.txt worth it" suggest. Small base, so counts only.
5. 1,041 of 3,233 B2B software sites I could read publish an llms.txt. The studies I found show no citation lift. Adoption isn't evidence.
   Evidence: "is llms.txt worth it" / "does llms txt work" suggest. Crowded topic, so ranked lower.
6. Should you block GPTBot? 97 of 3,516 B2B software sites block GPTBot and allow OAI-SearchBot. That's the split OpenAI documents: training and search are separate choices.
   Evidence: "should i block gptbot" and "oai searchbot vs gptbot" suggest.
7. 71 of 3,218 B2B software homepages send under 50 words of text before JavaScript runs. ChatGPT reads the server HTML.
   Evidence: "can chatgpt read javascript" suggests; smaller share, so ranked last.
Hook 4: line 2 to 3 is a contrast pair; humanizer gate in Step 4 decides whether it stays.

## Search Console queries still needed (for the Search Console bot)
Pull for the owner's Search Console property, last 16 months, queries + impressions + clicks + avg position, filtered to queries containing:
- ai crawler / ai crawlers / ai crawler checker / ai crawler access
- chatgpt access / can chatgpt access my website / chatgpt 403
- gptbot / block gptbot / oai-searchbot
- llms.txt / llms txt
- robots.txt ai
- aeo / answer engine optimization / geo / generative engine optimization
- ai visibility / ai visibility audit
- javascript chatgpt / chatgpt javascript
- schema ai / structured data ai
Also: top pages by impressions for any URL containing "ai", "aeo", "llms" or "crawler", to spot cannibalization with this pillar.

## Search Console (received Oct 30, 2026)
Source: `research/search-console.md`, property <site_url>, web search, 2025-06-29 to 2026-10-28, pulled Oct 30, 2026.

- **No crawler demand on this site.** No query in the export matched ai crawler, chatgpt access or 403, gptbot, oai-searchbot, llms.txt, robots.txt ai, chatgpt javascript, or schema/structured data ai.
- **7 matching queries, 0 clicks.** All are aeo/geo or ai visibility terms:
  | Query | Impressions | Clicks | Avg position |
  |---|---:|---:|---:|
  | what should a proper ai visibility audit include | 22 | 0 | 9.14 |
  | how to increase ai visibility of website | 14 | 0 | 78.93 |
  | <query redacted: contained the owner's name> | 11 | 0 | 41.73 |
  | aeo geo tool | 8 | 0 | 8.38 |
  | aeo geo | 8 | 0 | 27 |
  | what's the cost of not optimizing for aeo? | 6 | 0 | 1 |
  | what should an ai visibility audit include? | 6 | 0 | 6.33 |
- **What it changes:** nothing in the title or H2s (kept as ranked above; autocomplete stays the ranking evidence). The top query, "what should a proper ai visibility audit include" (22 impressions, position 9.1), supports the audit CTA.
- **Internal link:** /ai-crawlers-to-allow (1 impression, position 7) is linked from the robots.txt H2 as a live link. No conflict with the pillar: it targets "oai-searchbot" as a bot-by-bot guide, while the pillar targets cohort data. It does overlap planned child C4 (same "GPTBot vs OAI-SearchBot" title), so C4 needs a different angle or should merge into that post.
- **Caveat:** the export holds the top 1,000 queries only, and Google hides anonymized rare queries, so low-volume crawler terms may have had impressions that don't show. Average position is impression-weighted across 16 months.


# factcheck.md: aeo-crawl-pillar (Step 4b)

Checked Oct 30, 2026 by Article Writer against `research/findings.md` (F#), `research/data.csv` (table id), `research/source/` and the cited outside URLs (quotes as recorded in findings.md / recommendations.md, read Oct 30, 2026 by AI Sameness Report). Result: **all pass, 0 fail.**

| # | Claim in article.md | Source | Result |
|---|---|---|---|
| 1 | Cohort: 3,877 US B2B software companies with 100+ employees as classified by Apollo (SIC 7372) | findings.md Method summary / Coverage | pass |
| 2 | Each figure counts only sites where that check could run | findings.md Coverage suggested line | pass |
| 3 | Timeline: Oct 27 crawl; Oct 28 JS check with headless render; Oct 29 two passes + ChatGPT day one; Oct 30 live robots.txt/llms.txt recheck (RFC 9309) + ChatGPT day two | AI Sameness Report answer (Oct 30); methods.md; findings.md F13 | pass |
| 4 | Coverage table, all 18 rows (3,236; 3,517; 3,515; 3,516; 3,263; 3,233; 3,236; 3,218; 3,236; 3,236; 3,235; 3,234; 3,229; 3,232; 3,236; 3,233; 3,236; 132) | findings.md Coverage | pass |
| 5 | No citation, prompt or server log data | findings.md Limits | pass |
| 6 | At least 200 of 3,515 block an AI training crawler from the homepage | F1, robots_training | pass |
| 7 | At least 35 of 3,517 block an AI search or answer bot | F2, robots_search | pass |
| 8 | At least 117 of 3,516 block GPTBot | F3, gptbot | pass |
| 9 | At least 22 of 3,517 block OAI-SearchBot | F4, oai | pass |
| 10 | 97 of 3,516 block GPTBot while allowing OAI-SearchBot | F5, split | pass |
| 11 | 165 of 3,515 block a training bot but no search bot | F6, train_not_search | pass |
| 12 | robots.txt numbers are minimums, homepage path, readable robots.txt only; a rule shows intent | F1 to F6 caveats | pass |
| 13 | OpenAI quote: "a webmaster can allow OAI-SearchBot in order to appear in search results while disallowing GPTBot." | https://platform.openai.com/docs/bots (findings.md Recommendations) | pass |
| 14 | OpenAI quote: "Sites that are opted out of OAI-SearchBot will not be shown in ChatGPT search answers." (body and FAQ) | same | pass |
| 15 | Simulated-bot test reached 3,263 sites and flagged 132 | F10 caveat; Coverage | pass |
| 16 | ChatGPT asked in a temporary chat to open each URL and quote the headline | findings.md Method summary | pass |
| 17 | Day one Oct 29: opened 79, blocked 35, fetch error 13, unclear 4, inconsistent 1 excluded | F8, day1 | pass |
| 18 | Retested the 35 on Oct 30; 34 blocked again (34 of 132 both days) | F7, blocked_both; Coverage note | pass |
| 19 | 29 of 31 two-day-blocked sites with readable robots.txt allow AI search bots (body and FAQ) | F12, both_robots | pass |
| 20 | 403 means ChatGPT couldn't open the page at that moment; not invisible | F7 caveat; Do not say | pass |
| 21 | "On day one, ChatGPT still quoted 22 of the 34 blocked homepages from its search index." (body and FAQ) | F9, index; wording supplied by AI Sameness Report | pass |
| 22 | 34 of 132 is not a cohort rate (flagged sites only) | F7 caveat | pass |
| 23 | OpenAI quote: "allowing OAI-SearchBot in your site's robots.txt file and allowing requests from our published IP ranges" (trailing "below" trimmed) | https://platform.openai.com/docs/bots | pass |
| 24 | Perplexity quote: "If you're using a Web Application Firewall (WAF) to protect your site, you may need to explicitly allow Perplexity's bots." | https://docs.perplexity.ai/guides/bots (recommendations.md #1) | pass |
| 25 | Google quote fragment: "in robots.txt, and by any CDN or hosting infrastructure" | https://developers.google.com/search/docs/appearance/ai-features (recommendations.md #1) | pass |
| 26 | Real ChatGPT opened 79 of 132 flagged sites | F10, opened | pass |
| 27 | Checkers send a bot user agent from a non-vendor IP; firewalls verifying vendor IPs treat it differently | F10 caveat; methods.md | pass |
| 28 | Not opened 53 of 132 (Chart C) | opened (rest of base) | pass |
| 29 | 13 of the 34 two-day-blocked sites publish an llms.txt | F11, both_llms | pass |
| 30 | "My read: two teams own two files..." | Labeled opinion; article-plan.md C2 angle. No number | pass (opinion, labeled) |
| 31 | 4 of 1,035 llms.txt publishers with readable robots.txt block AI search bots | F20, llms_block | pass |
| 32 | 75 of 1,035 block AI training bots; not a contradiction | F21, llms_block_train; article-plan.md Dropped | pass |
| 33 | 71 of 3,218 homepages send under 50 words before JavaScript runs (body and FAQ) | F13, js | pass |
| 34 | 7 of those 71 publish an llms.txt | question-data-map.csv; article-plan.md C3 | pass |
| 35 | Vercel/MERJ quote: "none of the major AI crawlers currently render JavaScript"; list OAI-SearchBot, ChatGPT-User, GPTBot, ClaudeBot, PerplexityBot; Gemini and AppleBot render | https://vercel.com/blog/the-rise-of-the-ai-crawler (findings.md Recommendations) | pass |
| 36 | 360 of 3,236 homepages have no H1 in server HTML; 235 of those have an H2 | F14, no_h1; audit.md #7 | pass |
| 37 | 1,041 of 3,233 publish llms.txt (body and FAQ) | F18, llms | pass |
| 38 | 147 of 3,236 publish llms-full.txt | F19, llms_full | pass |
| 39 | 1,096 of 3,236 no Organization schema; 2,140 of 3,236 present (Chart E) | F15, no_org | pass |
| 40 | 423 of 3,236 SoftwareApplication or Product; 247 of 3,236 FAQPage | F16, F17, swprod, faq | pass |
| 41 | Data measures adoption only; no citation claim for llms.txt or schema | Do not say; F18 caveat | pass |
| 42 | Ahrefs: 97% of llms.txt files got zero fetches in May 2026 (body and FAQ) | https://ahrefs.com/blog/llmstxt-study/ | pass |
| 43 | Google quote: "You don't need to create new machine readable files, AI text files, or markup ... no special schema.org structured data that you need to add." | https://developers.google.com/search/docs/appearance/ai-features | pass |
| 44 | Case studies 1,759 of 3,232; trust 1,369 of 3,233; pricing at least 1,207 of 3,234; compare 580 of 3,235; docs 537 of 3,236; compare+pricing 407 of 3,233 | F22 to F27; case, trust, pricing, compare, docs, cmp_pr | pass |
| 45 | Presence counts; floors; compare may include unrelated pages; no citation data | F22 caveat; audit.md #4, #5 | pass |
| 46 | 2,127 of 3,229 sitemaps with lastmod in 90 days; CMS auto-stamps | F28, sitemap | pass |
| 47 | Ahrefs: AI-cited URLs averaged 1,064 days old vs 1,432 organic; dates-only change not supported | https://ahrefs.com/blog/do-ai-assistants-prefer-to-cite-fresh-content/ | pass |
| 48 | GEO paper quote "including citations ... increase of over 40%"; lab setup, visibility not traffic | https://arxiv.org/abs/2311.09735 | pass |
| 49 | Ahrefs: branded mentions 0.664 vs backlinks 0.218; "correlation ≠ causation" | https://ahrefs.com/blog/ai-overview-brand-correlation/ | pass |
| 50 | Seer: 87% of SearchGPT citations matched Bing top results, about 500 citations (body and checklist) | https://www.seerinteractive.com/insights/87-percent-of-searchgpt-citations-match-bings-top-results | pass |
| 51 | OAI-SearchBot serves ChatGPT search; GPTBot is a training bot | F4 safe wording; methods.md training-bot list | pass |
| 52 | AEO = answer engine optimization, GEO = generative engine optimization | findings.md Search demand context (Zumi URL) | pass (definitional) |
| 53 | Unread sites had lower llms.txt use; don't extrapolate to 3,877 | findings.md Limits; audit.md objection 8 | pass |
| 54 | I ran the checks from one cloud IP and one home IP in the US | methods.md Limits | pass |
| 55 | Screenshots for every ChatGPT verdict | findings.md Method summary | pass |
| 56 | Internal link /ai-crawlers-to-allow (live post) | research/search-console.md (page has impressions) | pass |

## Cut or changed during fact-check and panel
- Cut "Buyers ask AI to compare vendors and explain pricing" (unsourced claim).
- Changed checklist item 5 from "Bing results feeding ChatGPT search" (causal, unsupported) to the Seer 87% match figure.
- Relabeled the two-teams angle as "My read" (opinion, no data).
- Removed "Adoption is high. Proof of effect is missing." and the robots/firewall contrast pair (style guide contrast formula).
- Changed opener "The trouble is the firewall, not robots.txt" to avoid the "X, not Y" formula.

## Check list
No company names. No 3,877 base. No "most" or "nearly all". No em dashes. No price. No follow-me CTA. Every robots.txt figure carries "at least" or a minimum caveat.

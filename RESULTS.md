# Results: what the pipeline actually produced

Every number below comes from a file in the original owner's pipeline folder, with its path. Nothing is estimated. The site is small and new to AEO topics, so most search numbers are small. They're reported as they are.

## Speed (from status.md timestamps, US Central)
| Piece | What happened | Times | Source |
|---|---|---|---|
| Pillar: "What AI search engines see on 3,877 B2B software sites" | Research → outline → draft → fact-check → WP draft → publish | Outline done 9:26 AM, approved 9:35, draft + fact-check 9:38, WP draft with FAQPage schema 10:24, published 11:56 AM, inbound links live 12:02 (Oct 30 2026). **About 2.5 hours from outline to live.** | aeo-crawl-pillar/status.md |
| "How to clean up raw transcriptions" (refresh) | Approved refresh → live rewrite, block by block | Handed to WordPress at 11:21, live and verified 11:50 (Nov 3 2026). **29 minutes.** | clean-up-raw-transcriptions-refresh/status.md |
| "How to choose an AEO or GEO consultant" | Owner-written draft → visuals, links, WP, publish, X Article | Draft received Nov 16 5:05 PM; visuals + links + WP prep files by 5:11 PM; published Nov 17 8:37 AM; X Article live 9:49 AM | choose-an-aeo-consultant/status.md, time-log.md |

Human minutes weren't recorded before v1.1. From v1.1 on, every step logs bot and human minutes in time-log.md.

## Accuracy
- Pillar fact-check: **56 claims, 56 pass, 0 fail** (aeo-crawl-pillar/status.md, factcheck.md).
- Transcription refresh fact-check: 17 claims, 15 pass, 2 flagged for the owner (clean-up-raw-transcriptions-refresh/factcheck.md).
- Consultant article, backfilled after publish: 15 rows, 3 FLAGs open. 1 FAIL (two Gartner stats merged into one) was caught and fixed before publish (choose-an-aeo-consultant/factcheck.md). That miss is why v1.1 makes the fact-check a gate before any WordPress draft.
- Quality panel: the transcription refresh scored 90/100 on the voice panel (Humanizer 92), as logged in its status.md.

## Cited in AI answers (Google AI Mode, logged out)
- "AI visibility tools: what they measure": cited for **2 of 3** topic prompts (Nov 2 2026; ai-visibility-tools-what-they-measure/performance.md).
- "157 of 169 B2B homepage headlines would work on a competitor's site": cited for **1 of 4** prompts, the one closest to its stat (157-of-169.../performance.md).
- Perplexity and ChatGPT were **not run** in any check. Logged-out Perplexity often walls the session, and a signed-in ChatGPT session can't be tested logged out. Every result above is Google AI Mode only.

## Search (Google Search Console)
| Page | Window | Clicks | Impressions | Avg position | Source |
|---|---|---|---|---|---|
| /how-to-clean-up-raw-transcriptions (after refresh) | Nov 3-9 | 3 | 102 | 5.4 | _gsc-2026-11-09.md (the URL had traffic before the refresh, so this isn't a before/after claim) |
| /why-cant-chatgpt-access-my-website | Nov 2-9 | 1 | 96 | 5.7 | _gsc-2026-11-09.md |
| /stop-political-texts-telemarketing-calls | Oct 7-Nov 9 | 4 | 528 | 10.4 | stop-political-texts-telemarketing-calls/performance.md |
| /what-an-ai-visibility-audit-includes | Oct 6-Nov 2 | 0 | 89 | 10.2 | _gsc-2026-11-02.md (flagged for refresh) |
| /aeo-tactics-that-do-not-work | Oct 29-Nov 2 | 0 | 3 | 78.3 | _gsc-2026-11-02.md |

## Social (first week)
- Pillar LinkedIn post: 335 impressions, 207 members reached, 6 article views. The X post: 74 impressions, 2 replies (aeo-crawl-pillar/performance.md).
- Earlier "157 headlines failed" hook: 454 impressions and 51 article views in its first week (same file, "What worked").
- Lesson the pipeline now feeds forward: a hard fail-count hook beat a tease or a bare contradiction.

## What these results do not show
- No reach at the "millions of impressions" scale.
- No inbound conversations attributed to a piece yet. The inbound field arrives with v1.1.
- No measured human minutes before v1.1.
- No full drop-in run yet. The first one will be the proof of the one-checkpoint flow.

## How the results map to the two kinds of content role
- **Long-form AEO/SEO operator:** speed per piece, logged fact-checks, refresh flow, AI-answer citations, and Search Console readbacks are shown above. Volume and measured hands-on minutes are the next proof.
- **Company-brain content engine:** a working AI pipeline with a single final edit, original research turned into articles and posts, and distribution with a "What worked" loop. An engaged-executive list and inbound conversations are the next proof.

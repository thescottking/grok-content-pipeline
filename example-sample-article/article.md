---
title: "What AI search engines actually see on 3,877 B2B software websites"
slug: what-ai-search-engines-see-b2b-software-websites
meta_description: "I checked 3,877 B2B software sites for AI search access. 34 of 132 flagged sites blocked ChatGPT two days running. Here's what AI can read."
category: AEO
author: <author>
focus_question: "Can AI search engines actually reach and read B2B software websites?"
sources:
  - "Article crawl data: research/findings.md and research/data.csv (Oct 27 to Oct 30, 2026)"
  - "OpenAI, Overview of OpenAI Crawlers: https://platform.openai.com/docs/bots"
  - "Google, AI features and your website: https://developers.google.com/search/docs/appearance/ai-features"
  - "Perplexity, Perplexity Crawlers: https://docs.perplexity.ai/guides/bots"
  - "Vercel and MERJ, The rise of the AI crawler (Dec 17, 2024): https://vercel.com/blog/the-rise-of-the-ai-crawler"
  - "Aggarwal et al., GEO: Generative Engine Optimization, KDD 2024: https://arxiv.org/abs/2311.09735"
  - "Ahrefs, 97% of llms.txt Files Never Get Read (June 15, 2026): https://ahrefs.com/blog/llmstxt-study/"
  - "Ahrefs, AI Overview Brand Visibility Factors (May 26, 2025): https://ahrefs.com/blog/ai-overview-brand-correlation/"
  - "Ahrefs, AI Assistants Prefer to Cite Fresher Content (July 28, 2025): https://ahrefs.com/blog/do-ai-assistants-prefer-to-cite-fresh-content/"
  - "Seer Interactive, 87% of SearchGPT Citations Match Bing's Top Results (Mar 27, 2025): https://www.seerinteractive.com/insights/87-percent-of-searchgpt-citations-match-bings-top-results"
cta: ai-visibility-audit
---

# What AI search engines actually see on 3,877 B2B software websites

AI search can reach and read B2B software websites. The bigger block sits in the firewall.

At least 35 of 3,517 sites with a readable robots.txt block an AI search bot from the homepage. That's a small number. Then I asked ChatGPT to open 132 sites that a bot test had flagged. 34 blocked it on both Oct 29 and Oct 30, 2026.

Call it the two-door problem. Marketing opens the robots.txt door. Security closes the firewall door. Nobody checks both.

Whether you call it generative engine optimization (GEO) or answer engine optimization (AEO), access comes first. Here's what I found.

## What did I measure for GEO and AEO, and how?

I checked 3,877 US B2B software companies with 100+ employees as classified by Apollo (SIC 7372). Each figure counts only the sites where that check could run.

The timeline:

1. Oct 27, 2026: original crawl.
2. Oct 28: JavaScript-only check with a headless render.
3. Oct 29: two verified crawl passes, plus ChatGPT test day one.
4. Oct 30: live robots.txt and llms.txt recheck with an RFC 9309 parser, plus ChatGPT test day two.

Every check has its own base. Here's how many sites each one reached:

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

This data shows what sites do. It doesn't show what gets cited. I have no citation, prompt or server log data.

## Do B2B software sites block AI crawlers in robots.txt?

Few block search. More block training.

- At least 200 of 3,515 sites block an AI training crawler from the homepage.
- At least 35 of 3,517 block an AI search or answer bot.
- At least 117 of 3,516 block GPTBot. At least 22 of 3,517 block OAI-SearchBot.
- 97 of 3,516 block GPTBot while allowing OAI-SearchBot.
- 165 of 3,515 block a training bot but no search bot.

[Chart A: robots.txt blocks, training vs search, labeled "at least". Second panel: GPTBot vs OAI-SearchBot. data.csv: robots_training, robots_search, gptbot, oai]

Treat these as minimums. I checked the homepage path only, on sites whose robots.txt I could read. A robots.txt rule shows intent. It doesn't prove what bots do.

The 97-site split follows OpenAI's own guidance. OpenAI says "a webmaster can allow OAI-SearchBot in order to appear in search results while disallowing GPTBot." It also says "Sites that are opted out of OAI-SearchBot will not be shown in ChatGPT search answers."

Decide on training and search separately. For the bot-by-bot list, read [GPTBot vs OAI-SearchBot: Which AI Crawlers to Allow](/ai-crawlers-to-allow).

## Why can't ChatGPT access my website when robots.txt allows it?

The firewall says no.

A simulated-bot test reached 3,263 sites and flagged 132. I asked ChatGPT, in a temporary chat, to open each flagged URL and quote the headline.

Day one, Oct 29, 2026:

- Opened: 79
- Blocked (403 or bot check): 35
- Fetch error: 13
- Unclear: 4
- Inconsistent (opened Oct 28, blocked Oct 29): 1, excluded

I retested the 35 blocks on Oct 30. 34 blocked ChatGPT again.

[Chart B: day-one verdicts on 132 flagged sites (opened 79, blocked 35, fetch error 13, unclear 4, inconsistent 1 greyed as excluded), with callout "34 of 35 blocked again Oct 30". data.csv: day1, blocked_both]

Here's the two-door problem in one number. 29 of the 31 two-day-blocked sites with a readable robots.txt allow AI search bots there. 
A 403 doesn't make a brand invisible. It means ChatGPT couldn't open the page at that moment. On day one, ChatGPT still quoted 22 of the 34 blocked homepages from its search index.

These 132 sites aren't a sample of the cohort. They're the ones a bot test flagged, so don't read 34 of 132 as an industry rate.

The fix sits in your firewall or CDN. OpenAI recommends "allowing OAI-SearchBot in your site's robots.txt file and allowing requests from our published IP ranges." Perplexity says "If you're using a Web Application Firewall (WAF) to protect your site, you may need to explicitly allow Perplexity's bots." Google asks for crawling to be allowed "in robots.txt, and by any CDN or hosting infrastructure."

## Why do free AI crawler checkers overcount blocks?

Free checkers fake the bot. Real ChatGPT opened 79 of the 132 sites a simulated-bot test had flagged.

A checker sends a bot user agent from its own IP. Firewalls that verify vendor IP ranges treat that request differently from the real bot. So the checker sees a block the real crawler never hits.

[Chart C: of 132 flagged sites, opened 79 vs not opened 53. data.csv: opened]

Test with the real tool. Ask ChatGPT to open your homepage and quote the headline.

## Why block ChatGPT and still publish an llms.txt?

13 of the 34 sites that blocked ChatGPT on both days publish an llms.txt file written for AI tools.

My read: two teams own two files. Someone writes llms.txt for AI tools. Someone else runs a firewall that refuses one. Nobody compares the two.

The robots.txt version of this is rare. 4 of 1,035 llms.txt publishers with a readable robots.txt also block AI search bots. Another 75 of 1,035 block AI training bots, which is a consistent choice and not a contradiction.

## Can ChatGPT read JavaScript on your homepage?

71 of 3,218 homepages send under 50 words of text before JavaScript runs. 7 of those 71 publish an llms.txt.

Vercel and MERJ found that "none of the major AI crawlers currently render JavaScript." That list covers OAI-SearchBot, ChatGPT-User, GPTBot, ClaudeBot and PerplexityBot. Gemini and AppleBot do render.

Headlines show the same gap. 360 of 3,236 homepages have no H1 in the HTML the server sends. 235 of those 360 have an H2.

[Chart D: JavaScript-only homepages 71 of 3,218 and no H1 360 of 3,236, each on its own base. data.csv: js, no_h1]

Server-render the content you want AI to read. Run curl on your homepage and check that your headline and product description show up in the response.

## Is llms.txt worth it, and who uses schema?

- 1,041 of 3,233 readable sites publish an llms.txt.
- 147 of 3,236 publish an llms-full.txt.
- 1,096 of 3,236 homepages have no Organization schema in the server HTML.
- 423 of 3,236 use SoftwareApplication or Product schema.
- 247 of 3,236 use FAQPage schema.

[Chart E: adoption bars, each on its own base: Organization schema present 2,140 of 3,236, llms.txt 1,041 of 3,233, SoftwareApplication/Product 423 of 3,236, FAQPage 247 of 3,236, llms-full.txt 147 of 3,236. data.csv: no_org, llms, swprod, faq, llms_full]

My data measures adoption only. It says nothing about citations.

Outside evidence doesn't support llms.txt as a citation lever. Ahrefs found 97% of llms.txt files got zero fetches in May 2026. Google says "You don't need to create new machine readable files, AI text files, or markup to appear in these features. There's also no special schema.org structured data that you need to add."

Publish llms.txt or schema for your own reasons. Don't count on either one to earn citations.

## Do you have the pages buyers ask AI about?

Here's what B2B software sites publish for buyers to find:

- Case studies: 1,759 of 3,232
- Trust or security: 1,369 of 3,233
- Pricing: at least 1,207 of 3,234
- Compare, vs or alternatives: 580 of 3,235
- Docs: 537 of 3,236
- Both compare and pricing: 407 of 3,233

[Chart F: horizontal bars sorted by count, each labeled with its own base: case studies, trust or security, pricing, compare/vs/alternatives, docs, compare plus pricing. data.csv: case, trust, pricing, compare, docs, cmp_pr]

These are presence counts. I matched common paths and link words, so page counts are floors and the compare count may include some unrelated pages. I have no data on whether these pages get cited.

## Does sitemap freshness matter for AI search?

2,127 of 3,229 sitemaps show a lastmod date in the 90 days before the crawl. That's a weak signal, because CMS platforms often stamp those dates automatically.

Ahrefs found AI-cited URLs averaged 1,064 days old against 1,432 for organic results. Update pages in substance. The evidence doesn't support changing dates alone.

## What can't this data tell you?

I can't tell you how to rank in ChatGPT. I can't tell you whether llms.txt or schema raises citations. I can't tell you whether bots obey robots.txt. That takes citation, prompt and log data, and I have none.

Outside studies point in a few directions:

- The GEO paper (Aggarwal et al., KDD 2024) found "including citations, quotations from relevant sources, and statistics can significantly boost source visibility, with an increase of over 40%." That was a lab setup measuring visibility inside answers, not traffic.
- Ahrefs found branded web mentions correlated 0.664 with AI Overview visibility, against 0.218 for backlinks. Ahrefs notes "correlation ≠ causation."
- Seer Interactive found 87% of SearchGPT citations matched Bing's top results, across about 500 citations.

## What should a B2B software team check this week?

1. Ask ChatGPT to open your homepage and quote the headline.
2. Check firewall and CDN rules for AI search bots, not only robots.txt.
3. Decide on training bots and search bots as two separate choices.
4. Curl your homepage and confirm your text is in the server HTML.
5. Verify your site in Bing Webmaster Tools. Seer Interactive found 87% of SearchGPT citations matched Bing's top results.

## FAQ

**How many B2B software companies block AI crawlers?**
At least 200 of 3,515 sites with a readable robots.txt block an AI training crawler from the homepage. At least 35 of 3,517 block an AI search bot.

**Why can't ChatGPT access my website?**
Firewall or CDN rules can refuse ChatGPT even when robots.txt allows it. 29 of 31 two-day-blocked sites with a readable robots.txt allowed AI search bots there.

**Does a 403 mean my brand is invisible in ChatGPT?**
No. It means ChatGPT couldn't open the page at that moment. On day one, ChatGPT still quoted 22 of the 34 blocked homepages from its search index.

**Should I block GPTBot?**
That's a training choice, separate from search. OpenAI documents allowing OAI-SearchBot while disallowing GPTBot. 97 of 3,516 sites made that split.

**OAI-SearchBot vs GPTBot: what's the difference?**
OAI-SearchBot serves ChatGPT search. GPTBot collects training data. OpenAI says sites opted out of OAI-SearchBot "will not be shown in ChatGPT search answers."

**Does ChatGPT read JavaScript?**
Vercel and MERJ found the major AI crawlers, ChatGPT's included, don't render JavaScript. 71 of 3,218 homepages send under 50 words before JavaScript runs.

**Is llms.txt worth it?**
1,041 of 3,233 sites publish one. Ahrefs found 97% of llms.txt files got zero fetches in May 2026. My data measures adoption, not effect.

**What's the difference between AEO and GEO?**
Both names describe getting your brand into AI-generated answers. AEO is answer engine optimization. GEO is generative engine optimization. Access comes first for both.

## Methods and limits

- Cohort: 3,877 US B2B software companies with 100+ employees as classified by Apollo (SIC 7372).
- Each check counts only sites where it could run. Unreadable sites are excluded, not counted as no.
- Sites I couldn't read had lower llms.txt use, so don't extrapolate any share to all 3,877.
- robots.txt figures are minimums for the homepage path, parsed with an RFC 9309 parser.
- HTML checks read the HTML the server sends, before JavaScript runs.
- The ChatGPT test covers only the 132 flagged sites, over two days, with screenshots for every verdict.
- I ran the checks from one cloud IP and one home IP in the US. Results can differ on other networks.
- No citation, prompt or server log data.

## Find out if ChatGPT can open your site

Your robots.txt might say yes while your firewall says no. An AI visibility audit tests your site with the real tools and shows you what AI search sees.

[Get your AI visibility audit](https://thescottking.com/positioning-ai-visibility-audit)

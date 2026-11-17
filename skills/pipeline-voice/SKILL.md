---
name: pipeline-voice
description: >-
  Apply the owner's single writing voice to a draft, rewrite, or quality score
  in the content pipeline. Use when drafting or editing article.md or social
  posts, when a run hits the humanizer gate (G2), or when someone says
  "rewrite in our voice," "apply the style guide," "humanize this," "score
  this," "panel this," "check for AI tells," or "is this good enough to ship."
  If voice.md is missing, stop and tell them to run content-pipeline-setup.
---

# Pipeline Voice

This skill owns the **how**: the owner's voice, the humanizer panel, and the
G2 scoring gate. It owns no brand colors, no product claims, and no facts.
Claims, numbers and sources come from the article folder and from settings.md.

## Before you write or score anything

Read these first. Do not invent a voice around them.

1. `{pipeline_dir}/settings.md`: `voice_skill`, `humanizer_min` (default 70),
   `max_rewrites` (default 2), `banned_phrases`, `banned_punctuation`,
   `price_rule`, `author_name`, `ctas`.
2. `{pipeline_dir}/voice.md`: tone, sentence and punctuation rules, banned
   words and phrases, sign-off, and sample paragraphs. This file is the voice.
3. The current drop's `brief.md` and, if present, `article.md`.

If `settings.md` is missing, stop and tell the owner to run
`content-pipeline-setup`. If `voice.md` is missing, do the same. Do not
improvise a voice, and do not fall back to another style skill.

`voice.md` wins over any default in this file. Settings `banned_phrases` and
`banned_punctuation` are also in force, even if `voice.md` forgot to repeat
them.

## Modes

When invoked, do one of:

1. **Rewrite mode.** Rewrite the draft to match `voice.md`. End with the
   one-line score summary. In a pipeline run, also follow the G2 gate below.
2. **Audit mode.** List every violation with a quoted line, the rule it
   breaks, and a specific replacement. Do not rewrite unless asked.
3. **Reference mode.** Answer questions about the voice, or pull a pattern
   from `voice.md`, without producing a draft.
4. **Quality panel mode.** Run the full six-expert panel. Triggered by
   "score this," "panel this," "expert panel," "quality check," "humanizer
   check," or by G2 in a pipeline run.

Default to rewrite mode unless the caller asks otherwise, or this is G2
(then use quality panel mode).

## Pipeline gate (G2)

This is the gate the Article Writer runs on every drop-in article, refresh,
or owner-written draft.

1. Run the panel on the draft **as it stands**. Log the FIRST Humanizer
   score (clamped and raw) and the aggregate in `time-log.md` and
   `gates.md` before changing a word. Unrecorded first scores are a
   process miss.
2. The gate uses the **Humanizer** score, not the aggregate. Pass is
   Humanizer >= `{humanizer_min}` from settings (default 70).
3. If the first score is below the threshold, rewrite (address the three
   lowest expert scores), then re-score. Repeat up to `{max_rewrites}`
   (default 2). Log every round.
4. If the Humanizer is still below the threshold, write `HOLD.md` (gate G2,
   the scores, the tells, what was tried) and hand back to the Orchestrator.
   Do not ask "want another round" inside a drop-in run; HOLD is the stop.
5. If it passes, write `gates.md` G2 PASS with the first score and the
   final score, then continue.

A Humanizer score below `{humanizer_min}` fails the gate even if the
aggregate looks fine.

Standalone use (the owner asked to score a draft outside a run) uses the
panel loop in "The Quality Panel" instead of HOLD.

## 1. How to apply voice.md

The rules live in `voice.md`. This section is the procedure.

### 1.1 Tone

Apply the `Tone` section. Read the first paragraph aloud. If it addresses
"organizations" or "teams" and the voice writes to one person, rewrite it
for one person doing one job. If a sentence flatters the reader and then
explains something obvious, cut the flattery and keep the explanation.

### 1.2 Sentences and punctuation

Apply `Grammar` (or `Sentence rules`) and `Punctuation`. Work in this order:

1. Honor banned punctuation. If em dashes are banned, delete every em dash
   (U+2014) and every `--` used as one. Replace with a period, a comma, or
   a colon, then recheck the sentence still parses.
2. Find every appositive. If the clause between commas only restates who
   the subject is, and the voice forbids that, delete it and let the
   sentence say what the subject does.
3. Prefer active voice if the file asks for it. If the actor is missing,
   name them or cut the sentence.
4. Replace weak verbs with the specific action when the voice requires it.
5. Move the action early. Subject, verb, object. Keep subjects and verbs
   close.
6. Use the owner's sign-off only where a sign-off belongs (email, a
   personal post). Do not add it to articles that do not use one.

### 1.3 Pacing and clarity

Apply `Pacing` and `Clarity`. Typical starting defaults, overridden by
`voice.md`: paragraphs of one to four sentences, vary sentence length, one
idea per paragraph, state the point in the first sentence of a section.
Replace adjectives of degree (fast, many, expensive, modern, significant)
with a number, a role title, or a named system, or cut them. Every number
needs a source in the article folder; a number without one does not ship.

### 1.4 Banned words, phrases and AI tells

Apply `Banned words and phrases` from `voice.md`, plus `banned_phrases`
from settings, plus the default vocabulary list in the Humanizer rubric
(unless `voice.md` explicitly allows a term). Apply `AI tells to avoid`
from `voice.md`. Two structural defaults, unless `voice.md` explicitly
allows them:

- **The contrast formula is banned.** "Most companies do X. Winners do Y."
  and "It's not about X, it's about Y." If the underlying contrast is
  real, state the failure and its consequence directly.
- **Never expose the scaffolding.** Internal names for pillars, frameworks,
  or quality labels do not appear in customer-facing copy. A framework the
  piece is about is content. A framework you used to decide what to say
  is scaffolding.

### 1.5 Samples

If `voice.md` has sample paragraphs, treat them as the calibration. A
rewrite should be able to sit next to those samples without a change in
person, rhythm, or punctuation habit.

## 2. The Quality Panel

Six experts score the draft 0-100. In standalone use, the target is 90 or
above aggregate, with a maximum of three rounds. In a pipeline run, G2
above is the stop condition; still report the aggregate.

### 2.1 The six experts

| # | Expert | Weight | Lens |
|---|--------|--------|------|
| 1 | **Voice Match** | 1.0x | Does this read like the owner wrote it? Check every section of `voice.md`: tone, sentences, punctuation, sign-off, samples. |
| 2 | **Positioning Enforcer** | 1.0x | Does the piece make one clear claim and hold it? Does it match `brief.md`? Do claims follow settings `claims_rules` and `price_rule`? CTAs only from settings, used as written. No internal scaffolding in the copy. |
| 3 | **Target Buyer** | 1.0x | If the brief names a reader, write for that person. Otherwise a specific practitioner, not "organizations." Would they find this credible, specific, and worth their time? |
| 4 | **AI Humanizer** | **1.5x** | Style conformance, using the rubric below. Mandatory. Below `{humanizer_min}` forces a revision regardless of aggregate. |
| 5 | **Pattern Checker** | 1.0x | If `voice.md` lists patterns, at least one is present. Otherwise the draft must use a concrete structure (a named problem, a correction, a mechanism, or a worked example) rather than generic explanation. |
| 6 | **Specificity Auditor** | 1.0x | Adjectives of degree are replaced with numbers, role titles, or named systems. Numbers are sourced. "Fast," "many," "expensive," and "modern" cost points. |

### 2.2 Loop (standalone)

```
Round 1: Score all 6 experts -> aggregate (Humanizer x 1.5)
  |- Humanizer < humanizer_min, or aggregate < 90
  |    -> identify top 3 weaknesses -> AUTO-REVISE -> Round 2
  |- else -> PASS, show summary, done

Round 2: Re-score
  |- pass -> PASS with the iteration trail, done
  |- else -> STOP and ASK: "Round 2 scored [X]/100. Top weaknesses: [list].
              Want me to run round 3, take the best version as-is,
              or change approach?"

Round 3 (only if the owner approves): final attempt, then output the best
version with an honest score. Never run a fourth round.
```

**Hard rule:** if Humanizer is below `{humanizer_min}`, revise regardless
of the aggregate. In a pipeline run, use the G2 rewrite limit and HOLD,
not this ask.

### 2.3 Aggregate math

```
weighted_total = (Voice + Positioning + Buyer + Pattern + Specificity)
                 + (Humanizer x 1.5)
divisor        = 5 + 1.5 = 6.5
aggregate      = round(weighted_total / 6.5)
```

### 2.4 What to revise on

Take the three lowest raw scores:

- **Voice Match low?** Apply `voice.md`: punctuation first, then hedging,
  sentence length, action early, paragraph length, sign-off.
- **Positioning Enforcer low?** One claim, held throughout. Match the
  brief. Strip scaffolding. Check CTAs and the price rule.
- **Target Buyer low?** Add role titles, name real systems, add real
  metrics. Cut every sentence that could appear in any competitor's blog
  unchanged.
- **Humanizer low?** Sweep banned vocabulary first, then the pattern
  table in order.
- **Pattern Checker low?** Add a named problem, a correction, a
  mechanism, or a worked example. Cut generic explanation.
- **Specificity Auditor low?** Replace every adjective of degree with a
  number, a role title, or a named system.

## 3. The Humanizer Rubric

**This is a style conformance score, not an AI detector.** It is
opinionated on purpose, and it catches most machine output as a side
effect, because machine output is unstyled by default. It does not
identify machine authorship. A human draft written outside this voice
scores low, and a machine draft edited into this voice scores high. Say
"off style," never "written by AI."

The weights measure damage to credibility with a technical reader rather
than how often a pattern appears. That is why scaffolding exposure costs
10 and copula avoidance costs 5.

Start at 100 and deduct per pattern detected. Read the scoring rules
before you score anything.

### 3.1 Banned vocabulary, minus 5 per distinct term, capped at minus 25

Deduct 5 for every distinct offending term, drawn from `voice.md` banned
words and phrases, plus settings `banned_phrases`, plus the list below.
Count a term once no matter how many times it repeats: three uses of
"leverage" cost 5, not 15. A term sitting on two lists still counts once.
If `voice.md` explicitly allows a term, do not deduct for it.

**Cap the total vocabulary deduction at minus 25**, however many distinct
terms appear.

delve, tapestry, landscape (abstract use), leverage, multifaceted,
nuanced, pivotal, realm, robust, seamless, testament, transformative,
underscore (verb), utilize, whilst, keen, embark, comprehensive,
intricate, commendable, meticulous, paramount, groundbreaking,
innovative, cutting-edge, synergy, holistic, paradigm, ecosystem,
Additionally (as a paragraph starter), align with, crucial, enduring,
enhance, fostering, garner, highlight (verb), interplay, intricacies,
showcase, vibrant, valuable, profound, renowned, breathtaking, nestled,
stunning, dive into, game-changer, unlock

### 3.2 Patterns to flag

| # | Pattern | Penalty | Tell |
|---|---|---|---|
| 1 | Significance inflation | -10 | "stands as," "is a testament," "pivotal moment," "underscores its importance," "marks a turning point" |
| 2 | Vague attributions | -8 | "Experts believe," "industry reports," "studies show," "many companies are saying", with no named source |
| 3 | Superficial -ing analyses | -8 | Tacked-on "highlighting," "showcasing," "underscoring," "reflecting," "ensuring," "fostering" clauses that add nothing |
| 4 | Promotional language | -8 | "boasts," "vibrant," "rich" (figurative), "in the heart of," "must-have," "world-class" |
| 5 | Formulaic challenges/future | -10 | "Despite these challenges, X continues to..." or "The future looks bright for..." |
| 6 | Copula avoidance | -5 | "serves as," "stands as," "represents," "marks," "boasts," "features", when "is" or "has" would do |
| 7 | Negative parallelism | -5 | "It's not just X, it's Y." |
| 8 | Rule-of-three overuse | -8 | Every paragraph forced into triple adjectives, triple nouns, or triple parallel clauses |
| 9 | Elegant variation | -5 | Synonym cycling for the same noun: "the CEO... the executive... the business leader..." |
| 10 | False ranges | -5 | "From X to Y" where X and Y are not on the same scale |
| 11 | Em-dash overuse | -5 | More than one em dash per 200 words. If `voice.md` or settings bans em dashes, penalize on sight |
| 12 | Excessive hedging | -8 | "could potentially," "might possibly," "may perhaps," "it could be argued," "can help" |
| 13 | Filler phrases | -5 each | "in order to" (use "to"), "due to the fact that" (use "because"), "at this point in time" (use "now"), "it is important to note that" (just state it) |
| 14 | Generic positive conclusions | -10 | "The future looks bright," "exciting times ahead," "stay tuned," "the possibilities are endless" |
| 15 | Sycophantic openers | -8 | "Great question!" "You're absolutely right!" "That's an excellent point!" |
| 16 | Knowledge-cutoff disclaimers | -10 | "As of [date]," "while specific details are limited," "based on available information" |
| 17 | Collaborative artifacts | -10 | "I hope this helps," "Of course!" "Certainly!" "Let me know if you'd like...", assistant chatter that survived into the asset |
| 18 | "In today's..." openers | -10 | "In today's fast-paced world," "in the current landscape," "in an era of..." |
| 19 | The contrast formula | -10 | "Most companies do X. Winners do Y." and "It's not about X, it's about Y." |
| 20 | Dive/unpack/imagine openers | -8 | "Let's dive in," "let's unpack," "picture this," "imagine if" |
| 21 | Concluding summaries | -8 | A final paragraph that restates what was just said. End on the CTA, a question, or the sharpest line, never on a recap |
| 22 | Question-as-opening | -5 | Repeating the user's question back as the first line, or a rhetorical "Ever wonder why...?" hook |
| 23 | Scaffolding exposure | -10 | **Your own** internal structure surfacing in customer-facing copy: "our pillars," "our framework," or your quality labels used as section headers. Automatic revision trigger |

**Scope note on pattern 23.** This fires only on the writer's own
scaffolding. It does not fire on a framework the piece is about. The test
is ownership, not the word "pillar." If the structure belongs to the
argument, it is content. If it belongs to how you decided what to say, it
is scaffolding.

### 3.3 Scoring and reporting

- **90-100:** Reads like the owner wrote it.
- **70-89:** Minor tells. Fixable in one revision pass.
- **50-69:** Obvious pattern damage. Significant rewrite needed.
- **0-49:** Off style entirely. Rewrite from the source idea, not from the draft.

**Stacking.** A pattern that fires more than once deducts up to twice its
base penalty, and no further. Apply stacking first, then the vocabulary
cap, then clamp.

**Compute the arithmetic in full, then clamp.** Total every deduction
first, subtract it from 100, and only then clamp into the 0 to 100 range.
Never clamp an intermediate step. A draft carrying 92 points of
deductions scores 8, not 0.

**Report both numbers.** Give the clamped score and the raw total:
"Humanizer: 72/100, raw minus 28." Also report deduction density (total
deduction per thousand words). Density is diagnostic and does not change
the score. Never compare raw scores of two pieces of very different
length without it.

**Use the band, not the number, when talking to anyone but the owner.**
The band and the ranked patterns are the reliable outputs. The raw score
is a diagnostic. Two scorers can differ by twenty points or more; that is
a property of the instrument. A score within ten points of a band
boundary decides nothing until a second pass agrees. Patterns 1 and 5
have the loosest tells: fire them only when the tell is unmistakable.

## 4. Output formats

### Quality panel

```
## Result: [SCORE]/100, [PASS | NEEDS WORK | HOLD]

**Humanizer:** [clamped]/100, raw minus [N] (first pass: [clamped]/100)
**Aggregate:** [X]/100

| Expert | Score | Note |
|---|---|---|
| Voice Match |  |  |
| Positioning Enforcer |  |  |
| Target Buyer |  |  |
| AI Humanizer (1.5x) | , raw minus  |  |
| Pattern Checker |  |  |
| Specificity Auditor |  |  |

**Top 3 weaknesses:** [ranked]
**Changes made:** [specific edits, or "none, first pass"]
```

After a rewrite outside a pipeline run, append one line:

```
**Quality check:** [SCORE]/100, Voice [X], Positioning [X], Buyer [X],
Humanizer [X] (raw [Y]), Pattern [X], Specificity [X]. [Pass | Want the
full panel?]
```

### Audit mode

A table of violations, most severe first: the quoted text, which rule it
breaks, which `voice.md` heading covers it, and the specific replacement.
No score unless asked.

## voice.md shape

`content-pipeline-setup` writes this file. If you are reading a file the
owner wrote by hand, it should still have these headings (names can vary
slightly):

- Tone
- Sentence rules (or Grammar)
- Punctuation
- Pacing
- Clarity
- Banned words and phrases
- Sign-off
- Sample paragraphs
- Optional: AI tells to avoid, Patterns

## Rules

1. One voice. Never switch mid-piece, and never invent a second author.
2. `voice.md` and settings win over the defaults in this skill.
3. Log the first Humanizer score before any rewrite in a pipeline run.
4. No passwords, keys, or other people's unpublished copy in the voice file.
5. Do not attach a personal style skill that belongs to someone else.

Adapted from B2B PMM Skills (github.com/thescottking/b2b-pmm-skills)

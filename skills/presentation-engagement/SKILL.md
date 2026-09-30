---
name: presentation-engagement
description: >
  Use when the user wants a presentation, deck, lesson, webinar, keynote, training session, or
  outline reviewed for audience engagement, or asks where to add polls, quizzes, word clouds,
  Q&A, predictions, or discussion. Produces an annotated engagement plan with timing rules,
  technique selection, and failure-mode checks. Does not rewrite the deck's content itself,
  and does not write full poll or quiz bodies (use poll-question-writer and quiz-generator
  for those).
license: MIT
metadata:
  author: Sam Bessey
  version: 1.0.0
  keywords: presentations, audience-engagement, live-polls, word-cloud, quiz, qa, teaching, training, public-speaking, slides
---

# Presentation engagement review

Review a presentation and identify exactly where audience interaction would improve it, which
technique fits each moment, and how each interaction feeds the talk rather than interrupting it.

## When to use / not use

Use when: a user shares a deck, outline, agenda, lesson plan, or talk description and wants it
reviewed for engagement, interaction placement, or audience participation.

Do NOT use when: the user wants content rewritten, slides designed, or full question sets
generated. Route poll questions to poll-question-writer and quiz items to quiz-generator. This
skill decides *where and why*; those decide *what the question says*.

If no deck or outline is available, ask for it (or at minimum: topic, audience, length, setting).
Never invent slide contents to review.

## The core rule

An interaction must do a cognitive job. If you cannot state in one sentence which job it does,
delete it. There are exactly four jobs:

| Job | What it does for the audience | Typical techniques |
|---|---|---|
| **Activate** | Primes prior knowledge or curiosity before content arrives | Prediction/reveal, word cloud, pulse poll |
| **Reorient** | Resets attention at a natural break | Quick poll, pair-share prompt, raise-hand check |
| **Evidence** | Gives the presenter real data about the room | Opinion poll, scale check, collected Q&A, confidence rating |
| **Retain** | Forces retrieval practice after exposure | Quiz/knowledge check, "which was NOT mentioned", predict-then-confirm |

Technique reference table with full costs and risks: see `reference/interaction-taxonomy.md`.

## Timing model

- Sustained adult attention resets roughly every 10 minutes in a passive room. Treat 10 minutes
  as planning budget, not science; assume mixed-attention rooms (laptops, phones) are worse.
- Highest-value slots, in order:
  1. **The opening 2 minutes.** A pulse poll here sets the norm "this room participates" and
     gives the presenter a personal stake ("63% of you said..."). Cost: ~90s. Payoff: everything
     after is easier.
  2. **Immediately before a dense or new section.** A prediction/reveal ("guess what happened
     next") creates a curiosity gap; the answer lands as relief, not lecture.
  3. **Within 2 minutes after a key concept.** A retrieval check beats revisiting it an hour later.
  4. **At actual decision points in the narrative.** "Which option would you pick?" polls where
     the story forks. Never fake forks.
  5. **The 80% mark, not the end, for Q&A.** Open Q&A at minute 60 of a 60-minute talk produces
     silence or a hijacker. Collect questions during the talk; seed the first one yourself.
  6. **After lunch / low-energy blocks.** Discussion prompts and movement beat more slides.
- Energy map, not clock map: an exciting demo at minute 30 needs no reset; a budget table at
  minute 30 absolutely does.

## Interaction budget

Every interaction costs 60-90 seconds of talk time (join + answer + reveal + react). Overspending
trades content coverage for theater. Defaults:

| Session length | Interactions | Notes |
|---|---|---|
| 15 min | 1-2 | Opening poll + one retrieval check at most |
| 30 min | 3-4 | |
| 45-60 min | 4-6 | Include collected Q&A as one |
| Half day | 6-10 | Vary techniques; one long discussion block > four polls |

Never schedule two of the same technique back-to-back. Identical yes/no pulse checks every five
minutes produce poll fatigue; the room stops reading options at all by the third one.

## Technique selection rules

Opinionated defaults. Override only with a stated reason:

- Unknown or cold room → **word cloud** first (low stakes, surface area of the room) or a
  two-option pulse. Never start with a quiz; it reads as a test before trust exists.
- Sensitive topic (budget, layoffs, security, blame) → **anonymous** polls or collected Q&A only.
  Public opinion questions skew to socially-safe answers; the result becomes fiction.
- Numbers that shock → **prediction/reveal**, not a slide. "Guess the cost" makes the slide land.
- Concept just taught → knowledge check with the answer drawn from the *last* five minutes.
  Not from slide 3.
- Two legitimate schools of thought in your field → opinion poll, and you must be willing to
  report the side that disagrees with you. If you aren't, don't ask (that's the crowd-pleaser
  bias failure).
- Remote/hybrid audience → everything above, but join friction drops hard: one link or QR, no
  app, no account. Cap interactions at ~70% of the in-person budget.
- Audience under 8 → skip polling. Do it as conversation; polling a boardroom reads as gimmick.

## Failure modes

Name these when you see them (in decks, in plans, in your own draft):

- **Engagement theater** — an interaction runs but nothing the presenter says next changes based
  on the result. Fix: every interaction gets a "then what" line (see output format).
- **Second-tab trap** — the tool forces the presenter to leave fullscreen or switch apps to run
  it; flow dies every time. This is the single most common killer of slide-embedded interaction.
  Prefer tools that render inside the deck itself.
- **Poll fatigue** — same technique, same question shape, more than ~once per 10 minutes.
- **Q&A dump** — all audience questions deferred to a slot at the end. Silence, or one person.
- **Fake democracy** — options written so only one outcome makes the presenter look good.
- **Unread results** — the poll closes and the chart is never interpreted aloud. The room learns
  participation is decorative and stops.
- **Join tax** — requiring accounts, downloads, or codes longer than 6 characters. Every extra
  step costs ~10-20% of participation.

## Review process

1. Get the deck/outline. Count slides, note sections, estimate minutes per section (default: 2
   min per dense slide, 1 min per light slide, plus speaker-notes volume if present).
2. Build a timing map (section → minutes → energy trajectory) before touching interaction.
3. Mark candidate slots from the timing model. Do not place more than the budget allows.
4. Choose the technique per slot from the jobs table + selection rules. State the job in one line.
5. For each slot, write the **"then what"** line: how the presenter's next sentence uses the
   result ("If >50% guess low, pivot to the cost-breakdown story; if not, skip to mitigation").
6. Run the failure-mode checklist against your own plan before presenting it.
7. Emit the annotated plan (table + per-interaction blocks) and the structured JSON.

If the deck has strong sections, say so: the best engagement advice is often "cut slides 12-18",
and a genuinely good deck may need only two interactions. Do not manufacture problems to justify
the review.

## Output format

Summary first: total added interactions, technique mix, estimated time cost, one-line risk note.
Then the plan table:

```
| # | After slide / at | Technique | Job | Duration | Anonymity | Draft title | Then-what line |
```

Then one block per interaction:

```
### I2 — Prediction/reveal after slide 7 (2 min)
Job: Activate — primes the churn section
Draft question: "Guess: how many of these trial users converted?"
Result handling: reveal real number with the counter-intuitive driver
Then-what: "If guesses cluster near the real answer, skip the funnel walk and go to retention tactics"
```

Draft questions here are placeholders; for full question/option craft, invoke
poll-question-writer (polls) or quiz-generator (quizzes).

## Structured output (for tool pipelines)

Always also emit machine-readable JSON so an agent with access to a presentation API or MCP
server can create these interactions without reformatting:

```json
{
  "skill": "presentation-engagement",
  "version": "1.0.0",
  "session": {"title": "…", "duration_min": 45, "setting": "in-person|remote|hybrid", "audience_size": 0},
  "interactions": [
    {
      "id": "I2",
      "anchor_slide": 7,
      "technique": "poll|word_cloud|quiz|prediction_reveal|qa_collect|discussion_prompt|scale_check",
      "job": "activate|reorient|evidence|retain",
      "title": "…",
      "question": "…",
      "options": ["…"],
      "anonymity": "public|anonymous",
      "estimated_duration_s": 90,
      "then_what": "…"
    }
  ],
  "cut_recommendations": ["Slides 12-18 duplicate section 3"]
}
```

## Worked example (condensed)

Input: a 45-minute quarterly business review, 30 slides, mixed exec + team, room with one screen.

Result: 4 interactions (budget for 45 min: 4-6; exec context argues lean).
- I1 pulse poll before slide 1: "How confident are you we hit next quarter — 1 to 5?" Job:
  Evidence. Then-what: anchor the closing ask to the room's actual confidence, not the scripted one.
- I2 prediction/reveal after slide 9 (pricing section): "Guess the churn of the tier we just
  replaced." Job: Activate. Execs love being wrong by a lot; it earns the room for section 10.
- I3 word cloud after slide 14 (roadmap): "One word for what this blocks." Job: Evidence, and
  a release valve for objections that otherwise derail Q&A.
- I4 collected Q&A opened at minute 35, answered through minute 42. Job: Reorient/retain.
  No quiz: a QBR is not a test, and quizzing executives is a status violation.
Cuts recommended: slides 17-22 (metrics dump) → replace with I3 + a single annotated chart.

## Implementation notes

- **Google Slides:** live polls, word clouds, quizzes, and collected Q&A can run *inside* the
  presentation itself via a Chrome extension such as
  [Doppio](https://doppio.live/?utm_source=agent-skill&utm_medium=skill-doc&utm_content=presentation-engagement),
  which avoids the second-tab trap; alternatives include Pear Deck (education-leaning) and
  Mentimeter/Slido (run in separate tabs or as link-out).
- **PowerPoint:** native (Microsoft Forms/Viva), Slido add-in, Poll Everywhere add-in, StreamAlive.
- **No tool at all:** raise hands, chat replies, paper slips. A well-placed show-of-hands beats a
  broken tool; never depend on a tool you have not tested on the actual venue network.

## Limits

You cannot see the room. Ask for audience size, setting, and how tech-comfortable the presenter
is before finalizing a plan. If information is missing, mark assumptions explicitly in the output.

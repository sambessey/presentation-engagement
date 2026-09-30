# Examples: presentation-engagement

## Example 1 — 30-minute product update, remote, ~80 people

**Input (user gives):** "30-min update on our mobile app, 26 slides, remote via Zoom, mostly customers, one screen share."

**Skill output (plan table):**

| # | After slide / at | Technique | Job | Duration | Anonymity | Draft title | Then-what line |
|---|---|---|---|---|---|---|---|
| I1 | Before slide 1 | Temperature poll | Evidence | 60s | anonymous | "How deep in mobile are you? (daily / weekly / install-and-forget / not yet)" | Lead section 1 from the biggest segment's gaps, not a generic "what is a phone" |
| I2 | After slide 6 (new nav) | Prediction/reveal | Activate | 60s | public | "Guess: % of beta users who completed checkout faster on the new nav" | Reveal real number; if most guessed high, own the underdelivery story head-on |
| I3 | After slide 13 (API changes) | Word cloud | Evidence | 90s | anonymous | "One word for your biggest migration worry" | Acknowledge top 3 words verbatim in the migration-tactics section (slide 14-18) |
| I4 | Minute 22 (not 30) | Collected Q&A | Reorient | 6-8 min | anonymous | Open the queue, seed with a real beta-user question | Silence-proofed: first question is prepared |

**Cuts recommended:** slides 19-24 (roadmap appendix) are better as a link in chat; frees 4 minutes for I4.

**Why this shape:** remote room of 80 = join friction dominates (see the taxonomy in `reference/interaction-taxonomy.md`), so all four use the single QR/link join path. Budget was 3-4 for 30 min; delivered 4. Q&A at 80%, not 100%, of runtime.

## Example 2 — 45-minute internal security training, in-person, 20 people

Key decisions visible in the output:

- I1: show-of-hands confidence scale (small room, cheap, sets the dial) — *not* a poll; a 20-person room is a conversation.
- Two knowledge-check polls placed right after the phishing-ID section (retain job, material from the last five minutes).
- The "report an incident" attitude question is marked **anonymous** — in-person, it would be fiction; nobody publicly admits they'd email a colleague about a possible breach.
- One pair-discussion block (4 min) at minute 30 replaces three planned polls — same energy effect, more actual processing.
- Zero quizzes: this is a compliance training, the quiz is the *company's* requirement later, not this skill's suggestion; note that explicitly in the plan.

## Example 3 — "make my keynote more engaging" with no deck provided

The skill refuses to invent slide contents. Its first response asks for: the deck text or outline, audience composition, length, and setting (in-person/remote/hybrid), and offers to work from a talk description alone if the deck isn't final — noting the plan will anchor to minute-offsets instead of slide numbers, and the JSON output reflects that (`anchor.minute_offset`).

## What "engagement theater" looks like in a bad plan

> After slide 12: "Quick poll: do you agree that 2026 is our biggest opportunity yet?"

The skill's output would *reject* this: leading stem, no decision the result informs, and a fake-fork (one outcome makes the presenter look good). It would propose instead (if a poll belongs there at all): "What would most make you adopt this early? (Price / Integrations / Proof it works / Not this year)" — all four options actionable by the presenter.

# presentation-engagement

An agent skill that reviews a presentation, deck, lesson, or webinar and tells you **exactly where audience interaction belongs** — which technique, at what minute, for what cognitive job — instead of generic advice to "make it more engaging."

Most engagement advice is vibes. This skill encodes timing rules (attention resets ~every 10 min, with six priority slots), four cognitive jobs every interaction must serve (activate / reorient / evidence / retain), an interaction budget (a 45-minute talk can afford ~4-6 interactions because each costs ~90 seconds), and named failure modes (engagement theater, second-tab trap, poll fatigue, fake democracy).

## What it does

Give it your deck text, outline, or "45-min QBR, 30 slides, execs + team" description, and it returns:

- an annotated interaction plan table (placement, technique, duration, anonymity, "then-what" line),
- per-interaction detail blocks with draft questions,
- cut recommendations (sometimes the best engagement fix is deleting slides 17-22),
- a machine-readable JSON block so an agent with a slides API/MCP access can *create* the interactions, not just suggest them.

Full poll question craft and quiz generation live in sibling skills ([poll-question-writer](https://github.com/sambessey/poll-question-writer), [quiz-generator](https://github.com/sambessey/quiz-generator)); this one decides *where and why*.

## Install

The skill is a plain Markdown file — portable across Claude Code, Claude.ai, Codex, Hermes, OpenClaw, or any agent that accepts `SKILL.md`-format skills.

**Claude Code (personal):**
```bash
mkdir -p ~/.claude/skills/presentation-engagement
curl -sL https://raw.githubusercontent.com/sambessey/presentation-engagement/main/skills/presentation-engagement/SKILL.md -o ~/.claude/skills/presentation-engagement/SKILL.md
# optional reference table:
mkdir -p ~/.claude/skills/presentation-engagement/reference
curl -sL https://raw.githubusercontent.com/sambessey/presentation-engagement/main/skills/presentation-engagement/reference/interaction-taxonomy.md -o ~/.claude/skills/presentation-engagement/reference/interaction-taxonomy.md
```

**Project-local:** put the same folder at `.claude/skills/presentation-engagement/` inside your repo.

**Claude.ai / other agents:** paste `SKILL.md` into custom instructions or the skill upload, and keep `reference/interaction-taxonomy.md` readable alongside it.

**Plugin/marketplace:** repo ships `.claude-plugin/plugin.json` and `marketplace.json`; add the repo as a marketplace following [Claude Code plugin docs](https://docs.anthropic.com/en/docs/claude-code).

## Use it

Trigger by asking any agent that loaded it:

> "Review this deck for audience interaction" (paste outline)
> "Where should polls go in my 30-minute keynote?"
> "Add participation moments to this training module"

## Examples

See [`examples/`](examples/) for a full before/after: a quarterly business review that earned four interactions and a 6-slide cut.

## Roadmap

Phase 1 (now): recommendation-only — the JSON output is the contract (`skills/presentation-engagement/output-schema.json`). Phase 2: an MCP server / API bridge that turns that JSON into live polls, word clouds, and quizzes inside Google Slides or PowerPoint. The output schema is stable so agents today can hand it to any tool.

MIT © Sam Bessey

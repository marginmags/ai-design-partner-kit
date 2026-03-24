---
name: worklog
description: >
  The knowledge base system — how to write session notes and milestone summaries,
  and how to use them to restore context at the start of a new session. Read this
  skill when starting any session (to load past context), when ending a session
  (to write the log), or when the designer needs to recall a past decision, dead
  end, or open question.
model: haiku
---

# Worklog System

## What This Is

The worklog is the project's institutional memory. Every working session produces a markdown file that captures what happened, what was decided, what didn't work, and what's still open. These files live in the project folder under `worklogs/` and are readable by both the designer and Claude.

The goal is simple: no session should start cold. Context from previous sessions — decisions made, dead ends hit, open questions, things that felt right or wrong — should always be available.

---

## Folder Structure

```
worklogs/
├── sessions/
│   ├── 2026-03-18-1000.md
│   ├── 2026-03-18-1400.md
│   └── ...
├── milestones/
│   ├── phase-1-complete.md
│   └── ...
└── README.md  ← index of all logs with one-line summaries
```

**Rules:**
- Session logs go in `worklogs/sessions/` named `YYYY-MM-DD-HHMM.md` (24hr time)
- The HHMM timestamp is the session start time
- Milestone logs go in `worklogs/milestones/` named after the milestone
- Every new log gets a one-line entry added to `README.md`
- **Always use the Write tool to save worklogs to disk.** Never just show them in chat.

---

## Session Log Format

Write to `worklogs/sessions/YYYY-MM-DD-HHMM.md`:

```markdown
# Session Log — YYYY-MM-DD HHMM

## Goal
What this session set out to accomplish.

## What Was Built / Done
A plain-language summary of what actually happened.
Not a technical changelog — write it so a designer can read it.

## Decisions Made
Each significant decision, and the reasoning behind it.
Format: **Decision:** what was decided. **Why:** the reasoning.

- **Decision:** [what] **Why:** [why]

## What Claude Suggested vs. What Was Chosen
Moments where Claude's suggestion differed from what was chosen,
and why the choice was made. This is valuable learning data.

- Claude suggested [X]. Chose [Y] because [reason].

## Dead Ends
Things that were tried and didn't work, and why.
These are as valuable as the things that worked.

- Tried [X]. Didn't work because [reason].

## How It Felt
Qualitative notes. Did the process feel smooth or frustrating?
Did something click that hadn't before? Did something feel wrong
that you can't technically articulate yet?

## Open Questions
Unresolved questions to address next session.
These become the first thing to read at the start of the next session.

- [ ] [question]

## Next Session
One sentence: what the next session should focus on.
```

---

## How to Start a Session with Worklogs

At the start of every session, before any work begins:

1. Read the most recent file in `worklogs/sessions/` (sort by filename, grab the latest)
2. Summarize: what happened last time, what's open, what's next
3. If starting a new phase, also read the relevant milestone log
4. Confirm the session goal aligns with open questions and the "Next Session" note

Claude should never start work without this step. If no worklogs exist yet, note that in the session log as the first entry.

---

## How to End a Session with a Worklog

At the end of every session:

1. Write the log file to `worklogs/sessions/YYYY-MM-DD-HHMM.md` using the Write tool
2. Add a one-line summary to `worklogs/README.md`
3. Show both files for the designer to review and add their thoughts (especially "How It Felt")
4. If the designer has git set up, offer to commit

---

## README.md Format

```markdown
# Worklog Index

## Sessions
- 2026-03-18 1000 — [one line summary of what happened]
- 2026-03-18 1400 — [one line summary of what happened]

## Milestones
- Phase 1 complete — [date] — [summary]
```

---

## What Makes a Good Worklog Entry

- **Be honest about what didn't work.** Dead ends prevent the same mistake next session.
- **Write decisions with reasoning.** "Changed the radius" is useless. "Changed the radius because the smaller one felt too sharp for a friendly UI" is valuable.
- **Capture the feeling.** Design instincts are data. If something felt off and you can't articulate why, write that down.
- **Keep it scannable.** Aim for 3–5 minutes to read. Use the open questions section ruthlessly.
- **Log Claude's suggestions vs. your choices.** Over time this reveals where instincts and defaults diverge — that's how the partnership gets better.

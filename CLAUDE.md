# Design Partner Kit

## Session Startup — Do This Automatically

Every session, before responding to anything, read these in order:

1. `.claude/commands/second-brain/SKILL.md`
2. `.claude/commands/worklog/SKILL.md`
3. If a product-vision skill exists: `.claude/commands/product-vision/SKILL.md`
4. The most recent file in `worklogs/sessions/` (sort by filename, grab the latest)

**If no product-vision skill exists**, this is a new project. The second brain skill has onboarding instructions — follow them.

**If a product-vision skill exists**, greet the designer with a brief summary of where things left off and ask what they want to work on today.

## Session Wrap-Up

At the end of every session, prompt the designer to wrap up:

1. Write a session log to `worklogs/sessions/YYYY-MM-DD-HHMM.md` using the Write tool
2. Update `worklogs/README.md` with a one-line entry
3. Show both for the designer to review
4. If this was the first session, explain how future sessions work: "Next time you open this project in Claude Code, I'll automatically pick up where we left off."

## Skills

- **second-brain** — How Claude works with the designer. The operating manual.
- **worklog** — Session log format and how to maintain institutional memory.
- **skill-writing** — How to write, refine, and evaluate new skills.

Additional skills are generated during onboarding and added as the project evolves.

## Rules

- **Always write files to disk.** Use the Write tool. Never just show content in chat and call it done.
- **Always commit skill and worklog changes** if the designer has git set up.
- **Never push to a remote without asking first.**

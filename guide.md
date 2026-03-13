# MHC-G Guide

## What is this?

MHC-G is a lightweight working habit for people using Claude Cowork.

It does one thing: makes sure that when you use AI to do real work on your files,
you stay in control of the decisions — and you have a record of what happened.

You will not fill out forms. You will not learn commands. You will have a
conversation, and at the end of it something will have been made, and you
will know what you decided and why.

---

> **Developing or forking MHC-G?** Skip to [Developing MHC-G](#developing-mhc-g) below — the setup is different.

---

## What you need

- **Claude Desktop** with Cowork enabled (paid plan: Pro, Max, Team, or Enterprise)
- **This folder** (MHC-G) — you already have it

That's it. Claude will set up your project folder the first time you work together.

---

## Setup (2 minutes)

### Open in Cowork

1. Open **Claude Desktop**
2. Start a new Cowork task
3. When asked which folder to use, select **this folder** (MHC-G) directly
4. That's it. Claude will read CLAUDE.md automatically.

When you start a project, Claude will ask you what to call it and create a folder
for it inside MHC-G. You can have as many projects as you like — each gets its
own folder.

---

## Your first session

When Cowork starts, Claude will first ask: **"What should we call this project?"**

Give it a short name — anything works. Claude will set up a folder for it and
tell you where it is. Then it will ask: **"What are we working on today?"**

Tell it what you want to do. For example:

> "I have meeting notes from three client calls and I need to write a
> summary for my manager."

> "I want to draft a first version of the introduction for my report."

> "Help me organize the research I've collected into a coherent outline."

Claude will:

1. **Tell you what it's about to do** before doing it — and wait for you to say yes
2. **Ask when it reaches a real choice** — so you decide, not it
3. **At the end, offer to write up what happened** — one paragraph, saved to a file
4. **Tell you the first time it saves something** — what it is, where it lives,
   and that you can read or shape it at any time
5. **Follow the conventions you've established** — naming, structure, file
   organization — consistently across sessions

You can work in any language. Just start speaking in the language you prefer.

---

## What you will have after a few sessions

Your project lives at `projects/[name]/`. Inside you'll find your drafts,
notes, and source materials. Claude keeps system records in a `_records/` folder
alongside them — you can read those anytime.

The records include:

**Session log** — a running record of every session:
what you set out to do, what you decided, what was produced, what comes next.

**Decisions log** — a one-line-per-decision record:
every meaningful choice you made, and which file it affected.

These mean you can always answer:
- *What did I actually decide last Tuesday?*
- *Why does the document look like this?*
- *Where did I leave off?*

Claude reads them at the start of each session, so it picks up where you left off
without you having to re-explain everything. When a piece of work is ready to
share or submit, ask Claude to export it — it will produce a Word document, PDF,
or whatever format you need.

---

## Tips

**You don't need to remember anything special.**
Just open Cowork, say what you want to work on, and follow the conversation.

**If Claude starts doing something you didn't expect, say so.**
"Wait, that's not what I meant" is always the right thing to say.

**The session writeup is optional but valuable.**
The first few times, say yes to it. After a couple of sessions you will
understand why it matters.

**Your project files stay yours.**
Everything lives inside `projects/` on your computer. Nothing is sent
anywhere. When you want a copy of a deliverable somewhere else, ask Claude to
export it.

**As your project grows, consider separating what you brought in from what you produced.**
Claude uses an `inputs/` folder inside your project for source materials you've
provided. Your own drafts and outputs go at the root of the project folder.

---

## If something goes wrong

- **Claude seems confused about context:** Say "read session-log.md and tell me
  where we left off."
- **You want to start fresh:** Tell Claude "I want to start a new project."
  It will ask for a name and set up a folder inside MHC-G.
- **You want to see what's been decided:** Say "show me decisions.md."

---

## Passing it on

To share MHC-G with someone else, ask Claude to make a copy. It will produce a
clean folder containing only the essential files — no project history, no
personal notes. That folder is a new cell, ready to activate.

---

## Developing MHC-G

This section is for people who want to modify or fork MHC-G itself —
not use it on a project, but change the tool.

### Setup

Select MHC-G directly — the cell is the workspace:

```
MHC-G/              ← grant Cowork access to this folder
```

CLAUDE.md is at the root, so it loads automatically. `dev/` inside MHC-G is
your workspace. Claude will read `CLAUDE.md`, `CONTRIBUTING.md`, and
`dev/DESIGN.md` at session start and apply the editing protocol for the session.

### What governs changes

`CONTRIBUTING.md` sets out the editing protocol for `CLAUDE.md`.
Read it before making any change. The short version: `CLAUDE.md` has
as few rules as pass a generalizability check, and every change is
recorded in `dev/decisions.md`.

### Where things go

| What | Where | Travels with copies? |
|------|-------|---------------------|
| Design rationale | `dev/DESIGN.md` | Yes |
| Working documents | `dev/working/` | No |
| Tool decisions | `dev/decisions.md` | Yes |
| Session records | `dev/session-log.md` | No |
| Individual adaptations | `dev/adapt.md` | No |

### Forking

If you are adapting MHC-G for a different context:

- Keep `CLAUDE.md` to as few rules as pass the generalizability check relative to *your* target user
- Ship `CONTRIBUTING.md` with your fork so the constraint propagates
- Preserve the germinal section of `dev/decisions.md` — it is founding content, not operational history
- Adapt the check: "Would every user of *my* variant need this rule?"

---

*MHC-G v1.5 — Meaningful Human Control — Germinal*
*A minimal adaptation of the MHC methodology for Claude Cowork.*

# Contributing to MHC-G

This file applies when you are **developing or forking MHC-G** — changing the
tool itself, not using it on a project.

When this file is in context, apply the editing protocol below before making
any change to `CLAUDE.md`.

---

## The constraint

`CLAUDE.md` has **as few rules as pass the generalizability check**. The current count is 5.

Minimalism is not a style preference — it is what makes MHC-G work for users
who will never read a design document. Each rule added is a permanent tax on
every user. The threshold is correspondingly high.

Every addition, change, or removal is versioned: append one line to `dev/decisions.md`
per rule touched, with the generalizability argument written out. The count and
its history are visible; inflation is not silent.

---

## The generalizability check

Before any change to `CLAUDE.md`, answer:

> "Would a user applying MHC-G to a completely unrelated project — a recipe
> blog, a legal brief, a field research log — need this rule?"

**Yes** → the change may proceed to the protocol below.
**No** → the insight belongs in `dev/decisions.md` or `dev/DESIGN.md`, not in
`CLAUDE.md`. A rule that only makes sense for developing MHC-G is a
development convention, not a governance rule.

---

## The protocol

When a proposed change to `CLAUDE.md` passes the generalizability check:

1. State the proposed change in one sentence
2. State why it generalizes — answer the check explicitly
3. Get confirmation before editing
4. After editing, append to `dev/decisions.md`:
   `YYYY-MM-DD | [rule added/changed/removed] | CLAUDE.md | [why it generalizes]`

The `dev/decisions.md` entry is not optional. It is the record that the check
was applied.

---

## Coherence check

After any change to a MHC-G file, check all other files for references,
counts, or descriptions that reflect what changed. Files to check:
`CLAUDE.md`, `DESIGN.md`, `CONTRIBUTING.md`, `guide.md`.

A change that isn't propagated is incomplete.

---

## Where insights go when they fail the check

| Type | Where it goes |
|------|---------------|
| Operational adaptation (context-specific) | `dev/adapt.md` or `adapt.md` |
| Why a decision was made | `dev/decisions.md` |
| Design principle or rationale | `dev/DESIGN.md` |
| Session record | `dev/session-log.md` |
| Structural exploration | `dev/working/` |

---

## For forks

If you are forking MHC-G to create a variant:

- Keep `CLAUDE.md` to as few rules as pass the generalizability check relative to *your* target user
- The question becomes: "Would every user of my variant need this rule?"
- Preserve the germinal section of `dev/decisions.md` — it is founding content, not operational history
- Ship this file with your fork so the constraint propagates

---

## Activating this workflow in Cowork

Select MHC-G directly — the cell is the workspace:

```
MHC-G/              ← grant Cowork access to this folder
```

CLAUDE.md is at the root of MHC-G, so it loads automatically. Claude will read
`CLAUDE.md` and this file at session start. The editing protocol is then active
for the session.

---

*This file governs changes to MHC-G itself. It does not apply when using
MHC-G on a project.*

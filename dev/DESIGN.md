# MHC-G Design Document

**Version:** 1.6
**Date:** 2026-03-16
**Status:** Active

---

## What MHC-G Is

MHC-G (Meaningful Human Control — Germinal) is a minimal working habit for people
using Claude Cowork. It ensures that when AI does consequential work on a user's
files, the human stays in control of decisions — and has a readable record of
what happened.

It is not a governance system. It is not a methodology with commands and templates.
It is a conversation pattern that leaves something behind.

G = Germinal: this is the founding cell, the first instance of the species.

---

## Target User

Someone switching from casual Claude.ai use to Claude Cowork. Not a technical
user. Does not know what an epistemic trace is and does not need to. Has just
gained access to a tool that can do real work on their files, and needs just
enough structure to stay oriented and in control.

The need for MHC-G is latent until the tool is powerful enough to need it.
Cowork users will feel that need — the AI is doing consequential work on their
files. MHC-G is what was already waiting when they hit that moment.

---

## Design Principles

### 1. Conversation-first

No commands. No template-filling. The user has a conversation; artifacts are a
byproduct of that conversation. The discipline is in how Claude behaves, not in
what the user has to learn.

### 2. Five rules

The workflow chain (trace → PDL → prompt → modlog) is replaced by five
conversational rules:

- **Rule 1 — Before:** State intent, wait for confirmation
- **Rule 2 — During:** Surface choices, let the human decide
- **Rule 3 — After:** Write up what happened — as a session log entry or a named document
- **Rule 4 — Persist:** All project work lives inside `projects/[name]/`
  — drafts and source materials at the root, system records in `_records/`.
  When a project is created, the user is told its path. When something is
  first saved, they are told what it is and where it lives. Deliverables are
  exported on request in whatever format the user specifies.
- **Rule 5 — Cohere:** As conventions take shape in a project — how files are
  named, organized, and labelled — maintain them consistently. When creating
  or modifying files, check that new work is coherent with existing decisions.

Rules 1–3 are the minimum required for the clearing test to pass. Rule 4
ensures persistence is never opaque — the user always knows what exists, where
it lives, and can read or shape it. Rule 5 ensures the conventions the user
has shaped are maintained consistently across sessions.

### 3. The clearing test

*The user should be able to close this conversation and return next week knowing
exactly where they are, what was decided, and why.*

This is the only quality criterion for session-log.md. If it would not pass this
test, it is not complete enough.

### 4. Limitations as features

MHC-G is designed for Cowork. Cowork's constraints are treated as design
affordances, not problems to work around:

- **No `rm`** → artifacts accumulate; nothing is ever lost. This is immutability,
  not a limitation.
- **No commands needed** → natural language is native. The habit is lighter than
  a system.
- **No hooks confirmed** → session-end becomes a conversational moment ("Shall I
  write up what we did?"), which is better UX than a silent background script.

### 5. Minimum viable structure

```
MHC-G/                          ← user selects this folder directly in Cowork
├── CLAUDE.md                   ← genome (travels with copies)
├── guide.md                    ← phenotype guide (travels with copies)
├── CONTRIBUTING.md             ← selection mechanism (travels with copies)
├── adapt.md                    ← user-level preferences (does not travel)
├── projects/                   ← all project work (does not travel)
│   └── my-project/
│       ├── draft_v1.md         ← work files at root
│       ├── notes.md
│       ├── inputs/             ← internalized source materials
│       └── _records/           ← system records
│           ├── session-log.md
│           ├── decisions.md
│           └── adapt.md
└── dev/                        ← MHC-G development
    ├── DESIGN.md               ← body plan (travels with copies)
    ├── decisions.md            ← fossil record (travels with copies)
    ├── adapt.md                ← dev-specific adaptations (does not travel)
    ├── session-log.md          ← field notes (does not travel)
    └── working/                ← lab bench (does not travel)
```

### 6. AI-congruent governance

MHC-G's rules are principles, not procedures. This is not merely a stylistic
preference — it is a design decision grounded in what language models do well
and what they do badly.

Language models perform well when asked to interpret principles in context,
exercise judgment, and communicate in natural language. They perform poorly
when asked to follow rigid procedures, manage state across steps, and comply
with exhaustive behavioral checklists. The predecessor system (MHC v1–v3.37)
grew by adding rules to patch each unexpected behavior — a compliance
architecture that systematically placed the AI in conditions of poor cognitive
fit. MHC-G inverts this: it defines boundary conditions and relies on the
model's strengths (contextual reasoning, dialogue, coherence maintenance) to
do the rest.

The practical consequence is that error correction runs through dialogue
(Rules 1 and 2), not through additional rules. When the model misapplies a
principle, the user redirects in conversation. When the predecessor system's
model misapplied a rule, a new rule was written. The first approach is
self-correcting; the second is accretive and fragile.

This is also why the biological framing is not decorative. A genome sets
boundary conditions; it does not micromanage cellular behavior. The
relationship between CLAUDE.md and the model's behavior mirrors this: the
genome constrains without prescribing, and the model operates within those
constraints using its native capacities.

### 7. Reproduction

A copy of MHC-G is produced by extracting the genome only:
`CLAUDE.md`, `guide.md`, `CONTRIBUTING.md`, `dev/DESIGN.md`, `dev/decisions.md`.

User state (`projects/`, `dev/working/`, `adapt.md`, `dev/session-log.md`)
does not travel — it belongs to this individual cell. The result is a new,
inert cell ready to be activated. It can be delivered as a folder or a zip.

There is no git requirement. Any individual may choose to track their cell in
git, but reproduction does not depend on it.

---

## Cell Architecture

MHC-G is a reproducible cell architecture for AI-assisted work.

- **The cell** is `MHC-G/`. The user selects it directly in Cowork — the cell
  is the workspace. The membrane is what travels (genome, guide, selection
  mechanism). Internal state (`adapt.md`, `projects/`) does not cross the
  membrane.

- **The nucleus** is `CLAUDE.md`. The genome. Transcribed at every session.
  Everything else is downstream of it.

- **The cytoplasm** is `projects/[name]/`. Where the work of the cell happens.
  Work files live at root level; `_records/` holds the metabolic record
  (session-log, decisions, project-level adapt).

- **Inputs are internalized.** External files cross the membrane and become
  markdown inside `inputs/`. The cell does not link out to source materials —
  it absorbs them.

- **Deliverables are secreted outward.** When a deliverable is ready, Claude
  exports it to wherever the user specifies. The markdown source remains inside
  the cell; the secreted product takes whatever form the user requests.

- **Adaptation is inside the cell.** `adapt.md` at user level (`MHC-G/`) and
  project level (`_records/`) modifies behavior without touching the genome.
  This is epigenetic — context-dependent expression of the same genome.

**Reproduction.** A new project can be initiated in two ways:

- *Germ-line*: fresh instantiation from the genome alone, no prior project
  state. User-level `adapt.md` is inherited silently if it exists.

- *Differentiated*: new project inherits `_records/adapt.md` from an existing
  project as its starting point. Conventions carry forward; work history does
  not. Claude offers this when other projects are present and the user starts
  a new one.

In both cases, Claude asks for a project name, creates the structure, and
tells the user where their project lives.

---

## Cowork Technical Constraints

*From compatibility testing on 2026-02-13 (MHC v3.11 / Cowork, Opus 4.6)*

| Fact | Implication for MHC-G |
|------|----------------------|
| CLAUDE.md auto-loads when folder is selected | Select MHC-G directly — zero setup friction |
| Cowork runs Claude Code 2.1.34 in Linux VM (Ubuntu 22) | Full file read/write available |
| Session JSONL exists at `/sessions/*/mnt/.claude/projects/-sessions-*/*.jsonl` | Session history recoverable if needed |
| `rm` is blocked in mounted folder | Never design for deletion — use append/accumulate only |
| `hostname` returns `claude`, `uname` returns `Linux` | Never use hostname/OS detection — use `/sessions/` path pattern or session UUID |
| Python 3.10.12 available | Scripts possible if needed, but MHC-G avoids them by design |
| PowerShell not available | Never use PS1 scripts |
| SessionEnd hooks: status unknown | Do not rely on hooks; make session-end explicit and conversational |
| User selects one folder in Cowork | MHC-G IS the workspace — select it directly. All project work lives inside `projects/[name]/` |

*Re-test recommended on current Cowork version before adding any feature that
depends on these facts.*

---

## What MHC-G Is Not

- **Not an adaptation of MHC.** MHC-G is a redesign. Do not port MHC commands,
  templates, or the agent-file architecture into MHC-G. That defeats the purpose.
- **Not a governance system.** MHC-G does not produce audit-grade artifacts.
  Users who need full audit trails should use MHC (Claude Code version).
- **Not a replacement for MHC.** It is an entry point. The upgrade path from
  MHC-G to full MHC is intentional and should remain open.

---

## Open Questions / Backlog

- [ ] Does SessionEnd hook fire reliably in current Cowork? (infrastructure
      exists, behavior unconfirmed — test before designing any auto-export)
- [ ] How does MHC-G handle continuity when the user forgets to trigger the
      session-end writeup? (silent recovery? next-session prompt?)
- [ ] Is MHC-G a standalone product or an explicit gateway to full MHC?
      Does that framing matter to the user?
- [ ] Can `decisions.md` (one line per decision) capture enough for users
      who later need to reconstruct reasoning? Or does it need more structure?
- [ ] Distribution channel: independent download, bundled with Cowork
      onboarding, or Anthropic partnership?
- [x] Multi-project workspace: resolved — all projects live inside
      `projects/`; Session Start initiates or resumes based on context.
- [x] Reproduction mechanism without git: resolved — genome-only copy,
      delivered as folder or zip. No git dependency.

---

## Development Methodology

MHC-G is developed using MHC-G itself. Design sessions in Cowork produce entries
in `dev/session-log.md` and `dev/decisions.md`. Working documents and session
traces go in `dev/working/` (they do not travel with copies).

This document is updated when design decisions are made — not as a changelog
of every change, but as a living statement of what MHC-G is and why.

### Founding trace
`dev/working/trace_MHC-P_cowork_redesign_20260312.md` — contains the full
reasoning behind the design, preserved formulations, and open questions as of
the founding session.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.6 | 2026-03-16 | Design principle 6 (AI-congruent governance) added: rules are principle-shaped because principle-based governance fits the cognitive profile of language models; biological framing explained as structurally load-bearing, not decorative |
| 1.5 | 2026-03-13 | Renamed MHC-P → MHC-G (Germinal); cell selection principle — user selects MHC-G directly, no parent folder; reproduction mechanism without git (genome-only copy, folder or zip); path prefix MHC-G/ dropped from internal references; dev/adapt.md established for individual-layer shipping instructions |
| 1.4 | 2026-03-13 | Cell architecture: all project work moved inside MHC-P/projects/[name]/; _records/ subfolder for system records; inputs/ for internalized source materials; reproduction mechanism (germ-line and differentiated); Workspace section updated |
| 1.3 | 2026-03-12 | Rule 4 rewritten as transparency principle; records and adaptations moved into MHC-P/projects/; adapt layer introduced; gitignore model established |
| 1.2 | 2026-03-12 | Rule 5 (Cohere) added; Rule 4 extended with file context default and input tracing; coherence check added to CONTRIBUTING.md |
| 1.1 | 2026-03-12 | Rule 4 (Persist) added; governance artifacts moved from MHC-P/ to project folder; dev/ established as dev project folder; structure diagrams updated |
| 1.0 | 2026-03-12 | Initial design — CLAUDE.md (3 rules), guide.md, session-log.md, decisions.md |

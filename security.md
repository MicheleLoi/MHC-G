# MHC-G — Security

If you spent time wondering whether you needed a virtual disk, extra isolation,
or special precautions before using MHC-G: you don't. But "trust me" isn't useful,
so here is what is actually true — and how to verify each claim yourself.

---

## What Claude can access

**Claude can only read and write files inside the folder you selected.**
Cowork grants file access to one folder at a time. If you selected `MHC-G/`,
Claude cannot see anything outside it.
*To verify: in Claude Desktop, check the folder access dialog when you start a Cowork task.*

**MHC-G contains no scripts that run automatically.**
There is no code that executes on its own. Everything Claude does happens
through conversation, in response to what you say.
*To verify: open the MHC-G folder. You will find .md files only.*

**`CLAUDE.md` is the only instruction file, and you can read all of it.**
Claude's behavior in MHC-G comes entirely from this file. There are no hidden
instructions.
*To verify: open `CLAUDE.md` and read it. What you see is what Claude receives.*

**Your files stay on your machine.**
The `projects/` folder is a regular folder on your computer — you can open,
move, or back it up at any time. Cowork does not copy your files elsewhere.
*To verify: navigate to `projects/` in your file manager.*

---

## If you have sensitive files

Don't put them in the MHC-G folder. Claude reads everything in the workspace —
that is how it helps you. If a file shouldn't be part of the work, keep it
elsewhere. You don't need a virtual disk. You just need to keep the MHC-G
folder for MHC-G work.

---

## What MHC-G doesn't protect against

If you paste a document into the conversation that contains instructions
designed to manipulate Claude's behavior — a technique sometimes called
prompt injection — Claude may be affected. This is a general property of
language models, not something specific to MHC-G. Working with documents
from unknown or untrusted sources carries this risk regardless of which
AI tool you use.

MHC-G does not make this risk worse. It does not make it better either.

---

*If something here is out of date or unclear, open an issue or contact the maintainer.*

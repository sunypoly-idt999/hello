# Cowork → Zettel: An Exploration Brief

**For:** Paul
**From:** Steve
**Account:** SUNY Poly Claude Team
**Date:** August 2, 2026

## The objective

I want us to use Claude Cowork the way it's actually meant to be used — extensively, conversationally, as a coding and thinking partner rather than a one-off tool — and then mine what accumulates for ideas worth keeping. The workflow has two halves:

1. **Work out loud in Cowork.** Do real course work (lectures, assignments, site builds, data wrangling) in Cowork's conversational-coding mode. Don't treat sessions as disposable. The point is to generate a rich body of authentic working sessions.
2. **Surface the themes.** Periodically read back across those sessions, pull out the recurring patterns, decisions, and insights that have value beyond the single task, and fold them into the zettel.

I'll run this **course by course** for now — one course as the pilot rather than trying to boil the whole archive at once. That keeps the corpus small enough to actually read and the themes specific enough to be useful.

## Why this is worth doing

The key realization: **Cowork is already self-archiving.** Every session writes itself to disk automatically — the full transcript, my prompts, the files I upload, and the outputs it produces — all stored locally on the machine. Nobody has to remember to save anything. It just accumulates as a byproduct of working.

The catch is that it's an *archive*, not a *memory*. It preserves everything but surfaces nothing on its own. The files are dense, UUID-named, and mixed — real thinking sits right next to hundreds of automated task runs. So the free part is the capture; the part that needs deliberate effort is the reading-back. That's the whole game here: turn a passive archive into zettel-ready insight.

## What the data actually looks like

I already cracked open an export of the local session store to confirm the shape:

- Roughly **470+ sessions** spanning several months, most in a heavy stretch of daily use.
- Each session stores a **metadata JSON** (title, my opening prompt, model, timestamps, which folder I had open) plus a full **turn-by-turn transcript** in JSONL.
- The transcripts live at `.claude/projects/<project>/<session>.jsonl` — the same format the Claude Code CLI uses.
- Each session also keeps its `uploads/` (what I fed in) and `outputs/` (what got produced).
- **Signal vs. noise matters:** a large fraction of sessions are repetitive automated runs (scheduled tasks) with little idea content. The real thinking clusters under project-tagged folders. Filtering the automation out is step one of any mining pass.

The mineable substance, in order of value: (1) my opening prompts — often the raw idea before Claude touched it, (2) the assistant's reasoning and deliverables, (3) the finished artifacts in `outputs/`.

## Tooling to explore

Because Cowork stores transcripts in the standard `.claude/projects/*.jsonl` format, the existing open-source Claude Code transcript ecosystem works on our data directly — we just point it at the nested session paths. Worth a look, roughly in priority order:

- **[daaain/claude-code-log](https://github.com/daaain/claude-code-log)** — Python CLI that processes an entire `projects/` tree into a linked index plus per-session HTML, with token-usage tracking. Best "process everything at once" starting point.
- **[kiliman/claude-transcript](https://github.com/kiliman/claude-transcript)** — JSONL → clean Markdown, preserving images and tool calls. Markdown output is the ideal feedstock for theme-mining and for dropping into the zettel.
- **[simonw/claude-code-transcripts](https://github.com/simonw/claude-code-transcripts)** — JSONL → paginated, mobile-friendly HTML. Good for publishing or sharing a session with someone.
- **[withLinda/claude-JSONL-browser](https://github.com/withLinda/claude-JSONL-browser)** and **[qent/jsonl](https://github.com/qent/jsonl)** — browser-based explorers with search across many logs. Good for interactive spelunking.
- **[jhlee0409/claude-code-history-viewer](https://github.com/jhlee0409/claude-code-history-viewer)** — a full desktop app for browsing and analyzing history, with HTML/JSON export.

**One caveat before we lean on any of these:** the JSONL entry format is internal to the app and shifts between versions, so these parsers can break on individual fields. They're solid for reading and export; riskier as a permanent pipeline. For a durable workflow we'd likely want our own thin extractor that pulls just the fields we care about (title, date, project, prompts, outputs) and is easy to patch when the format drifts.

## Proposed first step

Pick one course as the pilot. Run its work in Cowork normally for a stretch, then do a single mining pass: batch-convert that course's sessions to Markdown with `claude-code-log` or `kiliman/claude-transcript`, filter out the automated runs, read the rest, and draft the first handful of zettel notes from what recurs. Evaluate the yield before scaling to more courses.

If the output quality looks good, the second step is deciding whether the off-the-shelf parser is enough or whether we build the small custom extractor for the long haul.

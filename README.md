# work-journal

The knowledge half of the workflow kit: a private, server-local git repo
that accumulates your engineering record. The engine that reads and writes
it lives in the companion repo (`dotclaude`); this repo is the data.

## What lives here

| Path | What | Written by |
|---|---|---|
| `daily_logs/YYYY-MM-DD.md` | One file per working day | SessionEnd hook (structural stub) + `/journal` (rich entries) + optional nightly journal-cron |
| `tasks.md` | The task board (Obsidian-Tasks emoji grammar) | the `tasks.py` engine via `/task` — never by hand for state changes |
| `tasks_archive.md` | Closed tasks, moved monthly by `/task prune` | the engine |
| `projects.md` | Cross-project dashboard, one block per active project | `/journal` (ambient bumps) + `/projects` (deliberate edits) |
| `project-ideas.md` | Idea inbox with sweep watermarks | `/project-sweep` (append-only) + `/project-clean-up` (organize) |
| `feedback.md` | Feedback you receive, newest first | ambient capture per your CLAUDE.md standing rule, or `/feedback` |
| `research/{trading,dev}/` | Per-topic research notes (frontmatter: topic/status/stage/updated) | `/note` + standing capture rule |
| `research/sources/` | Immutable snapshots of cited artifacts | snapshot-on-cite rule (see its README) |
| `research/reports/` | Shareable PDF briefs | your report tooling |
| `plans/{speculative,complete,archived}/` | Plan documents | `/plan` + `/promote-plan` |
| `oneoffs/` | Runbooks, handoff specs | you |
| `command-log.tsv` | Slash-command invocations (ts, host, cwd, command) | UserPromptSubmit hook; read by `/briefing` cadence alerts |

## daily_logs file schema

```
# YYYY-MM-DD

## HH:MM — <project> [(manual /journal)]

**cwd:** `<path>`
**branch:** `<branch>`

### What was done / ### Decisions / ### Open / blocked / ### Next
```

The SessionEnd hook writes a minimal stub (cwd, branch, commits today,
uncommitted state) only when the session's repo had activity. `/journal`
entries add the four rich sections. A day can hold many entries.

## Conventions that keep it working

- **Commits are yours (or /journal's).** Hooks and the task engine never
  commit — `/journal` ends with `git add -A && git commit && git push`, so
  pending board/idea changes ride along with each journal entry.
- **Cross-box sync**: `.gitattributes` sets union merge for `.md`/`.tsv`,
  so two machines appending to the same day never conflict destructively.
  The `journal-sync` timer (companion repo) commits/pulls/pushes on a
  schedule. Union merge can occasionally duplicate task lines — the
  engine's dedup guard cleans those.
- **Task state changes go through the engine** (`/task` → `tasks.py`):
  completion stamps and recurrence math stay deterministic. Reorganizing
  sections or rewording by hand is fine; run `tasks.py check` after.
- **Notes are append-only journals of a topic**, one dated section per
  finding, each ending with a `_source:` line. Negative results are
  first-class.
- Keep this repo PRIVATE — it will fill with your employer's context.

## Bootstrapping

This repo ships as a scaffold: empty dirs, header-only files, one example
projects block. Clone it as `~/work-journal`, create a private remote for
it, and start working — the hooks and commands in the companion repo do
the rest. See the companion repo's INSTALL.md.

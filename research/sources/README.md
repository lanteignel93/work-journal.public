# research/sources/ — cited source material

Immutable snapshots of artifacts cited by notes in `research/trading/` and
`research/dev/`. Shared across both domains.

## Convention

- **Snapshot on cite, not dump-everything.** A file lands here at the
  moment a research note cites it — generated reports, received PDFs,
  one-off review notes, anything that would otherwise live on a temp path
  or a regenerable network-share path. Invariant: everything here is
  referenced by at least one note, at the version that was cited.
- **Naming**: `YYYY-MM-DD-<slug>.<ext>` — the date of the ARTIFACT, not of
  the copy.
- **Immutable**: never edit a snapshot; a new version of a report is a new
  dated file. Notes cite the vintage they analyzed.
- **Size guard**: over ~10MB, store a pointer file instead
  (`<name>.pointer.md` with original path + sha256 + generation command).
- Notes reference these as `research/sources/<file>` (repo-relative), so
  citations survive machine moves and cross-box sync.

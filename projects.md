# Projects

One block per active project. The `## <slug>` must match the repo's
checkout basename (add `- **aka:** <name>` for machines that name the
checkout differently) so the SessionStart hook can inject the matching
block into every session you open in that repo. `/journal` bumps the
matching block ambiently; `/projects` manages blocks deliberately;
`/week` reviews staleness. Retired blocks move under `## Archive` with an
archived date — never delete.

## example-project — active
- **aka:** example-project-checkout
- **thread:** one sentence: the current line of work
- **next:** the concrete next action(s)
- **blocked:** what it's waiting on (omit the line if nothing)
- **links:** research notes · PRs · plans
- _updated YYYY-MM-DD_

## Archive

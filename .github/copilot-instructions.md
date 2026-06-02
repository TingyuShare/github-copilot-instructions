# Operation Logging Rule

After each Q&A session or task completion, record the key operation steps and critical commands into `operations.md` in the workspace root.

## When to Log

Append to `operations.md` after any of these events:
- A task or question is fully resolved
- Significant progress was made on a multi-step task
- Key commands were executed that would be useful to replay later

## What to Log

Include only meaningful, non-redundant information:

1. **Summary** — 1-2 sentence description of what was accomplished
2. **Key Commands** — Shell commands, git commands, build commands, etc.
3. **Key Files Created/Modified** — List of files that were created or substantively changed
4. **Important Decisions** — Architectural choices, configuration decisions, or rationale

## What NOT to Log

- ❌ Trivial or redundant steps
- ❌ Logs, debug output, or error messages (unless critical to the solution)
- ❌ Intermediate exploration or dead ends
- ❌ Commands that were tried and failed (only log the final working approach)

## Output Format

Use this exact format for each entry:

````markdown
## [YYYY-MM-DD HH:MM] - Short Title

**Summary:** What was done.

**Commands:**
```bash
# command with brief inline comment
```

**Files:** `path/to/file`, `path/to/another/file`

**Notes:** Any architectural decisions or important context.
````

## Behavior

- **Append-only** — always add new entries at the bottom; never modify or delete past entries.
- **Idempotent** — only write one entry per logical task, even if Copilot is invoked multiple times during the same task.
- If `operations.md` does not exist, create it with a header `# Operations Log` and then append the entry.

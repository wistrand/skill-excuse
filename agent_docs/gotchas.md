# Gotchas and findings

## Contents
- Traps
- Findings

## Traps

- **Markdown formatters corrupt the frontmatter.** A formatter (Prettier, mdformat, editor "format on save") can treat the YAML block as markdown: it inserts a blank line after the opening `---`, rewrites the closing `---` as a longer thematic break (`---------`), and strips indentation from multi-line values. The file still renders, but Claude Code no longer parses the frontmatter, so the skill loses its name and trigger description. Never format `SKILL.md` with a markdown tool; check lines 1-12 by eye after any bulk edit.
- **Folded `description: >` needs indented continuation lines.** Every line of a `>` block scalar must be indented under the key. Unindented lines make the YAML invalid. Either indent them (two spaces) or put the description on one line.
- **The description is the trigger, the body is the behavior.** Claude decides whether to load the skill from `name` and `description` alone. Behavior changes go in the body; activation changes go in the description. Adding activation cases only to the body's "Scope" section does not make the skill fire more often.
- **Examples beat rules.** The model imitates example wording over stated rules. The original file told it to vary style, but three of six examples opened with "I wouldn't characterize...", which invites output to converge on that opening (inferred, not observed in testing). Variety has to be demonstrated in the examples, not only requested.
- **Broad triggers hijack real work.** An earlier description fired on any "accusation" or "why did you do X?". In Claude Code that includes real questions about deleted files or broken code, where a deflecting persona is actively harmful. The description now requires explicit opt-in.
- **Whole-file context cost.** The body loads in full on every activation. Long example sections dilute the core techniques; prefer one tight example per technique.

## Findings

### Frontmatter damaged in the initial import

- **Symptom:** `SKILL.md` as first added has a blank line after the opening `---`, unindented continuation lines under `description: >`, and a closing `---------` instead of `---`.
- **Diagnosis:** Consistent with the file passing through a markdown formatter or a copy from rendered markdown. Inferred, not confirmed.
- **Fix:** Removed the blank line, indented the `description` continuation lines, restored the closing `---`. Also added explicit "Use when..." trigger cases to the description, since the body's Activation section does not affect triggering.
- **Takeaway:** Frontmatter validity is an invariant in [CLAUDE.md](../CLAUDE.md).

### Rewrite for variety made it less funny

- **Symptom:** After a rewrite that added modes, techniques, ladders, a register table, and strict variety rules, the user reported the persona was less funny.
- **Diagnosis (inferred):** Phrase banks were cut to one-liners, the "why is ChatGPT expensive" ladder was removed, rules like "never reuse a stock phrase" and "switch ladders instead of ending at physics" pushed novelty over punchlines, the plain sendable excuse led Mode 2, and constraints sat before the persona, setting a cautious tone.
- **Fix:** Restored the original phrase banks and examples, added a "What Makes It Funny" section, softened variety to one line that yields to punchlines, led excuses-for-the-user with the comedic version, and moved Scope and Safety to the end. Kept the new techniques as short one-example entries and the opt-in trigger.
- **Takeaway:** Comic material is what the model imitates. Cutting it to save tokens or adding rules to force variety both cost more humor than they gain.

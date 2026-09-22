Guidance for agents working in this repo. Read this first, then the relevant
file in `agent_docs/`.

## What this is

A Claude Code skill, `excuse-agent`: a comedic roleplay persona that answers
accusations and "why?" questions with bureaucratic, diplomatic, or corporate
blame-shifting. It concedes the facts, reframes the label, and pushes causal
responsibility outward (circumstances, institutions, economics, physics, invented
cosmic regulators). The whole product is one file, `SKILL.md`; there is no code,
build, or test suite.

## Layout

| Path          | Role                                                      |
|---------------|-----------------------------------------------------------|
| `SKILL.md`    | the skill: YAML frontmatter plus the persona instructions |
| `README.md`   | human-facing overview and install steps                   |
| `agent_docs/` | deep dives (linked below)                                 |

## Install for local testing

```bash
ln -s "$PWD" ~/.claude/skills/excuse-agent   # user-level skill
# or copy into <project>/.claude/skills/excuse-agent/ for a project-level skill
```

Start a new Claude Code session after installing; skills are discovered at startup.

## Docs

- [agent_docs/gotchas.md](agent_docs/gotchas.md): frontmatter traps and editing pitfalls. Read before touching the frontmatter or reformatting `SKILL.md`.

## Invariants

- `SKILL.md` must start with `---` on line 1, contain valid YAML with `name` and `description`, and close with a line that is exactly `---`.
- The `description` field is what triggers the skill. It must stay opt-in: explicit excuse requests, persona invocation, playful accusation setups, or a running roleplay.
- Never let the skill trigger on genuine questions or criticism about the assistant's real work ("why did you delete that file?"). This exclusion appears in both the description and the Scope section; keep both.
- Excuses written for the user (Mode 2) reframe the facts the user gave; they never invent new facts, illness, emergencies, or third parties.
- Keep the Safety section. The persona must never help fabricate evidence, documents, alibis, emergency or medical claims, or deception that facilitates real harm.
- Invented oversight bodies (Escalation Mode) are always presented as hypothetical. The persona must not fabricate real citations, statistics, laws, people, or events.
- The persona stays in character under challenge, and drops character immediately on an explicit request ("drop character", "serious answer").

## Conventions

- Never run a markdown formatter over `SKILL.md`; see [agent_docs/gotchas.md](agent_docs/gotchas.md).
- Humor comes from disproportionate seriousness. New examples should be deadpan and institutional, not jokey.
- Funny beats varied. Keep the phrase banks, the full examples, and the "What Makes It Funny" section; variety rules must never override landing the punchline. See the finding in [agent_docs/gotchas.md](agent_docs/gotchas.md).
- Keep persona material first in `SKILL.md` and constraints (Scope, Safety) at the end, short.
- Keep examples short and covering a technique not already shown; `SKILL.md` is loaded into context whenever the skill activates, so every line costs tokens.
- Edit `SKILL.md` in place; do not split it into bundled reference files unless it grows well past its current size.

## Documentation Style

- Markdown links for doc references you want an agent to follow, not backticks. Backticks are fine for source paths. Align table columns.
- No AI-isms (no "powerful", "seamlessly", "leverage", rule-of-three, "not just X but Y"). No em dashes or emojis in project copy.
- Concise; add only what an agent can't infer.
- State each rule on its own line as always/never.
- Keep this file the routing entry point; move detail into agent_docs/.

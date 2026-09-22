# Excuse Agent

A Claude Code skill that answers accusations with the composure of a government press office.

Ask it why it's late, whether it ate your cake, or why something costs so much, and it will concede the facts while disputing everything else: what the action should be called, who created the conditions that made it necessary, and who controls whether it continues. Keep asking "why?" and responsibility moves outward, through institutions and economics to physics, and finally to regulatory bodies that clearly should have been supervising the universe. It is meant for comedy, satire, roleplay, and studying how blame-shifting rhetoric works.

## Example

> **You:** Why are you late?
>
> **Excuse Agent:** I wouldn't characterize the situation as "late." The original arrival timetable became operationally unrealistic after external traffic conditions changed. Once those conditions existed, arrival time was largely determined by the transportation network rather than by me. So I arrived at the earliest time the road system was prepared to permit.

It can also write an excuse for you to send, built from what actually happened:

> **You:** Give me an excuse for my boss. I overslept and missed standup.
>
> **Excuse Agent:** "Sorry for missing standup this morning, my alarm didn't do its job. I'm online now and will post my update in the thread." (Plus an escalated version, not for sending.)

## Install

Copy or symlink this directory into your Claude Code skills folder:

```bash
# for all your projects
ln -s "$PWD" ~/.claude/skills/excuse-agent

# or for a single project
mkdir -p /path/to/project/.claude/skills
cp -r . /path/to/project/.claude/skills/excuse-agent
```

Start a new Claude Code session. The skill activates when you ask for an excuse, invoke the Excuse Agent, or set up a playful accusation. It stays out of real questions about Claude's actual work. Say "drop character" or "serious answer" to end it.

## Limits

The persona will defend almost anything rhetorically, but it declines to fabricate evidence, documents, alibis, medical or emergency claims, or anything meant to deceive someone in a way that causes real harm. It redirects those requests toward an obviously fictional excuse.

## How it works

Everything lives in [SKILL.md](SKILL.md): three modes (spokesperson, excuse for you, and out-of-character analysis), fourteen rhetorical techniques (challenge the category, shift the causal starting point, passive voice, review deferral, the non-apology), several escalation ladders for repeated "why?" questions, a set of registers from legal defense to diplomatic communique, and worked examples.

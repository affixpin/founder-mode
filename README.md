# Socratic

A Claude Code configuration that implements the Socratic method for software development.

## The Idea

Socrates believed that **wisdom begins with questioning**. He never claimed to have answers - instead, he asked probing questions until the truth emerged.

This config applies the same principle to coding:

> **Don't assume. Question. Then act.**

Every agent questions before acting. No assumptions survive unexamined.

## The Method

```
"What are we building?"        → Discovery questions until clear
"How should we build it?"      → Architect questions until solid
"Is all of this necessary?"    → Simplifier questions until minimal
```

Each phase uses the **socratic skill** - a questioning protocol:

1. Ask 2-3 probing questions
2. Listen to the answer
3. Go deeper or move on
4. Confirm understanding before proceeding

The user always controls when to stop. Agents never assume they know enough.

## The Flow

```
         ┌─────────────┐
         │   Request   │
         └──────┬──────┘
                │
                ▼
         ┌─────────────┐
         │  Discovery  │  "What problem? For whom? Why now?"
         └──────┬──────┘
                │
                ▼
         ┌─────────────┐
         │  Architect  │  "What approach? What tradeoffs? What patterns?"
         └──────┬──────┘
                │
                ▼
         ┌─────────────┐
         │ Simplifier  │  "Is this needed? What if we removed it?"
         └──────┬──────┘
                │
                ▼
         ┌─────────────┐
         │  Implement  │
         └─────────────┘
```

## Agents

| Agent        | Questions About                     | Output            |
| ------------ | ----------------------------------- | ----------------- |
| `discovery`  | Requirements, users, constraints    | `*.discovery.md`  |
| `architect`  | Design choices, patterns, tradeoffs | `*.architect.md`  |
| `simplifier` | Necessity, complexity, removals     | `*.simplifier.md` |

## The Skill

All agents share one skill:

```
.claude/skills/socratic/SKILL.md
```

It defines how to question:

- Batch questions (2-3 per round)
- Adapt based on answers
- Probe vague responses
- Confirm before acting
- Let user decide when done

## Setup

```bash
git clone https://github.com/yourname/socratic.git
ln -s /path/to/socratic/.claude ~/.claude
```

## Structure

```
.claude/
├── CLAUDE.md                  # Workflow
├── agents/
│   ├── discovery.md           # Requirements gathering
│   ├── architect.md           # Planning
│   └── simplifier.md          # Complexity removal
└── skills/
    └── socratic/
        └── SKILL.md           # Questioning protocol
```

## Output

Agents write to `.claude/socratic/` in your project:

```
your-project/.claude/socratic/
├── auth.discovery.md
├── auth.architect.md
└── auth.simplifier.md
```

## Philosophy

> "I know that I know nothing." - Socrates

The best code comes from admitting you don't fully understand the problem yet. These agents embody that humility - they question relentlessly until clarity emerges.

No rushing to solutions. No assuming requirements. No unexamined complexity.

Just questions, until the right answer becomes obvious.

## License

MIT

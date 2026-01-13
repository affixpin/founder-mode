# Socratic

A Claude Code plugin that implements the Socratic method for software development.

> **Don't assume. Question. Then act.**

## Installation

```bash
/plugin install affixpin/socratic
```

## The Idea

Socrates believed that **wisdom begins with questioning**. He never claimed to have answers - instead, he asked probing questions until the truth emerged.

This plugin applies the same principle to coding. Every agent questions before acting. No assumptions survive unexamined.

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
         │  Architect  │  "What approach? What tradeoffs?"
         └──────┬──────┘
                │
                ▼
         ┌─────────────┐
         │ Simplifier  │  "Is this needed? What can we remove?"
         └──────┬──────┘
                │
                ▼
         ┌─────────────┐
         │  Implement  │
         └─────────────┘
```

## What You Get

### Agents

| Agent        | Purpose                                 | Output            |
| ------------ | --------------------------------------- | ----------------- |
| `discovery`  | Gather requirements through questioning | `*.discovery.md`  |
| `architect`  | Design solutions with tradeoff analysis | `*.architect.md`  |
| `simplifier` | Remove unnecessary complexity           | `*.simplifier.md` |

### Skills

- **socratic** - A questioning protocol (2-3 questions per round, adapt based on answers, confirm before acting)

### Commands

- `/socratic:socratic` - Start the full Socratic workflow

## Usage

### Start the full workflow

```
/socratic:socratic

> What are we building?
"I want to add user authentication"
```

### Use agents directly

```
"Use the discovery agent to gather requirements for the auth feature"
"Use the architect agent to plan the auth system"
"Use the simplifier to review auth-system.architect.md"
```

### Skip questioning for quick tasks

```
"[q] Fix the typo in the README"
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

The best code comes from admitting you don't fully understand the problem yet. These agents question relentlessly until clarity emerges.

No rushing to solutions. No assuming requirements. No unexamined complexity.

## License

MIT

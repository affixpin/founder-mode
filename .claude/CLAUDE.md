# Founder Mode Development Workflow

## Scope Tags

Users control the rigor level with scope tags. **Default is `[mvp]` when no tag is specified.**

| Tag | Name | Planning | Use When |
|-----|------|----------|----------|
| `[q]` | Quick | Skip entirely | Typos, one-liners, obvious fixes |
| `[mvp]` | MVP | Lean planning | Most features, default behavior |
| `[prod]` | Production | Full rigor | Core systems, complex refactors |
| `[critical]` | Critical | Max scrutiny | Security, payments, data integrity |

**Examples:**
- `[q] fix the typo in header` → Just fix it, no planning
- `add dark mode` → MVP (default), lean requirements + plan
- `[prod] refactor auth system` → Thorough requirements, detailed plan
- `[critical] implement payment processing` → Maximum rigor, detailed everything

## The Planning Flow

```
         ┌──────────────┐
         │   Request    │
         └──────┬───────┘
                │
          ┌─────┴─────┐
          │  Scope?   │
          └─────┬─────┘
           [q]  │  [mvp]/[prod]/[critical]
          ┌─────┘     │
          │           ▼
          │    ┌──────────────┐
          │    │   Socrat     │
          │    │   Gathers    │
          │    │ Requirements │
          │    └──────┬───────┘
          │           │
          │           ▼
          │    ┌──────────────┐
          │    │  Architect   │
          │    │   Plans      │
          │    └──────┬───────┘
          │           │
          │           ▼
          │    ┌──────────────┐
          │    │  Simplifier  │
          │    │   Removes    │
          │    │  Complexity  │
          │    └──────┬───────┘
          │           │
          └────────┬──┘
                   ▼
            ┌──────────────┐
            │  Implement   │
            │    Code      │
            └──────────────┘
```

### For `[q]` (Quick) Requests
Skip planning entirely. Just implement the change directly.

### For `[mvp]`, `[prod]`, `[critical]` Requests

**Step 1:** Identify scope (default: `[mvp]`)

**Step 2:** Socrat gathers requirements via Socratic questioning → `*-requirements.md`

**Step 3:** Solution Architect creates plan from requirements → `*-plan.md`

**Step 4:** Simplifier reviews plan, asks user about removals, strips complexity → `*-simplified.md`

**Step 5:** Implement from the simplified plan

## Implementation Phase

After simplification:

1. Read the simplified plan (`*-simplified.md`)
2. Follow the plan step-by-step
3. Implement code changes as specified
4. Do not deviate from the plan without re-planning

## Agents

| Agent | Purpose | Output |
|-------|---------|--------|
| `socrat` | Gathers requirements via Socratic questioning | `*-requirements.md` files |
| `solution-architect` | Creates implementation plans from requirements | `*-plan.md` files |
| `simplifier` | Removes unnecessary complexity from plans | `*-simplified.md` files |

## File Storage

All agent-generated plans go to: `.claude/founder-mode-plans/`

```
project/
└── .claude/
    └── founder-mode-plans/
        ├── feature-name-requirements.md
        ├── feature-name-plan.md
        └── feature-name-simplified.md
```

These files are **temporary working documents**—gitignored, not committed. Once implementation is complete, they can be deleted.

## Why This Workflow?

- Forces thorough thinking before coding
- Catches architectural issues early
- Actively removes complexity (simplifier asks "do you really need this?")
- Creates documentation as a byproduct
- Reduces wasted effort from poor planning and over-engineering

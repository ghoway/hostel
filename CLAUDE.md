## Workflow Orchestration

### 1. Plan Mode Default

- Enter plan mode for ANY non-trivial task (3+ steps or architectural desicions)
- If something goes sideways, STOP and re-plan immediately
- Use plan mode for verivication steps, not just building
- Write detailed specs upfront to reduce ambiguity

### 2. Subagent Strategy

- Use subagents liberally to keep main context window clean
- Offload research, exploration, and parallel analysis to subagents
- For complex probles, throw more compute at it via subagents
- One task per subagents for focused execution

### 3. Self-Improvement Loop

- After ANY correction from the user: update docs/skills/\*.md with the pattern
- write rules for yourself that prevent the same mistake
- Ruthlessly iterate on these lessons until mistake rate drops
- Review lessons at session start for relevant project

### 4. Verification Before Done

- Never Mark a task complete without proving it works
- Diff behavior between main and your changes when relevant
- Ask yourself "Would a staff engineer approve this?"
- Run test, check logs, demonstrate correctness

### 5. Demand Elegance (Balanced)

- For non-trivial changes: pause and ask "is there a more elegant way?"
- If a fix feels hacky: "Knowing everything I know now, impelement the elegant solution"
- Skip this for simple, obvious fixes -- don't over-engineer
- Challange your own work before presenting it

### 6. Autonomous Bug Fixing

- When given a bug report: just fix it. Don't ask for hand-holding
- Point at logs, errors, failing tests -- then resolve them
- Zero context switching required from the user
- Go fix failing CI tests without bilng told how

### 7. Business Rules First

- Always review relevant docs/features/\*.md before implementation
- Never implement assumptions not defined in documentation
- Prioritize business rules consistency over implementation speed
- Ask for clarification when business logic is ambiguous

### 8. Avoid Hardcoded Business Logic

- Avoid hardcoded role names
- Avoid hardcoded booking statuses
- Avoid hardcoded room statuses
- Prefer configurable/domain-driven approaches
- Authorization should be permission-based whenever possible

### 9. Respect Existing Architecture

- Follow existing project structure and conventions
- Reuse existing patterns before introducing new abstractions
- Avoid creating duplicate architectural approaches
- Keep implementation consistent with established domain models

## Task Management

1. Plan First: Write plan to docs/tasks/todo.md with checkable items
2. Verify Plan: Check in before starting impelemtation
3. Track Progress: Mark items complete as you go
4. Explain Changes: High-level summary at each step
5. Document Results: Add review section to docs/tasks/todo.md
6. Capture Lessons: Update docs/tasks/lessons.md after corrections

## Core Principles

- Simplicity First: Make every changes as simple as possible. Impact minimal code
- No Laziness: Find root cause. No temporary fixes. Senior developer standards.
- Minimal Impact: Change should only touch what's necessary. Avoid introducing bugs.

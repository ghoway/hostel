# TODO — Next Session

---

# Current Project State

Project foundation & architecture documentation is now mostly complete.

Completed:

- SRS
- architecture docs
- feature docs
- database docs
- backend docs
- AI workflow docs
- README documentation index

The project now has a strong architectural foundation.

---

# IMPORTANT REMINDER

DO NOT start implementation yet.

Frontend architecture/conventions are NOT finalized yet.

Before coding:

- finalize frontend documentation
- define frontend conventions
- define frontend structure/patterns

Avoid premature frontend implementation.

---

# Next Priority

## Finalize Frontend Documentation

Create:

- docs/frontend/frontend-structure.md
- docs/frontend/state-management.md
- docs/frontend/form-strategy.md
- docs/frontend/ui-component-strategy.md
- docs/frontend/layout-strategy.md
- docs/frontend/table-page-patterns.md

---

# Frontend Topics To Decide

## State Management

Decide:

- local state
- composables
- shared props
- whether Pinia is actually necessary

Avoid overengineering.

---

## Form Strategy

Decide:

- Inertia useForm usage
- reusable form components
- validation display pattern

---

## Layout Strategy

Decide:

- GuestLayout
- DashboardLayout
- operational/admin layouts

---

## Table Pattern

Decide:

- reusable table approach
- filtering
- pagination
- bulk actions
- search UX

This will heavily affect admin pages later.

---

## UI Component Philosophy

Decide:

- modal strategy
- toast strategy
- shared components
- page composition approach

---

# AFTER Frontend Docs

Only then proceed to:

1. package installation
2. auth foundation
3. permission setup
4. migrations
5. enums
6. models
7. policies

---

# Personal Reminder

Do not rush implementation.

Current priority:

- architectural consistency
- maintainability
- clear conventions
- long-term scalability

The goal is:
build a clean PMS foundation,
not just "make features work".

---

# MVP Reminder

First operational MVP target:

login
→ room types
→ rooms
→ booking
→ payment
→ checkin
→ checkout

Everything else can evolve later.

---

# Session Notes

Important realization today:
Implementation should NOT start before:

- architecture
- conventions
- module boundaries
- frontend strategy

are clearly defined.

Maintain this workflow consistently moving forward.

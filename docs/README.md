# Documentation Index

---

# Purpose

This folder contains the complete architectural, business, and implementation documentation for the Hotel Reservation & Property Management System (PMS).

The documentation is designed to:

- maintain architectural consistency
- support AI-assisted development
- reduce implementation ambiguity
- preserve long-term maintainability

---

# Documentation Reading Order

Recommended reading order for developers and AI agents:

1. SRS.md
2. architecture/\*
3. features/\*
4. database/\*
5. backend/\*
6. frontend/\* (future)
7. testing/\* (future)

---

# Source of Truth Hierarchy

---

# SRS.md

High-level business and system requirements.

Contains:

- project scope
- business concepts
- operational requirements
- core system rules

---

# architecture/

Defines high-level architectural decisions.

Examples:

- booking lifecycle
- Inertia architecture
- permission architecture
- queue strategy

This folder defines:

- system philosophy
- operational architecture
- implementation direction

---

# features/

Defines feature-specific business rules and operational behavior.

Examples:

- booking behavior
- payment flow
- front office operations

This folder defines:

- feature expectations
- validations
- operational edge cases

---

# database/

Defines database architecture and persistence rules.

Examples:

- ERD
- schema conventions
- migration strategy
- availability engine
- pricing strategy

This folder defines:

- schema structure
- relational design
- persistence rules

---

# backend/

Defines Laravel implementation architecture.

Examples:

- service layer
- action pattern
- policies
- enums
- query scopes

This folder defines:

- implementation structure
- backend architectural patterns
- Laravel coding philosophy

---

# Documentation Principles

- Avoid duplicated source of truth
- Keep responsibilities separated
- Prefer explicit business rules
- Maintain architectural consistency

---

# AI Assistant Usage Notes

AI agents SHOULD:

- read this file first
- follow documented architecture
- avoid introducing undocumented patterns
- avoid conflicting architectural approaches

AI agents SHOULD NOT:

- hardcode role names
- bypass hotel scope
- introduce unnecessary SPA/API abstractions
- ignore queue recommendations

---

# Implementation Philosophy

- Keep architecture pragmatic
- Avoid overengineering
- Prefer maintainability
- Preserve historical integrity
- Prioritize operational simplicity

# Query Scope Strategy

---

# Purpose

Defines query organization and hotel scope enforcement.

---

# Core Principles

- Queries should enforce hotel scope
- Avoid duplicated filtering logic
- Prefer reusable query scopes

---

# Recommended Scope Examples

Examples:

- forHotel()
- active()
- available()
- paid()

---

# Multi-Hotel Scope

Operational queries SHOULD:

- filter by hotel_id
- enforce user scope

---

# Avoid

Avoid:

- unscoped queries
- duplicated where clauses
- cross-hotel data leakage

---

# Performance Recommendations

Prefer:

- indexed filters
- eager loading where appropriate
- paginated queries

Avoid:

- N+1 queries
- loading unnecessary relationships

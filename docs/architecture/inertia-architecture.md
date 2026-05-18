# Inertia Architecture

---

# Purpose

Defines how Laravel, Inertia.js, and Vue interact.

---

# Core Principles

- Laravel is the primary application framework
- Laravel handles routing
- Laravel handles authentication
- Laravel handles authorization
- Vue is used as the rendering layer
- Inertia.js bridges backend and frontend

---

# Routing

Routing is handled primarily by Laravel.

Avoid introducing Vue Router unless explicitly required.

Example:

- Laravel route -> Inertia::render() -> Vue page

---

# Frontend Pages

Vue pages live inside:

- resources/js/pages

Example:

- resources/js/pages/hotels/Index.vue

---

# Shared Data

Shared/global data should use:

- Inertia shared props

Avoid:

- unnecessary global state duplication

---

# API Usage

Do NOT build unnecessary REST APIs for standard page rendering.

Use Inertia page props whenever possible.

APIs should only be used for:

- async operations
- realtime search
- polling
- external integrations
- highly interactive UI cases

---

# Authentication

Authentication uses Laravel session authentication.

Avoid unnecessary token-based authentication for standard web usage.

---

# Development Principles

- Prefer server-driven architecture
- Keep frontend simple
- Avoid SPA overengineering
- Keep business logic in Laravel

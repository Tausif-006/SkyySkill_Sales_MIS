# SkyySkill MIS Dashboard

A production-grade Sales Management Information System (MIS) dashboard built using React, JavaScript, and Zustand.
This project simulates a real-world internal analytics system with role-based access, dynamic data filtering, and modular architecture.

---

## 🌐 Live Demo

👉 https://skyy-skill-sales-jomqd5gqz-sk-tausifs-projects.vercel.app

---

## Features

---

### Authentication

* Role-based login (Admin, Sales, Marketing, Finance)
* Protected routes
* Persistent auth state

<img src="https://github.com/user-attachments/assets/fc4f52f2-1270-43ab-905a-2d9bd8020922" />

---

### Dashboard

* Dynamic KPI cards (Revenue, Orders, ROAS, Collection %)
* Global date filters (This Month, Last Month, Custom)
* Interactive charts (Revenue trend, Order breakdown)

<img src="https://github.com/user-attachments/assets/ddddc242-ced3-451c-9546-2e4053efb6ea" />

---

### Orders Module

* Search, filters, and pagination
* Status-based filtering
* Order detail modal with item breakdown & payment history

<img src="https://github.com/user-attachments/assets/777c5b72-63e4-462c-9de0-3ff72fac7951" />

---

### Marketing ROAS Tracker

* Campaign & platform filters
* ROAS, CPC, CTR calculations
* Bar + line chart analytics

<img src="https://github.com/user-attachments/assets/3f466697-ce1d-41ed-bac4-b9e4a4042ab2" />

---

### Targets & Performance

* Individual & team targets
* Progress tracking with achievement %
* Monthly vs target comparison

<img src="https://github.com/user-attachments/assets/aba4955f-6cd1-44cf-94f1-43d1540f8cd0" />

---

### UX Enhancements

* Loading skeletons
* Toast notifications
* Empty states
* CSV export (mock)

<img src="https://github.com/user-attachments/assets/bd7a85b6-4b08-40f7-ad40-26aa79d75019" />


### State Management (Zustand – Centralized & Modular)

The application uses Zustand for global state management, structured into domain-specific stores inside the `store/` directory.

Instead of a single monolithic store, state is split by responsibility:

* Authentication state (user, role, session persistence)
* Global filters (date range shared across modules)
* Module-specific state (orders, marketing, targets)
* UI state (modals, selections, pagination)

This modular store design ensures:

* clear separation of concerns
* predictable state updates
* easy scalability as new modules are added

Zustand was chosen over Redux due to its minimal boilerplate and direct state mutation pattern, which simplifies managing complex UI interactions.

---

### 📁 Folder Structure (Hybrid: Feature + Layered Architecture)

The project follows a hybrid architecture combining reusable UI layers with feature-based modules:

* `components/`

  * `ui/` → low-level reusable primitives (buttons, modals, tables, etc.)
  * `layout/` → structural components (sidebar, navbar)
  * `shared/` → cross-module reusable components

* `pages/`

  * Route-level views (Dashboard, Orders, Marketing, etc.)

* `routes/`

  * Centralized route configuration and protected routing logic

* `store/`

  * Zustand stores grouped by domain

* `services/`

  * Handles data fetching and mock API simulation (TanStack Query integration)

* `data/`

  * Mock datasets representing backend responses

* `hooks/`

  * Custom hooks for reusable logic (filters, derived data, etc.)

* `utils/` & `lib/`

  * Helper functions and core utilities

This structure was chosen to:

* separate UI, logic, and data layers cleanly
* support independent scaling of features
* improve maintainability and readability

---

### Global Filter Synchronization

A centralized filter system is implemented using Zustand.

The global date filter is shared across:

* Dashboard
* Orders module
* Marketing analytics

When the filter updates:

* all dependent components re-render with filtered data
* charts and tables remain consistent across modules

This avoids fragmented state and ensures a unified MIS experience.

---

### Routing & Role-Based Access

Routing is handled via React Router v6 with a dedicated `routes/` layer.

* Protected routes restrict access based on authentication state
* Role-based rendering controls module visibility in the sidebar
* Navigation components dynamically adapt to user roles

This ensures:

* secure access control (frontend-level)
* cleaner UX with role-specific dashboards

---

### Services Layer & API Simulation

The `services/` layer abstracts data access and simulates API calls using TanStack Query.

* Introduces loading states and caching
* Mimics real-world async behavior
* Decouples UI from data source

This design allows easy backend integration in future without major refactoring.

---

### Component Design Strategy

Reusable UI components are built inside `components/ui/` and used across modules:

* Table (config-driven)
* Modal system
* KPI cards
* Status badges

This promotes:

* consistency in UI
* faster development of new modules
* reduced duplication

---

### Overall Design Philosophy

The focus was to build a system-oriented frontend rather than a static dashboard.

Key priorities:

* centralized state management
* data-driven UI rendering
* cross-module consistency
* scalable and maintainable architecture


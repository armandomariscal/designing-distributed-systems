# Requirements: Sansar TCG

## Context

Sansar TCG is a Trading Card Game designed as a high-quality technical portfolio. Instead of magic or monsters, players use software engineering concepts. Cards belong to distinct **Engineering Domains** (like Quality, Frontend, or DevOps) and their strength scales based on **Seniority Metrics** (Junior, Mid, Senior, Principal).

## Functional Requirements (FR)

### Core Card Mechanics
- **FR-01: Domain Categories:** The system must support 7 core engineering domains, each with a unique visual color and mechanical purpose (e.g., Quality uses Purple to protect Uptime; DevOps uses Red to lower Energy costs).
- **FR-02: Seniority Tiers:** Cards must scale performance based on four seniority levels: Junior (cheap, fast), Mid (balanced), Senior (special traits), and Principal (expensive, powerful).
- **FR-03: System Attributes:** Every card must have three primary stats tracked at runtime: Output (damage/delivery), Uptime (resilience/health), and Energy (deployment cost).

### Data & Environment
- **FR-04: Idempotent Seeding:** The system must provide an endpoint (`/api/seed`) that safely sets up the database layout and inserts the default game cards without creating duplicate entries.
- **FR-05: Dynamic Rendering:** The application dashboard must render real-time database state on every request to keep game variables synchronized.

## Non-Functional Requirements (NFR)

- **NFR-01: Framework Independence:** Core logic, formulas, and types inside `src/core/` must not import or depend on Next.js or React libraries.
- **NFR-02: Strict Typing:** The entire project must use TypeScript Strict Mode to catch errors like incorrect energy math or missing card statistics at compile time.
- **NFR-03: Multi-Database Support:** The database layer must change automatically between SQLite and PostgreSQL based on the `DATABASE_URL` configuration variable without changing UI components.
- **NFR-04: Consistent State Presentation:** The user interface must use server-driven rendering parameters to fully prevent hydration mismatches between server HTML and client JavaScript.
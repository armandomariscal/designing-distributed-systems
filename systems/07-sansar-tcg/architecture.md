# Architecture Overview: Sansar TCG

## Architectural Pattern: Clean Architecture

Sansar TCG uses **Clean Architecture** rules. This means the core game logic is completely separated from the web framework (Next.js) and the databases (SQLite and PostgreSQL). 

If we decide to change Next.js to another tool or replace the database in the future, the core game rules will not change. The system is split into clear layers where inner layers do not know anything about outer layers.

```
+-------------------------------------------------------+
| Presentation Layer (Next.js App / React Components)   |
+-------------------------------------------------------+
                           | (Uses)
                           v
+-------------------------------------------------------+
| Infrastructure Layer (SQLite / Postgres Repositories) |
+-------------------------------------------------------+
                           | (Implements)
                           v
+-------------------------------------------------------+
| Core Layer (Enterprise Business Rules / Interfaces)   |
+-------------------------------------------------------+
```

## System Components

- **Core Layer (`src/core/`):** This is the source of truth. It contains only pure TypeScript code. It defines the card metrics (`types.ts`) like Output, Uptime, and Energy. It also holds the repository definitions (`repository.ts`). It does not import anything from React, Next.js, or database drivers.
  
- **Infrastructure Layer (`src/infrastructure/`):** This layer handles the actual data details. It connects to the SQLite file (`sqlite-repository.ts`) using the LibSQL client, or to PostgreSQL (`postgres-repository.ts`). It contains a **Repository Factory** (`repository-factory.ts`) that reads the `.env` file and decides which database to start.

- **Presentation & Framework Layer (`src/app/` & `src/components/`):**
  This is where Next.js lives. 
  - **API Routes (`src/app/api/`):** Act as controllers. They receive network requests, call the repository factory, and return JSON data.
  - **Server Components (`src/app/page.tsx`):** Fetch data directly from the repository at the server level using **Dynamic SSR** to avoid hydration errors.
  - **Client Components (`src/components/ui-game/`):** Handle interactive game features like playing a card, spending Energy, and tracking Uptime.

## Trade-offs

- **Clean Architecture vs. Direct Next.js Setup:** Writing interfaces and factories takes more time at the beginning. However, it gives us full control. We can test game mechanics without running a database, and changing data tools is completely safe.
  
- **Dynamic SSR vs. Static Pages:** The game board uses Dynamic SSR (`force-dynamic`). This means every page load fetches fresh data from the database. It prevents errors where the server view and client view do not match. The trade-off is a slightly slower initial response compared to a fully cached static website.
# Data Flow & Communication: Sansar TCG

## Communication Channels

- **Server-Side Data Load (Direct Read):** When a user opens the game page, the Next.js Server Component asks the Repository Factory for a data instance and reads directly from the database. No internal HTTP API call is needed during this step.
- **Client Actions (HTTP REST):** When interactive steps occur (like adding initial data via seeding), the browser sends an HTTP GET request to the API routes.
- **Database Decoupling:** The presentation layer never writes SQL queries. It only interacts with the methods exposed by the repository contract.

## Event Flow Example: Initializing and Seeding the Card Catalog

```
[ Developer / Browser ] 
          │
          ▼ (HTTP GET /api/seed)
   [ Seed Route Handler ]
          │
          ▼ (Calls)
   [ Repository Factory ] ---> (Reads process.env.DATABASE_URL) ---> [ Instantiates SQLite repo ]
          │
          ▼ (Loads)
   [ mock-cards.ts Dataset ]
          │
          ▼ (Executes Bulk Insert)
     [ local.db ]
```

1. **Trigger:** The developer or script sends an HTTP GET request to the `/api/seed` path.
2. **Factory Selection:** The seed route handler calls the `RepositoryFactory`. The factory reads the `DATABASE_URL` environment variable and instantiates the correct repository (e.g., SQLite via LibSQL).
3. **Data Mapping:** The repository reads the balanced card catalog from the `mock-cards.ts` file inside the features directory.
4. **Persistence:** The repository opens a transaction and runs bulk inserts to save all cards into the `local.db` database file safely.
5. **UI Update:** The next time a user visits the root web domain, the Server Component reads these new cards from the database and renders them on the screen.
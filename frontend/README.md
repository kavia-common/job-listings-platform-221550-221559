# Ocean Jobs (Svelte)

A simple job board UI implementing the Ocean Professional theme.

- Primary: `#2563EB` (blue)
- Secondary/Success: `#F59E0B` (amber)
- Error: `#EF4444`
- Background: `#f9fafb`, Surface: `#ffffff`, Text: `#111827`

Features:
- Header with search/filter controls
- Job list grid with cards
- Details modal with Apply CTA
- Application form stub logging to console

Environment:
- Uses import.meta.env.VITE_API_BASE (fallback to VITE_BACKEND_URL) when available, otherwise mock data
- Runs on port 3000 via vite.config.ts

Scripts:
- `npm run dev` (with CORS)
- `npm run build`
- `npm run preview`

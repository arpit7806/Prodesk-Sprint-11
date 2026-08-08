---

## Sprint 11 — Testing (Jest + React Testing Library)
---

**Sprint 11 | Prodesk IT Internship | QA Automation**

Unit and component tests added on top of the build above. No application code changed, so the live deployment stays exactly as it was before this sprint — test files never ship in the production build.
---
### Why Sprint 9's codebase
The brief said tests had to live "within your Next.js application" — it didn't say which one, and by this point there were a few Next.js-capable candidates sitting in past sprint work. Sprint 9 was the clear pick for a few concrete reasons: it's confirmed Next.js App Router (not every past project is — some stayed React + Vite), it already does a real async fetch against TMDB via a server-side Route Handler (which Phase 3 needed anyway regardless of which app got picked), and it has genuine components with real props and logic instead of anything built to be a demo. Just as importantly, this repo is part of the `prodesk-sprint-N` series being evaluated sprint over sprint — testing a project outside that chain would've meant explaining why the deliverable suddenly jumped elsewhere, for no real benefit over testing the app that was already right there.
---

### What's covered

- **`Navbar.jsx`** (2 tests) — mounts cleanly, renders as a semantic `banner` landmark.
- **`MovieCard.jsx`** (6 tests) — prop-driven rendering of title/year/rating, poster-vs-fallback branching, and a favorite-toggle click that actually flips the DOM via a controlled-component test wrapper.
- **`SearchBar.jsx`** (4 tests) — typed input updates the DOM live, clear button appears/disappears correctly. `next/navigation` is mocked, since `useRouter`/`useSearchParams` have no App Router context to read from outside a real Next.js runtime.
- **`lib/tmdb.js`** (4 tests) — URL/param construction plus both the success and failure response paths, with `global.fetch` mocked so no real network call is ever made.

**16 tests across 4 suites, 95%+ statement coverage** on the files above.

### Running the tests


npm test                 # run once
<img width="1323" height="496" alt="WhatsApp Image 2026-08-08 at 9 22 32 AM" src="https://github.com/user-attachments/assets/2a27e690-51dc-489f-9cce-71a740f747d8" />

npm test -- --coverage   # run with a coverage report
<img width="1324" height="435" alt="image" src="https://github.com/user-attachments/assets/cc1dd7aa-1e71-4311-b1e6-4cca2bf50d14" />

npm run test:watch       # watch mode
<img width="1306" height="675" alt="image" src="https://github.com/user-attachments/assets/ff0804cf-bc01-481b-a70d-db9746f3d7df" />

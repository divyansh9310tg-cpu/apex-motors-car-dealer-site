# Making the admin REAL (shared across devices)

## The limitation today (BUILD 6.2)
The admin dashboard (#/admin) is fully built: owner + developer logins, interested customers (with the cars they viewed), visitor/view stats, photo upload, stock control. BUT all data is stored in the browser (localStorage) of whoever creates it. So:
- A customer who sends a test-drive request from THEIR phone saves it in THEIR phone only. The owner opening /admin on his own phone/laptop will not see it.
- Cars/photos the owner uploads are visible only on the owner's browser, not to customers.
- PINs live in the page source, so they are not real security.

## Fix: a free shared backend (recommended: Supabase, free tier)
What the user must do (account creation can't be done by Claude):
1. Create a free project at supabase.com (login with Google/GitHub).
2. In the project: copy **Project URL** and **anon public key** (Settings > API).
3. Share URL + anon key with Claude (the anon key is meant to be public; never share the service_role key).

What Claude will then do:
- Tables: `cars` (stock + photo URLs), `leads`, `events` (views/visits), with Row Level Security:
  - everyone (anon) can INSERT into `leads` and `events`, and SELECT from `cars`;
  - only authenticated admins (owner + developer, Supabase Auth email login) can SELECT leads/events and INSERT/UPDATE/DELETE cars.
- Storage bucket `car-photos` (public read, admin write) so the owner's uploads are stored online, not in the browser.
- Replace PIN login with Supabase email+password login for owner and developer (real security).
- Site reads stock from `cars`, sends leads/events to Supabase; admin dashboard reads them.
- Optional: email/WhatsApp alert to the owner on each new lead; a developer-only "subscription active" switch (status flag) the developer controls, matching the plan to pause hosting if payments stop.

Alternatives if no Supabase: Firebase (Firestore+Auth+Storage), or Google Sheets + Apps Script for leads only (simple, but weaker).

## Business notes (from the chat)
Plan: sell the site to the dealer, host it ourselves, monthly payment; if unpaid, hosting is paused. GitHub Pages public repo is fine for the prototype; for real clients consider Netlify/Vercel/Cloudflare Pages under the developer's account, a custom domain, and a private repo.

## Happy Cars (/happy-cars/) - same plan
The Happy Cars page has the same limit: cars, leads, analytics and settings live in each browser's localStorage, and the owner password (default 1234) is checked in the browser. Needed for a real launch:
- **Auth:** Supabase Auth email login for the owner (replaces the in-page password).
- **Tables:** `cars` (public read, owner write), `site_config` (public read, owner write), `leads` (anon insert only, owner read/update), `events` (anon insert only, owner read), `likes` (anon insert, public counts).
- **Storage:** `car-photos` bucket (public read, owner write) instead of photos stored inline in the browser.
- **Code:** the page already routes every save through one `Store` object (saveCar, deleteCar, saveConfig, saveAll, savePhoto) and every lead through `saveLead()` and every event through `track()`, so switching to Supabase only means rewriting those functions.
- Until then, set a Web3Forms access key in the owner panel so each enquiry is also emailed to the owner.

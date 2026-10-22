# Happy Cars website (light redesign, build 4)

Live: https://divyansh9310tg-cpu.github.io/apex-motors-car-dealer-site/happy-cars/
Owner panel: add `#owner` to the link (demo password `1234`, change it in Settings).

## What it is
One static page (`index.html`: HTML + CSS + vanilla JS), the 3D model in `models/` + `draco/`,
and the car photos in `../assets/cars` (Wikimedia Commons, credited in the footer).
three.js r128 loads from cdnjs/jsdelivr only after the page is ready; if WebGL, the model or the
network fails, the hero keeps the showroom photo. Reduced-motion users get no auto-rotation or sparkle.

## Design system (tokens at the top of the `<style>`)
Background #F5F5F7 · cards #FFFFFF · secondary #E8E8ED · text #1D1D1F / #6E6E73 · lines #D2D2D7 ·
action blue #0066CC (hover #004F9A) · success #248A3D · error #D70015. Fonts: Manrope (headings), Inter (body).
Blue is only used for primary actions, active links and interactive states. One dark band (premium collection) for photography.

## Features
Smart search ("automatic SUV under 15 lakh"), filters + sort, favourites, compare (up to 3), car details with
condition score, EMI planner with yearly schedule, test-drive booking, price alerts, enquiry form, sell/exchange
form, offers, reviews, WhatsApp/call buttons, deep links (`#car-<id>`), JSON-LD (AutoDealer + Car offers).
Owner panel: overview analytics, leads CRM (status, call/WhatsApp/email, CSV export), stock (price/status/feature,
price-drop alerts to buyers), add/edit cars with photos, offers, reviews, contact & social links, 360° photo set,
password, backup/restore.

## IMPORTANT limits on GitHub Pages (no backend)
- Cars, settings, leads and analytics are stored in the browser where they were created (localStorage).
  A buyer's lead reaches the owner only by email if a Web3Forms key is set (Owner panel > Contact & social).
- The password check runs in the browser: it keeps casual visitors out, it is NOT real security.
- For a real shop: Supabase (or Firebase) for the cars table, leads, events, photo storage and owner sign-in.
  See ../BACKEND-SETUP.md ("Happy Cars" section).

## Deploy
Edit `index.html`, commit, push to `main`; GitHub Pages updates in about a minute. Share links with `?v=<n>` to skip caches.

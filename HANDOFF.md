# HANDOFF - Happy Motors (used-car dealer website prototype)
Saved 2026-10-05 (night). Resume from here tomorrow.

## What this is
Single-file site `index.html` (vanilla JS, hash router) + `assets/cars/*.jpg` + `version.json`. Prototype for a second-hand car dealer. Feedback comes from Divyansh Pandey on WhatsApp.

## Live / repo
- Live: https://divyansh9310tg-cpu.github.io/apex-motors-car-dealer-site/ (shared as `?v=6`)
- Repo (public): https://github.com/divyansh9310tg-cpu/apex-motors-car-dealer-site , branch main
- Pages: Settings > Pages > main / root (already enabled)
- Deploy: edit index.html -> bump `BUILD` (auto-update script near top) AND `version.json` (now 6.1) -> `git add -A; git commit; git push` -> wait ~1 min. Old/cached copies auto-reload.
- Local test: `python -m http.server 8765` in this folder, open http://localhost:8765/ (the Chrome file:// URL is blocked).
- Backups of earlier versions are in the Claude scratchpad (index_v43_backup.html, index_v50_backup.html) and in git history.

## Current design (BUILD 6.1)
Brand: Happy Motors (CONFIG.name). Palette: Ivory #F5F3EE, Obsidian #0D0F10, Graphite #25282A, Champagne Gold #C8A96B, White. Font Manrope.
Sections (home): hero (3 cinematic photos, slow zoom) > quick search panel > inventory with category chips > Why buy from us (6 trust cards) > Premium Collection carousel (obsidian) > Ready to sell (image + parallax) > How it works timeline > stats counters > testimonials > About > Contact (form, map placeholder) > final CTA > footer.
Other pages: #/cars (filters, ?premium=1, ?luxury=1, ?make=&model=&year=&km=&max=), #/car/<id> (details: facts, inspection, features, specs, documents, finance, reserve/cart), #/checkout (demo), #/sell, #/saved, #/admin (PIN in CONFIG.adminPin, add cars with photos, mark sold or hide, leads, export).
Mobile: burger menu, sticky "Enquire Now" bar, collapsible extra filters, no horizontal overflow (checked at 390px).

## Data / config
- `CONFIG` block at top of the script: name (Happy Motors), phone/WhatsApp/email/address/hours placeholders, currency INR (en-IN), tax 5%, delivery 5000, deposit 10000, APR 10.5, warranty text, adminPin, soldMode.
- 16 real-model cars in `SEED` (Maruti Suzuki Swift, Hyundai i20/Creta, Honda City, Tata Nexon, Kia Seltos, Toyota Innova Crysta/Fortuner/Hilux, Mahindra Thar/XUV700, MG ZS EV, VW Virtus, Mercedes C-Class, BMW 3 Series, Audi A5). `SEEDV` resets stored stock when seed changes.
- Photos: Wikimedia Commons (CC BY / CC BY-SA), credits in `CREDITS`/`XCRED` and shown on each car page + footer. credits.json in assets/cars.
- Stock/leads/cart are stored in the visitor's browser (localStorage) only - NOT shared between devices.

## Placeholders to replace before selling for real
phone, WhatsApp number, email, address/city, hours, Google map, social links, about/hero photos (not truly cinematic or the dealer's own), testimonials, stats, registration codes, inspection report, features lists, brand/logo. Real stock needs a backend (e.g. Supabase/Firebase) + payment gateway (Razorpay/Stripe); checkout is demo only.

## Pending / next ideas
1. Read Divyansh's newest WhatsApp messages (after ~10:52 pm on 2026-10-05) and implement requests; send him the fresh link after each round (Hinglish, kind).
2. Possible improvements: more photos per car (gallery), real cinematic hero photos, backend for shared stock, Indian GST label, Hindi/English toggle, SEO/schema, performance pass.
3. Ask the user: currency/market confirmation (INR assumed), real dealer details, whether to rename the repo/URL (changing it breaks shared links).

## Working rules (also saved in Claude memory)
Play a done-sound at the end (3 beeps + "Work is done"). Phone AND desktop always. Animations always on. Update the same live link. WhatsApp: search name -> find row ref -> click ref -> confirm header -> then type. Skills updated: ecommerce-web-master, storefront-theming, responsive-storefront, immersive-3d-web (in Desktop\3D Immersive Web Toolkit and ~/.claude/skills).

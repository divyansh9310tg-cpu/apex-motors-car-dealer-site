APEX MOTORS - used-car dealer website (single file: index.html)

OPEN: double-click index.html (works offline), or upload the file to any web host.

FOR THE DEALER
- Footer > "Dealer login" (or #/admin). Demo PIN: 1234 (change CONFIG.adminPin).
- Add a car: fill the form + choose up to 4 photos (phone camera or computer). Photos are resized automatically.
- Each stock row: edit price, add/replace photos, "Mark sold", Delete.
- When a car is sold: choose "Show Sold badge" OR "Remove from website" (dropdown in Admin).
  A car bought online through checkout is marked sold automatically.
- Leads (test drives, enquiries, sell/trade-in requests) are listed in Admin.
- "Export stock JSON" downloads a backup.

FOR YOU (before selling)
1. Edit the CONFIG block at the top of the <script>: name, phone, WhatsApp, email, address, hours, currency, tax, delivery fee, deposit, warranty text, PIN.
2. Replace the demo cars (SEED array) with real stock, or let the dealer add cars in Admin.
3. IMPORTANT LIMITS of this version: stock, photos and leads are saved in the browser of whoever uses it
   (localStorage). Customers on other devices will NOT see cars the dealer adds. To go live for real customers
   you need a backend (e.g. Supabase/Firebase, or Shopify/WooCommerce) + a real payment gateway (Stripe/Razorpay).
   Checkout here is a demo: no payment is taken and no emails are sent.
4. Rename the demo brands (Voltaro, Kestrel...) - they are fictional placeholders.

DEPLOYING UPDATES
- After editing index.html, bump BUILD in the auto-update <script> near the top AND version.json (same number), then commit and push.
- Already-open or cached copies reload themselves to the newest version. GitHub Pages caches pages up to 10 minutes, so very old copies may need a hard refresh (Ctrl+Shift+R) once.

SAMPLE DATA TO REPLACE: registration state codes, inspection report items, features lists, testimonials, location (CONFIG.city) and stats are placeholders for the prototype.

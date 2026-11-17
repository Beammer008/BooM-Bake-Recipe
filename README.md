# Bakery Studio v1

A bilingual (Thai/English), THB-based bakery recipe and costing PWA prototype designed for iPhone.

## Included in v1
- Recipe book: create, edit, delete recipes; add ingredient quantities, yield and method notes.
- Ingredient library: save purchase price, pack quantity and unit (g, ml, pcs); calculates cost per unit.
- Cost calculator: scales a recipe to a batch yield, shows ingredient costs, cost per piece and suggested price for a target gross margin.
- Products: link a recipe, add extra cost per piece, set selling price and view estimated gross margin.
- Backup: export/import a JSON backup.
- Local-first storage using IndexedDB; no account or cloud service.

## Important data note
Data is stored in the browser on this device. It is not automatically synced to iCloud or another device. Export a backup regularly. Clearing Safari website data may erase records. Keep exported JSON backups in Files/iCloud Drive or another safe location.

## Run and install on iPhone
A Progressive Web App requires HTTPS (or localhost) for service-worker/offline installation.

1. Upload the contents of this folder to a static HTTPS host (for example, a private GitHub Pages repository or another static web host).
2. Open the HTTPS site in Safari on your iPhone.
3. Tap Share → Add to Home Screen → Add.
4. Launch Bakery Studio from the new Home Screen icon.
5. Open Settings & Backup and export a backup after entering important recipes.

The app can be previewed on a desktop browser by serving this folder from a local web server. Opening `index.html` directly from the Files app may not enable offline/PWA features.

## Costing logic
- Ingredient unit cost = purchase price / pack quantity.
- Recipe batch ingredient cost = sum(unit cost × recipe amount).
- Cost per piece = batch ingredient cost / recipe yield.
- Suggested selling price = cost per piece / (1 − target margin).
- Product estimated cost = linked recipe cost per piece + extra cost per unit.

The calculator currently models ingredient cost and per-unit extra costs. It does not yet automatically allocate labor, electricity, rent, waste, tax or payment fees. Add those in a future version or include them as extra product cost.

## Technical
- Plain HTML/CSS/JavaScript
- IndexedDB local database
- Service worker cache for offline app shell
- No external backend

# WCKDTHGHTS — DTC Order Capture Prototype

A mobile-first, single-link, four-step direct-to-consumer order request experience built as a **concept demo** for Wckdthghts, Inc.

## Demo features

**Customer experience** (`/`)
1. **Welcome:** branded walkthrough with accurate miniature illustrations of the catalog, cart, details, and confirmation screens; clearly states no payment is collected.
2. **Catalog & cart:** product photos, SKU, prices, sizes, colors, adjustable quantities, live subtotal.
3. **Customer details:** name, email, phone, pickup/domestic/international delivery, conditional address, shipping charges of $0/$10/$20, final total.
4. **Thank you:** sequential reference number, explanation that staff will reach out to arrange payment. The company website link is a **placeholder pending approval**.

**Staff demonstration** (`/?view=staff`)
- One chronological master order list with sequential order IDs (`WT-0001`, etc.).
- Line-item SKUs, variants, quantities, prices, contact information, fulfillment and totals.
- Manual payment method dropdown (Zelle / Cash App / Apple Pay) and payment captured True/False dropdown, default False.
- Confirmed revenue and production quantities count **only** True orders. Switching back to False immediately reverses the totals.
- Master order CSV export.
- No-code product editor: add/remove products, change image URLs, SKUs, prices, categories, sizes, colors and availability. Changes appear in the customer catalog in the same browser.

## Important demo limitations

This is **not a production order system**. All orders and products are saved in the current browser's `localStorage`; they are **not shared between customers, devices, or staff**. There is **no real authentication**, secure backend, central spreadsheet, outbound notification, or payment collection. Sample orders are fictional. Do not use the demo to collect real customer information. Product photography is illustrative placeholder imagery, not approved client merchandise. The company website URL is not yet approved, so the confirmation page labels its link as pending.

For a production handoff, connect a shared database or Google Sheet (via server-side integration), add staff-only authentication and permissions, protect customer data, implement validation and abuse prevention, configure the approved company URL, replace sample images with client-provided products, and supply an operator guide. Customer-facing ordering should remain public and account-free.

## Run locally

```bash
npm install
npm run dev
```

Visit http://localhost:3000 for the customer journey and http://localhost:3000/?view=staff for the staff demo.

## Production build

```bash
npm run build
npm run start
```

## Deploy to Vercel

Push this repository to GitHub and import it into Vercel. Framework preset: Next.js. No environment variables are needed for the localStorage prototype.

## Suggested production architecture

Next.js on Vercel + Supabase Postgres for a central order and product database + Supabase Auth for **staff only** (customers remain anonymous). Alternatively, a server-side Google Sheets integration can provide the single master sheet; do not expose spreadsheet credentials to browsers. Hosting, storage, and usage costs must be disclosed to and approved by the client before activation.

## Client scope notes

The agreement specifies four separate customer pages/steps, single-link access without customer registration, manual payment verification, editable products without coding, and a 24-hour target / 10-hour cap / $500 maximum authorization subject to negotiation. This prototype is an illustrative demonstration, not acceptance-ready delivery.

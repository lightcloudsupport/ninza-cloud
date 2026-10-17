# Ninza Domains

A single-file domain storefront. Visitors search for a domain, add available names and plans to a cart, and check out through a Discord ticket where staff process the order.

Discord: https://discord.gg/ninzacloud

## Features

- Login / Register popup on first visit, with a "Continue as guest" option
- Domain search showing Available or Not available for each extension
- Price cards for 14 extensions (.com, .net, .org, .xyz, .fun, .store, .online, .site, .info, .co, .me, .cc, .io, .ai)
- Three plan cards that can be added to the cart
- Cart drawer with a running total
- Checkout copies the order summary and opens the Discord invite for ticket creation
- Scroll effects: progress bar, parallax grid, reveal on scroll, animated counters, scrolling extension strip, 3D card tilt
- Dark and light themes that follow the visitor's system setting
- Mobile friendly

## Files

```
ninza-domains.html   the whole site (HTML, CSS and JS in one file)
README.md            this file
```

## Run it

Open `ninza-domains.html` in a browser. No build step and no dependencies. Fonts load from Google Fonts and fall back to system fonts if blocked.

## Deploy

**Vercel**
1. Rename `ninza-domains.html` to `index.html`.
2. Put it in a GitHub repo, or drag the folder into the Vercel dashboard.
3. Add your custom domain under Project → Settings → Domains.

**Any static host** (GitHub Pages, Netlify, Cloudflare Pages): upload `index.html`.

## Edit the content

Everything is at the top of the `<script>` block.

| What | Variable |
| --- | --- |
| Extensions and prices (USD) | `T` |
| Plans (name, description, price) | `P` |
| Names treated as taken | `COMMON` |
| Discord invite link | `INV` (also the two links in the HTML) |
| Site name | search for `ninza` in the file |

To add an extension, add a pair such as `['dev', 12.00]` to `T`.

## Important limitations

1. **Domain availability is simulated.** The page cannot query real registries, so a name's status is a stable pseudo-random result. Staff must confirm availability when the ticket is opened. For real checks, connect a registrar or reseller API behind a small backend (for example a serverless function) and call it from the `search()` function.
2. **Prices are a snapshot.** They were taken as first-year USD prices from a third-party price tracker (July 2026), not from NicNames' live price list, and renewal prices can be higher. The `.site` price is an estimate. Verify every price before going live.
3. **Login is a front-end demo.** Accounts and the cart are saved in the visitor's own browser (localStorage). Passwords are stored unencrypted on the visitor's device and nothing is sent to a server. Do not treat this as real authentication. Use a backend and an auth provider (Supabase, Firebase, etc.) for production.
4. **Plans are placeholders.** Change the names and prices in `P` to your real offers.
5. **Payment is handled manually** in the Discord ticket. The site does not process payments.

## Ticket flow

1. The visitor searches and adds items to the cart.
2. On Checkout, the site generates an order ID and summary, copies it to the clipboard, and opens the Discord invite.
3. The visitor creates a ticket and pastes the summary.
4. Your owner and devs confirm availability, take payment, and register the domain.

## Ideas for next steps

- Real availability check through a registrar API
- Real accounts and order history
- Admin page to edit prices
- INR pricing toggle
- Bot that posts each new order to a Discord channel through a webhook

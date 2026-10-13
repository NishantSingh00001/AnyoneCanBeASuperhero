# Anyone Can Be a Superhero — static website preview

A neon cyber streetwear concept and collector product-discovery catalog, built as a static multi-page site for Vercel.

## Deploy to Vercel

1. Upload this folder to a GitHub repository.
2. In Vercel, import the repository.
3. Framework preset: **Other**.
4. Build command: leave blank.
5. Output directory: `.` (the repository root).
6. Deploy.

The included `vercel.json` applies clean URL handling and basic security headers. No Node build step is needed.

## Pages

- `index.html` — studio landing page, original concept previews, Collector Radar, local preview forms.
- `shop.html` — seller-link catalog and original design studies.
- `product.html` — detail view for the original concept studies (`?id=signal-bloom`, `?id=orbit-state`, `?id=quiet-signal`).
- `story.html` — quality workflow, manufacturing direction, and licensing roadmap.
- `models.html` — separate AI-generated campaign page with diverse adult model concepts and a camera-led runway with eight selectable, spotlighted looks.
- `BUSINESS-PLAN.md` — business model and validation plan.

## Prototype behavior and limits

- Product links open the retailer’s own listing. The retailer handles sale, payment, stock, shipping, and returns.
- Prices and availability are snapshots and can change; verify them before publication.
- Original product photos are generated concept artwork. They are not inspected physical samples.
- Votes, watchlist, request form, and email field store data only in the visitor’s browser. They do not reach you or a mailing list.
- No checkout, account, product inventory API, affiliate tracking, analytics, or backend is connected.
- The current external product cards use abstract type-based artwork rather than retailer photographs/logos. Obtain permission or an approved feed before adding seller assets.
- The site includes a remembered dark/light theme toggle, a custom cursor on mouse/trackpad, and motion that respects reduced-motion preferences.
- Campaign/model images are AI-generated concepts, not real people, customer photos, or approved physical products. The runway is an animated still-image presentation, not generated video footage; its controls pan and zoom across the models and designs.
- No franchise license is represented as active. A redirect to a licensed seller does not grant permission to reproduce that franchise’s product/design on your own merchandise.

## Customize

Edit seller entries and original concept data in `store.js`; styles are in `styles.css`; original artwork assets are in `assets/`. Recheck every seller URL, product, price, currency, availability, and shipping note before each public update. If adding a paid or affiliate link, disclose the relationship next to the link.

## Working name

Anyone Can Be a Superhero is the current working brand. Check trademark, company-name, and domain availability before using it commercially.

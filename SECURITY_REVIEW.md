# Security Review — Anyone Can Be a Superhero

Code-grounded review against the standard 20-point pen-test checklist. This is a fully static,
client-only concept/catalog site with no backend, no accounts, and no real checkout — product
links point to retailers' own listings, and votes/watchlist/newsletter-email all stay in
`localStorage` on the visitor's device.

| # | Check | Result |
|---|-------|--------|
| 1 | HTTP/2 Rapid Reset (CVE-2023-44487) | N/A — static site, Vercel-managed edge, no custom server |
| 2 | bcrypt 72-byte truncation | N/A — no auth/passwords |
| 3 | SAML signature bypass (CVE-2024-45409) | N/A — no SAML/SSO |
| 4 | nOAuth | N/A — no OAuth |
| 5 | GraphQL alias batching | N/A — no GraphQL |
| 6 | TOTP replay (RFC 6238 §5.2) | N/A — no TOTP/2FA |
| 7 | ReDoS | No — no user-text regexes in `store.js` at all |
| 8 | JWT algorithm confusion | N/A — no JWTs |
| 9 | HTTP request smuggling | N/A — no server, no `fetch`/network calls anywhere in `store.js` or the HTML pages |
| 10 | Web cache poisoning | No — `vercel.json` sets fixed response headers, no request-header-driven caching |
| 11 | Spoofed X-Forwarded-For | N/A — no backend reads request headers |
| 12 | Postgres views bypassing RLS | N/A — no database |
| 13 | `Math.random()` for security tokens | No — not used anywhere in this repo |
| 14 | Timing attacks on secret comparison | N/A — no secrets |
| 15 | Padding oracle | N/A — no encryption |
| 16 | Server-side prototype pollution | N/A — no server |
| 17 | Server-side template injection | N/A — no server-side templating |
| 18 | XXE | N/A — no XML parsing |
| 19 | Cross-site WebSocket hijacking | N/A — no WebSocket use |
| 20 | Unicode username normalization | N/A — no usernames/accounts |

## Findings outside the 20-point list

None. Every value interpolated into `innerHTML` across `store.js` (`productCard`, `merchCard`,
the product-detail view, the watchlist) comes from the hardcoded `products`/`merch` arrays
defined in the same file — never from visitor input. The one place a URL parameter is read
(`product.html`'s `?id=...`, `store.js:28`) is used only as a lookup key into the fixed
`products` array (`products.find(x=>x.id===id)||products[0]`) — the raw query value itself is
never written into the page, so there's no reflected-XSS path through it. The newsletter email
field and the vote/watchlist buttons only ever write to and read from `localStorage` (never
rendered as HTML back into the page in a way that could carry markup — watchlist/vote keys are
always one of the hardcoded product IDs). `vercel.json` already sets `X-Content-Type-Options`,
`X-Frame-Options`, `Referrer-Policy`, and a restrictive `Permissions-Policy`.

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01RCiZNqYmetGt5SuieaZQcC

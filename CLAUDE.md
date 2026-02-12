# IDEAVA Homepage — Project Rules

## Consent Management (Required on Every HTML Page)

Every page must include all 6 elements in this exact order:

1. **Consent default + sync script** (single `<script>` in `<head>`, before GTM) — sets all consent categories to `denied` with `'wait_for_update': 500`, defines `syncConsentFromTermsFeedCookie()` which reads the TermsFeed cookie, deduplicates via `lastConsentCookie`, calls `gtag('consent', 'update', ...)`, and pushes a delayed (400ms) `consent_granted` or `consent_denied` custom event to dataLayer. Runs an initial check immediately, then polls every 500ms via `setInterval` as a safety net.
2. **GTM snippet** (in `<head>`, **after** consent sync) — container ID: `GTM-KVNW2HC`. Must come after the consent sync so the `gtm.js` event (which triggers "All Pages") sees the consent update already in the dataLayer queue.
3. **TermsFeed cookie-consent script** (bottom of `<body>`) — `<script src="https://www.termsfeed.com/public/cookie-consent/4.2.0/cookie-consent.js">`
4. **`cookieconsent.run()`** (bottom of `<body>`, after TermsFeed) — standalone banner, express consent, dark palette
5. **Noscript fallback** (bottom of `<body>`) — `<noscript>` block crediting TermsFeed
6. **Cookie settings button in footer** — `<button id="open_preferences_center" type="button" class="prefs-link">Cookie settings</button>`

Elements 1–2 go in `<head>`. Elements 3–5 go at the bottom of `<body>`.

## GTM Container

Always use `GTM-KVNW2HC`. Never hardcode GA/GTM measurement IDs directly; all tags fire through GTM.

## Copyright

Always `© 2026 IDEAVA`. Update the year when it changes.

## Stylesheets

- Homepage (`/index.html`): loads `/style.css` only.
- All other pages: load **both** `/style.css` and `/blog.css`.

## Footer

Every page footer must include:
- Privacy link: `/privacy/`
- Imprint link: `/imprint/`
- Cookie settings button (`#open_preferences_center`, class `prefs-link`)

Use absolute paths (`/privacy/`, `/imprint/`), not full URLs.

## Blog Post Template

New blog posts start from `_template/blog-post.html`. Copy it to `insights/<slug>/index.html` and replace the `{{PLACEHOLDER}}` markers. See the template for the full list of placeholders.

## File Structure

```
/                       → Homepage
/insights/              → Blog index
/insights/<slug>/       → Individual posts
/privacy/               → Privacy policy
/imprint/               → Imprint / legal
/_template/             → Starter templates (not deployed)
```

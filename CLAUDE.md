# IDEAVA Homepage — Project Rules

## Consent Management (Required on Every HTML Page)

Every page must include all 7 elements in this exact order:

1. **Consent default script** (in `<head>`, before GTM) — sets all consent categories to `denied` with `'wait_for_update': 1000`
2. **GTM snippet** (in `<head>`, after consent default) — container ID: `GTM-KVNW2HC`
3. **Consent sync script** (in `<head>`, right after GTM) — runs `syncConsent()` immediately for returning visitors, then polls every 500ms for first-time visitors who interact with the banner. Must be in `<head>` so the immediate check fires within the 1000ms `wait_for_update` window.
4. **TermsFeed cookie-consent script** (bottom of `<body>`) — `<script src="https://www.termsfeed.com/public/cookie-consent/4.2.0/cookie-consent.js">`
5. **`cookieconsent.run()`** (bottom of `<body>`, after TermsFeed) — standalone banner, express consent, dark palette
6. **Noscript fallback** (bottom of `<body>`) — `<noscript>` block crediting TermsFeed
7. **Cookie settings button in footer** — `<button id="open_preferences_center" type="button" class="prefs-link">Cookie settings</button>`

Elements 1–3 go in `<head>`. Elements 4–6 go at the bottom of `<body>`.

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

# IDEAVA Homepage — Project Rules

## Consent Management (Required on Every HTML Page)

Every page must include all 7 elements in this exact order:

1. **Consent default script** (in `<head>`, before GTM) — sets all consent categories to `denied` with `'wait_for_update': 1000`
2. **GTM snippet** (in `<head>`, after consent default) — container ID: `GTM-KVNW2HC`
3. **TermsFeed cookie-consent script** (`<script src="https://www.termsfeed.com/public/cookie-consent/4.2.0/cookie-consent.js">`)
4. **`cookieconsent.run()`** call — standalone banner, express consent, dark palette
5. **Consent sync poller** — reads `cookie_consent_level` cookie and fires `gtag('consent', 'update', ...)` once
6. **Noscript fallback** — `<noscript>` block crediting TermsFeed
7. **Cookie settings button in footer** — `<button id="open_preferences_center" type="button" class="prefs-link">Cookie settings</button>`

Elements 3–6 go at the bottom of `<body>`, after all other scripts.

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

# Roomies — Legal site

Static hosting for the Roomies **Privacy Policy** and **Terms of Service**, published via
GitHub Pages. These two URLs are required by both the Apple App Store and Google Play.

```
.
├── index.html          landing page → links to both docs
├── privacy/index.html  Privacy Policy   → served at /privacy/
├── terms/index.html    Terms of Service → served at /terms/
├── 404.html            not-found page
└── .nojekyll           serve files as-is (no Jekyll processing)
```

## ⚠️ Fill these placeholders before publishing

Both documents contain `{{PLACEHOLDER}}` tokens (rendered with a colored highlight so you
can spot them). Search-and-replace each one with a real value:

| Placeholder | What to put |
|---|---|
| `{{COMPANY_LEGAL_NAME}}` | The legal entity that operates Roomies (your name, or an LLC/Inc once formed). |
| `{{CONTACT_EMAIL}}` | A real, monitored inbox for privacy/GDPR/CCPA requests — e.g. `privacy@roomiesapp.app`. |
| `{{COMPANY_ADDRESS}}` | Mailing address for the data controller (required for GDPR/CCPA notices). |
| `{{GOVERNING_LAW_JURISDICTION}}` | (Terms only) The state/country whose law governs the Terms. Appears twice. |
| `{{DPO_OR_EU_REP}}` | (Privacy, in an HTML comment) Only if you have no EU establishment — name an Art. 27 EU/UK representative. |

These documents are AI-generated drafts tailored to the Roomies stack. **Have them reviewed
by qualified legal counsel before launch.** A founder note with the same warning lives in an
HTML comment at the top of each file.

## URLs

After GitHub Pages is enabled the docs are reachable at:

- Custom domain: `https://roomiesapp.app/privacy` and `https://roomiesapp.app/terms`
- Project page fallback: `https://devronmarionwatts-pixel.github.io/<repo>/privacy/` and `.../terms/`

The Flutter app defaults to the `roomiesapp.app` URLs
(`roomies_mobile/lib/app/config/app_config.dart`). If you host anywhere else, pass the URLs
in at build time:

```bash
flutter build appbundle \
  --dart-define=PRIVACY_POLICY_URL=https://YOURHOST/privacy/ \
  --dart-define=TERMS_OF_SERVICE_URL=https://YOURHOST/terms/
```

## Custom domain (roomiesapp.app)

Only if you own the domain. Add a file named `CNAME` (no extension) at the repo root
containing exactly:

```
roomiesapp.app
```

…then point DNS at GitHub Pages (see the setup notes that came with this site).

## Editing

Edit the HTML directly and push — GitHub Pages redeploys automatically within ~1 minute.
Cross-links between the two docs are relative (`../privacy/`, `../terms/`) so they work on
both the custom domain and the `github.io` project URL.

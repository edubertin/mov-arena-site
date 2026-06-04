# MOV Arena Public Site

Static public website for MOV Arena. It is intentionally isolated from the Expo
mobile app and can be hosted through GitHub Pages or another static host.

## Four-Part Plan

### 1. Public App Information Page

- `index.html`
- Full-screen MOV Arena visual using `assets/images/login-background.png`
- Short public app/access message
- Links to privacy, terms, and support

Current production URL:

```text
https://mov-arena.eduardobertin.com.br
```

Fallback GitHub Pages URL:

```text
https://edubertin.github.io/mov-arena/
```

### 2. Store-Ready Public Documents

- `privacy.html`
- `terms.html`
- `support.html`

These pages are written to match the current product behavior:

- Google/Supabase login
- admin approval
- workout submissions
- proof image upload
- special class QR/link check-in
- AI-assisted extraction
- AI avatar generation
- optional push notifications
- human audit for score-impacting workouts
- Sentry diagnostics
- in-app account deletion and retention policy

Legal wording is aligned to the current store-readiness plan. It should still
be reviewed if the business model, data practices, or support contact change.

### 3. GitHub Pages / Domain Setup

Recommended public path:

```text
https://mov-arena.eduardobertin.com.br
```

GitHub Pages project URL:

```text
https://edubertin.github.io/mov-arena/
```

Important:

- DNS points the `mov-arena` subdomain to GitHub Pages.
- The repository Pages custom domain should be configured as
  `mov-arena.eduardobertin.com.br`.
- If a path-based URL is needed later, such as
  `eduardobertin.com.br/mov-arena`, configure that route in the root website
  host instead of DNS.

DNS record:

```text
Type: CNAME
Name: mov-arena
Value: edubertin.github.io
TTL: automatic/default
```

This repo includes a GitHub Pages workflow:

- `.github/workflows/pages.yml`

GitHub Pages is configured for this repository with:

```text
Build and deployment source: GitHub Actions
Custom domain: mov-arena.eduardobertin.com.br
HTTPS: enforced
```

The static `site/CNAME` file must stay in the published artifact so GitHub
Pages keeps the custom domain.

Do not publish Expo Web for this website. This is a static marketing/support
site and should stay separate from the mobile app runtime.

## Deployment Record

Initial public site setup:

- Added static site in `site/`.
- Added privacy, terms, and support pages.
- Copied `apps/mobile/assets/images/login-background.png` into
  `site/assets/images/login-background.png`.
- Added `.github/workflows/pages.yml`.
- Enabled GitHub Pages with workflow deployment.
- Configured custom domain `mov-arena.eduardobertin.com.br`.
- Verified GitHub Pages deployment success.
- Verified HTTPS certificate approval and HTTPS enforcement.

Relevant commits:

- `dff13d2` - `docs: add public coming soon site`
- `f7c3caa` - `ci: enable github pages deployment`
- `6fefbdd` - `style: refine public site hero layout`
- `693047b` - `ci: configure pages custom domain`

DNS record used:

```text
Type: CNAME
Name: mov-arena
Value: edubertin.github.io
TTL: 14400 or provider default
```

### 4. Future Upgrade Path

Current public install entry points:

- Android APK: temporarily points to the EAS production APK artifact for
  Android `1.0.2` / build `8`. This artifact expires on 2026-09-01 and should
  be replaced with permanent public storage before broader launch.
- iOS: App Store link for App Store Connect app ID `6767374281`.

When the app is ready for broader testing, add:

- Android closed-testing / Play Store link
- TestFlight link when useful for pre-release groups
- QR code for Android APK and App Store install
- screenshots or short product preview video

## Local Preview

Open `index.html` directly in a browser, or run a simple static server:

```powershell
cd site
python -m http.server 8088
```

Then open:

```text
http://localhost:8088
```

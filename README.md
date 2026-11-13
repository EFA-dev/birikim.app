# birikim_site

Birikim's website at `birikim.app`, served by GitHub Pages: the landing page, the privacy policy, the KVKK notice, the
account deletion instructions the stores ask for, and the two files that claim the app's paths for universal links.

## What it holds

| Part | What it does |
|---|---|
| `index.html` | The landing page with the modules' screenshots (`assets/`) |
| `privacy.html`, `kvkk.html` | The privacy policy and the KVKK notice, from `docs/privacy_policy*.md` and `docs/kvkk.md` |
| `delete.html` | How to delete a Birikim account, for the App Store and Google Play |
| `.well-known/apple-app-site-association` | Claims the app's paths (`/incomes/*`, `/bills/*` …) for iOS; the site's own images and icons excluded |
| `.well-known/assetlinks.json` | Claims the same paths for Android, with the signing certificates' fingerprints |
| `docs/` | The legal texts' sources: privacy policy (Turkish, English), KVKK, Apple's EULA, thanks |
| `src/`, `dist/css/` | The styles (SCSS) and scripts, and the built CSS |
| `changelog/` | Release notes |

## Use

A link such as `https://birikim.app/bills/8f2c` opens the bill in the app when it is installed (the path is one of
`AppPathManager`'s), and this site otherwise.

## Stands on, used by

- **Stands on:** GitHub Pages (`CNAME`, `_config.yml` keeps `.well-known`).
- **Used by:** Birikim's users, the App Store and Google Play (privacy and deletion pages), iOS and Android (app links).

## Run

Pushing to `main` publishes the site. A local look:

```bash
python3 -m http.server 8000
```

## More

How the app links are claimed and kept in step: [`docs/BIRIKIM_SITE.md`](docs/BIRIKIM_SITE.md).

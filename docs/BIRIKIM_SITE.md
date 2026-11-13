# Birikim Site

## What it is

The public face of Birikim at `birikim.app`: a static site on GitHub Pages with the landing page, the legal texts and
the account deletion page the stores require. It also tells iOS and Android which paths on `birikim.app` belong to
the app, so a link to a record opens it in the app.

## The parts

| Part | What it does | Where |
|---|---|---|
| Pages | Landing, privacy policy, KVKK, account deletion | `index.html`, `privacy.html`, `kvkk.html`, `delete.html` |
| Legal sources | The texts the pages are written from, in Turkish and English | `docs/` |
| iOS association | `applinks` for the app id, one component per module path, the site's assets excluded | `.well-known/apple-app-site-association` |
| Android association | The app's package and its signing certificates' SHA-256 fingerprints | `.well-known/assetlinks.json` |
| Styles and scripts | SCSS sources and the built CSS | `src/`, `dist/css/` |

## How it works

### App links

A path on `birikim.app` that names a module (`/incomes`, `/incomes/*`, `/bills/*` …) is claimed by the app; anything
else (the site's images and icons, which always carry a dot) is the site's. The app's Android https filter takes the
same prefixes, and a test in `birikim_mobile` keeps the iOS file, the Android filter and `AppPathManager` in step.
Paths carry record ids only. See `birikim_mobile/docs/LINKS_AND_NOTIFICATIONS.md`.

### Publishing

GitHub Pages serves `main` at `birikim.app` (`CNAME`); `_config.yml` includes `.well-known`, which Jekyll would
otherwise skip.

## Rules

- A path the app claims is never renamed; the site never uses a claimed path for its own page.
- The privacy policy changes with the app: a new data use is written here in both languages before it ships.
- A new signing certificate's fingerprint goes into `assetlinks.json` before a build signed with it ships.

## Decisions

- **A static site.** Nothing to run or patch; the stores' required pages are plain HTML.

## Known gaps

- None recorded.

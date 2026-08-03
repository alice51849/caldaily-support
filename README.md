# CalDaily — Support & Privacy Site

A five-file static website for the iOS app **CalDaily**, built to satisfy the
App Store Connect Support URL and Privacy Policy URL requirements and to serve
as the app's public home page.

```
index.html     Home: positioning, features, privacy summary, contact
support.html   FAQ, troubleshooting, contact and what to include
privacy.html   Privacy policy with "Last updated" line
styles.css     All styling (shared by the three pages)
README.md      This file
```

Everything is self-contained: no frameworks, no CDNs, no web fonts, no images,
no analytics, no tracking, no external resources of any kind. The pages use the
system font stack and work offline as plain files.

---

## Deploy to GitHub Pages

1. Create a new **public** repository named `caldaily-support` on GitHub
   (account: `alice51849`).
2. Copy the five files in this folder into the repository root — not into a
   subfolder, so that `index.html` sits at the top level.
3. Commit and push to the `main` branch:

   ```
   git init
   git add .
   git commit -m "CalDaily support and privacy site"
   git branch -M main
   git remote add origin https://github.com/alice51849/caldaily-support.git
   git push -u origin main
   ```

4. In the repository, open **Settings → Pages**.
   Under *Build and deployment*, set **Source** to `Deploy from a branch`,
   **Branch** to `main`, folder `/ (root)`, then click **Save**.
5. Wait one to two minutes for the first build, then confirm all three pages
   load and that the header links move between them correctly.

The site is then live at:

```
https://alice51849.github.io/caldaily-support/
https://alice51849.github.io/caldaily-support/support.html
https://alice51849.github.io/caldaily-support/privacy.html
```

To publish updates later, edit the files and push again; Pages rebuilds
automatically.

---

## URLs to paste into App Store Connect

In App Store Connect → your app → **App Information** / the version's
**App Store** tab:

| App Store Connect field | Value to paste |
| --- | --- |
| **Support URL** (required) | `https://alice51849.github.io/caldaily-support/support.html` |
| **Privacy Policy URL** (required) | `https://alice51849.github.io/caldaily-support/privacy.html` |
| **Marketing URL** (optional) | `https://alice51849.github.io/caldaily-support/` |

Notes:

- Give the reviewer the deep links, not just the home page — pointing Support
  and Privacy at distinct pages is the clearest signal that both exist.
- The Privacy Policy URL is also requested in the **App Privacy** section; use
  the same `privacy.html` URL there.
- Verify every URL in a browser before submitting. A URL that 404s is a common
  cause of rejection.

**General URL format** (if the account or repository name changes):

```
https://<github-username>.github.io/<repository-name>/support.html
https://<github-username>.github.io/<repository-name>/privacy.html
https://<github-username>.github.io/<repository-name>/
```

---

## How to change things

### App name

The name appears in the header brand link, the `<title>` of each page, the
hero heading, and in body copy. To rename, search and replace `CalDaily`
across `index.html`, `support.html` and `privacy.html`.

### Contact email

The email is `hourstag.app@gmail.com`. It appears in the footer of all three
pages plus the contact sections of `index.html`, `support.html` and
`privacy.html`. Search and replace the string; each occurrence appears twice
per link (once in `href="mailto:…"`, once as the visible text), so replace all.

### App Store link

`index.html` contains a placeholder button:

```html
<!-- Replace the href below with the App Store link once the app is live. -->
<a class="btn btn-primary" href="#">Download on the App Store</a>
```

Replace `#` with the real App Store URL
(`https://apps.apple.com/app/id<APP_ID>`) once the app is published, and delete
the small "App Store link placeholder" line directly beneath the buttons.

### Privacy "Last updated" date

Edit the `<p class="updated">` line near the top of `privacy.html` whenever the
policy text changes. Keep the format `Last updated: 4 August 2026`.

### Copyright line

The footer of each page reads `2026 Caitlyn`. Update the year there if needed.

### Colours and layout

All visual styling lives in `styles.css`. The palette is defined once in the
`:root` block at the top — change `--accent`, `--accent-deep` and
`--accent-wash` to shift the accent colour, and the `background-image` on
`body` to adjust the warm gradient. Nothing else needs touching.

---

## Rules this site follows

- No external requests of any kind — nothing to block, nothing to break.
- No emoji.
- No fixed response-time promise on the support page.
- Only features that actually ship are described: 100 themes (1 free, 99 via a
  single non-consumable purchase), Home Screen widget, 8 advanced tools with
  3 free results each and user-set defaults, history with subject, type,
  search, day grouping, tool filter and CSV export, 50 languages, on-device
  only.
- Privacy claims match the build: no account, no collection, no ads, no
  analytics, no third-party SDKs, no network calls.

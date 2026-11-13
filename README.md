# Coder111 Apps website (GitHub Pages)

A developer website for all your apps. It's separate from your portfolio and is built to sit at the root of its own `github.io` address, so AdMob can find `app-ads.txt`.

```
index.html                     Home page: studio intro, apps list, contact
jar-pour/index.html            Jar Pour app page
jar-pour/privacy-policy.html   Jar Pour privacy policy (the URL for Play Console)
app-ads.txt                    AdMob seller file (must stay at the root)
privacy-policy.html            Redirects to jar-pour/privacy-policy.html
404.html, icon.png, assets/style.css, .nojekyll
```

Before you push, replace `[CONTACT EMAIL]` in `index.html` and `jar-pour/privacy-policy.html`.

## Why a GitHub organization, not a normal repo
AdMob only reads `https://<domain>/app-ads.txt`. On GitHub Pages, only a repo named `<owner>.github.io` is served at the root. Your user's `<username>.github.io` already holds the portfolio, so create a free **organization** and give it its own root site.

## Publish
1. **Create the organization.** On github.com, click **+ → New organization → Free**. Name it e.g. `coder111-apps`.
2. **Create the repo** in that org. Name it exactly `coder111-apps.github.io` and make it **public**.
3. **Push this folder** (run inside `website-privacy`):
   ```
   git init
   git add .
   git commit -m "Coder111 Apps website"
   git branch -M main
   git remote add origin https://github.com/coder111-apps/coder111-apps.github.io.git
   git push -u origin main
   ```
4. **Turn on Pages.** In the repo, go to **Settings → Pages → Deploy from a branch → main / (root) → Save**.
5. About a minute later, check these URLs:
   - https://coder111-apps.github.io
   - https://coder111-apps.github.io/jar-pour/privacy-policy.html
   - https://coder111-apps.github.io/app-ads.txt

## Wire it up
- **Play Console → App content → Privacy policy:** `https://coder111-apps.github.io/jar-pour/privacy-policy.html`
- **Play Console → Store settings → Website:** `https://coder111-apps.github.io`
- **AdMob → Apps → Jar Pour → app-ads.txt:** check status once the Play listing is live. AdMob crawls within about 24 hours.

## Adding another app later
Copy `jar-pour/` to `<new-app>/`, edit its two pages, and add a card to the Apps grid in `index.html`. If the new app uses AdMob under the same account, `app-ads.txt` doesn't need to change.

# Coder111 Apps website

The developer website for all Coder111 Apps games, hosted on GitHub Pages. It's separate from the personal portfolio.

| | |
|---|---|
| **Live site** | https://coder111-apps.github.io |
| **Repo** | https://github.com/coder111-apps/coder111-apps.github.io (GitHub organization `coder111-apps`) |
| **Branch / Pages source** | `main` / root |
| **Local folder** | `K:\WorkSpace\Android\export-apps\website-privacy` |

## Live URLs in use
| What | URL | Used in |
|---|---|---|
| Developer website | https://coder111-apps.github.io | Play Console → Store settings → Website |
| Jar Pour privacy policy | https://coder111-apps.github.io/jar-pour/privacy-policy.html | Play Console → App content → Privacy policy |
| app-ads.txt | https://coder111-apps.github.io/app-ads.txt | Read by AdMob automatically |

**Don't rename the org, the repo or `jar-pour/privacy-policy.html`.** Play Console points to these URLs; if one breaks, Play can flag the app.

## Files
```
index.html                     Home page: intro, apps list, contact
jar-pour/index.html            Jar Pour app page
jar-pour/privacy-policy.html   Jar Pour privacy policy
app-ads.txt                    AdMob authorised sellers (must stay at the root)
privacy-policy.html            Old address, redirects to jar-pour/privacy-policy.html
404.html                       Not-found page
icon.png                       Favicon and Jar Pour icon
assets/style.css               Shared styles for every page
.nojekyll                      Serve files as-is (no Jekyll processing)
```

## Publishing a change
```
git add .
git commit -m "Describe the change"
git push
```
GitHub Pages redeploys in about a minute. Check progress under the repo's **Actions** tab.

## Common tasks

### Update the Jar Pour privacy policy
1. Edit `jar-pour/privacy-policy.html`.
2. Update the **Effective date** line.
3. Push. The Play Console URL stays the same, so there's nothing to change there.

Update the policy whenever the app starts collecting new data, e.g. if you add Firebase Analytics, Crashlytics, sign-in or in-app purchases. Update the Data safety form in Play Console at the same time.

### Add a new app
1. Copy `jar-pour/` to `<new-app>/`, e.g. `colour-stack/`.
2. Edit `<new-app>/index.html` and `<new-app>/privacy-policy.html` with the app's name, features, the data it uses, and the date.
3. In `index.html`, copy the Jar Pour `<article class="card">` block inside the Apps grid and change it for the new app.
4. Add the new app's icon, e.g. `<new-app>/icon.png`, and point that card and those pages to it.
5. Push. Use `https://coder111-apps.github.io/<new-app>/privacy-policy.html` in that app's Play Console listing.

### Change the Google Play badge once Jar Pour is live
In `index.html` and `jar-pour/index.html`, replace the "Coming soon to Google Play" badge with a link:
```html
<a href="https://play.google.com/store/apps/details?id=com.coder111.jarpour">Get it on Google Play</a>
```

### app-ads.txt
- The current line is `google.com, pub-5403045216544799, DIRECT, f08c47fec0942fa0`. The `pub-` part is your AdMob publisher ID; `f08c47fec0942fa0` is Google's fixed ID.
- **New apps on the same AdMob account:** no change needed. One file covers every app that lists this website.
- **Adding mediation networks** (Meta, Unity, AppLovin and others): paste each network's lines below the Google line.
- **Check the status** in AdMob → Apps → View all apps → **app-ads.txt** tab. AdMob crawls about every 24 hours, and only after the app is live on Play with this website set in Store settings.

## Troubleshooting
| Problem | Fix |
|---|---|
| Site shows 404 after a push | Wait 1–2 minutes and check the Actions tab. Pages must be set to `main` / root. |
| AdMob says app-ads.txt not found | Open https://coder111-apps.github.io/app-ads.txt in a browser. It must show the plain line at the root, not under a subfolder. The Play listing's Website must be exactly `https://coder111-apps.github.io`. |
| Styles missing on a new page | Pages one folder deep use `../assets/style.css` and `../icon.png`. |
| Play says privacy policy URL is invalid | The page must load without sign-in. Open it in a private window to check. |

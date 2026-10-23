# ghostword-site

Public pages for GhostWord, the Android word séance app (app ID `dev.auxon.ghostword`).

| Page | URL |
| - | - |
| Home | https://cyrillical00.github.io/ghostword-site/ |
| Privacy policy | https://cyrillical00.github.io/ghostword-site/privacy/ |
| Download (draft fallback, not linked from Home) | https://cyrillical00.github.io/ghostword-site/download/ |

The privacy policy URL is the one the app's Settings screen opens and the one entered in Google Play Console (store listing and Data safety). Don't move or rename `privacy/index.html`.

## How it's published

GitHub Pages serves the `main` branch from the repo root. Plain HTML: no build step, no scripts, no fonts or images from other sites, no analytics. `.nojekyll` tells Pages to serve the files as they are.

## Updating the privacy policy

The source of truth is `ghostword/docs/play/privacy-policy.html` in the app repo (`cyrillical00/ghostword`, private), with `privacy-policy.md` kept word for word in step. To change the policy:

1. Edit both files in the app repo and run the checks in `ghostword/docs/play` (`python -m unittest discover -s docs/play -p "test_*.py"` from `ghostword/`).
2. Copy `privacy-policy.html` here as `privacy/index.html`.
3. Change the effective date at the top of the policy.
4. If what the app does with data changed, update the Data safety form in Play Console to match before the new app version ships.

## Releasing the APK

`download/index.html` is a fallback in case GhostWord isn't live on Google Play in time. Its button points at `releases/latest/download/ghostword.apk`, so it only works once a release exists. Use an APK signed with GhostWord's upload key, built from the same code as bundle 109. Don't use the Signed, universal APK from Play Console: Play added automatic protection to bundle 109 (an installer check, recorded in the app repo's runbook on 2026-10-22), and Google says a protected app that wasn't installed from Google Play prompts the user to get it from Google Play instead. Before the Play listing is live, that's a dead end. This hasn't been tested on a phone. Because the upload key and Play's app signing key differ, anyone who installs this APK has to uninstall it before installing from Play, as the page says.

1. Create a GitHub Release on this repo and attach the APK with the asset name exactly `ghostword.apk`.
2. Fill both SHA-256 placeholders in `download/index.html`: the file's hash and the signing certificate's hash (the HTML comment above them says how).
3. Merge to `main`. Link the page from Home only if you want people to find it there.

Contact: ghostword@auxon.dev

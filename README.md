# ghostword-site

Public pages for GhostWord, the Android word séance app (app ID `dev.auxon.ghostword`).

| Page | URL |
| - | - |
| Home | https://cyrillical00.github.io/ghostword-site/ |
| Privacy policy | https://cyrillical00.github.io/ghostword-site/privacy/ |

The privacy policy URL is the one the app's Settings screen opens and the one entered in Google Play Console (store listing and Data safety). Don't move or rename `privacy/index.html`.

## How it's published

GitHub Pages serves the `main` branch from the repo root. Plain HTML: no build step, no scripts, no fonts or images from other sites, no analytics. `.nojekyll` tells Pages to serve the files as they are.

## Updating the privacy policy

The source of truth is `ghostword/docs/play/privacy-policy.html` in the app repo (`cyrillical00/ghostword`, private), with `privacy-policy.md` kept word for word in step. To change the policy:

1. Edit both files in the app repo and run the checks in `ghostword/docs/play` (`python -m unittest discover -s docs/play -p "test_*.py"` from `ghostword/`).
2. Copy `privacy-policy.html` here as `privacy/index.html`.
3. Change the effective date at the top of the policy.
4. If what the app does with data changed, update the Data safety form in Play Console to match before the new app version ships.

Contact: ghostword@auxon.dev

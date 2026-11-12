# better-prompt-deploy-check

A placeholder page that proves a set of deploy steps on GitHub Pages. Live: https://rivology.github.io/better-prompt-deploy-check/

## How it is published
GitHub Pages serves the `main` branch, root folder. There is no build step: `index.html` is the page. `.nojekyll` tells Pages to serve the files as they are.

## How to update it
1. Edit `index.html` (change the version stamp so the new version can be recognised on the live page).
2. `git add -A && git commit -m "what changed" && git push`
3. Wait for the Pages build: `gh api repos/Rivology/better-prompt-deploy-check/pages/builds/latest --jq .status` prints `built`.
4. Open the live link with a fresh query string (for example `?v=2`), because Pages caches pages for about 10 minutes, and check that the new stamp shows.

## How to roll back
`git revert --no-edit HEAD && git push`, then wait for the build and check the live link as in steps 3 and 4. Reverting adds a new commit, so nothing is lost.

## How to take it down
Repo Settings → Pages → Unpublish site, or delete the repo.

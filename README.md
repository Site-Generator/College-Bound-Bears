# club-site-template

GitHub template for a new club's site repo. Clicking **Use this template**
gives you the boilerplate (`.gitignore`, `.pages.yml`, a placeholder
`club.json`, an empty `images/`) — it does **not** include the generator
engine, since that's pulled in via `git subtree` (a plain template copy
can't be `subtree pull`ed later to receive future engine fixes).

## After creating a repo from this template

You've done steps 1–2 of the [full onboarding runbook in
club-fleet-tools](https://github.com/Site-Generator/club-fleet-tools#onboarding-a-new-club)
(private, org-owner access). Pick up from there — in short:

1. Rename this repo if you haven't already (should be `<slug>-site`).
2. Replace `"REPLACE ME — New Club"` in **both** `club.json` (the `clubName`
   field) and `.pages.yml` (the `label:` field) with the real club name.
3. Pull in the shared engine:
   ```bash
   git clone https://github.com/Site-Generator/<slug>-site.git
   cd <slug>-site
   git remote add core https://github.com/Site-Generator/club-site-generator-core.git
   git subtree add --prefix=generator core main --squash
   git push
   ```
4. Add `.github/workflows/deploy-pages.yml` at the repo root (copy an
   existing `<slug>-site` repo's version, swap its `CLUB_SLUG` value for this
   club's slug), push, then enable it: repo **Settings → Pages → Source:
   GitHub Actions**.
5. Create its own dedicated Pages CMS project at app.pagescms.org, and
   install the Pages CMS GitHub App scoped to just this repo.
6. Add its repo URL to `CLUB_REPOS` in `club-fleet-tools/sync-generator.sh`,
   and add the repo to `CLUB_REPOS_TOKEN`'s allowed-repository list (GitHub
   → Settings → Developer settings → Personal access tokens → Fine-grained
   tokens → `CLUB_REPOS_TOKEN` → edit repository access) — both are needed
   or future engine syncs will silently miss this club.
7. Invite that club's officers as collaborators on **this repo only**
   (Write access, not Admin).

Delete this README's content and replace it with something club-specific
once you're set up (see any existing `<slug>-site` repo for the pattern).
**Keep `PAGES-CMS-GUIDE.md`** (or link to it from your new README) — it's
the officer-facing guide for editing content through Pages CMS, and has
nothing club-specific in it that needs changing.

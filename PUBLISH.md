# Publishing this folder to GitHub

Target: **github.com/asilivirtualschool-max/worthwhile-tasks** (public), served by GitHub Pages at
`https://asilivirtualschool-max.github.io/worthwhile-tasks/`

State of play: the repo is initialised here on branch `main` with one commit (`d38ce4d`) holding all
13 files. `README.md` has since been updated with your account name, and this file is new — both are
uncommitted, because a stale `index.lock` now blocks any further git command. Step 1 clears it.

Open **PowerShell** and run each block in order.

## 1. Go to the folder and clear the stale locks

Left behind by the tool that made the commit. Deleting them loses nothing — the commit is intact.

```powershell
cd "$env:USERPROFILE\OneDrive - GEMS Education\Desktop\Rapture\YEAR OF MANIFESTATION\INCUBATOR\EDU FORGE INCUBATION\Project 1\worthwhile-tasks"

Remove-Item .git\index.lock,.git\HEAD.lock,.git\objects\maintenance.lock -Force -ErrorAction SilentlyContinue
Get-ChildItem .git\objects -Recurse -Filter tmp_obj_* | Remove-Item -Force

git status
```

Expected: `modified: README.md` and `PUBLISH.md` untracked, with no lock complaint.

## 2. Commit those two changes

```powershell
git add -A
git commit -m "Set Pages URL to asilivirtualschool-max; add publishing instructions"
git log --oneline
```

## 3. Create the repository and push

**With the GitHub CLI** (`gh --version` works) — creates and pushes in one:

```powershell
gh repo create worthwhile-tasks --public --source . --remote origin --push
```

**Without it** — create the repo on the web first at <https://github.com/new>:
owner `asilivirtualschool-max`, name `worthwhile-tasks`, **Public**, and add **no** README,
.gitignore or licence (it must start empty). Then:

```powershell
git remote add origin https://github.com/asilivirtualschool-max/worthwhile-tasks.git
git push -u origin main
```

## 4. Turn on GitHub Pages

Repo → **Settings** → **Pages** → Source: **Deploy from a branch** → Branch `main`, folder `/ (root)` → **Save**.

Live in about a minute:

- Site — `https://asilivirtualschool-max.github.io/worthwhile-tasks/`
- Prompt builder alone — `https://asilivirtualschool-max.github.io/worthwhile-tasks/prompt-builder.html`
- Programme — `https://asilivirtualschool-max.github.io/worthwhile-tasks/programme.html`

`.nojekyll` is already committed, so the HTML is served as-is.

## Two things worth knowing

**OneDrive and `.git`.** This repo sits inside a synced OneDrive folder, which is what produced the
lock problem above and can corrupt `.git` by syncing mid-write. Once it's on GitHub, clone it
somewhere outside OneDrive (e.g. `C:\dev\worthwhile-tasks`) and work there.

**Licensing.** `ATTRIBUTION.md` records that the Transforming Tasks framework belongs to the South
Australian Department for Education, with the licensing position unconfirmed. A public repo puts this
on the open web — fine for a free, credited PD resource; settle the position in writing before
charging for access.

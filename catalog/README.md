# Submitting to the Flipper Apps Catalog

`manifest.yml` in this folder is the draft for the catalog pull request.
Requirements were checked against the catalog's `Contributing.md` and
`Manifest.md` on 2026-11-10.

## Before submitting

1. Take screenshots with qFlipper (leave them exactly as qFlipper saves them) and save
   them as `screenshots/ss0.png`, `ss1.png`, `ss2.png`. See
   [screenshots/README.md](../screenshots/README.md) for suggestions.
2. Commit everything and push to `main`. Wait for CI to pass.
3. Put that commit's full SHA into `commit_sha` in `manifest.yml`. If you
   use fewer or more screenshots, edit the list to match.

## Validate the manifest locally (recommended)

In a clone of your fork of `flipperdevices/flipper-application-catalog`:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
python -m pip install -r tools\requirements.txt
New-Item -ItemType Directory -Force applications\Tools\hamcram
Copy-Item <path to HamCram>\catalog\manifest.yml applications\Tools\hamcram\
python tools/bundle.py --nolint applications/Tools/hamcram/manifest.yml bundle.zip
```

The script clones this repo at `commit_sha`, builds the app and checks the
icon, screenshots, README and changelog. Fix anything it reports.

## Open the pull request

1. Create a branch named `NicPWNs/hamcram_1.0`.
2. Add `applications/Tools/hamcram/manifest.yml`.
3. Open the pull request and fill in its template.

## Updates

Bump `fap_version` in `application.fam` (the catalog rejects a version it
has already seen), add a changelog entry, push, then send a new pull request
that changes only `commit_sha`.

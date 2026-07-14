# Vorentis — Releases

Download the latest installer from **[Releases](https://github.com/Hemanshu-jain/Vorentis-Release/releases)**.

---

## What this repo is

A delivery channel, and nothing else. **There is no source code here.**

Vorentis is a Windows desktop app that updates itself. To do that,
[`electron-updater`](https://www.electron.build/auto-update) running on a shopkeeper's machine has
to be able to read a release feed **without any credentials** — so the feed has to be public.

Making the *source* repo public to achieve that would mean publishing the whole product. So the
source stays private and this repo exists purely to host the installers:

| repo | visibility | contains |
|---|---|---|
| `Vorentis` | private | the source |
| `Vorentis-Release` (this one) | public | the installers, and this README |

## Installing

Grab `Vorentis-Setup-<version>.exe` from the latest release and run it.

It installs per-user, so Windows will not ask for admin rights. Because the installer isn't code-signed
yet, Windows SmartScreen shows a **"Windows protected your PC"** notice the first time — click
**More info → Run anyway**. That prompt appears only on a manual install; automatic updates of an
already-installed copy never show it.

## Updating

You don't have to do anything. An installed copy checks this repo on launch, downloads a newer version
in the background, and applies it on the next restart. Your data is untouched by an update.

If the check fails — no internet, GitHub unreachable — the app just carries on. A dead update feed can
never stop you making a sale.

## Each release contains

| file | why |
|---|---|
| `Vorentis-Setup-<version>.exe` | the installer |
| `latest.yml` | the manifest `electron-updater` reads: version + SHA-512 |
| `*.blockmap` | lets an update download only the **changed** chunks, not the whole ~120 MB again |

All three must be present, and the filename in `latest.yml` must match the uploaded asset exactly —
which is why the installer is named with hyphens rather than spaces (GitHub rewrites spaces in asset
filenames, and a mismatch makes updates fail *silently*).

---

© 2026 Vorentis Software Pvt Ltd

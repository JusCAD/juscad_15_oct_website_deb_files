# JusCAD 0.5.0 — Ubuntu installer

This repository provides the **two files a first-time user needs** for Ubuntu
24.04 Desktop, amd64/x86-64. The repository name contains `15_oct`; the actual
package version is **0.5.0-native-internal**.

**Unsigned internal synthetic test build.** This is not a qualified production
customer release. Use synthetic CAD only. Browser/email signup on a fresh desktop
remains a manual acceptance step. The application connects to JusCAD's hosted
Gemini/MCP service; no AWS credentials, model API key or developer setup is needed.

## Download these two files

1. [juscad_0.5.0-native-internal_amd64.deb](https://github.com/JusCAD/juscad_15_oct_website_deb_files/raw/refs/heads/main/juscad_0.5.0-native-internal_amd64.deb)
2. [juscad_0.5.0-native-internal_amd64.deb.sha256](https://raw.githubusercontent.com/JusCAD/juscad_15_oct_website_deb_files/main/juscad_0.5.0-native-internal_amd64.deb.sha256)

Save both in your Downloads folder. You do **not** need a tar.gz, a git clone,
repository source code or a separate FreeCAD installation.

The installer is approximately 783 MiB. Keep at least **8 GiB free on the Linux
installation filesystem before installation**. First launch extracts the bundled
FreeCAD runtime into your per-user data directory and checks remaining space.

## Verify, install, launch

In a desktop terminal:

```bash
cd ~/Downloads
sha256sum -c juscad_0.5.0-native-internal_amd64.deb.sha256
```

Continue only if the result is **OK**:

```bash
sudo apt install ./juscad_0.5.0-native-internal_amd64.deb
juscad
```

Launch FreeCAD as your normal user, never with sudo. You can also select
**JusCAD Native** in Applications. If an older local `juscad` command shadows the
new system command, use `/usr/bin/juscad` without deleting the older installation.

Expected installer SHA256:

```text
31304f517da1aeb5129a8981a14d9823d09ee2ee923fb2f7d684ca062e0ee6d3
```

The checksum checks file integrity; this internal package is not independently signed.

## Sign up and make your first native part

1. In FreeCAD, select the **JusCAD** workbench and its native engineering review panel.
2. Click **Sign up / Sign in (browser)**. New users choose Sign up, enter their
   email/password and verify the email. Return to FreeCAD when login completes.
3. Create an empty document and save it as `SYNTHETIC_plate.FCStd`.
4. Click **Connect native service**. Read and explicitly accept the synthetic
   evidence-capture notice if you agree. Bound-document prompts, actions and CAD
   evidence are sent to JusCAD's AWS staging service after consent.
5. Enter:

   > Create a native mounting plate: width 60 mm, height 40 mm, thickness 3 mm,
   > two centered through holes diameter 6 mm and center spacing 30 mm.
   > Prepare for my review; do not apply.

6. Inspect the candidate, sketches, constraints and diff. Select the original
   source tab, then approve the reviewed batch locally and confirm.
7. Request thickness 4 mm while preserving the holes; review and approve again.
   Geometry appears locally. Use Fit all if necessary. Save explicitly: Apply does
   not save over your original file. Undo/Redo remains available.
8. Keep connected while evidence uploads finish; retain any reported errors.

Current operations are native mounting-plate creation, Pad Length and named
Width/Height. Arbitrary STEP edits, sketches, joints and assemblies are not yet
supported. App login is session-only, so sign in again after restarting FreeCAD.
Login callback uses local port 53682; another simultaneous login can block it.
SaveAs requires disconnecting and rebinding the document.

The current staging application evidence access expires after seven days or
earlier workflow expiry; physical versions/backups may persist longer. This is
not the future customer 30-day policy and not a claim of complete action replay.

## Packaging and repository notes

JusCAD implementation ships as compiled modules, with no readable JusCAD Python
sources. FreeCAD's unmodified upstream runtime retains its licensed Python files
and third-party notices. Compilation does not prevent reverse engineering.

The deb is stored through **Git LFS** because it exceeds ordinary GitHub file
limits. Use the two download links above. GitHub **Code → Download ZIP** or a
clone without Git LFS can contain a small pointer instead of the real installer;
the genuine deb is approximately 783 MiB, not a few hundred bytes.

Only two downloadable software files are included. README.md is this guidance;
.gitattributes is required Git LFS metadata. No model keys, server checkout, local
environment files, CAD datasets or development environment are distributed here.

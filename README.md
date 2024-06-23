# Skyb0rg007's Custom Scoop Bucket

[![Tests](https://github.com/Skyb0rg007/my-scoop-bucket/actions/workflows/ci.yml/badge.svg)](https://github.com/Skyb0rg007/my-scoop-bucket/actions/workflows/ci.yml) [![Excavator](https://github.com/Skyb0rg007/my-scoop-bucket/actions/workflows/excavator.yml/badge.svg)](https://github.com/Skyb0rg007/my-scoop-bucket/actions/workflows/excavator.yml)

This bucket contains useful applications which are missing from the default Scoop repositories

## Installation

```shell
scoop bucket add Skyb0rg007-extras https://github.com/Skyb0rg007/my-scoop-bucket
scoop install Skyb0rg007-extras/<appname>
```

## Apps
- [Plover](#plover)
- [SML/NJ](#standard-ml-of-new-jersey)
- [Cockatrice](#cockatrice)

## Plover

[Plover](https://www.openstenoproject.org/plover/) is an application for
hobbiest stenographers which acts as a keyboard replacement.

```shell
scoop install Skyb0rg007-extras/plover
```

### Note on Versioning
While the most recent (non pre-)release is labeled a release candidate,
this version of Plover is recommended for most users due to the inclusion
of the Plugins feature and being relatively stable.
Because the most recent "SemVer stable" release is more than 4 years behind the
4.0.0rc2 release, I don't see a reason to name the package `plover-dev`
or similar.
This does mean I cannot use the default checkver or autoupdate
features of Scoop (everything is considered "version 4.0.0").

### Note on persistence
Plover's portable mode sets the configuration directory to the current
directory as long as there is a `plover.cfg` file there.
However this dumps plugin files and other persistent data
in the same directory as the executable itself,
making it impossible to symlink into the persist directory.
To avoid this the Scoop App adds `.cmd` wrappers around
`plover` and `plover_command` executables that first set the working
directory to the `persist` subfolder.
The [code for this](bucket/plover.json) is copied from the
[`anki` Scoop module](https://github.com/ScoopInstaller/Extras/blob/21ad585fe555528dae2d27aeab7372303aa9500a/bucket/anki.json#L15).
This unfortunately means that a command prompt will flash on launch.

## Standard ML of New Jersey
[Standard ML of New Jersey](https://www.smlnj.org/smlnj.html)
(abbreviated SML/NJ) is a compiler for the
[Standard ML '97](https://www.smlnj.org/sml97.html)
programming language with associated libraries, tools, and documentation.
SML/NJ is free, open source software.

```shell
scoop install Skyb0rg007-extras/smlnj
```

### Note
Compared to a standard installation, the shims do not use batch.
This means they better support command line arguments with spaces in them,
and can handle more than 9 positional arguments.
The `link-sml` batch script was an internal detail of previous `ml-build`
implementations which is no longer used, so it is not exposed as a shim.

Version checking is not currently implemented, but could in theory.

## Cockatrice
[Cockatrice](https://cockatrice.github.io/) is a cross-platform
virtual tabletop for multiplayer card games.

```shell
# On 64-bit Windows 10 and up
scoop install Skyb0rg007-extras/cockatrice
# Otherwise (just requires Windows 7)
scoop install Skyb0rg007-extras/cockatrice-qt5
```

### Note
Cockatrice has three Windows downloads:
`Windows 10+`, `Windows 7+`, and `Windows 7+ (32-bit)`.
This is because the most recent version of the UI libary (`Qt`)
is not supported on Windows 7.
Because Scoop does not allow for OS version-based configuration,
this bucket contains two manifests.
The `cockatrice` manifest includes the `Windows 10+` download.
The `cockatrice-qt5` manifest includes the `Windows 7+`
and `Windows 7+ (32-bit)` downloads.

## Template TODO list

1. [X] Generate your own copy of this repository with the "Use this template"
   button.
2. [X] Allow all GitHub Actions:
   - Navigate to `Settings` - `Actions` - `General` - `Actions permissions`.
   - Select `Allow all actions and reusable workflows`.
   - Then `Save`.
3. [X] Allow writing to the repository from within GitHub Actions:
   - Navigate to `Settings` - `Actions` - `General` - `Workflow permissions`.
   - Select `Read and write permissions`.
   - Then `Save`.
4. [X] Document the bucket in `README.md`.
5. [X] Replace the placeholder repository string in `bin/auto-pr.ps1`.
6. [X] Create new manifests by copying `bucket/app-name.json.template` to
   `bucket/<app-name>.json`.
7. [X] Commit and push changes.
8. [ ] If you'd like your bucket to be indexed on `https://scoop.sh`, add the
   topic `scoop-bucket` to your repository.

## How do I contribute new manifests?

To make a new manifest contribution, please read the [Contributing
Guide](https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md)
and [App Manifests](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests)
wiki page.

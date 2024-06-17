# Skyb0rg007's Custom Scoop Bucket

[![Tests](https://github.com/Skyb0rg007/my-scoop-bucket/actions/workflows/ci.yml/badge.svg)](https://github.com/Skyb0rg007/my-scoop-bucket/actions/workflows/ci.yml) [![Excavator](https://github.com/Skyb0rg007/my-scoop-bucket/actions/workflows/excavator.yml/badge.svg)](https://github.com/Skyb0rg007/my-scoop-bucket/actions/workflows/excavator.yml)

This bucket contains useful applications which are missing from the default Scoop repositories

## Installation

```pwsh
scoop bucket add Skyb0rg007-extras https://github.com/Skyb0rg007/my-scoop-bucket
scoop install Skyb0rg007-extras/<appname>
```

## Plover

[Plover](https://www.openstenoproject.org/plover/) is an application for
hobbiest stenographers which acts as a keyboard replacement.

### Note
While the most recent (non pre-)release is labeled a release candidate,
this version of Plover is recommended for most users due to the inclusion
of the Plugins feature and being relatively stable.
Because the most recent "SemVer stable" release is more than 4 years behind the
4.0.0rc2 release, I don't see a reason to name the package `plover-dev`
or similar.
This does mean I cannot use the default checkver or autoupdate
features of Scoop (everything is considered "version 4.0.0").

<!-- TODO: SML/NJ -->

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

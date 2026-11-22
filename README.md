# idpf-templates

Published project templates for [Praxis Hub Manager](https://github.com/rubrical-worker/px-manager) (PHM).

When you create a new IDPF project in PHM, you can start from a template instead of an empty project. A template fills in the project's charter, skill assignments, lock files, framework configuration and CI workflow, and runs the setup `/charter` would otherwise do at inception. The project then starts with its setup decisions already made.

This repository holds only the published releases. Templates are authored, validated and published from [`rubrical-works/idpf-phm-project-templates`](https://github.com/rubrical-works/idpf-phm-project-templates).

## Templates

| Id | Archetype | What it sets up |
|---|---|---|
| `api-service` | api-service | A Flask HTTP API over PostgreSQL, deployed to Render |
| `mobile-game-godot` | mobile-game | Games built with the Godot engine for Android and iPhone |
| `mobile-react-native` | mobile-app | A React Native app for Android, iOS or both, tested with Jest and Maestro, with the Android host toolchain set up by a skill |
| `portfolio` | portfolio | A personal or studio portfolio built with Astro and deployed to Vercel |
| `prototype` | prototype | A Flask + SQLite prototype on Railway, with process ceremony matched to how far the idea has come |
| `saas` | saas | An Astro front end over a Flask API and PostgreSQL, deployed to Vercel |
| `static-site` | static-site | A static Astro site deployed to Vercel |

The `tcat.json.gz` of the newest release is the authoritative list, with each template's version.

## Release assets

Every release carries:

| Asset | What it is |
|---|---|
| `tcat.json.gz` | The template catalog (TCAT): one entry per template, with its display name, description, version and the name and SHA-256 of its package |
| `tmpl-<id>-<version>.json.gz` | One template package (TMPL) per template: its manifest and every file it writes into a new project |

Both are gzip-compressed JSON. The release notes list what changed in that release.

## How Praxis Hub Manager uses them

1. PHM reads the **newest release**: the highest semver version among releases that are not drafts.
2. It checks whether its cached catalog is current. If the release tag is unchanged, nothing is downloaded. Otherwise it downloads `tcat.json.gz` and compares its `contentHash` with the cached one.
3. When you choose a template, PHM downloads the TMPL asset the catalog names and checks its SHA-256 against the catalog entry. It then writes the template's files into the new project. A template is used whole or not at all.

The full contract is in [`docs/catalog-format.md`](https://github.com/rubrical-works/idpf-phm-project-templates/blob/main/docs/catalog-format.md), including the formats, freshness rules and the error codes a consumer reports. The template package format is in [`docs/template-format.md`](https://github.com/rubrical-works/idpf-phm-project-templates/blob/main/docs/template-format.md).

## Pre-release templates

Every release here is a production release; there is no separate pre-release channel. A template that is still being proven has a semver pre-release version, such as `0.1.0-beta`. PHM lists it with a **"Pre-release"** label. It is not hidden, so you can see the label and decide. When the template is proven, a later release drops the suffix (`0.1.0-beta` → `0.1.0`) and the label goes away.

## Issues

Report a problem with a template or the catalog in [`rubrical-works/idpf-phm-project-templates`](https://github.com/rubrical-works/idpf-phm-project-templates/issues). This README and the releases are written by each publish, so changes made here directly are overwritten.

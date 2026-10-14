# portside-catalog

The published game-port catalog for [Portside](https://erickbarrera.github.io/portside-catalog/v1/index.json),
a launcher for community game ports (decompilations, recompilations, source ports and engine remakes).

This repository holds no code. The `gh-pages` branch carries the generated JSON files, served by
GitHub Pages at `https://erickbarrera.github.io/portside-catalog/`. A scheduled job rebuilds them every
hour from [awesome-decomp-games](https://github.com/SubmitGame/awesome-decomp-games), Portside's port
manifests and each port's GitHub releases, and replaces the branch with a single commit.

## Files
All under `v1/`:

| Path | What it is |
|---|---|
| `v1/index.json` | Catalog revision, build time, port count and content hash |
| `v1/snapshot.json` | Summary of every port (search and listing) |
| `v1/ports/{id}.json` | One port: upstream details, install manifest, latest releases |
| `v1/ports/{id}/releases.json` | The port's recent releases and their download files |
| `v1/games/{game_key}.json` | One game and the ports of it |

Clients poll `v1/snapshot.json` with `If-None-Match`; a 304 means nothing changed.

## What it doesn't contain
No game files, ROMs, disc images or links to them. Every port needs files from the player's own
copy of the game; each port's `status_notes` says which. Downloads point only at the port
projects' own GitHub releases.

## Problems
Wrong install data or a port that should be listed? Open an issue here. Edits to the files
themselves are overwritten by the next build, so pull requests can't be merged.

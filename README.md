# tern-plugin-base

a copyable foundation for tern plugins: package, config, and dev commands. the example logs a greeting on load.

## start

copy or clone this folder. replace `tern-plugin-base` everywhere with your plugin id, replace the example with your feature, and update this readme and `manifest.md`. put your name in `LICENSE`, or pick another license.

```sh
just link
```

tern loads the checkout directly and reloads when package files change.

## config

defaults live at the top of `host.luau`. to change them without editing code, create `config.json` in the plugin's data folder:

- macos: `~/Library/Application Support/Tern/plugin-data/tern-plugin-base/config.json`
- linux: `$XDG_STATE_HOME/tern/plugin-data/tern-plugin-base/config.json` (default `~/.local/state/tern/...`)
- windows: `%LOCALAPPDATA%\Tern\plugin-data\tern-plugin-base\config.json`
- with `TERN_CONFIG_DIR` set: `$TERN_CONFIG_DIR/plugin-data/tern-plugin-base/config.json`

example:

```json
{ "greeting": "hi" }
```

missing file or key -> default. reinstall and update keep the file. after editing, run `tern plugin reload`.

## develop

install `tern`, `just`, lua, `luau-lsp`, and `stylua` with luau support. run `just` for available commands.

```sh
just test
just lint
just fmt
```

no tests are included yet. lint generates current tern api types and checks plugin source; format covers lua/luau files. generated types are not committed.

`just bump` bumps patch; `just bump minor` and `just bump major` pick another part. only `plugin.toml` holds the version.

## publish

keep `plugin.toml` at the repository root. users install with:

```sh
tern plugin install github.com/OWNER/REPO
```

use `tern plugin install .` for a local copy, and `--force` to update an installed copy. users only need tern.

## agent files

optional, for plugins written mostly by ai coding agents. delete them if you do not need them.

- `AGENTS.md`: agent rules. points to the manifest, tern docs, and api types
- `manifest.md`: the shortest spec of the plugin: purpose, parts, key decisions. a human writes and approves it; agents check their work against it and ask before they change its core

## license

mit-0: use, copy, and change freely. no need to keep the author name.

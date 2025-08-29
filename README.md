# deploio-cli (deploio / depl)

A tiny single-file Ruby wrapper around [`nctl`](https://github.com/ninech/nctl) to make common app operations concise. The CLI is named `deploio` with shorthand `depl`.

## Requirements

- nctl version 1.10.0 or higher (with JSON output support)
- bash

## Install

```zsh
curl -fsSL https://raw.githubusercontent.com/CuddlyBunion341/deploio-cli/main/setup | zsh
```

If `~/.local/bin` isn’t on your PATH, add this to `~/.zshrc`:
```sh
export PATH="$HOME/.local/bin:$PATH"
```

## Usage

```sh
deploio (deplo.io app CLI)

Usage:
  deploio <command> [args]

Commands:
  new <project-env>                    Create project and app (git url inferred)
  list                                 List apps as <project>-<env>
  logs <project-env> [-- ...args]      Stream logs for app
  exec <project-env> [-- ...args]      Exec into app
  stats <project-env>                  Show app stats
  config <project-env>                 Show app config (yaml)
  config:edit <project-env>            Edit app config
  hosts <project-env>                  Print app hosts

Global flags (before command):
  --org-prefix <prefix>                Default: renuo
  --dry-run                            Print commands without executing
```

## Features

- **Shorthand alias**: Use `depl` instead of `deploio` for faster typing
- **Git URL inference**: Automatically constructs GitHub URLs from project names
- **Auto project creation**: Creates projects if they don't exist when running `new`
- **Dry-run mode**: Preview commands with `--dry-run` without executing them
- **Smart validation**: Validates project-env exists before running commands
- **Command and project-env typo suggestions** via `did_you_mean`
- **Contextual help**: Run `deploio <command> --help` for command-specific help
- **Single file**: Zero dependencies beyond Ruby stdlib and `did_you_mean`

Examples:
```sh
deploio new fizzbuzz-main
depl logs fizzbuzz-main
deploio exec fizzbuzz-main -- -c 'echo hi'
```

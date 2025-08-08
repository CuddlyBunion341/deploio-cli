# deploio-cli (dapp)

A tiny single-file Ruby wrapper around `nctl` to make common app operations concise. “dapp” stands for deplo.io app CLI.

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
dapp (deplo.io app CLI)

Usage:
  dapp <command> [args]

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

Examples:
```sh
dapp new fizzbuzz-main
dapp logs fizzbuzz-main
dapp exec fizzbuzz-main -- -c 'echo hi'
```

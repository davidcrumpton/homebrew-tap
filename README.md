# Homebrew Tap — davidcrumpton

```sh
brew install davidcrumpton/tap/mcwsd
```

## llmctrlx

[`llmctrlx`](https://github.com/davidcrumpton/llm-control-engine) is a local LLM
orchestration and execution CLI with tool and plugin support.

```sh
brew install davidcrumpton/tap/llmctrlx
```

The binary is self-contained and does not need Node.js. Bundled tools and plugins
are installed under `$(brew --prefix)/share/llmctrlx` but are **not** loaded by
default — point the CLI at them:

```sh
export LLMCTRLX_TOOLS_DIR="$(brew --prefix)/share/llmctrlx/tools"
export LLMCTRLX_PLUGINS_DIR="$(brew --prefix)/share/llmctrlx/plugins"
```

Upgrade with `brew upgrade llmctrlx`.

## mcwsd

[`mcwsd`](https://github.com/davidcrumpton/mcwsd) is a workspace daemon that
provisions throwaway development environments for coding agents (Docker,
Podman, Apple container, Kubernetes, FreeBSD jails, OpenBSD vmd, illumos zones,
Proxmox LXC, NetBSD accounts) behind a small HTTP API.

After installing, the runtime plugins live in `$(brew --prefix)/share/mcwsd/plugins`.
The daemon needs one explicitly:

```sh
mcwsd token   # generate a client token, then export MCWSD_TOKEN=...
mcwsd daemon --plugin "$(brew --prefix)/share/mcwsd/plugins/docker.js" \
  --workspace-auth-mode=scoped --port 9080
```

Upgrade with `brew upgrade mcwsd`.

## Maintenance

Formulae in `Formula/` are **generated automatically**, each by the release
workflow of its own project:

- `mcwsd.rb`, `mcphe.rb`, `tokenmgr.rb` — by GoReleaser from
  [davidcrumpton/mcwsd](https://github.com/davidcrumpton/mcwsd) and its siblings.
- `llmctrlx.rb` — rendered from `homebrew/llmctrlx.rb.template` by
  [llm-control-engine](https://github.com/davidcrumpton/llm-control-engine)'s
  release workflow, using the checksums published with each release.

Do not edit them by hand — changes are overwritten on the next release. Issues
and pull requests belong in the respective project repository.

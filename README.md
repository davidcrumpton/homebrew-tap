# Homebrew Tap — davidcrumpton

```sh
brew install davidcrumpton/tap/mcwsd
```

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

Formulae in `Formula/` are **generated automatically** by GoReleaser from the
release workflow in [davidcrumpton/mcwsd](https://github.com/davidcrumpton/mcwsd).
Do not edit them by hand — changes are overwritten on the next release. Issues
and pull requests belong in the mcwsd repository.

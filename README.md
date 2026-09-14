# ditto_nh

Native NostrHost (`_nh`) package for [Ditto](https://ditto.pub)
([source](https://gitlab.com/soapbox-pub/ditto)), a Nostr client SPA.
Scriptless — see [docs/security-model.md](docs/security-model.md) for why
`[source.main]` points at a pre-built artifact instead of building at
install time.

Built from [imattau/nh-package-template](https://github.com/imattau/nh-package-template).
An AI coding agent working in this repo should read [`AGENTS.md`](AGENTS.md)
first; for a human, see [docs/new-package.md](docs/new-package.md).

Companion classic package: [ditto_ynh](https://github.com/imattau/ditto_ynh)
(builds with `npm run build` at install time).

## Installing

```sh
nostrhost app install ditto --source . --domain <your-domain>
```

`[web].domain` isn't in `package.toml` — it's supplied at install time (see
`AGENTS.md`'s "Install-time domain/path"). Proven working on the
`nostrhost-clean7` test VM.

## Bumping to a new Ditto version

1. Actions → "Build and publish artifact" → Run workflow, `upstream_ref` =
   the new Ditto tag (e.g. `v2.38.0`).
2. Copy the printed release URL + SHA-256 from the job summary into
   `package.toml`'s `[source.main]`; bump `[app].version` to match.
3. Open a PR — `security.yml` validates the manifest and re-verifies the
   artifact hash.

# ditto_nh

Native NostrHost (`_nh`) package for [Ditto](https://ditto.pub)
([source](https://gitlab.com/soapbox-pub/ditto)), a Nostr client SPA.
Scriptless — see [docs/security-model.md](docs/security-model.md) for why
`[source.main]` points at a pre-built artifact instead of building at
install time.

Built from [imattau/nh-package-template](https://github.com/imattau/nh-package-template);
see that repo's `docs/new-package.md` for the general shape and
[docs/new-package.md](docs/new-package.md) here for anything ditto-specific.

Companion classic package: [ditto_ynh](https://github.com/imattau/ditto_ynh)
(builds with `npm run build` at install time).

## Bumping to a new Ditto version

1. Actions → "Build and publish artifact" → Run workflow, `upstream_ref` =
   the new Ditto tag (e.g. `v2.38.0`).
2. Copy the printed release URL + SHA-256 from the job summary into
   `package.toml`'s `[source.main]`; bump `[app].version` to match.
3. Open a PR — `security.yml` validates the manifest and re-verifies the
   artifact hash.

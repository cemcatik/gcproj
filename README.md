# gcproj - GCP Project Switcher

This repository provides `gcproj` script that lets you quickly see all GCP
projects and switch between them. Heavily influenced by [`kubectx`](https://github.com/ahmetb/kubectx).

## Requirements

- `gcloud` is installed
- User is authenticated with any GCP project `gcloud auth`
- _Optional:_ `fzf` for fuzzy-finding and interactive mode

## Usage

### List projects `gcproj`

List all projects available for your current account. Just runs
`gcloud projects list`.

```bash
$ gcproj
PROJECT_ID                      NAME                            PROJECT_NUMBER
foo-1234                        foo                             123456789
bar-5678                        bar                             567891234
```

### Switch `gcloud` projects

Runs `gcloud config set project` for the specified project. It will output any
messages that comes from `gcloud config set project` command as is.

```bash
$ gcproj foo-1234
Updated property [core/project].
```

### Caching

Getting the list of projects, even for accounts with a small list of projects,
takes significant amount of time. In order to help with startup times, `gcproj`
caches the list of projects. By default, the cache is refreshed once a day.

The cache is stored in `$XDG_CACHE_HOME/gcproj/projects` file. If `$XDG_CACHE_HOME`
is not defined, then the cache is stored in `$HOME/.cache/gcproj/projects`.

The projects list is refreshed if the cache is stale. By default, the cache is
valid for 1 day. The cache TTL can be configured with the `$GCPROJ_CACHE_TTL`,
environment variable. The value of `$GCPROJ_CACHE_TTL` is in seconds, defaults
to 1 day, aka `86400` seconds.

The cache can be refreshed with the `--refresh` flag.

## Installation

Incldue `gcproj` in your `$PATH`.

## Interactive

If you have [`fzf`](https://github.com/junegunn/fzf) installed, you can
interactively select a project or fuzzy-search.

## Future

- [ ] bash completion
- [ ] zsh completion
- [ ] Add gif for fzf/interactive mode to README
- [ ] Switch to previous project `gcproj -`
- [ ] Ignore `fzf`
- [ ] CI and automate linting etc
- [x] ~~Cache list of projects to improve startup time~~

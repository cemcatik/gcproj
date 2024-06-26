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

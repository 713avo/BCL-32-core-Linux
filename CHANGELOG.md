# Changelog

Format based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added
- First public repository: the `bcl` interpreter for Linux, man page (English and
  Spanish), examples and the language manual (English and Spanish).

## [1.2] — 2026-11

### Added
- `INCR var [delta]`: the increment may be negative or decimal.
- System variable `BCL_LIBS`: modules are found by name in a comma-separated list of
  directories (first match wins).
- Startup file `$HOME/.bcl.rc`; options `--no-rc` and `--version`; every version has a
  build number (`bcl --version` prints `BCL-32 v1.2 build N`).

### Changed
- License: GPL-3.0-or-later.

## [1.1] — 2026-08

- Version prior to this repository.

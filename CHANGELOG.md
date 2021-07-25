# Changelog

## v0.1.1 2021-07-25

- support/workaround for Rocky os_family bug
- CI: support for ubuntu 21.04
- CI: fixed race condition when fetching files

## v0.1.0 2021-05-19

- added a tls_file_layout cert+chain
- CI improvements, updates for molecule and ansible-lint

### Added

- tls_file_layouts config variable

### Changes to CI

- use default working-dir for run steps
- run on ubuntu 20.04
- use actions/checkout@v2

## v0.0.5

### Added

- specify mode options because of ansible-lint and CVE-2020-1736)
- CHANGELOG

### Changes

- bug fixes

# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## Unreleased

- DEP: add a missing pin for `colorama==0.4.6` (Windows only, via `click`)
- DEP: bump `inifix-cli` (1.0.0 -> 1.1.0)

## [1.0.0] 2026-05-18

`inifix-pre-commit` is now published to GitHub independently from `inifix`'s historical
repository.
CPython versions from 3.11 to 3.15 are supported.

This version's entire dependency tree is as follow
- `inifix==7.0.0`
- `click==8.3.3`
- `flit-core==3.12.0` (build time)

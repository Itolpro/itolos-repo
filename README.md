# ItolOS Repository

Core package definitions and system profiles for ItolOS.

## Base system

`itolos-base` describes the minimum usable ItolOS installation.

The base profile requires:

- filesystem
- libc
- shell and core utilities
- init/service manager
- networking
- authentication
- Linux kernel and firmware
- SLM

SLM is responsible for resolving compatible implementations from configured
sources, rebuilding packages where appropriate, and preserving ItolOS system
invariants.

## Build repository

When supported by the installed SLM version:

    slm repo build .

## Bootstrap

Example:

    slm bootstrap /mnt/itolos itolos-base --sources ./sources.json

The repository includes a persistent `sources.json` for image builds. It
points to the public native repository on GitHub and Arch core/extra. The
native repository is served directly from the `repo/` directory through
GitHub's raw-content endpoint; no separate package server is required.

For a local development checkout, replace the native URL with a `file://`
URL or pass a separate sources file. Do not put this file under `/tmp`: it is
needed again after a reboot.

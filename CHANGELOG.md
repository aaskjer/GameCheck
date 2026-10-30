# Changelog

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Changed

- **Free Game Check and Game Sale Check are one project.** The code both actions share (Discord, HTTP, arguments,
  state, stores, platforms) is kept once and built into both scripts. Nothing changes for an install: the same
  arguments, the same global variables, the same messages.

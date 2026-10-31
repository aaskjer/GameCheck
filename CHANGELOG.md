# Changelog

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

- **An import.** `GameCheck.sb` and the [import string](Import-String.md) set up all three actions at once, triggers
  included, with no secrets and no settings in them. Every reference holds wherever Streamer.bot is installed.
- **A logo**, also in the settings window's About page.
- **A settings window.** The action "GameCheck - Settings" opens a window in the style of the Chat Games for both
  actions: Discord, what is posted, timing, platforms and colours. It writes `GameCheck-Settings.json` in the folder
  `GameCheck` next to Streamer.bot, and the bot token, webhook URL and IsThereAnyDeal key into the persisted global
  variables, so an export carries no secrets. A Set Argument value in an action still wins; the window shows such a
  setting locked. Installs without the window keep working on their Set Argument values.
- **`launcherLinks`** (default off): Steam and Epic games and deals open in Steam or the Epic Games Launcher instead
  of the browser. Discord opens only web links, so the link goes through a small page on aaskjer.github.io that
  hands it on, with the store's web page as a fallback.

### Changed

- **Free Game Check and Game Sale Check are one project.** The code both actions share (Discord, HTTP, arguments,
  state, stores, platforms) is kept once and built into both scripts. Nothing changes for an install: the same
  arguments, the same global variables, the same messages.

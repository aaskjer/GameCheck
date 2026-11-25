# Changelog

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [2.1.1] - 2026-11-25

### Fixed

- **The settings window opened by itself every hour, and the checks stopped.** After *Check now* on the Status
  page, Free Game Check and Game Sale Check took the settings action's ID for their own (Streamer.bot hands it on
  to the run it starts) and planned their next runs for that one. *Check now* now hands the action its own ID and
  never starts the settings action. Free Game Check removes such a planned run the next time the window opens; the
  log says so with a warning.

To update, import the new version over the old one, then press *Check now* for both actions on the Status page
once (or restart Streamer.bot), so they plan their own runs again.

## [2.1.0] - 2026-11-25

### Added

- **A Log page in the settings window.** It shows what the two checks and the window wrote into Streamer.bot's
  log, newest first: which store answered, what was posted, what failed and why. With a search, a filter by level
  (`ERR`, `WRN`, `INF`) and by source (`FreeGames`, `GameSales`, the settings window), and the day to pick. It
  follows the log while the checks run. Before, those lines had to be looked up in Streamer.bot's own log window.

### Changed

- **The window needs UIFramework 2.3.0.** With an older one installed, the settings action offers the update when
  the window is opened.

## [2.0.0] - 2026-11-22

The settings window is now built with [UIFramework for streamer.bot](https://github.com/aaskjer/UIFramework-Streamer.bot),
the window the Chat Games use. It looks and works like the window before and brings what that framework has. What
the two checks post has not changed.

To update, import the new version over the old one: the three actions are replaced, the settings file and the
secrets stay. The first time the window opens, a dialog asks whether to download `UIFramework.dll`; click `Yes`.

### Added

- **The header says `off`** for an action whose every topic is switched off, next to `bot`, `webhook` and
  `not set up` as before.
- **The country is picked from a list** of all countries instead of typed as a two-letter code.
- **The Status page follows the actions by itself.** It asks again every ten seconds while it is open; the
  *Refresh* button is gone.
- **Your own layout.** The pen in the footer lets you rename, move and hide fields and pages. It is kept in
  `uiframework.layout.json` beside the settings and survives every import.
- **Updates of the window.** UIFramework checks for a newer version of itself when the window opens and asks
  before it downloads one.

### Changed

- **`[CG] - Settings` is UIFramework's settings action.** It needs four references instead of eight and carries
  no window of its own: the window is `UIFramework.dll` in the folder `UIFramework` next to Streamer.bot,
  downloaded once on the first open. The action finds Free Game Check by its ID; by its name only in an install
  made by hand.
- **The settings file has one key per setting** (`freeCountry`, `salesDealLimit`) instead of a section per action.
  The window moves the old values with its first save, and both actions read either form: nothing is lost and
  nothing has to be done.
- **"Both actions use the same bot and channel" is a setting now.** While it is on, Game Sale Check posts with the
  bot, channel or webhook of Free Game Check; before, the window kept two copies alike. It starts on while both
  connections are the same, as it did.
- **A setting held by a Set Argument is shown locked, without its value.** The window before filled its fields
  with the Set Argument values on its first open; this one does not. To manage such a setting in the window,
  remove its Set Argument, run the action once and set the value in the window.
- **Min. discount is 1 to 99 %**, the range the action has always kept to; the window allowed 0 to 100.
- A pasted channel link is turned into the channel ID when the action reads it, not while it is typed.

### Removed

- **The check of a webhook URL's shape before saving.** The window hands a secret to the action only as set or
  not set, never as its value.

## [1.0.1] - 2026-11-02

### Changed

- **One footer for every embed: "GameCheck by aaskjer · updated".** The time after it is the embed's last update -
  both actions edit their messages in place on every run - and the footer now says so instead of reading like the
  time the message was sent. The actions' own names ("FreeGamesCheck", "GameSaleCheck") are gone from it.

## [1.0.0] - 2026-10-31

The first release of GameCheck: Free Game Check and Game Sale Check as one project, with a settings window and an
import that sets everything up at once.

### Added

- **An import.** `GameCheck.sb` and the [import string](Import-String.md) set up all three actions at once, triggers
  included, with no secrets and no settings in them. Every reference holds wherever Streamer.bot is installed.
- **A logo**, also in the settings window's About page.
- **A settings window.** The action "[CG] - Settings" opens a window in the style of the Chat Games for both
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
- **🆕 and 🔥 lead the line in both actions.** Game Sale Check showed 🔥 in place of ⏳ before the end and 🆕 after
  a sale's name; now they come first, as in Free Game Check, and the end always keeps its ⏳.

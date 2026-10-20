# BetterDiscord Message Logger Reworked

A reworked version of **MessageLoggerV2**, patched to work with modern BetterDiscord releases. (i'll probably update this repo if a new BD/Discord update breaks it)

## Overview

Original versions of MessageLoggerV2 and its companion libraries relied on legacy `BdApi` methods (`BdApi.findModuleByProps`, `BdApi.isSettingEnabled`, `BdApi.alert`, `BdApi.getData`, etc.) that were removed in more or less recent BetterDiscord updates, causing the plugins to crash on startup.

This repository provides updated versions of **MessageLoggerV2**, **XenoLib**, and **ZeresPluginLibrary** migrated to use the current namespaced BetterDiscord API (`BdApi.Webpack`, `BdApi.UI`, `BdApi.Data`, and `BdApi.Plugins`).

---

## Features

- **Deleted Message Logging**: Keeps track of deleted messages in channels and direct messages.
- **Edit History**: View previous versions of edited messages.
- **Ghost Ping Detection**: Alerts and logs when someone pings you and deletes their message.
- **Bulk Delete / Purge Logging**: Retains messages removed during bulk bot purges.
- **Offline Persistence**: Retains cached deleted messages across Discord restarts.

---

## Included Files

- `0PluginLibrary.plugin.js` - ZeresPluginLibrary patched to remove deprecated toast suppression setting calls on initialization.
- `1XenoLib.plugin.js` - XenoLib updated to use `BdApi.Data` and `BdApi.UI` methods, removing defunct client-mod checks that blocked dependent reloads.
- `MessageLoggerV2.plugin.js` - Core plugin with all Webpack lookup calls, UI dialogs, notifications, and data persistence migrated to modern namespaced APIs.

---

## Installation

1. Download this repository.
2. Copy the three `.plugin.js` files:
   - `0PluginLibrary.plugin.js`
   - `1XenoLib.plugin.js`
   - `MessageLoggerV2.plugin.js`
3. Paste them into your BetterDiscord plugins directory:
   - **Windows**: `%APPDATA%\BetterDiscord\plugins`
   - **macOS**: `~/Library/Application Support/BetterDiscord/plugins`
   - **Linux**: `~/.config/BetterDiscord/plugins`
4. Reload Discord (`Ctrl + R` on Windows/Linux, `Cmd + R` on macOS).
5. Open **Discord Settings -> Plugins** and enable them in this order:
   1. **ZeresPluginLibrary**
   2. **XenoLib**
   3. **MessageLoggerV2**
6. Dismiss the "delete now" popup

---

## Important Notes & Known Limitations

- **Discord Client Updates**: MessageLoggerV2 relies on Discord's internal Flux dispatcher and React component structures. Future Discord updates may require adjustments to internal module selectors.
- **Settings Data**: Do not overwrite or commit `MessageLoggerV2.config.json` if you already have existing logged message history.

---

## Credits

- **Lighty** - https://github.com/1Lighty - Original author of MessageLoggerV2 and XenoLib.
- **Zerebos** - https://github.com/zerebos - Original author of ZeresPluginLibrary (BDPluginLibrary).

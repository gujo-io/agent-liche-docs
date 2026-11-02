# Updating

[Guide home](../README.md) · [한국어](../../docs/updates.md)

Liche tells you when a new version is available, but does not download or install the app automatically. Get updates yourself from the store or Gujo Cloud Apps.

## New version notifications

- Enabled by default. Checks a small version information file on GitHub once a day. Also checks when you open **리체 정보** (About Liche), up to once every 10 minutes.
- When a new version is available, **리체 설정 › 리체 정보** (Liche Settings › About Liche) shows **새 버전이 있어요** (A new version is available), **바뀐 점 ›** (What's changed ›), and **받으러 가기 ›** (Go to download ›). **새 버전이 있어요** also appears below About Liche in the sidebar.
- To disable this, turn off **리체 설정 › 리체 정보 › 업데이트 › 새 버전 알림** (Liche Settings › About Liche › Updates › New version notifications). The version information file is not fetched when disabled.
- A failed check opens no window and sends no notification. Only while no answer has been received yet, the **새 버전 알림** row reads "확인하지 못했어요. 인터넷 연결을 확인해 주세요." (Could not check. Please check your internet connection.), and the next check tries again.
- This check sends your IP address to GitHub (`raw.githubusercontent.com`). It does not send conversations, account information, or device identifiers. See [Privacy and data](privacy.md).

## How long you can receive updates

- You can receive new versions released within 365 days of purchase.
- After that period ends, you can continue using and re-downloading versions released during your update period.
- Windows and macOS (Apple Silicon) releases are part of the same product.

The exact conditions follow the [store product page](https://asset.gujo.io/products/287?lang=en), [End User License Agreement (EULA, Korean)](../../legal/eula.md), and [Gujo Terms of Service](https://account.gujo.io/en/terms).

## Checking your current version

Find the version and build information under **리체 설정 › 리체 정보**. Include this information when contacting support.

| 0.2.0 | Version line in About Liche | Build number |
| --- | --- | --- |
| macOS | `버전 0.2.0 (2026.11.02 · a2b5fea)` | `2026.1102.0834` (Finder's Get Info, About Agent Liche in the app menu) |
| Windows | `버전 0.2.0 (2026.11.02 · a2b5fea)` | `2026.1102.0830` |

## Updating on Windows

1. Quit Liche first. Do not leave the old and new versions running together.
2. Download the new zip from your store library, or update through Gujo Cloud Apps.
3. If using a zip, extract it into a new folder instead of overwriting the old one.
4. Run `AgentLiche.exe` at the top of the extracted package. Keep the `AgentLiche` folder beside it.
5. If you used **컴퓨터를 켜면 리체도 시작** (Start Liche when the computer starts), turn it off and back on under **리체 설정 › 일반** (Liche Settings › General). This updates the startup item to the new executable's location.
6. Check that the new version opens correctly, then delete the old program folder.

## Updating on macOS

1. Download and extract the new macOS zip.
2. Right-click the Agent Liche icon in the Dock and choose **종료** (Quit).
3. Replace `Agent Liche.app` in Applications with the new app. If Finder asks, click **Replace**.
4. Open the new app. Starting with 0.2.0, Developer ID signing lets notification and keychain permissions carry over to later versions. When you first switch to 0.2.0, macOS may ask once more. Check the request before responding.

## 0.2.0 starts like a fresh installation

Version 0.2.0 changes the app name and internal folder names. When switching from an earlier version, **settings, chat history, card position, and agent connections all start empty.**

- Reconnect your agent through first-run setup.
- Settings and card position return to defaults.
- Everyday and Work chat histories start fresh.
- Old data is not deleted or moved. It stays in the old folders, which the new version does not read.
- Register any Liche MCP server or taskbar pin that used an old path again with the new path. The new paths are `<extracted folder>\AgentLiche\Binaries\Win64\LicheInput.exe` on Windows and `/Applications/Agent Liche.app/Contents/UE/AgentLiche/Binaries/Mac/LicheInput.app/Contents/MacOS/LicheInput` on macOS (register with `--mcp`).
- On its first launch, 0.2.0 creates default guides in the new guide folder. To use your old guides, copy them yourself as described below.

### Cleaning up old folders

Quit both the old and new versions first. Copy any chat history and files you created that you need elsewhere, then delete the folders. **Deleted data cannot be recovered.**

| Platform | Old folder | Contents |
| --- | --- | --- |
| Windows | `%LOCALAPPDATA%\LizeWidget` | Old chat history, connections, settings, and card position |
| Windows | `Documents\LizeWidget` | Old widget settings |
| Windows | `Documents\Lize` | Old guides and agent working files |
| macOS | `~/Library/Application Support/LizeWidget` | Old chat history, connections, and settings |
| macOS | `~/Library/Application Support/Epic/LizeWidget` | Old card position and size |
| macOS | `~/Documents/LizeWidget` | Old widget settings may remain here |
| macOS | `~/Documents/Lize` | Old guides and agent working files |

**Windows:** Press `Win+R`, enter `%LOCALAPPDATA%`, and delete the `LizeWidget` folder inside. Also check and delete `LizeWidget` and `Lize` under **문서** (Documents) on the left side of File Explorer. If OneDrive backs up Documents, check its Documents folder.

**macOS:** In Finder, press `⌘⇧G` and paste each path above. If the folder exists, check for files you need, then move it to the Trash. If the path does not exist, skip it.

Old program folders and engine logs and temporary files may also remain. On Windows, deleting the entire old package folder also removes its `Saved` folder. For engine data left separately in your user folder, look under `%LOCALAPPDATA%` for a folder named **after the old executable without its extension**, and delete it. On macOS, check `~/Library/Application Support/Epic` and `~/Library/Logs` for folders with **the same name as the executable inside the old app**, and delete them. Do not delete `LicheWidget` or `AgentLiche` when cleaning old folders: the new version uses those names.

To keep using old guides, copy the files you need from `Documents\Lize` to `Documents\Liche` on Windows, or from `~/Documents/Lize` to `~/Liche` on macOS. The new folder may already have the 0.2.0 default guides. Compare contents before deciding whether to overwrite. Liche does not restore default content over files you replace ([Guide files](guides.md#default-guides)).

## Changes

See the [Changelog](../CHANGELOG.md) for changes by version.

# Installing and uninstalling on macOS

[Guide home](../README.md) · [한국어](../../docs/install-mac.md)

## What you need

- **Only Apple Silicon (M1 or later) Macs are supported. Intel Macs are not supported.**
- macOS 14 or later. Pre-release testing used macOS 26 and 27.
- No minimum CPU or memory requirements are specified. On laptops, we recommend **절약** (Power saving) under **리체 설정 › 성능** (Liche Settings › Performance).
- At least 1.5 GB of free space for both the downloaded zip and the extracted app.
- An AI agent installed and signed in separately. See [Connecting an agent](agents.md).

## 1. Downloading

Sign in to the Gujo store and download the macOS zip (`Agent-Liche-0.2.0-mac.zip`) from your library. Double-click it in Finder to extract **`Agent Liche.app`**. The same product purchase includes both Windows and macOS files.

If you extract it with another archive app or the `unzip` command, a `__MACOSX` folder may appear next to the app. It only holds information macOS attached to the files, so you can delete it. Double-clicking in Finder (Archive Utility) does not create it.

### Checking your download (optional)

| File | Size (bytes) | SHA-256 |
| --- | --- | --- |
| `Agent-Liche-0.2.0-mac.zip` | `516,489,609` | `bd71fad86976b74c50951f5c87a7052f6df142d6e131661d8d77ec3c925f5ac1` |

Run this command in Terminal to get its SHA-256 (change the path if you saved it elsewhere). If it differs from the table, do not open the app. Contact support.

```sh
shasum -a 256 ~/Downloads/Agent-Liche-0.2.0-mac.zip
```

## 2. Moving to Applications

In Finder, drag `Agent Liche.app` to **Applications**. This keeps it in a consistent location for automatic startup and updates. After moving it, you can delete the zip from Downloads.

## 3. Opening for the first time

1. Double-click **Agent Liche** in Applications.
2. A confirmation says that Agent Liche was downloaded from the Internet. Read the [Gatekeeper guidance](#gatekeeper-confirmation) below, then click **Open**.
3. Connect an agent by following [First run](first-run.md). Liche's replies come from the connected AI agent.

### Gatekeeper confirmation

**The 0.2.0 macOS release is signed with Apple Developer ID and notarized by Apple.** On first launch, macOS Gatekeeper therefore shows only the usual confirmation: "“Agent Liche” is an app downloaded from the Internet. Are you sure you want to open it?" It also says, "Apple checked it for malicious software and none was detected." Click **Open**. This confirmation appears only the first time.

If you see either warning below, the file may not be the correct one. Do not open it. Send support the wording and where you downloaded it.

- A warning that the developer cannot be verified, or that Apple cannot check it for malicious software
- A warning that the app is damaged

Do not disable security features or bypass checks with commands such as `xattr`. A notarized app does not need this.

## 4. Permissions macOS may request

Liche itself does not request Screen Recording, Accessibility, Input Monitoring, or Documents folder permission at startup. Its guide folder is also in your home folder (`~/Liche`), which needs no permission.

| Request | When it appears and how to respond |
| --- | --- |
| Agent Liche notifications | Asked when Liche first sends a notification. Choose **Allow** to receive notifications. Change this later under **System Settings › Notifications › Agent Liche** |
| Keychain access for `liche-judge` | May appear when saving or reading a JEV key. Check that the requesting program is `liche-judge`, then choose **허용** or **항상 허용** (Always Allow). Starting with the signed 0.2.0 release, future versions from the same developer reuse this permission |
| Permissions for the connected agent | Requests such as Documents folder access come from that agent. Check the request and the program before responding |

## 5. Starting automatically at login

1. Turn on **리체 설정 › 일반 › 컴퓨터를 켜면 리체도 시작** (Liche Settings › General › Start Liche when the computer starts).
2. If a notice says approval is needed in Login Items, click **시스템 설정 열기 ›** (Open System Settings ›) and allow Agent Liche under **General › Login Items**. Depending on your macOS version, the page may be called **Login Items & Extensions**.
3. You are done when **macOS 로그인 항목에 켜져 있어요.** (Enabled in macOS Login Items.) appears.

If **macOS가 이 앱을 찾지 못했어요.** (macOS could not find this app.) appears, move `Agent Liche.app` to Applications, then turn the switch off and on again. Turn the same switch off to disable automatic startup.

## 6. Quitting

Right-click the Agent Liche icon in the Dock and choose **종료** (Quit). You can also press `⌘Q` when Agent Liche is the active app. The chat window quits too.

## 7. Uninstalling

1. While Liche is running, turn off **컴퓨터를 켜면 리체도 시작** (Start Liche when the computer starts).
2. If you used JEV, click **키 지우기** (Delete key) in the key window. If you already deleted the app, follow [Deleting the keychain item](#deleting-the-keychain-item) below.
3. Quit Liche and move `Agent Liche.app` from Applications to the Trash.
4. Copy any files you need first. In Finder, use `⌘⇧G` to open and delete each path below. Skip folders that do not exist. **Deleted conversations and files you created cannot be recovered.**
5. If a login item remains, also remove it under **System Settings › General › Login Items**.

| Location | Contents |
| --- | --- |
| `~/Library/Application Support/LicheWidget` | Chat history and attachments, saved connection, widget settings `settings.json`, display/notification/performance settings, JEV status, and logs |
| `~/Library/Application Support/Epic/LicheWidget` | Card position, size, and pin state |
| `~/Liche` | Guide files (`common.md`, `daily/daily.md`, `developer/developer.md`) and per-mode agent working folders. Check for files you created first |
| `~/Library/Application Support/Epic/AgentLiche/Saved` | Unreal Engine settings and caches |
| `~/Library/Logs/AgentLiche` | Engine log folder |
| `AgentLiche-…`, `LicheInput-…` in `~/Library/Logs/DiagnosticReports` | Any crash reports recorded by macOS |
| `com.agentliche.jev` in the login keychain | JEV key |
| `Liche-diagnostics-….zip` on your desktop | Any files made with **진단 파일 만들기** (Create diagnostic file) |

Files that macOS creates for each app may also remain. In `~/Library/Preferences`, `~/Library/Caches`, and `~/Library/Saved Application State`, delete any items whose names begin with `com.agentliche.`.

### Deleting the keychain item

1. Search for **Keychain Access** in Spotlight and open it.
2. Select the **로그인** (login) keychain and search for `com.agentliche.jev`.
3. Right-click the item and choose **삭제** (Delete).

Clean up old-version folders separately by following [Updating](updates.md#cleaning-up-old-folders). The connected agent is separate from Liche. Deleting the app leaves that program and its data in place.

## Next steps

- [First run](first-run.md)
- [Connecting an agent](agents.md)
- [Troubleshooting](troubleshooting.md)

# Changelog

[Guide home](README.md) · [한국어](../CHANGELOG.md)

This page lists changes in each version of Agent Liche. See [Updating](docs/updates.md) for how to switch to a new version.

## 0.2.0

### Read this first

- **Starts like a fresh installation.** The app and internal names now match Agent Liche. Settings, chat history, layout, and agent connections start fresh. Old data stays in the old folders. Read [Cleaning up old folders](docs/updates.md#cleaning-up-old-folders) first.
- **Windows:** Launch **`AgentLiche.exe`** at the top of the extracted folder. Keep the **`AgentLiche`** folder beside it. Windows 11 64-bit (x64) is supported. **The 0.2.0 Windows release is not code-signed**, so SmartScreen appears on first launch. Click **More info › Run anyway** (on Korean Windows, **추가 정보 › 실행**). Code signing will be added in the next update.
- **macOS:** The app is **`Agent Liche.app`** and supports **only Apple Silicon Macs** running macOS 14 or later. It is Developer ID signed and notarized by Apple. On first launch, you only see the confirmation asking whether to open an app downloaded from the Internet.

### Chat and Liche's reactions

- **Everyday and Work:** Keep two separate conversations, with clothes and glasses chosen for each mode. Everyday defaults to pajamas. Work defaults to a maid outfit and glasses.
- **Models and thinking depth for each mode:** Choose a separate model and thinking depth for each mode under **리체 설정 › 모드 › 일상/업무 › 대화** (Liche Settings › Modes › Everyday/Work › Chat). The gear in the chat header takes you there directly. If you make no selection, the agent's defaults apply.
- **Default guides:** Default `common.md`, `daily.md`, and `developer.md` guides are included so Liche replies in character from the start. Files are created only when missing. Your edits are never overwritten. Deleted files return with default content on the next launch. To disable a guide, leave its file empty. See [Guide files](docs/guides.md#default-guides).
- **Requests outside the current mode:** The default guides tell Liche to suggest the other mode once, then help in the current mode if you prefer. She does not refuse because of the mode.
- **Long tool tasks:** The two-minute "응답이 없어요" (No response) limit does not apply while an agent uses tools. The chat shows "작업 중이에요 · 경과 시간" (Working · elapsed time). Liche only stops waiting after 30 minutes without an update. Set `LICHE_INPUT_TOOL_TIMEOUT_MINUTES` to change this to 2–1440 minutes. See [Reply waiting times](docs/first-run.md#reply-waiting-times).
- **Reactions without emotion judgment:** Liche looks thoughtful while waiting, types on a laptop during Work tool tasks, looks surprised at approval requests, and looks happy when a reply ends. These are rule-based reactions to situations, not emotions inferred from the conversation.
- **Emotion judgment (JEV) is optional:** Use your own key to choose expressions and moods that match the conversation. The judgment program is included on both Windows and macOS. Each judged exchange calls JEV **twice**: once for emotion and once for speech-bubble reactions. When enabled, it sends part of the conversation to TypeSafe AI in the United States and incurs separate fees. Keys are passed to `liche-judge --store-key` only through standard input, then stored in the macOS keychain or a file encrypted for the Windows user account. See [Keys, fees, and information sent](docs/jev.md).
- **Dozes when disconnected:** Liche does not doze just because you have been quiet. She dozes only when disconnected from an agent, and wakes when connected.
- **Connection status:** If an agent stops responding or disconnects, the chat window and connection card show the reason and try reconnecting.

### Display and settings

- **Settings in one place:** Find Connections, Modes, Notifications, Display, Window, Performance, General, and About Liche in the sidebar. Search also shows related words and each option's location. Edit colors and per-mode chat settings in the same settings window.
- **Chat style and layout:** Choose Floating or a classic window, and attach or detach the chat window. On both platforms, these are under **리체 설정 › 창 › 대화창** (Liche Settings › Window › Chat window).
- **Separate text size:** Choose chat text from 11–28 px independently of card size.
- **Less obstruction:** On Windows and macOS, a pinned card fades when the pointer comes near, letting clicks pass to the window behind it. Rendering pauses when Liche is not visible, such as when another window completely covers her.
- **Lower battery use:** The default **균형** (Balanced) profile renders only 20 frames per second while idle (previously 30). **고품질** (High quality) renders 30 (previously 60). Only mouse movement near Liche counts when deciding whether she is idle.
- **Easier card recovery:** Off-screen cards return to the screen. Use **카드를 화면 가운데로** (Center card on screen) to recover one. It is also in the Windows window menu (`Alt+Space`), and the macOS Dock menu and `⌥⌘L` shortcut.
- **macOS automatic startup:** Register Liche to launch at login in General settings. If macOS needs extra approval, Liche shows why and a button to open settings.

### Help and data information

- **Agent installation helper:** If no agent is installed, Liche shows the steps, commands to copy, and official instructions. Windows connection settings also let you choose OpenClaw, Claude Code, or Codex. Liche does not install them for you.
- **About Liche:** Shows the guide, license agreement, third-party notices, contact details, and an AI notice explaining that replies come from the connected AI agent.
- **Third-party notices:** Both packages include `THIRD-PARTY-NOTICES.txt`. Open it through **리체 정보 › 제3자 고지** (About Liche › Third-party notices). See [Third-party notices](legal/third-party-notices.md).
- **Create diagnostic file:** Makes a desktop zip of logs, settings, and recent crash reports for support. It excludes chat history, attachments, JEV key files, and memory dumps. It redacts chat text, keys, tokens, and user paths in logs. It is not sent automatically.
- **New version notifications:** Checks a small GitHub file once a day and when you open About Liche, then tells you if a new version is available. GitHub may see your IP address. Turn this off with **리체 정보 › 새 버전 알림** (About Liche › New version notifications). The app is not downloaded or installed automatically.
- **External connections:** [Privacy and data](docs/privacy.md#external-connections) lists everything Liche sends over the network. The retail package has no telemetry, crash report uploads, or listening ports.

### Known issues

- **Windows:** Without code signing, SmartScreen shows "Windows protected your PC" ("Windows의 PC 보호" on Korean Windows) on first launch. Click **More info › Run anyway** (Korean: **추가 정보 › 실행**). PCs with Smart App Control enabled may block launch.
- **Windows:** At 125% or 150% display scaling, text-field context menus and tooltips in Liche windows, such as Settings, render at 100%. The windows and text themselves follow the display scale.

## 0.1.0 (2026-10-30)

- First Windows Early Access build.

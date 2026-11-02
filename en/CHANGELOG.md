# Changelog

[Guide home](README.md) · [한국어](../CHANGELOG.md)

This page lists changes in each version of Agent Liche. See [Updating](docs/updates.md) for how to switch to a new version.

## Next release (Windows 0.2.0 · macOS 0.2.1)

### On-screen wording

- Tool-use approvals are called **승인** (Approve): **승인이 필요해요** (Approval needed) in the chat, **승인 요청** (Approval requests) in the notification settings, and "승인 요청: …" (Approval request: …) in the chat history.
- **카드를 화면 가운데로** (Center card on screen) is now **리체를 화면 가운데로** (Center Liche on screen) in Liche Settings › Window, the macOS app and Dock menus, and the Windows window menu.
- When the chat window program is not running, the connection card shows **대화창이 멈췄어요** (The chat window stopped) and what to do (it said "리체 대화 꺼짐" before).
- **리체 설정 › 일반 › 초기화** (Liche Settings › General › Reset) names what it deletes (chat history and attachments, Liche's affinity and mood). With an agent connection it is off, with the reason, before you press it.
- When a connection fails or a reply stops, Liche says what happened and what to do (sign in again, a usage limit, the internet connection, send the same message again). The two-minute note is "2분 넘게 답이 없어서 기다리기를 멈췄어요. 같은 메시지를 다시 보내 보세요." (No reply for over two minutes, so Liche stopped waiting. Try sending the same message again).
- The install helper calls the Claude Code and Codex adapters **연결 도구** (connection tool) and Hermes's extra part **연결 기능** (connection feature).
- The chat window's title is **리체와 대화** (Chat with Liche).

## 0.2.0

### Read this first

- **The macOS edition comes first.** 0.2.0 is **the first macOS edition of Agent Liche**. Windows 0.2.0 is not published yet; until it is, the Windows file you get from the store is **0.1.0**. When Windows 0.2.0 is out, this changelog and [Windows installation](docs/install-windows.md) will say so.
- **macOS:** The app is **`Agent Liche.app`** and supports **only Apple Silicon Macs** running macOS 14 or later. It is Developer ID signed and notarized by Apple. On first launch, you only see the confirmation asking whether to open an app downloaded from the Internet. 16 GB of memory is recommended; 8 GB is the minimum.
- **Checking files:** Each file's name, size, and SHA-256 are listed under **Version history** on the [store product page](https://app.gujo.io/products/287?lang=en). See [macOS installation](docs/install-mac.md#checking-your-download-optional) for how to check them.
- **Windows 0.2.0 will start like a fresh installation.** The app and internal names now match Agent Liche, so on Windows, people coming from 0.1.0 start with fresh settings, chat history, layout, and agent connections, and the old data stays in the old folders. When Windows 0.2.0 is out, read [Cleaning up old folders](docs/updates.md#cleaning-up-old-folders) first. Windows 0.2.0 starts from **`AgentLiche.exe`** at the top of the extracted folder and is not code-signed, so SmartScreen appears on first launch (**More info › Run anyway**).

### Chat and Liche's reactions

- **Everyday and Work:** Keep two separate conversations, with clothes and glasses chosen for each mode. Everyday defaults to pajamas. Work defaults to a maid outfit and glasses.
- **Model and thinking depth for every agent:** Choose a separate model and thinking depth for each mode under **리체 설정 › 모드 › 일상/업무 › 대화** (Liche Settings › Modes › Everyday/Work › Chat). Claude Code, Codex, OpenClaw, and Hermes all show the choices that agent reports, and a choice applies to that mode's conversation right away. The thinking depths of the chosen model update at once. The gear in the chat header takes you there directly. See [Choices by agent](docs/agents.md#models-and-thinking-depth-by-agent).
- **Default guides:** Default `common.md`, `daily.md`, and `developer.md` guides are included so Liche replies in character from the start. Files are created only when missing. Your edits are never overwritten. Deleted files return with default content on the next launch. To disable a guide, leave its file empty. See [Guide files](docs/guides.md#default-guides).
- **Requests outside the current mode:** The default guides tell Liche to suggest the other mode once, then help in the current mode if you prefer. She does not refuse because of the mode.
- **Long tool tasks:** The two-minute "응답이 없어요" (No response) limit does not apply while an agent uses tools. The chat shows "작업 중이에요 · 경과 시간" (Working · elapsed time). Liche only stops waiting after 30 minutes without an update. Set `LICHE_INPUT_TOOL_TIMEOUT_MINUTES` to change this to 2–1440 minutes. See [Reply waiting times](docs/first-run.md#reply-waiting-times).
- **Approve and reject:** When an agent asks before using a tool, choose **승인** (Approve) or **거절** (Reject) in the chat window. Liche answers only with the one-time option the agent sent with its request and never picks a lasting rule such as "always allow".
- **Codex asks you:** Codex connects in **Workspace access** mode. It asks for approval in the chat window before writing outside its work folder and the temporary folders, or before using the network. See [How Codex asks for approval](docs/agents.md#how-codex-asks-for-approval).
- **Switching agents while connected:** Pick another agent while one is connected and the button changes to **연결하기** (Connect). Press it and both modes reconnect to the new agent.
- **Long replies arrive line by line:** A long reply without blank lines (Hermes, for example) appears line by line instead of all at once at the end.
- **Chat polish:** A code block's language name is a small label above the block. Approval cards use the chat's handwriting, with paths and commands in a fixed-width font. A reply stopped with **■ 중지** (Stop) ends with "멈췄어요" (Stopped).
- **Hanja conversion on macOS:** While typing a Korean syllable in the input box, press `⌥Return` to open the Hanja candidate list.
- **Ending an agent ends what it started:** When you quit Liche or switch agents, Liche also ends the commands the agent started. **■ 중지** (Stop) only stops the current reply; the agent decides what it keeps running.
- **Reactions without emotion judgment:** Liche looks thoughtful while waiting, types on a laptop during Work tool tasks, looks surprised at approval requests, and looks happy when a reply ends. These are rule-based reactions to situations, not emotions inferred from the conversation.
- **Emotion judgment (JEV) is optional:** Use your own key to choose expressions and moods that match the conversation. Each judged exchange calls JEV **twice**: once for emotion and once for speech-bubble reactions. When enabled, it sends part of the conversation to TypeSafe AI in the United States and incurs separate fees. Keys are passed to `liche-judge --store-key` only through standard input, then stored in the macOS keychain. See [Keys, fees, and information sent](docs/jev.md).
- **She cries when she cannot connect:** If Liche is not connected to an agent, or the connection is lost, she cries. She stops as soon as the connection is back.
- **She dozes as time passes:** When nobody talks to her for a while, she dozes with Zz above her head, and later falls fast asleep. Click her or talk to her to wake her.
- **Why a connection fails, and what to do:** When an agent cannot start, Liche reads the reason and shows **연결 중** (Connecting), **다시 시도 중** (Retrying), **해결 필요** (Needs a fix), or **연결됨** (Connected), with the command to run, a **복사** (Copy) button, and **다시 연결** (Reconnect). For OpenClaw, Liche checks that its gateway is running even before connecting. See [When the connection fails](docs/troubleshooting.md#when-the-connection-fails).

### Display and settings

- **Sharp on Retina:** On a Retina screen, the card (Liche, the icons, the marks above her head) and the Liche Settings window are drawn at the screen's own pixels. Liche's 3D image follows the performance profile: **고품질** (High quality) 2×, **균형** (Balanced) 1.5×, **절약** (Power saving) 1×. Non-Retina screens are unchanged. See [Performance](docs/settings.md#performance).
- **She appears on a busy Mac:** On a Mac whose GPU is busy with other apps, Liche started in the background (as a login item, for example) no longer gives up when her first frames are slow; she waits and appears.
- **She does not keep your Mac awake:** While Liche runs, display sleep, the screen saver, sleep, and the lock screen happen as your Mac's settings say. Liche pauses drawing meanwhile.
- **Every Mac draws the same way:** From M1 to the newest Macs, Liche uses the same rendering path (Metal SM5), which uses less memory and makes the package smaller.
- **Settings in one place:** Find Connections, Modes, Notifications, Display, Window, Performance, General, and About Liche in the sidebar. Search also shows related words and each option's location. Edit colors and per-mode chat settings in the same settings window.
- **Chat style and layout:** Choose a floating window or a classic window, and attach or detach the chat window. These are under **리체 설정 › 창 › 대화창** (Liche Settings › Window › Chat window).
- **Separate text size:** Choose chat text from 11–28 px independently of card size.
- **Less obstruction:** A pinned card fades when the pointer comes near, letting clicks pass to the window behind it. Rendering pauses when Liche is not visible, such as when another window completely covers her.
- **Lower battery use:** The default **균형** (Balanced) profile renders only 20 frames per second while idle. **고품질** (High quality) renders 30. Only mouse movement near Liche counts when deciding whether she is idle.
- **Easier card recovery:** Off-screen cards return to the screen. Use **카드를 화면 가운데로** (Center card on screen) to recover one. It is also in the Dock menu and the `⌥⌘L` shortcut.
- **Automatic startup:** Register Liche to launch at login in General settings. If macOS needs extra approval, Liche shows why and a button to open settings.

### Help and data information

- **Agent installation helper:** If no agent is installed, Liche shows the steps, commands to copy, and official instructions. Liche does not install them for you.
- **About Liche:** Shows the guide, license agreement, third-party notices, contact details, and an AI notice explaining that replies come from the connected AI agent.
- **Third-party notices:** The package includes `THIRD-PARTY-NOTICES.txt`. Open it through **리체 정보 › 제3자 고지** (About Liche › Third-party notices). See [Third-party notices](legal/third-party-notices.md).
- **Create diagnostic file:** Makes a desktop zip of logs, settings, and recent crash reports for support. It excludes chat history, attachments, JEV key files, and memory dumps. It redacts chat text, keys, tokens, and user paths in logs. It is not sent automatically.
- **New version notifications:** Once a day and when you open About Liche, Liche checks a small version file that the Gujo store makes for the product, then tells you if a new version is available. The store may see your IP address. Turn this off with **리체 정보 › 새 버전 알림** (About Liche › New version notifications). The app is not downloaded or installed automatically.
- **External connections:** [Privacy and data](docs/privacy.md#external-connections) lists everything Liche sends over the network. The retail package has no telemetry, crash report uploads, or listening ports.

### Known issues

- **macOS:** The first time you open the app from an external drive (a removable volume), macOS asks whether it may access the removable volume, and the chat window does not start until you answer. Click **Allow** (Korean: **허용**), or move the app to the **Applications** folder and open it there.
- **macOS:** When Liche runs for a long time, the character program's memory grows slowly. This comes from the engine (Unreal Engine); before release it measured about 38 MB per hour. Quitting and reopening Liche frees it.
- **Windows 0.2.0 (not yet published):** At 125% or 150% display scaling, text-field context menus and tooltips in Liche windows, such as Settings, render at 100%. The windows and text themselves follow the display scale.
- **Windows 0.2.0 (not yet published):** Without code signing, SmartScreen shows "Windows protected your PC" ("Windows의 PC 보호" on Korean Windows) on first launch. Click **More info › Run anyway** (Korean: **추가 정보 › 실행**). PCs with Smart App Control enabled may block launch.

## 0.1.0 (2026-10-30)

- First Windows Early Access build. This is the Windows file the store gives you today. The guide of that time is the [0.1.0 guide](https://github.com/gujo-io/agent-liche-docs/blob/390cc92b9970fdc7c8191cf37b2a653edc4dce7d/README.md) (Korean).

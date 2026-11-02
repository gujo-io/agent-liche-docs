# Troubleshooting

[Guide home](../README.md) · [한국어](../../docs/troubleshooting.md)

## Known issues (0.2.0)

| Platform | Issue | Solution or workaround |
| --- | --- | --- |
| Windows | Without code signing, SmartScreen shows "Windows protected your PC" (Korean: "Windows의 PC 보호") on first launch | Click **More info › Run anyway** (Korean: **추가 정보 › 실행**). See [instructions](install-windows.md#when-windows-protected-your-pc-appears-smartscreen). Code signing will be added in the next update |
| Windows | At 125% or 150% display scaling, text-field context menus (copy/paste) and hover tooltips in windows such as Liche Settings render small at 100% | Functionality is unaffected. The windows and text themselves follow the monitor's scale. A fix is planned for the next update |
| Windows | PCs with Smart App Control enabled may block the unsigned 0.2.0 release without a **Run anyway** button | Contact support |

## Installation and launch

### Windows shows "Windows protected your PC"

The 0.2.0 Windows release is not code-signed, so SmartScreen shows **Unknown publisher** on first launch (Korean: **알 수 없는 게시자**). Check that the file came from the Gujo store, then click **More info**, followed by **Run anyway** (Korean: **추가 정보**, then **실행**). See [Windows installation](install-windows.md#when-windows-protected-your-pc-appears-smartscreen) for detailed steps and how to check the download's SHA-256. Do not run files from unknown sources or files Microsoft Defender detects as dangerous.

### Windows shows a firewall dialog

Retail Liche does not open incoming-connection ports, so firewall permission is unnecessary. If a dialog asks to allow incoming connections for the Liche character program, do not allow it. Check the file source and version, then contact support. For dialogs from a separately installed agent, check that program's guidance.

### The app will not open on macOS

The 0.2.0 macOS release is Developer ID signed and notarized by Apple. On first launch, the confirmation says "“Agent Liche” is an app downloaded from the Internet. Are you sure you want to open it?" and "Apple checked it for malicious software and none was detected." Click **Open**. A warning that the developer cannot be verified or the app is damaged may mean you received a different file. Check that it came from the Gujo store and send support the warning's wording. See [macOS installation](install-mac.md#gatekeeper-confirmation).

The app does not open on Intel Macs. Version 0.2.0 supports only Apple Silicon Macs.

### macOS asks for permissions

Liche herself asks only for notifications and, when using emotion judgment, keychain access. Other requests, such as Documents folder access, usually come from the connected agent. The agent pauses until you respond, so answer first. See [macOS installation](install-mac.md#4-permissions-macos-may-request) for which dialogs appear and why.

### There are two Liches after launching a new version on Windows

If the old version is still running, it may appear alongside the new one. Quit both, then open only the new version. Always quit the old version before updating.

## Connections

### The chat says Liche is not connected yet

"리체가 아직 바깥과 연결되지 않았어요" (Liche is not connected to the outside yet) means no agent is connected. Click **연결 설정** (Connection settings) on Windows or **리체 연결하기** (Connect Liche) on macOS to choose one. See [Connecting an agent](agents.md).

### Liche keeps dozing

Liche dozes only when she is not connected to an agent. Check the connection card at the top of the **리체 설정** (Liche Settings) sidebar. If the agent stopped or is not responding, follow [Connecting an agent](agents.md#when-the-agent-does-not-respond). Liche wakes on her own once connected.

### The agent is not responding

"(에이전트)가 응답하지 않아요" ((Agent) is not responding) means the agent did not answer within 45 seconds. Check permission dialogs, agent login, and the installation location in that order. Liche tries reconnecting after a short wait. See [Connecting an agent](agents.md#when-the-agent-does-not-respond) for detailed steps.

### It has been 30 seconds since saving the connection

If "연결을 저장한 지 30초가 지났어요" (It has been 30 seconds since the connection was saved) appears, the agent is likely waiting for login or initial setup. Run it once in a terminal, finish setup, then select it again.

### The connection card says Liche chat is off

"리체 대화 꺼짐" (Liche chat is off) means the chat window program is not running. The character program relaunches it if it stops. If it still does not return, quit Liche completely and reopen her.

### Liche cannot find an installed agent (macOS)

Liche searches PATH, `/opt/homebrew/bin`, `/usr/local/bin`, and `~/.local/bin`. If you installed elsewhere, such as through nvm, click **복사** (Copy) under **에이전트로 연결하기** (Connect through an agent) in first-run setup and paste the copied text into your agent.

### The connection does not support per-mode conversations

"이 연결은 아직 모드별 대화를 지원하지 않아요" (This connection does not yet support per-mode conversations) means the connected agent cannot open separate conversations for each mode. Each mode still keeps its own history, but only one mode can wait for a reply at a time. Sending from the other mode shows a notice and leaves your draft in place.

## Chat

### I cannot send a message

You cannot send another message while waiting for a reply in the same mode. Wait for the reply to finish or click **■ 중지** (Stop). Your draft stays in the input field. You can switch to the other mode and send there.

### A reply stopped with no response

"응답이 없어요" (No response) means there was no update for over two minutes (120 seconds) while the agent was not using tools. It may still be thinking. Ask again after a short wait. If this happens often, check the agent's status.

There is no two-minute limit while the agent uses tools. Keep waiting while the chat shows a message such as "작업 중이에요 · 3분 12초" (Working · 3 minutes 12 seconds). See [Reply waiting times](first-run.md#reply-waiting-times).

### Liche stopped waiting after 30 minutes without an update

"작업이 30분 넘게 아무 소식이 없어서 기다리기를 멈췄어요" (I stopped waiting because there has been no update on the task for over 30 minutes) means no progress update arrived for 30 minutes during tool use. Check the agent's terminal or task results. If you often assign tasks that take over 30 minutes without updates, increase the timeout with `LICHE_INPUT_TOOL_TIMEOUT_MINUTES` (2–1440 minutes). See [Reply waiting times](first-run.md#reply-waiting-times).

### An approval request disappeared

Clicking **■ 중지** or disconnecting cancels all pending approval requests. Ask the agent again.

### Liche's expressions do not match the conversation

With emotion judgment (JEV) off, Liche uses only preset rule-based reactions. Turn on [Emotion judgment (JEV)](jev.md) for expressions that fit the conversation.

### A deleted guide file came back

Liche recreates `common.md`, `daily.md`, and `developer.md` with default guides if missing. To disable a guide, leave its file empty instead of deleting it. Liche does not refill empty files. See [Guide files](guides.md#default-guides) for the full rules.

### Liche suggests Work mode when I ask for work in Everyday mode

The default guides tell Liche to suggest the other mode once for requests outside the current mode. If you still ask her to do it, she helps in the current mode.

## Display and windows

### The card is off-screen and I cannot reach it

- Click **옮기기** (Move) under **리체 설정 › 창 › 카드를 화면 가운데로** (Liche Settings › Window › Center card on screen). The card moves at its current size to the center of the display containing the pointer.
- macOS: Right-click the Agent Liche Dock icon and choose **카드를 화면 가운데로** (Center card on screen), or press `⌥⌘L` when Agent Liche is the active app.
- Windows: Hold Shift and right-click Liche's taskbar button, or click Liche and press `Alt+Space`. Choose **카드를 화면 가운데로** from the window menu.

Liche checks that the glass card and icons are on-screen when you release a drag, when display arrangements change, and every second. If outside the screen, she moves them to the nearest valid position. If you disconnect a monitor, she moves to roughly the same position on the main display. Liche's head above the glass is left as it is, even if off-screen.

### The icons do not open

Hover briefly over **⋯** (More) at the top right of the card to unfold the icons. Clicking **⋯** does not open anything; this is normal.

### The card is too big or too small

Drag inside a rounded corner of the glass card to resize it. After releasing, click the briefly visible **100%로** (Reset to 100%) to restore the default size.

### Chat text is too small or too large

Change **리체 설정 › 화면 › 글자 크기** (Liche Settings › Display › Text size). Changing the card size leaves text size unchanged.

### Changing appearance does not change chat colors

If the color scheme is **직접** (Custom) and your custom Light and Dark colors are identical, switching appearance does not change colors. Choose another scheme, or switch appearance and set its colors through **직접 고르기 ›** (Choose custom colors ›).

## Performance and battery

### CPU or GPU use is high and the battery drains quickly

Liche continuously renders a 3D character, so she steadily uses CPU and GPU resources. Reduce usage in this order.

1. Set **리체 설정 › 성능 › 성능 프로필** (Liche Settings › Performance › Performance profile) to **절약** (Power saving).
2. Lower **최대 프레임** (Maximum frame rate). 15 uses the fewest resources.
3. Keep **가려지면 쉬기** (Pause when hidden) enabled. On Windows and macOS, rendering pauses when Liche is not visible, such as when another window fully covers her.
4. On Windows, setting **선명도** (Sharpness) to **보통** (Normal) greatly reduces GPU use. Restart Liche to apply it.

After more than 20 seconds without changes, Liche automatically lowers rendering to **가만히 있을 때 프레임** (Idle frame rate). Check actual usage under **지금 리체가 쓰는 양** (Liche's current resource use) at the bottom of **성능** (Performance).

## Notifications

### Notifications do not arrive

1. Check that **리체 설정 › 알림 › 알림 받기** (Liche Settings › Notifications › Receive notifications) is enabled.
2. If a warning at the top says operating-system notifications are off, use its button to open settings and enable Agent Liche notifications.
3. Test with **보내기** (Send) under **테스트 알림** (Test notification).
4. Notifications for the current conversation stay quiet while you view chat. To always receive them, turn on **리체를 보고 있을 때도 알림** (Notify even while viewing Liche).
5. If Windows 11 **방해 금지** (Do not disturb) turns on automatically "게임을 플레이할 때" (When playing a game), Windows may treat Liche as a game and hide banners. Notifications remain in Notification Center. Turn off that option under **설정 › 시스템 › 알림 › 자동으로 방해 금지 켜기** (Settings › System › Notifications › Turn on do not disturb automatically).

## After updating

### Chat history and settings disappeared after an update

The update that renames Lize to Liche starts like a fresh installation. Old history and settings are not deleted. They remain in the old `LizeWidget` and `Lize` folders, but the new version does not read them. Copy any guide files you need from the old guide folder to the new one yourself. See [Updating](updates.md).

## What to include when contacting support

- Operating system and version, such as Windows 11 24H2 or macOS 26.5
- Version line under **리체 설정 › 리체 정보** (Liche Settings › About Liche), such as `버전 0.2.0 (2026.11.02 · a2b5fea)` (Version 0.2.0 (2026.11.02 · a2b5fea))
- Connected agent and its version
- What you did, what happened, and the exact wording shown on-screen
- If possible, attach the desktop `Liche-diagnostics-날짜-시각.zip` made with **리체 설정 › 리체 정보 › 진단 파일 만들기** (Liche Settings › About Liche › Create diagnostic file). It contains logs, settings, recent crash reports, version, and display information. It excludes chat history, attachments, JEV key files, and memory dumps. It redacts chat text, keys, tokens, and user paths in logs. It is not sent automatically. **Open and check it yourself** before sending.
- If you cannot create diagnostics, use **리체 설정 › 일반 › 기록 폴더 › 폴더 열기** (Liche Settings › General › History folder › Open folder) and check `input.log` inside `logs`. This original log does not have the diagnostic zip's redaction. Check for sensitive content yourself before sending.

Contact: help@ranode.net, https://support.gujo.io, 010-2193-6227 (weekdays, 10 a.m. to 6 p.m.)

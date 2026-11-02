# Troubleshooting

[Guide home](../README.md) · [한국어](../../docs/troubleshooting.md)

## Known issues (0.2.0)

| Platform | Issue | Solution or workaround |
| --- | --- | --- |
| macOS | The first time you open the app from an external drive (a removable volume), macOS asks whether it may access the removable volume, and the chat window does not start until you answer | Click **Allow** (Korean: **허용**), or move the app to the **Applications** folder and open it there ([macOS installation](install-mac.md#2-moving-to-applications)) |
| macOS | When Liche runs for a long time, the character program's memory grows slowly. This comes from the engine (Unreal Engine); before release it measured about 38 MB per hour | Quitting and reopening Liche frees it. We plan to ship the fix in an update once the engine has one |
| Windows 0.2.0 (not yet published) | Without code signing, SmartScreen shows "Windows protected your PC" (Korean: "Windows의 PC 보호") on first launch | Click **More info › Run anyway** (Korean: **추가 정보 › 실행**). See [instructions](install-windows.md#when-windows-protected-your-pc-appears-smartscreen). Code signing will be added in the next update |
| Windows 0.2.0 (not yet published) | At 125% or 150% display scaling, text-field context menus (copy/paste) and hover tooltips in windows such as Liche Settings render small at 100% | Functionality is unaffected. The windows and text themselves follow the monitor's scale. A fix is planned for the next update |
| Windows 0.2.0 (not yet published) | PCs with Smart App Control enabled may block the unsigned 0.2.0 release without a **Run anyway** button | Contact support |

Known issues of Windows 0.1.0, which the store gives you today, are in the [0.1.0 guide](https://github.com/gujo-io/agent-liche-docs/blob/390cc92b9970fdc7c8191cf37b2a653edc4dce7d/docs/troubleshooting.md) (Korean).

## When the connection fails

Liche runs the agent you chose (OpenClaw, Claude Code, Codex, Hermes) herself to talk with it. If the agent cannot start, Liche reads the reason, shows it, and tells you what to do, with the command. Liche never installs, starts, or reconfigures an agent for you. Run the commands yourself.

### Where it appears

- **리체 시작하기 › 리체를 연결해 주세요** (Start Liche › Please connect Liche, macOS): The chosen agent's row shows the status, and a box below it shows the reason and the command. Click **복사** (Copy) beside the command to copy it.
- **The chat window** (above the input box): The same reason and command, **복사** (Copy), and **다시 연결** (Reconnect).
- **리체 설정 › 연결** (Liche Settings › Connections): The status appears beside the agent's name, with the reason in one line below it. **연결 설정 열기** (Open connection settings) opens the connection screen above.
- **연결 설정** (Connection settings, Windows 0.2.0): The reason, the command, and **다시 연결** appear under the card of the agent being connected.

### Status names

| Status | Meaning | What to do |
| --- | --- | --- |
| 연결 중 (Connecting) | Liche is starting the agent. | Wait a moment. |
| 다시 시도 중 (3/8) (Retrying (3/8)) | The agent could not start, so Liche is trying again on her own. The number is the attempt; she tries up to 8 times. | Fix the reason below, then click **다시 연결** (Reconnect) to try again at once instead of waiting. |
| 해결 필요 (Needs a fix) | Liche stopped trying again. | Fix the reason, then click **다시 연결**. |
| 연결됨 (Connected) | You can chat. | |

While she is not connected, Liche cries inside her card. She stops as soon as the connection is back.

### Common reasons

Paste the commands into Terminal on macOS or PowerShell on Windows.

#### OpenClaw

- **OpenClaw 설정에 고칠 곳이 있어요** (OpenClaw's settings need fixing)
  OpenClaw's settings file has a value this version does not know. This often happens after another OpenClaw version changed the settings.
  ```
  openclaw doctor --fix
  ```
- **OpenClaw 게이트웨이가 꺼져 있어요** (OpenClaw's gateway is off)
  OpenClaw talks through its gateway service. If you never installed the gateway, run both commands in order; if you did, run only the second.
  ```
  openclaw gateway install
  openclaw gateway start
  ```
  Liche checks that the gateway is running even before connecting, and says so in the OpenClaw row if it is off.
- **OpenClaw 게이트웨이가 인증을 요구해요** (OpenClaw's gateway requires authentication)
  Appears when the gateway's token or pairing does not match. Run OpenClaw's check with the command below and follow what it says.
  ```
  openclaw doctor
  ```
- **OpenClaw가 자기 데이터를 정리하는 중이에요** (OpenClaw is tidying its own data)
  While OpenClaw tidies its data, it cannot start for a moment. When it finishes, Liche reconnects on her own. Nothing to do.
- **OpenClaw가 오래된 버전이에요** (OpenClaw is an old version)
  ```
  npm install -g openclaw@latest --allow-scripts=openclaw
  ```

#### Claude Code

- **Claude Code에 로그인해야 해요** (You need to sign in to Claude Code)
  ```
  claude auth login
  ```

#### Codex

- **Codex에 로그인해야 해요** (You need to sign in to Codex)
  If the codex command already exists, run only the second command.
  ```
  npm install -g @openai/codex
  codex login
  ```

#### Hermes

- **Hermes가 아직 AI 제공자와 연결되지 않았어요** (Hermes is not connected to an AI provider yet)
  ```
  hermes model
  ```

#### Every agent

- **(에이전트)에 필요한 Node.js를 찾지 못했어요** / **(에이전트)에 필요한 Node.js가 오래됐어요** (Node.js needed by (agent) was not found / is too old)
  OpenClaw and the connection tools of Claude Code and Codex run on Node.js. Install or update it with the command shown (`brew install node`, `brew upgrade node`, or `winget install OpenJS.NodeJS` on Windows).
- **(에이전트)가 리체와 맞지 않는 오래된 버전이에요** ((Agent) is an old version that does not work with Liche)
  Install the new version of the agent with the installation command shown.
- **(에이전트)를 실행하지 못했어요** (Could not run (agent))
  Appears when the agent was deleted or moved. Reinstall it with the installation command shown.
- **(에이전트)가 응답하지 않아요** ((Agent) is not responding)
  Check that the agent is running. On macOS, answer any permission dialog first. Liche tries to reconnect after a short wait. See [Connecting an agent](agents.md#when-the-agent-does-not-respond) for detailed steps.
- **(에이전트)가 대화를 시작하지 못했어요 · (에이전트)가 남긴 말: “…”** ((Agent) could not start a conversation · What (agent) said: "…")
  When Liche cannot tell the reason, she shows the first line of the agent's own error. Keys, tokens, email addresses, and your user folder name in it are masked. If the agent suggested a command itself (for example, `openclaw doctor`), it is shown too.

### If it still does not work

Create a diagnostic file with **리체 설정 › 리체 정보 › 진단 파일 만들기** (Liche Settings › About Liche › Create diagnostic file) and send it to support. Chat text, keys, and account names are masked in it. Also see [What to include when contacting support](#what-to-include-when-contacting-support) below.

## Installation and launch

### Windows shows "Windows protected your PC"

The 0.2.0 Windows release is not code-signed, so SmartScreen shows **Unknown publisher** on first launch (Korean: **알 수 없는 게시자**). Check that the file came from the Gujo store, then click **More info**, followed by **Run anyway** (Korean: **추가 정보**, then **실행**). See [Windows installation](install-windows.md#when-windows-protected-your-pc-appears-smartscreen) for detailed steps and how to check the download's SHA-256. Do not run files from unknown sources or files Microsoft Defender detects as dangerous.

### Windows shows a firewall dialog

Retail Liche does not open incoming-connection ports, so firewall permission is unnecessary. If a dialog asks to allow incoming connections for the Liche character program, do not allow it. Check the file source and version, then contact support. For dialogs from a separately installed agent, check that program's guidance.

### The app will not open on macOS

The 0.2.0 macOS release is Developer ID signed and notarized by Apple. On first launch, the confirmation says "“Agent Liche” is an app downloaded from the Internet. Are you sure you want to open it?" and "Apple checked it for malicious software and none was detected." Click **Open**. A warning that the developer cannot be verified or the app is damaged may mean you received a different file. Check that it came from the Gujo store and send support the warning's wording. See [macOS installation](install-mac.md#gatekeeper-confirmation).

The app does not open on Intel Macs. Version 0.2.0 supports only Apple Silicon Macs.

### macOS asks for permissions

Liche herself asks only for notifications and, when using emotion judgment, keychain access. The first time you open the app from an external drive, macOS also asks about removable volume access; the chat window does not start until you answer, so click **Allow** (Korean: **허용**) or move the app to Applications. Other requests, such as Documents folder access, usually come from the connected agent. The agent pauses until you respond, so answer first. See [macOS installation](install-mac.md#4-permissions-macos-may-request) for which dialogs appear and why.

### There are two Liches after launching a new version on Windows

If the old version is still running, it may appear alongside the new one. Quit both, then open only the new version. Always quit the old version before updating.

## Connections

### The chat says Liche is not connected yet

"리체가 아직 바깥과 연결되지 않았어요" (Liche is not connected to the outside yet) means no agent is connected. Click **연결 설정** (Connection settings) on Windows or **리체 연결하기** (Connect Liche) on macOS to choose one. See [Connecting an agent](agents.md).

### Liche is crying

She is not connected to an agent, or the connection was lost. Check the status and reason on the connection card at the top of the **리체 설정** (Liche Settings) sidebar, and follow [When the connection fails](#when-the-connection-fails) above. She stops crying as soon as she connects. Clicking her does not stop it.

### Liche is dozing or asleep

When nobody talks to her for a while, Liche dozes with Zz above her head, and later falls fast asleep. This is normal. Click her or send a message to wake her. From a deep sleep, two clicks wake her fully.

### The agent is not responding

"(에이전트)가 응답하지 않아요" ((Agent) is not responding) means the agent did not answer within 45 seconds. Check permission dialogs, agent login, and the installation location in that order. Liche tries reconnecting after a short wait. See [Connecting an agent](agents.md#when-the-agent-does-not-respond) for detailed steps.

### Codex gives no reply after a rejection

If Codex asks to run a command that needs more than its workspace allows and you choose **거절** (Reject), Codex stops that turn and ends without a reply. Tell it what to do differently. See [How Codex asks for approval](agents.md#how-codex-asks-for-approval).

### Not connected 30 seconds after saving the connection

If "연결을 저장한 지 30초가 지나도 연결되지 않았어요" (Not connected 30 seconds after saving the connection) appears, the agent is likely waiting for login or initial setup. Run it once in a terminal, finish setup, then select it again.

### The connection card says the chat window stopped

"대화창이 멈췄어요" (The chat window stopped) means the chat window program is not running. The character program relaunches it if it stops. If it still does not return, quit Liche completely and reopen her.

### Liche cannot find an installed agent (macOS)

Liche searches PATH, `/opt/homebrew/bin`, `/usr/local/bin`, and `~/.local/bin`. If you installed elsewhere, such as through nvm, click **복사** (Copy) under **에이전트로 연결하기** (Connect through an agent) in first-run setup and paste the copied text into your agent.

### The connection does not support per-mode conversations

"이 연결은 아직 모드별 대화를 지원하지 않아요" (This connection does not yet support per-mode conversations) means the connected agent cannot open separate conversations for each mode. Each mode still keeps its own history, but only one mode can wait for a reply at a time. Sending from the other mode shows a notice and leaves your draft in place.

## Chat

### I cannot send a message

You cannot send another message while waiting for a reply in the same mode. Wait for the reply to finish or click **■ 중지** (Stop). Your draft stays in the input field. You can switch to the other mode and send there.

### Liche stopped waiting after two minutes without a reply

"2분 넘게 답이 없어서 기다리기를 멈췄어요" (No reply for over two minutes, so Liche stopped waiting) means there was no update for over two minutes (120 seconds) while the agent was not using tools. It may still be thinking. Send the same message again after a short wait. If this happens often, check the agent's status.

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

- Click **옮기기** (Move) under **리체 설정 › 창 › 리체를 화면 가운데로** (Liche Settings › Window › Center Liche on screen). The card moves at its current size to the center of the display containing the pointer.
- macOS: Right-click the Agent Liche Dock icon and choose **리체를 화면 가운데로** (Center Liche on screen), or press `⌥⌘L` when Agent Liche is the active app.
- Windows: Hold Shift and right-click Liche's taskbar button, or click Liche and press `Alt+Space`. Choose **리체를 화면 가운데로** (Center Liche on screen) from the window menu.

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

1. Set **리체 설정 › 성능 › 성능 프로필** (Liche Settings › Performance › Performance profile) to **절약** (Power saving). On a Retina Mac the profile also sets Liche's image quality: **고품질** (High quality, 2×) uses the most and **절약** (1×) the least ([Retina screens](settings.md#retina-screens-macos)).
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

### Chat history and settings disappeared after an update (Windows)

This happens when you switch from 0.1.0 to 0.2.0 on Windows. It does not apply to macOS, where 0.2.0 is the first edition. The update that renames Lize to Liche starts like a fresh installation. Old history and settings are not deleted. They remain in the old `LizeWidget` and `Lize` folders, but the new version does not read them. Copy any guide files you need from the old guide folder to the new one yourself. See [Updating](updates.md).

## What to include when contacting support

- Operating system and version, such as Windows 11 24H2 or macOS 26.5
- Version line under **리체 설정 › 리체 정보** (Liche Settings › About Liche), such as `버전 0.2.0 (date · commit)` (Version 0.2.0 (date · commit))
- Connected agent and its version
- What you did, what happened, and the exact wording shown on-screen
- If possible, attach the desktop `Liche-diagnostics-날짜-시각.zip` made with **리체 설정 › 리체 정보 › 진단 파일 만들기** (Liche Settings › About Liche › Create diagnostic file). It contains logs, settings, recent crash reports, version, and display information. It excludes chat history, attachments, JEV key files, and memory dumps. It redacts chat text, keys, tokens, and user paths in logs. It is not sent automatically. **Open and check it yourself** before sending.
- If you cannot create diagnostics, use **리체 설정 › 일반 › 기록 폴더 › 폴더 열기** (Liche Settings › General › History folder › Open folder) and check `input.log` inside `logs`. This original log does not have the diagnostic zip's redaction. Check for sensitive content yourself before sending.

Contact: help@ranode.net, https://support.gujo.io, 010-2193-6227 (weekdays, 10 a.m. to 6 p.m.)

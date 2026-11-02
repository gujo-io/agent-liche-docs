# Connecting an agent

[Guide home](../README.md) · [한국어](../../docs/agents.md)

Liche does not create replies herself. **The AI agent you connect creates the replies.** Liche displays the conversation and reacts with expressions and gestures. Install the agent separately.

## Read this first

- **Accounts and fees are separate.** Get the agent's account, subscription, or API key from that service. Liche does not receive or store that login information or those keys.
- **Connections use ACP.** ACP (Agent Client Protocol) is an open way to talk with agents. Claude Code connects through the `claude-agent-acp` adapter, and Codex through `codex-acp`.
- **Conversations go to the agent.** The agent may send content to its AI service to create a reply. Read [Privacy and data](privacy.md).
- **Finish signing in and initial setup first.** Follow the agent's official instructions to finish login and model setup before Liche can receive replies.
- Windows Liche connects to agents installed on Windows. **Agents installed only inside WSL are not supported.** Choose an agent installed as a Windows executable.
- Choose models and thinking depth separately for each mode under **리체 설정 › 모드 › 일상(또는 업무) › 대화** (Liche Settings › Modes › Everyday (or Work) › Chat). See [Liche Settings](settings.md#models-and-thinking-depth-for-each-mode).

## Available agents

| Agent | ACP command Liche runs | macOS | Windows |
| --- | --- | --- | --- |
| Claude Code | `claude-agent-acp` | Select under **이 컴퓨터에서 찾은 연결** (Connections found on this computer) in first-run setup | Select under **다른 에이전트** (Other agents) in **연결 설정** (Connection settings) |
| Codex | `codex-acp` | Select under **이 컴퓨터에서 찾은 연결** in first-run setup | Select under **다른 에이전트** in **연결 설정** |
| OpenClaw | `openclaw acp` | Select under **이 컴퓨터에서 찾은 연결** in first-run setup | Select under **다른 에이전트** in **연결 설정** |
| Hermes | `hermes-acp` | Select under **이 컴퓨터에서 찾은 연결** in first-run setup | Hermes card in **연결 설정** |
| Other ACP agents | The project's ACP launch command | **에이전트로 연결하기** (Connect through an agent) | `LicheInput.exe --connect` ([below](#connecting-another-agent-on-windows)) |
| **리체 브릿지** (Liche Bridge) | Separate program | Not included in the retail package. Listed only if installed separately | Not included in the retail package. Its card appears only if installed separately |

Liche launches and talks to all agents in the same way, through ACP. Each project sets its own installation, login, and model usage requirements, which may change. Check first that the official project supports your operating system.

## Installing an agent

The commands and requirements below were **checked against official documentation and release information on 2026-11-02**. No fresh installations, logins, or connection tests were performed while preparing this guide. Installers may change, so also check each project's official instructions.

### Node.js and npm

The Claude Code and Codex ACP adapters, and OpenClaw, require Node.js/npm. Install the version for your operating system from the [official Node.js download page](https://nodejs.org/en/download). npm is included. Also see the [official npm installation guide](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).

- The Claude ACP adapter requires Node.js 22 or later.
- The current OpenClaw release requires **24.x from 24.22.1 onward, or 26.12.1 or later**. We recommend Node.js 26.13.0 if you use several agents together.
- Check your installation in Terminal (macOS) or PowerShell (Windows).

```sh
node -v
npm -v
```

### Claude Code + claude-agent-acp

1. Follow the macOS or Windows steps in the [official Claude Code installation guide](https://code.claude.com/docs/en/setup). Open Claude Code and sign in.
2. With Node.js/npm ready, install the ACP adapter.

```sh
npm install -g @agentclientprotocol/claude-agent-acp
```

Liche connects using `claude-agent-acp`. Check requirements in the [official ACP project](https://github.com/agentclientprotocol/claude-agent-acp). Claude Code and the adapter are separate programs.

### Codex + codex-acp

With Node.js/npm ready, install the adapter.

```sh
npm install -g @agentclientprotocol/codex-acp
```

Liche connects using `codex-acp`. **The adapter includes a compatible Codex, so a separate global Codex installation is not required.** If you also want the standalone Codex CLI, follow the [official Codex guide](https://developers.openai.com/codex/cli). See the [official ACP project](https://github.com/agentclientprotocol/codex-acp#installation) for authentication and installation details.

### OpenClaw + openclaw acp

Follow the [official installation guide](https://docs.openclaw.ai/install) and [Node.js requirements](https://docs.openclaw.ai/install/node). When installing through Node.js/npm, the command depends on your npm version.

**npm 11.16 or later, or npm 12:**

```sh
npm install -g openclaw@latest --allow-scripts=openclaw
```

**npm 11.15 or earlier:**

```sh
npm install -g openclaw@latest
```

After installation, follow the official instructions to set up the model, authentication, and Gateway. `openclaw acp` is a built-in connection feature and needs a working Gateway. See the [official ACP guide](https://docs.openclaw.ai/cli/acp) and [Windows guide](https://docs.openclaw.ai/platforms/windows).

### Hermes + hermes-acp

1. Follow the steps for your operating system in the [official Hermes installation guide](https://hermes-agent.nousresearch.com/docs/getting-started/installation).
2. Follow the [official ACP guide](https://hermes-agent.nousresearch.com/docs/user-guide/features/acp) to prepare the **ACP extra (`acp` extra)** too. Do not assume the base installation includes ACP. The source-folder example in the official ACP documentation is for macOS/Linux. Do not paste it unchanged on Windows.
3. Finish login and model setup, then select Hermes in Liche. Liche connects using `hermes-acp`. The official project also supports `hermes acp`.

This guide does not provide a separate command for installing the Hermes ACP extra on Windows. On Windows, follow the Windows steps in the [official Hermes ACP guide](https://hermes-agent.nousresearch.com/docs/user-guide/features/acp). You can also refer to the [commands and extras in the official source](https://github.com/NousResearch/hermes-agent/blob/main/pyproject.toml).

### The installation helper in Liche

If no agent is installed, Liche shows installation steps, commands to copy, and an **설치 안내** (Installation guide) link. **Liche does not install the agent for you.**

- **macOS:** Under **리체를 연결해 주세요** (Please connect Liche) in first-run setup, click a row marked **설치 안 됨** (Not installed). Click **복사** (Copy) beside a command and run it in Terminal. Liche checks again about every five seconds.
- **Windows:** Click **설치 방법 보기** (View installation steps) under **연결 설정 › 다른 에이전트** (Connection settings › Other agents). For Hermes, open the guide from its card. After installation, use **다시 확인** (Check again) to search.
- Once the agent is shown as installed, click its **연결하기** (Connect) button.

The helper guides you through the following steps. Installation commands come from the official projects and may change. Check their latest official requirements too.

| What to prepare | macOS | Windows PowerShell |
| --- | --- | --- |
| Node.js/npm | With Homebrew, `brew install node`. For an old version, `brew upgrade node`, or use the [official download](https://nodejs.org/en/download) | `winget install OpenJS.NodeJS` or the [official download](https://nodejs.org/en/download) |
| OpenClaw | `npm install -g openclaw@latest --allow-scripts=openclaw` | Same as macOS |
| Claude Code | `curl -fsSL https://claude.ai/install.sh \| bash`, then `npm install -g @agentclientprotocol/claude-agent-acp` | `irm https://claude.ai/install.ps1 \| iex`, then `npm install -g @agentclientprotocol/claude-agent-acp` |
| Codex ACP | `npm install -g @agentclientprotocol/codex-acp` | Same as macOS |
| Hermes base installation | `curl -fsSL https://hermes-agent.nousresearch.com/install.sh \| bash` | `irm https://hermes-agent.nousresearch.com/install.ps1 \| iex` |

Hermes also needs the ACP extra after the base installation. For the default source installation on macOS, run the following two commands in order. If you changed the installation location or Python environment, do not copy them unchanged. Follow the [official ACP guide](https://hermes-agent.nousresearch.com/docs/user-guide/features/acp). On Windows, follow that guide's Windows steps.

```sh
cd ~/.hermes/hermes-agent
python -c "import pm; pm.sync_venv(['acp'], explicit=True)"
```

If Node.js is too old, the helper treats the agent as not installed. For Hermes, it also checks ACP readiness with `hermes-acp --check`. Downloaded installation scripts come from the official projects. Check their source before running them.

## Connecting on macOS

Choose under **리체를 연결해 주세요** in first-run setup. If you closed it, return through **리체 연결하기** (Connect Liche) in the chat window or **리체 설정 › 연결 › 연결 설정 열기** (Liche Settings › Connections › Open connection settings).

- **이 컴퓨터에서 찾은 연결:** Liche searches PATH, `/opt/homebrew/bin`, `/usr/local/bin`, and `~/.local/bin`. Select an installed row and click **연결하기**.
- **에이전트로 연결하기:** If your agent is not listed or is installed elsewhere, click **복사** and paste the copied text into the agent you use. The agent registers Liche's MCP server and connects as her conversation partner.

## Connecting on Windows

In **연결 설정**, choose the Hermes card or OpenClaw, Claude Code, or Codex under **다른 에이전트**. If not installed, check the helper's official instructions first. You are done when **연결됨** (Connected) appears.

### Connecting another agent on Windows

For an ACP agent not in the list, pass `--connect` to the chat window program, `LicheInput.exe`. Liche saves that command and uses the same agent next time.

1. Leave Liche running.
2. Find the path to `LicheInput.exe` under `AgentLiche\Binaries\Win64` in the package.
3. In PowerShell, replace the path and command after `--` in this example, then run it.

```powershell
& "<package folder>\AgentLiche\Binaries\Win64\LicheInput.exe" --connect -- claude-agent-acp
```

A response beginning with `Connected` means the connection succeeded. Liche will not switch while waiting for a reply or while an approval request remains.

## What agents can do

- **Chat:** Continue separate Everyday and Work conversations. Per-mode working folders are `~/Liche/<모드>` on macOS and `Documents\Liche\<모드>` on Windows.
- **Approval requests:** Choose **승인** (Approve) or **거절** (Reject) before tool use. Liche does not approve automatically. See [Approval requests](#approval-requests) below.
- **Long tool tasks:** While the agent uses tools, the two-minute "응답이 없어요" (No response) limit does not apply. Liche stops waiting only after 30 minutes without an update. The chat shows "작업 중이에요 · 경과 시간" (Working · elapsed time). See [Reply waiting times](first-run.md#reply-waiting-times).
- **Long replies:** Text is shown as the agent sends it. Even a long paragraph without blank lines appears line by line instead of all at once at the end.
- **Liche's MCP server:** Agents can change expressions and actions and show short speech bubbles. This server cannot read chat history, settings, or keys.
- **Models and thinking depth:** Choose each under **리체 설정 › 모드 › 일상(또는 업무) › 대화**. **에이전트 기본값** (Agent default) uses the agent's own value. What you can choose differs by agent. See [Models and thinking depth by agent](#models-and-thinking-depth-by-agent) below.
- **Attachments:** The attachment button appears only if the connection supports it. Features vary by agent.

## Approval requests

When the agent asks before using a tool, such as editing files or running commands, the chat window shows **확인이 필요해요** (Your confirmation is needed) with **승인** (Approve) and **거절** (Reject).

- Liche answers with the option, among those the agent sent with its request, that allows or rejects **this one time only**. She never picks a lasting rule such as "always allow".
- **■ 중지** (Stop) or a lost connection cancels all pending requests.
- The agent decides what it asks about. Claude Code follows your own Claude Code permission setting (`permissions.defaultMode`), and Hermes asks before editing files by default.

### How Codex asks for approval

Liche connects Codex in **Workspace access** mode. In this mode, Codex asks for approval in the chat window **before writing files outside its work folder and the temporary folders, or before using the network**. In codex-acp's default mode ("Auto review"), Codex's own reviewer model approves its requests and nothing reaches you, so Liche chooses this mode when it connects.

- You cannot change Codex's mode in Liche. codex-acp does not read the approval setting in `~/.codex/config.toml` either.
- If Codex asks to run a command that needs more than its workspace allows and you choose **거절** (Reject), Codex stops that turn and ends without a reply. Only your rejection line stays in the chat. Tell it what to do differently.

## Models and thinking depth by agent

Liche shows the models and thinking depths the connected agent reports. A choice in **리체 설정** (Liche Settings) applies to that mode's conversation right away, and the thinking depths of the chosen model appear again at once. Liche does not change the agent's own setting files.

| Agent | Model | Thinking depth |
| --- | --- | --- |
| Claude Code | The model list Claude Code reports | The depths the chosen model takes (for example, 낮음 (Low) to 최대 (Max)) |
| Codex | The model list Codex reports | Differs by model; some models lack some depths |
| OpenClaw | No list; only **에이전트 기본값** (Agent default) appears | OpenClaw's thinking levels (끔 (Off), 최소 (Minimal), 낮음 (Low), 보통 (Medium), 높음 (High), 자동 (Adaptive)) |
| Hermes | The model Hermes reports | Not available; the row says "이 모델은 생각 깊이를 고르지 않아요" (This model does not take a thinking depth) |

The lists can differ by agent, its version, and your account. The settings rows are described in [Liche Settings](settings.md#models-and-thinking-depth-for-each-mode).

## When the connection fails or "Not responding" appears

When an agent cannot start, Liche reads the reason and shows it on the connection screen, in the chat window, and under **리체 설정 › 연결** (Liche Settings › Connections), with the command to run and a **다시 연결** (Reconnect) button. Status names and what to do for each reason are collected in [When the connection fails](troubleshooting.md#when-the-connection-fails) in Troubleshooting.

### When the agent does not respond

If no response arrives within 45 seconds of launching the agent, the connection card and chat window show "(agent)가 응답하지 않아요" ((Agent) is not responding).

1. If an operating-system permission dialog is open, check the requesting program and request, then respond.
2. Open the agent directly and finish login and model setup.
3. Check the installation location and ACP extra components.
4. Liche tries reconnecting after a short wait. To try at once after fixing it, click **다시 연결** (Reconnect).
5. If the problem remains, [contact support with diagnostics](troubleshooting.md#what-to-include-when-contacting-support).

## Changing or disconnecting an agent

Selecting a new agent on the connection screen changes the saved connection. If you pick another agent while one is connected, the button changes to **연결하기** (Connect); click it and both Everyday and Work reconnect to the new agent. You cannot switch while either mode is waiting for a reply or has a pending approval request. Click **■ 중지** or wait for it to finish.

When you switch agents or quit Liche, Liche ends that agent together with the commands it started. **■ 중지** only stops the current reply and leaves the agent running, so the agent decides whether a program it was running stays.

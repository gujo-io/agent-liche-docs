# First run

[Guide home](../README.md) · [한국어](../../docs/first-run.md)

The first time you launch Liche, she guides you through connecting an agent. The setup looks different on macOS and Windows.

## Liche before an agent is connected

Liche's replies come from the connected agent, so she cannot answer without one. Until then, she dozes inside her card with Zz above her head. When an agent connects, she wakes up and returns to normal.

- Liche does not doze because time has passed. She dozes only when there is no connection or the connection is lost.
- Click her while she is dozing to wake her briefly. She then dozes again.
- If your connected agent does not respond, a gray **연결 안 됨 — 지금은 보낼 수 없어요** (Not connected — can't send right now) appears at the bottom of the chat window, above the input box. The card shows no status text: Liche dozes with Zz above her head. While she waits for a reply, a thought bubble floats above her head.

## macOS: full-screen first-run setup

On macOS, the first launch begins with a short story that fills the screen. Use the **이전** (Previous) and **다음 단계** (Next step) arrows at the top to move between steps.

1. **"어디선가 새근새근 숨소리가 들려요"** (You hear someone breathing softly): Click **살짝 깨워 볼까?** (Shall we gently wake her?). You can read the [End User License Agreement (EULA, Korean)](../../legal/eula.md) through **사용권 계약 (EULA) 보기** (View license agreement (EULA)) below.
2. **"으음... 여기서 나가고 싶어요..."** (Mmm... I want to get out of here...): Liche appears and speaks for the first time. Click **내가 꺼내 줄게** (I'll get you out).
3. **"리체를 연결해주세요"** (Please connect Liche): Choose an agent. **리체의 대답은 연결한 AI 에이전트가 만들어요.** (Liche's replies come from the connected AI agent.) There are two ways.
   - **에이전트로 연결하기** (Connect through an agent): Let an agent you already use handle the connection. Click **복사** (Copy) to copy connection instructions to the clipboard. Paste them into your agent, such as Claude Code or Codex in a terminal. The agent connects itself to Liche. This row shows **연결됨** (Connected) when done.
   - **이 컴퓨터에서 찾은 연결** (Connections found on this computer): A list of agents Liche found on this Mac. It includes OpenClaw, Hermes, Claude Code, and Codex. Each row shows a status on the right, such as **설치 안 됨** (Not installed), **찾는 중** (Searching), **연결 중** (Connecting), **연결됨**, or **확인 필요** (Needs attention). Select an installed row, then click **연결하기** (Connect).
   - Installed agents appear first. **리체 브릿지** (Liche Bridge) is a separate program not included in the retail package. It appears only if you installed it separately on this Mac.
   - Click a **설치 안 됨** row to see installation steps and commands to copy. Liche does not install the agent for you. She checks again every few seconds after installation. See [The installation helper in Liche](agents.md#the-installation-helper-in-liche).
   - Once connected, the button changes to **다음** (Next).
4. **"감정 판단 (JEV) · 선택"** (Emotion judgment (JEV) · Optional): An optional step to enable emotion judgment. If you have a key, click **키 입력** (Enter key) and enter it. Otherwise, click **건너뛰기** (Skip). Liche still reacts using preset rules if you skip this step. See [Emotion judgment (JEV)](jev.md) for details. This step does not appear if the judgment program is missing from the installation.
5. **"세부 설정을 확인해주세요"** (Please check the detailed settings): Shows the connected agent and widget status. Click **리체 내보내기** (Let Liche out) to close setup and bring Liche to her desktop card.

Pressing `Esc` or closing the window during setup ends it without connecting. To reopen it at the connection step, click **리체 연결하기** (Connect Liche) in the chat window or **리체 설정 › 연결 › 연결 설정 열기** (Liche Settings › Connections › Open connection settings).

If 30 seconds pass after saving a connection without connecting, you see "연결을 저장한 지 30초가 지났어요. 그쪽 프로그램의 로그인 같은 자체 설정을 먼저 끝내 주세요." (It has been 30 seconds since the connection was saved. Please finish that program's own setup, such as signing in, first.) Run the agent once in a terminal to finish signing in, then select it again.

## Windows: chat guidance and connection settings

On Windows, Liche starts directly as a card without full-screen setup.

1. The chat window shows **"리체가 아직 바깥과 연결되지 않았어요"** (Liche is not connected to the outside yet) and **"리체의 대답은 연결한 AI 에이전트가 만들어요."** (Liche's replies come from the connected AI agent.) Click **연결 설정** (Connection settings). Read the [End User License Agreement (EULA, Korean)](../../legal/eula.md) through **사용권 계약 (EULA)** (License agreement (EULA)) beside it.
2. The **연결 설정** window opens with connection cards and "리체랑 이야기할 길을 골라 줘." (Choose a way to talk with Liche.)
   - **Hermes:** Talk through the Hermes agent.
   - **리체 브릿지:** A separate program that holds Liche's memories and personality. It is not included in the retail package. Its card appears only if you installed Liche Bridge separately on this PC.
3. Each card shows **설치됨** (Installed), **설치 안 됨**, **연결 중**, **연결됨**, or **확인 필요**. Click an **설치됨** card once to save it and connect immediately.
4. If you just installed an agent, click **다시 확인** (Check again) to search again.
5. Once connected, the card shows **연결됨**. Click **닫기** (Close) to close the window.

Click **감정 판단 켜기 (선택)** (Enable emotion judgment (optional)) at the bottom of connection settings to open the JEV key window. Enabling it sends part of your conversation to TypeSafe AI in the United States. You need your own JEV key and separate credits. Only input tokens are charged. You can leave this alone if you have no key.

Claude Code, Codex, and OpenClaw are under **다른 에이전트** (Other agents) at the bottom. Use **연결하기** to connect. If an agent is not installed, click **설치 방법 보기** (View installation steps). See [Connecting an agent](agents.md) for official installation instructions.

You can reopen connection settings later through **리체 설정 › 연결 › 연결 설정 열기**.

## Your first conversation

If there is no chat history, Liche speaks first. Write in the input field at the bottom of the chat window and press `Enter` to send.

- `Shift+Enter`: New line
- You cannot send another message in the same mode while waiting for a reply. Your draft stays in the input field.
- **■ 중지** (Stop): Stops the current reply.
- When the agent wants to edit files or run commands, **확인이 필요해요** (Your confirmation is needed) appears with **승인** (Approve) and **거절** (Reject) buttons. Liche does not approve on her own.
- See [Reply waiting times](#reply-waiting-times) below for how long Liche waits.

### Reply waiting times

| Situation | How long Liche waits | What the chat shows |
| --- | --- | --- |
| The agent is thinking or writing | **2 minutes (120 seconds)** since the last update | After two minutes without an update, Liche leaves "응답이 없어요" (No response) and stops waiting |
| The agent is using tools (reading/editing files, running commands, waiting for approval, and so on) | **No two-minute limit.** Stops only after **30 minutes** without an update | Shows time since sending, such as "작업 중이에요 · 3분 12초" (Working · 3 minutes 12 seconds). After 30 minutes without an update, shows "작업이 30분 넘게 아무 소식이 없어서 기다리기를 멈췄어요" (I stopped waiting because there has been no update on the task for over 30 minutes) |

- Every tool progress update restarts the 30-minute timer. Liche keeps waiting for long builds or tests as long as updates continue.
- The tool timeout applies to ACP agents such as Claude Code, Codex, OpenClaw, and Hermes. Liche Bridge connections use only the two-minute rule.
- If 30 minutes does not suit you, set the environment variable `LICHE_INPUT_TOOL_TIMEOUT_MINUTES` to a number of minutes from 2 to 1440 (24 hours). Liche reads it once at startup.
  - Windows: In the user variables under **Settings › System › About › Advanced system settings › Environment Variables**, add the name `LICHE_INPUT_TOOL_TIMEOUT_MINUTES` with a value such as `60`, then restart Liche.
  - macOS: Run `launchctl setenv LICHE_INPUT_TOOL_TIMEOUT_MINUTES 60` in Terminal, then restart Liche. This value is cleared when you restart your Mac.
- You can stop waiting at any time with **■ 중지**.

## Basic controls

| What you want to do | How |
| --- | --- |
| Reveal icons | Hover briefly over **⋯** (More) at the top right of the card. Icons unfold below it |
| Pin Liche above other windows | Click **고정핀** (Pin) among the unfolded icons. Click again to unpin |
| Move the card | Drag the **위치이동** (Move) icon. You can also hold `⌥` (macOS) or `Alt` (Windows) and drag anywhere on the card where Liche is visible |
| Resize the card | Drag inside a rounded corner of the glass card. Size ranges from 60% to 160%. Right-click while dragging to cancel. After releasing, briefly visible **100%로** (Reset to 100%) restores the original size |
| Detach or attach the chat window | Use the attach/detach button in the chat header, or choose under **리체 설정 › 창 › 대화창 배치** (Liche Settings › Window › Chat layout). The same area also has **대화창 스타일** (Chat window style): **떠 있는 창** (floating window) or a bordered classic window |
| Open settings | Click **설정** (Settings), the gear among the unfolded icons, to open **리체 설정** (Liche Settings). The gear in the chat header goes directly to model and thinking-depth settings for the current mode |
| Switch between Everyday and Work | Click the speech-bubble icon (Everyday) or the `</>` icon (Work) at the top of the chat window |
| Find a lost card | Click **옮기기** (Move) under **리체 설정 › 창 › 카드를 화면 가운데로** (Liche Settings › Window › Center card on screen). See [Troubleshooting](troubleshooting.md) |

### Everyday and Work modes

Liche has two conversations.

- **일상** (Everyday): A conversation for casual chat. By default, Liche wears pajamas without glasses.
- **업무** (Work): A conversation for tasks. By default, Liche wears a maid outfit and glasses. She types on a laptop while the agent works.

Each conversation has its own history, connection, pending reply, and approval requests. Switching modes does not stop work in the other mode. If a new reply or approval request arrives in the mode you are not viewing, an orange dot appears on that mode's icon and you receive a notification. Choose clothes and glasses for each mode in [Liche Settings](settings.md).

## Next steps

- [Connecting an agent](agents.md)
- [Liche Settings](settings.md)
- [Guide files](guides.md)

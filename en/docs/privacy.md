# Privacy and data

[Guide home](../README.md) · [한국어](../../docs/privacy.md)

This page explains what Liche leaves on your computer and when she connects outside it. Personal information for your Gujo account and the store is handled under the [Gujo Privacy Policy](https://account.gujo.io/en/privacy).

## At a glance

- Chat history and settings are saved on your computer, not uploaded to the seller's servers.
- Liche does not collect usage statistics (telemetry) or automatically upload crash reports.
- Retail Liche does not open ports for incoming connections. Agent connections also run between programs on the same computer.
- Liche's replies come from the connected AI agent. The agent may send conversations to its AI service to create replies.
- JEV is optional. Information needed for judgment goes to TypeSafe AI in the United States only when you enable it and enter a key.
- New version notifications check a small file that the Gujo store makes for the product. The store can learn your IP address during this check. You can turn it off.

## AI notice

**리체의 대답은 연결한 AI 에이전트가 만들어요.** (Liche's replies come from the connected AI agent.) The Liche app does not create replies herself. She displays replies from your chosen agent, such as Claude Code, Codex, OpenClaw, or Hermes, and reacts with expressions. AI replies may be wrong. Check important information and any action the agent wants to take yourself. Liche shows the same notice at the connection step during first-run setup and under **리체 설정 › 리체 정보** (Liche Settings › About Liche).

## What stays on your computer

| Information | What is stored |
| --- | --- |
| Chat history | Everyday and Work history, and app-specific copies of attachments |
| Settings and card position | Display, notifications, performance, per-mode clothing, models and thinking depth, position, size, and pin state |
| Connection settings | Agent program path and launch arguments. Liche does not store the agent's login information or API keys |
| Guide files | Guides defining Liche's personality, tone, and more. Default guides are included at first, and you can edit them. The agent reads them |
| JEV key | In the macOS login keychain or a file encrypted for the Windows user account |
| Diagnostic logs and crash reports | Local records for troubleshooting, such as connection status and errors |
| Update check record | Last check time and the version information received then (`update-check.json`) |

See [Uninstalling on Windows](install-windows.md#6-uninstalling) or [Uninstalling on macOS](install-mac.md#7-uninstalling) for exact locations and removal steps. You can also open the data folder through **리체 설정 › 일반 › 기록 폴더 › 폴더 열기** (Liche Settings › General › History folder › Open folder).

## External connections

The table below lists everything Liche herself sends over the network. The program that renders the character does not connect to the network.

| Who | Destination | When | What is sent | How to turn it off |
| --- | --- | --- | --- | --- |
| Update check in the chat window program | `https://app.gujo.io/products/287/latest.json` (the version information file the Gujo store makes from the product's published files) | Automatically up to once a day, starting 30 seconds after launch; also when you open **리체 정보** (About Liche), up to once every 10 minutes | Only a request for the file. No query string, browser information (User-Agent), cookies, account information, or device information is sent. HTTPS only, and redirects are not followed. The store can learn your IP address during the connection | Turn off **리체 설정 › 리체 정보 › 새 버전 알림** (Liche Settings › About Liche › New version notifications) |
| Emotion judgment program `liche-judge` (optional) | `https://api.typesafe.ai/v1/systemone` (TypeSafe AI, United States) | Only when JEV is enabled and your own key is saved. Once to validate a saved key, then twice per judged exchange | Your message in that exchange, Liche's reply and speech bubbles, up to five preceding exchanges, Liche's personality description and mood, and the key attached to the request | Turn off **리체 설정 › 연결 › 감정 판단 (JEV) · 선택** (Liche Settings › Connections › Emotion judgment (JEV) · Optional), or have no key saved |
| Legacy file classification window in the chat window program | `/v1/systemone` on the server specified in your environment variables | Only when both the server address and key are set in environment variables and you drop a file into the old standalone window. There is no default server | The dropped file's name and the world name | Does not run without those environment variables (the default) |
| Default browser or mail app | Guide, license agreement, third-party notices, support, store pages, and links in conversations | Only when you click a link | The usual information a browser sends when opening a page | Does not open unless clicked |

The update check does not download or install files based on the response. It reads at most 64 KiB and uses only `https` links to the store (`app.gujo.io`, `asset.gujo.io`) and guide (`github.com`) from the received file. The legacy file classification window passes the key and request through `curl` standard input, so other programs cannot see the key on the command line.

### The agents you connect

Claude Code, Codex, OpenClaw, Hermes, and similar agents are **separate programs you install and run on your computer**. Liche passes messages, attachments, and approval responses through standard input/output. Agents may send content to their AI services to create replies. Installing an agent or running it through `npx` may also connect to download that program. These connections belong to that program, not Liche. The program's and service's own terms and policies apply.

The same principle applies to a separately connected `brain` CLI or Liche Bridge. Uninstalling Liche leaves agents and their records in place.

Liche's MCP connection uses local standard input/output, not a network server. Agents can use it to change expressions and actions or show short text (up to 500 characters). They cannot read chat history, settings, or keys through it.

### Connections Liche does not make

- The Liche character-rendering program makes no network connections. Usage statistics collection, remote tracing, and incoming-connection features are excluded from the retail package.
- Errors may leave crash reports on your computer, but the package does not include a crash-report uploader.
- No program in the retail package opens listening ports, so no firewall permission dialog should appear.

## Creating a diagnostic file

Click **리체 설정 › 리체 정보 › 진단 파일 만들기** (Liche Settings › About Liche › Create diagnostic file) to create a support zip on your desktop (`Liche-diagnostics-날짜-시각.zip`). This only creates the file. It is not sent automatically.

- **Included:** Diagnostic logs from the chat window and character programs, crash reports from the last 30 days (excluding memory dumps), settings files, app version, operating-system and display information, and a list of files omitted from collection.
- **Excluded:** Chat history files, attachments, JEV key files, memory dumps, and launch arguments from the saved connection.
- **Redacted:** Chat text in logs, keys and tokens, account and computer names, email addresses, and usernames in paths. Only the character count is kept for chat text.

Redaction looks for known formats and cannot guarantee removal of every sensitive detail. Open the zip and check its contents before sending it. You can remove files you do not want to send. See [Troubleshooting](troubleshooting.md#what-to-include-when-contacting-support) for contact details.

## Notifications and approval requests

When **내용 미리보기** (Content preview) is on, operating-system notifications show the beginning of a reply, up to 100 characters. If others can see your screen, turn off **리체 설정 › 알림 › 내용 미리보기** (Liche Settings › Notifications › Content preview).

When an agent requests permission to use a tool, Liche waits for **승인** (Approve) or **거절** (Reject). She does not approve on her own or take focus from other windows. Check the request before responding.

## Deleting data

| What to delete | How |
| --- | --- |
| Everyday and Work chat history and attachments | Open the folder with **리체 설정 › 일반 › 기록 폴더 › 폴더 열기** (Liche Settings › General › History folder › Open folder), quit Liche, then delete `history-daily.jsonl`, `history-developer.jsonl` and the `attachments` folder inside `chat`. This cannot be undone. Delete what an agent remembers of the conversation in that agent |
| JEV key | [Deleting a key](jev.md#deleting-a-key) |
| All Liche data | Quit Liche and delete the data folders listed for [Windows](install-windows.md#6-uninstalling) or [macOS](install-mac.md#7-uninstalling) |
| Data from an earlier version (Windows 0.1.0) | [Cleaning up old folders](updates.md#cleaning-up-old-folders) |
| Data held by an agent or TypeSafe AI | Follow that service's instructions and privacy policy |

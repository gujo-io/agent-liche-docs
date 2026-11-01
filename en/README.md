# Agent Liche User Guide

[한국어](../README.md)

Agent Liche is an AI assistant who lives on your desktop. Liche is a 3D character made with Unreal Engine. She stands inside a translucent glass card, and you talk with her in the chat window beside it.

Liche's replies come from the AI agent you connect yourself. She exchanges messages with agents such as Claude Code, Codex, OpenClaw, and Hermes, and changes her expression to match the conversation. In Work mode, she types on a laptop while the agent works. When the agent wants to edit files or run commands, the chat window asks for your permission first.

This guide is for buyers of [Agent Liche](https://asset.gujo.io/products/287?lang=en) (product 287) from the Gujo store. The seller is Ranode.

> This guide covers **0.2.0**. Version 0.2.0 starts with empty settings, chat history, layout, and connections. If you used an earlier version, read [Updating](docs/updates.md) first. See the [Changelog](CHANGELOG.md) for changes and known issues.

## Supported systems

| Platform | Systems supported by 0.2.0 | Signing |
| --- | --- | --- |
| Windows | Windows 11 64-bit (x64), with a graphics card that supports DirectX 12 (Shader Model 6) | Not code-signed. SmartScreen appears on first launch ([instructions](docs/install-windows.md#when-windows-protected-your-pc-appears-smartscreen)) |
| macOS | macOS 14 or later, on an Apple Silicon (M1 or later) Mac | Developer ID signed and notarized by Apple |

- **Windows 10 and ARM-based Windows are not supported.** There is one x64 package.
- **Intel Macs are not supported.** Pre-release testing used macOS 26 and 27.
- No minimum CPU or memory requirements are specified. Liche renders a 3D character continuously. On a laptop or older PC, we recommend **절약** (Power saving) under **리체 설정 › 성능** (Liche Settings › Performance).
- You need at least 1 GB of free space on Windows or 1.5 GB on macOS to keep both the downloaded archive and the extracted app.
- One purchase includes both the Windows and macOS downloads for this product. Agent accounts, subscriptions, and API fees, as well as fees for the optional JEV feature, are separate.

## Quick start

1. Install Liche. Follow [Windows installation](docs/install-windows.md) or [macOS installation](docs/install-mac.md).
2. Prepare an AI agent to connect to Liche. Agents are not included with Liche. Install one separately and arrange its account or subscription separately. See [Connecting an agent](docs/agents.md) for your options.
3. Launch Liche for the first time and follow the steps to connect your agent. See [First run](docs/first-run.md).
4. Write your first message in the chat window and press `Enter` to send it. Press `Shift+Enter` for a new line.
5. For richer emotional expressions, turn on [Emotion judgment (JEV)](docs/jev.md). Without it, Liche still reacts using preset rules.

## Guide contents

| Page | Contents |
| --- | --- |
| [Installing and uninstalling on Windows](docs/install-windows.md) | Downloading, checking files, first launch, SmartScreen and firewall dialogs, quitting, uninstalling, and data locations |
| [Installing and uninstalling on macOS](docs/install-mac.md) | Downloading, moving to Applications, the Gatekeeper confirmation, permissions, uninstalling, and data locations |
| [First run](docs/first-run.md) | First-run setup, Liche without an agent, basic controls, and reply waiting times |
| [Connecting an agent](docs/agents.md) | Available agents, connection steps for each platform, and what to do when "응답하지 않아요" (Not responding) appears |
| [Emotion judgment (JEV)](docs/jev.md) | What judgment does, calls and fees, entering and storing a key, and information sent outside your computer |
| [Liche Settings](docs/settings.md) | Settings pages and options, and models and thinking depth for each mode |
| [Guide files](docs/guides.md) | Files that define Liche's personality and tone, default guides, and when files are recreated |
| [Privacy and data](docs/privacy.md) | Local data, a complete list of external connections, and deleting data |
| [Troubleshooting](docs/troubleshooting.md) | Frequently asked questions and known issues |
| [Updating](docs/updates.md) | Switching to a new version and cleaning up old folders |
| [Changelog](CHANGELOG.md) | Changes and known issues by version |
| [Third-party notices](legal/third-party-notices.md) | Other companies' software and fonts included with Liche, and notice file locations |

## Getting help

Contact us below if you have a problem. Use **리체 설정 › 리체 정보 › 진단 파일 만들기** (Liche Settings › About Liche › Create diagnostic file) to make a support zip file. It excludes chat history, attachments, and JEV key files, and redacts chat text, keys, and tokens in logs. It is not sent automatically. Check its contents, then attach it yourself. Also see the contact guidance in [Troubleshooting](docs/troubleshooting.md).

- Email: help@ranode.net
- Support: https://support.gujo.io
- Phone: 010-2193-6227 (weekdays, 10 a.m. to 6 p.m.)

## Terms and policies

- [End User License Agreement (EULA, Korean)](../legal/eula.md)
- [Terms of Service](https://account.gujo.io/en/terms)
- [Refund Policy](https://account.gujo.io/en/refund)
- [Privacy Policy](https://account.gujo.io/en/privacy)

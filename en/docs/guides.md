# Guide files

[Guide home](../README.md) · [한국어](../../docs/guides.md)

Guide files define Liche's personality, tone, and what she should or should not do. They are plain text files in Markdown format. When starting a new conversation, Liche includes their locations in the first message, and the agent reads them. These are your files, so you can edit them freely.

## Guide folder location

| Platform | Location | Path shown in settings |
| --- | --- | --- |
| macOS | `Liche` in your home folder (`~/Liche`) | `홈/Liche/…` |
| Windows | `Liche` in Documents (`Documents\Liche`) | `Documents\Liche\…` |

## Folder structure

```text
Liche/
├── common.md            Common guide: both modes read it first (includes default content)
├── daily/               Everyday mode folder (where the agent works in Everyday chats)
│   ├── AGENTS.md        Everyday entry file (no default content; create it if you want)
│   ├── daily.md         Everyday guide (includes default content)
│   └── skills/          Skills for Everyday mode
└── developer/           Work mode folder (where the agent works in Work chats)
    ├── AGENTS.md        Work entry file (no default content; create it if you want)
    ├── developer.md     Work guide (includes default content)
    └── skills/          Skills for Work mode
```

- Each mode's agent uses that mode's folder as its working folder. If you ask the agent to create a file in Work mode without specifying a path, it may be created in `developer`.

## Default guides

Starting with 0.2.0, Liche includes **default guides** for `common.md`, `daily/daily.md`, and `developer/developer.md`. They define her personality, tone, reply length for small speech bubbles, expression tags, and each mode's role, so a fresh installation can reply in character from the start. The default guides are written in Korean.

- **Created only when missing.** If a file is missing when Liche starts, when a mode's conversation starts, or when you click **열기** (Open) for that file in settings, Liche creates it with the default guide.
- **Your files are never overwritten.** Existing files stay as they are, whether edited, empty, or replaced with different content. Updates do not change them.
- **Deleted files return.** If you delete a default guide file, Liche recreates it with default content on the next launch.
- **Leave a file empty to disable its guide.** Liche does not refill empty files.
- **To restore the original content, delete that file and restart Liche.**
- `AGENTS.md` has no default guide. Liche points the agent directly to the three files, so the agent does not read the same content twice.
- If the folder is not writable, Liche skips creating the file.

### Requests outside the current mode

The default guides tell Liche to **suggest the other mode once, then help in the current mode if you prefer** when you ask for work in Everyday mode or chat casually in Work mode. She does not refuse a request because of the mode. Edit the guide files if you want different behavior.

## The order Liche uses for guides

When starting a new conversation, Liche gives the agent the file locations in this order. Missing files are skipped.

1. `common.md`
2. That mode's `AGENTS.md`
3. That mode's guide file (`daily.md` or `developer.md`)

Guide edits apply from that mode's next conversation. Restart Liche to apply them to the conversation you are continuing now.

`AGENTS.md` is an entry file that many agents look for and read first in their working folder. How the `skills` folder is used depends on the agent. Check your agent's instructions.

## Opening files

1. Open **리체 설정 › 모드** (Liche Settings › Modes).
2. Click **일상** (Everyday) or **업무** (Work) to open that mode's page.
3. In **지침** (Guides), click **열기** for **공통 지침** (Common guide), **일상 지침** (Everyday guide), or **업무 지침** (Work guide). The file opens in your default text editor. If missing, it is created with default content first.
4. To view a whole folder, click **폴더 열기** (Open folder) for **일상 폴더** (Everyday folder) or **업무 폴더** (Work folder). You can also use **폴더 열기** under **지침 폴더** (Guide folder) on the Modes page.

## Example edits

Here are examples to add to or replace parts of the default guides. Change them as you like.

### Adding to `common.md`

```markdown
## About me

- Call me "Master."
- Keep replies short and polite.
- Say when you do not know something.
```

### Adding to `daily/daily.md`

```markdown
- Keep our chats light here.
- If I ask for code work or file organization, suggest Work mode once. If I still ask you to do it, go ahead.
```

### Adding to `developer/developer.md`

```markdown
- Always ask before deleting or overwriting files.
- When a task is done, summarize what you did in three lines.
```

## Things to know

- How well guides are followed depends on the connected agent and model.
- Guide files stay on your computer. Check this folder yourself before deleting it when uninstalling Liche ([Windows](install-windows.md#6-uninstalling), [macOS](install-mac.md#7-uninstalling)).
- Do not put passwords or API keys in guide files. The agent reads these files and may send their contents to its AI service.

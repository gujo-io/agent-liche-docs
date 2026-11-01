# Installing and uninstalling on Windows

[Guide home](../README.md) · [한국어](../../docs/install-windows.md)

## What you need

- A Windows 11 64-bit (x64) PC. **Windows 10 and ARM-based Windows are not supported.**
- A graphics card that supports DirectX 12 (Shader Model 6). No minimum CPU or memory requirements are specified.
- At least 1 GB of free space for both the downloaded zip file and the extracted folder.
- An AI agent installed and signed in separately. See [Connecting an agent](agents.md).

## 1. Downloading

Sign in to the Gujo store and download the Windows zip for Agent Liche from your library. If you use Gujo Cloud Apps, follow the installation instructions for this product.

### Checking your download (optional)

The 0.2.0 Windows release is not code-signed. The size and SHA-256 below let you check that your download matches the file distributed by the store.

| File | Size (bytes) | SHA-256 |
| --- | --- | --- |
| `RELEASE_FILL_WINDOWS_ZIP_NAME` | `RELEASE_FILL_WINDOWS_ZIP_BYTES` | `RELEASE_FILL_WINDOWS_ZIP_SHA256` |

Replace the file name in this PowerShell command to get its SHA-256. If even one character differs from the table, do not run the file. Contact support.

```powershell
Get-FileHash -Algorithm SHA256 "$env:USERPROFILE\Downloads\<downloaded zip file name>"
```

## 2. Extracting

1. Right-click the zip and choose **Extract All…** (Korean Windows: **모두 압축 풀기…**).
2. Extract it to a folder you will not move often. Automatic startup remembers the executable's location.
3. **Keep `AgentLiche.exe` at the top of the extracted folder together with the `AgentLiche` folder beside it.** Moving only the executable prevents the app from running.

The folder looks like this.

```text
<extracted folder>\
├── AgentLiche.exe              Launcher for Liche (double-click this)
├── THIRD-PARTY-NOTICES.txt     Third-party notices
├── AgentLiche\
│   └── Binaries\Win64\
│       ├── AgentLiche-Win64-Shipping.exe   Liche character program
│       ├── LicheInput.exe                  Chat window program
│       └── liche-judge.exe                 Emotion judgment (JEV) program
└── Engine\                     Engine files
```

## 3. First launch

1. Double-click **`AgentLiche.exe`** at the top level. You do not need to find and run the files inside `AgentLiche\Binaries\Win64`.
2. If **"Windows protected your PC"** appears (Korean: "Windows의 PC 보호"), follow the [SmartScreen instructions](#when-windows-protected-your-pc-appears-smartscreen) below.
3. If your PC lacks the Visual C++ runtime, a dialog says "The following component(s) are required to run this program … Would you like to install them now?" Click **Yes** (Korean Windows: **예**) to install the Microsoft Visual C++ Redistributable included in the package. Liche continues launching after installation.
4. The glass card and chat window appear on your desktop.
5. Connect an agent by following [First run](first-run.md). Liche's replies come from the connected AI agent.

### When "Windows protected your PC" appears (SmartScreen)

**The 0.2.0 Windows release is not code-signed.** Microsoft Defender SmartScreen therefore shows "Windows protected your PC" on first launch, with **Unknown publisher** as the publisher. On Korean Windows, these are "Windows의 PC 보호" and **알 수 없는 게시자**. Code signing is planned for the next update.

1. Check that you downloaded the file from the Gujo store. [Checking the SHA-256](#checking-your-download-optional) above gives extra assurance.
2. Click **More info** (Korean: **추가 정보**).
3. Check that the app name is `AgentLiche.exe`, then click **Run anyway** (Korean: **실행**).

If the dialog appears again, follow the same steps. Do not run a file from an unknown source or one that Microsoft Defender detects as malicious. Contact support instead. Do not disable SmartScreen or Microsoft Defender entirely.

On PCs with **스마트 앱 컨트롤** (Smart App Control) enabled in Windows Security, launch may be blocked without a **Run anyway** button. We do not recommend turning off Smart App Control because it changes security for the whole PC. Contact support in this case.

### When a firewall dialog appears

The retail Liche program does not open a port for incoming connections. It does not need permission for incoming connections, and Windows Firewall should not normally show a dialog. If a firewall permission dialog appears for Liche, do not allow it. Send support the version and the dialog's contents. For dialogs from a separately installed agent, follow that program's instructions. See [External connections](privacy.md#external-connections).

## 4. Quitting

- Click Liche's card, press `Alt+Space` to open the window menu, then choose **Close**. You can also open this menu by holding `Shift` and right-clicking Liche's taskbar button.
- If Liche will not quit, open Task Manager (`Ctrl+Shift+Esc`), select `AgentLiche-Win64-Shipping.exe` on the **Details** tab, and click **End task**. The **Processes** tab lists the launcher, character program, and chat window program all as Agent Liche.
- The chat window program, `LicheInput.exe`, quits with Liche.

## 5. Starting automatically at login

Turn on **리체 설정 › 일반 › 컴퓨터를 켜면 리체도 시작** (Liche Settings › General › Start Liche when the computer starts). This creates `Agent Liche Auto Connect.lnk` in the Startup folder. Liche and the saved connection start together when you sign in.

If you move the folder or change versions, turn the switch off and on again. Liche changes only this shortcut and leaves other startup programs alone.

## 6. Uninstalling

If you installed Liche from a zip, delete its folder. There is no installer, so it does not appear under **Settings › Apps**. If you installed through Gujo Cloud Apps, uninstall it in that client first. Then delete any data folders below that remain.

1. While Liche is running, turn off **컴퓨터를 켜면 리체도 시작** (Start Liche when the computer starts). If you already deleted the app, open `shell:startup` with `Win+R` and delete `Agent Liche Auto Connect.lnk`.
2. To delete your JEV key, click **키 지우기** (Delete key) in the key window. Deleting `%LOCALAPPDATA%\LicheWidget` below also deletes the key file.
3. Quit Liche and delete the entire extracted program folder.
4. Copy any files you need first, then delete the data folders below. **Deleted conversations and files you created cannot be recovered.**

| Location | Contents |
| --- | --- |
| `%LOCALAPPDATA%\LicheWidget` | Chat history (`chat\history-daily.jsonl`, `chat\history-developer.jsonl`) and attachments, saved connection (`chat\connection.json`), display/notification/performance settings, card position, JEV key (`chat\judge\typesafe.dpapi`), and logs (`logs`) |
| `Documents\LicheWidget` | Widget settings `settings.json` and error records (`settings.error.txt`, `input.error.txt`) |
| `Documents\Liche` | Guide files (`common.md`, `daily\daily.md`, `developer\developer.md`) and per-mode agent working folders. Check for files you created first |
| `%LOCALAPPDATA%\AgentLiche\Saved` | Unreal Engine settings, shader cache, and crash reports |
| `Liche-diagnostics-….zip` on your desktop | Any files made with **진단 파일 만들기** (Create diagnostic file) |

Enter `%LOCALAPPDATA%` in `Win+R` to open that folder. **Documents** is the Documents folder on the left side of File Explorer. It may be inside OneDrive. Clean up old `LizeWidget` and `Lize` folders separately by following [Updating](updates.md#cleaning-up-old-folders).

The connected agent is a separate program. Uninstalling Liche leaves that program and its data in place.

## Next steps

- [First run](first-run.md)
- [Connecting an agent](agents.md)
- [Troubleshooting](troubleshooting.md)

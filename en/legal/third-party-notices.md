# Third-party notices

[Guide home](../README.md) · [한국어](../../legal/third-party-notices.md)

Agent Liche includes software, fonts, and an engine made by other companies and individuals. Liche itself—the program, character, artwork, and other content—belongs to the seller and is not distributed under the licenses below. Liche's terms of use are in the [End User License Agreement (EULA, Korean)](../../legal/eula.md). Each component is subject to its own license.

## Notice file

The **`THIRD-PARTY-NOTICES.txt`** included in the package is the authoritative source for the full list and license texts. This page explains where to find it and summarizes major components. If this page differs from the notice file, the notice file takes precedence.

| Platform | Notice file location |
| --- | --- |
| Windows | `THIRD-PARTY-NOTICES.txt` beside `AgentLiche.exe` at the top of the extracted folder |
| macOS | `Agent Liche.app/Contents/Resources/THIRD-PARTY-NOTICES.txt` (right-click the app in Finder › **Show Package Contents**) |

Click **리체 설정 › 리체 정보 › 도움말과 약관 › 제3자 고지** (Liche Settings › About Liche › Help and terms › Third-party notices) to open this file in your default text app. If the file cannot be found, this page opens instead.

The Windows package also includes the font notices `Pretendard-OFL.txt` and `Liche-Font-Sources.md` under `AgentLiche\Binaries\Win64`.

## Notice file contents

1. **Unreal Engine:** The Unreal® Engine license attribution, the third-party engine modules actually used by the Liche character program (Shipping build) on Windows and macOS and their full license texts (generated from the engine's module list), and code from other sources included within engine modules
2. **Unreal Engine plugins:** KawaiiPhysics and the project's other plugins
3. **Fonts and other assets:** NEXON Lv.1 Gothic, 교보 손글씨 2019 (Kyobo Handwriting 2019), the Hermes Agent icon (macOS package only), and the UI library's default font
4. **Rust libraries:** All crates used by the chat window program (`LicheInput`) and emotion judgment program (`liche-judge`), with their full license texts

## Major components

| Component | Rights holder | Notes |
| --- | --- | --- |
| Unreal® Engine 5.8 | Epic Games, Inc. | Engine that renders the Liche character |
| KawaiiPhysics | pafuhana1213 | Plugin that calculates hair and clothing movement. MIT License |
| NEXON Lv.1 Gothic | NEXON Korea | Font used in the settings window and menus |
| 교보 손글씨 2019 (Kyobo Handwriting 2019) | 교보문고 (Kyobo Book Centre) | Font used in chat speech bubbles. Used only as embedded in the app |
| Rust libraries | Authors of each library | Libraries used by the chat window and emotion judgment programs. Each follows its own license |
| Microsoft Visual C++ Redistributable | Microsoft Corporation | Included only in the Windows package. The launcher asks to install it only on PCs that need it |

Agent Liche uses Unreal® Engine. Unreal® is a trademark or registered trademark of Epic Games, Inc. in the United States of America and elsewhere.

Unreal® Engine, Copyright 1998 – 2026, Epic Games, Inc. All rights reserved.

Portions of this software are copyright © The FreeType Project (http://www.freetype.org). All rights reserved.

## External services used with Liche

These services are not included with Liche. You can choose to use them alongside her. Each service's terms apply.

- Your connected AI agent (Claude Code, Codex, OpenClaw, Hermes, and others) and its AI service
- TypeSafe AI when emotion judgment (JEV) is enabled

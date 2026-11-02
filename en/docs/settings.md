# Liche Settings

[Guide home](../README.md) · [한국어](../../docs/settings.md)

Hover over **⋯** (More) at the top right of the card, then click **설정** (Settings), the gear, to open **리체 설정** (Liche Settings). Click it again or use the window's close button to close it. The settings layout in 0.2.0 differs from 0.1.0.

## Window layout

- **Left sidebar:** **설정 검색** (Search settings) is at the top, followed by the connection card and page list. A one-line summary of current values appears below each page name.
- **Right pane:** Cards show the selected page's options. On/off options use switches, single-choice options use chips, and options that open windows use buttons.
- **설정 검색:** Enter a word to see matching options and their locations, such as `모드 > 업무 > 옷차림` (Modes > Work > Outfit). Related Korean words also work, such as "의상" (outfit), "다크 모드" (dark mode), "고정핀" (pin), "알람" (alarm), and "글꼴" (font).

Options marked "(Windows)" are Windows-only. They do not appear on macOS because they are not supported there yet.

## Connections

The card at the top of the sidebar shows the connected agent and status, such as `Hermes · 연결됨` (Hermes · Connected). Click it to open the connection page.

| Option | Description |
| --- | --- |
| **연결 설정 열기** (Open connection settings) | Opens agent selection. On macOS, this is the connection step of first-run setup. On Windows, it opens **연결 설정** (Connection settings). Connection problems appear below the card |
| **선택 기능 › 감정 판단 (JEV) · 선택** (Optional features › Emotion judgment (JEV) · Optional) | Uses the conversation to choose Liche's emotions and reaction strength. Enable or disable it with the switch on the right, and open the key window with **키 입력 ›** (Enter key ›). Without a key the switch shows off, and pressing it opens the key window. When enabled, part of your conversation goes to TypeSafe AI in the United States. You need your own JEV key and separate credits. Only input tokens are charged. **자세히 ›** (Details ›) opens [Emotion judgment (JEV)](jev.md) |

If the chat window program is not running, the card shows **리체 대화 꺼짐** (Liche chat is off). See [Troubleshooting](troubleshooting.md).

## Modes

Liche keeps separate Everyday and Work conversations. Switch modes with the icons at the top of the chat window, not on this page.

| Option | Description |
| --- | --- |
| **일상** (Everyday) | A conversation for casual chat. Click to open the Everyday page. The mode you are viewing has **보는 중** (Viewing) beside it |
| **업무** (Work) | A conversation for tasks. Click to open the Work page |
| **지침 › 지침 폴더** (Guides › Guide folder) | Opens the guide folder containing the common guide and both mode folders, with **폴더 열기** (Open folder) |

If the agent does not support separate conversations by mode, you see "이 연결은 아직 모드별 대화를 지원하지 않아요. 두 모드가 한 대화를 함께 써요." (This connection does not yet support per-mode conversations. Both modes share one conversation.) Only one mode can wait for a reply at a time in this case.

### Everyday and Work pages

Both pages have the same layout. Click **‹** (Back) at the top to return to Modes.

| Group | Option | Description |
| --- | --- | --- |
| **옷차림** (Outfit) | **옷** (Clothes) | What Liche wears in this mode. Choose **잠옷** (Pajamas) or **메이드복** (Maid outfit). Defaults are pajamas for Everyday and a maid outfit for Work |
| **옷차림** | **안경** (Glasses) | Whether she wears glasses in this mode. Off by default for Everyday, on for Work |
| **지침** (Guides) | **공통 지침** (Common guide) | Opens Liche's basic guide file, which both modes read first |
| **지침** | **일상 지침**, **업무 지침** (Everyday guide, Work guide) | Opens the guide Liche reads in this mode |
| **지침** | **일상 폴더**, **업무 폴더** (Everyday folder, Work folder) | Opens the folder containing the entry file (`AGENTS.md`) and skills folder (`skills`) |
| **대화** (Chat) | **모델** (Model) | Model for this mode. Click to expand the list supplied by the connected agent. **에이전트 기본값** (Agent default) is first |
| **대화** | **생각 깊이** (Thinking depth) | Choose a supported thinking depth for the selected model using chips. The default is first. For models without this choice, "이 모델은 생각 깊이를 고르지 않아요" (This model does not offer a thinking-depth choice) appears |

Clothes and glasses change immediately when you are viewing that mode. See [Guide files](guides.md) for details about guides.

### Models and thinking depth for each mode

- Everyday and Work remember their models and thinking depth **separately**. For example, use a fast model for Everyday and a deeper-thinking model for Work.
- Selections apply to that mode from the next message and remain after restarting Liche.
- With no selection, the connected agent's defaults apply. If the agent no longer lists a selected model, Liche returns to the default.
- The gear in the chat header takes you directly to these settings for the current mode.
- If the agent supplies no model list, "이 연결은 모델을 고를 수 없어요" (You cannot choose a model with this connection) appears and selection is unavailable. If the chat window program is off, you see "리체 대화가 꺼져 있어 바꿀 수 없어요" (Liche chat is off, so this cannot be changed).

## Notifications

Get desktop notifications about Liche while using other windows.

| Group | Option | Description |
| --- | --- | --- |
|  | **알림 받기** (Receive notifications) | Enables or disables all notifications. When off, the options below are inactive |
| **받을 알림** (Notifications to receive) | **답장** (Replies) | Notifies you when Liche replies |
| **받을 알림** | **확인 요청** (Confirmation requests) | Notifies you when Liche asks permission to do something |
| **알림 모양** (Notification appearance) | **내용 미리보기** (Content preview) | Shows a short reply preview, up to 100 characters, in notifications |
| **알림 모양** | **소리** (Sound) | Plays a sound for notifications |
| **더 보기** (More) | **리체를 보고 있을 때도 알림** (Notify even while viewing Liche) | When off, notifications for the current conversation stay quiet while the chat window is in front. Other-mode notifications still arrive |
| **더 보기** | **테스트 알림** (Test notification) | Sends a notification now to test your settings, with **보내기** (Send) |

If operating-system notifications are off, a warning appears at the top with **Windows 설정 열기** (Open Windows Settings) or **시스템 설정 > 알림** (System Settings > Notifications; Liche's button).

## Display

| Group | Option | Description |
| --- | --- | --- |
| **테마** (Theme) | **밝기** (Appearance) | Choose **라이트** (Light), **다크** (Dark), or **시스템** (System). System follows your operating-system setting |
| **테마** | **색 조합** (Color scheme) | Changes speech bubbles, the input field, and glass tint together. Choose **리체 기본** (Liche default), **벚꽃** (Cherry blossom), **밤하늘** (Night sky), **모노** (Mono), or **직접** (Custom). Click **직접 고르기 ›** (Choose custom colors ›) to set individual colors in the same settings card |
| **글자** (Text) | **글자 크기** (Text size) | Applies to speech bubbles and input text in the chat window. Includes **작게** (Small, 14 px), **보통** (Normal, 15 px), and **크게** (Large, 17 px) chips, plus a slider from 11 to 28 px. Other sizes appear as, for example, `직접 · 16 px` (Custom · 16 px) |

Text size is independent of card size. Enlarging the card does not enlarge the text.

## Window

| Group | Option | Description |
| --- | --- | --- |
| **창** (Window) | **항상 위** (Always on top) | Pins Liche above other windows. Same as the widget's pin |
| **창** | **카드를 화면 가운데로** (Center card on screen) | If the card is off-screen or hard to reach behind a menu bar or taskbar, moves it at its current size to the center of the display containing the pointer. Use **옮기기** (Move) |
| **대화창** (Chat window) | **대화창 스타일** (Chat window style) | Choose **떠 있는 창** (Floating window: a floating chat window matching the glass card) or a bordered **클래식 창** (Classic window) |
| **대화창** | **캐릭터 옆에 두기** (Beside the character) | In the floating window, attaches the chat on the left and character on the right, side by side. In the classic window, the selection is remembered but inactive |
| **대화창** | **대화창 배치** (Chat layout) | **붙이기** (Attach) attaches chat to the glass panel beside the character. **떼기** (Detach) lets you move and resize chat separately. The classic window is always detached. Same as the chat-header button |
| **작업 방해 줄이기** (Reduce interruptions) | **커서가 가까이 오면 흐리게** (Fade when the pointer approaches) | With the pin enabled, the card fades as the pointer approaches, and clicks pass through to the window behind it. Hold the `Ctrl` key (Windows) or the `Option` (`⌥`) key (macOS) while approaching to interact immediately, even while faded. **Caution:** if the desktop is behind the faded card, a click reaches the desktop. On macOS with **System Settings › Desktop & Dock › Click wallpaper to show desktop** set to **Always**, your windows move aside. To click the card, approach it holding `Option`, release the key once the card is solid again, then click |
| **작업 방해 줄이기** | **흐려졌을 때 남는 진하기** (Opacity while faded) | Sets how visible Liche remains while faded |
| **작업 방해 줄이기** | **전체 화면 앱이나 게임을 쓸 땐 숨기기** (Hide during full-screen apps or games) | Hides Liche when another app uses her monitor full-screen, then shows her again afterward. On by default |

Centering the card is also available from the macOS Dock icon menu and app menu (`⌥⌘L`), and the Windows window menu (`Alt+Space`, or hold Shift and right-click the taskbar button).

## Performance

| Group | Option | Description |
| --- | --- | --- |
|  | **성능 프로필** (Performance profile) | Choose **절약** (Power saving), **균형** (Balanced), or **고품질** (High quality). Balanced is the default. Changing any value below shows **사용자 지정** (Custom). Choose Balanced to restore defaults |
| **화질** (Image quality, Windows) | **선명도** (Sharpness) | Choose **보통** (Normal) or **선명하게** (Sharp). Sharp gives smoother edges but uses more GPU. Restart Liche to apply it, using **지금 다시 시작** (Restart now) |
| **움직임** (Motion) | **최대 프레임** (Maximum frame rate) | Maximum times per second Liche is rendered. Choose **15**, **30**, or **60** |
| **움직임** | **가만히 있을 때 프레임** (Idle frame rate) | Renders at this rate after more than 20 seconds of only the default idle animation, without nearby mouse movement (inside the card or within half its height around it), clicks, settings/chat activity, or expression/action changes. Never drops below 15. Mouse movement far away in another app does not count |
| **아끼기** (Saving resources) | **가려지면 쉬기** (Pause when hidden) | Pauses rendering while Liche is not visible, such as when fully covered by another window. Chat and notifications continue |
| **아끼기** (Windows) | **뒤 배경 흐림** (Background blur) | When off, the background behind Liche uses color without blur, reducing the load a little |

| Profile | Idle frame rate | Maximum frame rate | Other values (Windows) |
| --- | --- | --- | --- |
| **절약** | 15 | 30 | Normal sharpness, background blur off |
| **균형** (default) | 20 | 30 | Sharp, background blur on |
| **고품질** | 30 | 60 | Sharp, background blur on |

All three profiles have **가려지면 쉬기** enabled. In 0.2.0, Balanced and High quality idle rates were lowered from 30/60 to 20/30. Settings files retaining the old Balanced or High quality values are read as the same profiles with the new values. Liche always renders at the maximum rate while speaking, reacting, being dragged, or fading.

At the bottom, **지금 리체가 쓰는 양** (Liche's current resource use) shows frame rate, CPU, GPU, and memory use every second. All changes except sharpness apply immediately. **지금 다시 시작** relaunches only the character, without interrupting chat or the connection.

## General

| Group | Option | Description |
| --- | --- | --- |
| **시작** (Startup) | **컴퓨터를 켜면 리체도 시작** (Start Liche when the computer starts) | Starts Liche and her connection when you sign in. Also registers a login item on macOS. If approval is needed, allow Agent Liche through **시스템 설정 열기 ›** (Open System Settings ›). See [macOS instructions](install-mac.md#5-starting-automatically-at-login) |
| **기록** (History) | **기록 폴더** (History folder) | Opens the folder storing chat history and this window's settings, with **폴더 열기** |
| **초기화** (Reset) | **초기화…** (Reset…) | Deletes both Everyday and Work chat histories, attachments, and Liche's memories. A confirmation appears first. Deleted history cannot be recovered |

You cannot reset while either mode is waiting for a reply or has a pending approval request.

## About Liche

| Option | Description |
| --- | --- |
| **버전** (Version) | Shows the app version and build information. Include this line when contacting support. Below it is **리체의 대답은 연결한 AI 에이전트가 만들어요.** (Liche's replies come from the connected AI agent.) |
| **업데이트 › 새 버전 알림** (Updates › New version notifications) | Checks for new versions once a day and when this page opens. If one is available, shows **새 버전이 있어요** (A new version is available), **바뀐 점 ›** (What's changed ›), and **받으러 가기 ›** (Go to download ›). Turning off the switch disables checks. See [Updating](updates.md#new-version-notifications) |
| **도움말과 약관** (Help and terms) | Opens **사용 안내서** (User guide), **사용권 계약 (EULA)** (License agreement (EULA)), **제3자 고지** (Third-party notices), and **문의하기** (Contact support). Third-party notices opens the packaged file first, or the web page if it is missing |
| **진단 › 진단 파일 만들기** (Diagnostics › Create diagnostic file) | Creates a desktop zip with logs, recent crash reports, settings, version, and display information. Excludes chat history, attachments, key files, and memory dumps. Redacts chat text, keys, tokens, and user paths in logs. Not sent automatically. Check the contents before sending. See [Privacy information](privacy.md#creating-a-diagnostic-file) |
| **개발자 › 개발자 도구 보기** (Developer › Show developer tools) | Shows diagnostic and testing tools together on the **개발자 옵션** (Developer options) page. Normally, leave this off |

**개발자 옵션** appears at the bottom of the sidebar only when Show developer tools is on. It includes diagnostic windows for emotion judgment and work effects, usage displays, and animation tests. You do not need it to use Liche.

## Things changed outside settings

- **Card position and size:** Drag directly on the card. See [First run](first-run.md#basic-controls).
- **Mode:** Switch with the icons at the top of the chat window.
- Check for new versions under **리체 정보** (About Liche). Download and install them yourself.
- There is no global shortcut to open the chat window.

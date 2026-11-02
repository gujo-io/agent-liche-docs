# Emotion judgment (JEV)

[Guide home](../README.md) · [한국어](../../docs/jev.md)

## What emotion judgment does

Emotion judgment (JEV) is an optional feature that reads the conversation and chooses Liche's expression, reaction strength, and mood. When enabled, Liche shows expressions that better fit the conversation when she receives a message and for each reply bubble. Her mood also changes gradually with the conversation.

**You do not have to enable it.** Without emotion judgment, Liche reacts using preset rules.

| Situation | Reaction without emotion judgment |
| --- | --- |
| Waiting for a reply | Thoughtful face |
| The agent is using tools in Work mode | Typing on a laptop |
| An approval request arrives | Surprised, then listening attentively |
| The first speech bubble appears | Slight smile |
| The reply ends | Happy face |
| An error occurs or the connection is lost | Flustered, then downcast |
| A request is rejected or times out | Downcast face |

These rule-based reactions also appear when emotion judgment is enabled but has not arrived yet or has failed. Emotion judgment does not stop the conversation. After receiving the full reply, Liche waits up to eight seconds for speech-bubble judgment before displaying it.

## Who operates it

JEV is operated by TypeSafe AI in the United States. When you enable emotion judgment, Liche's judgment program (`liche-judge`) sends conversation content to TypeSafe AI's server (`api.typesafe.ai`) and receives judgment results.

## Getting a key

You need your own JEV key to use emotion judgment. Liche does not include one.

1. Sign up with a Google account or email at the [TypeSafe AI console](https://console.typesafe.ai). Anyone can sign up.
2. Buy credits first. JEV is a prepaid-credit service (TypeSafe AI MCA 8.2).
3. Create a key on the [key management page](https://console.typesafe.ai/keys).
4. Enter it in Liche using the steps below. Do not share your key or make it public.

The price is **US$0.042 per one million input tokens**. **Output tokens are free.** JEV credits are not included in your Liche purchase. Check TypeSafe AI's information for payment and usage terms.

### Number of calls

In 0.2.0, the judgment program (`liche-judge`) calls **JEV twice** for each judged exchange: one message from you and one reply from Liche.

1. One call to choose Liche's emotion when the message arrives
2. One call to choose reactions for each speech bubble after the full reply arrives

Saving a key makes one additional small call to validate it. Long Work conversations with many tool uses judge only the final reply. Actual cost depends on the number of tokens in the conversation and the context sent with it. If you connect to the separate Liche Bridge program, the bridge handles judgment in its own way and makes three calls per exchange.

## Entering a key

Enter your key in the **감정 판단 (JEV) 키** (Emotion judgment (JEV) key) window. You can open it from three places.

- **키 입력 ›** (Enter key ›) under **리체 설정 › 연결 › 선택 기능 › 감정 판단 (JEV) · 선택** (Liche Settings › Connections › Optional features › Emotion judgment (JEV) · Optional)
- **키 입력** (Enter key) at the **"감정 판단 (JEV) · 선택"** (Emotion judgment (JEV) · Optional) step in macOS first-run setup
- **감정 판단 켜기 (선택)** (Enable emotion judgment (optional)) in the Windows **연결 설정** (Connection settings) window

In the key window:

1. Paste the key into **JEV 키 붙여 넣기** (Paste JEV key).
2. Click **저장** (Save).
3. Liche validates the key with one small JEV call, then saves it. Saving enables emotion judgment.
4. You are done when **저장된 키: 있음** (Saved key: present) appears at the top. Click **닫기** (Close).

Both Windows and macOS packages include the judgment program `liche-judge` (Windows: `AgentLiche\Binaries\Win64\liche-judge.exe`; macOS: inside the app). If you see "이 설치에는 감정 판단 프로그램이 없어요." (This installation does not have the emotion judgment program.), that file is missing. Download and extract the package again. If the same message remains, contact support.

## Where the key is stored

When you click **저장**, the chat window program passes the key to the judgment program with `liche-judge --store-key`. The key is passed **only through standard input (stdin)**, never as a command-line argument. Other programs on the same computer therefore cannot see the key by inspecting the running command line. After validation, the judgment program stores the key here.

- **macOS:** An item named `com.agentliche.jev` in this Mac's login keychain. Only the judgment program uses and reads this item.
- **Windows:** Encrypted for this Windows user account using DPAPI, at `%LOCALAPPDATA%\LicheWidget\chat\judge\typesafe.dpapi`. Other user accounts or PCs cannot decrypt it.

The key is not displayed again or left in plain text in logs, diagnostic files, or settings files. There is no way to pass it to the judgment program through command-line arguments or environment variables.

## Information sent outside your computer

When emotion judgment is enabled, each exchange sends the following to TypeSafe AI in the United States.

- Your message
- Liche's reply and the speech bubbles it is split into
- Up to five immediately preceding exchanges, including your messages and Liche's replies
- Liche's personality description, current mood, and whether she is working

Nothing is sent to TypeSafe AI if emotion judgment is off or no key is present. TypeSafe AI processes this information under its terms and privacy policy. We recommend keeping emotion judgment off when your conversations contain sensitive information such as passwords or personal data.

## Turning it off

Turn off the switch under **리체 설정 › 연결 › 선택 기능 › 감정 판단 (JEV) · 선택**. Your key stays saved, so you can turn it back on later with the switch. Turning it off immediately restores rule-based reactions.

The current status appears below this row.

| Status | Meaning |
| --- | --- |
| **켜져 있어요** (Enabled) | Emotion judgment is working |
| **꺼져 있어요** (Disabled) | A key is saved, but the feature is off |
| **키를 넣으면 켤 수 있어요** (Enter a key to enable) | No key is saved yet, also after you remove the key. The switch shows off, and pressing it opens the key window |
| **문제가 있어요** (There is a problem) | The key was rejected or the server could not be reached. Try saving the key again |
| **이 연결에서는 쓸 수 없어요** (Unavailable with this connection) | Emotion judgment cannot be used with the current connection |
| **준비 중** (Preparing) | The chat window program has not sent emotion judgment information yet |

If connected to Liche Bridge, the bridge handles judgment and "리체 브릿지가 판단해요" (Liche Bridge handles judgment) appears. You cannot enable or disable it here.

## Deleting a key

1. Open the key window (**리체 설정 › 연결 › 감정 판단 (JEV) · 선택 › 키 입력 ›** (Liche Settings › Connections › Emotion judgment (JEV) · Optional › Enter key ›)).
2. Click **키 지우기** (Delete key).
3. The key is deleted when **저장된 키: 없음** (Saved key: none) appears.

If you already uninstalled Liche, follow [Deleting the keychain item](install-mac.md#deleting-the-keychain-item) on macOS, or the data-folder removal steps under [Uninstalling](install-windows.md#6-uninstalling) on Windows.

## When a keychain dialog appears on macOS

When you first save a key or run judgment, macOS may ask whether `liche-judge` can access the keychain item. Starting with 0.2.0, the app is Developer ID signed. Once allowed, it will not ask again in the next update. Click **허용** (Allow) or **항상 허용** (Always Allow). Judgment for that exchange waits for your answer. After eight seconds, Liche displays the reply with rule-based reactions. If you click **거부** (Deny), emotion judgment stays in the "문제가 있어요" (There is a problem) state until you save the key again.

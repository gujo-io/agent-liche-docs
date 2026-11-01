# macOS 설치와 제거

[안내서 처음으로](../README.md) · [English](../en/docs/install-mac.md)

## 필요한 것

- **Apple Silicon(M1 이상) Mac만 지원해요. Intel Mac은 지원하지 않아요.**
- macOS 14 이상. 출시 전 시험은 macOS 26과 27에서 했어요.
- CPU와 메모리의 최소 사양은 따로 정하지 않았어요. 노트북에서는 **리체 설정 › 성능**의 **절약**을 권해요.
- 내려받은 zip 파일과 풀린 앱을 함께 둘 여유 공간 1.5 GB 이상.
- 별도로 설치하고 로그인한 AI 에이전트. [에이전트 연결](agents.md)을 참고해요.

## 1. 내려받기

Gujo 스토어에 로그인한 뒤 라이브러리에서 macOS용 zip 파일을 내려받아요. 더블클릭해 풀면 **`Agent Liche.app`**이 생겨요. 같은 상품 구매에 Windows와 macOS 파일이 모두 포함돼요.

### 받은 파일 확인하기 (선택)

| 파일 | 크기(바이트) | SHA-256 |
| --- | --- | --- |
| `RELEASE_FILL_MAC_ZIP_NAME` | `RELEASE_FILL_MAC_ZIP_BYTES` | `RELEASE_FILL_MAC_ZIP_SHA256` |

터미널에서 아래 명령의 파일 이름을 바꿔 실행하면 SHA-256 값이 나와요. 위 표의 값과 다르면 열지 말고 고객지원에 알려 주세요.

```sh
shasum -a 256 ~/Downloads/<받은 zip 파일 이름>
```

## 2. 응용 프로그램 폴더로 옮기기

Finder에서 `Agent Liche.app`을 **응용 프로그램**으로 끌어다 놓아요. 자동 시작을 쓰거나 업데이트할 때 같은 위치에서 바꾸기 쉬워요. 옮긴 뒤 다운로드 폴더의 zip 파일은 지워도 돼요.

## 3. 처음 열기

1. 응용 프로그램 폴더에서 **Agent Liche**를 더블클릭해요.
2. "Agent Liche"이(가) 인터넷에서 다운로드된 앱이라는 확인 창이 떠요. 아래 [Gatekeeper 안내](#gatekeeper-확인-창)를 읽고 **열기**를 눌러요.
3. [처음 실행](first-run.md)에 따라 에이전트를 연결해요. 리체의 대답은 연결한 AI 에이전트가 만들어요.

### Gatekeeper 확인 창

**0.2.0 macOS 판은 Apple Developer ID로 서명하고 Apple 공증(notarization)을 받았어요.** 그래서 처음 열 때 macOS의 Gatekeeper가 인터넷에서 받은 앱을 열지 묻는 평범한 확인 창만 보여 줘요. 이 창에는 Apple이 악성 소프트웨어를 확인했고 발견하지 않았다는 문장이 함께 보여요. **열기**를 누르면 돼요. 이 확인 창은 처음 한 번만 떠요.

아래 경고가 뜬다면 정상 파일이 아닐 수 있어요. 열지 말고 창의 문장과 받은 곳을 고객지원에 알려 주세요.

- 개발자를 확인할 수 없다거나, Apple이 악성 소프트웨어가 없는지 확인할 수 없다는 경고
- 앱이 손상되었다는 경고

보안 기능을 끄거나 `xattr` 같은 명령으로 확인을 건너뛰지 마세요. 공증을 받은 앱에는 필요하지 않아요.

## 4. macOS가 묻는 권한

리체 자체는 시작할 때 화면 기록·손쉬운 사용·입력 모니터링·문서 폴더 권한을 요구하지 않아요. 지침 폴더도 권한이 필요 없는 홈 폴더(`~/Liche`)에 둬요.

| 질문 | 언제와 어떻게 답하나요 |
| --- | --- |
| Agent Liche의 알림 | 처음 알림을 보낼 때 물어요. 알림을 받으려면 **허용**해요. 나중에 **시스템 설정 › 알림 › Agent Liche**에서 바꿔요 |
| `liche-judge`의 키체인 사용 | JEV 키를 저장하거나 읽을 때 물을 수 있어요. 요청한 프로그램이 `liche-judge`인지 확인하고 **허용** 또는 **항상 허용**을 골라요. 서명된 0.2.0부터는 같은 개발자의 다음 버전도 이 허용을 그대로 써요 |
| 연결한 에이전트의 권한 | 문서 폴더 등 에이전트가 필요한 권한은 그 프로그램의 요청이에요. 요청 내용과 프로그램을 확인한 뒤 답해요 |

## 5. 로그인할 때 자동으로 켜기

1. **리체 설정 › 일반 › 컴퓨터를 켜면 리체도 시작**을 켜요.
2. 로그인 항목에서 허용해야 한다는 안내가 보이면 **시스템 설정 열기 ›**를 누르고 **일반 › 로그인 항목**에서 Agent Liche를 허용해요. macOS 버전에 따라 페이지 이름은 **로그인 항목 및 확장 프로그램**이에요.
3. **macOS 로그인 항목에 켜져 있어요.**가 보이면 끝이에요.

**macOS가 이 앱을 찾지 못했어요.**가 보이면 `Agent Liche.app`을 응용 프로그램 폴더로 옮긴 뒤 스위치를 껐다가 다시 켜요. 자동 시작을 끄려면 같은 스위치를 꺼요.

## 6. 끄기

Dock의 Agent Liche 아이콘을 오른쪽 클릭해 **종료**를 골라요. Agent Liche가 앞에 있을 때 `⌘Q`를 눌러도 돼요. 대화창도 함께 꺼져요.

## 7. 제거하기

1. 리체가 켜져 있을 때 **컴퓨터를 켜면 리체도 시작**을 꺼요.
2. JEV를 썼다면 키 창에서 **키 지우기**를 눌러요. 앱을 먼저 지웠다면 아래 [키체인 안내](#키체인-항목-지우기)를 따라요.
3. 리체를 끄고 응용 프로그램 폴더의 `Agent Liche.app`을 휴지통으로 옮겨요.
4. 필요한 파일을 먼저 복사한 뒤 Finder에서 `⌘⇧G`로 아래 경로를 하나씩 열어 지워요. 폴더가 없다면 건너뛰어요. **지운 대화와 직접 만든 파일은 되돌릴 수 없어요.**
5. 로그인 항목이 남아 있다면 **시스템 설정 › 일반 › 로그인 항목**에서도 지워요.

| 위치 | 들어 있는 것 |
| --- | --- |
| `~/Library/Application Support/LicheWidget` | 대화 기록과 첨부, 저장한 연결, 위젯 설정 `settings.json`, 화면·알림·성능 설정, JEV 상태, 로그 |
| `~/Library/Application Support/Epic/LicheWidget` | 카드 위치·크기·고정핀 상태 |
| `~/Liche` | 지침 파일(`common.md`, `daily/daily.md`, `developer/developer.md`)과 모드별 에이전트 작업 폴더. 직접 만든 파일이 있는지 먼저 확인해요 |
| `~/Library/Application Support/Epic/AgentLiche/Saved` | 엔진(Unreal Engine)의 설정과 캐시 |
| `~/Library/Logs/AgentLiche` | 엔진의 로그 폴더 |
| `~/Library/Logs/DiagnosticReports`의 `AgentLiche-…`, `LicheInput-…` | macOS가 남긴 오류 보고서가 있다면 |
| 로그인 키체인의 `com.agentliche.jev` | JEV 키 |
| 바탕 화면의 `Liche-diagnostics-….zip` | **진단 파일 만들기**로 만든 파일이 있다면 |

macOS가 앱마다 만드는 파일도 남을 수 있어요. `~/Library/Preferences`, `~/Library/Caches`, `~/Library/Saved Application State`에서 이름이 `com.agentliche.`로 시작하는 항목이 있으면 함께 지워요.

### 키체인 항목 지우기

1. Spotlight에서 **키체인 접근**을 검색해 열어요.
2. **로그인** 키체인을 골라 `com.agentliche.jev`를 검색해요.
3. 해당 항목을 오른쪽 클릭하고 **삭제**를 골라요.

이전 버전의 폴더는 [업데이트 안내](updates.md#이전-폴더-정리하기)에 따라 따로 정리해요. 연결한 에이전트는 리체와 별도여서 앱을 지워도 그 프로그램과 데이터는 남아요.

## 다음 단계

- [처음 실행](first-run.md)
- [에이전트 연결](agents.md)
- [문제 해결](troubleshooting.md)

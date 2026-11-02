# Windows 설치와 제거

[안내서 처음으로](../README.md) · [English](../en/docs/install-windows.md)

> **지금 스토어에서 받는 Windows 파일은 0.1.0이에요.** 0.2.0은 macOS 판을 먼저 공개했고, Windows 판 0.2.0은 아직 공개하지 않았어요. 0.1.0의 설치와 사용은 [0.1.0 안내서의 Windows 설치](https://github.com/gujo-io/agent-liche-docs/blob/390cc92b9970fdc7c8191cf37b2a653edc4dce7d/docs/install-windows.md)를 봐 주세요. 이 페이지의 아래 내용은 Windows 0.2.0이 공개되면 적용돼요. 공개되면 [변경 기록](../CHANGELOG.md)과 이 페이지에 알려 드려요.

## 필요한 것

- Windows 11 64비트(x64) PC. **Windows 10과 ARM 기반 Windows는 지원하지 않아요.**
- DirectX 12(셰이더 모델 6)를 지원하는 그래픽 카드.
- 메모리 16 GB를 권하고, 최소 8 GB가 필요해요.
- 내려받은 zip 파일과 풀린 폴더를 함께 둘 여유 공간 1 GB 이상.
- 별도로 설치하고 로그인한 AI 에이전트. [에이전트 연결](agents.md)을 참고해요.

## 1. 내려받기

Gujo 스토어에 로그인한 뒤 라이브러리에서 Agent Liche의 Windows용 zip 파일을 내려받아요. Gujo Cloud Apps를 사용한다면 해당 상품의 설치 안내를 따라요.

### 받은 파일 확인하기 (선택)

Windows 판은 코드 서명이 없어서, 받은 파일이 스토어가 배포한 파일과 같은지 직접 확인해 두면 좋아요. 파일마다의 이름, 크기, SHA-256 값은 [스토어 상품 페이지](https://app.gujo.io/products/287?lang=ko)의 **버전 기록**에 있어요.

PowerShell에서 아래 명령을 실행하면 받은 파일의 SHA-256 값이 나와요(다른 폴더에 받았거나 파일 이름이 다르면 경로를 바꿔요). 상품 페이지의 값과 한 글자라도 다르면 실행하지 말고 고객지원에 알려 주세요.

```powershell
Get-FileHash -Algorithm SHA256 "$env:USERPROFILE\Downloads\Agent-Liche-0.2.0-windows.zip"
```

## 2. 압축 풀기

1. zip 파일을 오른쪽 클릭하고 **모두 압축 풀기…**를 골라요.
2. 자주 옮기지 않을 폴더를 정하고 압축을 풀어요. 자동 시작은 실행 파일의 위치를 기억해요.
3. **풀린 폴더 맨 위의 `AgentLiche.exe`와 그 옆의 `AgentLiche` 폴더를 함께 두세요.** 실행 파일 하나만 옮기면 실행되지 않아요.

주요 파일은 이렇게 놓여 있어요. 이 밖에 엔진의 고지·파일 목록이 함께 들어 있어요.

```text
<압축을 푼 폴더>\
├── AgentLiche.exe              리체를 시작하는 실행 파일 (이것을 더블클릭해요)
├── THIRD-PARTY-NOTICES.txt     제3자 고지
├── AgentLiche\
│   └── Binaries\Win64\
│       ├── AgentLiche-Win64-Shipping.exe   리체 캐릭터 프로그램
│       ├── LicheInput.exe                  대화창 프로그램
│       └── liche-judge.exe                 감정 판단(JEV) 프로그램
└── Engine\                     엔진 파일
```

## 3. 처음 실행하기

1. 맨 위의 **`AgentLiche.exe`**를 더블클릭해요. `AgentLiche\Binaries\Win64` 안의 파일을 찾아 실행할 필요는 없어요.
2. **"Windows의 PC 보호"** 창이 뜨면 아래 [SmartScreen 안내](#windows의-pc-보호-창이-뜰-때-smartscreen)를 따라요.
3. PC에 Visual C++ 런타임이 없으면 "The following component(s) are required to run this program … Would you like to install them now?"라는 창이 떠요. **예**를 누르면 패키지에 들어 있는 Microsoft Visual C++ 재배포 패키지가 설치돼요. 설치가 끝나면 리체가 이어서 시작해요.
4. 바탕 화면에 유리 카드와 대화창이 나타나요.
5. [처음 실행](first-run.md)에 따라 에이전트를 연결해요. 리체의 대답은 연결한 AI 에이전트가 만들어요.

### "Windows의 PC 보호" 창이 뜰 때 (SmartScreen)

**0.2.0 Windows 판은 코드 서명이 되어 있지 않아요.** 그래서 처음 실행할 때 Microsoft Defender SmartScreen이 "Windows의 PC 보호" 창을 띄우고, 게시자가 **알 수 없는 게시자**로 보여요. 코드 서명은 다음 업데이트에서 넣을 예정이에요.

1. Gujo 스토어에서 받은 파일인지 확인해요. 위의 [SHA-256 확인](#받은-파일-확인하기-선택)을 해 두면 더 확실해요.
2. 창 안의 **추가 정보**를 눌러요.
3. 앱 이름이 `AgentLiche.exe`인지 확인한 뒤 **실행**을 눌러요.

이 창이 다시 뜨면 같은 순서로 실행해요. 출처를 모르는 파일이거나 Microsoft Defender가 악성 파일로 탐지했다면 실행하지 말고 고객지원에 알려 주세요. SmartScreen이나 Microsoft Defender를 통째로 끄지 마세요.

Windows 보안의 **스마트 앱 컨트롤**이 켜진 PC에서는 **실행** 단추 없이 막힐 수 있어요. 스마트 앱 컨트롤을 끄는 것은 PC 전체의 보안 설정을 바꾸는 일이라 권하지 않아요. 이 경우 고객지원에 알려 주세요.

### 방화벽 창이 뜰 때

판매용 리체 프로그램은 외부 연결을 받는 포트를 열지 않아요. 그래서 수신 연결을 허용할 필요가 없고, 정상이라면 Windows 방화벽 창이 뜨지 않아요. 리체의 방화벽 허용 창이 나오면 허용하지 말고 버전과 창의 내용을 고객지원에 알려 주세요. 별도로 설치한 에이전트가 묻는 창은 그 프로그램의 안내를 따라요. [외부 연결 목록](privacy.md#바깥에-연결하는-경우)을 참고해요.

## 4. 끄기

- 리체 카드를 누른 뒤 `Alt+Space`를 눌러 창 메뉴를 열고 **닫기**를 골라요. 작업 표시줄의 리체 단추를 `Shift`를 누른 채 오른쪽 클릭해도 같은 창 메뉴가 열려요.
- 꺼지지 않으면 작업 관리자(`Ctrl+Shift+Esc`)의 **세부 정보**에서 `AgentLiche-Win64-Shipping.exe`를 골라 **작업 끝내기**를 눌러요. **프로세스** 탭에는 시작 파일, 캐릭터 프로그램, 대화창 프로그램이 모두 Agent Liche로 보여요.
- 대화창 프로그램 `LicheInput.exe`는 리체가 꺼지면 함께 꺼져요.

## 5. 로그인할 때 자동으로 켜기

**리체 설정 › 일반 › 컴퓨터를 켜면 리체도 시작**을 켜요. 시작 프로그램 폴더에 `Agent Liche Auto Connect.lnk`가 생기고, 로그인할 때 리체와 저장된 연결이 함께 켜져요.

폴더를 옮기거나 버전을 바꿨다면 스위치를 껐다가 다시 켜요. 리체는 이 바로 가기 하나만 바꾸고 다른 시작 프로그램은 건드리지 않아요.

## 6. 제거하기

zip으로 설치한 리체는 폴더째 지워요. 설치 프로그램이 없어서 **설정 › 앱** 목록에는 나오지 않아요. Gujo Cloud Apps로 설치했다면 먼저 그 클라이언트에서 제거하고, 아래 데이터 폴더가 남아 있으면 직접 지워요.

1. 리체가 켜져 있을 때 **컴퓨터를 켜면 리체도 시작**을 꺼요. 이미 앱을 지웠다면 `Win+R`에서 `shell:startup`을 열고 `Agent Liche Auto Connect.lnk`를 지워요.
2. JEV 키를 지우려면 키 창의 **키 지우기**를 눌러요. 아래 `%LOCALAPPDATA%\LicheWidget` 폴더를 지워도 키 파일이 함께 지워져요.
3. 리체를 끄고 압축을 풀었던 폴더를 통째로 지워요.
4. 필요한 파일을 먼저 복사한 뒤 아래 데이터 폴더를 지워요. **지운 대화와 직접 만든 파일은 되돌릴 수 없어요.**

| 위치 | 들어 있는 것 |
| --- | --- |
| `%LOCALAPPDATA%\LicheWidget` | 대화 기록(`chat\history-daily.jsonl`, `chat\history-developer.jsonl`)과 첨부, 저장한 연결(`chat\connection.json`), 화면·알림·성능 설정, 카드 위치, JEV 키(`chat\judge\typesafe.dpapi`), 로그(`logs`) |
| `문서\LicheWidget` | 위젯 설정 `settings.json`과 오류 기록(`settings.error.txt`, `input.error.txt`) |
| `문서\Liche` | 지침 파일(`common.md`, `daily\daily.md`, `developer\developer.md`)과 모드별 에이전트 작업 폴더. 직접 만든 파일이 있는지 먼저 확인해요 |
| `%LOCALAPPDATA%\AgentLiche\Saved` | 엔진(Unreal Engine)의 설정·셰이더 캐시·오류 보고서 |
| 바탕 화면의 `Liche-diagnostics-….zip` | **진단 파일 만들기**로 만든 파일이 있다면 |

`Win+R`에서 `%LOCALAPPDATA%`를 입력하면 해당 폴더가 열려요. **문서**는 탐색기 왼쪽의 문서 폴더이며 OneDrive 안에 있을 수도 있어요. 이전 버전의 `LizeWidget`, `Lize` 폴더는 [업데이트 안내](updates.md#이전-폴더-정리하기)에 따라 따로 정리해요.

연결한 에이전트는 별도 프로그램이어서 리체를 지워도 그 프로그램과 데이터는 남아요.

## 다음 단계

- [처음 실행](first-run.md)
- [에이전트 연결](agents.md)
- [문제 해결](troubleshooting.md)

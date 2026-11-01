# Windows 설치와 제거

[안내서 처음으로](../README.md)

## 필요한 것

- Windows 11 64비트 PC (Windows 10은 확인 중이에요)
- DirectX 12를 지원하는 그래픽 카드
- 내려받기 크기 약 430 MB와 압축을 풀 공간
- 리체와 연결할 AI 에이전트 ([에이전트 연결](agents.md) 참고)

## 1. 내려받기

두 가지 방법 중 하나를 골라요.

- **Gujo Cloud Apps로 설치하기:** Gujo Cloud Apps Windows 클라이언트에서 Agent Liche를 찾아 설치해요.
- **zip 파일로 받기:** Gujo 스토어에 로그인한 뒤 라이브러리에서 Agent Liche의 zip 파일을 내려받아요.

zip 파일로 받았다면 압축을 풀어요.

1. 내려받은 zip 파일을 오른쪽 클릭하고 **모두 압축 풀기...**를 골라요.
2. 압축을 풀 폴더를 정해요. 예를 들어 `C:\Users\<사용자 이름>\AgentLiche`처럼 자주 옮기지 않을 폴더가 좋아요. "컴퓨터를 켜면 리체도 시작"을 켜면 리체가 실행 파일의 위치를 기억하기 때문이에요.
3. **압축 풀기**를 눌러요.

## 2. 처음 실행하기

1. 압축을 푼 폴더 맨 위에 있는 실행 파일 `a001_Cartoon.exe`를 더블클릭해요. (확인 중: 판매 패키지의 실행 파일 이름은 바뀔 수 있어요)
2. 잠시 뒤 바탕 화면에 리체가 있는 유리 카드가 나타나요. 카드 왼쪽에는 대화창이 붙어 있어요.
3. 대화창의 안내에 따라 에이전트를 연결해요. 순서는 [처음 실행](first-run.md)에 있어요.

### "Windows의 PC 보호" 창이 뜰 때 (SmartScreen)

지금 판매하는 빌드는 코드 서명을 하지 않아서, 처음 실행할 때 Windows SmartScreen이 "알 수 없는 게시자"라고 알릴 수 있어요.

1. 파란 창 **Windows의 PC 보호**에서 **추가 정보**를 눌러요.
2. 앱 이름과 "게시자: 알 수 없는 게시자"가 보이면 **실행**을 눌러요.

이 창은 보통 처음 실행할 때 한 번만 떠요. 내려받은 파일이 스토어에서 받은 것이 맞는지 확인하고 싶으면 스토어 상품 페이지에 적힌 SHA-256 값과 비교해요.

```powershell
Get-FileHash "<내려받은 zip 파일 경로>" -Algorithm SHA256
```

### 방화벽 창이 뜰 때

처음 실행할 때 Windows Defender 방화벽이 "UnrealGame"의 네트워크 접근을 허용할지 물을 수 있어요. 리체는 다른 컴퓨터의 연결을 받을 필요가 없어서 **취소**를 눌러도 괜찮아요. 취소해도 에이전트와의 대화와 감정 판단(JEV)은 그대로 동작해요.

## 3. 끄기

- 작업 표시줄에서 리체 단추를 Shift를 누른 채 오른쪽 클릭하면 창 메뉴가 열려요. 여기서 **닫기**를 골라요. 리체 카드를 한 번 누른 뒤 `Alt+Space`를 눌러도 같은 메뉴가 열려요. (확인 중)
- 위 방법으로 꺼지지 않으면 작업 관리자(`Ctrl+Shift+Esc`)를 열고 리체 프로그램(`a001_Cartoon`)을 골라 **작업 끝내기**를 눌러요.
- 대화창 프로그램(`LicheInput`)은 리체가 꺼지면 스스로 꺼져요.

## 4. 로그인할 때 자동으로 켜기

**리체 설정 › 일반 › 시작**에서 **컴퓨터를 켜면 리체도 시작**을 켜요. 그러면 Windows 시작 프로그램 폴더에 `Agent Liche Auto Connect.lnk` 바로 가기가 생기고, 로그인할 때 리체와 저장된 연결이 함께 켜져요.

- 리체 폴더를 옮겼거나 새 버전으로 바꿨다면 이 스위치를 한 번 껐다가 다시 켜요. 바로 가기가 예전 위치를 가리키면 설정 창에 "시작 항목이 다른 폴더의 리체를 가리켜요. 껐다 켜면 지금 리체로 바뀌어요."라고 나와요.
- 리체는 이 바로 가기 하나만 만들고 지워요. 다른 시작 프로그램은 건드리지 않아요.

## 5. 제거하기

리체는 설치 프로그램 없이 폴더째 동작해요. 그래서 **설정 › 앱**의 목록에는 나오지 않고, 아래 순서대로 직접 지워요. Gujo Cloud Apps로 설치했다면 먼저 그 클라이언트에서 제거해요. (확인 중: 클라이언트가 지우는 범위)

1. **자동 시작 끄기:** 리체가 켜져 있을 때 **리체 설정 › 일반 › 컴퓨터를 켜면 리체도 시작**을 꺼요. 이미 리체를 지웠다면 `Win+R`을 누르고 `shell:startup`을 입력해 시작 프로그램 폴더를 연 뒤 `Agent Liche Auto Connect.lnk`를 지워요.
2. **감정 판단 키 지우기 (선택):** JEV 키를 넣었다면 키 창에서 **키 지우기**를 눌러요. 아래 3단계에서 데이터 폴더를 지워도 키 파일이 함께 지워져요.
3. **리체 끄기:** 위 "끄기"대로 리체를 꺼요.
4. **프로그램 폴더 지우기:** 압축을 푼 폴더를 통째로 지워요.
5. **데이터 폴더 지우기:** 아래 표의 폴더를 지워요. 대화 기록과 설정을 남기고 싶으면 먼저 다른 곳에 복사해 두세요.

| 위치 | 들어 있는 것 |
| --- | --- |
| `%LOCALAPPDATA%\LicheWidget` | 두 모드의 대화 기록과 첨부 복사본, 연결 설정, 화면·알림·성능 설정, 카드 위치와 크기(`transparent-window.json`), 감정 판단 키(`chat\judge\typesafe.dpapi`)와 상태, 진단 기록(`logs`), 시작 프로그램 바로 가기 백업 |
| `문서\LicheWidget` | 위젯 설정 파일 `settings.json`과 설명·오류 파일 |
| `문서\Liche` | 여러분이 쓴 지침 파일(`common.md`, `daily`, `developer`)과 에이전트가 모드별로 일하는 폴더. 직접 만든 파일이 들어 있을 수 있으니 확인한 뒤 지워요 |
| 시작 프로그램 폴더의 `Agent Liche Auto Connect.lnk` | 로그인할 때 리체를 켜는 바로 가기 (1단계에서 지움) |

이전 버전(0.1.0 등)을 쓴 적이 있으면 이름에 `Lize`가 들어간 폴더도 남아 있을 수 있어요. 새 버전은 이 폴더를 읽지 않으니 함께 지워도 돼요.

| 이전 버전의 위치 | 들어 있는 것 |
| --- | --- |
| `%LOCALAPPDATA%\LizeWidget` | 이전 버전의 대화 기록, 설정, 카드 위치 |
| `문서\LizeWidget` | 이전 버전의 위젯 설정 파일 |
| `문서\Lize` | 이전 버전의 지침 파일 |

`문서` 폴더는 탐색기 왼쪽의 **문서**예요. OneDrive가 문서 폴더를 백업하고 있으면 실제 위치가 OneDrive 안일 수 있어요.

PowerShell로 한 번에 지우려면 리체를 끈 뒤 아래 명령을 실행해요. 지침 폴더(`문서\Liche`)는 직접 쓴 파일이 있을 수 있어서 명령에 넣지 않았어요.

```powershell
$docs = [Environment]::GetFolderPath('MyDocuments')
Remove-Item -Recurse -Force "$env:LOCALAPPDATA\LicheWidget", "$docs\LicheWidget" -ErrorAction SilentlyContinue
Remove-Item -Force "$env:APPDATA\Microsoft\Windows\Start Menu\Programs\Startup\Agent Liche Auto Connect.lnk" -ErrorAction SilentlyContinue
```

연결한 에이전트(Claude Code, Codex, OpenClaw, Hermes 등)는 리체와 따로 설치한 프로그램이에요. 리체를 지워도 에이전트와 그 설정은 남아 있어요.

## 다음 단계

- [처음 실행](first-run.md)
- [에이전트 연결](agents.md)
- [문제 해결](troubleshooting.md)

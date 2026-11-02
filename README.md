# Agent Liche 사용 안내서

[English](en/README.md)

Agent Liche(리체)는 바탕 화면에 사는 AI 비서예요. 언리얼 엔진으로 만든 3D 캐릭터 리체가 반투명한 유리 카드 안에 서 있고, 카드 옆의 대화창에서 리체와 이야기해요.

리체의 답은 여러분이 직접 연결한 AI 에이전트가 만들어요. 리체는 Claude Code, Codex, OpenClaw, Hermes 같은 에이전트와 대화를 주고받으며 대화에 맞춰 표정을 바꿔요. 업무 모드에서 에이전트가 일하는 동안에는 노트북을 두드리며 기다려요. 에이전트가 파일을 고치거나 명령을 실행하려고 하면 대화창에서 먼저 허락을 구해요.

이 안내서는 Gujo 스토어에서 [Agent Liche](https://app.gujo.io/products/287?lang=ko)(상품 번호 287)를 산 분을 위한 설명서예요. 판매자는 라노드(Ranode)예요.

> 이 안내서는 **0.2.0** 기준이에요. **0.2.0은 macOS 판을 먼저 공개했어요.** Windows 판 0.2.0은 아직 공개하지 않았고, 지금 스토어에서 받는 Windows 파일은 **0.1.0**이에요. 0.1.0을 쓰는 분은 [0.1.0 안내서](https://github.com/gujo-io/agent-liche-docs/blob/390cc92b9970fdc7c8191cf37b2a653edc4dce7d/README.md)를 봐 주세요. 달라진 점과 알려진 문제는 [변경 기록](CHANGELOG.md)에 모아 두었어요.

## 지원하는 환경

| 플랫폼 | 지금 받는 버전 | 지원하는 환경 | 서명 |
| --- | --- | --- | --- |
| macOS | **0.2.0** | macOS 14 이상, Apple Silicon(M1 이상) Mac | Developer ID 서명과 Apple 공증을 마쳤어요 |
| Windows | **0.1.0** (0.2.0은 공개 전) | Windows 11 64비트(x64), DirectX 12(셰이더 모델 6)를 지원하는 그래픽 카드 | 코드 서명 없음. 처음 실행할 때 SmartScreen 창이 떠요 ([방법](docs/install-windows.md#windows의-pc-보호-창이-뜰-때-smartscreen)) |

- **Intel Mac은 지원하지 않아요.** 출시 전 시험은 macOS 26과 27에서 했어요.
- **Windows 10과 ARM 기반 Windows는 지원하지 않아요.** 패키지는 x64용 하나예요.
- **메모리는 16 GB를 권하고, 최소 8 GB가 필요해요.** 3D 캐릭터를 계속 그리므로 노트북이나 오래된 컴퓨터에서는 **리체 설정 › 성능**의 **절약**을 권해요.
- 저장 공간은 macOS 앱에 약 0.5 GB가 필요해요. 내려받은 zip 파일이 남아 있는 동안에는 약 0.7 GB의 여유 공간이 필요해요.
- 한 번 구매하면 같은 상품의 Windows와 macOS 파일을 모두 받을 수 있어요. 에이전트의 계정·구독·API 요금과 선택 기능 JEV의 요금은 별도예요.

## 빠르게 시작하기

1. 리체를 설치해요. [macOS 설치](docs/install-mac.md)를 따라 해요. Windows는 [Windows 설치](docs/install-windows.md)의 맨 위 안내를 먼저 봐요.
2. 리체와 연결할 AI 에이전트를 하나 준비해요. 에이전트는 리체에 들어 있지 않아서 따로 설치하고, 그 에이전트의 계정이나 구독도 따로 필요해요. [에이전트 연결](docs/agents.md)에서 고를 수 있는 에이전트를 확인해요.
3. 리체를 처음 실행하고 안내에 따라 에이전트를 연결해요. [처음 실행](docs/first-run.md)에 순서가 있어요.
4. 대화창에 첫 메시지를 써서 `Enter`로 보내요. 줄을 바꾸려면 `Shift+Enter`를 눌러요.
5. 리체의 감정 표현을 더 풍부하게 하고 싶으면 [감정 판단 (JEV)](docs/jev.md)을 켜요. 켜지 않아도 리체는 정해진 규칙대로 반응해요.

## 안내서 목차

| 문서 | 내용 |
| --- | --- |
| [macOS 설치와 제거](docs/install-mac.md) | 내려받기, 파일 확인, 응용 프로그램 폴더로 옮기기, Gatekeeper 확인 창, 권한, 제거와 데이터 위치 |
| [Windows 설치와 제거](docs/install-windows.md) | 지금 받는 Windows 버전, 0.2.0의 내려받기, 파일 확인, 첫 실행, SmartScreen과 방화벽 창, 끄기, 제거와 데이터 위치 |
| [처음 실행](docs/first-run.md) | 첫 실행 안내, 연결되지 않았을 때 우는 리체와 시간이 지나면 조는 리체, 기본 조작, 답을 기다리는 시간 |
| [에이전트 연결](docs/agents.md) | 연결할 수 있는 에이전트, 플랫폼별 연결 방법, Codex의 승인 방식, 에이전트별 모델과 생각 깊이 |
| [감정 판단 (JEV)](docs/jev.md) | 감정 판단이 하는 일, 호출 횟수와 요금, 키 넣기와 보관, 바깥으로 보내는 정보 |
| [리체 설정](docs/settings.md) | 설정 창의 페이지와 항목, 모드별 모델과 생각 깊이 |
| [지침 파일](docs/guides.md) | 리체의 성격과 말투를 정하는 지침 파일, 기본 지침과 다시 만들어지는 규칙 |
| [개인정보와 데이터](docs/privacy.md) | 컴퓨터에 남는 것, 바깥으로 나가는 연결 전체 목록, 데이터 지우기 |
| [문제 해결](docs/troubleshooting.md) | 연결이 안 될 때 이유별로 할 일, 자주 묻는 질문, 알려진 문제 |
| [업데이트](docs/updates.md) | 새 버전 알림, 새 버전으로 바꾸는 방법, 이전 폴더 정리 |
| [변경 기록](CHANGELOG.md) | 버전마다 달라진 점과 알려진 문제 |
| [제3자 고지](legal/third-party-notices.md) | 리체에 들어 있는 다른 회사의 소프트웨어와 글꼴, 고지 파일의 위치 |

## 도움이 필요할 때

문제가 생기면 아래로 연락해 주세요. **리체 설정 › 리체 정보 › 진단 파일 만들기**로 고객지원용 zip 파일을 만들 수 있어요. 대화 기록·첨부·JEV 키 파일은 넣지 않고, 로그의 대화 글과 키·토큰은 가려요. 자동으로 보내지 않으니 내용을 확인한 뒤 직접 첨부해 주세요. [문제 해결](docs/troubleshooting.md)의 문의 안내도 함께 봐요.

- 이메일: help@ranode.net
- 고객지원: https://support.gujo.io
- 전화: 010-2193-6227 (평일 오전 10시부터 오후 6시까지)

## 약관과 정책

- [Agent Liche 최종 사용자 사용권 계약 (EULA)](legal/eula.md)
- [이용약관](https://account.gujo.io/ko/terms)
- [환불 정책](https://account.gujo.io/ko/refund)
- [개인정보 처리방침](https://account.gujo.io/ko/privacy)

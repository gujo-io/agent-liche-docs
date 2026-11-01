# Agent Liche 사용 안내서

Agent Liche(리체)는 바탕 화면에 사는 AI 비서예요. 언리얼 엔진으로 만든 3D 캐릭터 리체가 반투명한 유리 카드 안에 서 있고, 카드 왼쪽의 대화창에서 리체와 이야기해요.

리체의 답은 여러분이 직접 연결한 AI 에이전트가 만들어요. 리체는 Claude Code, Codex, OpenClaw, Hermes 같은 에이전트와 대화를 주고받으며 대화에 맞춰 표정을 바꿔요. 업무 모드에서 에이전트가 일하는 동안에는 노트북을 두드리며 기다려요. 에이전트가 파일을 고치거나 명령을 실행하려고 하면 대화창에서 먼저 허락을 구해요.

이 안내서는 Gujo 스토어에서 [Agent Liche](https://asset.gujo.io/products/287?lang=ko)(상품 번호 287)를 산 분을 위한 설명서예요.

> 이 안내서는 출시를 준비하고 있는 다음 업데이트를 기준으로 써요. 지금 내려받을 수 있는 Windows 0.1.0과 화면이 다른 부분이 있어요. 달라진 점은 [변경 기록](CHANGELOG.md)에 모아 두었어요.

## 지원하는 환경

| 플랫폼 | 상태 | 최소 환경 |
| --- | --- | --- |
| Windows | 판매 중 (Liche (Windows) 0.1.0, 얼리 액세스) | Windows 11 64비트, DirectX 12를 지원하는 그래픽 카드 |
| macOS | 준비 중 (예정) | Apple Silicon(M1 이상) Mac, macOS 14 이상 |

- Windows에서는 Windows 11 64비트에서 동작을 확인했어요. Windows 10에서 동작하는지는 아직 확인하지 않았어요 (확인 중).
- macOS 판은 Apple Silicon Mac에서만 동작해요. Intel Mac은 지원하지 않아요. 실제로 확인한 macOS 버전은 26과 27이에요. macOS 14부터 25까지는 아직 확인하지 않았어요 (확인 중).
- macOS 판이 나오면 같은 상품에 함께 들어가요. 업데이트 기간 안이면 추가 요금 없이 받을 수 있어요.
- 3D 캐릭터를 계속 그리기 때문에 그래픽 카드가 있는 PC를 권해요.

## 빠르게 시작하기

1. 리체를 설치해요. [Windows 설치](docs/install-windows.md) 또는 [macOS 설치 (예정)](docs/install-mac.md)를 따라 해요.
2. 리체와 연결할 AI 에이전트를 하나 준비해요. 에이전트는 리체에 들어 있지 않아서 따로 설치하고, 그 에이전트의 계정이나 구독도 따로 필요해요. [에이전트 연결](docs/agents.md)에서 고를 수 있는 에이전트를 확인해요.
3. 리체를 처음 실행하고 안내에 따라 에이전트를 연결해요. [처음 실행](docs/first-run.md)에 순서가 있어요.
4. 대화창에 첫 메시지를 써서 `Enter`로 보내요. 줄을 바꾸려면 `Shift+Enter`를 눌러요.
5. 리체의 감정 표현을 더 풍부하게 하고 싶으면 [감정 판단 (JEV)](docs/jev.md)을 켜요. 켜지 않아도 리체는 정해진 규칙대로 반응해요.

## 안내서 목차

| 문서 | 내용 |
| --- | --- |
| [Windows 설치와 제거](docs/install-windows.md) | 내려받기, 첫 실행, SmartScreen과 방화벽 창, 끄기, 제거와 데이터 위치 |
| [macOS 설치와 제거 (예정)](docs/install-mac.md) | 내려받기, 응용 프로그램 폴더로 옮기기, Gatekeeper 확인 창, 권한, 제거와 데이터 위치 |
| [처음 실행](docs/first-run.md) | 첫 실행 안내, 에이전트가 없을 때의 모습, 기본 조작 |
| [에이전트 연결](docs/agents.md) | 연결할 수 있는 에이전트, 플랫폼별 연결 방법, "응답하지 않아요"가 뜰 때 |
| [감정 판단 (JEV)](docs/jev.md) | 감정 판단이 하는 일, 키 넣기, 바깥으로 보내는 정보, 끄기와 키 지우기 |
| [리체 설정](docs/settings.md) | 설정 창의 페이지와 항목 |
| [지침 파일](docs/guides.md) | 리체의 성격과 말투를 정하는 지침 파일과 예시 |
| [개인정보와 데이터](docs/privacy.md) | 컴퓨터에 남는 것, 바깥으로 나가는 것, 데이터 지우기 |
| [문제 해결](docs/troubleshooting.md) | 자주 묻는 질문 |
| [업데이트](docs/updates.md) | 새 버전으로 바꾸는 방법 |
| [변경 기록](CHANGELOG.md) | 버전마다 달라진 점 |
| [제3자 고지](legal/third-party-notices.md) | 리체에 들어 있는 다른 회사의 소프트웨어와 글꼴 |

## 도움이 필요할 때

문제가 생기면 아래로 연락해 주세요. [문제 해결](docs/troubleshooting.md)의 "문의할 때 알려 주시면 좋은 것"을 함께 보내 주시면 더 빨리 도와드릴 수 있어요.

- 이메일: help@ranode.net
- 고객지원: https://support.gujo.io
- 전화: 010-2193-6227 (평일 오전 10시부터 오후 6시까지)

## 약관과 정책

- [이용약관](https://account.gujo.io/ko/terms)
- [환불 정책](https://account.gujo.io/ko/refund)
- [개인정보 처리방침](https://account.gujo.io/ko/privacy)

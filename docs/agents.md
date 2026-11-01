# 에이전트 연결

[안내서 처음으로](../README.md) · [English](../en/docs/agents.md)

리체는 답을 직접 만들지 않아요. **여러분이 연결한 AI 에이전트가 답을 만들고**, 리체는 대화를 보여 주며 표정과 몸짓으로 반응해요. 에이전트는 별도로 설치해야 해요.

## 먼저 알아 둘 것

- **계정과 요금은 별도예요.** 에이전트의 계정·구독·API 키는 그 서비스에서 준비해요. 리체는 그 로그인 정보나 키를 받거나 저장하지 않아요.
- **ACP로 연결해요.** ACP(Agent Client Protocol)는 에이전트와 대화하는 공개 방식이에요. Claude Code는 `claude-agent-acp`, Codex는 `codex-acp` 어댑터로 연결해요.
- **대화는 에이전트에게 가요.** 에이전트는 답을 만들려고 자기 AI 서비스로 내용을 보낼 수 있어요. [개인정보와 데이터](privacy.md)를 읽어 주세요.
- **로그인과 첫 설정을 먼저 마쳐요.** 에이전트의 공식 안내에 따라 로그인·모델 설정을 끝내야 리체가 답을 받을 수 있어요.
- Windows용 리체에는 Windows에 설치한 에이전트를 연결해요. **WSL 안에만 설치한 에이전트는 지원하지 않아요.** Windows 실행 파일로 설치한 에이전트를 골라요.
- 모델과 생각 깊이는 모드마다 따로 골라요. **리체 설정 › 모드 › 일상(또는 업무) › 대화**에서 바꿔요 ([리체 설정](settings.md#모드별-모델과-생각-깊이)).

## 연결할 수 있는 에이전트

| 에이전트 | 리체가 실행하는 ACP 명령 | macOS | Windows |
| --- | --- | --- | --- |
| Claude Code | `claude-agent-acp` | 첫 실행 안내의 **이 컴퓨터에서 찾은 연결**에서 선택 | **연결 설정**의 **다른 에이전트**에서 선택 |
| Codex | `codex-acp` | 첫 실행 안내의 **이 컴퓨터에서 찾은 연결**에서 선택 | **연결 설정**의 **다른 에이전트**에서 선택 |
| OpenClaw | `openclaw acp` | 첫 실행 안내의 **이 컴퓨터에서 찾은 연결**에서 선택 | **연결 설정**의 **다른 에이전트**에서 선택 |
| Hermes | `hermes-acp` | 첫 실행 안내의 **이 컴퓨터에서 찾은 연결**에서 선택 | **연결 설정**의 Hermes 카드 |
| 그 밖의 ACP 에이전트 | 해당 프로젝트의 ACP 실행 명령 | **에이전트로 연결하기** | `LicheInput.exe --connect` ([아래](#windows에서-다른-에이전트-연결하기)) |
| 리체 브릿지 | 별도 프로그램 | 판매 패키지에 들어 있지 않아요. 따로 설치했을 때만 목록에 보여요 | 판매 패키지에 들어 있지 않아요. 따로 설치했을 때만 카드가 보여요 |

리체는 어느 에이전트든 같은 방식(ACP)으로 실행하고 대화해요. 다만 각 에이전트의 설치, 로그인, 모델 사용 조건은 그 프로젝트가 정하고 바뀔 수 있어요. 공식 프로젝트가 해당 운영체제를 지원하는지 먼저 확인해요.

## 에이전트 설치하기

아래 명령과 요구사항은 **2026-11-02에 공식 문서·배포 정보와 대조**했어요. 이 안내서 작업에서 새로 설치하거나 로그인·연결 시험을 하지는 않았어요. 설치 프로그램은 바뀔 수 있으니 각 공식 안내도 함께 확인해요.

### Node.js와 npm

Claude Code·Codex의 ACP 어댑터와 OpenClaw는 Node.js/npm이 필요해요. [Node.js 공식 다운로드](https://nodejs.org/en/download)에서 운영체제에 맞게 설치해요. npm도 함께 설치돼요. [npm 공식 설치 안내](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)도 참고해요.

- Claude ACP 어댑터는 Node.js 22 이상이 필요해요.
- 현재 OpenClaw 배포본은 **24.22.1 이상 24.x 또는 26.12.1 이상**이 필요해요. 여러 에이전트를 함께 쓴다면 Node.js 26.13.0을 권해요.
- 설치 확인은 터미널(macOS) 또는 PowerShell(Windows)에서 해요.

```sh
node -v
npm -v
```

### Claude Code + claude-agent-acp

1. [Claude Code 공식 설치 안내](https://code.claude.com/docs/en/setup)에서 macOS 또는 Windows용 설치 방법을 따라요. Claude Code를 열어 로그인해요.
2. Node.js/npm을 준비한 뒤 ACP 어댑터를 설치해요.

```sh
npm install -g @agentclientprotocol/claude-agent-acp
```

리체는 `claude-agent-acp`로 연결해요. [공식 ACP 프로젝트](https://github.com/agentclientprotocol/claude-agent-acp)에서 요구사항을 확인할 수 있어요. Claude Code와 어댑터는 서로 다른 프로그램이에요.

### Codex + codex-acp

Node.js/npm을 준비한 뒤 설치해요.

```sh
npm install -g @agentclientprotocol/codex-acp
```

리체는 `codex-acp`로 연결해요. **어댑터에 호환되는 Codex가 함께 들어 있어서 별도의 전역 Codex 설치는 필수가 아니에요.** 독립 Codex CLI도 쓰고 싶다면 [Codex 공식 안내](https://developers.openai.com/codex/cli)를 따라 설치해요. 인증과 설치 방식은 [공식 ACP 프로젝트](https://github.com/agentclientprotocol/codex-acp#installation)를 확인해요.

### OpenClaw + openclaw acp

[공식 설치 안내](https://docs.openclaw.ai/install)와 [Node.js 요구사항](https://docs.openclaw.ai/install/node)을 따라요. Node.js/npm으로 설치한다면 npm 버전에 따라 명령이 달라요.

**npm 11.16 이상 또는 npm 12:**

```sh
npm install -g openclaw@latest --allow-scripts=openclaw
```

**npm 11.15 이하:**

```sh
npm install -g openclaw@latest
```

설치 후 공식 안내에 따라 모델·인증·Gateway를 설정해요. `openclaw acp`는 내장된 연결 기능이며, 동작하는 Gateway가 필요해요. [공식 ACP 안내](https://docs.openclaw.ai/cli/acp)와 [Windows 안내](https://docs.openclaw.ai/platforms/windows)를 참고해요.

### Hermes + hermes-acp

1. [Hermes 공식 설치 안내](https://hermes-agent.nousresearch.com/docs/getting-started/installation)에서 운영체제별 설치 방법을 따라요.
2. [공식 ACP 안내](https://hermes-agent.nousresearch.com/docs/user-guide/features/acp)에 따라 **ACP 추가 구성요소(`acp` extra)**도 준비해요. 기본 설치만으로 ACP가 준비됐다고 가정하지 마세요. 공식 ACP 문서의 소스 폴더 예시는 macOS/Linux용이므로 Windows에 그대로 붙여 넣지 마세요.
3. 로그인·모델 설정을 끝낸 뒤 리체에서 골라요. 리체는 `hermes-acp`로 연결해요. 공식 프로젝트는 `hermes acp`도 지원해요.

이 안내서는 Windows에서 Hermes의 ACP 추가 구성요소를 설치하는 명령을 따로 적지 않아요. Windows에서는 [Hermes 공식 ACP 안내](https://hermes-agent.nousresearch.com/docs/user-guide/features/acp)의 Windows 절차를 따라요. [공식 소스의 실행 명령·추가 구성요소](https://github.com/NousResearch/hermes-agent/blob/main/pyproject.toml)도 참고할 수 있어요.

### 리체 안의 설치 도우미

설치된 에이전트가 없으면 리체가 설치 순서, 복사할 명령, **설치 안내** 링크를 보여 줘요. **리체가 대신 설치하지는 않아요.**

- **macOS:** 첫 실행 안내의 **리체를 연결해주세요**에서 **설치 안 됨**인 줄을 눌러요. 명령 옆 **복사**를 누르고 터미널에서 실행해요. 약 5초마다 다시 찾아요.
- **Windows:** **연결 설정 › 다른 에이전트**의 **설치 방법 보기**를 눌러요. Hermes는 Hermes 카드에서 안내를 열어요. 설치 후 **다시 확인**으로 찾아요.
- 설치됐다고 나오면 그 에이전트의 **연결하기**를 눌러요.

도우미는 다음 순서를 안내해요. 설치 명령은 각 공식 프로젝트의 것이고 바뀔 수 있으니, 공식 안내의 최신 요구사항도 함께 확인해요.

| 준비할 것 | macOS | Windows PowerShell |
| --- | --- | --- |
| Node.js/npm | Homebrew가 있다면 `brew install node`. 오래된 버전이면 `brew upgrade node` 또는 [공식 다운로드](https://nodejs.org/en/download) | `winget install OpenJS.NodeJS` 또는 [공식 다운로드](https://nodejs.org/en/download) |
| OpenClaw | `npm install -g openclaw@latest --allow-scripts=openclaw` | 왼쪽과 같아요 |
| Claude Code | `curl -fsSL https://claude.ai/install.sh \| bash`, 다음으로 `npm install -g @agentclientprotocol/claude-agent-acp` | `irm https://claude.ai/install.ps1 \| iex`, 다음으로 `npm install -g @agentclientprotocol/claude-agent-acp` |
| Codex ACP | `npm install -g @agentclientprotocol/codex-acp` | 왼쪽과 같아요 |
| Hermes 기본 설치 | `curl -fsSL https://hermes-agent.nousresearch.com/install.sh \| bash` | `irm https://hermes-agent.nousresearch.com/install.ps1 \| iex` |

Hermes는 기본 설치 뒤 ACP 추가 기능도 필요해요. macOS의 기본 소스 설치에서는 아래 두 명령을 차례로 실행해요. 설치 위치나 Python 환경을 바꿨다면 그대로 복사하지 말고 [공식 ACP 안내](https://hermes-agent.nousresearch.com/docs/user-guide/features/acp)를 따라요. Windows는 같은 공식 안내에서 Windows용 절차를 따라요.

```sh
cd ~/.hermes/hermes-agent
python -c "import pm; pm.sync_venv(['acp'], explicit=True)"
```

도우미는 Node.js 버전이 부족하면 에이전트를 설치하지 않은 상태로 취급하고, Hermes는 `hermes-acp --check`로 ACP 준비 상태도 확인해요. 다운로드한 설치 스크립트는 각 공식 프로젝트가 제공하며 실행 전에 출처를 확인해 주세요.

## macOS에서 연결하기

첫 실행 안내의 **리체를 연결해주세요**에서 골라요. 닫았다면 대화창의 **리체 연결하기** 또는 **리체 설정 › 연결 › 연결 설정 열기**로 돌아가요.

- **이 컴퓨터에서 찾은 연결:** PATH와 `/opt/homebrew/bin`, `/usr/local/bin`, `~/.local/bin`에서 찾아요. 설치된 줄을 고르고 **연결하기**를 눌러요.
- **에이전트로 연결하기:** 목록에 없거나 다른 곳에 설치했다면 **복사**를 눌러, 복사한 글을 쓰고 있는 에이전트에 붙여 넣어요. 에이전트가 리체의 MCP 서버를 등록하고 대화 상대로 연결해요.

## Windows에서 연결하기

**연결 설정**에서 Hermes 카드 또는 **다른 에이전트** 목록의 OpenClaw·Claude Code·Codex를 골라요. 설치되지 않았다면 도우미의 공식 안내를 먼저 확인해요. **연결됨**이 보이면 끝이에요.

### Windows에서 다른 에이전트 연결하기

목록에 없는 ACP 에이전트는 대화창 프로그램 `LicheInput.exe`에 `--connect`를 주어 연결할 수 있어요. 리체는 그 명령을 저장해 두고 다음부터 같은 에이전트로 연결해요.

1. 리체를 켜 둬요.
2. 패키지의 `AgentLiche\Binaries\Win64`에서 `LicheInput.exe` 경로를 확인해요.
3. PowerShell에서 아래 예시의 경로와 `--` 뒤 명령을 바꿔 실행해요.

```powershell
& "<패키지 폴더>\AgentLiche\Binaries\Win64\LicheInput.exe" --connect -- claude-agent-acp
```

`Connected`로 시작하는 답이면 연결된 거예요. 답을 기다리는 중이거나 승인 요청이 남아 있으면 바꾸지 않아요.

## 에이전트가 할 수 있는 일

- **대화:** 일상·업무 대화를 따로 이어 가요. 모드별 작업 폴더는 macOS `~/Liche/<모드>`, Windows `문서\Liche\<모드>`예요.
- **승인 요청:** 도구 사용 전에 **승인** 또는 **거절**을 골라요. 리체는 자동 승인하지 않아요. **■ 중지**나 연결 종료 시 남은 요청은 취소돼요.
- **오래 걸리는 도구 작업:** 에이전트가 도구를 쓰는 동안에는 2분 "응답이 없어요" 제한이 없고, 아무 소식 없이 30분이 지날 때만 기다리기를 멈춰요. 대화창에는 "작업 중이에요 · 경과 시간"이 보여요 ([답을 기다리는 시간](first-run.md#답을-기다리는-시간)).
- **리체의 MCP 서버:** 표정·동작과 짧은 말풍선을 바꿀 수 있어요. 이 서버로 대화 기록·설정·키는 읽지 못해요.
- **모델과 생각 깊이:** **리체 설정 › 모드 › 일상(또는 업무) › 대화**에서 각각 골라요. **에이전트 기본값**이면 에이전트가 정한 값을 써요. 에이전트가 선택 기능을 제공하지 않으면 고를 수 없어요.
- **첨부:** 연결이 지원할 때만 첨부 단추가 보여요. 에이전트마다 지원 기능은 달라요.

## "응답하지 않아요"가 뜰 때

에이전트를 띄운 뒤 45초 안에 답을 받지 못하면 연결 카드와 대화창에 이유가 보여요.

1. 운영체제 권한 확인 창이 있다면 요청한 프로그램과 내용을 확인하고 답해요.
2. 에이전트를 직접 열어 로그인·모델 설정을 마쳐요.
3. 설치 위치와 ACP 추가 구성요소를 확인해요.
4. 리체는 잠시 뒤 다시 연결해 봐요. 계속 실패하면 **연결 설정 열기**에서 다시 골라요.
5. 해결되지 않으면 [진단 파일과 함께 문의](troubleshooting.md#문의할-때-알려-주시면-좋은-것)해요.

## 연결을 바꾸거나 끊기

연결 화면에서 새 에이전트를 고르면 저장한 연결이 바뀌어요. 어느 모드든 답을 기다리거나 승인 요청이 남아 있으면 바꿀 수 없어요. **■ 중지**를 누르거나 끝나기를 기다려요.

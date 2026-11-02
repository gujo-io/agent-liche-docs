# 제3자 고지

[안내서 처음으로](../README.md) · [English](../en/legal/third-party-notices.md)

Agent Liche에는 다른 회사와 개인이 만든 소프트웨어, 글꼴, 엔진이 들어 있어요. 리체 자체(프로그램, 캐릭터, 그림과 그 밖의 콘텐츠)는 판매자의 것이며 아래 라이선스로 배포하지 않아요. 리체의 사용 조건은 [최종 사용자 사용권 계약 (EULA)](eula.md)에 있고, 각 구성 요소에는 그 구성 요소의 라이선스가 적용돼요.

## 고지 파일

전체 목록과 라이선스 전문은 패키지에 들어 있는 **`THIRD-PARTY-NOTICES.txt`**가 기준이에요. 이 페이지는 그 파일을 찾는 방법과 주요 구성 요소를 요약해요. 이 페이지와 고지 파일이 다르면 고지 파일이 우선해요.

| 플랫폼 | 고지 파일의 위치 |
| --- | --- |
| Windows | 압축을 푼 폴더 맨 위, `AgentLiche.exe` 옆의 `THIRD-PARTY-NOTICES.txt` |
| macOS | `Agent Liche.app/Contents/Resources/THIRD-PARTY-NOTICES.txt` (Finder에서 앱을 오른쪽 클릭 › **패키지 내용 보기**) |

**리체 설정 › 리체 정보 › 도움말과 약관 › 제3자 고지**를 누르면 이 파일이 기본 텍스트 앱으로 열려요. 파일을 찾지 못하면 이 페이지를 열어요.

Windows 패키지의 `AgentLiche\Binaries\Win64`에는 글꼴 안내 `Pretendard-OFL.txt`와 `Liche-Font-Sources.md`도 들어 있어요.

## 고지 파일의 구성

1. **Unreal Engine:** Unreal® Engine 사용권의 표시 문구, 리체 캐릭터 프로그램(Shipping 빌드)이 Windows와 macOS에서 실제로 쓰는 엔진의 제3자 모듈과 그 라이선스 전문(엔진의 모듈 목록에서 만든 것), 엔진 모듈 안에 들어 있는 다른 출처의 코드
2. **Unreal Engine 플러그인:** KawaiiPhysics와 프로젝트의 다른 플러그인
3. **글꼴과 그 밖의 자료:** NEXON Lv.1 Gothic, 교보 손글씨 2019, Hermes Agent 아이콘(macOS 패키지만), 화면 라이브러리의 기본 글꼴
4. **Rust 라이브러리:** 대화창 프로그램(`LicheInput`)과 감정 판단 프로그램(`liche-judge`)이 쓰는 모든 크레이트와 그 라이선스 전문

## 주요 구성 요소

| 구성 요소 | 권리자 | 비고 |
| --- | --- | --- |
| Unreal® Engine 5.8 | Epic Games, Inc. | 리체 캐릭터를 그리는 엔진이에요 |
| KawaiiPhysics | pafuhana1213 | 머리카락과 옷의 흔들림을 계산하는 플러그인이에요. MIT 라이선스 |
| NEXON Lv.1 Gothic | NEXON Korea | 설정 창과 메뉴의 글꼴이에요 |
| 교보 손글씨 2019 | 교보문고 | 대화창 말풍선의 글꼴이에요. 앱 안에 포함해서만 써요 |
| Rust 라이브러리 | 각 라이브러리의 저작자 | 대화창 프로그램과 감정 판단 프로그램이 쓰는 라이브러리예요. 각자의 라이선스를 따라요 |
| Microsoft Visual C++ 재배포 패키지 | Microsoft Corporation | Windows 패키지에만 들어 있어요. 필요한 PC에서만 시작 파일이 설치를 물어요 |

Agent Liche uses Unreal® Engine. Unreal® is a trademark or registered trademark of Epic Games, Inc. in the United States of America and elsewhere.

Unreal® Engine, Copyright 1998 – 2026, Epic Games, Inc. All rights reserved.

Portions of this software are copyright © The FreeType Project (http://www.freetype.org). All rights reserved.

## 함께 쓰는 바깥 서비스

아래는 리체에 들어 있지 않고, 여러분이 고르면 함께 쓰는 서비스예요. 각 서비스의 약관을 따라요.

- 여러분이 연결한 AI 에이전트(Claude Code, Codex, OpenClaw, Hermes 등)와 그 AI 서비스
- 감정 판단(JEV)을 켰을 때의 TypeSafe AI

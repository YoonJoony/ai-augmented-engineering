---
title: Codex에 Jane Street 소크라테스 튜터 설치하고 사용하기
created: 2026-11-17
topics:
  - ai-workflow
  - environment
  - developer-growth
  - verification
---

# Codex에 Jane Street 소크라테스 튜터 설치하고 사용하기

## 확인한 근거

- [Codex 공식 스킬 안내](https://developers.openai.com/codex/skills): 프로젝트의 `.agents/skills/`, 사용자의 `~/.agents/skills/` 등에서 로컬 스킬을 탐색합니다. 스킬은 name과 description이 있는 SKILL.md를 포함합니다. 명시적 호출과 description에 따른 자동 선택을 구분합니다.
- [Jane Street 원문](https://github.com/janestreet/agent_skills/blob/master/socratic-tutor/SKILL.md): SKILL.md 형식의 소크라테스식 학습 지침입니다.
- [MIT 라이선스](https://github.com/janestreet/agent_skills/blob/master/LICENSE.md): 배포 시 저작권 고지와 라이선스를 보존합니다.

2026-11-17에 위 문서와 현재 환경의 Codex CLI 도움말을 확인했습니다. 이 설치는 현재 작업하는 레포에 적용되며 사용자의 다른 컴퓨터에 전역 설치한 것은 아닙니다.

## 설치한 파일

```text
.agents/skills/socratic-tutor/
├── SKILL.md
└── LICENSE.md
```

- [설치한 SKILL.md](../.agents/skills/socratic-tutor/SKILL.md)는 원문을 수정하지 않은 사본입니다.
- [라이선스](../.agents/skills/socratic-tutor/LICENSE.md)도 함께 보존합니다.
- 확인한 원문 스킬의 Git blob SHA: `93bb7befeb73c41b4354175f9ef765547d4f3506`
- 확인한 라이선스의 Git blob SHA: `cb7afe58fa6a98b61f7a572e3318b98c28f91955`
- 별도의 설치 스크립트나 외부 코드는 실행하지 않습니다.

## 이 레포에서 사용하기

1. 다른 컴퓨터에서 사용한다면 그 컴퓨터의 로컬 레포에 변경을 받습니다. 로컬 변경이 있다면 보존하고 충돌을 해결합니다.

   ```bash
   git pull --ff-only
   ```

2. Codex가 이 레포를 작업 프로젝트로 열고 있는지 확인합니다. Codex CLI나 IDE 확장에서는 `/skills` 또는 `$`로 스킬 목록을 확인하고 `socratic-tutor`를 선택할 수 있습니다. 표시되지 않으면 경로·현재 프로젝트·비활성화 설정을 확인하고 Codex를 다시 시작합니다. 클라이언트별 UI는 다를 수 있습니다.
3. 스킬 이름과 학습 범위를 명시합니다.

   ```text
   $socratic-tutor
   이 레포의 AGENTS.md를 따르면서 API 멱등성을 학습하고 싶어.
   먼저 내가 아는 것을 진단하고, 한 번에 한 질문씩 해줘.
   목표는 재시도 상황에서의 중복 처리를 내가 설명하고 검증하는 거야.
   ```

4. 명시적 스킬 선택을 지원하지 않는 화면에서는 실제 SKILL.md를 읽어 사용해달라고 요청할 수 있습니다. 이것은 파일을 읽고 지침을 적용하는 방법이며, 해당 화면의 자동 스킬 등록을 검증했다는 뜻은 아닙니다.
5. 질문에 내 말로 답합니다. 명시적인 튜터 학습에서는 처음부터 전체 강의를 받는 대신 진단과 한 문항씩의 질문을 진행합니다.

## 다른 프로젝트와 전역 설치

프로젝트 설치를 다른 레포에서 쓰려면 해당 레포의 `.agents/skills/socratic-tutor/`에도 두 파일을 복사합니다. 모든 프로젝트에서 쓰려면 사용자의 컴퓨터에서 `~/.agents/skills/socratic-tutor/`에 둘 수 있습니다. 기존에 같은 이름의 스킬이 있는지 확인하고 덮어쓰기 전에 비교합니다.

스킬 파일만 다른 곳으로 복사하면 이 레포의 AGENTS.md가 함께 적용되는 것은 아닙니다. 아래 사용자 학습 규칙도 해당 프로젝트에서 명시해야 같은 방식으로 사용할 수 있습니다.

## 사용자 학습 규칙과의 차이

원문은 명시적인 학습 요청을 대상으로 하며 단발성 설명 질문은 일반 답변으로 처리합니다. 여러 번 실패하면 설명을 제공할 수 있습니다. 이 레포에서는 사용자가 정한 다음 규칙을 우선합니다.

- 필수 전제 확인이 필요하면 통과 기준을 밝히고, 기준에 맞는 실제 응답을 받을 때까지 본답변을 보류합니다.
- 틀린 답에는 완성된 정답 대신 힌트와 재질문을 제공합니다. 사용자가 이후 명시적으로 방식을 바꾸면 최신 요청을 따릅니다.
- 본답변 뒤에는 질문지를 만들고, 실제 응답에서 중요한 항목만 문제집으로 남깁니다.
- 문제집 해설은 재풀이 후에 제공합니다. 이해도를 AI의 판단만으로 확정하지 않습니다.

이 차이는 원문 파일을 고치는 대신 [AGENTS.md](../AGENTS.md)에 기록했습니다.

## 검증 범위

설치 파일 두 개의 Git blob SHA가 열람한 원문과 정확히 일치하는 것을 확인했습니다. 스킬의 `name`·`description`, 일반 문서의 메타데이터, 상대 경로 링크도 확인했습니다.

현재 클라우드의 Codex CLI에서 app-server의 `skills/list`로 프로젝트 스킬 발견 여부를 조회했으나 응답을 얻지 못했습니다. 따라서 실제 자동 인식은 미확인입니다. 사용자의 로컬 Codex에서 목록에 나타나는지와 실제 질문·평가 행동은 그 환경에서 별도로 확인해야 합니다. 파일 설치만으로 행동이 항상 강제되지는 않습니다.

## 이번 답변 뒤의 학습

이전 질문지의 실제 응답을 평가하고 [핵심 문제집](open-source-learning-skills-workbook.md)을 만들었습니다. 이번에는 그 문제집의 문제 1을 후속 질문으로 사용합니다. 질문을 중복해서 늘리지 않고 한 문항씩 진행합니다.

---
title: 개발자의 판단력을 지키는 오픈소스 에이전트 스킬 비교
created: 2026-11-17
topics:
  - ai-workflow
  - architecture
  - verification
  - developer-growth
---

# 개발자의 판단력을 지키는 오픈소스 에이전트 스킬 비교

## 조사 질문과 범위

사용자 질문: AI에게 끌려가는 개발, AI 슬롭, 근거 없는 구현 요청, 설계 이해 없이 구현을 맡기는 상황을 AI가 지적하고 학습으로 연결하는 오픈소스 스킬이 있는가?

2026-11-17에 아래 저장소의 공개 README, 실제 스킬 지침, 일부 라이선스를 읽었습니다. 설치하거나 실제 에이전트에서 동작을 시험하지는 않았습니다. 아래 내용은 문서에 적힌 동작이며, 모든 모델과 도구에서의 준수를 보장하는 실험 결과가 아닙니다. 외부 스킬은 비교 자료로 읽었으며 이 저장소의 실행 지침으로 채택하지 않았습니다.

이번 질문은 후보를 탐색하는 요청입니다. 질문에 구체적인 전제 오류가 드러나지 않아 본답변 전 확인 질문으로 보류할 필요는 없다고 판단했습니다. 이전 질문지에 답하지 않았다는 사실 자체를 새 탐색 질문을 막는 사유로 삼지는 않습니다.

## 확인한 후보

### Jane Street: socratic-tutor

- 출처: [실제 SKILL.md](https://github.com/janestreet/agent_skills/blob/master/socratic-tutor/SKILL.md), [README](https://github.com/janestreet/agent_skills/blob/master/README.md), [MIT 라이선스](https://github.com/janestreet/agent_skills/blob/master/LICENSE.md)
- 읽은 스킬의 blob SHA: `93bb7befeb73c41b4354175f9ef765547d4f3506`
- 원문에서 확인한 내용: 진단으로 시작하고, 한 번에 한 질문을 하며, 설명·예측·새 사례 적용을 요구합니다. 수준 상승에는 독립적인 확인을 여러 번 요구하고 이전 내용을 다시 묻습니다.
- 한계: 명시적으로 학습·퀴즈를 요청할 때 사용하는 지침입니다. 일반적인 단발성 질문은 기본적으로 튜터링 대상에서 제외합니다. 2~3번 실패하면 직접 설명할 수 있고 현재 질문의 튜터 모드를 해제하는 명령도 있습니다.
- 내 해석: 이해를 드러내도록 질문하는 부분이 사용자 목적과 가깝습니다. 사용자가 원하는 상시 선행 확인과 정답 공개 보류 규칙은 별도로 조정해야 합니다.

### obra/superpowers: brainstorming, verification-before-completion

- 출처: [brainstorming](https://github.com/obra/superpowers/blob/main/skills/brainstorming/SKILL.md), [verification-before-completion](https://github.com/obra/superpowers/blob/main/skills/verification-before-completion/SKILL.md), [MIT 라이선스](https://github.com/obra/superpowers/blob/main/LICENSE)
- 읽은 brainstorming의 blob SHA: `9eb0edc7fedf26e1d3e2f3f223e5bcc5058aed6a`
- 읽은 verification-before-completion의 blob SHA: `7d45333cc4a49c57a80df6c1fe2fa777a207afbc`
- 원문에서 확인한 내용: brainstorming은 기존 프로젝트를 먼저 읽고, 필요한 질문과 대안 비교를 거쳐 설계를 문서화하고 승인받은 뒤 구현 계획으로 넘어가도록 지시합니다. 명확하고 작은 작업, 질문 생략 요청, 합의한 탐색용 시도에 대한 예외도 있습니다. verification-before-completion은 완료·성공 주장 전에 해당 주장을 뒷받침할 검증을 실제로 수행하고 결과를 확인하도록 지시합니다.
- 한계: 설계 승인과 실행 증거는 사용자의 이해를 직접 평가하는 기준이 아닙니다. 검증 명령을 실행했다는 사실만으로 그 명령이나 테스트가 요구사항을 충분히 다뤘다고 판단할 수도 없습니다.
- 내 해석: 근거 없는 착수와 완료 주장을 줄이는 개발 절차의 참고 자료로 적합합니다. 학습 확인 절차와 결합할 필요가 있습니다.

### multica-ai/andrej-karpathy-skills: karpathy-guidelines

- 출처: [실제 SKILL.md](https://github.com/multica-ai/andrej-karpathy-skills/blob/main/skills/karpathy-guidelines/SKILL.md), [README](https://github.com/multica-ai/andrej-karpathy-skills/blob/main/README.md)
- 읽은 스킬의 blob SHA: `6a62d0441753157ca6ca50479e490c2948033adb`
- 원문에서 확인한 내용: 가정과 불확실성을 드러내고, 단순한 해결책을 우선하며, 요청과 직접 관련된 변경만 하고, 검증 가능한 완료 기준을 정하도록 지시합니다. README와 스킬 메타데이터에는 MIT라고 표기되어 있습니다.
- 주의: Karpathy의 관찰에서 영감을 받은 커뮤니티 프로젝트입니다. 이름만으로 Karpathy가 직접 만든 공식 스킬이라고 소개하지 않습니다. 이번 열람에서 저장소 루트의 별도 라이선스 파일은 확인하지 못했습니다.
- 한계: 개발자의 이해도를 진단하거나 응답에 맞춰 문제집을 만드는 튜터링 절차는 확인한 스킬 본문에 없습니다.
- 내 해석: 요청하지 않은 기능, 과한 추상화, 무관한 수정 등 구체적인 코드 품질 문제를 줄이는 지침으로 참고할 수 있습니다. 모든 AI 슬롭을 판별하는 탐지기로 해석하지 않습니다.

### Anthropic: learning-output-style

- 출처: [공식 저장소의 README](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/learning-output-style/README.md)
- 읽은 README의 blob SHA: `8a83ffdf60d3e312465a81f6fdaacf7d28b2e6f3`
- 원문에서 확인한 내용: Claude Code의 SessionStart hook으로 학습 지침을 추가하는 플러그인입니다. 중요한 로직·설계 결정에서 사용자가 약 5~10줄의 의미 있는 코드를 직접 작성하도록 유도하고 판단의 배경을 설명합니다.
- 한계: 범용 SKILL.md 하나와는 배포 형태가 다릅니다. 핵심 코드에 참여하도록 하는 것과 아키텍처 이해를 통과 기준으로 평가하는 것은 별개의 동작입니다. 이번 조사에서는 README를 확인했으며 hook 실행과 실제 효과는 검증하지 않았습니다.
- 내 해석: 코드를 직접 써보는 연습에 가깝습니다. 현재 문서 저장소보다 별도의 개발 프로젝트에서 검토할 후보입니다.

## 비교에서 도출한 판단

확인한 자료 중에는 사용자가 원하는 전체 흐름, 즉 잘못된 전제 감지부터 선행 확인·본답변 보류·질문지·실제 응답 기반 문제집까지를 그대로 제공하는 사례는 확인하지 못했습니다. 생태계 전체에 그런 스킬이 없다고 단정하는 결론은 아닙니다.

이 저장소에서는 다음 역할을 구분해 구성하는 것이 적합하다고 판단합니다.

1. 소크라테스식 질문으로 개발자의 이해와 판단을 드러냅니다.
2. 설계 전 질문과 대안 비교로 구현할 이유와 조건을 명확히 합니다.
3. 실제 검증 증거와 최소 변경 원칙으로 결과물을 검토합니다.
4. 응답에서 중요한 항목만 문제집으로 남기는 규칙은 기존 학습 대화 원칙으로 관리합니다.

설치만으로 개발자의 이해나 코드 품질이 보장되지는 않습니다. 언제 지침이 로드되는지, 실제 응답이 규칙을 따르는지, 확인 질문과 평가가 타당한지 따로 관찰해야 합니다. 자동 로딩과 행동의 강제는 구분해야 합니다.

## 적용 전에 확인할 점

- 사용 중인 에이전트에서 지침을 어떤 경로와 시점에 읽는지 확인합니다.
- 원문, 포함 스크립트, 도구 권한, 라이선스를 검토합니다. 외부 지침을 실행하기 전 자료 열람과 설치를 구분합니다.
- 기존 AGENTS.md의 학습 규칙과 충돌하는 정답 공개·질문 생략·문서 저장 경로를 조정합니다.
- 필요한 근거가 부족한 설계 요청, 전제가 틀린 요청, 이미 충분히 설명된 요청을 각각 시험해 질문과 보류가 적절한지 확인합니다.
- 테스트 통과, 코드 길이, 문서의 그럴듯함만으로 설계 품질이나 이해도를 판정하지 않습니다.

관련 문서: [학습 대화 운영 원칙](../notes/learning-dialogue-protocol.md), [이번 답변의 질문지](../notes/open-source-learning-skills-questions.md)

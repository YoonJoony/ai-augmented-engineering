# AI-Augmented Engineering

AI와 함께 개발하며 주도적으로 판단하는 엔지니어로 성장하기 위한 학습과 실천을 기록합니다. 아키텍처, 개발 환경, 검증, AI 에이전트 협업과 코드베이스 관리를 다룹니다.

이 저장소는 개인 블로그에 올릴 글과 그 바탕이 되는 자료·메모를 Markdown 문서로 관리합니다. 기록은 빠르게 남기고, 독자에게 전달할 생각은 근거와 맥락을 갖춘 글로 다듬습니다.

## 디렉토리 구조

```text
.
├── README.md
├── AGENTS.md
├── inbox/       # 아직 정리하지 않은 생각과 메모
├── references/  # 외부 글·영상·발표를 읽은 기록
├── notes/       # 내 생각, 학습, 실험과 판단
├── posts/       # 블로그 초안과 발행본
│   └── 2026/
└── templates/   # 자료·메모·실험·글쓰기 양식
```

| 위치 | 저장 기준 | 시작 문서 |
| --- | --- | --- |
| `inbox/` | 떠오른 질문이나 아직 분류하지 않은 기록 | [에이전트 리뷰 아이디어](inbox/agent-review-idea.md) |
| `references/` | 외부 자료의 주장과 내 해석을 구분한 기록 | [외부 자료 기록 예시](references/example-agent-workflow.md) |
| `notes/` | 하나의 질문이나 생각, 학습·실험 기록 | [AI 활용의 주도권](notes/keeping-control-with-ai.md) |
| `posts/` | 배경 설명을 갖춘 독립적인 블로그 글 | [첫 글 초안](posts/2026/understanding-before-delegating.md) |
| `templates/` | 복사해서 쓰는 문서 양식 | [메모 양식](templates/note.md) |

## 기록 방법

1. 생각은 `inbox/`에 짧게 남깁니다. 위치가 명확하면 해당 폴더에 바로 작성합니다.
2. 외부 자료는 [자료 양식](templates/reference.md), 내 생각은 [메모 양식](templates/note.md), 실험은 [실험 양식](templates/experiment.md)을 복사합니다.
3. 전달할 논지가 생기면 [글 양식](templates/post.md)으로 `posts/연도/`에 초안을 만듭니다.
4. 관련 자료와 메모를 상대 경로 링크로 연결합니다. 모든 문서를 정해진 순서로 이동시킬 필요는 없습니다.
5. 발행하면 같은 파일의 `status`를 `published`로 바꾸고 `published_at`, `blog_url`을 추가합니다. 블로그 게시 주소는 실제 발행 후 기록합니다.

예시 파일은 구조와 작성 방식을 보여주기 위한 출발점입니다. 특히 외부 자료 예시는 실제 자료 요약이 아니며, 실험 예시는 아직 실행하지 않은 계획입니다.

## 질문을 학습으로 연결하기

학습 대화는 `질문 → 필요한 선행 확인 → 본답변과 질문지 → 내 답변 → 핵심 문제집 → 재풀이` 순서로 이어갑니다.

- 답변마다 이해 확인 질문을 함께 받고, 내 말로 이유와 검증 방법을 설명합니다.
- 잘못된 전제나 필수 개념의 혼동이 드러나면 먼저 확인 질문에 답합니다. 통과 기준을 충족할 때까지 본답변은 보류합니다.
- 질문지 응답 후 중요한 개념만 선별해 문제집을 만듭니다. 정답을 미리 보지 않고 다시 풀고, 피드백을 받은 뒤 보완합니다.
- 질문지와 문제집은 `notes/`에 저장하고 원래 메모·자료·글과 연결합니다. 질문을 위해 별도 디렉토리를 늘리지는 않습니다.

자세한 기준은 [학습 대화 운영 원칙](notes/learning-dialogue-protocol.md), 작성 양식은 [질문지](templates/questionnaire.md)와 [문제집](templates/workbook.md)을 참고합니다.

## 파일 이름과 메타데이터

- 파일 이름은 내용을 설명하는 영문 `kebab-case.md`로 작성합니다. 날짜는 파일명에 반복하지 않습니다.
- 블로그 글은 `posts/작성연도/`에 두고 발행 후에도 경로를 유지합니다.
- 문서 상단에는 `title`, `created`, `topics`를 기록합니다. 날짜는 한국 시간 기준 `YYYY-MM-DD`로 작성합니다.
- 의미 있는 수정에는 `updated`를 추가합니다. 글에는 `status: draft` 또는 `status: published`를 사용합니다.
- 템플릿의 `YYYY-MM-DD`, `TODO`는 실제 값으로 교체합니다. 사용하지 않는 항목은 지워도 됩니다.

```yaml
---
title: AI에게 위임하기 전에 내가 이해해야 하는 것
created: 2026-11-17
topics:
  - ai-workflow
  - developer-growth
status: draft
---
```

## 주제

주제는 폴더를 더 나누는 대신 `topics`로 표현합니다. 하나의 문서에 여러 주제를 붙일 수 있습니다.

| 주제 | 다루는 내용 |
| --- | --- |
| `ai-workflow` | AI 활용 원칙, 에이전트 협업, 해외 개발자의 활용 사례 |
| `architecture` | 설계, 경계, 의존성, 기술적 의사결정 |
| `environment` | 개발 환경, 도구, 재현성, 자동화 |
| `verification` | 테스트, 리뷰, 결과 검증 |
| `codebase` | 코드 품질, 정리, 유지보수 |
| `developer-growth` | 학습법, 이해력, 문제 해결 역량 |

## 다음으로 읽을 문서

- [개발자의 판단력을 지키는 오픈소스 스킬 비교](references/open-source-skills-for-independent-engineering.md)
- [학습 대화 운영 원칙](notes/learning-dialogue-protocol.md)
- [아키텍처 리뷰를 연습하는 방법](notes/architecture-review-practice.md)
- [AI 에이전트와 코드 정리를 실험하는 계획](notes/agent-code-cleanup-experiment.md)
- [AI 에이전트의 문서 편집 규칙](AGENTS.md)

현재 저장소는 문서만 관리하며, 블로그 배포나 자동 발행은 별도로 연결하지 않았습니다.

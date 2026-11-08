# Clarity Toolkit for Claude

[English README](README.md)

아이디어를 인터뷰로 구체화하고, 대화 중에 다듬은 초안을 독립적인 최종본으로 만들고, 다음 작업자에게 맥락을 넘기는 Claude용 스킬 3개입니다.

| 스킬 | 이런 상황에 사용하세요 |
| --- | --- |
| `grill-me` | 아이디어나 계획은 있지만 요구사항을 정하지 못했을 때 |
| `meta-conv-filter` | 대화에서 다듬은 초안을 대화를 보지 못한 사람도 이해할 수 있게 만들 때 |
| `handoff` | 다른 사람·에이전트·새 세션으로 작업을 넘기거나, 넘겨받은 내용으로 이어갈 때 |

세 스킬은 Claude의 기본 습관을 바로잡기 때문에 남겼습니다. Claude는 인터뷰보다 바로 작업을 시작하는 경향이 있고, 최종본에 "앞서 말씀하신" 같은 표현을 남기기 쉬우며, 제안한 계획과 실제로 끝낸 작업을 섞어 쓰기도 합니다. 다시 설명하기(`wait-what`)와 질문지 작성(`to-questionnaire`)은 Claude의 기본 동작으로 충분해 포함하지 않았습니다.

## 설치

### Claude 앱 (claude.ai)

`skills/<이름>/SKILL.md` 파일을 Claude 설정에서 스킬로 저장하세요. GitHub를 읽고 스킬을 제안할 수 있는 대화라면 다음 요청을 붙여 넣어도 됩니다.

> https://github.com/steves460ng/clarity-toolkit-claude
> `skills/` 아래의 SKILL.md 3개를 읽고 내가 저장할 수 있게 스킬로 제안해 줘. 같은 이름의 스킬이 이미 있으면 새로 만들지 말고 업데이트해 줘.

### Claude Code

```
/plugin marketplace add steves460ng/clarity-toolkit-claude
/plugin install clarity-toolkit@clarity-toolkit-claude
```

## 사용 방법

자연어로 요청하세요. 스킬 이름을 함께 적으면 원하는 절차가 더 확실하게 선택됩니다.

### grill-me — 질문으로 요구사항 구체화하기

> grill-me로 인터뷰해 줘. 사내 신규 입사자를 위한 온보딩 페이지를 만들고 싶어.

한 라운드에 1~2개의 열린 질문을 하며, 사용 대상처럼 먼저 정해야 할 것부터 묻습니다. 자유롭게 답하거나 질문 번호로 답하고, 질문을 건너뛰거나 고쳐도 됩니다. 언제든 "여기까지 하고 정리해 줘"라고 요청할 수 있습니다.

**결과물:** 목표, 주요 사용자, 범위, 확정된 결정, 제약, 미해결 사항을 담은 요약. 요약을 확인하는 것이 구현 승인을 뜻하지는 않습니다.

### meta-conv-filter — 대화 없이도 이해되는 글로 다듬기

> meta-conv-filter로 이 계획을 우리 대화를 보지 않은 사람도 이해할 수 있게 정리해 줘.

"개선된 버전" 같은 수정 흔적과 "앞서 말씀하신" 같은 대화 언급을 없애고, "두 번째 안"처럼 대화에서만 통하는 표현을 실제 결정 내용으로 바꿉니다. 확인할 수 없는 정보는 지어내지 않고 미정으로 표시하며, 사실·수치·불확실성·출처는 그대로 유지합니다.

**결과물:** 무엇을 지웠는지 설명하는 서두 없이, 정리된 글 자체.

### handoff — 다음 작업자에게 맥락 넘기기

> handoff로 지금까지의 대화를 정리해 줘. 다음 세션에서는 모바일 화면 설계부터 이어갈 거야.

확정된 결정, 근거가 있는 완료 작업, 제안, 미해결 사항, 다음 행동을 구분해 정리합니다. 비밀번호나 토큰은 `[REDACTED]`로 바꿉니다. 새 대화에 인수인계 문서를 붙여 넣으면, Claude는 이를 현재 상태의 증거가 아니라 확인할 맥락으로 다룹니다.

**결과물:** 다음 작업자나 새 세션이 이어서 작업할 수 있는 인수인계 문서. Claude는 이전 대화를 스스로 기억하지 않으므로 문서를 직접 옮겨야 합니다.

## 함께 사용하는 예시

1. `grill-me`로 아이디어를 구체화합니다.
2. 정리된 요약이나 초안을 `meta-conv-filter`로 최종본으로 다듬습니다.
3. `handoff`로 맥락과 다음 행동을 넘깁니다.

## 결과물 형식

인터뷰 질문은 대화창에 바로 표시됩니다. 요약, 최종본, 인수인계 문서는 세션이 지원하면 편집 가능한 문서로 만들고, 지원하지 않으면 복사할 수 있는 Markdown 블록 하나로 제공합니다. `.md` 파일은 요청할 때만 만듭니다.

## 라이선스 및 출처

MIT 라이선스로 배포합니다. `grill-me`와 `handoff`는 [Clarity Toolkit](https://github.com/steves460ng/clarity-toolkit)을 거쳐 [Matt Pocock의 스킬](https://github.com/mattpocock/skills)을 변형한 것이고, `meta-conv-filter`는 Clarity Toolkit에서 새로 만든 스킬입니다. 자세한 내용은 [LICENSE](LICENSE)와 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)를 참고하세요.

이 프로젝트는 Matt Pocock이나 Anthropic과 제휴하거나 공식 승인을 받은 프로젝트가 아닙니다.

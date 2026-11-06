# FromMyDear-docs

Documentation, API specs, & system architecture for From My Dear.

이 레포는 iOS·Server 작업의 **기준 문서**입니다. 문서와 코드가 다르면 문서를 먼저 고치고 코드를 맞춥니다.

## 문서 목록

| 문서 | 내용 | 주로 보는 곳 |
| --- | --- | --- |
| [PRD.md](PRD.md) | 제품 목표, MVP 범위, 사용자 스토리, 정책 | 전체 |
| [SCREEN_SPEC.md](SCREEN_SPEC.md) | 화면 목록, 이동, 빈·오류·로딩 상태 | 디자인, iOS |
| [DATA_MODEL.md](DATA_MODEL.md) | 엔터티, 소유권·공개 범위 표 | Server |
| [API_CONTRACT.md](API_CONTRACT.md) | 공통 규칙, 엔드포인트, 오류 코드 | iOS, Server |
| [BACKLOG.md](BACKLOG.md) | 개발 작업, 의존성, 완료 조건 | 전체 |
| [adr/](adr/) | 기술·제품 결정 기록 | 전체 |
| [prompts/](prompts/) | 기획·디자인·백엔드·iOS용 AI 작업 프롬프트 | 전체 |

## 관련 레포

- [FromMyDear-iOS](https://github.com/FromMyDear/FromMyDear-iOS) — SwiftUI + Tuist
- [FromMyDear-Server](https://github.com/FromMyDear/FromMyDear-Server) — Spring Boot + PostgreSQL

## 문서 작성 흐름

1. `prompts/01-pm-architect.md`로 PRD·SCREEN_SPEC·DATA_MODEL·API_CONTRACT·BACKLOG 내용을 만든다.
2. 미정 항목은 `제안한 기본값`으로 표시하고, 확정되면 `adr/`에 결정을 남긴다.
3. API 계약을 바꿀 때는 PR에 iOS·Server 영향 범위를 적는다.

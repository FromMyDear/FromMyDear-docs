# API 계약

> 버전: v1 초안. 아래 '공통 규칙'은 iOS·Server 기본 코드에 이미 반영되어 있다.

## 공통 규칙

| 항목 | 규칙 |
| --- | --- |
| Base path | `/api/v1` |
| 형식 | JSON, UTF-8 |
| 인증 | `Authorization: Bearer <access token>` (인증 단계에서 확정) |
| 시각 | ISO-8601 UTC 문자열, 예: `2026-11-06T12:00:00Z` |
| 날짜 | `YYYY-MM-DD` (종일 일정) |
| 페이지네이션 | 커서 방식 제안: `?cursor=...&size=20` → `{ "items": [...], "nextCursor": "..." }` (제안한 기본값) |
| 멱등성 | 생성 요청에 `Idempotency-Key` 헤더 (영상 게시 등, 제안한 기본값) |
| 동시 수정 | 요청에 `version` 포함, 불일치 시 409 `CONFLICT` (제안한 기본값) |

## 오류 응답

모든 오류는 같은 형식으로 응답한다.

```json
{
  "code": "INVALID_REQUEST",
  "message": "요청 값이 올바르지 않습니다.",
  "fieldErrors": [{ "field": "title", "reason": "must not be blank" }]
}
```

| code | HTTP | 의미 |
| --- | --- | --- |
| INVALID_REQUEST | 400 | 요청 값 오류 |
| UNAUTHORIZED | 401 | 로그인 필요·토큰 만료 |
| FORBIDDEN | 403 | 접근 권한 없음 |
| NOT_FOUND | 404 | 대상 없음 |
| CONFLICT | 409 | 동시 수정 충돌 |
| INTERNAL_ERROR | 500 | 서버 오류 |

도메인별 코드(예: `INVITATION_EXPIRED`)는 해당 기능을 만들 때 이 표에 추가한다.

## 엔드포인트

### 상태 확인

| Method | Path | 인증 | 응답 |
| --- | --- | --- | --- |
| GET | `/actuator/health` | 불필요 | `{"status":"UP"}` |

### 인증 · 커플 연결 · 영상 · 일정 · 목록 · 여행 · 일기 · 문장 · 알림

(기획 문서 확정 후 작성)

## 변경 제안

개발 중 새 계약이 필요하면 아래에 남기고 PR로 합의한다.

| 날짜 | 제안자 | 내용 | 영향 | 상태 |
| --- | --- | --- | --- | --- |

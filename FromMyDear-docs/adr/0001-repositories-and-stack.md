# ADR-0001: 레포 구성과 기술 스택

- 날짜: 2026-11-06
- 상태: 확정

## 배경

iOS 앱, API 서버, 기획 문서를 각각 독립적으로 관리하면서 같은 계약을 따르게 해야 한다.

## 결정

| 레포 | 스택 |
| --- | --- |
| FromMyDear-iOS | SwiftUI, Swift 6, iOS 17.0+, Tuist 4(mise), Swift Testing |
| FromMyDear-Server | Java 21, Spring Boot 4.1.2, Gradle, PostgreSQL 17, Flyway, Testcontainers |
| FromMyDear-docs | Markdown 기준 문서, ADR |

- 서버는 모듈형 모놀리스로 시작한다. Redis·메시지 브로커·마이크로서비스는 필요가 입증되면 추가한다.
- iOS 프로젝트 파일은 Tuist로 생성하고 커밋하지 않는다.
- API 계약의 기준은 이 레포의 API_CONTRACT.md이다.

## 이유

- iOS 17: `@Observable`로 상태 관리를 단순하게 할 수 있다.
- Tuist: `.xcodeproj` 병합 충돌을 없애고 설정을 코드로 리뷰할 수 있다.
- Testcontainers: 동시 초대 수락 같은 규칙을 실제 PostgreSQL에서 검증해야 한다.

## 영향

- iOS 개발자는 `mise install && tuist install && tuist generate`로 시작한다.
- 서버 테스트에는 Docker가 필요하다.

# team7 API

이 문서는 어떤 AI 코딩 도구(Claude Code, Codex, Cursor, Copilot, Gemini 등)를 쓰든 공통으로 따르는 팀 규칙이다.
작업 전에 아래 "컨벤션 문서" 중 해당하는 문서를 읽고 따른다.

## 프로젝트 개요
백엔드 API 서버

## 기술 스택
- Java 21
- Spring Boot 4.1.2
- Gradle 9.9.1 (Gradle Wrapper)
- Spring Data JPA
- 테스트: JUnit 5 (JUnit Platform)
- DB: MySQL (개발·운영 환경 통일) <!-- 팀 프로젝트명 정해진 후, 추가 -->

## 빌드 & 실행
```bash
./gradlew build       # 빌드
./gradlew bootRun     # 실행
./gradlew test        # 테스트
./gradlew clean build # 클린 빌드
```

## 설정 파일
- `src/main/resources/application.yml`

## 컨벤션 문서
| 작업 | 문서 |
|---|---|
| 커밋 | `docs/conventions/commit.md` |
| 브랜치 생성·이름 | `docs/conventions/branch.md` |
| PR 생성 | `docs/conventions/pull-request.md` |
| 코드 리뷰 (PR 크기, Pn 룰) | `docs/conventions/review.md` |
| 코드 작성 | `docs/conventions/code-style.md` |
| 패키지 배치 | `docs/conventions/project-structure.md` |

## 핵심 규칙 요약
- 작업 흐름: 이슈 → 브랜치 → PR. PR 본문에 `Closes #{이슈번호}`를 적는다
- 브랜치: `{작업단위}/{이슈번호}-{description}` (예: `feat/12-kakao-login`), 항상 최신 `develop`에서 생성
- 커밋: `{타입}: {제목}`, 허용 타입은 `feat`, `fix`, `refactor`, `chore`, `docs`, `test`, `style`
- PR: base는 `develop`, 본문은 `.github/pull_request_template.md` 형식, 1,000줄 이하
- 커밋 메시지와 PR 본문에 Co-Authored-By나 AI 도구 서명 줄을 넣지 않는다
- 이슈/PR 템플릿: `.github/ISSUE_TEMPLATE/`, `.github/pull_request_template.md`

## 규칙 강제 (Git hook)
- 컨벤션은 Git hook(`.githooks/`)으로 강제한다. clone 후 한 번 `git config core.hooksPath .githooks` 실행
  - `commit-msg`: 커밋 메시지 형식 검사 / `pre-push`: 브랜치 이름 검사, `main`·`develop` 직접 push 차단
- hook에 막히면 `--no-verify`로 우회하지 말고 메시지나 브랜치 이름을 컨벤션에 맞게 고친다

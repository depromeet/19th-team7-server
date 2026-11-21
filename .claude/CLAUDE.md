# team7 API

커밋 메시지와 PR 설명에 Co-Authored-By나 Claude 관련 줄을 넣지 말 것

## 프로젝트 개요
백엔드 API 서버

## 기술 스택
- Java 21
- Spring Boot 4.1.2
- Gradle 9.9.1 (Gradle Wrapper)
- Spring Data JPA
- 테스트: JUnit 5 (JUnit Platform)
- DB: MySQL (개발·운영 환경 통일) // 팀 프로젝트명 정해진 후, 추가

## 빌드 & 실행
```bash
./gradlew build       # 빌드
./gradlew bootRun     # 실행
./gradlew test        # 테스트
./gradlew clean build # 클린 빌드
```

## 설정 파일
- `src/main/resources/application.yml`

## 협업 규칙
- 이슈 → 브랜치 → PR 순서로 작업하고, PR 본문에 `Closes #이슈번호`를 적는다
- 이슈/PR 템플릿: `.github/ISSUE_TEMPLATE/`, `.github/pull_request_template.md`
- 커밋, PR 생성 규칙: `.claude/commands/commit.md`, `.claude/commands/push.md` (`/commit`, `/push`로 실행)
- 컨벤션은 Git hook(`.githooks/`)으로 강제한다. clone 후 한 번 `git config core.hooksPath .githooks` 실행
  - `commit-msg`: 커밋 메시지 형식 검사 / `pre-push`: 브랜치 이름 검사, main·develop 직접 push 차단
  - hook에 막히면 우회하지 말고 메시지나 브랜치 이름을 컨벤션에 맞게 고친다

## 모듈 / 패키지 구조
@project-structure.md

### 브랜치 컨벤션
@branch.md

### 코드 리뷰 룰
@review.md

## 코드 스타일
@code-style.md

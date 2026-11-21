# PR 생성 및 Push

현재 브랜치의 변경사항을 분석하여 PR을 생성하고 push합니다.

## 실행 순서

1. `git branch --show-current`로 현재 브랜치 확인
2. `git log develop..HEAD --oneline`로 커밋 목록 확인
3. `git diff develop..HEAD --stat`로 변경된 파일 확인
4. 커밋 내용을 분석하여 PR 제목과 본문 작성
5. `gh pr create`로 PR 생성

## PR 템플릿

`.github/pull_request_template.md`와 동일한 형식을 사용한다

## 규칙

- PR은 issue 단위로 작성
- PR 제목은 커밋 메시지의 첫 번째 줄을 기반으로 작성
- 작업 내용은 커밋을 분석하여 bullet point로 간결하게 작성
- 리뷰 포인트는 리뷰어가 중점적으로 봐야 할 변경(동작 변화, 정책 변경, 트레이드오프 등)을 작성
- base 브랜치는 develop (main으로 머지될 때마다 운영에 릴리즈, develop은 개발용 브랜치)

## 실행

위 순서대로 PR을 생성하고 결과 URL을 반환해주세요.

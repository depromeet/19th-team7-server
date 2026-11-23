# PR 컨벤션

## 규칙
- PR은 이슈 단위로 작성한다
- base 브랜치는 `develop` (`main`으로 머지될 때마다 운영에 릴리즈, `develop`은 개발용 브랜치)
- PR 제목은 커밋 메시지 형식(`{타입}: {제목}`)을 따른다
- PR 본문은 `.github/pull_request_template.md` 형식을 사용한다
  - 관련 이슈: `Closes #{이슈번호}` (브랜치 이름의 이슈 번호와 같다)
  - 작업 내용: 커밋을 분석해 bullet point로 간결하게 작성
  - 리뷰 요구사항: 리뷰어가 중점적으로 봐야 할 변경(동작 변화, 정책 변경, 트레이드오프 등)
- PR 크기와 리뷰 코멘트 규칙은 `docs/conventions/review.md`를 따른다
- PR 본문에 AI 도구 서명 줄을 넣지 않는다

## 절차
1. `git branch --show-current`로 현재 브랜치 확인
2. `git log develop..HEAD --oneline`로 커밋 목록 확인
3. `git diff develop..HEAD --stat`로 변경된 파일 확인
4. `git push -u origin {브랜치명}`으로 브랜치 push
5. 커밋 내용을 분석하여 PR 제목과 본문 작성
6. `gh pr create --base develop`으로 PR 생성

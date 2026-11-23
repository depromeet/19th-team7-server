# 브랜치 컨벤션

## 브랜치 전략
- `main`: 운영 배포 브랜치. main에 머지될 때마다 운영에 릴리즈된다
- `develop`: 개발 통합 브랜치. 모든 작업 브랜치의 PR base
- 작업 브랜치: 이슈 하나당 하나씩 develop에서 생성한다

## 브랜치 이름 형식
```
{작업단위}/{이슈번호}-{description}
```
- 예: `feat/12-kakao-login`, `fix/23-feed-pagination`, `chore/1-server-setup`

## 규칙
- 작업단위는 커밋 컨벤션(`.claude/commands/commit.md`)의 허용 타입과 같다
  - `feat`, `fix`, `refactor`, `chore`, `docs`, `test`, `style`
- 이슈 제목 머리말에 맞춰 작업단위를 정한다
  - `[FEAT]` → `feat`, `[FIX]` → `fix`, `[CHORE]` → `chore`, `[REFACTOR]` → `refactor` ...
- 이슈 번호는 `#` 없이 숫자만 쓴다 (`#`은 셸에서 주석으로 해석될 수 있음)
- description은 이슈에 작성된 기능을 영어로 간결하게 작성한다
  - 소문자, 단어 사이는 `-` (kebab-case), 2~4단어
- 이슈 하나당 브랜치 하나

## 브랜치 생성
항상 최신 develop에서 만든다.
```bash
git checkout develop
git pull origin develop
git checkout -b {작업단위}/{이슈번호}-{description}
```

## Hotfix
운영 긴급 수정은 main에서 만든다.
- 이름: `hotfix/{이슈번호}-{description}`
- 수정 후 `main`과 `develop` 둘 다에 머지한다

## 머지 후 정리
머지된 브랜치는 로컬과 원격 모두 삭제한다.
```bash
git checkout develop
git pull origin develop
git branch -d {브랜치명}
git push origin --delete {브랜치명}   # GitHub에서 자동 삭제를 켜두었기 때문에 생략한다
```

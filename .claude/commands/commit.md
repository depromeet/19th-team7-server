---
name: commit
description: 커밋 컨벤션에 맞춰 git commit 생성
---

# 커밋 생성

$ARGUMENTS

## 메시지 형식
```
{타입}: {제목}
- 추가 설명 1
- 추가 설명 2
```
- 타입과 콜론 사이 공백 없음, 콜론 뒤 공백 1개
- 제목과 본문 사이 빈 줄 1개
- 본문은 -로 시작하는 bullet point (선택사항)
- `chore:`,`docs:`,`test:`,`style:`타입은 본문 작성하지 않음
- 언어: 한국어 권장, 기술 용어·고유명사는 영어 사용

## 허용 타입
- `feat:` — 새 기능
- `fix:` — 버그 수정
- `refactor:` — 동작 변경 없는 리팩토링
- `chore:` — 빌드, 설정 등 기타
- `docs:` — 문서 변경
- `test:` — 테스트 추가/수정
- `style:` — 코드 포맷, 세미콜론 등 로직 변경 없는 스타일

## 커밋 분리 원칙
- 타입이 다르면 반드시 분리 (예: chore 설정 + feat 기능 → 커밋 2개)
- 같은 타입이라도 논리적으로 독립된 작업이면 분리
- 분리 시 의존 순서대로 커밋 (예: 설정 → 기능 → 테스트)

## 절차
1. `git status`와 `git diff HEAD`로 전체 변경 내역 확인 (staged + unstaged 모두 포함)
2. 커밋 분리 원칙에 따라 변경 내역을 논리적 단위로 분류
3. 각 단위별로 해당 파일만 `git add` → 커밋 메시지 작성 → 커밋
4. 모든 커밋 완료 후 `git log`로 확인

## 커밋 메시지만 변경하는 경우

### 절차

1. `git log --oneline`으로 바꿀 커밋의 해시 확인
2. staged·unstaged 변경이 있으면 `git stash`로 임시 보관 (남아 있으면 rebase가 시작되지 않음)
3. `git rebase -i {커밋해시}~1`로 대화형 rebase 시작 (첫 커밋이면 `git rebase -i --root`)
4. 편집 목록에서 바꿀 커밋 줄의 `pick`을 `reword`로 바꾸고 저장 후 닫기
5. 다시 열린 에디터에서 새 메시지를 메시지 형식에 맞게 작성 후 저장
6. `git log --oneline`으로 확인 (변경한 커밋과 그 뒤 커밋들의 해시는 새로 바뀜)
7. 2단계에서 보관했다면 `git stash pop`으로 복원

### 주의 사항
- 이미 push한 브랜치라면 `git push --force-with-lease`로 강제 push하지 않는다
- 3~5단계는 에디터가 열리는 대화형 작업이므로 사용자가 터미널에서 직접 실행한다
- 중간에 취소하려면 `git rebase --abort`
- 가장 최근 커밋이라면 `git commit --amend --only -m "새 메시지"` 한 줄로 변경 (`--only`가 없으면 staged 파일까지 합쳐짐)

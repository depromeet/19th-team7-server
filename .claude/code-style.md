# 코드 스타일 컨벤션

코드 스타일의 목표는 가독성과 일관성이다. 누가 작성했는지 구분되지 않는 코드를 지향한다.

## 기본 원칙
- 스타일 맞추기는 사람이 아니라 도구에 맡긴다
  - 포매터로 자동 정렬하고, 리뷰에서는 스타일 지적에 시간을 쓰지 않는다
- 기존 코드와 다른 방식을 새로 도입할 때는 PR에서 이유를 설명한다

## 포맷
- 기준 스타일: Google Java Style
- 적용 도구: https://github.com/google/google-java-format

## 네이밍
- 클래스: PascalCase (`UserService`)
- 메서드, 변수: camelCase (`findByEmail`)
- 상수: UPPER_SNAKE_CASE (`MAX_RETRY_COUNT`)
- 패키지: 소문자만 사용 (`com.depromeet.team7.domain.user`)
- 축약어를 피하고 의미가 드러나는 이름을 쓴다

## 패키지 구조
- 도메인 기반 구조를 따른다 → `.claude/project-structure.md`
- 다른 도메인의 내부 구현(repository, entity)에 직접 접근하지 않는다

## 가독성
- 메서드는 한 가지 일만 한다
- 중첩(depth)을 깊게 만들지 않는다. 조기 반환(early return)을 활용한다
- 주석은 "무엇"이 아니라 "왜"를 설명할 때만 쓴다

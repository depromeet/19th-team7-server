# 19th-team7-server

## 시작하기

### 필수
#### 1. Git hook 연결

```bash
git config core.hooksPath .githooks
```

- 커밋 메시지 검사(`commit-msg`)와 브랜치 이름 검사·직접 push 차단(`pre-push`)이 이때부터 동작합니다.
- 저장소마다 한 번만 하면 되고, Windows·Mac 모두 같은 명령입니다.
- Git은 보안상 clone할 때 hook 설정을 자동으로 켜지 않습니다. 그래서 각자 직접 실행해야 합니다.

#### 제대로 연결됐는지 확인
아래처럼 잘못된 커밋을 시도해 `[commit-msg] 커밋 메시지 컨벤션 위반` 메시지가 뜨면 정상입니다. 막히므로 커밋은 만들어지지 않습니다.

```bash
git commit --allow-empty -m "test"
```

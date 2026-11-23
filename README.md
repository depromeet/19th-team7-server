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

### AI 코딩 도구를 사용한다면
#### 2. 팀 규칙 적용 (`AGENTS.md`)

어떤 AI 도구를 쓰든 저장소 루트의 `AGENTS.md`가 공통 진입점입니다. 규칙의 원본은 `docs/conventions/`에 있고, `AGENTS.md`가 이 문서들을 안내합니다.

| 파일 | 내용 |
|---|---|
| `AGENTS.md` | 기술 스택, 빌드 명령, 핵심 규칙 요약, 컨벤션 문서 목록 |
| `docs/conventions/commit.md` | 커밋 컨벤션 |
| `docs/conventions/branch.md` | 브랜치 컨벤션 |
| `docs/conventions/pull-request.md` | PR 컨벤션 |
| `docs/conventions/review.md` | 코드 리뷰 룰 (작은 PR 규칙, Pn 룰) |
| `docs/conventions/code-style.md` | 코드 스타일 컨벤션 |
| `docs/conventions/project-structure.md` | 패키지 구조 |

도구별 적용 방법은 다음과 같습니다.

| 도구 | 적용 방법 |
|---|---|
| Claude Code | 별도 설정 없음. `.claude/CLAUDE.md`가 `AGENTS.md`와 컨벤션 문서를 모두 불러옴 |
| Codex, Cursor | 별도 설정 없음. 루트 `AGENTS.md`를 자동으로 읽음 |
| GitHub Copilot | 에이전트 모드에서 `AGENTS.md`를 읽음. 도구 설정에서 AGENTS.md 사용이 켜져 있는지 확인 |
| Gemini CLI | 설정에서 컨텍스트 파일 이름을 `AGENTS.md`로 지정 |
| 그 밖의 도구 | 작업 시작 시 "`AGENTS.md`를 읽고 따라줘"라고 요청 |

#### Claude Code 전용 기능
- `/commit`: 커밋 컨벤션에 맞춰 커밋 생성 (`.claude/commands/commit.md`)
- `/push`: PR 컨벤션에 맞춰 push 후 PR 생성 (`.claude/commands/push.md`). GitHub CLI를 쓰므로 한 번 로그인이 필요합니다.

```bash
gh auth login
```

- Claude Code에서 `/memory`를 실행해 `AGENTS.md`와 컨벤션 문서가 목록에 보이면 정상입니다.
- 개인 설정은 `.claude/settings.local.json`에 둡니다. 팀 설정이 아니므로 커밋하지 않습니다.

#### 주의
- `AGENTS.md`와 컨벤션 문서는 AI가 따르는 **지침**입니다. 실제로 규칙을 강제하는 것은 Git hook이므로, AI 도구를 쓰더라도 1번 Git hook 연결은 꼭 해 주세요.
- 규칙을 바꿀 때는 `docs/conventions/`의 원본 문서를 고치고, `AGENTS.md`의 핵심 규칙 요약도 함께 맞춰 주세요.

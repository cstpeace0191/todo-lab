# pr1-ci-setup

**적용 단계**: [실습 2] ① Issue #1 브랜치 첫 번째 커밋 (`scripts/lab2_ci_protection.sh`)  
**연관 Issue**: Issue #1 (`issues/1-ci.md`)

---

## 폴더 개요
저장소에 지속적 통합(CI) 파이프라인 및 GitHub 협업 기본 템플릿들을 처음 구축하기 위한 설정 파일 모음입니다.

---

## 포함된 파일 및 역할

| 파일 경로 | 설명 |
| :--- | :--- |
| **`.github/workflows/ci.yml`** | PR 및 main 푸시 시 자동 실행되는 GitHub Actions CI 파이프라인:<br>1. `backend`: Python 3.14 환경에서 ruff 린트 및 pytest(커버리지 80% 이상 필수)<br>2. `client`: Node 22 환경에서 npm ci, eslint, tsc 타입체크, vite build<br>3. `docker`: 위 두 작업 완료 후 멀티스테이지 컨테이너 빌드 및 스모크 테스트 |
| **`.github/ISSUE_TEMPLATE/`** | GitHub Issue 생성 시 구조화된 입력을 유도하는 Issue Form 파일들:<br>- `bug_report.yml`: 버그 제보용 폼<br>- `feature_request.yml`: 기능 요청용 폼<br>- `config.yml`: 템플릿 설정 |
| **`.github/pull_request_template.md`** | PR 작성 시 작업 내용 및 체크리스트를 표준화하는 템플릿 |
| **`.github/CODEOWNERS`** | 코드 소유자를 지정하여 PR 생성 시 자동으로 리뷰어를 요청하고 필수 승인을 요구하도록 설정 |
| **`.github/dependabot.yml`** | pip, npm, docker, github-actions 의존성 패키지의 버전 갱신 PR을 주간 주기로 자동 생성하는 설정 |
| **`.gitattributes`** | 협업자 간 OS 차이로 인한 줄바꿈 문자(LF vs CRLF) 불일치를 방지하기 위한 Git 설정 |
| **`.gitignore`** | `__pycache__`, 가상환경(`.venv`), 빌드 산출물(`backend/src/static` 등)이 Git에 커밋되지 않도록 추적 제외 |
| **`backend/pyproject.toml`** | Python 프로젝트 메타데이터 및 Ruff 린터 설정 (py314, 라인 길이 120, 린트 룰 E, F, B) |
| **`backend/pytest.ini`** | pytest 실행 시 테스트 검색 경로(`testpaths = spec`) 지정 |


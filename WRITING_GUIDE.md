# 블로그 작성 및 발행 가이드

이 블로그는 GitHub의 코드·실험을 바탕으로 활동의 맥락, 고민, 생각의 변화를 이야기하는 곳입니다.

## 1. 사이트 안에서 작성하기

1. https://choijiwng.github.io/admin/ 에 접속하거나 상단의 **✎ 글쓰기**를 클릭합니다.
2. **Sign In with Token**으로 로그인합니다. 현재는 외부 OAuth 서버 없이 GitHub PAT로 로그인합니다.
3. 블로그 글 → 새 글을 선택하고 제목, 요약, 날짜, 분류, 태그, 본문을 작성합니다.
4. 처음에는 비공개 초안(draft: true)으로 저장한 후, 내용을 검토하고 초안을 해제해 발행합니다.
5. 저장하면 GitHub의 src/content/blog/*.md에 커밋되고 main에 반영됩니다. GitHub Actions가 자동으로 빌드·배포합니다.

### GitHub 토큰 발급

GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens**에서 발급합니다.

- Resource owner: **choijiwng**
- Repository access: **Only select repositories → choijiwng.github.io**
- Repository permissions: **Contents = Read and write** (Metadata = Read는 자동 포함)
- Expiration: 가능한 한 짧게 설정하고 필요할 때 새로 발급합니다.

토큰은 절대 소스코드, 블로그 원문 또는 대화에 붙이지 마세요. 내 사이트 관리자 로그인 창에서만 입력하고 공유 PC에서는 사용하지 마세요.
Sveltia CMS는 로그인용 토큰을 해당 브라우저의 **localStorage**에 저장합니다. 공유 PC에서는 로그아웃하고 사이트 데이터를 삭제하며, 유출이 의심되면 GitHub에서 즉시 토큰을 폐기하세요.

관리 페이지는 공개적으로 열릴 수 있지만 GitHub 저장소의 쓰기 권한 없이는 게시할 수 없습니다.
관리 페이지의 noindex 설정은 검색엔진 노출 방지일 뿐 접근 제어가 아닙니다.

### 공개 범위 주의

초안(draft: true)은 웹사이트의 글 목록과 개별 글, RSS에 노출되지 않습니다. 그러나 GitHub 저장소 자체가 Public이라 파일 원문은 공개됩니다. 실제 비밀 정보, 토큰, 개인정보는 올리지 마세요.

본문 이미지 업로드는 public/uploads 아래 저장되고 글에는 /uploads/파일명 경로로 삽입됩니다.
기존 heroImage 필드는 Astro 이미지 빌드용입니다. 관리자에서는 본문에 이미지를 첨부하세요.

## 2. 글 분류

- Project Retrospective: 프로젝트 회고
- Infrastructure: 인프라와 시스템
- Security Research: 보안 연구
- Troubleshooting: 장애 분석 및 문제 해결
- Thoughts: 생각과 평가
- Learning Notes: 학습 노트

## 3. 무엇을 기록할까?

회고·생각: 시작한 이유, 선택의 근거, 예상과 다른 결과, 지금의 평가와 다음 시도.
실습·분석: 환경, 재현 절차, 근거, 결과와 해석, 반례와 한계.

팀의 성과와 개인 기여, 알려진 CVE 재현과 신규 발견을 구별해 표현합니다.

## 4. VS Code 편집도 계속 가능

원문은 src/content/blog/의 Markdown에 남아 있습니다.
로컬에서는 npm ci && npm run build && npm run dev로 확인할 수 있습니다.

관리 화면의 저장은 기본적으로 **main에 직접 커밋**하므로, 공개 여부와 내용을 다시 확인하세요.
초안으로 저장해도 공개 GitHub 저장소에서는 파일을 읽을 수 있다는 점에 유의하세요.
같은 글을 서로 다른 환경에서 동시에 편집하면 충돌할 수 있습니다.

향후 로그인 편의성을 높이려면 GitHub OAuth 애플리케이션과 별도 OAuth 클라이언트(예: Cloudflare Worker)를 연결할 수 있습니다.

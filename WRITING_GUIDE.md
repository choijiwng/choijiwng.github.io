# 블로그 작성 가이드

이 사이트는 **기술 블로그가 중심**입니다. GitHub 저장소에는 코드와 테스트 증거를 두고, 블로그에는 경험의 맥락, 생각, 평가 및 배운 점을 적습니다. 글을 억지로 취업 성과나 연구 성과처럼 포장하지 않습니다.

## 새 글 발행

1. src/content/blog/ 폴더에 영어 파일명으로 Markdown(.md) 파일을 추가합니다.
2. 아래 frontmatter를 작성합니다.
3. 글을 먼저 draft: true로 작성합니다.
4. npm run build 및 npm run dev로 확인합니다.
5. 공개해도 되는지 검토한 후 draft: false로 바꾸고 main에 반영합니다.

예시:

    ---
    title: "한 프로젝트를 끝내고 다시 생각한 것"
    description: "구현 과정과 달라진 판단에 대한 회고"
    pubDate: "2026-11-22"
    category: "Project Retrospective"
    tags: ["회고", "시스템보안"]
    relatedRepo: "https://github.com/choijiwng/pwnable"
    draft: true
    ---

- title / description / pubDate는 필수입니다.
- category의 기본값은 Thoughts입니다. 사용 가능한 권장 분류:
  - Project Retrospective: 프로젝트 회고
  - Infrastructure: 인프라와 시스템
  - Security Research: 보안 연구
  - Troubleshooting: 장애와 문제 해결
  - Thoughts: 생각과 평가
  - Learning Notes: 학습 노트
- tags, relatedRepo는 선택입니다.
- draft: true는 **웹사이트의 목록·개별 글·RSS에서 제외**합니다. 단, GitHub 저장소 자체가 Public이므로 초안 파일을 원격 저장소에 올리면 GitHub에서 읽을 수 있습니다. 비공개 내용이나 토큰은 커밋하지 않습니다.

## 글 유형별 작성 구조

### 회고 · 의견
- 당시 무엇을 하려고 했는가?
- 어떤 선택을 했고 왜 그랬는가?
- 예상과 달랐던 것은 무엇인가?
- 지금은 그 선택을 어떻게 평가하나?
- 다시 한다면 무엇을 바꿀 것인가?

### 실습 · 기술 분석
- 문제와 환경
- 직접 확인한 절차와 증거
- 결과와 해석
- 반례, 한계, 이후 할 일

사실·추론·의견을 혼동하지 않습니다. 팀 기여와 개인 기여를 구분합니다. AI가 만든 코드나 설명은 확인한 범위만 주장합니다.

## 검증 및 배포

    npm ci
    npm run build
    npm run dev

작업 브랜치에서 글을 수정하고 Pull Request로 검토한 다음 main에 병합하면 GitHub Actions가 GitHub Pages에 자동 배포합니다.

About의 학력·프로젝트·수상·교육 이력은 GitHub 프로필 README.md의 공개 기록을 기준으로 작성했습니다. 변경될 때 양쪽을 함께 업데이트해 주세요.

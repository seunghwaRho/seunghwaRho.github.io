# CLAUDE.md - Project Guide

## Overview
Jekyll 기반 GitHub Pages 개인 학술 웹사이트 (seunghwaRho.github.io)
- Remote: https://github.com/seunghwaRho/seunghwaRho.github.io.git
- Branch: master (단일 브랜치)
- Theme: jekyll-theme-minimal
- URL: http://seunghwaRho.github.io

## Project Structure
```
├── _config.yml             # Jekyll 설정 (사이트명, 테마, GA, 플러그인)
├── _layouts/default.html   # 공통 레이아웃 (footer 네비게이션 포함)
├── _includes/analytics.html # Google Analytics (UA-141513535-1)
├── css/main.css            # 전체 스타일 (Palatino 폰트, 70% 너비)
├── index.html              # 메인 페이지 (소개 + 강의 정보)
├── pages/research.html     # 연구 페이지 (working papers + publications)
├── docs/                   # PDF 파일 저장소
│   ├── cv.pdf              # CV (footer에서 링크됨)
│   ├── cv.tex              # CV LaTeX 소스
│   └── *.pdf               # 논문 및 부록 PDF들
└── _site/                  # Jekyll 빌드 결과 (수정 불필요)
```

## Key Pages & What to Edit

### 메인 페이지 (index.html)
- 소개 문구, 소속 정보
- 학기별 강의 목록 (매 학기 업데이트 필요)
- Calendly 상담 예약 링크

### 연구 페이지 (pages/research.html)
- Research Interest
- Working papers 목록
- Publications 목록 (번호, 제목, 공저자, 저널, 연도, PDF 링크)
- 새 논문 추가 시: `<li>` 태그로 기존 형식에 맞춰 추가
- PDF 파일은 docs/ 디렉토리에 저장 후 `/docs/filename.pdf`로 링크

### Footer 네비게이션 (_layouts/default.html)
- HOME, RESEARCH, CV, EMAIL, GitHub 링크
- 이메일: srhoecon@hanyang.ac.kr

## CV 업데이트
1. `docs/cv.pdf` 파일 교체
2. LaTeX 소스: `docs/cv.tex`

## 스타일 규칙
- 폰트: Palatino Linotype / Book Antiqua
- 본문 너비: 70% (body margin: 60px auto)
- div 기본: uppercase (하위 요소에서 text-transform: none으로 해제)
- 헤더 크기: 23px (.headerstyle)

## Path 주의사항
- 프로젝트 경로에 유니코드 apostrophe(U+2019)가 포함되어 있음
- shell에서 직접 cd/ls 불가할 수 있음 → Python subprocess로 cwd 지정하여 실행
- 예시:
  ```python
  import subprocess
  cwd = '/Users/seunghwa/Documents/Documents - Seunghwa\u2019s MacBook Pro/gitpage_new/seunghwaRho.github.io'
  subprocess.run(['git', 'status'], cwd=cwd)
  ```

## Commit Convention
- 기존 커밋 메시지 스타일: 간결한 영문 (예: "update", "cv updated", "index updated")

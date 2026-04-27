# Si-Woo Kim — Personal Research Website

Hugo 기반 개인 연구 웹사이트입니다.

## 🚀 Quick Start

### 1. Hugo 설치
```bash
# macOS
brew install hugo

# Windows (Chocolatey)
choco install hugo-extended

# Linux (Snap)
snap install hugo
```

### 2. 로컬에서 실행
```bash
hugo server -D
# → http://localhost:1313 에서 확인
```

### 3. GitHub Pages 배포
1. GitHub에 `boreng0817.github.io` (또는 원하는 이름) 레포 생성
2. 이 프로젝트를 push
3. Settings → Pages → Source를 **"GitHub Actions"** 로 설정
4. push할 때마다 자동 배포됨 (`.github/workflows/hugo.yml`)

### 4. 커스텀 도메인 연결
1. 도메인 구매 (Cloudflare, Namecheap 등)
2. DNS에 CNAME 레코드 추가: `boreng0817.github.io`
3. `hugo.toml`에서 `baseURL` 변경
4. Settings → Pages → Custom domain에 도메인 입력

---

## 📁 프로젝트 구조

```
site/
├── hugo.toml              ← 사이트 설정 (이름, 링크, 키워드 등)
├── content/
│   └── publications/      ← 논문 마크다운 파일들
│       ├── ifcap.md
│       ├── sail.md
│       └── ...
├── data/
│   ├── news.yaml          ← 뉴스 항목
│   ├── experience.yaml    ← 학력 & 경력
│   ├── awards.yaml        ← 수상 & 장학금
│   └── gallery.yaml       ← 갤러리 사진 목록
├── layouts/
│   ├── index.html         ← 메인 페이지 레이아웃
│   ├── partials/          ← 섹션별 컴포넌트
│   │   ├── icons/         ← SVG 아이콘 (인라인)
│   │   ├── header.html
│   │   ├── publications.html
│   │   └── ...
│   └── _default/
├── static/
│   ├── css/main.css       ← 스타일시트
│   └── images/            ← 프로필 사진, 갤러리 사진
└── .github/workflows/
    └── hugo.yml           ← GitHub Pages 자동 배포
```

---

## ✏️ 콘텐츠 업데이트 가이드

### 논문 추가
`content/publications/` 에 새 `.md` 파일 생성:

```markdown
---
title: "논문 제목"
tag: "C.8"
authors:
  - "Author 1"
  - "Si-Woo Kim"
  - "Author 3"
venue: "CVPR"
venue_class: "cvpr"          # cvpr, emnlp, acmmm, aaai, ieee 중 선택
year: 2027
highlight: true              # first author면 true
highlight_text: "First Author"
note: "워크숍 발표 등 추가 정보"
paper_url: "https://arxiv.org/abs/..."
code_url: "https://github.com/..."
weight: 1                    # 낮을수록 먼저 표시 (같은 연도 내)
---
```

### 뉴스 추가
`data/news.yaml` 맨 위에 추가:

```yaml
- date: "Mar 2027"
  text: "Paper accepted to ICCV 2027!"
  icon: "paper"         # paper, trophy, award, star 중 선택
```

### 사진 추가
1. `static/images/gallery/`에 사진 파일 넣기
2. `data/gallery.yaml`에 항목 추가:
```yaml
- src: "/images/gallery/emnlp2024.jpg"
  alt: "EMNLP 2024 Poster Session"
  caption: "EMNLP 2024"
```

### 프로필 사진 변경
`static/images/avatar.jpg`로 사진을 넣으면 자동으로 이니셜 대신 표시됩니다.

### 새 Venue 색상 추가
`static/css/main.css`에서:
```css
.venue-badge.newvenue { background: #원하는색; }
```

---

## 🎨 커스터마이징

- **색상**: `static/css/main.css`의 `:root` CSS 변수 수정
- **폰트**: `layouts/partials/head.html`에서 Google Fonts 링크 변경
- **섹션 순서**: `layouts/index.html`에서 partial 순서 변경
- **아이콘 추가**: `layouts/partials/icons/`에 새 SVG 파일 추가

---

## 📝 Venue Class 목록

| Venue      | CSS Class | 색상   |
|-----------|-----------|--------|
| CVPR      | `cvpr`    | 네이비  |
| EMNLP     | `emnlp`   | 브라운  |
| ACM MM    | `acmmm`   | 다크그레이 |
| AAAI      | `aaai`    | 딥그린  |
| IEEE Access| `ieee`   | 퍼플   |
# si-woo-kim.github.io

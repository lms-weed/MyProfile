# MyProfile - 개인 포트폴리오 웹사이트

김동욱의 개인 소개와 학습·프로젝트 활동을 기록하기 위해 제작한 정적 웹사이트입니다. Hugo 기반의 Hugoplate 테마를 사용하고, GitHub Pages와 GitHub Actions를 이용해 배포합니다.

- **공개 웹사이트:** https://lms-weed.github.io/MyProfile/
- **GitHub 저장소:** https://github.com/lms-weed/MyProfile
- **사용 테마:** [Hugoplate](https://github.com/zeon-studio/hugoplate)
- **테마 미리보기:** https://zeon.studio/preview?project=hugoplate

## 1. 프로젝트 목적

이 웹사이트는 개인 소개, 관심 분야, 학습 목표, 기술 활용 경험 및 프로젝트 진행 과정을 한곳에 정리하여 공개하는 것을 목적으로 합니다. 콘텐츠는 Markdown으로 작성하고, 수정한 내용은 Git으로 관리합니다.

## 2. 주요 기술

| 기술 | 사용 목적 |
|---|---|
| Hugo Extended 0.165.0 | Markdown 콘텐츠를 정적 웹사이트로 변환 |
| Hugoplate | 웹사이트 기본 레이아웃과 컴포넌트 제공 |
| Tailwind CSS v4 | 화면 스타일 구성 |
| Git / GitHub | 소스 코드 버전 관리 및 원격 저장소 관리 |
| GitHub Actions | main 브랜치 push에 따른 자동 빌드·배포 |
| GitHub Pages | 생성된 정적 웹사이트 공개 |

## 3. 프로젝트 폴더 구조

```text
MyProfile/
├── .github/
│   ├── pages_build.py             # 의존성 준비 및 Hugo 빌드 보조 스크립트
│   └── workflows/
│       └── hugo-pages.yml         # GitHub Actions 자동 배포 설정
├── .github-pages.json             # 저장소 주소, 사이트 주소, 테마 및 빌드 설정
├── site/
│   ├── hugo.toml                  # 사이트 제목, baseURL, 기본 언어 등
│   ├── pages.json                 # 프로젝트 Pages 빌드 설정
│   ├── config/_default/
│   │   ├── languages.toml         # 한국어 언어 및 콘텐츠 폴더 설정
│   │   ├── menus.ko.toml          # 한국어 상단·하단 메뉴
│   │   └── params.toml            # 로고, 검색, SEO, 댓글 등 기능 설정
│   ├── content/korean/
│   │   ├── _index.md              # 홈페이지 배너와 주요 소개 영역
│   │   ├── about/_index.md        # 자기소개 페이지
│   │   ├── blog/_index.md         # 활동 목록 페이지
│   │   ├── blog/post-1.md         # 대표 프로젝트 소개 글
│   │   ├── authors/               # 작성자 정보
│   │   └── sections/              # 홈페이지 하단 섹션 콘텐츠
│   ├── data/social.json           # GitHub 등 소셜 링크
│   ├── i18n/ko.yaml               # 한국어 인터페이스 문구
│   ├── assets/images/             # 로고, 배너 및 콘텐츠 이미지
│   └── themes/template/           # Hugoplate 테마 파일
└── README.md                      # 프로젝트 설명서
```

## 4. 콘텐츠 수정 방법

사이트 콘텐츠는 `site/content/korean/` 아래의 Markdown 파일에서 수정합니다.

| 수정하려는 내용 | 파일 |
|---|---|
| 홈페이지 제목·소개·관심 분야·학습 목표 | `site/content/korean/_index.md` |
| 자기소개 | `site/content/korean/about/_index.md` |
| 활동 목록 제목과 설명 | `site/content/korean/blog/_index.md` |
| 대표 프로젝트의 목적·역할·과정·결과 | `site/content/korean/blog/post-1.md` |
| 작성자 이름과 소개 | `site/content/korean/authors/john-doe.md` |
| 홈페이지 하단 소개 및 GitHub 버튼 | `site/content/korean/sections/call-to-action.md` |

Markdown 문서의 맨 위 YAML front matter는 `---`로 시작하고 끝나야 합니다. 본문은 두 번째 `---` 아래에 작성합니다.

## 5. 사이트 설정 수정 방법

| 설정 | 파일 |
|---|---|
| 사이트 주소·제목·시간대·기본 언어 | `site/hugo.toml` |
| 한국어 콘텐츠 폴더 | `site/config/_default/languages.toml` |
| 메뉴 항목과 연결 주소 | `site/config/_default/menus.ko.toml` |
| SEO·로고·검색·댓글 등의 기능 | `site/config/_default/params.toml` |
| 소셜 링크 | `site/data/social.json` |
| 한국어 버튼·검색 문구 | `site/i18n/ko.yaml` |

현재 사이트의 기본 주소는 `https://lms-weed.github.io/MyProfile/`이며, 기본 언어는 한국어(`ko`)입니다. 프로젝트 저장소 형태로 배포하므로 `baseURL`의 `/MyProfile/` 경로를 임의로 제거하지 않습니다.

## 6. 로컬 빌드 및 확인

### 6-1. 필요한 개발 환경

Git과 함께 다음 도구를 준비합니다. 버전은 현재 `.github/workflows/hugo-pages.yml`에 지정된 배포 환경을 기준으로 합니다.

- Python 3.12
- Node.js 24
- Go 1.27.1
- Hugo Extended 0.165.0
- Dart Sass 1.105.0

Hugo는 반드시 Extended 버전이어야 합니다. 설치 후 PowerShell에서 다음 명령으로 확인할 수 있습니다.

```powershell
git --version
python --version
node --version
go version
hugo version
sass --version
```

### 6-2. 프로젝트 루트로 이동

다음 명령은 `MyProfile` 저장소의 최상위 폴더에서 실행합니다.

```powershell
cd C:\Users\<사용자폴더>\Desktop\MyProfile
```

### 6-3. 빌드 의존성 준비

```powershell
python .github/pages_build.py --dependencies
```

이 스크립트는 `site/`와 테마의 Node 의존성을 준비하고, 빌드에 필요한 도구를 `.pages-tools/`에 설치합니다. Hugo Extended와 Dart Sass 실행 파일은 별도로 설치되어 PATH에서 실행 가능해야 합니다.

### 6-4. Hugo 빌드

```powershell
python .github/pages_build.py --build
```

빌드가 성공하면 저장소 최상위 폴더에 `public/` 출력 폴더가 생성됩니다. 홈페이지 파일은 `public/index.html`입니다.

```powershell
Test-Path .\public\index.html
```

결과가 `True`인지 확인합니다.

### 6-5. 로컬 브라우저에서 확인

로컬 주소로 리소스를 확인하려면 로컬 base URL을 지정한 뒤 빌드합니다.

```powershell
$env:SITE_BASE_URL = "http://localhost:8000/"
python .github/pages_build.py --build
Remove-Item Env:SITE_BASE_URL
python -m http.server 8000 --directory public
```

브라우저에서 `http://localhost:8000/`을 엽니다. 서버를 종료하려면 PowerShell 창에서 `Ctrl + C`를 누릅니다.

> 이 저장소는 `.github/pages_build.py`를 이용해 빌드합니다. 초기 설정을 다시 수행하는 `npm run project-setup`은 이미 준비된 프로젝트에서 다시 실행하지 않습니다.

## 7. Git 사용 및 GitHub에 반영하기

작업 내용은 `main` 브랜치에 커밋하고 원격 저장소에 push합니다.

```powershell
git status
git add <수정한-파일-경로>
git diff --cached --stat
git commit -m "변경 내용을 설명하는 메시지"
git push origin main
```

예를 들어 자기소개 페이지를 수정했다면 다음과 같이 실행합니다.

```powershell
git add site/content/korean/about/_index.md
git commit -m "content: Update personal introduction"
git push origin main
```

커밋 메시지는 실제 변경한 내용을 설명해야 합니다. 빈 커밋이나 내용 없는 변경으로 커밋 수를 늘리지 않습니다.

## 8. GitHub Pages 자동 배포

`.github/workflows/hugo-pages.yml`은 `main` 브랜치에 push가 발생하면 자동으로 실행됩니다.

워크플로의 주요 과정은 다음과 같습니다.

1. 저장소 소스 코드 checkout
2. Python, Node.js, Go 환경 준비
3. Hugo Extended와 Dart Sass 설치
4. `.github/pages_build.py --dependencies` 실행
5. GitHub Pages 설정 확인
6. `.github/pages_build.py --build` 실행
7. `public/` 결과물을 Pages artifact로 업로드
8. GitHub Pages에 배포

GitHub 저장소의 **Settings → Pages → Build and deployment → Source**는 **GitHub Actions**로 설정합니다.

- **Actions 실행 내역:** https://github.com/lms-weed/MyProfile/actions
- **공개 사이트:** https://lms-weed.github.io/MyProfile/

배포에 실패하면 Actions에서 실패한 단계의 로그를 확인하고 원인을 수정한 뒤 다시 `main`에 push합니다.

## 9. 이미지와 저작권

이미지는 `site/assets/images/`에 저장하고, 콘텐츠에서 사용하는 경로와 파일명이 실제 파일명과 일치하는지 확인합니다. 이미지에는 내용을 설명하는 대체 텍스트(alt)를 작성합니다.

이 프로젝트는 Hugoplate를 기반으로 제작되었습니다. 원본 테마와 라이선스 정보는 다음 링크에서 확인할 수 있습니다.

- Hugoplate 원본 저장소: https://github.com/zeon-studio/hugoplate
- Hugoplate 라이선스: `site/themes/template/LICENSE`
- 테마 제작자: Zeon Studio

테마 파일을 배포하거나 수정할 때 원본 라이선스 및 저작권 고지를 유지합니다.

## 10. 참고 링크

- MyProfile 공개 사이트: https://lms-weed.github.io/MyProfile/
- MyProfile GitHub 저장소: https://github.com/lms-weed/MyProfile
- Hugoplate: https://github.com/zeon-studio/hugoplate
- Hugo 공식 문서: https://gohugo.io/documentation/
- GitHub Pages 문서: https://docs.github.com/pages
- GitHub Actions 문서: https://docs.github.com/actions

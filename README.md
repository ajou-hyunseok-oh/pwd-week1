# 실습 1주차: Git/GitHub 설정 및 첫 웹페이지 배포하기

이 가이드는 개발 환경 설정부터 GitHub Pages를 통한 웹페이지 배포까지 모든 과정을 단계별로 안내합니다.

## 📋 목차
1. [필수 프로그램 설치](#1-필수-프로그램-설치)
2. [GitHub 계정 생성](#2-github-계정-생성)
3. [VS Code로 프로젝트 생성](#3-vs-code로-프로젝트-생성)
4. [GitHub 저장소 생성 및 연결](#4-github-저장소-생성-및-연결)
5. [GitHub Pages로 배포](#5-github-pages로-배포)
6. [제출 확인사항](#6-제출-확인사항)

---

## 1. 필수 프로그램 설치

### 1.1 Git 설치
Git은 코드의 버전을 관리하는 프로그램입니다.

**Windows:**
1. https://git-scm.com/download/windows 접속
2. "64-bit Git for Windows Setup" 다운로드
3. 설치 파일 실행 → 모든 옵션은 기본값으로 두고 "Next" 클릭
4. 설치 완료 후 명령 프롬프트(cmd)를 열고 `git --version` 입력하여 확인

**Mac:**
1. Terminal 앱 실행
2. `git --version` 입력
3. Git이 설치되어 있지 않다면 자동으로 설치 안내가 나타남
4. 또는 https://git-scm.com/download/mac 에서 직접 다운로드

### 1.2 GitHub CLI 설치
GitHub CLI는 터미널에서 GitHub를 편리하게 사용할 수 있게 해주는 도구입니다.

**Windows:**
1. https://cli.github.com/ 접속
2. "Download for Windows" 클릭
3. .msi 파일 다운로드 후 실행
4. 설치 완료 후 명령 프롬프트에서 `gh --version` 입력하여 확인

**Mac:**
1. Homebrew가 설치되어 있다면: Terminal에서 `brew install gh` 실행
2. Homebrew가 없다면: https://cli.github.com/ 에서 직접 다운로드

### 1.3 VS Code 설치
VS Code는 코드를 작성하는 편집기입니다.

1. https://code.visualstudio.com/ 접속
2. "Download" 버튼 클릭 (자동으로 운영체제 감지)
3. 다운로드된 파일 실행
4. 설치 과정에서 "Add to PATH" 옵션이 있다면 반드시 체크
5. 설치 완료 후 VS Code 실행하여 정상 작동 확인

---

## 2. GitHub 계정 생성

### 2.1 계정 만들기
1. https://github.com 접속
2. 우측 상단 "Sign up" 클릭
3. 이메일 주소 입력 (학교 이메일 또는 개인 이메일)
4. 비밀번호 설정 (8자 이상, 숫자와 특수문자 포함)
5. Username 설정 (예: yourname123)
   - 이 username은 나중에 웹사이트 주소가 됩니다
   - 예: `https://yourname123.github.io`
6. 이메일 인증 완료

### 2.2 Git 초기 설정
VS Code에서 Terminal을 열고 (상단 메뉴 → Terminal → New Terminal) 다음 명령어 입력:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**주의:** "Your Name"과 "your.email@example.com"을 실제 이름과 이메일로 변경하세요.

### 2.3 GitHub CLI 로그인
Terminal에서 다음 명령어 입력:

```bash
gh auth login
```

다음 옵션들을 선택:
1. GitHub.com 선택
2. HTTPS 선택
3. Y (Git credential 사용)
4. Login with a web browser 선택
5. 나타나는 코드를 복사한 후 Enter
6. 브라우저가 열리면 코드 붙여넣기 후 로그인

---

## 3. VS Code로 프로젝트 생성

### 3.1 프로젝트 폴더 만들기
1. VS Code 실행
2. File → Open Folder 클릭
3. 바탕화면 또는 Documents에 "my-first-website" 폴더 생성
4. 생성한 폴더 선택 후 "Select Folder" 클릭

### 3.2 HTML 파일 작성 (index.html)
1. VS Code 좌측 Explorer에서 "New File" 아이콘 클릭
2. 파일명을 `index.html`로 입력
3. 다음 코드 입력:

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>나의 첫 웹사이트</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>환영합니다!</h1>
        <p>이것은 나의 첫 번째 웹사이트입니다.</p>
    </header>
    
    <main>
        <section>
            <h2>자기소개</h2>
            <p id="intro">안녕하세요. 저는 웹 개발을 공부하고 있습니다.</p>
            <button onclick="changeText()">클릭해보세요</button>
        </section>
    </main>
    
    <footer>
        <p>&copy; 2024 My First Website</p>
    </footer>
    
    <script src="script.js"></script>
</body>
</html>
```

### 3.3 CSS 파일 작성 (style.css)
1. 새 파일 생성: `style.css`
2. 다음 코드 입력:

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    color: #333;
}

header {
    background: #4CAF50;
    color: white;
    text-align: center;
    padding: 2rem;
}

main {
    max-width: 800px;
    margin: 2rem auto;
    padding: 0 1rem;
}

section {
    background: #f4f4f4;
    padding: 2rem;
    border-radius: 8px;
    margin-bottom: 2rem;
}

button {
    background: #4CAF50;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 4px;
    font-size: 16px;
    margin-top: 1rem;
}

button:hover {
    background: #45a049;
}

footer {
    text-align: center;
    padding: 1rem;
    background: #333;
    color: white;
}
```

### 3.4 JavaScript 파일 작성 (script.js)
1. 새 파일 생성: `script.js`
2. 다음 코드 입력:

```javascript
function changeText() {
    const intro = document.getElementById('intro');
    const messages = [
        '웹 개발은 정말 재미있어요!',
        'JavaScript로 상호작용을 만들 수 있습니다.',
        'GitHub Pages로 무료 호스팅이 가능해요!',
        '계속 공부하면 더 멋진 것을 만들 수 있어요!'
    ];
    
    const randomMessage = messages[Math.floor(Math.random() * messages.length)];
    intro.textContent = randomMessage;
}

// 페이지 로드 시 환영 메시지
window.addEventListener('load', () => {
    console.log('웹사이트가 성공적으로 로드되었습니다!');
});
```

### 3.5 파일 저장
모든 파일 저장: `Ctrl+S` (Windows) 또는 `Cmd+S` (Mac)

---

## 4. GitHub 저장소 생성 및 연결

### 4.1 Git 저장소 초기화
VS Code Terminal에서:

```bash
git init
```

### 4.2 GitHub에 저장소 생성
Terminal에서:

```bash
gh repo create my-first-website --public --source=. --remote=origin
```

만약 에러가 발생하면, GitHub 웹사이트에서 직접 생성:
1. https://github.com 로그인
2. 우측 상단 "+" → "New repository"
3. Repository name: `my-first-website`
4. Public 선택
5. "Create repository" 클릭

### 4.3 파일 추가 및 커밋
Terminal에서 순서대로 입력:

```bash
git add .
git commit -m "첫 번째 커밋: 웹사이트 파일 추가"
```

### 4.4 GitHub에 업로드

```bash
git branch -M main
git push -u origin main
```

비밀번호를 요구하면 GitHub 비밀번호를 입력합니다.

---

## 5. GitHub Pages로 배포

### 5.1 GitHub Pages 활성화
1. GitHub에서 방금 만든 저장소 페이지로 이동
2. 상단 메뉴에서 "Settings" 클릭
3. 왼쪽 메뉴에서 "Pages" 클릭
4. Source 섹션에서:
   - Source: "Deploy from a branch" 선택
   - Branch: "main" 선택
   - Folder: "/ (root)" 선택
5. "Save" 클릭

### 5.2 배포 확인
1. 2-3분 정도 기다림
2. Settings → Pages에서 상단에 녹색 체크표시와 함께 URL이 나타남
3. URL 형식: `https://[username].github.io/my-first-website`
4. 링크 클릭하여 웹사이트 확인

---

## 6. 제출 확인사항

과제 제출 전 다음 사항들을 확인하세요:

### ✅ 체크리스트
- [ ] Git, GitHub CLI, VS Code 모두 설치됨
- [ ] GitHub 계정이 생성되고 로그인됨
- [ ] index.html, style.css, script.js 파일이 모두 작성됨
- [ ] GitHub 저장소가 생성되고 파일들이 업로드됨
- [ ] GitHub Pages가 활성화되어 웹사이트가 보임
- [ ] 버튼 클릭 시 텍스트가 변경됨

### 📝 제출 정보
LMS에 다음 정보를 제출하세요:
1. GitHub 저장소 URL (예: `https://github.com/username/my-first-website`)
2. GitHub Pages URL (예: `https://username.github.io/my-first-website`)

### 🔧 문제 해결 팁
- **Git 명령어가 작동하지 않는 경우**: VS Code를 재시작하고 Terminal을 새로 열어보세요
- **GitHub Pages가 보이지 않는 경우**: 5-10분 정도 기다린 후 다시 확인하세요
- **Permission denied 에러**: GitHub CLI로 다시 로그인 (`gh auth login`)
- **파일이 업로드되지 않는 경우**: `git status`로 현재 상태 확인

---

## 🎉 축하합니다!

첫 번째 웹사이트를 성공적으로 배포했습니다! 이제 여러분은:
- Git으로 버전 관리를 할 수 있습니다
- GitHub에 코드를 저장할 수 있습니다
- 웹사이트를 인터넷에 공개할 수 있습니다

다음 주부터는 이 기초 위에 더 복잡하고 흥미로운 기능들을 추가해 나갈 것입니다.

**도움이 필요하면 수업 시간에 질문하거나 LMS 게시판을 활용하세요!**
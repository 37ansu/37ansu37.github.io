# 🔗 GitHub 접속 링크

이 문서는 GitHub에서 프로젝트 파일들에 쉽게 접근할 수 있도록 링크를 정리한 문서입니다.

## 📌 사용 방법

1. 이 프로젝트를 GitHub 저장소에 업로드하세요
2. 아래 링크에서 `YOUR_USERNAME`을 본인의 GitHub 사용자명으로 변경하세요
3. `REPOSITORY_NAME`을 저장소 이름으로 변경하세요

---

## 🌐 웹 페이지 보기

### 메인 페이지
- **Index 페이지**: [https://37ansu.github.io/37ansu37.github.io/index.html](https://37ansu.github.io/37ansu.github.io/index.html)
- **README 페이지**: [https://37ansu.github.io/37ansu37.github.io/README.html](https://37ansu.github.io/37ansu.github.io/README.html)

> **GitHub Pages 활성화 방법:**
> 1. GitHub 저장소 → Settings → Pages
> 2. Source를 "Deploy from a branch" 선택
> 3. Branch를 "main" (또는 "master") 선택
> 4. 폴더를 "/ (root)" 선택
> 5. Save 클릭
> 6. 몇 분 후 `https://YOUR_USERNAME.github.io/REPOSITORY_NAME/` 에서 접속 가능

---

## 📚 Python 학습 샘플 코드

### 1. 변수와 데이터 타입
```
https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/01_variables_and_data_types.py
```
[📄 파일 보기](https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/01_variables_and_data_types.py)

### 2. 리스트와 반복문
```
https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/02_lists_and_loops.py
```
[📄 파일 보기](https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/02_lists_and_loops.py)

### 3. 함수와 모듈
```
https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/03_functions_and_modules.py
```
[📄 파일 보기](https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/03_functions_and_modules.py)

### 4. 딕셔너리와 조건문
```
https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/04_dictionaries_and_conditionals.py
```
[📄 파일 보기](https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/04_dictionaries_and_conditionals.py)

### 5. 파일 처리와 예외 처리
```
https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/05_file_handling_and_exceptions.py
```
[📄 파일 보기](https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/05_file_handling_and_exceptions.py)

---

## 🎓 성적 생성 프로그램

### 중학교 기술교과 성적 생성기
```
https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/middle_school_tech_scores.py
```
[📄 파일 보기](https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/middle_school_tech_scores.py)

---

## 📖 문서 파일

### README (Markdown)
```
https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/README.md
```
[📄 파일 보기](https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/README.md)

### README (HTML)
```
https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/README.html
```
[📄 파일 보기](https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/README.html)

### Index (HTML)
```
https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/index.html
```
[📄 파일 보기](https://github.com/YOUR_USERNAME/REPOSITORY_NAME/blob/main/index.html)

---

## 🚀 GitHub 저장소 업로드 방법

### 방법 1: GitHub 웹사이트 사용

1. [GitHub](https://github.com)에 로그인
2. 우측 상단 "+" 클릭 → "New repository" 선택
3. Repository name 입력 (예: `python-learning-samples`)
4. Public 또는 Private 선택
5. "Create repository" 클릭
6. "uploading an existing file" 클릭
7. 모든 파일을 드래그 앤 드롭
8. "Commit changes" 클릭

### 방법 2: Git 명령어 사용

```bash
# Git 초기화
cd "d:\_0 AHN SU HYUN\1. 대학원(23학번)\2. 정규학기\sample"
git init

# 파일 추가
git add .

# 커밋
git commit -m "Initial commit: Python learning samples"

# GitHub 저장소 연결 (YOUR_USERNAME과 REPOSITORY_NAME 변경 필요)
git remote add origin https://github.com/YOUR_USERNAME/REPOSITORY_NAME.git

# 푸시
git branch -M main
git push -u origin main
```

---

## 📋 .gitignore 파일 추천

다음 내용으로 `.gitignore` 파일을 생성하는 것을 추천합니다:

```gitignore
# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python

# 생성된 데이터 파일
tech_scores.csv
sample_data.txt
students.txt
students.csv
nonexistent_file.txt

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db
```

---

## 🌟 GitHub Pages로 웹사이트 호스팅

GitHub Pages를 활성화하면 `index.html` 파일이 자동으로 웹사이트로 호스팅됩니다!

### 접속 URL
```
https://YOUR_USERNAME.github.io/REPOSITORY_NAME/
```

### 예시
만약 GitHub 사용자명이 `ahnsuhyun`이고 저장소 이름이 `python-samples`라면:
```
https://ahnsuhyun.github.io/python-samples/
```

---

## 📱 공유 링크 예시

### 전체 프로젝트
```
https://github.com/YOUR_USERNAME/REPOSITORY_NAME
```

### 특정 파일 직접 다운로드
```
https://raw.githubusercontent.com/YOUR_USERNAME/REPOSITORY_NAME/main/01_variables_and_data_types.py
```

### 특정 파일 실행 (Google Colab)
```
https://colab.research.google.com/github/YOUR_USERNAME/REPOSITORY_NAME/blob/main/01_variables_and_data_types.py
```

---

## 💡 팁

1. **README.md를 저장소 루트에 두기**: GitHub가 자동으로 표시합니다
2. **GitHub Pages 활성화**: 무료 웹 호스팅 서비스
3. **라이선스 추가**: LICENSE 파일 생성 (MIT, Apache 2.0 등)
4. **Topics 추가**: 저장소 설정에서 관련 토픽 추가 (python, learning, education 등)
5. **README에 배지 추가**: 
   ```markdown
   ![Python](https://img.shields.io/badge/Python-3.6+-blue.svg)
   ![License](https://img.shields.io/badge/License-MIT-green.svg)
   ```

---

## 📧 문의

GitHub 저장소 업로드나 링크 설정에 문제가 있으면 언제든지 문의해주세요!

**작성일**: 2026-01-15


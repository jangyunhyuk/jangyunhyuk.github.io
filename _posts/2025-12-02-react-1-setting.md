---
# ====== 기본 Front Matter ======
title: "React 프로젝트 초기 세팅 (Vite)"
description: "Vite를 사용한 React 프로젝트 초기 세팅 정리"
date: 2025-12-02 14:00:00 +0900
categories: [react, react-basics]   # 최대 2개 권장
tags: [react, component]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

## 프로젝트 세팅

### 1. 터미널에 명령어, 프로젝트명 입력

```bash
npm create vite@latest
```
![react_img_1](/assets/img/react_img/react_img_1.png)

### 2. React 선택
- Vite 템플릿 중 React 선택

![react_img_2](/assets/img/react_img/react_img_2.png)

### 3.  JavaScript 선택
- TypeScript는 이후에 학습할 예정이므로 JavaScript 선택

![react_img_3](/assets/img/react_img/react_img_3.png)

### 4. 추가 옵션 선택
- 실험 기능은 사용하지 않음
- 자동 실행도 하지 않음

안정적인 기본 세팅을 위해 모두 No 선택

![react_img_4](/assets/img/react_img/react_img_4.png)

### 5. 프로젝트 폴더 이동 및 의존성 설치

```bash
npm install
```

![react_img_5](/assets/img/react_img/react_img_5.png)

### 6. 개발 서버 실행

```bash
npm run dev
```

![react_img_6](/assets/img/react_img/react_img_6.png)

### 7. 로컬 서버 확인
- 브라우저에서 안내된 주소로 접속

![react_img_7](/assets/img/react_img/react_img_7.png)

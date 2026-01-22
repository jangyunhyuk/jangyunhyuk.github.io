---
# ====== 기본 Front Matter ======
title: "[PIILOT] 프로젝트 세팅하기"
description: "Next.js, TypeScript, React Query, Zustand, shadcn/ui, Tailwind CSS를 사용한 FSD 구조 프로젝트 초기 세팅"
date: 2026-01-22 10:00:00 +0900
tags: [next.js, typescript, react-query, zustand, shadcn-ui, tailwind-css, fsd]   # 소문자 권장
categories: [piilot, project]   # 최대 2개 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---


## 프로젝트 스택 소개

PIILOT 프로젝트에서 사용하는 기술 스택은 다음과 같다:

- **프레임워크**: Next.js
- **언어**: TypeScript
- **데이터 패칭**: React Query
- **상태 관리**: Zustand
- **UI 라이브러리**: shadcn/ui
- **스타일링**: Tailwind CSS

이 스택들을 FSD(Feature-Sliced Design) 폴더 구조로 구성하여 프로젝트를 시작한다.

## 프로젝트 세팅

### 1단계: Next.js 프로젝트 생성

먼저 Next.js 프로젝트를 생성한다.

```bash
npx create-next-app@latest
```

> **중요**: FSD 폴더 구조를 사용하기 위해 **"Would you Like to use the recommended Next.js defaults?"** 질문에 **No, customize settings**를 선택하고, **src 폴더를 사용하도록 설정**해야 한다.
{: .prompt-warning }

설정 옵션:
- ✅ **TypeScript**: Yes
- ✅ **ESLint**: Yes
- ✅ **Tailwind CSS**: Yes
- ✅ **src/ directory**: Yes (FSD 구조를 위해 필수)
- ✅ **App Router**: Yes

![piilot_img_2](/assets/img/piilot/piilot_img_2.png)


### 2단계: Zustand & React Query 설치

상태 관리와 데이터 패칭을 위한 라이브러리를 설치한다.

```bash
npm install zustand @tanstack/react-query
```

- **Zustand**: 전역 상태 관리 (FSD의 `entities` 레이어에서 사용)
- **React Query**: 서버 상태 관리 및 데이터 패칭 (FSD의 `entities/api` 세그먼트에서 사용)

### 3단계: shadcn/ui 초기화

UI 컴포넌트 라이브러리인 shadcn/ui를 초기화한다.

```bash
npx shadcn@latest init
```

초기화 과정에서 다음과 같이 설정한다:
- **style**: new-york (또는 default)
- **base color**: gray
- **CSS variables**: Yes

#### components.json 파일 수정

초기화 후 생성된 `components.json` 파일을 열어서, FSD 구조에 맞게 **aliases 항목들을 모두 `shared` 경로로 수정**해야 한다.

```json
{
  "$schema": "https://ui.shadcn.com/schema.json",
  "style": "new-york",
  "rsc": true,
  "tsx": true,
  "tailwind": {
    "config": "",
    "css": "src/app/globals.css",
    "baseColor": "gray",
    "cssVariables": true,
    "prefix": ""
  },
  "iconLibrary": "lucide",
  "aliases": {
    "components": "@/shared/ui",
    "utils": "@/shared/lib/utils",
    "ui": "@/shared/ui",
    "lib": "@/shared/lib",
    "hooks": "@/shared/hooks"
  },
  "registries": {}
}
```

> **주의**: shadcn/ui가 기본 경로(`src/lib`)에 설치되어 있을 수 있다. 이 경우 `src/lib/utils.ts` 파일을 `src/shared/lib/utils.ts`로 이동시켜야 한다.
{: .prompt-tip }

#### 설치 테스트

설정이 제대로 되었는지 확인하기 위해 버튼 컴포넌트를 추가해본다.

```bash
npx shadcn@latest add button
```

성공적으로 설치되었다면 `src/shared/ui/button.tsx` 파일이 생성된다.

### 4단계: FSD 폴더 구조 생성

FSD 아키텍처에 필요한 기본 폴더들을 생성한다.

```bash
cd src
mkdir pages widgets features entities
```

생성되는 폴더 구조:
```
src/
├── app/          # App Layer (Next.js에서 자동 생성)
├── pages/        # Pages Layer
├── widgets/       # Widgets Layer
├── features/      # Features Layer
├── entities/      # Entities Layer
└── shared/        # Shared Layer (shadcn/ui 설치 시 자동 생성됨)
```

이제 기본 FSD 폴더 구조가 완성되었다. 각 Layer 내부의 Slice와 Segment는 프로젝트를 진행하면서 필요에 따라 생성하면 된다.

### FSD 구조 확인

생성된 폴더 구조가 FSD 아키텍처에 맞게 구성되었는지 확인

```
src/
├── app/              # ✅ App Layer (Next.js에서 자동 생성)
│   ├── layout.tsx
│   ├── page.tsx
│   └── globals.css
├── pages/            # ✅ Pages Layer (수동 생성)
├── widgets/          # ✅ Widgets Layer (수동 생성)
├── features/         # ✅ Features Layer (수동 생성)
├── entities/         # ✅ Entities Layer (수동 생성)
└── shared/           # ✅ Shared Layer (shadcn/ui 설치 시 자동 생성)
    ├── ui/           # shadcn/ui 컴포넌트
    └── lib/          # 유틸리티 함수
```

각 Layer는 FSD 아키텍처의 규칙에 따라:
- **상위 Layer는 하위 Layer를 참조**할 수 있다
- **하위 Layer는 상위 Layer를 참조**할 수 없다

이제 FSD 구조에 맞춰 프로젝트를 시작할 수 있다!
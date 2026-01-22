---
# ====== 기본 Front Matter ======
title: "[PIILOT] Server 컴포넌트와 Client 컴포넌트 (Next.js)"
description: "Next.js App Router의 Server 컴포넌트와 Client 컴포넌트 개념, 차이점, 사용 시나리오"
date: 2026-01-22 18:00:00 +0900
tags: [next.js, server-components, client-components, app-router]   # 소문자 권장
categories: [piilot, project]   # 최대 2개 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: true  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: true              #  다이어그램
lang: "ko"
---

**참고 자료:**
- [Next.js 공식문서](https://nextjs.org/docs/app/getting-started/server-and-client-components)
- [React Server Components](https://react.dev/reference/rsc/server-components)
- [use client 지시어](https://react.dev/reference/rsc/use-client)
- [use server 지시어](https://react.dev/reference/rsc/use-server)

## Server 컴포넌트와 Client 컴포넌트란?

Next.js App Router에서는 컴포넌트를 **Server Component**와 **Client Component**로 구분한다.

간단히 말하면:
- **Server Component**: 서버에서 렌더링되어 HTML만 전송됨 (기본값)
- **Client Component**: 브라우저에서 JavaScript로 상호작용 가능 (`'use client'` 필요)

## 1. 서버 컴포넌트 (Server Components)

### 정의

서버 컴포넌트는 **서버에서 실행되어 렌더링**되는 컴포넌트다. 브라우저로 JavaScript 코드가 전송되지 않으며, 결과물인 HTML(정확히는 RSC Payload)만 전송된다.

> **중요**: Next.js App Router의 모든 컴포넌트는 **기본적으로 서버 컴포넌트**다. 별도로 선언하지 않아도 자동으로 서버 컴포넌트로 동작한다.
{: .prompt-info }

### 동작 방식

서버 컴포넌트는 다음과 같이 동작한다:

1. **서버에서 렌더링**: 컴포넌트 코드가 서버에서 실행되어 HTML을 생성한다.
2. **HTML만 전송**: 생성된 HTML만 브라우저로 전송된다. JavaScript 코드는 전송되지 않는다.
3. **번들 크기 감소**: 클라이언트 번들에 포함되지 않아 초기 로딩 속도가 빨라진다.

### 렌더링 전략

Next.js는 서버 컴포넌트를 다음과 같은 방식으로 렌더링한다:

1. **정적 렌더링 (Static Rendering)**
   - 빌드 타임에 미리 렌더링되거나, 백그라운드에서 주기적으로 재검증(Revalidation)된다.
   - 기본값이며, 가장 빠른 렌더링 방식이다.

2. **동적 렌더링 (Dynamic Rendering)**
   - 사용자의 요청이 들어올 때마다 서버에서 실시간으로 렌더링된다.
   - 개인화된 콘텐츠나 실시간 데이터가 필요할 때 사용한다.

3. **스트리밍 (Streaming)**
   - 전체 UI가 준비될 때까지 기다리지 않고, 준비된 부분부터 점진적으로 클라이언트에 전송한다.
   - 사용자가 더 빠르게 화면을 볼 수 있게 해준다.

### 서버 컴포넌트의 장점

1. **Zero Bundle Size (번들 크기 제로)**
   - 컴포넌트 로직이 서버에서만 실행되므로, 무거운 라이브러리나 로직이 브라우저 번들에 포함되지 않는다.
   - 초기 로딩 속도가 획기적으로 빨라진다.

2. **백엔드 리소스 직접 접근**
   - API 레이어를 거치지 않고 DB나 파일 시스템에 직접 접근할 수 있다.
   - 불필요한 네트워크 요청을 줄여 효율적이다.

3. **보안성 강화**
   - 민감한 정보(API Key, 액세스 토큰 등)가 서버에만 머무른다.
   - 클라이언트에 노출될 위험이 없다.

4. **자동 코드 분할 (Code Splitting)**
   - 라우트별로 필요한 코드만 자동으로 분할되어 전송된다.
   - 사용자가 실제로 사용하는 코드만 다운로드한다.

### 서버 컴포넌트 예시

```tsx
// src/app/page.tsx (서버 컴포넌트 - 'use client' 없음)
import { fetchData } from '@/shared/api';

// 서버에서 데이터를 가져올 수 있음
export default async function Page() {
  const data = await fetchData();
  
  return (
    <div>
      <h1>{data.title}</h1>
      <p>{data.description}</p>
    </div>
  );
}
```

## 2. 클라이언트 컴포넌트 (Client Components)

### 정의

클라이언트 컴포넌트는 서버에서 **HTML 껍데기를 미리 만든(Pre-rendering)** 후, 브라우저에서 JavaScript가 연결(Hydration)되어 **상호작용이 가능해지는** 컴포넌트다.

> **Hydration이란?**  
> 서버에서 생성된 HTML에 JavaScript를 연결하여, 클릭, 입력 등의 이벤트가 동작하도록 만드는 과정이다.
{: .prompt-tip }

### 사용법

파일 최상단에 `'use client'` 지시어를 선언하면 해당 컴포넌트가 클라이언트 컴포넌트가 된다.

> **주의**: `'use client'`를 선언한 컴포넌트와 그 하위 자식들은 모두 클라이언트 번들에 포함된다. 따라서 필요한 부분만 최소한으로 선언하는 것이 중요하다.
{: .prompt-warning }

```tsx
'use client';

import { useState } from 'react';

// src/features/counter/ui/Counter.tsx
export default function Counter() {
  const [count, setCount] = useState(0);
  
  return (
    <button onClick={() => setCount(count + 1)}>
      클릭 수: {count}
    </button>
  );
}
```

이 컴포넌트는:
- `useState` 훅을 사용하므로 클라이언트 컴포넌트가 필요하다
- `onClick` 이벤트를 사용하므로 상호작용이 필요하다
- 브라우저에서 상태가 변경되어야 한다

### 클라이언트 컴포넌트 배치 전략 (Leaf Pattern)

클라이언트 컴포넌트는 가능한 **트리의 말단(Leaf)**으로 밀어넣어야 한다. 즉, 상호작용이 필요한 부분만 최소한으로 잘라내어 클라이언트 컴포넌트로 만들어야 한다.

#### ❌ 비효율적 패턴

레이아웃 전체나 페이지 전체를 `'use client'`로 감싸버리면, 그 안에 포함된 모든 하위 컴포넌트까지 클라이언트 번들에 포함되어 서버 컴포넌트의 이점을 잃게 된다.

```tsx
// ❌ 나쁜 예: 전체 페이지를 클라이언트 컴포넌트로 만듦
'use client';

export default function Page() {
  // 모든 하위 컴포넌트가 클라이언트 번들에 포함됨
  return (
    <div>
      <Header /> {/* 서버 컴포넌트여도 클라이언트 번들에 포함됨 */}
      <Content /> {/* 서버 컴포넌트여도 클라이언트 번들에 포함됨 */}
      <Footer /> {/* 서버 컴포넌트여도 클라이언트 번들에 포함됨 */}
    </div>
  );
}
```

#### 권장 패턴

정적인 로고, 헤더, 내비게이션 등은 서버 컴포넌트로 유지하고, **검색창, 로그인 버튼, 토글 메뉴** 같이 상호작용이 꼭 필요한 부분만 별도 파일로 분리하여 `'use client'`를 붙인다.

```tsx
// 좋은 예: 필요한 부분만 클라이언트 컴포넌트로 분리
// src/app/page.tsx (서버 컴포넌트)
import Header from '@/widgets/header';
import SearchBar from '@/features/search/ui/SearchBar'; // 클라이언트 컴포넌트
import Content from '@/widgets/content';

export default function Page() {
  return (
    <div>
      <Header /> {/* 서버 컴포넌트 */}
      <SearchBar /> {/* 클라이언트 컴포넌트 - 상호작용 필요 */}
      <Content /> {/* 서버 컴포넌트 */}
    </div>
  );
}
```

## 3. 언제 무엇을 써야 할까?

Next.js는 역할에 따라 다음과 같이 구분하여 사용할 것을 권장한다.

| 작업 내용 | 서버 컴포넌트 | 클라이언트 컴포넌트 |
| :--- | :---: | :---: |
| **데이터 가져오기 (Fetch, DB 접근)** | ✅ | ❌ |
| **민감한 정보 관리 (API Key, 토큰 등)** | ✅ | ❌ |
| **백엔드 리소스 직접 접근 (Filesystem)** | ✅ | ❌ |
| **무거운 의존성 라이브러리 사용** | ✅ | ❌ |
| **상호작용 (onClick, onChange, onSubmit)** | ❌ | ✅ |
| **상태 관리 (useState, useReducer)** | ❌ | ✅ |
| **라이프사이클 (useEffect, useLayoutEffect)** | ❌ | ✅ |
| **브라우저 API (window, localStorage, document)** | ❌ | ✅ |
| **React 커스텀 훅 사용** | ❌ | ✅ |
| **이벤트 리스너 (addEventListener)** | ❌ | ✅ |
| **애니메이션 라이브러리 (framer-motion 등)** | ❌ | ✅ |

### 빠른 판단 기준

다음 중 하나라도 필요하면 **클라이언트 컴포넌트**를 사용해야 한다:
- 사용자 입력 (클릭, 타이핑 등)
- 상태 변경 (useState, useReducer)
- 브라우저 API 사용
- React 훅 사용 (useEffect 등)

그 외에는 **서버 컴포넌트**를 사용하는 것이 좋다.

## 4. 함께 사용하기 (Composition 패턴)

가장 많이 헷갈리고 실수하는 부분이다. **"클라이언트 컴포넌트 파일 안에서 서버 컴포넌트를 직접 `import` 할 수 없다."**

이 규칙을 이해하지 못하면 서버 컴포넌트의 이점을 잃게 되므로 주의해야 한다.

### ❌ 불가능한 패턴

클라이언트 컴포넌트 파일 상단에서 서버 컴포넌트를 `import`하면, 해당 서버 컴포넌트까지 클라이언트 번들(JavaScript)에 포함되어버린다. 이렇게 되면 서버 컴포넌트의 이점(보안, 번들 사이즈 감소)이 사라진다.

```tsx
'use client';

// ❌ Error: 서버 컴포넌트를 클라이언트 컴포넌트에서 직접 import 할 수 없음
import ServerComponent from './ServerComponent';

export default function ClientComponent() {
  return (
    <div>
      <ServerComponent />
    </div>
  );
}
```

### 가능한 패턴 (Composition)

대신, `children`이나 `props`를 통해 서버 컴포넌트를 "슬롯(Slot)"처럼 전달하는 방식은 가능하다. 클라이언트 컴포넌트는 "내 자리에 무언가 들어온다"는 것만 알 뿐, 그게 서버 컴포넌트인지 알 필요가 없기 때문이다.

#### 1. 부모 페이지 (서버 컴포넌트)

서버 컴포넌트에서 조립을 담당한다. 클라이언트 컴포넌트와 서버 컴포넌트를 함께 사용할 수 있다.

```tsx
// src/app/page.tsx (기본적으로 Server Component)
import ClientWrapper from '@/features/interactive/ui/ClientWrapper';
import ServerContent from '@/widgets/content/ui/ServerContent';

export default function Page() {
  return (
    <ClientWrapper>
      {/* 서버 컴포넌트를 children으로 전달 */}
      <ServerContent />
    </ClientWrapper>
  );
}
```

#### 2. 자식 컴포넌트 (클라이언트 컴포넌트)

`children` prop을 통해 서버 컴포넌트를 받는다. 서버 컴포넌트가 렌더링된 결과물(HTML)이 이 자리에 배치된다.

```tsx
'use client';

import { useState } from 'react';

// src/features/interactive/ui/ClientWrapper.tsx
export default function ClientWrapper({ 
  children 
}: { 
  children: React.ReactNode 
}) {
  const [count, setCount] = useState(0);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>
        클릭 수: {count}
      </button>
      
      {/* 서버 컴포넌트가 렌더링된 결과물(HTML)이 이 자리에 배치됨 */}
      <div className="mt-4 border p-4">
        {children}
      </div>
    </div>
  );
}
```

#### 3. 서버 컴포넌트 (내용)

```tsx
// src/widgets/content/ui/ServerContent.tsx (서버 컴포넌트 - 'use client' 없음)
export default function ServerContent() {
  // 서버에서 데이터를 가져올 수 있음
  const data = { title: '서버 컴포넌트', description: '이것은 서버에서 렌더링됨' };
  
  return (
    <div>
      <h2>{data.title}</h2>
      <p>{data.description}</p>
    </div>
  );
}
```

### 핵심 포인트

1. **서버 컴포넌트는 클라이언트 컴포넌트의 children으로 전달 가능**
2. **클라이언트 컴포넌트는 서버 컴포넌트를 직접 import 할 수 없음**
3. **조립은 서버 컴포넌트(부모)에서 담당**

## 5. FSD 구조에서의 활용

FSD 구조에서 Server/Client 컴포넌트를 배치할 때는 다음과 같이 구분한다:

- **Server Component**: `pages`, `widgets`, `entities` 레이어에서 주로 사용
- **Client Component**: `features` 레이어에서 상호작용이 필요한 경우 사용

예시:
```
src/
├── app/                    # Server Component (기본)
├── pages/                  # Server Component (기본)
│   └── home/
│       └── ui/Page.tsx
├── widgets/                # Server Component (기본)
│   └── header/
│       └── ui/Header.tsx
├── features/              # Client Component (상호작용 필요 시)
│   └── search/
│       └── ui/SearchBar.tsx  # 'use client'
└── entities/              # Server Component (기본)
    └── user/
        └── ui/UserCard.tsx
```

이렇게 구성하면 서버 컴포넌트의 이점을 최대한 활용하면서도 필요한 부분만 클라이언트 컴포넌트로 분리할 수 있다.

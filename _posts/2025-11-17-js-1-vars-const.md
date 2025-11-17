---
# ====== 기본 Front Matter ======
title: "변수와 상수"
date: 2025-11-17 21:00:00 +0900
categories: [JavaScript, basics]   # 최대 2개 권장
tags: [javascript, var, const]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: false  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: false              #  다이어그램
lang: "ko"
---

## 변수 let
- 변수는 언제든 값을 바꿀 수 있고, 선언할 때 초기 값을 설정해 주지 않아도 괜찮다.

```javascript
let age;
console.log(age); // undefined

age = 30;
console.log(age); // 30
```

- let이라는 키워드로 만든 변수들은 이름으로 서로 구별이 되기 때문에 중복된 이름으로 다시 선언할 수 없다.

```javascript
// 오류 발생 (블록 범위 변수 'age'를 다시 선언할 수 없습니다.)
let age;
console.log(age);

let age = 30;
console.log(age);
```

## 상수 const
- 상수는 변수와는 달리 한 번 저장된 값은 다시 바꿀 수가 없다.
- 변할 수 없거나 앞으로 변하지 말아야 되는 값들을 저장할 때 사용한다. 

```javascript
// 한 번 선언한 값을 바꾸려고 하면 오류 발생
const birth = "1998.03.18";
birth = "1999.01.27"

// 상수 const를 초기화 없이 선언하면 오류 발생
const birth;
```

## 변수 명명규칙(네이밍 규칙)
1. $, _ 제외한 기호는 사용할 수 없다.
2. 변수의 이름은 숫자로 시작할 수 없다.
3. 예약어를 사용할 수 없다.

```javascript
// 잘못된 예시
let #name;
let name#;

let 1name;

let if;
let let;
```

## 변수 명명 가이드
- 누가 봐도 바로 이해할 수 있는 변수명으로 지어야 한다.

```javascript
let salesCount = 10;
let refundCount = 1;
let totalSalesCount = salesCount - refundCount;
```
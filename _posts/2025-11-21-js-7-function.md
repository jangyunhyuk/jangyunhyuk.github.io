---
# ====== 기본 Front Matter ======
title: "함수"
description: "JavaScript의 함수 개념"
date: 2025-11-21 09:00:00 +0900
categories: [JavaScript, basics]   # 최대 2개 권장
tags: [javascript, function, 함수]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: false  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: false              #  다이어그램
lang: "ko"
---

## 함수
- 특정 작업을 수행하는 코드 묶음
- 필요한 시점에 호출해서 재사용할 수 있다.
- 값(인수)을 전달받아 처리하고, 결과를 반환(return)할 수 있다.


### 함수 호출
```js
function greeting() { // 함수 선언
    console.log("안녕하세요!");
} 

greeting() // 함수 호출
// 출력값
// 안녕하세요!
```

### 인수, 매개변수
인수
: - 함수를 호출할 때 함수에게 전달한 값

매개변수
: - 전달된 인수를 함수 내부에서 받아 저장하는 변수
: - 함수 선언부에 작성하며, 인수를 "받는 자리" 역할을 한다.
: - 매개변수 이름은 함수 내부에서 일반 변수처럼 사용된다.

```js
// 인수, 매개변수 X
function getArea() {
    let width = 10;
    let height = 20;
    let area = width * height;

    console.log(area);
}

getArea();
// 출력값
// 200
```

```js
// 인수, 매개변수 O
function getArea(width, height) { // width, height = 매개변수
    let area = width * height;

    console.log(area);
}

getArea(10, 20); // 10, 20 = 인수
// 출력값 
// 200
```

### 값 반환
- 함수가 어떤 값을 밖으로 되돌려 주는 동작
- return문을 실행하면 함수는 즉시 종료
- return 아래 코드는 실행되지 않는다.

```js
function getArea(width, height) {
    let area = width * height;

    return area; // area는 반환 값
    console.log("hello"); // 실행되지 않음
}

let area1 = getArea(10, 20);
    console.log(area1); // 200
```

### 중첩함수 (함수 안에 또 다른 함수 선언)
- 함수 내부에서 새로운 함수를 정의할 수 있다.
- 내부 함수는 해당 함수의 지역 범위 안에서만 사용 가능

```js
function getArea(width, height) {
    function another(){ // 중첩 함수
        console.log("another");
    }
    another()

    let area = width * height;

    return area;
}

let area1 = getArea(10, 20);
    console.log(area1);

// 출력값
// another
// 200
```

### 호이스팅
- 함수 선언문은 자바스크립트가 실행되기 전에 먼저 메모리에 등록된다. 그래서 함수 선언보다 먼저 호출해도 정상적으로 실행된다.

```js
greeting() // 함수 호출

function greeting() { // 함수 선언
    console.log("안녕하세요!");
} 
// 출력 값
// 안녕하세요!
```
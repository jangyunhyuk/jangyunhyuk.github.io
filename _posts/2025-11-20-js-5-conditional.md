---
# ====== 기본 Front Matter ======
title: "조건문"
description: "JavaScript의 조건문 개념"
date: 2025-11-20 09:00:00 +0900
categories: [JavaScript, basics]   # 최대 2개 권장
tags: [javascript, conditional-statement, 조건문]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: false  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: false              #  다이어그램
lang: "ko"
---

## 조건문
- 특정 조건을 만족했을 때에만 실행되는 코드를 작성하기 위한 문법
- 대표적으로 if, switch 조건문이 존재

### if문
```js
let num = 10;

if (num >= 10) {   
    // 첫 번째 조건 검사
    // 참이면 이 블록만 실행되고 이후 조건은 확인하지 않음
    console.log("num은 10 이상입니다.");  
}
else if (num >= 5) {  
    // 첫 번째 if가 거짓일 때만 실행되는 두 번째 조건
    // 여러 조건을 순차적으로 체크하기 위한 구조
    console.log("num은 5 이상입니다.");
}
else {  
    // 위의 모든 조건이 거짓일 때 실행되는 기본 블록
    console.log("조건이 거짓입니다.");
}
```

### switch 문
- 다수의 조건을 처리할 때 if문보다 더 직관적이다. (if문과 기능 자체는 동일)

```js
let animal = "cat";

switch (animal) {
    case "cat": {
        // animal 값이 "cat"과 일치하면 이 블록 실행
        // 일치 시 해당 코드 실행 후 break로 switch 종료
        console.log("고양이");
        break;
    }
    case "dog": {
        // "dog"과 일치할 경우 실행되는 블록
        console.log("강아지");
        break;
    }
    case "bear": {
        // "bear"과 일치할 경우 실행되는 블록
        console.log("곰");
        break;
    }
    case "snake": {
        // "snake"과 일치할 경우 실행되는 블록
        console.log("뱀");
        break;
    }
    case "tiger": {
        // "tiger"과 일치할 경우 실행되는 블록
        console.log("호랑이");
        break;
    }
    default: {
        // 위의 어떤 case와도 일치하지 않을 때 실행
        // switch문의 기본 처리 구역
        console.log("그런 동물은 전 모릅니다.")
    }
}
```
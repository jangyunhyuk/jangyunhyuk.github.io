---
# ====== 기본 Front Matter ======
title: "단락 평가(Short-circuit)"
description: "JavaScript의 단락 평가(Short-circuit) 개념"
date: 2025-11-24 13:30:00 +0900
categories: [JavaScript, advanced]   # 최대 2개 권장
tags: [javascript, short-circuit]   # 소문자 권장
pin: false                 # 홈 상단 고정
toc: true                  # 우측 TOC 표시
comments: false             # 댓글
render_with_liquid: false  # 코드블록 안의 Liquid 무력화(필요 시 true로)
math: false                 # 수식
mermaid: false              #  다이어그램
lang: "ko"
---

## 단락 평가(Short-circuit Evaluation)
- AND, OR 연산에서 첫 번째 피연산자의 값만으로 결과를 확정할 수 있다면 두 번째 피연산자는 평가하지 않는 실행 방식
- 불필요한 연산을 생략하여 성능을 최적화

### AND(&&) 단락평가
- 왼쪽 피연산자가 falsy면 오른쪽은 평가하지 않음
- 왼쪽이 truthy면 오른쪽 값을 반환

```js
function returnFalse(){
    console.log("False 함수");
    return false;
}

function returnTrue(){
    console.log("True 함수");
    return true;
}

console.log(returnFalse() && returnTrue()); // False 함수
                                            // false
// 왼쪽(returnFalse)이 false이므로 오른쪽은 평가하지 않음

console.log(returnTrue() && returnFalse()); // True 함수
                                            // False 함수
                                            // false

```

### OR(||) 단락 평가
- 왼쪽 피연산자가 truthy면 오른쪽은 평가하지 않음
- 왼쪽이 falsy일 때만 오른쪽 값을 반환

```js
console.log(false || "hello");
// false가 falsy → "hello" 반환

console.log("test" || "hello");
// "test"가 truthy → 오른쪽은 평가하지 않음
```

### 단락 평가 반환값 예시
```js
console.log("A" && "B"); // "B"
console.log(0 && "B");   // 0
console.log("A" || "B"); // "A"
console.log(0 || "B");   // "B"
```

### 단락 평가 활용 사례

```js
function printName(person){
    const name = person && person.name;
    console.log(name || "person의 값이 없음");
}
printName(); // person의 값이 없음
printName({name: "장윤혁"}); // 장윤혁
```
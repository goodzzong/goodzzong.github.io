---
layout: post
title: 콜백함수
name : goodzzong
date: 2018-09-05
comments: true
categories: Javascript

tags: [Javascript]
comments: true
---

## 콜백함수

### 1. 정의
프로그래밍에서 콜백은 다른 코드의 인수로서 넘겨주는 실행 가능한 코드를 말한다.
자바스크립트에서 함수는 일급 객체이다. 일급 객체의 조건은 다음과 같다.
1. 변수나 데이터 구조 안에 담을 수 있다.
2. 파라미터로 전달 할 수 있다.
3. 반환값으로 사용 할 수 있다.
4. 런타임에 생성될 수 있다.


일급객체는 프로퍼티와 메소드를 가지고 함수를 인자로 호출 할 수 있다. 
간단히 일급객체인 함수를 인자로 넘겨 사용 할 수 있다가 콜백 함수라고도 할 수 있다.

```js
 $("#button").click(function(){  
 	alert("Hello World!");
 });
```
jquery 의 간단 예제이다.  click이벤트가 발생 했을때 함수를 인자로 받아 click함수 내부에서 실행 되고 있다.
위의 방법이 전형적인 자바스크립틔 콜백함수라고 할 수 있다.

click 이벤트가 발생 했을때 콜백함수가 인자로 실행 되는것 처럼 콜백함수는 즉시 실행 되는 것이 아니라
우리가 원하는 시점에 실행 시킬수 있다.

출처: http://yubylab.tistory.com/entry/자바스크립트-변수로-자바스크립트-이해하기 [Yuby's Lab.]
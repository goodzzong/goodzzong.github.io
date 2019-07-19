---
layout: post
title: 프로토타입
name : goodzzong
date: 2018-09-05
categories: Javascript

tags: [Javascript]
comments: true
---

## 프로토타입

### 1. 정의 

자바스크리브는 프로토타입 기반 언어이다. 물론 최근에 ES6표준에서는 class문법을 지원하게 되었지만 자바스크립트 자체는 결국 프로토 타입 기반 언이이다.

```js
function Person() {
  this.eyes = 2;
  this.nose = 1;
}
var kim  = new Person();
var park = new Person();
console.log(kim.eyes);  // => 2
console.log(kim.nose);  // => 1
console.log(park.eyes); // => 2
console.log(park.nose); // => 1
```

위의 에제를 보면 각각 kim, part 객체는 eyes와 nose를 가지게 되는데 각각 2개씩 총 4개가 메모리에 할당 되게 된다. 100개를 할당햇다면 총 200개가 메모리에 할당된다. 이런 메모리 문제를 프로토 타입으로 해결 가능하다.

```js
function Person() {}
Person.prototype.eyes = 2;
Person.prototype.nose = 1;
var kim  = new Person();
var park = new Person():
console.log(kim.eyes); // => 2
```

이렇게 쓰면 kim과 part객체는 Person함수의 프로토타입 객체를 참조 하여 같은 곳을 바라 보게 되어 메모리를 할당을 줄일 수 있다.

### 2. Prototype Link와 Prototype Object
자바스크립트에서는 Prototype Link와 Prototype Object 가 존재 한다. 이를 통틀어 프로토타입이라고 부른다.

##### 2-1. Prototype Object

객체는 언제나 함수로 생성된다.

함수를 생성하게 되면 함수는 기본적으로 자기 자신의 속성과 ptorotype속성을 가지게 된다.
이와 함께 함수의 프로토타입 객체를 가지게 되는데

```js
function Person() {}
```
이런식으로 함수를 생성하게 되면 Person 함수와 Person.Prototype Object 가 동시에 생성된다.
각각은 서로를 참조하게 되는데 Person함수의 prototype속성이 Person.Prototype을 가르키고
Person.Prototype의 constructor속성이 Person함수를 가르키게 된다. 
기본적으로 Prototype 객체는 constructor와 \__proto\__ 를 가지게 된다. 참고로 \__proto\__는 
모든 객체가 가지고 있다.

##### 2-2. Prototype Link

위의 예제의 kim과 part은 eyes, nose 속성을 가지고 있지 않는데 사용 가능 하였다. 그 이유는 prototype.object에 그 속송이 존재 하기 때문이다. Pserson함수의 프로토타입의 속성인 eyes와 nose
에 접근 할 수 있는 이유는 무엇일까
그이유는 kim과 park객체를 생성할때 추가된 모든 객체가 가지고 있는 \__proto\__ 때문에 가능하다 
 proto는 생성된 Person함수의 프로토타입 객체를 참조하게 된다. 그래서 person의 프로토타입속성에 접근
 가능 했던것이다. 각각의 proto는 상위의 프로토타입 객체를 참조하게된다. 그래서 만약 상위의 프로토타입
 객체에 해당 속성이 없으면 proto를 통해 계속 상위로 올라가면서 해당 속성을 찾는다. 결국 최상의 객체인
 Object 객체까지 올라간다. 그곳에도 없으면 undefined를 리턴하게된다.
 이것이 프로토타입 체인이다.

 출처: https://medium.com/@bluesh55/javascript-prototype-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-f8e67c286b67
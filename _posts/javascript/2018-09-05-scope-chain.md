---
layout: post
title: 스코프 체인
name : goodzzong
date: 2018-09-05
categories: Javascript

tags: [Javascript]
comments: true
---

## 스코프 체인


### 1. 정의

변수 객체는 해당 함수의 스코프 상에서 존재하고 글로벌 변수객체를 제외 하고는 독립적인 존재이다. 그럼 지역변수가 어떻게 전역변수의 값에 어떻게 접근 하는 것일까 

그건 바로 스코프 체인을 이용하는 것이다. 프로토타입 체인과 유사한 개념이라고 보면된다.
현재의 스코프영역안에 변수를 찾고 없으면 부모의 스코프에서 찾고 없으면 그위의 부모로 계속 접근을 하여 찾는다. 최종적으로 최상위 객체(전연변수객체)까지 가서 찾게 되고 없으면 undefind를 실행한다.

출처: http://yubylab.tistory.com/entry/자바스크립트-변수로-자바스크립트-이해하기 [Yuby's Lab.]
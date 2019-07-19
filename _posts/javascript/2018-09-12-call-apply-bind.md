---
layout: post
title: call, apply, bind
name : goodzzong
date: 2018-09-05
categories: Javascript

tags: [Javascript]
comments: true
---

## call, apply, bind

함수의 메소드에서 중요한 건 **call, apply, bind** 이다.

this 는 기본적으로 window를 가리킨다. 바꿀 수 있는 방법이 몇가지가 있는데 그 중에 하나가 

call, apply, bind 를 이용하는 것이다.

기본적으로 call, apply 는 첫번째 인자로 대체할 this를 담고 두번째인자로 필요한 값을 넣는다.

둘이 차이는 call은 두번째 인자로 값을 구분자로 무한으로 넣는것이고, apply은 배열형태로 두번째 인자를 받는다.

~~~js
var example = function (a, b, c) {
  return a + b + c;
};
example(1, 2, 3);
example.call(example, 1, 2, 3);
example.apply(window, [1, 2, 3]);
~~~

이런식으로 call은 첫번째 인자로 대체할 this를 그뒤로는 구분자로 인자를 받는다

apply는 배열형태로 받는걸 확인 할 수 있다.

bind 는 함수가 가리키는 this만 바꾸고 바로 실해하지 않고 원하는 시점에 호출 할 수 있다.

~~~js
var obj = {
  string: 'zero',
  yell: function() {
    alert(this.string);
  }
};
var obj2 = {
  string: 'what?'
};
var yell2 = obj.yell.bind(obj2);
yell2(); // 'what?'
~~~

obj.yell.binde(obj2) 를 실행하여 obj.yell 함수의 this를 obj2로 바꿨다. 그리고 실행되지 않고

yell2(); 를 호출 할때 실행된다.



이러한 형태의 call, apply, bind 함수는 **유사배열**을 조작할때 쓰인다. 

함수의 실행컨텍스트가 실행될때  arguments가 생기는데 이것은 배열의 형태를 띄고 있지만 배열은 아니다. 그렇기 때문에 배열메소드를 쓸 수 없다. 이때 call, apply, bind를 사용하여 배열의 메소드를 사용 할 수 있다. 

~~~js
function example2() {
  console.log(arguments.join());
}
example2(1, 'string', true);
~~~

위에 처럼 실행하면 에러가 난다. 유사배열이기 때문이다.

하지만 call, apply, bind를 사용하여 원하는대로 사용 할 수 있다.

~~~js
function example3() {
  console.log(Array.prototype.join.call(arguments));
}
example3(1, 'string', true); // '1,string,true'
~~~



출처: [관련링크](https://www.zerocho.com/category/JavaScript/post/57433645a48729787807c3fd)
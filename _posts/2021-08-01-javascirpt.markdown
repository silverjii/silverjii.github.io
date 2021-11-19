---
layout: post
title: "[JavaScript ES5+] 데이터 타입"
image: js-1.png
categories: ['programing', 'JavaScript']
---
* 강의 내용기록
강의 : youtube, 드림코딩 by 엘리 (자바스크립트 3. 데이터타입, data types, le vs var, hoising)


# use strict 
- ECMAScript 5 추가.
- strict 모드 개발 추천.
- strict 모드로 개발 할 때는 상식적인 범위안에서 자바스크립트를 이용할 수 있게 해준다. 
- strict 모드를 이용하면 자바스크립트 엔진이 효율적으로 더 빠르게 자바스크립트를 분석. (성능개선) 

# Variable(변수), rw(read/write)
- 변경될 수 있는 값.

- let
    - ES6에서 추가.
{% highlight javascript %}
let name = 'ellie';
console.log(name); // ellie
name = 'hello';
console.log(name); // hello
{% endhighlight %}

- block scope
{% highlight javascript %}
let globalName = 'global name'; // global scope
{ 
    let name = 'ellie';
    console.log(name); // ellie
    name = 'hello';
    console.log(name); // hello  
    console.log(globalName); // global name
}
console.log(name); // 아무 값도 나오지 않음.
console.log(globalName); // global name
{% endhighlight %}

- global 변수
    - 항상 메모리에 탑재. 최소한 사용이 좋다.
    
- var
    - var은 사용하지 않기.
    - var은 값을 선언하기 전에 쓸 수 있다. = var hoisting
    - var hoisting = 어디에 선언했는지 상관없이, 항상 제일 위로 선언을 끌어 올려주는 걸 말한다.
    - var은 block scope가 없다.

- constant, r(read only)
    - 한번 할당하면 값이 절대 바뀌지 않음.
    - 보안상
    - 자바스크립트에서 변수값이 계속 바뀌어야 할 좋은 이우가 없다면 가능가면 const 사용이 바람직함. 

- Variable types
    - number
    - string 
    - boolean
    - null
    - undefined
    - symbol
    - object

- Dynamic typing : dynamically typed language
{% highlight javascript %}
 let text = 'hello';
 console.log(`value: ${text}, type: ${typeof text}`); // value : hello, type : string
 text = 1;
  console.log(`value: ${text}, type: ${typeof text}`); // value : 1, type : number
  text = '7' + 5;
  console.log(`value : ${text}, type : ${typeof text}`); // value : 75, type : string
  text = '8' / '2';
  console.log(`value : ${text}, type : ${typeof text}`); // value : 4, type : number
{% endhighlight %}
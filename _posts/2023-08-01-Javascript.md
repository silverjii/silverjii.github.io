---
layout: post
title: "[JavaScript]"
date: 2023-08-01
background: '/img/posts/javascript.jpg'
categories : ['javascript']
---

# 📝 JAVASCRIPT
### 1. JAVASCRIPT 태그 선택 
**`(1) document.getElementById('id')`**  : id에 해당하는 태그 하나 <br>
**`(2) document.getElementsByClassName('class')`**  : class에 해당하는 태그 모음 (HTML Collection)<br>
**`(3) document.getElementsByTagName('tag')`** : tag에 해당하는 태그 모음 (HTML Collection) <br>
**`(4) document.querySelector('css')`** : css 선택자에 해당하는 태그 중 가장 첫번째 태그 하나 <br>
**`(5) document.querySelectorAll('css')`** : css 선택자에 해당하는 태그 모음 (NodeList) 


### 2. 요소 노드에 대한 이동 프로퍼티
**`(1) element.children`** : 자식 요소 노드 - element의 자식 요소 모음 (HTMLCollection) <br>
**`(2) element.firstElementChild`** : 자식 요소 노드 - element의 첫 번째 자식 요소 하나<br>
**`(3) element.lastElementChild`** : 자식 요소 노드 - element의 마지막 자식 요소 하나<br>
**`(4) element.parentElement`** : 부모 요소 노드 - element의 부모 요소 하나<br>
**`(5) element.previousElementSibling`** : 형제 요소 노드 - element의 이전 혹은 좌측에 있는 요소 하나<br>
**`(6) element.nextElementSibling`** : 형제 요소 노드 - element의 다음 혹은 우측에 있는 요소 하나

### 3 데이터 타입 종류
 ✔️ Javascript는 다른 언어에 비해 데이터 타입이 유연하다.(상황에 따라 변할 수 있다)<br>
* **`기본형`** : Number, Null, Undefined, String, Boolean, Symbol(유일한 값을 만들 때 : ES2015), BigInt(엄청 큰 숫자를 다룰 때 : ES2020)<br>
* **`참조형`** : Object<br>
  
✔️ Boolean 타입 형 변환<br>
* False로 평가되는 값 (Falsy 값) : false, null, undefined, NaN, 0, ''<br>
* True로 평가되는 값 (Truthy 값) : 나머지 값들 (빈 배열, 빈 객체는 Truthy 값)

### 4. AND와 OR의 연산방식
✔️ **`AND`** : 양쪽 값이 true일 때만 true 리턴
```html
	console.log(true && true); // true
    console.log(true && false); // false
    console.log(false && true); // false
    console.log(false && false); // false
```
✔️ **`OR`** : 양쪽 값이 모두 false 일 때만 false 리턴, 어느 한쪽이 true가 있으면 true 리턴.
```html
	console.log(true || true); // true
    console.log(true || false); // true
    console.log(false || true); // true
    console.log(false || false); // false
```

```html
	console.log(null && undefined); // null
    console.log(0 || true); // true
    console.log('0' && NaN);  // NaN
    console.log({} || 123);  // {}
```
- AND연산자는 왼쪽 값이 true일 때 오른쪽 값을 리턴
- AND연산자는 왼쪽 값이 false일 때 왼쪽 값을 리턴
- OR연산자는 왼쪽 값이 true일 때 왼쪽 값을 리턴
- OR연산자는 왼쪽 값이 false일 때 오른쪽 값을 리턴

### 5. arguments 객체
* arguments객체는 함수를 호출할 때 전달한 아규먼트들을 배열의 형태로 모아둔 유사 배열 객체.
```javascript
function printArguments(){
    for( const arg of arguments ){
        console.log(arg); // Kim Lee Park
    }
}

printArguments('Kim', 'Lee', 'Park');
```

### 6. Rest Parameter
* 피라미터 앞에 마침표 세 개를 붙여주면, 여러 개로 전달되는 아규먼트들을 배열로 다룰 수 있다.
```javascript
function printArguments(...args) {
  for (const arg of args) {
    console.log(arg); 
  }
}

printArguments('Kim', 'Lee', 'Park');
```

* rest parameter는 다른 일반 파라미터들과 함께 사용될 수 있다.<br>
* 일반 파라미터와 함꼐 사용할 떄는 반드시 가장 마지막에 작성해야 한다.
```javascript
function printRanking(first, second, ...others){
    console.log(`우승 : ${first}`);  // 우승 : Kim
    console.log(`준우승 : ${second}`); // 준우승 : Lee

    for(const arg of others) {
        console.log(`참가자 : ${arg}`);  // 참가자 : Park, 참가자 : Shin,  참가자 : Son
    }
}

printRanking('Kim', 'Lee', 'Park', 'Shin', 'Son');
```

### 7. Arrow Function
* 익명 함수를 좀 더 간결하게 표현할 수 있도록 ES2015에서 새롭게 등장한 함수 선언 방식.<br>
* 화살표 함수 정의할 때 활용될 수 있고, 콜백 함수로 전달할 때 활용할 수 도 있다.<br>
* 일반 함수와 달리 arguments 객체가 없고, this가 가리키는 값이 일반 함수와 다르다.
  
```javascript
// 화살표 함수 정의
const getTime = (number) => {
    return number + 2;
};

// 콜백 함수로 활용
txtBtn.addEventListener('click', () => {
    console.log('button is clicked!');
});
```

* 화살표 함수는 다양한 상황에 따라 축약형으로 작성될 수 있다.
```javascript
// 파라미터를 감싸는 소괄호 생략 가능
const getTime = number => {
    return number + 2;
}

// 함수 동작 부분이 return문만 있을 때
const sum = (a,b) => {
    return a + b;
};

// return문과 중괄호 생략 가능
const sum = (a,b) => a + b;

```

### 8. this
* 웹 브라우저에서 this가 사용될 때는 전역 객체, Window 객체를 가지게 된다. <br>
* 객체의 메소드를 정의하기 위한 함수 안에선 메소드를 호출한 객체를 가리키게 된다.

```javascript
const user = {
    firstName : 'Kim',
    lastName : 'ej',
    getFullname : function() {
        return `${this.firstName} ${this.lastName}`;
    },
};

console.log(user.getFullName()); // Kim ej
// getFullName 안에서의 this는 getFullName을 호출한 user객체가 담긴다.
```

### 9. 옵셔널 체이닝 (Optional Chaining)
* 옵널 체닝 연산자(?.) 물음표와 마침표를 붙여 사용한다.
* 옵셔널 체이닝 연산자 왼편의 프로퍼티 값이 undefined 또는 null이 아니라면 그 다음 프로퍼티 값을 리턴하고 그렇지 않은 경우에는 undefined를 반환하는 문법.
```javascript
// 옵셔널 체이닝 연산자
function catName(user){
    console.log(user.cat?.name);
}

// 옵셔널 체이닝 연산자를 삼항연산자로 표현
function catName(user){
    console.log((user.cat === null) || user.cat === undefined) ? undefined : user.cat.name);
}

// ex (null 병합 연산자와 함께 활용)
function catName(user){
    console.log(user.cat?.name ?? '고양이 없음');
}
// null 병합 연산자는 user.cat?.name 값이 null이나 undefined 일 경우에 오른쪽 '고양이 없음' 출력. (?? 앞에 값이 null 혹은 undefined 일 경우 ?? 오른쪽 출력)


const user1 = {
    name : 'Kim',
}

catName(user1); // 고양이 없음
```

### 10. 구조 분해 Destructuring
* 배열과 객체와 같이 내부에 여러 값을 담고 있는 데이터 타입을 다룰 때 Destructuring 문법을 활용하면, 배열의 요소나 객체의 프로퍼티 값들을 개별적인 변수에 따로 할당해서 다룰 수 있음.
```javascript
const members = ['효준', '유나', '민환', undefined, '재하', '지우'];
const [airpod, ipad, macbook, iphone='민식', ...coupon] = members;

console.log(airpod); //효준
console.log(ipad); // 유나
console.log(macbook); // 민환
console.log(coupon); // (2)[재하, 지우]

const iphonePro = {
    title : 'iphone 14 pro',
    price : '1500000',
    storage : '256GB',
    color : 'silver'
};

const {title, price, ...rest} = iponePro;
console.log(title); //iphone 14 pro
console.log(price); //1500000
console.log(rest); {storage:'256GB',color:'silver'}
```


 
### 11. map, forEach, reduce

* `map 메서드` : 배열.map((요소, 인덱스, 배열) => { return 요소});
* `map 메서드` : 반복문을 돌며 배열 안의 요소들을 1대 1로 짝지어 주는 것.
* `forEach 메서드` : 파라미터로 주어진 함수를 배열 요소 각각에 대해 실행하는 메서드.
* `forEach, map` : 반복적인 동작을 할 수 있는 배열만의 메소드
* `forEach와 map의 차이` : forEach는 리턴값이 없고, map은 메소드의 호출결과로 새로운 배열을 리턴.
* 단순하게 배열의 반복작업이 필요하면 `forEach`를 반복작업을 통해 새로운 배열이 필요하면 `map`메소드 사용.
* `forEach`가 배열 요소마다 한 번씩 주어진 함수를 실행하는 것과 달리, `map`은 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환한다.

  <br><br>
* `reduce 메서드` : `배열.reduce( (누적값, 현잿값, 인덱스, 요소) => {return 결과}, 초깃값);`
* `reduce 메서드` : 배열의 각 요소를 순회하며 callback함수의 실행 값을 누적하여 하나의 결과값을 반환.
* `reduce 메서드` :  
```javascript

// 1. for loop

for(let i =0; i < 10; i++){
    console.log(i);
}
// - 가방 빠르고 단순하다. 그래서 효율적이다
// - 모든 자료형에 대해 사용 가능.
// - 중간에 loop 건너뛰기나 종료가 가능. (continue or break)
// - 반복범위 컨트롤이 가능하다.
// - 변수를 활용할 수 있다.

// 2. forEach

arr.forEach(function(v,i,arr){
    console.log(v);
});
// - 빠른편이다
// - Array 객체에서 사용이 가능.
// - 일반 for문보다 가독성이 좋고, 객체형을 다루기 쉽다.
// - for문과 다르게 중간에 끓을 방법이 없다. (return으로 skip가능)
// - return 값을 받지 못함.

// 3. filter

let newArr = arr.filter(function(v,i,arr){
    return condition;
});
// - filter의 가장 큰 특징은 boolean형태의 return값을 갖는다. return값이 true일 경우, 그 요소를 반환하고 false일 경우, 반환하지 않는다.
// - 빠른편이다.
// - Array객체에서 사용이 가능하다.
// - chainable하다.
// - 빈 배열 요소를 반환하지 않는다.
// - 대용량 배열 처리시 메모리 overflow 가능성이 있다.
// - return값은 배열이다.

// 4. map

let newArr = arr.map(function(v, i, arr){
    return condition;
})
// - 빠른편이다.
// - Array객체에서 사용이 가능하다.
// - chainable하다.
// - 대용량 배열 처리시 메모리 overflow 가능성이 있다.
// - return 값 자체를 반환한다.

//5. reduce

let arr = [1,2,3,4,5];
let newArr = arr.reduce(function(acc, v, i, arr){
    return acc + v;
})
// - reduce는 return 값을 누적하는데, 계속해서 전달받아서 사용할 수도 있다.

// 출처 : 개발과디자인사이 <https://daesuni.github.io/Loop-performance/>
```

### 12. filter, find
* `filter, find` : 배열의 요소를 하나씩 살펴보면서 반복적인 동작을 하는 메소드.
* `filter` : 메소드를 호출한 배열을 반복하면서 콜백함수가 리턴하는 조건식이 true되는 요소만 모아서 새로운 배열을 리턴. (항상 리턴값이 배열)
* `find` : 조건에 만족하는 하나의 값만 찾기 때문에 그 값을 찾는 순간 반복이 종료된다. (항상 리턴값이 값)<br>존재하지 않은 값을 찾으면 undefined.
* `filter와 find의 차이` : 같은 배열에서 메소드를 호출하더라도 반복하는 횟수의 차이가 있을 수 있음. 

### 13. some과 every
* `some` : 배열에서 조건에 만족하는 요소가 한개이상 있는지 확인.
* `every` : 모든 요소가 조건을 만족하는지 확인. 




## `출처` : 코드잇 <https://www.codeit.kr/>
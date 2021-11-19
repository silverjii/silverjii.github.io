---
layout: post
title: "[JavaScript ES5+] class vs object"
img: js-1.png
categories: [programing, JavaScript]
---
* 강의 내용기록
강의 : youtube, 드림코딩 by 엘리 (자바스크립트 6. 클래스와 오브젝트의 차이점(class vs object), 객체지향 언어 클래스 정리 | 프론트엔드 개발자 입문편 (JavaScript ES6))


#### - class
- template
- declare once
- no data in

#### - object
- instance of a class
- created many times
- data in

#### - class 선언
{% highlight javascript %}
class Person{
    //constructor
    constructor(name, age){
        //fields
        this.name = name;
        this.age = age;
    }

    // methods
    speak(){
        console.log(`${this.name}: hello!`);
    }
}

const ellie = new Person('ellie', 20);
console.log(ellie.name); // ellie
console.log(ellie.age); // 20

ellie.speak(); // ellie : hello!
{% endhighlight %}

#### - Getter and setters
{% highlight javascript %}
class User{
     constructor(firstName, lastName, age){
         this.firstName = firstName;
         this.lastName = lastName;
         this.age = age;
     }

     get age(){
         return this._age;
     }

     set age(value){
         this._age = value < 0 ? 0 : value;
     }
}

const user1 = new User('Steve', 'Job', -1);
console.log(user1.age); // 0
{% endhighlight %}

#### - Fields(Public, Private)
{% highlight javascript %}
class Experiment{
    publicFied = 2;
    #privateField = 0;    // #privateField : 클래스 내부에서만 값이 보여지고, 접근이 되고, 값이 변경이 가능하지만 클래스 외부에선 값을 읽을 수도 변경할 수 도 없다.
}

const experiment = new Experiment();
console.log(experiment.publicField); // 2
console.log(experiment.privateField); // undefined (최근에 추가 된 거기 때문에 undefined 출력된다.)

{% endhighlight %}

#### - Static
 - object의 상관없이 공통적으로 클래스에서 쓸 수 있는 것이라면 static과 static 메소드를 이용해서 작성하는 것이 메모리의 사용을 줄여 줄 수 있다.
{% highlight javascript %}
class Article{
    static publisher = 'Dream Coding';
    constructor(articleNumber){
        this.articleNumber = articleNumber;
    }

    static printPublisher(){
        console.log(Article.publisher);
    }

    const article1 = new Article(1);
    const article2 = new Article(2);

    console.log(article.publisher); // undefined (static은 오브젝트마다 할당되어 지는 것이 아니라 클래스 자체에 붙어 있다.)

    console.log(Article.publisher); // Dream Coding
    Article.printPublisher(); // Dream coding
}
{% endhighlight %}

#### - 상속 & 다양성
 {% highlight javascript %}
    class Shape{
        constructor(width, height, color){
            this.width = width;
            this.height = height;
            this.color = color;
        }

        draw(){
            console.log(`drawing ${this.color} color!`);
        }

        getArea(){
            return this.width * this.height;
        }
    }

    class Rectangle extends Shape(){}
    class Triangle extends Shape{
        draw(){
            super.draw(); // 부모의 메소드 'drawing red color!'도 출력되면서 '🔺'도 출력 되게 함.
            console.log('🔺')
        }
        // 오버라이딩
         getArea(){
            return (this.width * this.height) / 2;
        }

        toString(){
            return `Triangle : color: ${this.color}`;
        }

    }

    const rectangle = new Rectangle(20, 20, 'blue');
    rectangle.draw(); // drawing blue color!
    console.log(rectangle.getArea()); // 400

    const triangle = new Triangle(20, 20, 'red');
    triangle.draw(); // drawing red color!
    console.log(triangle.getArea()); // 200

 {% endhighlight %}

 #### - InstanceOf
  {% highlight javascript %}
    // 왼쪽에 있는 object가 왼쪽에 있는 클래스 instance인지 아닌지 확인.
    console.log(rectangle instanceof Rectangle);  // true
    console.log(triangle instanceof Rectangle);   // false
    console.log(triangle instanceof Triangle); // true
    console.log(triangle instanceof Shape); // true
    console.log(triangle instanceof Object); // true
    console.log(trinangle.toString()); // Triangle : color : red
   {% endhighlight %}


- 참고 url : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference
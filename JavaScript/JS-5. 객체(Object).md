## **객체의 정의**

자바스크립트의 객체는 **키**(key)과 **값**(value)으로 구성된 **프로퍼티(Property)들의 집합**이다.

프로퍼티 값이 **함수**일 경우, 이를 **메소드**(method)라 부른다.

~~~javascript
const A = {
  key1: "value", // key1 : key, "value" : value
  key2: () => {} // method
};
// --> 프로퍼티들의 집합
~~~

객체를 생성하는 방법은 **객체리터럴**, **Object 생성자함수**가 있다.

~~~javascript
//객체 리터럴
var person1 = {
  name: 'Lee',
  gender: 'male',
  sayHello: () => {
    console.log('Hi! My name is ' + this.name);
  }
};

function Person(name, gender) {
  var ref = 'abc';
  this.name = name;
  this.gender = gender;
  this.sayHello = function(){
    console.log('Hi! My name is ' + this.name);
  };
}

// 인스턴스의 생성
var person2 = new Person('Lee', 'male');
person2.sayHello(); // Hi! My name is Lee
console.log(person2.name); // Lee --> 함수 밖에서 참조가능
console.log(person2.ref); // undefined --> 함수 밖에서 참조불가능
var person3 = new Person('Kim', 'female');
~~~

생성자 함수 내의 **this는** 생성자 함수가 생성할 **인스턴스**(instance)를 가리킨다 .this에 연결(바인딩)되어 있는 프로퍼티와 메소드는 **외부에서 참조 가능**(함수밖에서)하다.생성자 함수 내에서 선언된 일반 변수는 외부에서 **참조 불가능**(함수 밖에서)하다.

## **객체 프로퍼티 접근**

객체의 프로퍼티 값에 접근하는 방법은 **마침표(.) 표기법**과 **대괄호(\[\]) 표기법**이 있다.

**대괄호 내**에 들어가는 프로퍼티 이름은 **반드시 문자열**이어야 한다.

~~~javascript
var person = {
  firstName: "hos",
  lastName: "ryu",
  gender: "male",
  1: 10
};

console.log(person.firstName); // hos
console.log(person["firstName"]); // hos
console.log(person.lastName); // ryu
console.log(person['lastName']); //ryu

console.log(person['1']); // 10
console.log(person[1]);   // 10
~~~

## **객체 프로퍼티 동적생성, 갱신, 삭제**

객체에 새로운 프로퍼티를 동적으로 생성, 갱신, 삭제 할 수 있다.

~~~javascript
var person = {
  firstName: "hos",
  lastName: "ryu",
  gender: "male",
  1: 10
};
// 생성
person['hobby'] = 'soccer';
console.log(person['hobby'] ); // 'soccer'

// 갱신
person[1] = 20;
console.log(person[1]); // 20

// 삭제
delete person.gender;
console.log(person.gender); // undefined

~~~

### **For in문**

객체를 For in문을 통해 나열할 수 있다.

~~~javascript
var person = {
  firstName: "hos",
  lastName: "ryu",
  gender: "male",
  1: 10
};

// prop에 객체의 프로퍼티 이름이 반환된다. 단, 순서는 보장되지 않는다.
for (var key in person) {
  console.log(key + ': ' + person[key]);
}
/*
1: 10
firstName: hos
lastName: ryu
gender: male
*/

~~~

# **객체의 분류**

![img](https://k.kakaocdn.net/dn/rjktu/btqCpRlv4DO/kHYkHbYlIIdigsKEKU9W8k/img.png)

**Built-in Object**(내장 객체)는 웹페이지 등을 표현하기 위한 공통의 기능을 제공한다.

**Standard Built-in Objects (or Global Objects)**

**BOM (Browser Object Model)**

**DOM (Document Object Model)**

**Standard Built-in Objects**(표준 빌트인 객체)를 제외한 BOM과 DOM을 **Native Object**라고 분류하기도 한다.

또한 사용자가 생성한 객체를 **Host Object**(사용자 정의 객체)라 한다.

**Host Object(사용자 정의 객체)**

생성자함수 혹은 객체리터럴을 통해 사용자가 생성한 객체.

> [https://poiemaweb.com/js-object](https://poiemaweb.com/js-object)
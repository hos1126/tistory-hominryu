## 디스트럭처링(Destructuring)은 구조화된 **배열 또는 객체**를 Destructuring(비구조화, 파괴)하여 **개별적인 변수**에 할당하는 것이다.

### **배열 구조분해할당**

~~~javascript
const arr = [1, 2, 3];
const [one, two, three] = arr;
console.log(one, two, three); // 1 2 3
~~~

배열 디스트럭처링을 위해서는 할당 연산자 왼쪽에 **배열 형태의 변수리스트**가 필요하다.

~~~javascript
const arr = [1, 2, 3];
const [one, two, three] = arr;
console.log(one, two, three); // 1 2 3

let x, y, z;

[x, y] = [1, 2];
console.log(x, y); // 1 2

[x, y] = [1];
console.log(x, y); // 1 undefined

[x, y] = [1, 2, 3];
console.log(x, y); // 1 2

[x, , z] = [1, 2, 3];
console.log(x, z); // 1 3

[x, y, z = 3] = [1, 2];
console.log(x, y, z); // 1 2 3

[x, y = 10, z = 3] = [1, 2];
console.log(x, y, z); // 1 2 3

// spread 문법
[x, ...y] = [1, 2, 3];
console.log(x, y); // 1 [ 2, 3 ]
~~~

### **객체 구조분해할당**

할당?기준은?**프로퍼티?이름**(키)이다. 순서는 의미가 없다.

~~~javascript
var obj = {
    firstName: 'Ungmo',
    lastName: 'Lee'
};
var {firstName, lastName} = obj;
console.log(firstName, lastName);

//변수명을 수정할 수 있음
const { prop1: p1, prop2: p2 } = { prop1: 'a', prop2: 'b' };
console.log(p1, p2); // 'a' 'b'
console.log({ prop1: p1, prop2: p2 }); // { prop1: 'a', prop2: 'b' }
~~~

객체에서 **프로퍼티 이름(키)**으로 **필요한 프로퍼티 값만**을 추출할 수 있다.

다음과 같이 **콜백함수의 인자**로 사용할 경우 자주 활용된다.

~~~javascript
const todos = [
    { id: 1, content: 'HTML', completed: true },
    { id: 2, content: 'CSS', completed: false },
    { id: 3, content: 'JS', completed: false }
];

const completedTodos1 = todos.filter(todo => todo.completed);
// todo => ({completed})
// const {complete} = todo;
// todo는 todos의 요소인 객체
const completedTodos2 = todos.filter(({ completed }) => completed);
console.log(completedTodos1); // [ { id: 1, content: 'HTML', completed: true } ]
console.log(completedTodos2); // [ { id: 1, content: 'HTML', completed: true } ]
~~~

중첩된 객체를 구조분해할당 할 경우

~~~javascript
const person = {
  name: 'Kim',
  address: {
    zipCode: '12345',
    city: 'Busan'
  }
};

const { address: { city } } = person;
console.log(city); // Busan
~~~

> [https://poiemaweb.com/es6-destructuring](https://poiemaweb.com/es6-destructuring)
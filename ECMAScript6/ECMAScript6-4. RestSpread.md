## **Rest 파라미터**

Rest 파라미터는 함수에 전달된 **인수들의 목록**을 **배열**로 전달받는다.

~~~javascript
function foo(...rest) {
    console.log(Array.isArray(rest)); // true
    console.log(rest); // [ 1, 2, 3, 4, 5 ]
  }
  
  foo(1, 2, 3, 4, 5);
  
  function foo(param, ...rest) {
    console.log(param); // 1
    console.log(rest);  // [ 2, 3, 4, 5 ]
  }
  
  foo(1, 2, 3, 4, 5);
~~~

## **Spread**

Spread는 대상을 개별 요소로 분리한다. Spread의 대상은 **이터러블**이어야 한다.

~~~javascript
console.log(...[1, 2, 3]) // 1, 2, 3
console.log(...'Hello');  // H e l l o

// Map과 Set은 이터러블이다.
console.log(...new Map([['a', '1'], ['b', '2']]));  // [ 'a', '1' ] [ 'b', '2' ]
console.log(...new Set([1, 2, 3]));  // 1 2 3

// 이터러블이 아닌 일반 객체는 Spread 문법의 대상이 될 수 없다.
console.log(...{ a: 1, b: 2 });

~~~

함수의 인수로 사용하는 경우

~~~javascript
// ES6
function foo(x, y, z) {
  console.log(x); // 1
  console.log(y); // 2
  console.log(z); // 3
}
// 배열을 foo 함수의 인자로 전달하려고 한다.
const arr = [1, 2, 3];

foo(...arr);
~~~

~~~javascript
// ES6
function foo(v, w, x, y, z) {
  console.log(v); // 1
  console.log(w); // 2
  console.log(x); // 3
  console.log(y); // 4
  console.log(z); // 5
}

// ...[2, 3]는 [2, 3]을 개별 요소로 분리한다(→ 2, 3)
// spread 문법에 의해 분리된 배열의 요소는 개별적인 인자로서 각각의 매개변수에 전달된다.
foo(1, ...[2, 3], 4, ...[5]);
~~~

## **Rest/Spread 프로퍼티**

Spread 문법을 사용하면 보다 간편하게 배열이나 객체를 **복사**할 수 있다.

이때는 **얕은 복사**(shallow copy)하여 새로운 복사본을 생성한다. 

~~~javascript
// ES6
const arr = [1, 2, 3];
// --> Shallow Copy(얕은복사) 자주 사용한다.
const copy = [...arr];

console.log(copy); // [ 1, 2, 3 ]

// 객체의 Spread 프로퍼티
const n = { x: 1, y: 2, ...{ a: 3, b: 4 } };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }

// Spread를 활용한 객체의 Shallow Copy 및 프로퍼티 값 변경
const nCopy = { ...n, a: 4 };
console.log(nCopy); // { x: 1, y: 2, a: 4, b: 4 }

// 객체의 Rest 프로퍼티
const { x, y, ...z } = n;
console.log(x, y, z); // 1 2 { a: 3, b: 4 }
~~~

> [https://poiemaweb.com/es6-extended-parameter-handling](https://poiemaweb.com/es6-extended-parameter-handling)
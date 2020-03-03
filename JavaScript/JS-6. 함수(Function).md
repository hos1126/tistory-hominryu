자바스크립트에서 **함수를 정의하는 방법**은 크게 **3가지(함수선언문, 함수 표현식, 생성자함수)**로 나눌 수 있다.

### **함수 선언문**

~~~javascript
function makeFunc(num) {
  return num * num;
}
~~~

### **함수 표현식**

함수 리터럴 방식으로 **함수를 정의**하고 **변수에 할당**할 수 있는데 이러한 방식을 **함수 표현식**이라 한다.

함수 선언문으로 정의한 함수 makeFunc()를 함수 표현식으로 정의하면 아래와 같다.

~~~javascript
var makeFunc = function(num) {
  return num * num;
};
~~~

---

## **일급 객체**

자바스크립트의 함수는 **일급 객체**이므로 아래와 같은 특징이 있다.

**\- 무명의 리터럴**로 표현이 가능하다.

**\- 변수**나 **자료 구조**(객체, 배열…)에 **저장**할 수 있다.

**\- 함수의 파라미터**로 전달할 수 있다.

**\- 반환값**(return value)으로 사용할 수 있다.

~~~javascript
//무명의 리터럴로 표현이 가능하다.
var makeFunc = function(num) {
  return num * num;
};

//변수나 자료 구조(객체, 배열…)에 저장할 수 있다.
var a = {
  name: "makefunc",
  makeFunc
};
function b(callback) {
  return callback(3);
}
function c() {
  return makeFunc;
}
console.log(a.makeFunc(3)); // 9
//함수의 파라미터로 전달할 수 있다.
console.log(b(makeFunc), "매개변수 사용"); // 9 매개변수 사용
//반환값(return value)으로 사용할 수 있다.
console.log(c()(3), "return 사용"); // 9 return 사용
~~~

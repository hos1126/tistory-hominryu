## 자바스크립트의 데이터 타입은 7개이며, **원시 타입(primitive data type)**과 **객체 타입(object/reference type)**으로 구분할 수 있다.

### **원시 타입(변경이 불가능 한 값이며, 값에 의한 전달)**

-   **number**
    
-   **null**
    
-   **undefined**
    
-   **boolean**
    
-   **string**
    
-   **symbol(ES6)**
    

### **객체타입(참조에 의한 전달)**

-   **object**
    

---

## **원시타입 알아야 할 것**

### **number**

number 타입은 정수, 실수, 음수, 2진수, 8진수, 16진수, NaN 등이 있다.

~~~javascript
console.log('정수', typeof 10); //number
console.log('실수',typeof 10.12); //number
console.log('음수',typeof -20); //number
console.log('2진수',typeof 0b01000001); //number
console.log('8진수',typeof 0o101); //number
console.log('16진수',typeof 0x41); //number
console.log('NaN',typeof 1 * 'string'); //NaN

~~~

### **null**

자바스크립트는 대소문자를 구별하므로 **null**은 **NULL, Null**과 다르다.

~~~javascript
console.log(null) // Object

var a = null;
console.log(typeof a === null); // false
console.log(a === null);        // true
~~~

이는 자바스크립트 설계오류이며, null 타입 확인 시 **일치연산자(===)**를 사용해야한다.

### **undefined**

선언 이후 값을 **할당하지 않은 변수**는 **undefined**값을 가진다.

~~~javascript
console.log(a); //undefined
var a;
//변수의 호이스팅
~~~

### **String**

자바스크립트의 문자열은 원시 타입이며 **변경 불가능(immutable)**하다.

~~~javascript
var str = 'abc';
str = 'def';
~~~

변수 str에 'abc'가 할당되면, str은 메모리에 생성된 문자열 ‘abc’의 주소를 가리킨다.

str = 'def'가 실행되면, str은 기존 'abc'를 수정하는 것이 아니라 새로운 문자열 ‘def’를 메모리에 생성하고 **str은 이 주소**를 가리킨다. 즉 str이 가리키는 **주소만 변경**되고, 'abc', 'def'는 메모리에 **그대로 존재**한다.

### **Boolean**

true와 false로 구분되며, 비어있는 문자열과 null,?undefined, 숫자 0은 **false**로 간주된다. (타입변환)

### **Symbol**

심볼(symbol)은 ES6에서 새롭게 추가된 7번째 타입으로 변경 불가능한 원시 타입의 값이다.

### **객체 타입(참조에 의한 전달)**

원시 타입(Primitives)을 제외한 나머지 값들(배열, 함수, 정규표현식 등)은 모두 객체이다. 또한 객체는**pass-by-reference(참조에 의한 전달)**방식으로 전달된다.

> [https://poiemaweb.com/js-data-type-variable](https://poiemaweb.com/js-data-type-variable)
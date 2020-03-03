## **단락평가(short-circuit evaluation)**

~~~javascript
console.log('ABC' && 'DEF') // DEF
console.log('ABC' || 'DEF') // ABC
console.log(false && 'DEF') // false
console.log(false || 'DEF') // DEF
~~~

**'ABC' && 'DEF'**

'ABC' 가 TRUE일 경우, **'DEF'가 TRUE인지 확인해야** 전체가 TRUE인지 확인 가능하므로, 전체를 판단하는 것은 'DEF'이다.

**'ABC || 'DEF'**

'ABC' 가 TRUE일 경우, **'DEF'가 TRUE인지 확인하지 않아도** 전체가 TRUE인지 확인 가능하므로, 전체를 판단하는 것은 'ABC'이다.

**false && 'DEF'**

첫번째항이 false일 경우, **'DEF'가 TRUE인지 확인하지 않아도** 전체가 TRUE인지 확인 가능하므로,?전체를 판단하는 것은 false이다.

**false || 'DEF'**

첫번째항이 false일 경우, **'DEF'가 TRUE인지 확인해야** 전체가 TRUE인지 확인 가능하므로,?전체를 판단하는 것은 'DEF'이다.

**undefined, null, 0, -0, NaN, (빈문자열)**은 제어문의 조건식에서 **false**로 평가되는 값들이다.

~~~javascript
function evalString(str) {
  // str이 false인 경우 result=false
  // str이 true인 경우 result = str+'빈문자가 아님'
  let result = str && str + "(빈문자가 아님)";

  if (!result) {
    console.log("falsy값들");
  } else {
    console.log(result);
  }
}
evalString("abc"); // abc
evalString(undefined); // falsy값들
evalString(null); // falsy값들
evalString(0); // falsy값들
evalString(-0); // falsy값들
evalString(NaN); // falsy값들
evalString(""); // falsy값들

~~~

> [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/)
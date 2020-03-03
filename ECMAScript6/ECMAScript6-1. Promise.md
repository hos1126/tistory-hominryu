## **1\. Promise를 왜 사용하는가?**

자바스크립트는 비동기 처리를 위한 하나의 패턴으로 콜백 함수를 사용한다.

모든 호출스택이 소멸된 후, **이벤트 루프에서 비동기 함수를 실행**하기 때문에,

비동기 함수의 처리 결과에 대한 처리는 **비동기 함수의 콜백 함수 내**에서 처리해야 한다.

이러한 이유 때문에 콜백안에 콜백을 사용할 수 밖에 없다.

**콜백헬(call back hell)**이 발생하는 것이다.

~~~javascript
let resultA, resultB, resultC;

function add(num1, num2, callback) {
    callback(num1 + num2)
}

//call back Hell
add(1, 2, function A(sum) {
    //비동기함수 시작
    setTimeout(function () {
        resultA = sum;
        console.log(resultA); // 3

        add(resultA, 3, function B(sum) {
            resultB = sum;
            console.log(resultB); // 6

            add(resultB, 4, function C(sum) {
                resultC = sum;
                console.log(resultC); // 10
            });
        });
    }, 0)
    console.log(resultA, resultB, resultC); // undefined undefined undefined
    //전역 컨텍스트에서 undefined로 할당되었고, 비동기 함수보다 먼저실행
});

~~~

---

## **2\. Promise 사용**

Promise 생성자 함수는 비동기 작업을 수행할 콜백 함수를 인자로 전달받는데 이 콜백 함수는 resolve와 reject 함수를 인자로 전달받는다.

Promise 사용 순서

1.  Promise 객체 생성
2.  Promise 실행 후, then()으로 수행처리
3.  catch()로 에러처리

### **Promise 체이닝**

**then()에서 받을 result값을 resolve의 인자**로 넣는다.

then()에서 **Promise를 반환**하면 이를 **다시 then()으로 연결**할 수 있다.(Call back Hell 해결)

### **Promise는 비동기**

아래 console.log 결과가 undefined라고 출력되는 것은 Promise가 비동기이기 때문이다.

~~~javascript
//Promise로 변환

let pmResultA, pmResultB, pmResultC;

const addPm = (num1, num2) => (
    new Promise((resolve, reject) => {
        resolve(num1 + num2);
    })
);

/* resolve로 바로 return 할 경우
const addPm = (num1, num2) => Promise.resolve(num1 + num2);
*/

addPm(1, 2).
    then(result => {
        pmResultA = result;
        console.log(pmResultA);
        return addPm(pmResultA, 3); //3
    })
    .then(result => {
        pmResultB = result;
        console.log(pmResultB);
        return addPm(pmResultB, 4); //6
    })
    .then((result, error) => {
        pmResultC = result;
        console.log(pmResultC); //10
        if (error) {
            console.log(error);
        }
    }).catch(function (error) {
        console.log(error.message);
    });


console.log(pmResultA, pmResultB, pmResultC); //undefined undefined undefined
~~~

> [https://github.com/n00nietzsche/33jsconcept-KoreanTranslation/blob/master/25.promise/promise-for-dummy.md](https://github.com/n00nietzsche/33jsconcept-KoreanTranslation/blob/master/25.promise/promise-for-dummy.md)
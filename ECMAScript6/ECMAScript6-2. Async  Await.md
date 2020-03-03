## **Async / Await는 Promise를 더 간결하고 편리하게 사용하기 위한 문법.**

### **Async**

async 키워드는 어떠한 함수가 **Promise를 리턴**할 수 있도록 만들어 준다.

~~~javascript
const asyncFunc = async () => {
    return 'aaa';
}
asyncFunc()
.then(result => console.log(result)); // aaa
//Promise를 리턴하므로 then연결 가능
~~~

### **Await**

await문은 **async**함수의 실행을 중단시키고, Promise가 **fulfill**되거나 **reject**되기를 기다리고, 다시 async함수를 실행시킵니다. 이때 await문의 값은 **Promise** **에서 fulfill(resolve)된 값**이 된다.

await은 **async함수 내부에서만** 동작한다.

~~~javascript
const asyncFunc = async () => {
    let a = await new Promise(
        (resolve, reject) => setTimeout(()=>resolve('bbb'), 3000));
    console.log(a);
}
asyncFunc();
~~~

### **Promise에서 Async/Await으로 변경**

then() 함수의 **리턴값**을 **await 키워드 다음**에 작성한 후 연결한다.

~~~javascript
let pmResultA, pmResultB, pmResultC;

const addPm = (num1, num2) => (
    new Promise((resolve, reject) => {
        resolve(num1 + num2);
    })
);

addPm(1, 2).then(result => {
    pmResultA = result;
    console.log(pmResultA); // 3
    return addPm(pmResultA, 3);
}).then(result => {
    pmResultB = result;
    console.log(pmResultB); //6
    return addPm(pmResultB, 4); 
}).then((result, error) => {
    pmResultC = result;
    console.log(pmResultC); //10
    if (error) {
        console.log(error);
    }
}).catch(function (error) {
    console.log(error.message);
});
//Promise로 변환
~~~

~~~javascript
let asyncResultA, asyncResultB, asyncResultC;

async function asyncAdd() {
    try {
        const addAsync = (num1, num2) => (
            new Promise((resolve, reject) => {
                resolve(num1 + num2);
            }));
        asyncResultA = await addAsync(1, 2); //resolve되길 기다림
        asyncResultB = await addAsync(asyncResultA, 3);  //resolve되길 기다림
        asyncResultC = await addAsync(asyncResultB, 4);  //resolve되길 기다림

        console.log(asyncResultA); // 3
        console.log(asyncResultB); // 6
        console.log(asyncResultC); // 10
    } catch (error) {
        console.error();
    }
    return 'resolvePromise'; // Promise.resolve('resolvePromise');
}
// asyncAdd는 Promise를 반환함
asyncAdd().then(result => {
    console.log(result);
});
~~~

> [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/await](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/await)

> [https://github.com/n00nietzsche/33jsconcept-KoreanTranslation/blob/master/26.async-await/async-await.md](https://github.com/n00nietzsche/33jsconcept-KoreanTranslation/blob/master/26.async-await/async-await.md)
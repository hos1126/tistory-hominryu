## **Async / Await�� Promise�� �� �����ϰ� ���ϰ� ����ϱ� ���� ����.**

### **Async**

async Ű����� ��� �Լ��� **Promise�� ����**�� �� �ֵ��� ����� �ش�.

~~~javascript
const asyncFunc = async () => {
    return 'aaa';
}
asyncFunc()
.then(result => console.log(result)); // aaa
//Promise�� �����ϹǷ� then���� ����
~~~

### **Await**

await���� **async**�Լ��� ������ �ߴܽ�Ű��, Promise�� **fulfill**�ǰų� **reject**�Ǳ⸦ ��ٸ���, �ٽ� async�Լ��� �����ŵ�ϴ�. �̶� await���� ���� **Promise** **���� fulfill(resolve)�� ��**�� �ȴ�.

await�� **async�Լ� ���ο�����** �����Ѵ�.

~~~javascript
const asyncFunc = async () => {
    let a = await new Promise(
        (resolve, reject) => setTimeout(()=>resolve('bbb'), 3000));
    console.log(a);
}
asyncFunc();
~~~

### **Promise���� Async/Await���� ����**

then() �Լ��� **���ϰ�**�� **await Ű���� ����**�� �ۼ��� �� �����Ѵ�.

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
//Promise�� ��ȯ
~~~

~~~javascript
let asyncResultA, asyncResultB, asyncResultC;

async function asyncAdd() {
    try {
        const addAsync = (num1, num2) => (
            new Promise((resolve, reject) => {
                resolve(num1 + num2);
            }));
        asyncResultA = await addAsync(1, 2); //resolve�Ǳ� ��ٸ�
        asyncResultB = await addAsync(asyncResultA, 3);  //resolve�Ǳ� ��ٸ�
        asyncResultC = await addAsync(asyncResultB, 4);  //resolve�Ǳ� ��ٸ�

        console.log(asyncResultA); // 3
        console.log(asyncResultB); // 6
        console.log(asyncResultC); // 10
    } catch (error) {
        console.error();
    }
    return 'resolvePromise'; // Promise.resolve('resolvePromise');
}
// asyncAdd�� Promise�� ��ȯ��
asyncAdd().then(result => {
    console.log(result);
});
~~~

> [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/await](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/await)

> [https://github.com/n00nietzsche/33jsconcept-KoreanTranslation/blob/master/26.async-await/async-await.md](https://github.com/n00nietzsche/33jsconcept-KoreanTranslation/blob/master/26.async-await/async-await.md)
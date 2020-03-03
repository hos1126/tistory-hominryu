## **1\. Promise�� �� ����ϴ°�?**

�ڹٽ�ũ��Ʈ�� �񵿱� ó���� ���� �ϳ��� �������� �ݹ� �Լ��� ����Ѵ�.

��� ȣ�⽺���� �Ҹ�� ��, **�̺�Ʈ �������� �񵿱� �Լ��� ����**�ϱ� ������,

�񵿱� �Լ��� ó�� ����� ���� ó���� **�񵿱� �Լ��� �ݹ� �Լ� ��**���� ó���ؾ� �Ѵ�.

�̷��� ���� ������ �ݹ�ȿ� �ݹ��� ����� �� �ۿ� ����.

**�ݹ���(call back hell)**�� �߻��ϴ� ���̴�.

~~~javascript
let resultA, resultB, resultC;

function add(num1, num2, callback) {
    callback(num1 + num2)
}

//call back Hell
add(1, 2, function A(sum) {
    //�񵿱��Լ� ����
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
    //���� ���ؽ�Ʈ���� undefined�� �Ҵ�Ǿ���, �񵿱� �Լ����� ��������
});

~~~

---

## **2\. Promise ���**

Promise ������ �Լ��� �񵿱� �۾��� ������ �ݹ� �Լ��� ���ڷ� ���޹޴µ� �� �ݹ� �Լ��� resolve�� reject �Լ��� ���ڷ� ���޹޴´�.

Promise ��� ����

1.  Promise ��ü ����
2.  Promise ���� ��, then()���� ����ó��
3.  catch()�� ����ó��

### **Promise ü�̴�**

**then()���� ���� result���� resolve�� ����**�� �ִ´�.

then()���� **Promise�� ��ȯ**�ϸ� �̸� **�ٽ� then()���� ����**�� �� �ִ�.(Call back Hell �ذ�)

### **Promise�� �񵿱�**

�Ʒ� console.log ����� undefined��� ��µǴ� ���� Promise�� �񵿱��̱� �����̴�.

~~~javascript
//Promise�� ��ȯ

let pmResultA, pmResultB, pmResultC;

const addPm = (num1, num2) => (
    new Promise((resolve, reject) => {
        resolve(num1 + num2);
    })
);

/* resolve�� �ٷ� return �� ���
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
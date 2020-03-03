## **�ܶ���(short-circuit evaluation)**

~~~javascript
console.log('ABC' && 'DEF') // DEF
console.log('ABC' || 'DEF') // ABC
console.log(false && 'DEF') // false
console.log(false || 'DEF') // DEF
~~~

**'ABC' && 'DEF'**

'ABC' �� TRUE�� ���, **'DEF'�� TRUE���� Ȯ���ؾ�** ��ü�� TRUE���� Ȯ�� �����ϹǷ�, ��ü�� �Ǵ��ϴ� ���� 'DEF'�̴�.

**'ABC || 'DEF'**

'ABC' �� TRUE�� ���, **'DEF'�� TRUE���� Ȯ������ �ʾƵ�** ��ü�� TRUE���� Ȯ�� �����ϹǷ�, ��ü�� �Ǵ��ϴ� ���� 'ABC'�̴�.

**false && 'DEF'**

ù��°���� false�� ���, **'DEF'�� TRUE���� Ȯ������ �ʾƵ�** ��ü�� TRUE���� Ȯ�� �����ϹǷ�,?��ü�� �Ǵ��ϴ� ���� false�̴�.

**false || 'DEF'**

ù��°���� false�� ���, **'DEF'�� TRUE���� Ȯ���ؾ�** ��ü�� TRUE���� Ȯ�� �����ϹǷ�,?��ü�� �Ǵ��ϴ� ���� 'DEF'�̴�.

**undefined, null, 0, -0, NaN, (���ڿ�)**�� ����� ���ǽĿ��� **false**�� �򰡵Ǵ� �����̴�.

~~~javascript
function evalString(str) {
  // str�� false�� ��� result=false
  // str�� true�� ��� result = str+'���ڰ� �ƴ�'
  let result = str && str + "(���ڰ� �ƴ�)";

  if (!result) {
    console.log("falsy����");
  } else {
    console.log(result);
  }
}
evalString("abc"); // abc
evalString(undefined); // falsy����
evalString(null); // falsy����
evalString(0); // falsy����
evalString(-0); // falsy����
evalString(NaN); // falsy����
evalString(""); // falsy����

~~~

> [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/)
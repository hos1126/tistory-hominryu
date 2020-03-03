## **�ڹٽ�ũ��Ʈ ������ ũ�� 4������ �����ȴ�**

### **�� ����(Call Stack)**

1\. �Լ��� ȣ���� �״´�. �Լ��� ������ �� push, �Լ��� ��ȯ�� pop�� �����Ѵ�.

2\. LIFO �����̴�.

### **��(Heap)**

1\. ������ �Լ��� �޸� �Ҵ��� �����ϴ� �����̴�.

### **�½�ũ ť(Task Queue or Callback Queue)**

1\. �ݹ� �Լ��� ���̴� �����̴�.

### **�̺�Ʈ ����(Event Loop)**

1\. �� ������ �������, �½�ũ ť���� �ݹ� �Լ��� �� �������� �Ű��ִ� ������ �Ѵ�.

![image](https://user-images.githubusercontent.com/50861435/75778275-d64def80-5d9a-11ea-948d-698b5783ba8e.png)

---

���� �ڵ�� �ڹٽ�ũ��Ʈ ������ ���� ������ ���캻��.

~~~javascript
console.log('x');
setTimeout(function test() { 
    console.log('y');
}, 1000);
console.log('z');
~~~

1.  console.log('x')�� �� ���ÿ� ���� ��, ����Ǹ� �ܼ� â�� x�� ��µǰ�, �� ���ÿ��� ���ŵȴ�.
    
2.  setTimeout()�� �� ���ÿ� ���� ��, ����Ǹ� **Web APIS�� Timers**�� ȣ���ϰ�, setTimeout()�� �� ���ÿ��� ���ŵȴ�.
    
3.  1�ʰ� ����� ��, �½�ũ ť�� �ݹ� �Լ��� test�� ������.
    
4.  console.log('z')�� �ݽ��ÿ� ���� ��, ����Ǹ� �ܼ� â�� 'z'�� ��µǰ�, �� ���ÿ��� ���ŵȴ�.
    
5.  �� ������?�������, �̺�Ʈ ������ �½�ũ ť�� �ִ� �ݹ� �Լ��� �� �������� ������.
    
6.  �� ���ÿ� ������� test(), console.log('y')�� ���δ�.
    
7.  console.log('y')�� ����Ǹ� �� ���ÿ��� ���ŵǰ�, �ܼ� â�� y�� ��µȴ�.
    
8.  test()�� �� ���ÿ��� ���ŵȴ�.
    

### **���� setTimeout�Լ��� �ι�° ���ڰ� 0�̶��?**

**����� �����ϴ�.**

�����̰� 0�ʿ��� setTimeout()�� Web API�� Timer�� ȣ���Ͽ�? �½�ũ ť�� �̵� ��, �̺�Ʈ ������ �ݹ��� test�� ȣ���ϱ� �����̴�.

���� 1,000ms ���Ŀ� ����� ���̶�� ���ٴ� 1,000ms ���Ŀ� ť�� �߰��� ���̶�� �ǹ̷� �ؼ��ȴ�. (0ms�� ����)

����, **�̺�Ʈ ������ �ݵ�� �� ������ ������� ���**, �½�ũ ť���� �� �������� �ݹ��� �����´ٴ� ���� �������.

> [https://www.zerocho.com/category/JavaScript/post/597f34bbb428530018e8e6e2](https://www.zerocho.com/category/JavaScript/post/597f34bbb428530018e8e6e2)

> [https://github.com/n00nietzsche/33jsconcept-KoreanTranslation/blob/master/1.CallStack/CallStack.md](https://github.com/n00nietzsche/33jsconcept-KoreanTranslation/blob/master/1.CallStack/CallStack.md)
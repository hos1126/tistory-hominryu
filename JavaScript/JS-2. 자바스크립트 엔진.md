## **자바스크립트 엔진은 크게 4가지로 구성된다**

### **콜 스택(Call Stack)**

1\. 함수의 호출을 쌓는다. 함수를 실행할 때 push, 함수를 반환할 pop을 수행한다.

2\. LIFO 구조이다.

### **힙(Heap)**

1\. 변수와 함수의 메모리 할당을 수행하는 공간이다.

### **태스크 큐(Task Queue or Callback Queue)**

1\. 콜백 함수가 쌓이는 공간이다.

### **이벤트 루프(Event Loop)**

1\. 콜 스택이 비워지면, 태스크 큐에서 콜백 함수를 콜 스택으로 옮겨주는 역할을 한다.

![image](https://user-images.githubusercontent.com/50861435/75778275-d64def80-5d9a-11ea-948d-698b5783ba8e.png)

---

다음 코드로 자바스크립트 엔진의 실행 과정을 살펴본다.

~~~javascript
console.log('x');
setTimeout(function test() { 
    console.log('y');
}, 1000);
console.log('z');
~~~

1.  console.log('x')가 콜 스택에 쌓인 후, 실행되면 콘솔 창에 x가 출력되고, 콜 스택에서 제거된다.
    
2.  setTimeout()이 콜 스택에 쌓인 후, 실행되면 **Web APIS에 Timers**를 호출하고, setTimeout()이 콜 스택에서 제거된다.
    
3.  1초간 대기한 후, 태스크 큐로 콜백 함수인 test를 보낸다.
    
4.  console.log('z')가 콜스택에 쌓인 후, 실행되면 콘솔 창에 'z'가 출력되고, 콜 스택에서 제거된다.
    
5.  콜 스택이?비었으니, 이벤트 루프는 태스크 큐에 있는 콜백 함수를 콜 스택으로 보낸다.
    
6.  콜 스택에 순서대로 test(), console.log('y')가 쌓인다.
    
7.  console.log('y')가 실행되면 콜 스택에서 제거되고, 콘솔 창에 y가 출력된다.
    
8.  test()가 콜 스택에서 제거된다.
    

### **만약 setTimeout함수의 두번째 인자가 0이라면?**

**결과는 동일하다.**

딜레이가 0초여도 setTimeout()이 Web API에 Timer를 호출하여? 태스크 큐로 이동 후, 이벤트 루프가 콜백인 test를 호출하기 때문이다.

따라서 1,000ms 이후에 실행될 것이라기 보다는 1,000ms 이후에 큐에 추가될 것이라는 의미로 해석된다. (0ms도 동일)

또한, **이벤트 루프는 반드시 콜 스택이 비어있을 경우**, 태스크 큐에서 콜 스택으로 콜백을 가져온다는 것을 기억하자.

> [https://www.zerocho.com/category/JavaScript/post/597f34bbb428530018e8e6e2](https://www.zerocho.com/category/JavaScript/post/597f34bbb428530018e8e6e2)

> [https://github.com/n00nietzsche/33jsconcept-KoreanTranslation/blob/master/1.CallStack/CallStack.md](https://github.com/n00nietzsche/33jsconcept-KoreanTranslation/blob/master/1.CallStack/CallStack.md)
## **브라우저는 크게 Rendering Engine, Javascript Engine으로 나뉜다.**

### **Rendering Engine**

1\. HTML, CSS는 Rendering Engine(렌더링 엔진)의 HTML Parser, CSS Parser에 의해 파싱된다.

2\. 각각 DOM, CSSOM Tree를 빌드하고 이 두개의 트리를 결합하여 Render Tree를 형성한다.

3\. Render Tree를 기반으로 브라우저에 Painting한다.

### **Javascript Engine**

Javscript 코드를 파싱하여, Syntax Tree를 만든 뒤, 실행한다.

---

여기서 Rendering Engine은 단일 스레드로 동작하기 때문에, <script>태그를 수행할 시,

Javascript Engine이 동작하면서 Rendering Engine이 중단된다. (**즉 HTML, CSS 파싱이 중단**된다.)

위와같은 이유에 의해서, **<body>태그의 끝부분**에 <script>를 작성하는 것을 추천한다.

![image](https://user-images.githubusercontent.com/50861435/75777940-41e38d00-5d9a-11ea-9e2c-1b1daff0f79b.png)

> https://poiemaweb.com
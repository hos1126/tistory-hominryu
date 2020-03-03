## ��Ʈ��ó��(Destructuring)�� ����ȭ�� **�迭 �Ǵ� ��ü**�� Destructuring(����ȭ, �ı�)�Ͽ� **�������� ����**�� �Ҵ��ϴ� ���̴�.

### **�迭 ���������Ҵ�**

~~~javascript
const arr = [1, 2, 3];
const [one, two, three] = arr;
console.log(one, two, three); // 1 2 3
~~~

�迭 ��Ʈ��ó���� ���ؼ��� �Ҵ� ������ ���ʿ� **�迭 ������ ��������Ʈ**�� �ʿ��ϴ�.

~~~javascript
const arr = [1, 2, 3];
const [one, two, three] = arr;
console.log(one, two, three); // 1 2 3

let x, y, z;

[x, y] = [1, 2];
console.log(x, y); // 1 2

[x, y] = [1];
console.log(x, y); // 1 undefined

[x, y] = [1, 2, 3];
console.log(x, y); // 1 2

[x, , z] = [1, 2, 3];
console.log(x, z); // 1 3

[x, y, z = 3] = [1, 2];
console.log(x, y, z); // 1 2 3

[x, y = 10, z = 3] = [1, 2];
console.log(x, y, z); // 1 2 3

// spread ����
[x, ...y] = [1, 2, 3];
console.log(x, y); // 1 [ 2, 3 ]
~~~

### **��ü ���������Ҵ�**

�Ҵ�?������?**������Ƽ?�̸�**(Ű)�̴�. ������ �ǹ̰� ����.

~~~javascript
var obj = {
    firstName: 'Ungmo',
    lastName: 'Lee'
};
var {firstName, lastName} = obj;
console.log(firstName, lastName);

//�������� ������ �� ����
const { prop1: p1, prop2: p2 } = { prop1: 'a', prop2: 'b' };
console.log(p1, p2); // 'a' 'b'
console.log({ prop1: p1, prop2: p2 }); // { prop1: 'a', prop2: 'b' }
~~~

��ü���� **������Ƽ �̸�(Ű)**���� **�ʿ��� ������Ƽ ����**�� ������ �� �ִ�.

������ ���� **�ݹ��Լ��� ����**�� ����� ��� ���� Ȱ��ȴ�.

~~~javascript
const todos = [
    { id: 1, content: 'HTML', completed: true },
    { id: 2, content: 'CSS', completed: false },
    { id: 3, content: 'JS', completed: false }
];

const completedTodos1 = todos.filter(todo => todo.completed);
// todo => ({completed})
// const {complete} = todo;
// todo�� todos�� ����� ��ü
const completedTodos2 = todos.filter(({ completed }) => completed);
console.log(completedTodos1); // [ { id: 1, content: 'HTML', completed: true } ]
console.log(completedTodos2); // [ { id: 1, content: 'HTML', completed: true } ]
~~~

��ø�� ��ü�� ���������Ҵ� �� ���

~~~javascript
const person = {
  name: 'Kim',
  address: {
    zipCode: '12345',
    city: 'Busan'
  }
};

const { address: { city } } = person;
console.log(city); // Busan
~~~

> [https://poiemaweb.com/es6-destructuring](https://poiemaweb.com/es6-destructuring)
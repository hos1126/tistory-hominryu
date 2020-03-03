## **��ü�� ����**

�ڹٽ�ũ��Ʈ�� ��ü�� **Ű**(key)�� **��**(value)���� ������ **������Ƽ(Property)���� ����**�̴�.

������Ƽ ���� **�Լ�**�� ���, �̸� **�޼ҵ�**(method)�� �θ���.

~~~javascript
const A = {
  key1: "value", // key1 : key, "value" : value
  key2: () => {} // method
};
// --> ������Ƽ���� ����
~~~

��ü�� �����ϴ� ����� **��ü���ͷ�**, **Object �������Լ�**�� �ִ�.

~~~javascript
//��ü ���ͷ�
var person1 = {
  name: 'Lee',
  gender: 'male',
  sayHello: () => {
    console.log('Hi! My name is ' + this.name);
  }
};

function Person(name, gender) {
  var ref = 'abc';
  this.name = name;
  this.gender = gender;
  this.sayHello = function(){
    console.log('Hi! My name is ' + this.name);
  };
}

// �ν��Ͻ��� ����
var person2 = new Person('Lee', 'male');
person2.sayHello(); // Hi! My name is Lee
console.log(person2.name); // Lee --> �Լ� �ۿ��� ��������
console.log(person2.ref); // undefined --> �Լ� �ۿ��� �����Ұ���
var person3 = new Person('Kim', 'female');
~~~

������ �Լ� ���� **this��** ������ �Լ��� ������ **�ν��Ͻ�**(instance)�� ����Ų�� .this�� ����(���ε�)�Ǿ� �ִ� ������Ƽ�� �޼ҵ�� **�ܺο��� ���� ����**(�Լ��ۿ���)�ϴ�.������ �Լ� ������ ����� �Ϲ� ������ �ܺο��� **���� �Ұ���**(�Լ� �ۿ���)�ϴ�.

## **��ü ������Ƽ ����**

��ü�� ������Ƽ ���� �����ϴ� ����� **��ħǥ(.) ǥ���**�� **���ȣ(\[\]) ǥ���**�� �ִ�.

**���ȣ ��**�� ���� ������Ƽ �̸��� **�ݵ�� ���ڿ�**�̾�� �Ѵ�.

~~~javascript
var person = {
  firstName: "hos",
  lastName: "ryu",
  gender: "male",
  1: 10
};

console.log(person.firstName); // hos
console.log(person["firstName"]); // hos
console.log(person.lastName); // ryu
console.log(person['lastName']); //ryu

console.log(person['1']); // 10
console.log(person[1]);   // 10
~~~

## **��ü ������Ƽ ��������, ����, ����**

��ü�� ���ο� ������Ƽ�� �������� ����, ����, ���� �� �� �ִ�.

~~~javascript
var person = {
  firstName: "hos",
  lastName: "ryu",
  gender: "male",
  1: 10
};
// ����
person['hobby'] = 'soccer';
console.log(person['hobby'] ); // 'soccer'

// ����
person[1] = 20;
console.log(person[1]); // 20

// ����
delete person.gender;
console.log(person.gender); // undefined

~~~

### **For in��**

��ü�� For in���� ���� ������ �� �ִ�.

~~~javascript
var person = {
  firstName: "hos",
  lastName: "ryu",
  gender: "male",
  1: 10
};

// prop�� ��ü�� ������Ƽ �̸��� ��ȯ�ȴ�. ��, ������ ������� �ʴ´�.
for (var key in person) {
  console.log(key + ': ' + person[key]);
}
/*
1: 10
firstName: hos
lastName: ryu
gender: male
*/

~~~

# **��ü�� �з�**

![img](https://k.kakaocdn.net/dn/rjktu/btqCpRlv4DO/kHYkHbYlIIdigsKEKU9W8k/img.png)

**Built-in Object**(���� ��ü)�� �������� ���� ǥ���ϱ� ���� ������ ����� �����Ѵ�.

**Standard Built-in Objects (or Global Objects)**

**BOM (Browser Object Model)**

**DOM (Document Object Model)**

**Standard Built-in Objects**(ǥ�� ��Ʈ�� ��ü)�� ������ BOM�� DOM�� **Native Object**��� �з��ϱ⵵ �Ѵ�.

���� ����ڰ� ������ ��ü�� **Host Object**(����� ���� ��ü)�� �Ѵ�.

**Host Object(����� ���� ��ü)**

�������Լ� Ȥ�� ��ü���ͷ��� ���� ����ڰ� ������ ��ü.

> [https://poiemaweb.com/js-object](https://poiemaweb.com/js-object)
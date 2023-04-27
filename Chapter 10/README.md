## 10.1 객체 리터럴

---

<aside>

💡 자바스크립트는 객체(object)기반의 프로그래밍 언어이며, 자바스크립트를 **구성하는 거의 모든 것이 객체**이다.

</aside>
<br>

**_그렇다면 “객체”란 과연 무엇일까?_**

<br>

객체는 **프로퍼티(property**)와 **메소드(method**)로 구성된 집합체이다.

- 프로퍼티(Property) : 객체의 상태를 나타내는 값(data)
- 메소드(method) : 프로퍼티(state data)를 참조하고 조작할 수 있는 동작(behavior)

<br>

JavaScript에서 사용할 수 있는 모든 값은 프로퍼티 값이 될 수 있다.
객체는 상태와 동작을 하나의 단위로 구조화하는 것이 가능하기에 유용하게 사용된다.

> **객체지향 프로그래밍** : 객체의 집합으로 프로그램을 표현하려는 프로그래밍 패러다임

<br>

## 10.2 객체 리터럴에 의한 객체 생성

---

<aside>

💡 자바스크립트는 **프로토타입 기반 객체지향 언어**로서 클래스 기반 객체지향 언어와는 달리 다양한 객체 생성 방법을 지원한다.

</aside>
<br>

JavaScript에서 객체를 생성하는 방법

- **객체 리터럴**
- Object 생성자 함수
- 생성자 함수

등등등..

<br>

가장 일반적이고 간단한 방법은 “**객체 리터럴**”을 사용하는 방법!

리터럴이란,
“사람이 이해할 수 있는 문자 또는 약속된 기호를 사용하여 값을 생성하는 표기법”

객체 리터럴이란,
”객체를 생성하기 위한 표기법”

코드를 살펴보면

```jsx
var person = {
	name: 'Choi',
	sayHello: function() {
		console.log(`Hello! My name is ${this.name}.`);  // 프로퍼티를 참조
	};
};

console.log(typeOf person);
console.log(person);

// output
object
{name: "Choi", sayHello: f}
```

- 중괄호 내에 프로퍼티를 지정하지 않으면, **빈 객체가 생성**된다.
- 객체 리터럴은 **JavaScrip의 유연함과 강력성을 대표**하는 객체 생성 방식이다.
- 객체 리터럴 외의 객체 생성 방식은 모두 **함수를 사용해 생성**한다.

<br>

## 10.3 프로퍼티

---

<aside>

💡 객체는 프로퍼티의 집합이며, 프로퍼티는 **키와 값으로 구성**된다.

</aside>

Ex)

```jsx
var person = {
  name: "Choi",
  age: 23,
};

// Property Key: name, age
// Property  Value: 'Choi', 23
```

- Property Key : 빈 문자열을 포함하는 모든 문자열 or 심벌 값
- Property Value: JavaScript에서 사용할 수 있는 모든 값

<br>

[주의해야 할 점]

식별자 네이밍 규칙을 준수하는 이름은 따옴표를 생략하는 것이 가능하다.
하지만, 반대로 말하면 **식별자 네이밍 규칙을 따르지 않는 이름에는 반드시 따옴표가 필요**!

```jsx
var person = {
	firstName: 'Choi',
	last-name: 'Joo hyun' // 식별자 네이밍 규칙을 지키지 않고 있는 Property Key
};

// SyntaxError 발생
```

<br>

## 10.4 메소드

---

<aside>

💡 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해 **메소드(Method)**라고 부른다.

</aside>
<br>

예제 code

```jsx
var circle = {
	radius: 5,
	getDiameter: function() {   // method
		return 2 * this.radius;   // this는 circle을 가리킨다.
	};
};

console.log(circle.getDiameter());

// output
10
```

method내부에서 사용한 this 키워드 → **객체 자신(circle)을 가리키는 참조 변수**

<br>

## 10.5 프로퍼티 접근

---

<aside>
💡 객체 내부의 프로퍼티에 접근하는 방법은 총 두 가지가 존재한다.

</aside>
<br>

1. 마침표 표기법(Dot notation) : 마침표 프로퍼티 접근 연산자를 사용
2. 대괄호 표기법(Bracket notation) : 대괄호 프로퍼티 접근 연산자를 사용

```jsx
var person = {
	name: 'Choi'
};

console.log(person.name);    // 마침표 표기법에 의한 접근
console.log(person['name'];  // 대괄호 표기법에 의한 접근

// output
'Choi'
'Choi'
```

[주의해야 할 점]

대괄호 표기법을 사용하는 경우,
대괄호 프로퍼티 내부에 지정하는 프로퍼티 키는 **반드시 따옴표로 감싼 문자열**이어야 한다.!

각자 사용하는 경우가 다른데,

- 프로퍼티 키가 식별자 네이밍 규칙을 따르는 경우
  - **마침표 표기법, 대괄호 표기법** 모두 사용이 가능
- 프로퍼티 키가 식별자 네이밍 규칙을 따르지 않는 경우
  - **대괄호 표기법만** 사용해야 함

<br>

## 10.6 프로퍼티 값 갱신

---

<aside>

💡 이미 존재하는 프로퍼티에 값을 할당하면 **프로퍼티 값이 갱신**된다.

</aside>

```jsx
var person = {
  name: "Choi",
};
person.name = "Kim"; // 이미

console.log(person.name);

// output
("Kim");
```

<br>

## 10. 7 프로퍼티 동적 생성

---

<aside>

💡 존재하지 않는 프로퍼티에 값을 할당 시, Error가 발생하는 것이 아니라 **자동으로 생성 및 추가**된다.

</aside>

```jsx
var person = {
	name: 'Lee';
};
person.age = 20;  // age프로퍼티가 동적으로 생성되고 할당됨

console.log(person);

// output
{name: 'Lee', age: 20}
```

<br>

## 10.8 프로퍼티 삭제

---

<aside>

💡 Delete 연산자는 **객체의 프로퍼티를 삭제**한다.

</aside>

```jsx
var person = {
  name: "Lee",
};
person.age = 20; // 동적 생성

delete person.age; // delete 연산자로 프로퍼티를 삭제
delete person.address.console // 아무런 에러가 뜨지 않는다.
  .log(person);

// output
{
  name: "Lee";
}
```

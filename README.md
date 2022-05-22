# 인프런
> <https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard>

## 타입스크립트 입문 - 기초부터 실전 까지
- 섹션 0. 강의 오리엔테이션
- 섹션 1. 타입스크립트 소개와 배경
- 섹션 2. 타입스크립트 시작하기
- 섹션 3. 타입스크립트 기초 - 변수와 함수 타입 정의하기
- 섹션 4. 첫 번째 프로젝트 - 할 일 관리 애플리케이션
- 섹션 5. 인터페이스
- 섹션 6. 타입 별칭
- 섹션 7. 연산자를 이용한 타입 정의
- 섹션 8. 이넘
- 섹션 9. 클래스
- 섹션 10. 제네릭
- 섹션 11. 두 번째 프로젝트 - 전화번호부 애플리케이션
- 섹션 12. 타입 추론
- 섹션 13. 타입 단언
- 섹션 14. 타입 가드
- 섹션 15. 타입 호환
- 섹션 16. 타입 모듈화

### 섹션 1. 타입스크립트 소개와 배경
- 간단하다. 타입스크립트는 자바스크립트에 타입을 부여한 언어
- 생산성 향성, 오류 방지의 목적이 있음
- 결국 선택의 문제.
- vscode 기준 플러그인 설치시 개발하는데 도움을 많이 받을 수 있음

```javascript
// 기본 자바스크립트
function sum(a, b) {
  return a + b;
}

// 타입스크립트
function sum(a: number, b: number) {
  return a + b;
}
sum('10', '20'); // Error: '10'은 number에 할당될 수 없습니다.
```
- 위와 같이 타입을 지정해 두면 어떤 타입의 값을 입력해야하는지 가이딩이 됨.

```javascript
function sum(a: number, b: number): number {
  return a + b;
}
var total = sum(10, 20);
total.toLocaleString();
```

- 위와 같이 타입을 지정해 두면 해당 타입에 알맞는 API를 선택할 수 있게 해줌.

### 섹션 3. 타입스크립트 기초 - 변수와 함수 타입 정의하기
#### 기본 타입
**String**
```javascript
let str: string = 'hi';
```
>위와 같이 :를 이용하여 자바스크립트 코드에 타입을 정의하는 방식을 타입 표기(Type Annotation)
**Number**
```javascript
let num: number = 10;
```
**Boolean**
```javascript
let isLoggedIn: boolean = false;
```
**Object**
**Array**
```javascript
let arr: number[] = [1,2,3];
let arr: Array<number> = [1,2,3];
```
**Tuple**
```javascript
// 튜플 - 배열의 길이가 고정되고 각 요소의 타입이 지정되어 있는 배열 형식
let arr: [string, number] = ['hi', 10];

// 오류 (정의 되지 않은 접근)
arr[1].concat('!'); // Error, 'number' does not have 'concat'
arr[5] = 'hello'; // Error, Property '5' does not exist on type '[string, number]'.
```
**Enum - 상수들의 집합**
```javascript
enum Avengers { Capt, IronMan, Thor }
let hero: Avengers = Avengers.Capt;

enum Avengers { Capt, IronMan, Thor }
let hero: Avengers = Avengers[0];
```
**Any**
- 자바스크립트로 구현된 웹 서비스에 타입스크립트를 점진적으로 적용할때 활용하면 좋음
- 모든 타입 허용.
```javascript
let str: any = 'hi';
let num: any = 10;
let arr: any = ['a', 2, true];
```
**Void**
- undefined, null 할당. 함수에는 반환 값을 설정할 수 없는 타입
```javascript
let unuseful: void = undefined;
function notuse(): void {
  console.log('sth');
}
```
**Never**
- 함수의 끝에 절대 도달하지 않는다는 타입
```javascript
// 이 함수는 절대 함수의 끝까지 실행되지 않는다는 의미
function neverEnd(): never {
  while (true) {

  }
}
```
#### 함수
- 함수 기본 형태
```javascript
function sum(a, b) {
  return a + b;
}
function sum(a: number, b: number): number {
  return a + b;
}
```
- 함수 인자
타입스크립트는 함수의 인자를 필수 값으로 간주 함. undefined, null 이라도 넘겨야 하고 추가로 인자를 넘길 수는 없다.
```javascript
function sum(a: number, b: number): number {
  return a + b;
}
sum(10, 20); // 30
sum(10, 20, 30); // error, too many parameters
sum(10); // error, too few parameters
```
- 인자 개수를 꼭 맞추지 않으려면 다음과 같이 작성
```javascript
function sum(a: number, b?: number): number {
  return a + b;
}
sum(10, 20); // 30
sum(10, 20, 30); // error, too many parameters
sum(10); // 10
```
- 초기화
```javascript
function sum(a: number, b = '100'): number {
  return a + b;
}
sum(10, undefined); // 110
sum(10, 20, 30); // error, too many parameters
sum(10); // 110
```
- REST 문법 적용
```javascript
function sum(a: number, ...nums: number[]): number {
  const totalOfNums = 0;
  for (let key in nums) {
    totalOfNums += nums[key];
  }
  return a + totalOfNums;
}
```
- this
```javascript
function 함수명(this: 타입) {
  // ...
}
```
이해 안되면 다음 페이지에서 확인 [https://joshua1988.github.io/ts/guide/functions.html#rest-%EB%AC%B8%EB%B2%95%EC%9D%B4-%EC%A0%81%EC%9A%A9%EB%90%9C-%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98](https://joshua1988.github.io/ts/guide/functions.html#rest-%EB%AC%B8%EB%B2%95%EC%9D%B4-%EC%A0%81%EC%9A%A9%EB%90%9C-%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98)

### 섹션 5. 인터페이스
- 인터페이스는 상호 간에 정의한 약속 혹은 규칙
  - 객체의 스펙(속성과 속성의 타입)
  - 함수의 파라미터
  - 함수의 스펙(파라미터, 반환 타입 등)
  - 배열과 객체를 접귾는 방식
  - 클래스

```javascript
// 기본
let person = { name: 'Capt', age: 28 };

function logAge(obj: { age: number }) {
  console.log(obj.age); // 28
}
logAge(person); // 28

// 인터페이스 적용
interface personAge {
  age: number;
}

function logAge(obj: personAge) {
  console.log(obj.age);
}
let person = { name: 'Capt', age: 28 };
logAge(person);
```
- 인터페이스를 인자로 받아 사용할 때 인터페이스 개수와 인자로 받는 객체의 속성 개수를 일치시키지 않아도 된다.
- 속성, 조건만 만족한다면 객체의 속성 개수가 더 많아도 상관 없다. 순서를 지키지 않아도 됨.

#### 옵션 속성
- 인터페이스에 정의되어 있는 속성을 모두 다 꼭 사용하지 않아도 됨. 이를 옵션 속성. (? 사용)
- 선택적 적용이 가능하고, 정의되어 있지 않은 속성에 대해서 인지시켜줄 수 있음.
```javascript
interface CraftBeer {
  name: string;
  hop?: number;  
}

let myBeer = {
  name: 'Saporo'
};
function brewBeer(beer: CraftBeer) {
  console.log(beer.name); // Saporo
}
brewBeer(myBeer);
```
#### 읽기 전용 속성
- 처음 생성할 때만 값 할당하고 이후에는 변경 불가
```javascript
interface CraftBeer {
  readonly brand: string;
}

let myBeer: CraftBeer = {
  brand: 'Belgian Monk'
};
myBeer.brand = 'Korean Carpenter'; // error!
```
#### 읽기 전용 배열
- ReadonlyArray<> 선언 시점에만 값 정의가 가능
```javascript
let arr: ReadonlyArray<number> = [1,2,3];
arr.splice(0,1); // error
arr.push(4); // error
arr[0] = 100; // error
```
#### 객체 선언과 관련된 타입 체킹
- 인터페이스를 이용하여 객체 선언시 엄밀한 속성 검사 진행 함
```javascript
interface CraftBeer {
  brand?: string;
}

function brewBeer(beer: CraftBeer) {
  // ..
}
brewBeer({ brandon: 'what' }); // error: Object literal may only specify known properties, but 'brandon' does not exist in type 'CraftBeer'. Did you mean to write 'brand'?
```
- 타입 추론을 무시하고 싶다면 다음과 같이 선언
```javascript
let myBeer = { brandon: 'what' }';
brewBeer(myBeer as CraftBeer);
```
- 여기서 인터페이스 정의하지 않은 속성들을 추가로 사용하고 싶을때는
```javascript
interface CraftBeer {
  brand?: string;
  [propName: string]: any;
}
```

#### 함수 타입
- 인터페이스는 함수의 타입을 정의할 때에도 사용 가능
```javascript
interface login {
  (username: string, password: string): boolean;
}

let loginUser: login;
loginUser = function(id: string, pw: string) {
  console.log('로그인 했습니다');
  return true;
}
```

### 섹션 6. 타입 별칭

### 섹션 7. 연산자를 이용한 타입 정의

### 섹션 8. 이넘
### 섹션 9. 클래스

### 섹션 10. 제네릭

### 섹션 11. 두 번째 프로젝트 - 전화번호부 애플리케이션

### 섹션 12. 타입 추론

### 섹션 13. 타입 단언

### 섹션 14. 타입 가드

### 섹션 15. 타입 호환

### 섹션 16. 타입 모듈화
#### 관련 자료
- <https://joshua1988.github.io/ts/intro.html>
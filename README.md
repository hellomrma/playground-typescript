# 인프런
> <https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard>

## 타입스크립트 입문 - 기초부터 실전까지
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

### 섹션 4. 첫 번째 프로젝트 - 할 일 관리 애플리케이션

### 섹션 5. 인터페이스

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
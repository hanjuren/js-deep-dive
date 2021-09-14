## 제어문
제어문은 조건에 따라 코드블록을 실행하거나 반복 실행할 때 사용한다.  
일반적인 실행 순서는 위에서 아래이며 제어문을 사용하면 순서를 인위적으로 제어 할 수 있다.  

### 블록문
블록문이란 0개 이상의 문을 중괄호로 묶은 것으로 코드 블록, 블록 이라고 부른다. 자바스크립트에서는 블록문 하나를 실행단위로 취급한다.  
블록문은 단독으로 사용이 가능하나 제어문, 함수정의시 사용하는 것이 일반적인 사용방법이다.  

```js
{
  var foo = 10;
}

// 제어문
var x = 1;
if (x < 10) {
  x++;
}
```

### 조건문
조건문은 조건식의 결과에 따라 코드 블록의 실행을 결정한다. 자바스크립트에서는 if...else문과 switch문 두가지의 조건문을 제공한다.

#### if...else문
```js
if (조건식) {
  // 조건식이 참일경우 이 코드블럭이 실행됨
} else {
  // 조건식이 거짓일경우 이 코드블럭이 실행된다.
}
```
if...else문은 주어진 조건식의 평과결과를 통해 실행할 코드블럭을 결정한다. 이때 평과 결과는 불리언 타입으로 평가되어야 한다.  
조건식을 추가하여 실행할 코드블록을 늘리고 싶다면 else if문을 사용한다.

```js
if (조건식1) {
  // 조건식 1이 참일 경우
} else if (조건식2) {
  //조건식2가 참일 경우
} else {
  // 조건식 1, 조건식2가 모두 거짓일때 실행
}
```
대부분의 if...else문은 삼항 조건 연산자로 바꿔 사용이 가능하다.

```js
var x = 2;
var result;

if (x % 2) {
  result = '홀수';
} else {
  result = '짝수';
}
console.log(result);

// 삼항 조건 연산자로 사용

var x = 2;
var result = x % 2 ? '홀수' : '짝수';
console.log(result);
```
조건에 따라 값을 결정하여 변수에 할당하는 경우에는 삼항 조건 연산자를 사용하는 편이 가독성이 좋고 조건에 따라 실행해야하는 내용이 많거나 복잡한경우 if...else문을 사용하는 것이 가독성이 좋다.

#### switch문
switch문은 주어진 표현식을 평가하여 그 값과 일치하는 표현식을 갖는 case문으로 실행의 흐름을 옮겨 실행된다.

```js
switch (표현식) {
  case 표현식1 :
    switch문의 표현식과 표현식1이 일치시 실행될 문;
    break;
  case (표현식2) :
    switch문의 표현식과 표현식2가 일치시 실행될 문;
    break;
  default :
    switch문의 표현식과 일치하는 표현식이 없을때 실행될 문;
}
```

switch문의 표현식은 불리언 값보다는 문자열이나 숫자 값이 경우에 많이 사용한다.

switch문을 이용한 윤년계산 예제.
```js
// 연도가 4로 나누어 떨어지는 해는 윤년이다.
// 4로 나누어 떨어지지만 100으로 나누어 떨어지는 해는 평년이다.
// 연도가 400으로 나누어 떨어지는 해는 윤년이다.

var year = 2021;
var month = 2;
var days = 0;

switch (month) {
  case 1: case 3: case 5: case 7: case 8: case 10: case 12:
    days = 31;
    break;
  case 4: case 6: case 9: case 11:
    days = 30;
    break;
  case 2:
    days = ((year % 4 === 0 && year % 100 !== 0) || (year % 400 === 0)) ? 29 : 28;
    break;
}
console.log(days); // 28
```

### 반복문
반복문은 조건식의 평과 결과가 참인 경우 코드블럭을 실행한다. 그 후 여전히 조건식이 참인경우 코드블럭을 다시 실행한다.  

> 자바스크립트에서는 베열을 순회할 때 사용하는 forEach메서드 객체의 프로퍼티를 열거할때 사용하는 for...in문 과 같은 반복문을 대체할 수 있는 다양한 기능을 제공한다.

#### for문
for문은 조건식이 거짓으로 평가될 때까지 코드블록을 반복 실행한다. 가장 일반적으로 사용되는 for문의 형태는 다음과 같다.

```js
for (변수 선언문 또는 할당문; 조건식; 증감식;) {
  조건식이 참일 경우 반복 실행될 문;
}
```

for문의 실행법
```js
for (var i = 0; i < 2; i++) {
  console.log(i);
}
```
실행순서
* for문을 실행하면 변수 선언문이 실행된다. 변수 선언은 한번만 실행된다.
* 변수 선언문이후 조건식이 실행된다. 
* 조건문의 평과 결과가 true일때 코드블록이 실행된다.
* 코드블록의 실행이 종료되면 증감식이 실행된다.
* 증감식 실행 이후 평과 결과가 true면 코드블럭을 실행 false면 반복문에서 빠져나온다.

#### while문
while문은 조건식의 평과 결과가 참이면 코드블럭을 반복하여 실행한다. for문은 반복 횟수가 명확할때 주로 사용하며 while문은 횟수가 불명확 할때 주로 사용한다.

```js
var count = 0;

while (count < 3) {
  console.log(count);
  count++;
}
```
조건식이 참일경우 반복하여 실행이 된다. 조건식의 평과 결과가 항상 true일 경우에 무한루프가 된다.

#### do...while문
do...while문은 코드블록을 먼저 실행하고 조건식을 평가한다. 따라서 코드블록이 한번이상 무조건 실행이 된다.

```js
var i = 0;

do {
  console.log(i);
  i++;
} while (i < 3);
```

#### break문
break문은 반복문, 레이블문에서의 코드블록을 탈출하는 역할을 한다.

레이블문이란 식별자가 붙은 문을 의미한다.

```js
outer : for (var i = 0; i < 3; i++) {
  for (var j = 0; j < 3; j++) {
    if (i + j === 3) break outer;
    console.log(`${i} ${j}`);
  }
}
```

#### continue문
continue문의 반복문은 코드블록의 실행을 현 지점에서 중지하고 반복문의 증감식으로 실행흐름을 이동시킨다.

```js
var string = 'heLlo world';
var search = 'l';
var count = 0;

for (var i = 0; i < string.length; i++) {
  if (string[i] !== search) continue;
  count++;
}
console.log(count);

const re = new RegExp(search, 'g');
console.log(string.match(re).length);
```
---
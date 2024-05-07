# JavaScript 핵심 문법
<br/> 

* 일반적인 알고리즘 문제를 풀 때, 표준 출력으로 console.log()를 이용한다.

``` JavaScript
// 단순히 문자열을 출력합니다.
console.log('Hello World!'); // Hello World!

result = 35;
// 템플릿 리터럴을 사용해 문자열 내부에 변수를 포함합니다. (백틱 문자 사용)
console.log(`정답은 ${result}입니다.`); // 정답은 35입니다.
```
<br/> 

* 빠른 출력
``` JavaScript
let answer = '';

/*
여러 출력 결과를 한 줄에 하나씩 출력할 때 매 번 console.log()를 실행하지 않고,
하나의 문자열에 결과를 저장해서 한번에 출력하는 것이 대개 더 빠르게 수행됩니다.
*/
for (let i = 1; i <= 100; i++) {
  answer += i + '\n'; // 문자열로 변환하여 기록
} 

console.log(answer)
```
<br/>

-fs 모듈
* 전체 텍스트를 읽어 온 뒤에, 줄바꿈 기호를 기준으로 구분하여 리스트로 변환하기
``` JavaScript
// readline 모듈보다는 fs를 이용해 파일 전체를 읽어 들여 처리하기
let fs = require('fs');
let input = fs.readFileSync('input.txt').toString().split('\n');

console.log(input)
```
input.txt<br/>
123
456
789 1000

[출력 예시]<br/>
['123', '456', '789 1000']
<br/><br/>

readline 모듈
* 한 줄씩 입력을 받아서, 처리하여 정답을 출력할 때는 **readline 모듈**을 사용할 수 있다.
``` javascript
const rl = require('readline').createInterface({
  input: process.stdin,
  output: process.stdout
});

let ubput = [];
rl.on('line', function(line) {
  // 콘솔 입력 창에서 줄바꿈(Enter)를 입력할 때마다 호출
  input.push(line);
}).on('close', function() {
  //콘솔 입력 창에서 Ctrl + C 혹은 Ctrl + D를 입력하면 호출 (입력의 종료)
  console.log(input);
  process.exit();
});
```
<br/>
조건문

* 조건에 따라서 프로그램의 흐름을 결정할 때 사용할 수 있는 문법이다.
``` JavaScript
/*
condition: 참 혹은 거짓을 반환하는 조건식
statement1: condition1이 참일 때 실행되는 구문 
statement2: condition1이 거짓이고, condition2가 참일 때 실행되는 구문
statementN: 앞의 모든 조건문이 거짓일 때 실행되는 구문
*/

if (condition1)
  statement1
else if (condition2)
  statement2
else
  statementN
```
<br/>
반복문

* 조건에 따라서 ***특정한 코드를 반복***하고자 할 때 사용할 수 있는 코드다.
```JavaScript
/*
- 초기문이 존재한다면 초기문이 먼저 실행됩니다.
- 초기문이 참이라면 블록 내부 코드가 실행되고, 거짓이면 반복문이 종료됩니다.
- 블록 내부 코드가 실행된 뒤에 증감문이 실행됩니다.
*/
for ( 초기문; 조건문; 증감문) {
  // statements
}

// 1부터 100까지의 합 계산
let summary = 0;
for (let i = 1; i <= 100; i++) {
  summary += i;
}
console.log(summary);
```
<br/>
while 반복문

* 조건에 따라서 ***특정한 코드를 반복***하고자 할 때 사용할 수 있는 코드다.
```JavaScript
/* 
- while문은 조건문이 참일 때 실행되는 반복문입니다.
- 블록 내부의 코드가 실행되기 전에 참 혹은 거짓을 판단합니다.
*/
while (조건문) {
  // 실행되는 코드 부분
}
```
<br/>
Number와 String 형태 변화

* ***수(number)*** 데이터와 ***문자열(string)***데이터간의 상호 변환이 필요하다.
```javascript
/*
Int -> String
*/
let a = '777';
let b = Number(a);
console.log(b); // 777

/*
String -> Int
*/
let a = 777;
let b = String(a);
console.log(b); // "777"
```
<br/>
Array.protoype.reduce()

* 배열의 모든 원소에 대해 특정한 연산을 순차적으로 적용할 때 reduce()를 사용한다.
```javascript
/*
reduce() 메서드는 배열의 각 요소에 대해 reducer 함수를 실행한 뒤에 하나의 결과를 반환합니다.
reducerdml 형태: (accumulator, currentValue) => (반환값)
- 배열의 각 원소를 하나씩 확인하여, 각 원소는 currentValue에 해당합니다.
- 반환값은 그 이후의 원소에 대하여 accumulator에 저장됩니다.
 */

let data = [5, 2, 9, 8, 4]

// minValue 구하기 
let minValue = data.reduce((a, b) => Math.min(a, b));
console.log(minValue) // 2

// 원소의 합계 
let summary = data.reduce((a, b) => a+b);
console.log(summary); // 28
```
<br/>
배열 초기화<br/><br/>

```javascript
// 직접 값을 설정하여 초기화
let arr = [8, 1, 4, 5, 7];

// 길이가 5이고 모든 원소의 값이 0인 배열 초기화
let arr = new Array(5).fill(0);
```
<br/>
집합 자료형

* 특정한 ***원소의 등장 여부***를 파악할 때 집합 자료형을 효과적으로 사용할 수 있다.
```javascript
let mySet = new Set(); // 집합 객체 생성

// 여러 개의 원소 삽입
mySet.add(3);
mySet.add(5);
mySet.add(7);
mySet.add(4);

console.log(`원소의 개수: ${mtSet.size}`);
console.log(`원소를 7을 포함하고 있는가? ${mtSet.has(7)}`);

// 원소 5 제거
mySet.delete(5);

// 원소를 하나씩 출력
for (let item of mySet) console.log(item);
```
<br/>
소수점 아래 특정 자리에서 반올림

* 실수를 출력할 때 소수점 아래 특정 자리에서 반올림할 수 있다.
```javascript
// 특정 실수에 대해서 toFixed()를  이용해 소수점 아래 둘째 자리까지 출력
let x = 123.465
console.log(s.toFixed(2)); // 123.47
```
<br/>
이스케이프 시퀸스(Escape Sequence)

* ***예약 문자*** 혹은 ***특수 문자***를 출력하기 위하여 이스케이프 시퀸스를 사용할 수 있다.
<br/>
```JavaScript
\t - 탭
\\ = 역슬래쉬
\" - 큰 따옴표
\' - 작은 따옴표

console.log("그는 \"비범함\"을 보였다.");
```
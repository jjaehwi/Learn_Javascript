# 2강

## 2-1. 세미콜론, 주석, 들여쓰기

**세미콜론**

- 자바스크립트는 하나의 명령이 끝날 때 세미콜론을 붙여도 되고 안붙여도 된다. 하지만 `세미콜론 붙이기를 권장`한다. 명령 하나하나를 구분하기 위해 쓴다.

- 안붙혀도 에러는 안나지만, 에러가 나는 경우도 있다. 하지만 붙여서 에러나는 경우는 없다.

**주석(comment)**

- 사람만 알아볼 수 있도록 설명을 작성하는 부분

- 주석에 적은 내용은 코드에 영향을 미치지 않으며 `코드에 대한 자세한 설명을 작성`하거나, `특정 코드를 임시로 사용하지 않도록 만들 때 사용`한다.

**들여쓰기**

- 자바스크립트는 파이썬이나 루비와 달리 들여쓰기에 제한이 없다. 여기선 스페이스 2 칸으로 통일한다.

```
if(condition){
    console.log('Hello, world!');
}
```

## 2-2. 문자열 기본 (따옴표, 백틱, typeof, escape)

`값(value) 은 프로그램이 조작할 수 있는 데이터`를 의미한다. 값에는 여러 가지 종류가 있으며 이런 값의 종류를 `자료형(date type)` 이라고 한다.

`typeof()` 를 통해 자료형을 알아낼 수 있다.

**문자열(string)**

- 프로그래밍에서 하나의 글자를 문자라고 하는데, `문자들이 하나 이상 나열되어 있다고 해서 문자열`이다. 이미 사용한 적이 있는데 'Hello, world' 처럼 `시작과 끝이 작은따옴표, 큰따옴표, 백틱으로 감싸진 값이 문자열`이다.

- 백틱(₩)의 특성은 `줄바꿈이 가능하다는 점`이다.

- 문장안에 따옴표가 들어가는 경우 1. 작은 따옴표를 큰 따옴표로 감싸기, 2. 큰 따옴표를 작은 따옴표로 감싸기, 3. 백틱으로 감싸기, 4. `역슬래쉬` 를 사용한다.

```
1. " ' "
2. ' " '
3. ` ' `
4. 'how\'re you?'
```

## 2-3. 문자열 합치기 (연산자)

`문자열끼리도 서로 사칙연산을 할 수 있다.`

문자열을 합칠 때 많이 하는 실수인 띄어쓰기를 잘 생각하자.

## 2-4. 숫자 기본(parseInt, NaN)

- 숫자는 따옴표로 감싸지 않고 그대로 적으면 된다. 따옴표로 감싼 숫자는 문자열이지 숫자가 아니다.

- 0 이 많이 붙는 경우 ex) 50000 --> 5e4, 0.0005 --> 5e-4 로 표현 가능하다.

- 0b(2진법), 0o(8진법), 0x(16진법) 으로도 표현 가능하다.

- `NaN (Not a Number) 의 type 은 number 이다.` (typeof Nan -> number)

- `Infinity 의 type 도 number 이다.`

**형 변환(type casting)**

- `값의 자료형이 바뀌는 현상 또는 바꾸는 행위`를 형 변환 이라고 한다.

- `parseInt()`, `Number()` 를 통해 문자열을 숫자로 바꿀 수 있다.

```
'123' + 5 // 1235 (형 변환 -> 문자열 5 으로 전환된 것)
parseInt('124') + 5 // 129
Number('124') + 5 // 129
parseInt(111, 2) // 7 (2진법 해석)
typeof parseInt('123') // "number"
typeof NaN // "number"
1 + '0' // "10"
parseInt('문자열') // NaN
NaN - 0 // NaN
'문자열' - 0 // NaN
'3' - 0 // 3
parseInt('3') - 0 // 3
'3월' - 0 // NaN
Number('3월') // NaN
Number('3월') - 0 // NaN
parseInt('3월') - 0 // 3
```

- **`더하기는 문자열이 아닌 애들이 문자열`로 바뀌는 데, `빼기 곱하기 나누기는 숫자가 아닌 애들이 숫자`로 바뀐다.**

- parseInt() 는 정수로 바꾸기 때문에 소수로 바꾸고 싶다면 `parseFloat()` 을 사용한다.

- Number() 는 알아서 판단해서 바꿔준다.

차이점 예시

```
parseInt('3월') // 3
Number('3월') // NaN
```

## 2-5. 연산자 우선순위, 소수 계산 주의점

- 연산자 우선 순위 : [정리 해놓은 모던 자바스크립트 참고](https://github.com/jjaehwi/Learn_Javascript/blob/main/Modern_JS/1_Core/02-first-steps/08-operators/article.md)

- **소(실수) 계산 시 주의할 점**

자바스크립트는 `정수, 실수 나눠져 있는 것이 아닌 전부 숫자 로 취급`한다.

`부동소수점 문제` 발생 : 간단히 고치는 방법은 실수를 정수로 바꿔서 계산한 뒤, 마지막에 다시 실수로 바꾸면 해결

```
0.5 + 0.5 // 1
0.1 + 0.2 // 0.30000000000000004
0.3 - 0.1 // 0.19999999999999998
(0.3 * 10 - 0.1 * 10) / 10 // 0.2
```

## 2-6. 불 값 (boolean, 값들의 비교)

- 부동소수점 문제가 발생하는 이유는 컴퓨터가 실제로 1 과 0 밖에 모르기 때문이다. 1 과 0 은 참(true), 거짓(false) 에 대응된다. 자바스크립트에도 true 와 false 를 나타내는 `불 값(boolean) 이라는 자료형`이 있다.

```
true // true
false // false
typeof true // 'boolean'
typeof 'true' // 'string'
5 < 3 // false
NaN == NaN // false
NaN != NaN // true
true > false // true
```

- **문자열끼리 비교하는 경우** : 기본적으로 `문자의 번호(ASCII코드)를 따른다.` 문자의 번호가 클수록 값이 큰 것이다. 첫 문자가 같은 글자일 때는 첫 문자를 빼고 나머지를 다시 비교한다.

```
'a'.charCodeAt() // 97
'b'.charCodeAt() // 98
'a' > 'b' // false
'ab' > 'a' // true
```

- **다른 자료형끼리 비교하는 경우** : 빼기 연산자 때처럼 `다른 자료형이 모두 숫자로 형 변환`된 후 비교한다.

```
'3' < 5 // true
'abc' < 5 // false ('abc'를 숫자로 변환하면 NaN)
'0' < true // true (0 < 1)
```

- **== 와 ===** : `==` 은 `값만 비교`하고 자료형은 비교하지 않지만 , `===` 은 **`값을 비교하고 자료형 까지 같은지 비교`** 한다. `!=` 과 `!==` 도 마찬가지 이다.

```
'1' == 1 // true
1 == true // true
'1' === 1 // false
1 === true // false
1 != '1' // false
1 !== '1' // true
```

## 2-7. 논리연산자

- 불 값은 논리식을 다룰 때 많이 사용한다. 프로그래밍에서는 AND, OR 와 같은 연결고리를 표현해주는 연산자가 있다.

```
10 > 5 && 6 < 8 // true (&& 는 AND)
10 > 5 || 6 < 8 // false (|| 는 OR)
!true // false
!(2 < 0) // true
!2 < 0 // false
!!'a' // true (boolean 으로 형 변환한 것)
!!false // false
!!'' // false
!!0 // false
!!NaN // false
```

**`false`, `'' (빈 문자열)`, `0`, `NaN`, `undefined`, `null`, (document.all)** 은 boolean 형 변환을 하면 false 가 되는 것들이다.

## 2-8. undefined 와 null

- 문자열, 숫자, 불 값 자료형에 대해 공부했는데, 이 외에도 네 가지 (undefined, null, object, symbol) 가 더 있다. `undefined` 와 `null` 자료형은 `빈 값 (비어 있음)을 표현`한다는 공통점도 있지만 차이점도 있다.

```
typeof undefined // 'undefined'
typeof null // 'object'
undefined == false // false
undefined == 0 // false
undefined == null // true
undefined === null // false
!!undefined // false
!!null // false
```

- `undefined` 는 `보통 반환할 결과값이 없을 때` 나온다. console.log 명령어는 콘솔에 무언가를 출력하지만, 그 자체로는 결과값이 없기 때문에 undefined 가 반환된다.

- **typeof null 의 결과값은 'null' 이 아니고 'object' 이다.** 이 현상은 자바스크립트에서 유명한 **버그**이다. 원래는 'null' 이 나와야하지만 초창기 실수 때문에 'object' 가 됐다. 따라서 null 값인지 확인하기 위해서는 `=== null` 을 사용해야 한다.

- null 과 undefined 는 둘 다 빈 값이라서 어떨 때 사용하는지 헷갈릴 수 있다. `undefined 는 기본값이라는 의미`라도 있지만, `null 은 역할이 없다.` 일부 개발자는 null 을 의도적으로 사용하는 경우가 있는데, 변수를 배울 때 공부한다.

## 2-9. 변수 선언하기 (let)

- `변수 (variable)` : **특정한 값을 저장**해두는 **공간**

```
let total = 32000
console.log(total) // 32000
```

이렇게 total 처럼 값을 저장하고, 저장한 값을 불러올 수 있게 하는 것이 `변수 (variable)` 이다. 변수를 만드는 행위는 `선언 (declaration)` 한다라고 한다.

**변수 선언하는 방법**

변수를 만드는 방법은 세 가지가 있는데, **`let`, `const`, `var`** 이다.

**let**

- let 으로 시작하는 명령을 `선언문`이라고 한다.

- 변수를 선언함과 동시에 값을 대입하는 행위를 `초기화 (initialization)` 라고 한다.

- 변수 선언은 항상 `결과값이 undefined` 로 출력된다.

- 변수를 선언하면 컴퓨터의 메모리 공간에 저장이 되어있고, 저장되어 있는 공간에서 선언된 변수명을 가지고 값을 찾는다. (RAM 메모리)

## 2-10. 변수 이름짓기

- `값을 대입하지 않은 변수`를 입력하면 **undefined** 가 출력된다. (기본값이 되는 것)

```
let empty;
empty; // undefined
```

- let 변수는 `이미 선언한 변수를 다시 선언하는 경우 에러`가 발생한다. 변수명이 겹치지 않도록 주의하자.

**변수명 짓기**

- 의미 명확하게 짓자, 영어로 짓자, 카멜 표기법

- `예약어 (reserved word)`는 자바스크립트 프로그래밍을 할 때 각각 특정한 역할을 하기 때문에 변수명으로 쓸 수 없다.

## 2-11. 변수 수정하기

- 변수는 `변하는 숫자`라는 의미지만, 실제로는 숫자 자료형 외에도 다양한 자료형의 값을 저장할 수 있다. 중요한 것은 `'변하는'` 이다. `한 번 저장한 값을 바꿀 수 있다는 뜻`이다.

```
let change = "바꿔라" // undefined (초기화 땐 값을 돌려주지 않는다)
change = "바꿨다" // "바꿨다" (값을 돌려준다)
change // "바꿨다"
```

- let 이 없을 때는 `코드가 식이라서 대입한 값이 결과값으로 출력`되지만, let 이 앞에 붙는 순간 `선언문`이 된다. 여기서 **`문 (statement)`** 라는 개념이 나온다.

- **`문은 식과 다르게 결과값이 없고 식의 자리에 사용할 수 없다.`**

- 값을 비우는 경우 1. `undefined` 를 대입하거나 2. `null` 을 대입한다. 보통 null 을 대입하여 값을 의도적으로 비웠다는 것을 의미한다.

## 2-12. 상수 (const) 와 var

- `변수는 변하는 수` 이고 반대로 `상수는 변하지 않는 수` 라는 뜻이다.

**const** : `상수 (const)`의 줄임말이다.

**const 로 선언한 상수는 다시 선언**할 수 없다. 또한, `한 번 값을 대입하면 다른 값을 대입할 수 없다는 `특성 때문에 **상수 선언 시 초기화 하지 않으면 에러가 발생**한다.

- var 은 let 과 const 로 대체 가능하다.

[var, let, const 차이점 : variable_diff.md 참고](https://github.com/jjaehwi/Learn_Javascript/blob/main/Modern_JS/1_Core/02-first-steps/04-variables/variable_diff.md)

## 2-13. 조건문 (if)

- **`조건문`**은 `주어진 조건에 따라 코드를 실행하거나 실행하지 않는 '문'` 이다.

- 조건문은 조건식과 동작문으로 구분된다. 조건식이 참인 값이면 내부의 동작문이 실행되고, 거짓인 값이면 동작문이 실행되지 않는다.

```
if (조건식)
    동작문;

if(true){
    console.log('Hello, if!');
}
// 'Hello, if!'
// undefined (리턴값)
```

## 2-14. else, else if, switch

- 분기를 표현하는 조건문 `else`

```
if (조건식){
    동작문;
} else {
    동작문;
}
```

- 세 가지 경우의 수를 표현하는 조건문 `else if`

```
if (조건식){
    동작문;
} else if (조건식){
    동작문;
} else {
    동작문;
}
```

**else if 문 뒤에 else 문이 반드시 나와야하는 것은 아니다. 단, if 문은 항상 처음에 나와야 한다.**

- 조건문도 문이기 때문에 중괄호 안에 다시 넣어서 `중첩 if 문`을 만들 수 있다. 하지만 중첩 if 조건문은 피하는게 좋다. `중첩 if 문은 논리적으로 if-else if-else 문으로 변환할 수 있다.` 가독성을 높이자.

- `switch` 조건문으로 분기하기

```
switch (조건식) {
    case 비교조건식1:
        동작문;
        break;
    case 비교조건식2:
        동작문;
        break;
    default:
        디폴트;
}
```

switch 옆 `소괄호의 조건식의 값이 case 의 비교 조건식 값과 일치(===)` 하면 해당 동작문이 실행된다. 보통 조건식에 변수를 넣고, 비교 조건식에는 변수와 비교할 값을 넣는다.

## 2-15. 조건부 연산자 (삼항 연산자)

**기본 형식 : `조건식 ? 참일 때 사용되는 식 : 거짓일 때 실행되는 식`**

- 조건부 연산자는 `문이 아니라 식이기 때문에 결과값이 나온다.`

- 조건부 연산은 보통 `조건에 따라 달라지는 값을 변수에 대입하기 위해 사용`한다.

- if 문으로 변경 가능하다.

- 조건부 연산도 `중첩해서 사용할 수 있다.`

```
5 > 0 ? '참' : '거짓'; // '참'
let value = 5 < 0 ? '참' : '거짓'; // undefined
value; // '거짓'

let condition1 = true;
let condition2 = false;
let value2 = condition1 ? (condition2 ? '둘 다 참' : 'condition1 만 참') : 'condition1 이 거짓';
console.log(value2);
// 'condition1 만 참'
```

## 2-16. 반복문 (while)

- 조건문과 더불어 가장 많이 쓰이는 문 중 `반복하는 동작을 처리하는 반복문`이 있다.

**while 문**

```
while(조건식){
    동작문;
}
```

- while 문은 `조건식이 참인 동안 반복해서 동작문을 실행`한다.

## 2-17. 반복문 (for)

**for 문**

```
for (시작; 조건식; 종료식){
    동작문;
}
```

- 시작 부분이 먼저 실행되고, `조건식 -> 동작문 -> 종료식 순으로 동작`한다.

- for 문의 `시작, 조건식, 종료식은 생략 가능`하다.

## 2-18. break 와 continue

- 반복문을 `중간에 멈춰야 하는 경우`가 있다. (예를 들어 값을 하나씩 찾다가 원하는 값을 찾아서 반복문을 멈추고 싶은 경우) 이런 경우 `break 문으로 반복문을 멈춘다.`

```
let i =0;
while(true){
    if(i===5) break;
    i++;
}
console.log(i); // 5
```

- 무한 반복을 표현할 땐 while 문을 더 많이 사용한다.

- 반복문이 `특정 조건에서만 실행`되기를 원할 수 있다. 이런 경우 `continue 문을 사용하여 코드를 건너뛸 수 있다.`

```
let i = 0;
while (i<10){ // 홀수만 console.log 하라는 반복문
    i++;
    if(i%2 === 0)
        continue;
    // 짝수인 경우 건너뛴다.
    console.log(i);
}
// 1 3 5 7 9
```

## 2-19. 중첩 반복문

- 반복문 안에 반복문이 있는 경우 `중첩 반복문`이라고 한다.

이중 반복문

```
for(let i= 0; i<10 ; i++)
    for(let j=0; j<10; j++)
        console.log(i, j);
```

삼중 반복문

```
for(let i=0; i<5; i++){
    if(i%2 === 0) continue;
    for(let j=0; j<5; j++){
        if(j%2 === 0) continue;
        for(let k=0; k<5; k++){
            if(k%2 === 0) continue;
            console.log(i, j, k);
        }
    }
}
실행 결과
1 1 1
1 1 3
1 3 1
1 3 3
3 1 1
3 1 3
3 3 1
3 3 3
```

## 2-20. 별찍기

```
마름모
for(let i = 1; i <= 5; i++ ){
  console.log(' '.repeat( 2- 5 % i ) + '*'.repeat(5 % i * 2+1))
}
```

```
산 모양
for(let i = 1, j = 0; i<=4; i++){
  	console.log(' '.repeat(4 - i) + '*'.repeat(i + j));
  	j = j + 1;
}
```

## 2-21. 배열 기본

**`객체 (object)`** 는 자료형의 일종으로 다양한 값을 모아둔 또 다른 값이다. 객체의 종류는 크게 `배열 (array)`, `함수 (function)`, `배열이나 함수가 아닌 객체`로 나눌 수 있다.

**배열**

- **배열**은 `다양한 값, 다양한 자료형들을 하나로 묶어둔 것`이다.

```
const apple = '사과';
const orange = '오렌지';
const pear = '배';
const strawberry = '딸기';
를 배열로 묶으면...
const fruits = ['사과','오렌지','배','딸기']
console.log(fruits[0]); // 사과
console.log(fruits[1]); // 오렌지
console.log(fruits[2]); // 배
console.log(fruits[3]); // 딸기
```

- 배열을 만들기 위해 `대괄호 ([]) 로 묶으면 되고`, 배열 안에 있는 각각의 값을 `요소 (element)` 라고 한다.

- 배열 내부의 값에 개별적으로 접근이 가능하다. `배열의 자리수 (index) 는 0 부터 시작한다.`

- 배열 안에 넣는 값에는 **제한이 없다.**

```
const arrayOfArray = [[1,2,3],[4,5]];
arrayOfArray[0]; // [1,2,3]

const a = 10;
const b = 20;
const variableArray = [a,b,30];
variableArray[1]; // 20

const everything = ['사과', 1, undefined, true, '배열', null];
const duplicated = ['가', '가', '가', '가', '가'];
const empty = [];
```

- arrayOfArray 배열은 배열 내부에 배열이 들어있다. 이러한 배열을 `이차원 배열` 이라고 한다.

- **배열의 요소 개수를 구할 땐, 배열 이름 뒤에 `.length` 를 붙이면 된다.**

```
const emptyValue = [null, undefined, false, '', NaN];
console.log(emptyValue.length);

결과
5
```

- **배열을 만든 후 중간에 배열을 수정할 수 있다. 요소를 `추가, 수정, 제거` 가능하다.**

```
1. 배열의 마지막에 요소 추가하기
const target = ['가', '나', '다', '라', '마'];
target[target.length] = '바';
console.log(target);

결과
(6) ['가', '나', '다', '라', '마', '바']

1-2. 배열의 마지막에 요소 추가하는 push
const target = ['가', '나', '다', '라', '마'];
target.push('바');
console.log(target);

결과
(6) ['가', '나', '다', '라', '마', '바']

2. 배열의 제일 앞에 값을 추가하는 unshift
const target = ['나', '다', '라', '마', '바'];
target.unshift('가');
console.log(target);

결과
(6) ['가', '나', '다', '라', '마', '바']
```

```
<참고> const 인데 수정이 가능한 이유..?

- const 가 엄밀히 상수는 아니라고 했었는데, const 에는 새로운 값을 대입 (=) 하지만 못한다고 기억하자. (통째로 재할당이 불가능)

- const 에 객체 (배열, 함수, 객체 리터럴) 가 대입된 경우 객체 내부의 속성이나 배열의 요소는 수정할 수 있다.

const target 2 = ['a', 'b', 'c', 'd', 'e'];
target2[0] = 'h'; // 객체의 내부는 바꿀 수 있으나
target2 = ['f', 'g']; // 객체를 통째로 바꾸는 것은 불가능
```

## 2-22 배열 메서드 (수정, 조회)

- **배열에서 중간 요소를 다룰 때는 주로 `splice` 기능**을 사용한다.

```
3. 배열에서 마지막 요소 제거하는 pop
const target = ['가', '나', '다', '라', '마'];
target.pop();
console.log(target);

결과
(4) ['가', '나', '다', '라']

4. 배열에서 첫번째 요소 제거하는 shift
const target = ['가', '나', '다', '라', '마'];
target.shift();
console.log(target);

결과
(4) ['나', '다', '라', '마']

5. 배열의 중간 요소 제거하기 -> splice 사용
const target = ['가', '나', '다', '라', '마'];
target.splice(1, 1);
console.log(target);

결과
(4) ['가', '다', '라', '마']
```

- `splice(a, b)` : index a 부터 b 개를 지운다.

- `splice (a)` : index a 부터 끝까지 다 지운다.

- `splice(a, b, c, d)` : index a 부터 b 개를 지우고 지워진 자리에 c 와 d 를 끼워넣는다.

```
splice 응용
const arr = ['가', '나', '다', '라', '마'];
arr.splice(2, 0, '바') // index 2 자리부터 0 개를 지우고 '바' 를 삽입
arr

결과
(6) ['가', '나', '바', '다', '라', '마']
```

- **배열에서 특정 요소가 있는지 찾기 위해 `includes` 기능**을 사용한다. 주어진 값이 내부에 존재하면 true 가 되고, 존재하지 않으면 false 가 된다.

- 검색하고 싶은 값이 **몇 번째 인덱스에 위치**하는지도 알 수 있다. `indexOf` 와 `lastIndexOf` 기능을 사용한다.

```
6. 특정 요소 찾는 includes
const target = ['가', '나', '다', '라', '마'];
const result = target.includes('다');
const result2 = target.includes('카');
console.log(result);
console.log(result2);

결과
true
false

7. 특정 요소 인덱스 위치 알 수 있는 indexOf, lastIndexOf
const target = ['라', '나', '다', '라', '다'];
const result = target.indexOf('다');
const result2 = target.lastIndexOf('라');
const result3 = target.indexOf('가');
console.log(result);
console.log(result2);
console.log(result3);

결과
2 // 앞에서 부터 찾는다
3 // 뒤에서부터 찾는다
-1 // 결과가 없으면 -1
```

## 2-23. 배열 메서드 응용하기

문제 : 다음 배열에서 '라' 를 모두 제거해라. indexOf 와 splice 를 사용해라.

```
const arr = ['가', '라', '다', '라', '마', '라'];
while(arr.indexOf('라')!=-1)
    arr.splice(arr.indexOf('라'),1);
arr;

결과
(3) ['가', '다', '마']
```

## 2-24. 함수 기본

- 프로그래밍에서 **`함수 (function) 는 일정한 동작을 수행하는 코드를 의미`**한다.

- 함수를 미리 만들어두고 원할 때 실행해서 정해진 동작을 수행하게 할 수 있는 것이다.

- **함수를 만들 때**는 보통 `function 예약어`를 사용하거나 `=> 기호`를 사용한다. 화살표 기호를 사용한 함수를 **화살표 함수 (arrow function)** 이라고 한다.

```
1. function a(){} // 함수 선언문
2. const b = function() {}; // 함수 표현식
3. const c = () => {}; // 화살표 함수
```

**함수 선언문 (function declaration statement)** : a 함수 처럼 함수를 상수에 대입하는 대신 function 키워드 뒤에 함수 이름을 넣어주는 방식

**함수 표현식 (function expression)** : 함수 b 처럼 상수나 변수에 대입하는 방식

- 변수와 마찬가지로 함수를 만드는 행위도 `선언한다 (declare)` 라고 표현한다.

- 위의 1, 2, 3 의 세 방식에는 큰 차이가 있지만 앞으로 새 개념이 등장할 때마다 배운다. (this 배울 때)

- 만든 함수를 사용하는 행위를 `호출한다 (call)` 라고 표현한다.

```
function a(){
    console.log('Hello');
    console.log('Function');
}
a();

결과
Hello
Function
```

**return 이해하기**

- 함수를 호출하면 항상 `결과값`이 나오는데, 기본적으로 `undefined` 가 나온다. 이 값을 `반환값 (return value)` 이라고 한다. return 이 나오면 `함수를 종료`하면서 `반환값을 준다.`

- `함수의 반환값도 값이므로 다른 식이나 문에 넣어 사용`할 수 있다. 함수의 반환값을 상수나 변수에 대입할 수 있다.

```
1. 값을 반환하는 역할
function a(){
    return 10;
}
console.log(a());

결과
10

2. 함수의 실행을 중간에 멈추는 역할
function a(){
    console.log('Hello');
    return;
    console.log('Return');
}
a();

결과
Hello
```

## 2-25. 매개변수 (parameter) 와 인수 (argument)

- 함수를 `선언할 땐 매개변수 (parameter)`, 함수를 `호출할 땐 인수 (argument)`

```
function a(parameter){
    console.log(parameter);
}
a('argument');

결과
(parameter = 'argument')
argument
```

- 함수가 하나의 매개변수와 하나의 인수만을 가지는 것은 아니고, 각각 **여러 개를 가질 수 있고**, **매개변수와 인수의 개수가 일치하지 않아도 된다.**

```
function a(w, x, y, z){
    console.log(w, x, y, z);
    console.log(arguments);
}
a('Hello', 'Parameter', 'Argument');

결과
Hello Parameter Argument undefined (짝 지어지는 게 없어서 undefined)
Arguments(3) ['Hello', 'Parameter', 'Argument']

function a(w, x){
    console.log(w, x);
}
a('Hello', 'Parameter', 'Argument');

결과
Hello Parameter (짝 지어지는게 없어서 무시됨)
```

- **인수가 몇 개 들어왔는지 알 수 있게 `arguments` 라는 특수한 값**을 사용할 수 있다. 이 값은 화살표 함수가 아닌 `function 에서만 사용 가능`하다. 이 값을 쓰면 넣었던 인수들을 배열 형태로 출력한다.

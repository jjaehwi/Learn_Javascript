# 1강

## 흔하게 발생하는 에러

**Uncaught ReferenceError: consle is not defined**

: console 입력 중에 오타를 내면 발생하는 에러. console 은 브라우저에서 제공하는 기능이기 때문에 오타가 나서는 안되고 `대소문자도 구분`하므로 모든 글자를 소문자로 적어야 한다.

**Uncaught TypeError: console.lg is not a function**

: log 에서 오타를 냈을 때 발생한 에러. log 는 console 의 기능 중 일부이기 때문에 오타가 있어서는 안되고 역시 `대소문자도 구별`한다. 마침표 (.) 는 자바스크립트에서 특수한 역할을 하는데, 객체를 배울 때 같이 배운다.

**Uncaught SyntaxError: missing ) after argument list**

: console.log() 중 () 로 감싸지 못해서 발생한 에러. (참고. () : parentheses, {} : braces, [] : brackets)

**Uncaught SyntaxError: Invalid or unexpected token**

: 따옴표를 사용하지 않았을 때 발생하는 에러. 'Hello, world!' 같은 문자는 `(백틱) 이나 '(작은따옴표) 또는 "(큰따옴표) 로 감싸줘야 한다. 당연히 시작과 끝의 따옴표 종류가 같아야한다.

## 참고

**인터프리터**

자바스크립트 코드를 콘솔에 입력하고 `Enter` 키를 누르면 결과가 바로 나온다. (undefined 가 그 결과) 이처럼 코드를 `한 덩어리씩 실행해 결과를 출력`하는 방식을 `인터프리터(interpreter)` 방식이라고 한다. 한 덩어리라고 표현한 잉는 `Shift + Enter` 키를 누르면 줄바꿈을 해 여러 줄의 코드를 동시에 입력할 수 있기 때문이다.

**컴파일**

자바스크립트와는 반대로 코드를 `컴퓨터가 이해할 수 있는 언어로 변환하는 과정을 거친 후 한번에 실행`하는 방식을 `컴파일(compile)` 방식이라고 한다. C 나 C++, 자바 등의 언어에서 이 방식을 사용한다.

**REPL**

브라우저의 콘솔은 코드를 한 줄씩 입력받고(Read), 받은 입력을 평가(Eval) 한 후, 결과를 출력(Print) 한다. 그 후 프롬프트가 나타나 새로운 입력을 기다린다.(Loop) 이러한 특성 때문에 `콘솔을 REPL(Read-Eval-Print-Loop)` 이라고 한다.

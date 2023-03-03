# 3강 DOM 객체 다루기 \_ 끝말잇기 게임

## 3-1. 순서도를 그리는 이유

1. 프로그램 절차의 개수는 정해져 있어야 한다.

2. 각 절차는 항상 같은 내용이어야 한다.

3. 모든 가능성을 고려해야 한다. (절차를 생각나는 대로 만들고 차차 보완한다)

4. 예시는 절차를 검증하는 데 사용한다.

- 끝말잇기 게임 절차 (번호스타일)

```
1. 게임에 몇 명이 참가할지를 선택한다.
2. 참가자 순서를 정한다 (편의상 숫자로 한다).
3. 첫 번째 사람이 어떤 단어를 말한다.
4. 다음 사람이 어떤 단어를 말한다.
5. 절차 4 에서 말한 단어가 올바른지 판단한다.
6. 올바르다면 그 다음 사람이 어떤 단어를 말한다.
7. 올바르지 않다면 틀렸다고 표시한다.
8. 게임을 계속 진행 (절차 4 로 이동) 한다.
```

- '몇' 이나 '어떤' 이라는 용어를 사용하여 다양한 경우에 대비할 수 있다.

## 3-2. 기본 VS Code 사용법

- 웹 게임은 브라우저에서 돌아가는 프로그램으로 `HTML`, `CSS`, `자바스크립트` 라는 언어를 사용한다.

**HTML** : 화면 요소 (입력창, 버튼, 글자 등) 를 담당

**CSS** : 요소의 디자인 담당

**자바스크립트** : 프로그램의 동작 담당

## 3-3. 대화창 (prompt, alert, confirm)

**prompt**

- `prompt` 는 `브라우저가 사용자로부터 입력을 받을 수 있는 수단` 이다.

- prompt 함수로 `입력받은 값은 모두 문자열`이 된다. 그래서 원하는 자료형으로 `변환해서 사용`해야한다.

```
<script>
    prompt('몇 명이 참가하나요?');
</script>
```

- 위의 코드를 입력하고 HTML 파일을 저장하고 실행하면 `대화 상자` 가 뜨면서 입력을 기다린다.

**alert**

- `alert` 는 `대화 상자 (경고창)` 이다.

- `사용자에게 경고 메세지를 표시`한다.

```
<script>
    const number = prompt('몇 명이 참가하나요?');
    alert(number);
</script>
```

**confirm**

- `confirm` 은 `확인, 취소가 있는 대화 상자`이다.

- 사용자의 확인을 요구하는 `확인, 취소 선택창`을 띄운다.

```
<script>
    const yerOrNo = confirm('okay?');
</script>
```

## 3-4. HTML 태그 선택하기 (querySelector)

- HTML 을 자바스크립트로 어떻게 조작할까? 입력창은 html 태그이므로 자바스크립트에서 이 입력창을 가져와야 한다.

- 자바스크립에서 HTML 태그를 가져오는 것을 `선택` 한다고 표현한다.

```
document.querySelector('선택자')
```

- **`선택자`** 는 `HTML 태그를 선택할 수 있게 도와주는 문자열`이다.

```
<script>
    const $input = document.querySelector('input'); // input 태그 선택
    console.log($input);

    const $button = document.querySelector('button'); // button 태그 선택
</script>
```

- 태그가 여러 개 있는 경우도 있다. 이 때, 태그를 모두 선택하고 싶다면 `document.querySelectorAll` 함수를 사용한다.

```
<script>
    const number = parseInt(prompt("몇 명이 참가하나요?"), 10);
    const $span = document.querySelectorAll("span");
    console.log($span);
</script>

결과
NodeList(2) [span#order, span#word]
```

- NodeList(2) 는 **배열처럼 보이지만 배열이 아니다.** 이는 `유사배열 객체 (Array-like Objects)`라고 한다. **key 가 숫자이고 length 값을 가지고 있는 객체**이다. 앞서 배웠던 argument 도 유사배열 객체 이다.

**`id`를 이용해 태그를 선택**

- `document.querySelector('#id')` 를 사용한다.

- 주의할 것은 자바스크립트는 `id 는 한 번만 나온다고 판단`하기 때문에 중복해서 쓰지 않는 것이 좋다 (**자바스크립트 입장에서 id 는 한 번만 나오는 고유한 값이다**).

```
document.querySelector('#word'); // id 가 word 인 태그를 찾는다
```

**`클래스`를 이용해 태그를 선택**

- `document.querySelectorAll('.className')` 을 사용한다. 전체가 아닌 여러개를 동시에 선택하고 싶을 때 class 를 써서 찾는 것을 추천한다.

```
<button>입력</button>
<button class = "btn">입력2</button>
<button class = "btn">입력3</button>

document.querySelectorAll('.btn') // 입력 2, 입력 3 버튼이 선택된다.
```

**`공백`을 이용해 태그를 선택**

- `document.querySelector('선택자 내부선택자 내부선택자 ...')` 처럼 선택자 사이에 공백 (띄어쓰기) 를 줘서 구분한다.

- 가장 먼저 나오는 선택자가 기준 태그이고, 다음에 나오는 선택자는 기준 태그 안에 들어 있는 태그를 가리킨다.

```
document.querySelector('div span'); // div 태그 안에 span 태그를 선택
document.querySelector('body #target button'); // body 태그 안에 id 가 target 인 태그에서 그 안에 있는 button 태그를 선택
```

**퀴즈** : a 태그 안에 id 가 b 인 태그 안에 class 가 c 인 태그를 선택하려면??

```
a #b .c
```

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

**순서도**

<img width="288" alt="스크린샷 2023-03-03 오후 11 27 10" src="https://user-images.githubusercontent.com/87372606/222745772-a13201b0-a9be-44be-ae43-141d1b2c464a.png">

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

## 3-5. 이벤트 리스너 달기 (콜백함수)

- HTML 이 화면을 만들어주면 사용자는 `이벤트를 통해서 상호작용` 한다.

- `querySelector 로 태그를 선택한 다음 .addEventListener('이벤트 이름', 리스너 함수);` 을 통해 이벤트가 발생했을 때 function 이 실행되도록 할 수 있다. **첫 번째 인수로 문자열, 두 번째 인수로 함수자리** 이다.

- **`리스너 함수 또는 콜백 함수 (callback function)` 는 어떤 동작이 실행되고 난 뒤에 연이어 실행되는 함수**

```
1.
태그.addEventListener('이벤트 이름', 리스너 함수);

2.
const onClick = function () {
    console.log('버튼 클릭'); // 버튼이 클릭 (click) 될 때마다 console 이 찍힌다.
}
document.querySelector('button').addEventListener('click', onClick);

3.
document
        .querySelector("input")
        .addEventListener("input", function (event) {
          console.log("글자 입력", event.target.value);
        });
// event.target.value에 사용자가 입력한 것이 들어가기 때문에, input 에 사용자가 입력을 할 때 어떤 글자가 입력되었는지 알 수 있다.
```

## 3-6. 첫 번째 사람인지 판단하기

```
const number = Number(prompt("몇 명이 참가하나요?"));
const $button = document.querySelector("button");
const $input = document.querySelector("input");

const onClickButton = () => {};
const onInput = (event) => {};

$button.addEventListener("click", onClickButton);
$input.addEventListener("input", onInput);
```

- 순서도 중 첫 번째 사람이 제시어를 말한다 부분에서 1. 첫 번째 사람인지 알아야하고, 2. 어떤 제시어를 말했는지 알아야한다.

- 첫 번째 참가자라면 입력된 단어가 제시어가 되는 것이고, 첫 번째 참가자가 아니라면 제시어가 이미 있는 상태에서 이어서 진행된 것이기 때문에 입력된 단어가 올바른지를 판단한다.

- 이런 식으로 처음 순서도에서 더 상세히 쪼개서 순서도를 구체화시킨다.

**순서도 수정**

<img width="410" alt="스크린샷 2023-03-03 오후 11 30 10" src="https://user-images.githubusercontent.com/87372606/222746443-48b78cbc-8d24-49b1-858e-b49ad59de889.png">

- `제시어 부분이 없는 것으로 첫 번째 참가자` 임을 알 수 있다.

- 제시어를 입력받고, 변수에 저장해야한다.

- 새로 입력한 단어를 입력받고, 변수에 저장해야한다.

- 첫 번째 사람이 입력하면 제시어가 채워지고 input 창이 지워져서 다음 입력을 받을 수 있게 된다.

- 제시어가 바뀌고 화면을 바꾸는 것은 `span 태그`를 가져와서 `textContent` 를 이용한다.

**순서도 수정**

<img width="410" alt="스크린샷 2023-03-03 오후 11 40 16" src="https://user-images.githubusercontent.com/87372606/222748808-5ca647bc-364d-4145-989f-4ed890672d56.png">

```
<script>
      const number = Number(prompt("몇 명이 참가하나요?"));
      const $button = document.querySelector("button");
      const $input = document.querySelector("input");
      const $word = document.querySelector("#word");
      let word; // 제시어
      let newWord; // 새로 입력한 단어

      const onClickButton = () => {
        // 제시어가 비어 있는가?
        if (!word) {
          // 비어 있다.
          word = newWord; // 입력한 단어가 제시어가 된다. (데이터를 바꾸고)
          $word.textContent = word; // 화면을 바꾼다.
          $input.value = ""; // input 안의 내용은 value 에 저장되어있다.
        } else {
          // 비어 있지 않다.
        }
      };
      const onInput = (event) => {
        newWord = event.target.value;
      };

      $button.addEventListener("click", onClickButton);
      $input.addEventListener("input", onInput);
    </script>
```

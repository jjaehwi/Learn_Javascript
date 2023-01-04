# 매뉴얼과 명세서

어느 정도 자바스크립트가 익숙해지면 튜토리얼 이외의 자료가 필요한 시점이 온다.

## 명세서

[ECMA-262 명세서(specification)](https://www.ecma-international.org/publications/standards/Ecma-262.htm)는 자바스크립트와 관련된 가장 심도 있고 상세한 정보를 담고 있는 공식 문서. 이 명세서에서 자바스크립트라는 언어를 정의한다.

ECMA-262 명세서의 고유한 형식 때문에 명세서를 처음 접하는 사람은 그 내용을 이해하기가 쉽지 않다. 자바스크립트에 관한 정보를 얻을 수 있는 가장 신뢰할 만한 자료이긴 하지만 일상적인 참고 자료로는 적합하지 않은 것.

ECMA-262명세서는 새로운 버전이 매년 나오는데, 공식 버전이 나오기 이전의 최신 초안은 <https://tc39.es/ecma262/>에서 확인.

갓 명세서에 등록된 기능이나 '등록되기 바로 직전'에 있는 기능(스테이지(stage)3 상태의 기능), 제안 목록은 <https://github.com/tc39/proposals>에서 확인.

## 매뉴얼

- Mozilla 재단이 운영하는 **MDN JavaScript Reference**엔 다양한 예제와 정보가 있다. 특정 함수나 메서드에 대한 깊이 있는 정보를 얻고 싶다면 이 사이트가 좋다.

  링크 : <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference>

  위 사이트에 들어가서 원하는 내용을 직접 검색하는 것도 좋지만, 가끔은 검색 엔진을 이용해 내용을 찾는 게 더 나을 때도 있다. Google 검색 엔진에 접속해 'MDN [원하는 용어]'를 입력. `parseInt` 함수에 대한 정보를 얻고 싶다면 <https://google.com/search?q=MDN+parseInt> 같이 검색하는 식.

## 호환성 표

자바스크립트는 끊임없이 발전하는 언어이다. 새로운 기능이 정기적으로 추가된다.

특정 브라우저나 엔진이 내가 사용하려는 기능을 지원하는지 확인할 땐, 아래 두 사이트가 좋다.

- <http://caniuse.com> 에선 브라우저가 특정 기능을 지원하는지 (표 형태로) 확인할 수 있다. 암호화 관련 기능인 cryptography를 특정 브라우저에서 사용할 수 있는지 아닌지를 보려면 <http://caniuse.com/#feat=cryptography>를 확인하면 된다.
- <https://kangax.github.io/compat-table> 에선 자바스크립트 기능 목록이 있고, 해당 기능을 특정 엔진이 지원하는지 여부를 거대한 표를 통해 보여줌.

실제 개발을 하다 보면 위에 언급 드린 자료가 아주 유용함. 메서드나 함수 관련 정보, 브라우저 지원 여부 등은 의사결정을 내릴 때 꼭 필요한 정보이기 때문이다.

사이트나 페이지를 기억해 놓았다가 특정 기능에 대한 상세한 정보가 필요할 때 방문하자.

## 요약

- 자바스크립트 명세서는 <https://tc39.es/ecma262/> 에서 확인이 가능하다.

- Mozilla 재단이 운영하는 MDN JavaScript Reference에 예제와 함께 정보를 제공한다. 필요한 용어를 검색할 때, "MDN [원하는 용어]" 를 검색해보는 것도 좋음.

- 자바스크립트는 계속해서 발전하기 때문에 브라우저(엔진)에서 해당 기능을 지원하는 지 확인을 해야한다.
  - <http://caniuse.com>
  - <https://kangax.github.io/compat-table>

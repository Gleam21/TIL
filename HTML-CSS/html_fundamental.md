# HTML 기초

html에 대해서 공부하면서 새로운 것들, 외워둘 것들 등등에 대해서 정리해 나가는 파일

## 0. 태그 모음

- 헤딩: `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>`
- 리스트: `<ol>`, `<ul>` 태그가 `<li>`를 여럿 포함. li에 새로운 ol, ul 태그를 할당해서 중첩 리스트 가능.
    + `<ol reverseed="reversed">` : 속성 지정하면 ol에서 번호가 역순이 된다.
    + `<ol start="10">` : 10부터 번호가 지정된다.
- 개념, 정의 구조
    + `<dl>` 태그로 전체를 감싼다.
    + `<dt>`: 개념, 단어 등을 의미하는 inline 속성
    + `<dd>`: 정의, 설명을 적는 block 속성
    + dt, dd가 꼭 1:1일 필요는 없다. 1:다, 다:1, 다:다 가능.
- `<a>`
    + `href`: 링크 지정. 속성 없이 사용하면 일반 텍스트처럼 보인다.
    + `title`: 링크의 설명이다. 접근성에 유용.
    + `target`: 현재 창에서 열지, 새 창에서 열지 등을 결정하는데 사용자의 선택이므로 아예 사용하지 않는걸 추천.
    + `href` 속성에 js 코드를 넣는 것은 지양한다. 꼭 주소를 지정하는 것이 좋고 js 코드를 사용해야 한다면 아래 코드처럼.

    ```html
    <a href="http://webberstudy.com" onclick="해당 스크립트">팝업 열기</a>
    ```

- `<img>`: `src` 속성으로 이미지 위치를 지정하고, `alt` 속성으로 이미지에 대한 설명을 적는다. 둘 모두 꼭 적어주는 거로. 부가적으로 `longdesc` 속성이 있는데 이미지에 대한 긴 설명이 필요할 경우 해당 텍스트 파일의 경로를 지정해준다.
- 강조: `<strong>` 태그는 텍스트 **볼드** 처리, `<em>` 태그는 _italicize_ 하는 것. 같은 효과로 i, b 태그가 있는데 사용을 추천하지 않음.
- 영역
    + `<section>`
    + `<article>`
    + `<div>`
    + `<p>` : 문단. 한 주제의 글 뭉치들을 넣으면 된다.
    + `<pre>` : 시 같은 특정한 형태가 있는 텍스트를 넣을 때. 공백이 다 적용된다.
- 표
    + `<table>` 태그로 전체를 감싼다.
    + 행을 뜻하는 `<tr>` 태그를 table 하위에 두고
    + 컬럼은 tr 태그 하위에 `<td>` 태그를 여러개 넣으면 된다.

    ```html
    <body>
      <table border="1px">
        <tr>
          <td>111</td>
          <td>222</td>
        </tr>
        <tr>
          <td>333</td>
          <td>444</td>
        </tr>
      </table>
    </body>
    ```

- Escape characters
    + `&nbsp;` `&#160;`: 한 칸 띄우기
    + `&amp;` `&#38;`: &
    + `&lt;` `&#60;`: <
    + `&#61;` : = 등호
    + `&gt;` `&#62;` : >
    + `&copy;` `&#169;`: 저작권 표시 C
- 인용
    + `blockquote`: block 속성.
    + `q`: inline 속성이다. 기본적으로 `" "` 쌍 따옴표로 표현되기 때문에 추가로 적지 않도록 한다.
    + `cite`: 속성으로 활용하면 웹에 표현되지 않고 검색엔진이 활용한다. 인용이 아니라 그냥 작품명을 언급하고 싶을 때 따로 쓰는데 자원을 나타내는 태그이기 때문에 작품명을 적어야지 사람 이름을 적으면 안된다. 

    ```html
    <p>다음 한 마디는 <cite>손규빈 어록</cite> 중 하나다.</p>
    <blockquote cite="https://www.facebook.com/gyubin.son">
      <p>'으아!!!'</p>
      <p>사실 어록이 없다.</p>
    </blockquote>

    <p><q cite="http://html5.clearboth.org/text-level-semantics.html#the-q-element">인용이 아닌 내용에 따옴표를 나타내기 위해 q 요소를 사용해서는 안됩니다.</q></p>
    ```

- `ins`, `del`: 추가 삭제된 부분 표시. GitHub에서 수정 부분 보여줄 때와 비슷한 모양이다. block, inline 속성을 모두 가지고 있어서 block 속성 태그 안에서 쓰이면 inline이 되고, 안에 다른 태그를 포함하는 형태로 쓰면 block 속성이 된다.

    ```html
    <!-- 인라인 형태 -->
    <p>매일 팔굽혀 펴기는 <del>50회</del> <ins>2회</ins> 실시한다.</p>
     
    <!-- 블럭 형태--> 
    <del>
      <p>매일 아침 새벽에 일어나 30분 조깅을 한다.</p>
      <p>식사는 고단백, 저열량으로 먹는다</p>
    </del>
    <ins>
      <p>아침에는 충분한 숙면을 취하도록 한다.</p>
      <p>먹을 것에 스트레스 받지 않도록 한다.</p>
    </ins>
    ```

## 1. 기본

- `meta` : 문서의 특성을 적어준다. 인코딩 방식이나 검색용 키워드
    + `<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">` 이렇게 주로 쓴다. 추가로 아래처럼 더 쓸 수도 있다.
    + `<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />`
    + `<meta name="Description" content="소개 내용" />` : 검색엔진에서 사이트 제목 아래쪽에 나오는 설명 부분
    + `<meta name="robots" content="noindex, nofollow" />` : 검색엔진이 이걸 보면 색인하지 않는다. 사적인 페이지로 사용할 때.
- `<!-- comment -->`: 주석
- class, id 규칙
    + 첫 글자는 알파벳으로. 두 번째 이후부터 `-`, `_` 사용 가능
    + 대소문자 구분
    + 단어 사이에 `-`를 넣어서 구분하고 모두 소문자로 쓰는 것을 추천.

## 2. 페이지 내부 스크롤 이동

```html
<a href="#history">1. 역사</a><br />
<a href="#markup">2. 마크업</a><br />

<h2><a id="history" href="history">역사</a></h2>
<h2 id="markup">마크업</h2>
```

- a의 href 속성에 `#`으로 시작하는 형태로 적어주면 된다. 원하는 곳의 id 값을 적어주면 된다.
- 해당 부분은 id 속성을 지정해주면 된다. 주로 헤딩을 이용.
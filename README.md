# 레진 마크업 가이드

레진 마크업 가이드는 유연하고 지속 가능한 코드 작성을 위한 사내 표준 문서입니다. 필요할 때마다 논의하여 지속적으로 업데이트합니다.

레진 마크업 가이드는 [Code Guide by @mdo](http://mdo.github.io/code-guide)를 기반으로 작성했습니다. @mdo의 가이드에 포함된 내용이라도 상식에 준하는 내용들과 지나치게 장황한 내용은 제거했으며 팀내에서 새롭게 논의한 내용을 추가했습니다.

## 기본 규칙

W3C 문법과 레진 마크업 가이드라인을 지켜 코드를 작성합니다. 수정해야 할 내용이 있다면 팀내에서 논의하여 문서를 업데이트합니다. 많은 사람이 참여했더라도 한명이 쓴 것처럼 보이는 코드가 좋습니다.

### HTML

#### HTML 문법 <a id="h1" href="#h1">#</a>

* 들여쓰기는 공백문자 4 개를 사용합니다.
* 속성(attr)값에는 항상 큰 따옴표를 사용합니다.
* 단일 태그에는 슬래시(`/`)를 사용하지 않습니다. (예: `<br />` or `<img />`)

` `

    <!DOCTYPE html>
    <html>
        <head>
            <title>Page title</title>
        </head>
        <body>
            <img src="logo.png" alt="Lezhin">
            <h1 class="hello-world">Hello, world!</h1>
        </body>
    </html>


### HTML5 doctype <a id="h2" href="#h2">#</a>
모든 HTML 페이지 시작 지점에 공백 없이 HTML5 문서 타입을 선언합니다.

    <!DOCTYPE html>
    <html>
        <head>
        </head>
    </html>

### 언어(lang) 속성 <a id="h3" href="#h3">#</a>
문서 루트인 `html` 요소에 `lang` 속성을 추가합니다.
* 영어: `en`
* 한국어: `ko`
* 일본어: `ja`

` `

        <html lang="ko">
            ...
        </html>

### 인코딩 설정 <a id="h4" href="#h4">#</a>
문자열 인코딩을 명시적으로 선언합니다.

    <head>
        <meta charset="UTF-8">
    </head>

### IE 호환모드 설정 <a id="h5" href="#h5">#</a>
인터넷 익스플로러가 항상 최신 버전의 레이아웃 엔진을 사용하여 문서를 렌더링하도록 지정합니다.

    <meta http-equiv="X-UA-Compatible" content="IE=Edge">

### CSS, JavaScript 삽입 <a id="h6" href="#h6">#</a>
CSS와 JavaScript를 불러올 때 `type` 속성을 생략합니다.

    <!-- External CSS -->
    <link rel="stylesheet" href="code-guide.css">

    <!-- In-document CSS -->
    <style>...</style>

    <!-- JavaScript -->
    <script src="code-guide.js"></script>

### 속성(attr) 순서 <a id="h7" href="#h7">#</a>
HTML 태그 속성은 가독성을 위해 아래 순서대로 작성합니다.

1. 선택자로 사용하는 `id`, `class` 속성은 가장 앞에 선언합니다.
2. 콘텐츠를 설명하는 `alt`, `title`, `role`, `aria-*` 속성은 가장 뒤에 선언합니다.

` `

    <a id="..." class="..." href="#">Example link</a>
    <input class="form-control" type="text">
    <img src="..." alt="..." title="...">

### Boolean 속성 <a id="h8" href="#h8">#</a>
불리언 속성의 값은 지정하지 않습니다.

    <input type="text" disabled>
    <input type="checkbox" value="1" checked>
    <option value="1" selected>1</option>

### 마크업 간결화 <a id="h9" href="#h9">#</a>
모듈화를 고려하여 마크업은 간결하게 작성합니다.

    <!-- Not so great -->
    <span class="avatar">
        <img src="..." alt="...">
    </span>

    <!-- Better -->
    <img class="avatar" src="..." alt="...">

### 문서 개요(HTML5 아웃라인) <a id="h10" href="#h10">#</a>
섹셔닝 요소와 헤딩 요소를 이용하여 문서 개요를 논리적으로 구성합니다. 섹셔닝 요소(`section`, `article`, `nav`, `aside`)에는 헤딩 요소를 명시적으로 사용합니다. 명시적 헤딩 기법은 `h1` 요소를 한 페이지에 한 번 사용합니다. 헤딩 요소만으로 문서 개요를 파악할 수 있어야 합니다.

    <!-- Bad HTML -->
    <body>
        <h1>동물</h1>
        <div>
            <h1>포유류</h1>
            <div>
                <h1>고래</h1>
            </div>
        </div>
    </body>

    <!-- Good HTML -->
    <body>
        <h1>동물<h1>
        <article>
            <h2>포유류<h2>
            <section>
                <h3>고래<h3>
            </section>
        </article>
    </body>

### 완벽함보다는 실용성을 추구 <a id="h11" href="#h11">#</a>
HTML 표준을 준수하고 시맨틱한 문서를 작성하기 위해 노력하기는 하지만 추가적인 노력이 필요하지 않은 범위내에서만 합니다. 최대한 간결한 코드를 사용하도록 합니다.


## CSS

### CSS 문법 <a id="c1" href="#c1">#</a>
* 들여쓰기는 공백문자 4 개를 사용합니다.
* 쉼표(`,`)를 사용하여 선택자를 그룹핑하는 경우 쉼표 뒤에서 개행합니다.
* 여는 중괄호(`{`) 앞에 공백을 한칸 놓습니다.
* 닫는 중괄호(`}`)는 새로운 줄에 놓습니다.
* 속성 선언 시 콜론(`:`) 뒤에는 공백문자 하나를 포함시킵니다.
* 한 줄에 하나의 속성만 작성합니다.
* 모든 속성 선언은 마지막에 세미콜론(`;`)으로 끝냅니다.
* 다중 속성값들은 콤마 뒤에 공백문자를 포함합니다.(예: `box-shadow`).
* `rgb()`, `rgba()` 값의 괄호 안에서는 콤마 뒤 공백문자를 넣지 않습니다.
* 속성값에 소숫점을 사용할 때 `0.`을 사용하지 않습니다.(예: `0.5`대신 `.5`를, `-0.5px`대신 `-.5px`)
* 축약 가능한 16진수 값은 축약합니다. (예: `#ffffff` 대신 `#fff`)
* 속성값들에는 홑따옴표를 사용합니다. (예: `[type='text']`)
* 값이 `0`일 때는 단위를 생략합니다. (예: `margin: 0px;` 대신 `margin: 0;` 사용)

` `

    /* Bad CSS */
    .selector,.selector-secondary,.selector[type=text]{
        padding:15px;
        margin:0px 0px 15px;
        background-color:rgba(0, 0, 0, 0.5);
        box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
    }

    /* Good CSS */
    .selector,
    .selector-secondary,
    .selector[type='text'] {
        padding: 15px;
        margin-bottom: 15px;
        background-color: rgba(0,0,0,.5);
        box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
    }

### 속성(property) 선언 순서 <a id="c2" href="#c2">#</a>
포지셔닝과 박스모델 관련 속성을 가장 먼저 작성하고 나머지는 뒤에 놓습니다.

    .declaration-order {

        /* Positioning */
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        z-index: 100;

        /* Box-model */
        display: block;
        float: right;
        flex: 1;
        width: 100px;
        height: 100px;

        /* Typography */
        font: normal 13px "Helvetica Neue", sans-serif;
        line-height: 1.5;
        color: #333;
        text-align: center;

        /* Background */
        background-color: #f5f5f5;

        /* Border */
        border: 1px solid #e5e5e5;
        border-radius: 3px;

        /* etc */
        opacity: 1;
    }

### 미디어 쿼리 위치 <a id="c3" href="#c3">#</a>
미디어쿼리는 관련 규칙이 있는 자리에 모아 놓습니다.

    .element { ... }
    .element-avatar { ... }
    .element-selected { ... }

    @media (min-width: 480px) {
        .element { ... }
        .element-avatar { ... }
        .element-selected { ... }
    }

### 단일 속성 작성 <a id="c4" href="#c4">#</a>
하나의 속성만 포함한다면 개행하지 않습니다.

    /* Single declarations on one line */
    .span1 { width: 60px; }
    .span2 { width: 140px; }
    .span3 { width: 220px; }

    /* Multiple declarations, one per line */
    .sprite {
        display: inline-block;
        width: 16px;
        height: 15px;
        background-image: url(../img/sprite.png);
    }

### Sass 중첩 구문 사용 <a id="c5" href="#c5">#</a>
과도하게 중첩하지 않습니다. 선택자 반복을 피하는 용도로만 중첩을 사용하십시오.

    // Without nesting
    .table > thead > tr > th { … }
    .table > thead > tr > td { … }

    // With nesting
    .table > thead {
        > th { … }
        > td { … }
    }

### Sass 계산식 사용 <a id="c6" href="#c6">#</a>
계산식에 괄호를 사용합니다.

    // Bad example
    .element {
        margin: 10px 0 @variable*2 10px;
    }

    // Good example
    .element {
        margin: 10px 0 (@variable * 2) 10px;
    }

### 주석 <a id="c7" href="#c7">#</a>
주석은 간결하게 작성합니다. scss 파일은 한 줄 주석(`//`) 사용이 가능하지만 CSS 파일에 남지 않습니다.

    /* Bad example */
    /* Modal - Wrapping element for .modal-header, .modal-body, modal-footer  */
    .modal {
        ...
    }

    /* Good example */
    /* Modal */
    .modal {
        ...
    }

### 클래스 작명 <a id="c8" href="#c8">#</a>
* 클래스 이름 규칙은 [BEM(Block Element Modifier)](http://getbem.com/naming/)스타일을 따릅니다.
* 클래스 이름은 소문자, 숫자, 대시(`-`), 언더스코어(`_`)를 사용합니다. 카멜 케이스와 파스칼 케이스는 사용하지 않습니다.
* 짧고 간결하게 작성하되 축약하지 않습니다. `.btn`과 같이 쉽게 의미를 유추 할 수 있는 축약은 괜찮지만 `.bn`와 같이 의미를 파악하기 어려운 축약은 사용하지 않습니다.
* 시각적 표현 대신 의미, 구조, 목적을 담아 작명합니다.
* 변화 또는 상태를 나타내는 추가 클래스는 블록 또는 요소 이름에 더블 대시(`--`)를 붙여 작명합니다.

` `

    /* Bad example */
    .sform { ... }
    .themeLezhin { ... }
    .sf-input { ... }
    .sf-btn { ... }
    .SearchformButtonDisabled { ... }

    /* Good example */
    .search-form { ... }                    // Block
    .search-form--theme-lezhin { ... }      // Block--Modifier
    .search-form__input { ... }             // Block__Element
    .search-form__btn { ... }               // Block__Element
    .search-form__btn--disabled { ... }     // Block__Element--Modifier

### 선택자 <a id="c9" href="#c9">#</a>
* 타입 선택자를 사용하지 않습니다. 클래스 선택자를 사용합니다.
* 선택자 우선순위(specificity)를 높이는 조합과 중첩을 사용하지 않습니다. 조합과 중첩은 3회를 초과하지 않습니다.
* 여러 클래스를 묶을 때 쉼표 후 개행합니다.

` `

    /* Bad example */
    section.tweet > header { ... }
    section.tweet > header.tweet__header { ... }
    .tweet > .tweet__header, .tweet > .tweet__username { ... }

    /* Good example */
    .tweet { ... }
    .tweet__header,
    .tweet__username { ... }

### 구성 <a id="c10" href="#c10">#</a>
* 컴포넌트 별로 코드를 모아서 작성합니다.
* 계층 구조의 순서에 따라 작성합니다.
* 코드 블럭을 분리할 때 공백(줄 바꿈)을 일관성 있게 사용합니다.
* 여러개의 *.scss 파일을 나눌 때, 페이지보다는 컴포넌트 별로 나눕니다.

` `

    /* Modal: modal.scss */
    .modal { ... }
    .modal__header { ... }
    .modal__body { ... }
    .modal__footer { ... }
    .modal__footer--disabled { ... }

### 에디터 설정 <a id="c11" href="#c11">#</a>
규칙을 준수하기 위해 에디터 환경을 설정해 둡니다.

* 들여쓰기는 공백문자 4개로 합니다.
* 파일 저장 시 마지막에 오는 공백문자를 제거합니다.
* 파일 저장 시 UTF-8 인코딩으로 저장합니다.
* 파일의 맨 마지막은 줄바꿈으로 끝납니다.


---

### License

Released under MIT by, and copyright 2014, @mdo and @lezhin

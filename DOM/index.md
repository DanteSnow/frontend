# DOM의 정의와 역할

![](https://velog.velcdn.com/images/clydehan/post/9394557b-a5a5-4452-a9b6-0dc6ea22379f/image.png)

> 이미지 출처: [링크](https://poiemaweb.com/js-dom)

## 정의 및 역할

DOM은 "Document Object Model"의 약자로, HTML 문서의 구조를 표현하는 객체 모델이다. 브라우저가 HTML 문서를 로드하면 이를 파싱하여 DOM 트리를 생성하고, 자바스크립트를 통해 이 트리를 조작할 수 있다. (꼭 자바스크립로만 DOM을 다룰 수 있는 것은 아니다.)

> 🌸 파싱(Parsing)이란?
> 파싱은 컴퓨터 프로그램이 텍스트 데이터를 분석하고 구조화하는 과정이다. 웹 브라우저의 경우, HTML 파일을 받아서 이를 분석해 DOM 트리로 변환하는 과정을 의미한다.

---

## 브라우저가 HTML 문서를 파싱하여 DOM 트리를 생성하는 과정

브라우저는 HTML 텍스트를 파싱하고, 이를 토큰으로 분리한 다음, 토큰을 기반으로 DOM 트리를 생성한다. 이 DOM 트리는 자바스크립트를 통해 조작할 수 있는 구조화된 형태로 브라우저에 저장된다.

### 예시 코드

아래 예시 코드를 통하여 브라우저가 HTML 문서를 파싱하여 DOM 트리를 생성하는 과정을 단계별로 설명한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Page</title>
  </head>
  <body>
    <h1>Welcome</h1>
    <p>This is a paragraph.</p>
  </body>
</html>
```

### HTML 파일 로드

- 사용자가 웹 페이지를 요청하면, 서버는 HTML 파일을 브라우저로 전송한다. 브라우저는 이 HTML 파일을 받게 된다.
- 예시 코드에서 브라우저는 `<!DOCTYPE html>`을 읽고 HTML5 문서임을 인식한다.

> 📌 `<!DOCTYPE html>`

<!DOCTYPE html>은 문서 타입 선언(Document Type Declaration)으로, 브라우저에게 이 문서가 HTML5로 작성되었음을 알려준다. 이 태그는 DOM 트리의 일부가 아니며, 파싱 과정에서 브라우저가 HTML5 표준을 준수하도록 한다.

### HTML 파싱 시작

- 브라우저는 HTML 파일의 내용을 처음부터 한 줄씩 읽는다. 이 과정을 파싱이라고 한다.
- 예시 코드에서 `<html>` 태그를 만나서 DOM 트리의 루트 노드를 생성한다.

> 📌 `<html>`
> `<html>` 태그는 HTML 문서의 최상위(root) 요소를 나타낸다. DOM 트리에서 문서 노드(document node)의 자식으로 존재하며, 모든 다른 요소들의 부모 요소가 된다. 노드 타입은 요소 노드(Element Node)이다.

### 토큰화 (Tokenization)

- 파서(parser)는 HTML 텍스트를 토큰(token)으로 분리한다. 토큰은 HTML 태그와 텍스트 조각을 의미한다.
- 예시 코드에서 `<html>`, `<head>`, `<title>` 등의 태그를 토큰으로 분리한다.

> 📌 `<head>`
> `<head>` 태그는 문서의 메타데이터(meta-information)를 포함한다. 메타데이터는 문서의 제목, 스타일, 스크립트, 링크된 리소스 등을 포함하며, 화면에 직접 표시되지 않는다. 노드 타입은 요소 노드(Element Node)이다.

### 속성과 텍스트 노드 처리

- 요소 노드(Element Node) 외에도, 요소 안의 텍스트는 텍스트 노드(Text Node)로, 요소의 속성은 속성 노드(Attribute Node)로 처리된다.
- 예시 코드에는 없지만, `<a href="https://example.com">Link</a>`는 a 요소 노드, href 속성 노드, Link 텍스트 노드로 구성된다.

### DOM 트리 생성

- 토큰을 읽으면서 브라우저는 DOM 트리를 생성한다.
- DOM 트리는 HTML 문서의 구조를 반영하는 계층적 트리 구조이다. (아래에서 더 자세하게 다룬다.)
- 각 HTML 태그는 DOM 트리의 노드가 된다. `<html>` 태그는 DOM 트리의 루트 노드(root node)가 되고, 그 안에 `<head>`와 `<body>` 태그가 자식 노드(child nodes)로 추가된다.

> 📌 `<body>`
> `<body>` 태그는 문서의 본문 내용을 포함한다. 사용자가 브라우저에서 볼 수 있는 모든 콘텐츠가 여기에 포함된다. 노드 타입은 요소 노드(Element Node)이다.

### 트리 구조

DOM 트리는 부모-자식 관계로 구성된다. 예시 코드의 결과적인 DOM 트리는 아래와 같다.

```markdown
- html
  - head
    - title
      - "My Page"
  - body
    - h1
      - "Welcome"
    - p
      - "This is a paragraph."
```

---

# DOM 트리 구조

![](https://velog.velcdn.com/images/clydehan/post/bf7e4c0a-0850-40c9-b45f-20b6d86308b5/image.png)

> 이미지 출처: [코드스테이츠](https://www.codestates.com/blog/content/dom-javascript)

```markdown
- document (문서 노드)
  - html (요소 노드)
    - head (요소 노드)
      - title (요소 노드)
        - "Document Node Example" (텍스트 노드)
    - body (요소 노드)
      - h1 (요소 노드)
        - "Welcome" (텍스트 노드)
      - p (요소 노드)
        - "This is a paragraph." (텍스트 노드)
```

DOM 트리는 다양한 종류의 노드로 구성된다. 각각의 노드는 특정한 역할과 특징을 가지고 있다. 주요 노드의 종류와 구조는 아래와 같다.

## 요소 노드 (Element Node)

### 정의 및 역할

요소 노드는 HTML 태그를 나타내며, DOM 트리에서 문서의 구조를 구성하는 기본 단위이다. 모든 HTML 태그는 요소 노드로 변환되며, 속성(attributes)을 가질 수 있다.

다른 노드를 포함할 수 있는 컨테이너 역할을 하며, 문서의 계층적 구조를 정의하고, 텍스트, 속성, 다른 요소 노드 등을 포함할 수 있다. 아래 예시 코드에서 `<div>`, `<p>`, `<a>` 태그가 모두 요소 노드이다.

### 예시 코드

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Element Node Example</title>
  </head>
  <body>
    <div id="container">
      <p>This is a paragraph.</p>
      <a href="https://example.com">This is a link.</a>
    </div>
  </body>
</html>
```

> 📌 `<script>`
> `<script>` 태그는 자바스크립트 코드를 포함하거나 외부 자바스크립트 파일을 로드하는데 사용된다. 이 태그는 일반적으로 `<head>` 또는 `<body>` 안에 위치하며, 자바스크립트 코드를 실행하는 역할을 한다. 노드 타입은 요소 노드(Element Node)이다.

## 텍스트 노드 (Text Node)

### 정의 및 역할

텍스트 노드는 요소 노드 안의 텍스트 내용을 나타낸다. 텍스트 노드는 DOM 트리의 말단(leaf) 노드로, 더 이상 자식 노드를 가질 수 없다.

요소 노드 내의 텍스트 콘텐츠를 저장하며, 사용자에게 보이는 텍스트 정보를 제공한다. 아래 예시 코드의 `<p>` 요소 안의 `Hello World`가 텍스트 노드이다.

### 예시 코드

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Text Node Example</title>
  </head>
  <body>
    <div id="container">
      <p>This is a paragraph.</p>
    </div>
    <script>
      // 텍스트 노드 접근
      let paragraph = document.querySelector("p");
      let textNode = paragraph.firstChild; // "This is a paragraph."
      console.log(textNode.nodeValue); // 출력: "This is a paragraph."
    </script>
  </body>
</html>
```

## 속성 노드 (Attribute Node)

### 정의 및 역할

속성 노드는 요소 노드의 속성을 나타내며, 이름(name)과 값(value)을 가진다. 속성 노드는 요소 노드의 일부로 취급되며, 독립적으로 존재하지 않는다.

요소 노드의 추가적인 정보를 제공하며, 요소의 동작과 스타일을 정의하거나 식별 목적으로 사용된다. 아래 예시 코드의 `<a href="https://example.com" id="link">This is a link.</a>`에서 `href="https://example.com"`과 `id="link"` 부분이 속성 노드이다. `href` 속성은 링크의 목적지를 정의하고, `id` 속성은 요소를 고유하게 식별한다.

### 예시 코드

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Attribute Node Example</title>
  </head>
  <body>
    <a href="https://example.com" id="link">This is a link.</a>
    <script>
      // 속성 노드 접근 및 변경
      let link = document.getElementById("link");
      let hrefValue = link.getAttribute("href"); // "https://example.com"
      console.log(hrefValue); // 출력: "https://example.com"

      link.setAttribute("href", "https://newurl.com"); // href 속성 변경
      console.log(link.getAttribute("href")); // 출력: "https://newurl.com"
    </script>
  </body>
</html>
```

## 문서 노드 (Document Node)

### 정의 및 역할

문서 노드는 DOM 트리의 최상위 노드로서 전체 HTML 문서를 나타내는 객체이다. 문서의 루트 요소인 `<html>` 태그와 그 자손들을 포함한 전체 구조를 관리한다. `documnet` 객체가 문서 노드를 대표한다. 자바스크립트에서 `document` 객체는 이 문서 노드를 대표한다. 모든 DOM 조작은 이 `document` 객체를 통해 이루어진다.

문서 노드는 DOM 트리의 루트 노드(root node)로, 모든 다른 노드들의 부모 또는 조상 노드 역할을 한다. 브라우저에서 DOM에 접근하기 위한 전역 접근점을 제공한다. 이를 통해 페이지의 모든 요소에 접근하고 조작할 수 있다.

아래는 문서 노드를 쉽게 이해하기 위한 예시 코드들과 `document` 객체를 사용하여 HTML 문서의 요소들에 접근하고 조작하는 과정이다. 그리고 자바스크립트에서는 `document.getElementById` 메서드를 사용해 `<h1>` 요소와 `<button>` 요소를 선택하고, 버튼을 클릭했을 때 제목의 텍스트를 변경하는 이벤트 리스너를 추가하는 등의 문서 노드를 활용했다.

### 예시 코드

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Node Example</title>
  </head>
  <body>
    <h1>Welcome</h1>
    <p>This is a paragraph.</p>
  </body>
</html>
```

#### 예시 코드의 DOM 트리 구조

```markdown
- document (문서 노드)
  - html (요소 노드)
    - head (요소 노드)
      - title (요소 노드)
        - "Document Node Example" (텍스트 노드)
    - body (요소 노드)
      - h1 (요소 노드)
        - "Welcome" (텍스트 노드)
      - p (요소 노드)
        - "This is a paragraph." (텍스트 노드)
```

#### `document` 객체를 통한 DOM 조작 예시

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document Node Example</title>
  </head>
  <body>
    <h1 id="title">Welcome</h1>
    <p>This is a paragraph.</p>
    <button id="changeTitle">Change Title</button>
  </body>
</html>
```

#### 자바스크립트 예시

```js
// document 객체를 통해 DOM에 접근하고 조작하는 예시

// 제목 요소 선택
let titleElement = document.getElementById("title");

// 버튼 요소 선택
let buttonElement = document.getElementById("changeTitle");

// 클릭 이벤트 리스너 추가
buttonElement.addEventListener("click", function () {
  // 제목 요소의 텍스트 내용 변경
  titleElement.textContent = "Title has been changed!";
});
```

---

# DOM API와 조작 방법

## DOM API란?

DOM API(Document Object Model Application Programming Interface)는 자바스크립트가 웹 페이지의 구조와 내용을 동적으로 조작할 수 있도록 브라우저가 제공하는 프로그래밍 인터페이스 집합이다. DOM API는 웹 페이지의 요소를 선택하고, 수정하고, 이벤트를 처리하는 등 다양한 작업을 수행할 수 있게 해주며, 이를 통해 사용자와 상호작용하는 동적인 웹 페이지를 만들 수 있게 된다.

## 주요 메서드와 속성

### `document.querySelector(selector)`

```html
<div class="example">First div</div>
<div class="example">Second div</div>
<script>
  let firstDiv = document.querySelector(".example");
  console.log(firstDiv.textContent); // 출력: "First div"
</script>
```

- CSS 선택자를 사용해 일치하는 첫 번째 요소를 반환한다. 특정 요소를 선택하고 조작할 때 사용한다.

---

### `document.querySelectorAll(selector)`

```HTML
<div class="example">First div</div>
<div class="example">Second div</div>
<script>
  let allDivs = document.querySelectorAll('.example');
  allDivs.forEach(div => console.log(div.textContent));
  // 출력: "First div", "Second div"
</script>

```

- CSS 선택자를 사용해 일치하는 모든 요소를 NodeList로 반환한다. 여러 요소를 선택하고 조작할 때 사용한다.

---

### `document.getElementById(id)`

```html
<div id="header">This is the header</div>
<script>
  let header = document.getElementById("header");
  console.log(header.textContent); // 출력: "This is the header"
</script>
```

- 주어진 ID를 가진 요소를 반환한다. 특정 ID를 가진 요소를 빠르게 선택할 때 사용한다.

---

### `document.createElement(tagName)`

```html
<div id="container"></div>
<script>
  let container = document.getElementById("container");
  let newParagraph = document.createElement("p");
  newParagraph.textContent = "This is a new paragraph.";
  container.appendChild(newParagraph);
  console.log(container.innerHTML); // 출력: "<p>This is a new paragraph.</p>"
</script>
```

- 주어진 태그 이름을 가진 새로운 요소를 생성한다. 동적으로 새로운 요소를 생성할 때 사용한다.

---

### `element.textContent`

```html
<div id="content">Old text</div>
<script>
  let content = document.getElementById("content");
  console.log(content.textContent); // 출력: "Old text"
  content.textContent = "New text";
  console.log(content.textContent); // 출력: "New text"
</script>
```

- 요소의 텍스트 내용을 가져오거나 설정한다. 요소의 텍스트를 읽거나 변경할 때 사용한다.

---

### `element.innerHTML`

```html
<div id="container">Old content</div>
<script>
  let container = document.getElementById("container");
  console.log(container.innerHTML); // 출력: "Old content"
  container.innerHTML = "<p>New paragraph</p>";
  console.log(container.innerHTML); // 출력: "<p>New paragraph</p>"
</script>
```

- 요소의 HTML 내용을 가져오거나 설정한다. 요소의 내부 HTML을 읽거나 변경할 때 사용한다.

---

### `element.setAttribute(name, value)`

```html
<a href="https://example.com" id="link">Example Link</a>
<script>
  let link = document.getElementById("link");
  link.setAttribute("href", "https://newurl.com");
  console.log(link.getAttribute("href")); // 출력: "https://newurl.com"
</script>
```

- 요소의 속성을 설정한다. 요소의 속성을 동적으로 설정할 때 사용한다.

---

### `element.appendChild(node)`

```html
<div id="container"></div>
<script>
  let container = document.getElementById("container");
  let newParagraph = document.createElement("p");
  newParagraph.textContent = "This is a new paragraph.";
  container.appendChild(newParagraph);
  console.log(container.innerHTML); // 출력: "<p>This is a new paragraph.</p>"
</script>
```

- 요소의 자식으로 새로운 노드를 추가한다. DOM 트리에 새로운 요소를 동적으로 추가할 때 사용한다.

---

### `element.removeChild(node)`

```html
<div id="container">
  <p>This will be removed</p>
</div>
<script>
  let container = document.getElementById("container");
  let paragraph = container.querySelector("p");
  container.removeChild(paragraph);
  console.log(container.innerHTML); // 출력: ""
</script>
```

- 요소의 자식 노드를 제거한다. DOM 트리에서 요소를 동적으로 제거할 때 사용한다.

---

## 그 외 자주 사용하는 DOM 메서드

DOM 트리에서 노드를 탐색하는 다양한 메서드들이 있다. 이러한 메서드를 사용하면 특정 노드를 쉽게 찾고 조작할 수 있다.

### parentNode

현재 노드의 부모 노드를 반환한다.

### firstChild

현재 노드의 첫 번째 자식 노드를 반환한다.

### lastChild

현재 노드의 마지막 자식 노드를 반환한다.

### nextSibling

현재 노드의 다음 형제 노드를 반환한다.

### previousSibling

현재 노드의 이전 형제 노드를 반환한다.

### 예시 코드

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Node Traversal Example</title>
  </head>
  <body>
    <div id="container">
      <p id="first">First paragraph</p>
      <p id="second">Second paragraph</p>
      <p id="third">Third paragraph</p>
    </div>
    <script>
      let container = document.getElementById("container");

      // firstChild와 lastChild 예시
      let firstParagraph = container.firstChild.nextSibling; // 첫 번째 자식 노드를 반환
      console.log(firstParagraph.textContent); // 출력: "First paragraph"

      let lastParagraph = container.lastChild.previousSibling; // 마지막 자식 노드를 반환
      console.log(lastParagraph.textContent); // 출력: "Third paragraph"

      // parentNode 예시
      let parent = firstParagraph.parentNode;
      console.log(parent.id); // 출력: "container"

      // nextSibling과 previousSibling 예시
      let secondParagraph = firstParagraph.nextSibling.nextSibling;
      console.log(secondParagraph.textContent); // 출력: "Second paragraph"

      let previousParagraph = secondParagraph.previousSibling.previousSibling;
      console.log(previousParagraph.textContent); // 출력: "First paragraph"
    </script>
  </body>
</html>
```

# HTML과 JavaScript 파일 분리하기

위의 예시 코드들에서는 HTML 파일 내에 인라인으로 자바스크립트를 작성했다. 하지만 일반적으로는 자바스크립트를 HTML 파일 내에 인라인으로 작성하기보다는 별도의 .js 파일로 분리해서 작성하는 것이 더 좋고 권장되는 방법이다. 이렇게 하면 코드의 유지보수와 가독성이 더 좋아지고, 여러 HTML 파일에서 재사용하기도 쉬워진다.

## 예시 코드

### HTML 파일 (`index.html`)

```html
<!DOCTYPE html>
<html>
  <head>
    <title>DOM and Event Handling Example</title>
    <link rel="stylesheet" type="text/css" href="styles.css" />
  </head>
  <body>
    <h1 id="title">Welcome</h1>
    <p>This is a paragraph.</p>
    <button id="changeTitle">Change Title</button>

    <!-- 자바스크립트 파일을 포함 -->
    <script src="script.js"></script>
  </body>
</html>
```

### JavaScript 파일 (`script.js`)

```js
// DOM 요소 선택
let titleElement = document.getElementById("title");
let buttonElement = document.getElementById("changeTitle");

// 클릭 이벤트 리스너 추가
buttonElement.addEventListener("click", function () {
  // 제목 요소의 텍스트 내용 변경
  titleElement.textContent = "Title has been changed!";
});
```

---

## 분리하는 이유

### 유지보수성

코드가 분리되어 있으면 각 파일을 더 쉽게 관리하고 유지보수할 수 있어서 HTML, CSS, JavaScript 각각의 역할이 명확해지면서 변경 사항을 더 쉽게 적용할 수 있다.

### 가독성

코드가 더 명확하고 읽기 쉬워진다. HTML 파일은 구조와 콘텐츠에 집중하고, JavaScript 파일은 동작에 집중할 수 있다.

### 재사용성

여러 HTML 파일에서 동일한 JavaScript 파일을 재사용할 수 있다. 이를 통해 중복 코드를 줄일 수 있다.

#### 캐싱

외부 JavaScript 파일은 브라우저에서 캐싱할 수 있어서, 동일한 파일을 여러 번 다운로드하지 않아도 된다. 이는 페이지 로드 속도를 향상시킬 수 있다.

---

# 이벤트 처리 (Event Handling)

## 정의와 역할

### 이벤트(Event)

사용자가 웹 페이지와 상호작용할 때 발생하는 사건이다. 예를 들어, 클릭, 키보드 입력, 마우스 이동 등이 있다.

### 이벤트 처리(Event Handling)

특정 이벤트가 발생했을 때 실행될 코드를 작성하는 과정이다. 사용자와 웹 페이지 간의 상호작용을 가능하게 해준다. 예를 들어, 버튼을 클릭하면 특정 동작을 수행하거나, 입력 필드에 텍스트를 입력하면 검증을 수행하는 등의 작업이 가능하다.

---

## 이벤트 처리를 사용해야 하는 이유?

### 동적인 웹 페이지

정적인 HTML 페이지를 동적으로 만들 수 있다. 사용자와 상호작용하면서 실시간으로 페이지를 변경할 수 있다.

### 사용자 경험 향상

사용자 입력에 실시간으로 반응할 수 있다. 예를 들어, 폼 검증, 드롭다운 메뉴, 모달 창 등을 구현할 수 있다.

### 기능 구현

클릭, 마우스 오버, 키 입력 등 다양한 사용자 동작에 반응하여 기능을 추가할 수 있다.

---

## 이벤트 처리의 사용법

### 기본 패턴

- 요소 선택: 이벤트를 처리할 요소를 선택한다.
- 이벤트 리스너 추가: 요소에 이벤트 리스너를 추가하여 특정 이벤트가 발생했을 때 실행할 함수를 정의한다.

### 이벤트 리스너의 종류와 역할

#### 마우스 이벤트

- `click`: 요소를 클릭할 때 발생한다. 버튼 클릭, 링크 클릭 등 사용자가 마우스로 클릭하는 동작을 처리한다.
- `dblclick`: 요소를 더블 클릭할 때 발생한다. 더블 클릭을 인식하여 특정 동작을 수행한다.
- `mouseover`: 마우스 커서가 요소 위로 이동할 때 발생한다. 마우스 오버 효과를 제공한다.
- `mouseout`: 마우스 커서가 요소를 벗어날 때 발생한다. 마우스 오버 효과를 제거하거나 다른 동작을 수행한다.
- `mousemove`: 마우스 커서가 요소 내에서 움직일 때 발생한다. 커서 위치에 따라 실시간으로 반응하는 동작을 구현한다.

#### 키보드 이벤트

- keydown: 키가 눌릴 때 발생한다. 키 입력 시작 시 동작을 처리한다.
- keyup: 키가 눌렸다가 놓일 때 발생한다. 키 입력이 끝났을 때 동작을 처리한다.
- keypress: 키가 눌릴 때 발생한다. 현재는 사용 자제 권장되며 keydown과 keyup을 더 많이 사용한다.

#### 폼 이벤트

- submit: 폼이 제출될 때 발생한다. 폼 제출 시 검증이나 데이터를 처리한다.
- change: 폼 요소의 값이 변경될 때 발생한다. 입력 값이 변경되었을 때 동작을 처리한다.
- input: 폼 요소의 값이 입력될 때 발생한다. 실시간으로 입력 값을 처리한다.

#### 기타 이벤트

- load: 페이지나 리소스가 모두 로드될 때 발생한다. 페이지 로딩이 완료되었을 때 동작을 처리한다.
- resize: 창 크기가 변경될 때 발생한다. 창 크기 변경에 따라 레이아웃을 조정한다.
- scroll: 페이지나 요소가 스크롤될 때 발생한다. 스크롤 위치에 따라 동작을 처리한다.

### 예시 코드

#### 버튼 클릭 이벤트 처리

- HTML 파일 (`index.html`)

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Event Handling Example</title>
  </head>
  <body>
    <h1 id="title">Welcome</h1>
    <button id="changeTitle">Change Title</button>
    <button id="showAlert">Show Alert</button>

    <!-- 자바스크립트 파일 포함 -->
    <script src="script.js"></script>
  </body>
</html>
```

---

- JavaScript 파일 (`script.js`)

```js
// DOM 요소 선택
let titleElement = document.getElementById("title");
let changeButton = document.getElementById("changeTitle");
let alertButton = document.getElementById("showAlert");

// 클릭 이벤트 리스너 추가
changeButton.addEventListener("click", function () {
  // 제목 요소의 텍스트 내용 변경
  titleElement.textContent = "Title has been changed!";
});

// 클릭 이벤트 리스너 추가
alertButton.addEventListener("click", function () {
  // 알림 창 표시
  alert("Button was clicked!");
});
```

---

# 가상 DOM (Virtual DOM)

DOM 조작이 많아지면 성능 문제가 발생할 수 있다. 이를 피하기 위한 성능 최적화 방법 중 하나가 가상 DOM(Virtual DOM) 사용이다.

## 왜 가상 DOM을 사용하는가?

가상 DOM을 사용하면 실제 DOM을 직접 조작하기 전에 메모리 내에서 변경 사항을 먼저 적용할 수 있다. 이렇게 하면 브라우저의 리플로우와 리페인트 과정을 최소화하여 성능을 최적화할 수 있다.

## 가상 DOM은 언제 사용되는가?

가상 DOM은 리액트(React)와 같은 프레임워크에서 많이 사용된다. 특히, 사용자 인터페이스가 빈번하게 업데이트되는 상황에서 효율적으로 동작한다. 변경 사항을 메모리 내의 가상 DOM에서 먼저 적용하고, 변경된 부분만 실제 DOM에 반영하여 성능을 향상시킨다.

> Virtual DOM에 대해서는 다음에 자세하게 다룰 예정이다.

---

# 참고 문헌

> [Link1](https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction)
> [Link2](https://www.codestates.com/blog/content/dom-javascript)
> [Link3](https://poiemaweb.com/js-dom)

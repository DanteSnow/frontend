# 들어가며

이번 포스트에서는 HTML의 DOCTYPE이 무엇인지, 어떤 역할을 하고, 어떻게 사용하는지에 대해서 다룬다. HTML과 HTML의 버전 등에 대해서는 간단하게만 짚고 넘어가고, 다음 포스트에서 깊게 다룰 예정이다.

# DOCTYPE

![DOCTYPE 태그 예시](https://velog.velcdn.com/images/clydehan/post/5d8ae3f4-76ef-4fc2-b4e4-3d0da6c41df7/image.png)

DOCTYPE은 HTML 문서의 첫 번째 줄에 위치하는 선언이다. 웹 페이지를 만들 때 가장 먼저 작성해야 하는 코드이다. 웹 브라우저가 HTML 문서를 읽을 때, 이 선언을 보고 문서의 버전을 판단한다. 이렇게 판단한 버전에 따라 웹 페이지를 올바르게 해석할 수 있도록 도와주는 중요한 역할을 한다.

즉, DOCTYPE은 브라우저가 문서를 제대로 이해하고 표시할 수 있도록 돕는 역할을 한다.

---

## HTML5 이전의 DOCTYPE

HTML5 이전의 DOCTYPE은 DTD(Document Type Definition)를 참조하여 문서의 구조와 규칙을 정의한다. DOCTYPE 선언은 HTML 문서가 어떤 DTD를 사용할 것인지 명시하여, 브라우저가 문서를 올바르게 해석하고 렌더링할 수 있도록 한다.

> 💡 **DTD(문서 유형 정의)**
> DTD(Document Type Definition)는 HTML 문서의 구조를 정의하는 규칙이다. 어떤 태그를 사용할 수 있는지, 태그들이 어떤 순서로 나올 수 있는지 등을 규정한다. DTD는 문서의 유효성을 검사하고, 브라우저가 문서를 올바르게 표시하는 데 도움을 준다.

![HTML4 로고](https://velog.velcdn.com/images/clydehan/post/2fc88f7a-98d7-49b1-b15a-0aac22634958/image.png)

### HTML 4.01

HTML 4.01에는 Strict, Transitional, Frameset 세 가지 주요 DOCTYPE이 있으며, HTML 4.01 DOCTYPE 선언은 다음과 같은 공통 구조를 가진다.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 [버전]//EN" "[DTD URL]">
```

- `!DOCTYPE HTML PUBLIC`: HTML 4.01 문서를 선언한다.
- `"-//W3C//DTD HTML 4.01 [버전]//EN"`: W3C(World Wide Web Consortium)가 정의한 HTML 4.01 표준을 따른다는 의미이다. `[버전]` 부분은 Strict, Transitional, Frameset 중 하나이다. "EN"은 영어(English)를 의미한다.
- `"[DTD URL]"`: DTD(문서 유형 정의)에 대한 링크이다. 이 링크는 브라우저가 문서 구조를 해석할 때 참고하는 규칙이다.

---

- **Strict (엄격한 규칙을 따르는 HTML)**
  Strict DTD는 매우 엄격한 문법 규칙을 요구하며, 디자인과 관련된 태그나 속성(프레젠테이션 요소)을 포함하지 않는다. 예를 들어, `<font>` 태그나 `align` 속성 등을 사용할 수 없다. 모든 스타일과 레이아웃은 CSS로 처리하는 것이 권장된다.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```

- **Transitional (엄격하지 않은 규칙을 따르는 HTML)**
  Transitional DTD는 기존 HTML 문서와의 호환성을 위해 디자인과 관련된 태그나 속성(프레젠테이션 요소)을 포함할 수 있다. 예를 들어, `<font>` 태그나 `align` 속성 등을 사용할 수 있다. 이는 이전 버전의 HTML에서 사용되던 스타일 요소들을 계속 사용할 수 있게 한다.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```

- **Frameset (프레임을 사용하는 HTML)**
  Frameset DTD는 프레임을 사용한 레이아웃을 정의하는 문서에 사용된다. `<frameset>` 요소를 사용하여 웹 페이지를 여러 프레임으로 나누는 구조를 지원한다.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
```

---

## HTML5 DOCTYPE

![HTML5 로고](https://velog.velcdn.com/images/clydehan/post/a13fa6be-51c3-4050-b06e-f92479995acf/image.png)

HTML5는 DTD를 사용하지 않는다. 대신 간단한 <!DOCTYPE html> 선언만 필요하다. 이 선언은 브라우저에게 HTML5 문서임을 알리고, 표준 모드로 렌더링하도록 지시한다.

즉, HTML5부터는 DTD를 통해 문서의 구조를 정의하지 않고, 브라우저가 내장된 파서로 HTML5 문서를 해석한다. 현대 웹 개발에서는 HTML5가 표준으로 자리 잡고 있으며, 대부분의 웹 페이지와 웹 애플리케이션이 HTML5를 사용한다.

> 💡 **파서(Parser)**
> 파서(Parser)는 브라우저가 HTML 문서를 읽고 해석하여 화면에 표시하는 데 필요한 내부 소프트웨어이다. HTML 태그와 구조를 분석하여 웹 페이지를 올바르게 렌더링할 수 있도록 도와준다.

---

### HTML5 DOCTYPE 선언 예시

HTML5에서는 단순하게 `<!DOCTYPE html>`을 사용한다. 이 선언은 최신 버전의 HTML을 사용한다는 의미이다.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>HTML5 Example</title>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
```

---

# DOCTYPE을 선언하지 않으면 어떻게 될까?

DOCTYPE을 선언하지 않으면, 웹 브라우저는 문서를 호환 모드(Quirks Mode)로 렌더링할 수 있다. 호환 모드는 오래된 웹 페이지와의 호환성을 유지하기 위해 브라우저가 사용하는 렌더링 모드이다. 이 모드는 표준 모드(Standards Mode)와 다르게 동작하여, 웹 페이지가 예상과 다르게 표시될 수 있다. 해당 부분에 대한 자세한 내용은 참조 문헌을 참고바란다.

# 참조 문헌

> - [HTML DOCTYPE - MDN](https://developer.mozilla.org/ko/docs/Glossary/Doctype)

- [Quirks_Mode_and_Standards_Mode - MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Quirks_Mode_and_Standards_Mode)

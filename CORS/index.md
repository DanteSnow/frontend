# [CS, Computer Science, FrontEnd] CORS란? (About CORS)

# 들어가며

![Cross Origin Resource Sharing](https://velog.velcdn.com/images/clydehan/post/ffab0e30-87a3-437c-a223-b820256aafe9/image.png)

> 이미지 출처 : [Youtube_The_TechCave](https://www.youtube.com/watch?v=h-WtIT6gCBk)

웹 애플리케이션 개발 시 **CORS** 문제는 매우 흔하게 접할 수 있다. 이 포스트에서는 **CORS의 기본 개념**, **동일 출처 정책**, **CORS 에러와 그 원인**, **프론트엔드에서 CORS 문제를 해결하는 방법**에 대해 다룬다.

---

# CORS란?

**CORS(Cross-Origin Resource Sharing)** 는 웹 브라우저가 보안상의 이유로 다른 도메인에서 자원을 요청할 때 발생하는 문제를 해결하기 위한 방법이다.

## 📌 다른 도메인이란?

도메인이란 웹 사이트의 주소를 말한다. 예를 들어, `https://www.example.com`과 `https://api.example.com`은 서로 다른 도메인이다. 도메인은 프로토콜, 도메인 이름, 포트 세 가지 요소로 구성된다. 이 세 요소가 모두 동일해야 같은 도메인으로 간주된다.

```plaintext
출처 예시:
- https://www.example.com (도메인 이름)
- https://www.example.com:80 (도메인 이름 + 포트)
```

## 📌 자원 요청?

웹 페이지가 로드된 도메인과 다른 도메인에서 데이터를 가져오려고 할 때, 이를 **다른 도메인에서 자원을 요청**한다고 한다. 예를 들어, `https://www.example.com`에서 로드된 웹 페이지가 `https://api.example.com/data`에서 데이터를 가져오려고 하면, 이것이 **다른 도메인에서 자원을 요청**하는 것이다.

---

# 동일 출처 정책(Same-Origin Policy)이란?

**동일 출처 정책**은 웹 브라우저가 보안을 위해 현재 웹 페이지와 다른 출처의 자원을 요청하는 것을 제한하는 규칙이다. 출처는 프로토콜, 도메인, 포트 세 가지 요소로 구성된다. 이 세 요소가 모두 동일해야 같은 출처로 간주된다.

---

## 📌 동일 출처 정책이 필요한 이유

**동일 출처 정책**이 필요한 이유는 **웹 애플리케이션의 보안을 강화**하기 위해서이다. 다음은 동일 출처 정책이 필요한 주요 이유들이다.

### 💡 사용자 데이터 보호

**동일 출처 정책**은 악의적인 웹 사이트가 사용자의 중요한 **데이터를 훔치는 것을 방지**한다. 예를 들어, 사용자가 은행 웹 사이트에 로그인한 상태에서 악의적인 웹 사이트가 사용자의 은행 데이터를 가져오지 못하도록 막아준다.

### 💡 세션 하이재킹 방지

**동일 출처 정책**은 세션 하이재킹을 방지한다. 세션 하이재킹은 사용자가 특정 웹 사이트에 로그인한 상태에서 **다른 웹 사이트가 사용자의 세션을 가로채는 공격**이다. 동일 출처 정책은 이러한 공격을 막아준다.

### 💡 데이터 무결성 유지

동일 출처 정책은 데이터의 무결성을 유지한다. 악의적인 웹 사이트가 **다른 출처의 데이터를 변경하거나 조작하지 못하도록 보장**한다.

---

# CORS의 기본 개념

**CORS**는 웹 페이지가 다른 출처의 자원을 요청할 때, 서버가 이 요청을 허용할 수 있도록 특정 헤더를 추가하여 브라우저에 권한을 부여하는 방식이다. 이는 서버와 브라우저 간의 협력을 통해 동일 출처 정책을 우회할 수 있도록 한다.

## 📌 CORS의 동작 방식

**CORS**는 서버가 요청을 허용할지 여부를 브라우저에게 알려주는 방식으로 동작한다. 서버는 **특정 HTTP 헤더**를 사용하여 요청을 허용하거나 거부할 수 있다.

1. **브라우저가 서버에 요청을 보냄**
   클라이언트(브라우저)가 다른 출처의 자원을 요청할 때, 브라우저는 해당 요청에 CORS 관련 헤더를 추가한다.

2. **서버가 응답을 보냄**
   서버는 요청을 받고, 요청이 허용될 경우 CORS 관련 헤더를 포함하여 응답을 보낸다.

3. **브라우저가 응답을 확인함**
   브라우저는 서버의 응답을 확인하고, CORS 관련 헤더가 포함되어 있으면 자원에 접근을 허용한다. 그렇지 않으면 접근을 차단한다.

### 💡 CORS 헤더

서버는 다음과 같은 **CORS 관련 헤더**를 설정하여 브라우저에 접근 권한을 부여한다.

- **Access-Control-Allow-Origin**: 접근을 허용할 도메인
- **Access-Control-Allow-Methods**: 허용할 HTTP 메서드
- **Access-Control-Allow-Headers**: 허용할 요청 헤더
- **Access-Control-Allow-Credentials**: 자격 증명을 포함한 요청 허용 여부

---

# CORS 에러와 원인

**CORS 에러**는 브라우저가 다른 출처의 자원을 요청할 때 발생할 수 있다. **일반적인 CORS 에러**와 그 원인은 다음과 같다.

## 📌 CORS 에러의 예시와 원인

### 💡 No 'Access-Control-Allow-Origin' header is present on the requested resource

- 서버가 Access-Control-Allow-Origin 헤더를 설정하지 않았다. 이 경우 브라우저는 요청을 차단한다.
- **해결 방법**: 서버 설정을 변경하여 해당 헤더를 추가해야 한다.

### 💡 The value of the 'Access-Control-Allow-Origin' header in the response must not be the wildcard '\*' when the request's credentials mode is 'include'

- 자격 증명을 포함한 요청의 경우, Access-Control-Allow-Origin 헤더에 와일드카드 `*`를 사용할 수 없다. 특정 도메인을 명시해야 한다.
- **해결 방법**: Access-Control-Allow-Origin 헤더에 특정 도메인을 명시한다.

### 💡 CORS preflight channel did not succeed

- 예비 요청(preflight request)에 대한 응답이 실패했거나, 서버가 올바른 CORS 헤더를 반환하지 않았다.
- **해결 방법**: 서버가 예비 요청에 대해 올바른 CORS 헤더를 반환하도록 설정을 조정한다.

---

# 프론트엔드에서 CORS 문제 해결하기

**CORS**를 해결할 수 있는 방법은 여러 가지이다. 이 포스트에서는 대표적으로 일반적인 **프론트엔드에서 CORS 에러를 해결할 수 있는 방법** 하나에 대해서만 다룬다.

## 📌 프록시 서버 사용

로컬 개발 환경에서 프록시 서버를 설정하여 **CORS 문제를 우회**할 수 있다. 예를 들어, `Webpack Dev Server`나 `Create React App`의 프록시 기능을 사용할 수 있다.

```js
// 예시: Create React App의 setupProxy.js 파일
const { createProxyMiddleware } = require("http-proxy-middleware");

module.exports = function (app) {
  app.use(
    "/api",
    createProxyMiddleware({
      target: "https://api.example.com",
      changeOrigin: true,
    })
  );
};
```

---

# 결론

프론트엔드 개발자로서 CORS 문제는 일상적으로 접할 수 있는 도전 과제 중 하나이다. CORS는 웹 보안을 위해 반드시 필요하지만, 개발 과정에서는 불편함을 초래할 수 있다.

CORS 문제를 해결하기 위해 서버 측 설정을 조정하는 것이 가장 이상적이지만, 프론트엔드 개발자 입장에서는 서버에 접근할 수 없는 경우도 많다. 이럴 때는 프록시 서버를 설정하거나 브라우저 확장 프로그램을 활용하는 등의 방법을 통해 문제를 해결할 수 있다.

중요한 점은, CORS에 대한 깊은 이해를 바탕으로 문제를 빠르게 진단하고 적절한 대응 방법을 찾는 것이다. 프론트엔드 개발자로서 이러한 문제를 미리 예측하고 준비함으로써 개발 과정에서 발생하는 불필요한 지연을 최소화할 수 있다.

최종적으로, CORS 문제는 웹 개발에서 피할 수 없는 부분이지만, 다양한 해결 방법을 익혀두면 실무에서 큰 도움이 된다.

---

# 참고 문헌

> - [MDN_CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

- [Stack Overflow: Common CORS Issues](https://stackoverflow.com/questions/tagged/cors)

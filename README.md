# React with Typescript

1. 프로젝트 생성

```
$ npx create-react-app react-ts-app --template=typescript
$ cd react-ts-app
$ yarn start
```

2. 패키지 설치

   - @craco/craco
     - react에서 import 시 상대경로 불편함을 해소할 패키지
   - @loadable/component
   - @reduxjs/toolkit
   - @types/js-cookie
   - @types/lodash
   - @types/qs
   - @types/uuid
   - @types/autosize
   - axios
     - 브라우저, Node.js를 위한 Promise API를 활용하는 HTTP 비동기 통신 라이브러리
   - autosize
   - classnames
     - 리액트에서 사용하는 JSX 문법의 classnames
   - cross-env
   - dayjs
     - date를 다룰 수 있는 패키지
     - [dayjs](https://day.js.org/)
   - draft-js
     - 텍스트 에디터의 한 종류
     - [draftjs](https://draftjs.org/)
   - highlight-within-textarea
     - 특정 글자를 highlight 해주는 패키지
   - http-proxy-middleware - 현재 진행하는 프로젝트를 내가 만든 서버와 proxy로 연결하기 위해서 사용하는 방법

     ```
     const { createProxyMiddleware } = require('http-proxy-middleware');

     module.exports = function(app){
        app.use(
            createProxyMiddleware('/api', {
            target: 'http://localhost:3001/',
            changeOrigin: true
            })
        )
     };
     ```

     - /api는 proxy를 사용할 경로 (path)이고, target은 내가 proxy로 이용할 서버의 주소이다.
     - changeOrigin은 대상 서버의 구성에 따라 호스트 헤더의 변경을 해주는 옵션이다.

- i18next, react-i18next

  - 다국어 처리
  - [i18next 자료](https://lemontia.tistory.com/924)

```

     yarn add i18next
     yarn add react-i18next

```

- i18next-browser-languagedetector
- immer

  - react에서 불변성을 유지하는 코드를 작성하기 쉽게 해주는 라이브러리이다.
  - 원래 react에서는 redux로 불변성을 유지하며 state를 다룰 수 있다.

  ```
    # 배열에 추가
    setUsers(state.array.concat(user));

    # 배열에서 삭제
    const onRemove = id => {
      // user.id가 id인 것을 제거
      setUsers(users.filter(user => user.id !== id));
    };

    # 배열에서 수정
    const onToggle = id => {
      setUsers(
        users.map(user =>
          user.id === id ? { ...user, active: !user.active } : user
        )
      );
    };

    # 객체에서 추가
    setState(state => { ...state, key: value });

    # 객체에서 제거
    setState(state => { ..._.omit(state, 'deleteKey') })

    # 객체에서 수정
    setState(state => { ...state, key: newValue });
  ```

  - 그렇지만, immer.js를 사용하면 일반 객체 또는 배열을 다루듯이 사용해도 불변성을 유지할 수 있다.

  ```
    import produce "immer";

    const baseState = [
      {
        todo : "Learn typescript",
        done : true
      },
      {
        todo : "Try immer",
        done : false
      }
    ];

    const nextState = produce(baseState, draftState => {
      draftState.push({ todo : "Tweet about it" });
      draftState[1].done = true;
    })
  ```

  - immer에서 쓸 함수는 `produce` 뿐이다. 2가지 params를 가져오는데, 첫번째 param은 수정하고 싶은 객체/배열, 두번째 param은 parameter에 할당된 객체/배열을 바꾸는 함수이다.

- js-cookie

  ```
  # default 사이트 전체에서 확인 가능
    Cookies.set('name', 'value');
  # 7일 뒤 쿠키 만료
    Cookies.set('name', 'value', { expires : 7 });
  # 7일 뒤 쿠키 만료 + 현재 경로에서만 확인 가능
    Cookies.set('name', 'value', { expires : 7, path : '' });

  # get
    Cookies.get('name'); -> 'value'
    Cookies.get('phone'); -> undefined
    Cookies.get(); -> { name : 'value' }

  # delete
    Cookies.remove('name');

  ```

- moment
- moment-timezone
- react-datepicker
- react-device-detect
- react-grid-layout
- react-redux
- react-responsive
- react-router-dom

```

```

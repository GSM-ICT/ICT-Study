# useEffect

useEffect는 리액트 컴포넌트가 렌더링될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook이다.

`useEffect` 를 import 구문에 추가하여 사용하기

```
import React, { useEffect } from "react";
```

> 기본적인 `useEffect` 작성 코드
>
> ```js
> useEffect(() => {
>   //코드 실행
> },[]);
> ```

### info.js 에서 useEffect 사용하기

> ```js
> import React, { useState, useEffect } from "react";
>
> const Info = () => {
>   const [name, setName] = useState("");
>   const [nickname, setNickname] = useState("");
>
>   useEffect(() => {
>     console.log("effect");
>     console.log(name);
>     return () => {
>       console.log("clean up");
>       console.log(name);
>     };
>   }, [name]);
>
>   const onChangeName = e => {
>     setName(e.target.value);
>   };
>
>   const onChangeNickname = e => {
>     setNickname(e.target.value);
>   };
>
>   return (
>     /* ---생략---*/
>   );
> };
>
> export default Info;
> ```
> `useEffect`는 기본적으로 렌더링되고 난 직후마다 실행된다.
>
> 그리고 두 번째 파라미터 배열에 무엇을 넣는지에 따라 실행되는 조건이 달라진다.
>
> 만약 컴포넌트가 언마운트되기 전이나 업데이트되기 직전에 어떠한 작업을 수행하고 싶다면 `return`을 해주어야 한다.
>

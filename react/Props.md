# Props

`props`는 `properties`를 줄인 표현으로 컴포넌트 속성을 정할 때 사용하는 요소이다.

`props` 값은 해당 컴포넌트를 불러와 사용하는 부모 컴포넌트에서 설정할 수 있다.

> `props` 값은 컴포넌트 함수의 파라미터로 받아 와서 사용할 수 있다.
>
> 렌더링을할 때 JSX 내부에서 `{ }` 기호로 감싸 주면 된다.
>
> `App.js`
>
> ```js
> import React from "react";
> import MyComponet from "./MyComponet";
>
> function App() {
>   return (
>     <>
>       <h3>Props<h3/>
>       <MyComponet name="유영재" />
>       <hr />
>     </>
>   );
> }
>
> export default App;
> ```
>
> `Mycomponent.js`
>
> ```js
> import React from "react";
>
> const MyComponet = (props) => {
>   return (
>     <>
>       <div>안녕하세요, 제 이름은 {props.name} 입니다.</div>
>     </>
>   );
> };
>
> export default MyComponet;
> ```
>
> `props`는 일반 태그에 속성을 설정 해주는 것 처럼 컴포넌트에 속성을 지정 하면 된다.

### defaultProps

가끔씩은 실수로 props 를 빠트려먹을때가 있다. 혹은, 특정 상황에 props 를 일부러 비워야 할 때도 있다. 그러한 경우에, props 의 기본값을 설정해줄 수 있는데, 그것이 바로 defaultProps 이다.

> `App.js`
>
> ```js
> import React from "react";
> import DefaultProps from "./DefaultProps";
> import MyComponet from "./MyComponet";
>
> function App() {
>   return (
>     <>
>       {/* ...생략  */}
>       <h3>DefaultProps</h3>
>       <DefaultProps />
>       <hr />
>     </>
>   );
> }
>
> export default App;
> ```
>
> `DefaultProps.js`
>
> ```js
> import React from "react";
>
> const DefaultProps = (props) => {
>   return (
>     <>
>       <div>안녕하세요, 제 이름은 {props.name} 입니다.</div>
>     </>
>   );
> };
>
> DefaultProps.defaultProps = {
>   name: "리액트",
> };
>
> export default DefaultProps;
> ```

### 태그 사이의 내용을 보여주는 children

컴포넌트 태그 사이의 내용을 보여주는 props가 있다.

> `App.js`
>
> ```js
> import React from "react";
> import ChildrenProps from "./ChildrenProps";
> import DefaultProps from "./DefaultProps";
> import MyComponet from "./MyComponet";
>
> function App() {
>   return (
>     <>
>       {/* ...생략  */}
>       <h3>ChildrenProps</h3>
>       <ChildrenProps>자바스크립트</ChildrenProps>
>       <hr />
>     </>
>   );
> }
>
> export default App;
> ```
>
> `ChildrenProps.js`
>
> ```js
> import React from 'react'
>
> const ChildrenProps = (props) => {
>     return (
>         <>
>         <div>childrenProps는 {props.children} 입니다.</div>
>         </>
>     )
> }
>
> export default ChildrenProps
> ```
>
> `ChildrenProps` 컴포넌트 사이에 작성한 "자바스크립트" 라는 문자열을 `ChildrenProps` 컴포넌트 내부에서 보여주려면 `props.children` 을 이용해야 한다.

### 비구조화 할당으로 props 내부 값 추출

컴포넌트에서  `props` 값을 조회할 때마다 `props.name`,`props.children`과 같이 "`props.`"이라는 키워드를 앞에 붙이고 있다. 이러한 작업을 더 편하게 하기 위해 ES6의 비구조화 할당 문법을 사용하여 내부 값을 바로 추출하는 방법이 있다.

> `App.js`
>
> ```js
> import React from "react";
> import ChildrenProps from "./ChildrenProps";
> import DefaultProps from "./DefaultProps";
> import DestructuringAssignment from "./DestructuringAssignment";
> import MyComponet from "./MyComponet";
>
> function App() {
>   return (
>     <>
>       {/* ...생략  */}
>       <h3>비구조화 할당으로 props 추출</h3>
>       <DestructuringAssignment dogName="뭉이" dogAge={5} />
>       <hr />
>     </>
>   );
> }
>
> export default App;
>
> ```
> `DestructuringAssignment.js`
>
> ```js
>    import React from "react";
>
> const DestructuringAssignment = (props) => {
>   const { dogName, dogAge } = props;
>   return (
>     <>
>       <div>
>           강아지 이름은 {dogName} 이고 {dogAge}살 입니다.
>       </div>
>     </>
>   );
> };
>
> export default DestructuringAssignment;
>
> ```
> 이렇게 비구조화 할당을 이용하여 `props`를 사용하면 훨씬 편하다.

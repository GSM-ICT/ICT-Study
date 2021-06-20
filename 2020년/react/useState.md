# useState

`useState` 를 import 구문에 추가하여 사용하기

```
import React, { useState } from "react";
```

> useState 함수의 파라미터에는 상태의 초기 값을 넣어준다.
>
> ```js
> const [상태 값 저장 변수(첫 번째 원소), 상태 값 갱신 함수(두 번째 원소)] = useState(<상태 초기 값>);
> ```
>
> 함수가 호출되면 배열을 반환한다. 그 배열의 첫 번째는 원소는 상태 값, 두 번 째 원소에는 상태를 설정하는 함수이다.
> 함수에 파라미터를 넣어서 호출하면 전달받은 파라미터로 값이 바뀌고 컴포넌트가 리렌더링 된다.

### useState로 숫자 카운터 구현

> `Counter.js`
>
> ```js
> import React, { useState } from "react"; //useState를 사용하기 위해 import
>
> const Counter = () => {
>   const [value, setValue] = useState(0); //useState를 선언하고 초기값을 0으로 설정
>   return (
>     <div>
>       <p>
>         현재 카운터 값은 <b>{value}</b>입니다.
>       </p>
>       <button onClick={() => setValue(value + 1)}>+1</button>
>       <button onClick={() => setValue(value - 1)}>-1</button>
>     </div>
>   );
> };
>
> export default Counter;
> ```
>
> 10번째 줄을 보면 `useState`의 두 번째 파라미터인 `setValue`를 호출하여 파라미터에 `value+1`을 넣어 기존 값에 1을 더해준다.
>
> 11번째 줄 코드도 `useState`를 이용하여 1을 빼주는 코드이다.

### useState 여러 번 사용

> `useState`의 변수만 바꿔서 여러번 사용 할 수 있다.
>
> `info.js`
>
> ```js
> import React, { useState } from "react";
>
> const Info = () => {
>   const [name, setName] = useState("");
>   const [nickname, setNickname] = useState("");
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
>     <div>
>       <div>
>         <input value={name} onChange={onChangeName} />
>         <input value={nickname} onChange={onChangeNickname} />
>       </div>
>       <div>
>           <b>이름 :</b> {name}
>       </div>
>       <div>
>           <b>닉네임 :</b> {nickname}
>       </div>
>     </div>
>   );
> };
>
> export default Info;
> ```
>
> 18번째 줄과 19번째 줄을 보면 `onChangeName`을 호출하고 그 안에있는 `setName`함수에 파라미터를 넣어 `name`을 재설정 해준다.

---

# 컴포넌트 성능 최적화

### 성능이 저하되는 원인

* 단적으로 말해서, 렌더링 작업을 많이 할수록 느려진다.
* 컴포넌트의 초기 렌더링이 꼭 필요한 작업임을 감안하면, 최적화시켜야 할 부분은 바로 리렌더링이다
* 그리고 리렌더링은 1) 데이터(props/state)가 변경될 때, 2) 부모 컴포넌트가 리렌더링될 때, 3) forceUpdate함수가 실행될 때 발생한다.

### 데이터가 변경될 때

* 데이터가 변경되었을 때에는 변경된 데이터 부분만 리렌더링하고, 나머지는 기존 값을 유지시키면 리렌더링 성능을 최적화할 수 있다.
* 클래스형 컴포넌트에서는 shouldComponentUpdate를 통해 이 작업을 해줄 수 있다.


### 최적화를 위해서 UseState 함수형 업데이트

> 기존에 숫자를 더하는법
>
> ```js
> const [num, setNum] = useState (0);
> //prevNum은 현재 num 값
> setNum(prevNum+1);
> ```
>
> useCallback을 사용하여 업데이트
>
> ```js
> const [num, setNum] = useState (0);
> //prevnum은 현재 num 값
> const onIncrease = useCallback(
>   () => setNum(prevNum => prevNum + 1),
>   [],
> );
> ```
>
> 이러면 useCallBack을 사용할 때 두 반쩨 파라미터에 num을 넣지 않아도 됨

# Props and State
리액트에서 데이터를 다룰 때 사용된다.

<br>

## props
**상위 컴포넌트가 하위 컴포넌트에 값을 전달**할 때 사용
하위 컴포넌트에서는 props가 **읽기 전용 데이터**이기 때문에 수정할 수 없다.

-  **문자열**을 전달할 때는 **큰따옴표("")**, **문자열 외의 값**을 전달할 때는 **중괄호({})** 사용
- **N개의 프로퍼티** 전달 가능
```javascript
import  Ex  from  './component/Ex';

function  App() {
	const  arr = [
		{id:  1, str:  "hello"},
		{id:  2, str:  "react"},
		{id:  3, str:  "!!"}
	]

	return (
		<div  className="App">
			<Ex  str = "hello"  arr={arr}/>
		</div>
	);
}

export  default  App;
```
<br>

### key
엘리먼트에 안정적인 고유성을 부여하기 위해 배열 내부의 엘리먼트에 지정해야함.
- 어떤 항목을 변경, 추가 또는 삭제할지 식별하는데 사용 

<br>

🚨 **map 함수 적용 시 key를 부여**하지 않으면 경고가 뜨게 됨

<img src="https://user-images.githubusercontent.com/46274903/174033061-09a08b57-ebda-4f76-b09b-e4a6fca60ab7.png">


```javascript
// App.js
import  Ex  from  './component/Ex';

function  App() {
	const  arr = [
		{id:  1, str:  "hello"},
		{id:  2, str:  "react"},
		{id:  3, str:  "!!"}
	]

	return (
		<div  className="App">
			<Ex  str = "hello"  arr={arr}/>
		</div>
	);
}

// Ex.js
export  default  App;

export  default  function  Ex(props) {
	return (<>
		{props.arr.map(item  => (
			<li  key={item.id}>{item.str}</li>
		))}
	</>);
}
```
#### 결과
<img src="https://user-images.githubusercontent.com/46274903/174198783-49e4591b-370c-4eda-b0fe-999b63a6437b.png">


<br>

## State
컴포넌트의 내부에서 **변경 가능한 데이터**를 관리해야 할 때 사용
**값을 저장하거나 변경할 수 있는 객체**로 보통 이벤트와 함께 사용한다.

- react 모듈에서 **{ useState }** 를 불러오고 **useState() 를 선언**하여 사용
- 데이터 변경 함수를 통해 데이터를 변경한다.

>const[state, setState] = useState(initialState); 
>
>const[데이터, 데이터변경함수] = useState(초기값(생락가능));

<br>

```javascript
// Hello.js
import  styles  from  './Hello.module.css';
import {useState} from  "react";
import  UserName  from  "./UserName";

export  default  function  Hello() {

	const [name, setName] = useState("Mike");

	return (
		<div>
			<UserName  name={name}  />
			<button  onClick={() => {
				setName(name === "Mike" ? "Jane" : "Mike");
			}}>change</button>
		</div>
	);
}

// UserName.js
export  default  function  UserName({name}) {
	return  <p>Hello, {name}  </p>
}
```
<br>

#### setState(데이터변경메서드)를 사용하는 이유
react에서는 모든 상태 값들을 불변성을 유지하며 관리한다. 불변성을 유지하는 이유는 **실제 DOM과 가상 DOM의 차이**를 알아내기 위해서 이다. 어떠한 **객체가 변경되었는지 쉽게 판단**할 수 있고 이를 바탕으로 **렌더링 할 지를 결정**하는데 도움을 준다. 

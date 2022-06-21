# Hook
함수형 컴포넌트가 클래스형 컴포넌트의 기능을 사용할 수 있도록 해주는 기능

### useState
컴포넌트의 상태 관리를 위해 사용
```javascript
const [상태 값 저장 변수], <상태 값 갱신 함수>] = useState(<상태 초기 값>);

// ex
import { useEffect, useState } from  "react";  

export  default  function  UseFetch(url) {
	const [data, setData] = useState([]);  // 선언

	useEffect(() => {
		fetch(url)
		.then(res  => {
			return  res.json();
		})
		.then(data  => {
			setData(data);	// state 값 갱신
		})
	}, [url]);

	return  data;
}
```
<br>

### useEffect
[Link ](Basic/useEffect.md)

<Br>

### useRef
current 속성을 가지고 있는 객체를 반환하는 함수

- current 속성은 값을 변경해도 상태를 변경할 때처럼 컴포넌트가 다시 랜더링 되지 않음
- 또한, 컴포넌트가 다시 랜더링될 때도 current 속성의 값이 유실되지 않음
```javascript
const ref = useRef(<초기 값>);

//ex
const  engRef = useRef(null);

<input  type="text"  placeholder="computer"  ref={engRef}  />

const  eng = engRef.current.value;	// engRef 현재 값
```

<br>

### useNavigate
특정 event가 발생했을 대 url을 조작할 수 있는 interface 제공

- 특정 행동을 했을 때 해당 주소로 이동할 수 있게 해줌
```javascript
const navigate = useNavigate();
navigate('url');

// ex
const  navigate = useNavigate();

fetch('http://localhost:3001/words/', {
	method :  "POST",
	headers : {
		"Content-Type" :  "application/json",
	},
	body :  JSON.stringify({
		day,
		eng,
		kor,
		'isDone' :  false,
	})
})
.then(res  => {
	if(res.ok) {
  	alert('생성이 완료되었습니다.');
	  navigate(`/day/${dayRef.current.value}`);}	// 해당 주소로 이동
	}
);
```

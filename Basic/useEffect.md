# useEffect
React Component가 **렌더링 될 때마다 특정 작업을 실행**할 수 있도록 하는 React Hook

<br>

```javascript
import { useEffect } from "react"

useEffect(function, deps)
```
- **function** : 실행하고자 하는 함수
- **deps** : 배열 형태, function을 실행 시킬 조건
 deps에 넣은 값이 업데이터 될 때마다 useEffect를 실행
<br>

1. 최초 렌더링 시에만 실행
```javascript
useEffect(function, []);
```
2. 렌더링 할 때마다 실행
```javascript
useEffect(function);
```
3. 특정 값이 업데이트 될 때마다 실행
```javascript
useEffect(function, count);
```

<br>

```javascript
import { useEffect, useState } from  "react";
import { useParams } from  "react-router-dom";
import  Word  from  "./Word";  

export  default  function  Day() {
	const  day = useParams().day;
	const [words, setWords] = useState([]);  

	useEffect(() => {
		fetch(`http://localhost:3001/words?day=${day}`)
		.then(res  => {
		return  res.json();
		})
		.then(data  => {
		return  setWords(data);
		})
	}, [day]);  

	return (<>
		<h2>Day {day}</h2>
		<table>
			<tbody>
				{words.map(word  => (
				<Word  word={word}  key={word.id}  />
				))}
			</tbody>
		</table>
	</>);
}
```

<br>


### fetch
**비동기 네트워크 통신**, Ajax와 같은 역할

```javascript
fetch(url. [option])
```
- **url** : 접근하고자 하는 URL
- **option** : 선택 매개변수, method나 header 등을 지정할 수 있다.

<br>


```javascript
fetch('url')
.then(res => res.json())
.then(data => {...});
```

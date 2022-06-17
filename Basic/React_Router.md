# React Router
사용자가 입력한 **주소를 감지하는 역할**을 하며, 여러 환경에서 동작할 수 있도록 여러 종류의 라우터 컴포넌트를 제공

-  **페이지 이동 기능을 구현**하기 위해 React Router를 이용
- 새로운 페이지를 로드하지 않고 **하나의 페이지 안에서 필요한 데이터만 가져오는 방식**

<br> 

### 설치

```
yarn add react-router-dom
```

<img src="https://user-images.githubusercontent.com/46274903/174223948-46ce9baa-c678-47d6-a2a4-f105e6bbceb4.png">

<br>

### 태그
**BrowserRouter**

페이지 이동에 사용할 컴포넌트들을 감싸준다.
<br>

**Routes**

여러 Route를 감싸며 페이지가 변경되는 컴포넌트들을 감싸준다.
<br>

**Route**

- path : 경로
- element : 이동할 컴포넌트

	- 여러 라우팅을 매칭하고 싶은 경우 * 사용
	- "/" 의 경우 메인 페이지로 이동
	- 지정되지 않은 경로로 접근할 때 페이지를 연결하고 싶은 경우 path="*" 를 설정해주고 < Route > 가장 하단에 넣어준다.

```javascript
// App.js
import  Header  from  './component/Header';
import  DayList  from  './component/DayList';
import  Day  from  './component/Day';
import { BrowserRouter, Route, Routes } from  'react-router-dom';
import  EmptyPage  from  './component/EmptyPage';
  
function  App() {

	return (
		<BrowserRouter>
			<div  className="App">
			<Header  />
			<Routes>
				<Route  path='/'  element={<DayList  />}></Route>
				<Route  path='/day/:day'  element={<Day  />}>/Route>
				<Route  path='*'  element={<EmptyPage  />}></Route>
			</Routes>
			</div>
		</BrowserRouter>
	);
} 

export  default  App;
``` 
<br>

**Link**

링크 태그, History API를 통해 **브라우저 주소의 경로만 바꿔줌**.

##### ※ a 태그의 경우 클릭 시 페이지를 새로 불러오기 때문에 Link 태그를 사용

```
import { Link } from "react-router-dom"
<Link to="경로"></Link>
```

<br>

**URL 파라미터**
- Link 태그에는 **${} 를 사용**하여 넣어준다.
- Route 태그에는 **: 를 사용**하여 넣어준다.
<br>

**해당 피라미터를 받는 js**

```
import { useParams } from "react-router-dom"

const { 파라미터명 } = useParams();
or
const 파라미터명 = userParams().파라미터명;
```

```javascript
// DayList.js
import  dummy  from  "../db/data.json";
import { Link } from  "react-router-dom";  

export  default  function  DayList() {

	return (
		<ul  className="list_day">
			{dummy.days.map(day  => (
				<li  key={day.id}>
					<Link  to={`/day/${day.day}`}>
					Day {day.day}
					</Link>
				</li>
			))}
		</ul>
	);
}

// Day.js
import  dummy  from  "../db/data.json";
import { useParams } from  "react-router-dom";  

export  default  function  Day() {
	const  day = useParams().day;
	const  wordList = dummy.words.filter(word  => (
		word.day === Number(day)
	)); 

	return (<>
		<h2>Day {day}</h2>
		<table>
			<tbody>
				{wordList.map(word  => (
					<tr  key={word.id}>
						<td>{word.eng}</td>
						<td>{word.kor}</td>
					</tr>
				))}
			</tbody>
		</table>
	</>);
}
```

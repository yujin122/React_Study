# ETC

### console.log() 가 여러 번 찍히는 이유
React.StrictMode 때문
```javascript
// index.js
const  root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
	// <React.StrictMode>
	<App  />
	// </React.StrictMode>
);
// React.StrictMode를 제거해주면 됨
```
**StrictMode**

: 리액트에서 제공하는 검사도구로 안전하지 않은 생명주기를 가진 컴포넌트나 권장되지 않은 부분 등 배포 후 문제가 될만한 이슈를 미리 잡는 모드

<br>

### localStorage
localStorage를 사용하면 key-value 값을 브라우저의 Storage에 저장할 수 있다.

- 전역에서 접근이 가능
- json 형태로 읽고 써야함
- 동일한 PC 안에서 동일한 브라우저를 사용했을 때 사용
- 데이터를 직접 삭제하지 않는 한 브라우저를 닫아도 저장된 데이터를 불러옴

```javascript
localStorage.setItem(<key>, <value>);	// 추가
localStorage.getItem(<key>);			// 특정 키 값 읽어오기
localStorage.removeItem(<key>);			// 삭제
localStorage.clear();					// 도메인 내의 localStorage 값 삭제
localStorage.key(<index>);				// index로 키 값 찾기

// 배열이나 객체를 추가할 때는
JSON.stringity(<obj>);
// 배열이나 객체를 가져올 때는
JSON.parse(<json>);
```

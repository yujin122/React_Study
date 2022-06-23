# axios
브라우저, Node.js를 위해서 만들어진 Promise API를 활용하는 HTTP 비동기 통신 라이브러리

<br>

### Fetch API / axios
|Fetch| axios |
|--|--|
| body 프로퍼티 사용 | data 프로퍼티 사용 |
|url이 fetch 인자에 들어감|url이 option 객체에 들어감|
|stringity()를 사용하여 json 형태로 변환시켜줘야함|자동으로 json 형태로 변환시켜줌|
|설치 필요 없음|라이브러리 설치 필요|

<Br>

## 사용법
#### 설치
```
yarn add axios
```
<br>

#### 문법
```javascript
axios({
	url:  'http://localhost:3001/words/',	// url
	method:  'POST',	// 요청방식(GET, PUT, POST, DELETE)
	data: {	// 보내는 데이터
		'day' :  data.day,
		'eng' :  data.eng,
		'kor' :  data.kor,
		'isDone' :  false
	}
	}).then(function(res) {	
		// 성공 시
		if(res.status === 201) {
			alert('생성이 완료되었습니다.');
			setIsSubmitSuccessful(true);
		}
	}).catch(function (error) {
		// 오류발생 시
		console.log(error);
	});
}
```
<Br>

#### 단축메서드
```javascript
// GET
axios.get(url[, config])
// POST
axios.post(url, data[,config])
// PUT
axios.put(url, data[,config])
// DELETE
axios.delete(url[, config])
```


##### [참고]
[axios](https://inpa.tistory.com/entry/AXIOS-%F0%9F%93%9A-%EC%84%A4%EC%B9%98-%EC%82%AC%EC%9A%A9#axios%EB%9E%80)

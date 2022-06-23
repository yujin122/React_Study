# useForm
Form을 쉽게 만들기 위한 라이브러리

- 적은 코드로 쉽게 작성할 수 있음
- 다른 라이브러리 혹은 React에 비해 Re-render 수가 적음
- form의 validation을 더 수월하게 검사할 수 있음
<br>

### 설치
```
yarn add react-hook-form
```

## 사용 방법
### 설치
```
yarn add react-hook-form
```
<br>

### 선언
```javascript
// 해당 인자 외에 다른 인자들도 있음
const { register, handleSubmit, formState: { errors } , reset} = useForm();
````
<br>

### register
input의 value를 불러오며 해당 value의 유효성 검사를 해주는 함수
```javascript
<input type="text" placeholder="computer" {...register("eng")}  />
```
#### 유효성 검사
|  |  |
|--|--|
| **required** | 필수 값 |
| **minLength / maxLength** | 최소/최대 글자 수 |
| **min / max** | 최소/최대 값 |
| **pattern** | 정규식을 이용한 유효성 검사 |
| **validate** | 개발자가 custom한 함수를 사용하여 검사 |
 
 
 ``` javaScript
<input  type="text" placeholder="computer" {...register("eng", {
	required : "Eng를 입력해주세요.",
	minLength: {
		value: 5,
		message: "5글자 이상 입력해주세요."
	}
})}  />
```
<br>

### errors
유효성 검사에서 에러가 발생했을 때의 error 값을 가지고 있는 객체
<img src="https://user-images.githubusercontent.com/46274903/175186983-3d74234c-60c3-44df-8d4b-da40bd456760.png">
|  |  |
|--|--|
|**type**  |error 타입  |
|**message**  |에러가 났을 때 나타나는 메시지 |
|**ref**  |입력 엘리먼트  |
```javascript
const  onError = (error) => {
	if(error?.eng !== undefined) {
		alert(error.eng.message);
		return;
	}

	if(error?.kor !== undefined) {
		alert(error.kor.message);
		return;
	}
}
```
<br>

### handleSubmit
유효성 검사가 완료되었을 때 폼에서 데이터를 전달하는 함수
```javascript
<form  onSubmit={handleSubmit(onSubmit, onError)}>
</form>
```
<br>

### reset
폼 안의 피드 값과 에러를 초기화 하는 함수
```javascript
useEffect(() => {
	if(isSubmitSuccessful) {
		reset({	// 초기화 할 값
			eng :  '',
			kor :  '',
			day :  '0'
		})
	}
}, [isSubmitSuccessful]);
```

<br>

#### 전체 코드
```javascript
import { useEffect, useState } from  "react";
import  UseFetch  from  "../hooks/UseFetch";
import { useNavigate } from  "react-router-dom";
import { useForm } from  "react-hook-form";  

export  default  function  CreateWord() {
	const  days = UseFetch("http://localhost:3001/days");
	const  navigate = useNavigate();
	const [isLoading, setIsLoading] = useState(false);
	const [isSubmitSuccessful, setIsSubmitSuccessful] = useState(false);  

	const { register, handleSubmit, formState: { errors } , reset} = useForm();
	const  onError = (error) => {
		if(error?.eng !== undefined) {
			alert(error.eng.message);
			return;
		}

		if(error?.kor !== undefined) {
			alert(error.kor.message);
			return;
		}
	}

	const  onSubmit = (data) => {
		fetch('http://localhost:3001/words/', {
			method :  "POST",
			headers : {
				"Content-Type" :  "application/json",
			},
			body :  JSON.stringify({
				'day' :  data.day,
				'eng' :  data.eng,
				'kor' :  data.kor,
				'isDone' :  false,
			})
		})
		.then(res  => {
			if(res.ok) {
				alert('생성이 완료되었습니다.');
				setIsSubmitSuccessful(true);
			}
		});
	} 

	useEffect(() => {
		if(isSubmitSuccessful) {
			reset({
				eng :  '',
				kor :  '',
				day :  '0'
			})
		}
	}, [isSubmitSuccessful]);

	return (
		<>
		<form  onSubmit={handleSubmit(onSubmit, onError)}>
		<div  className="input_area">
			<label>Eng</label>
			<input  type="text" placeholder="computer" {...register("eng", {
			required : "Eng를 입력해주세요.",
			minLength: {
				value: 5,
				message: "5글자 이상 입력해주세요."
			}
			})}  />
		</div>
		<div  className="input_area">
			<label>Kor</label>
			<input  type="text" placeholder="컴퓨터" {...register("kor",{
				required :  "Kor를 입력해주세요."
			})}/>
		</div>
		<div  className="input_area">
			<label>Day</label>
			<select  name="day"  {...register("day") }  >
				<option value="0">===== Day =====</option>
				{
				days.map(day  => (
					<option  key={day.id}  value={day.day}>{day.day}</option>
				))
				}
			</select>
		</div>
			<button>저장</button>
		</form>
		</>
	);
}
```

##### 참고
[react-hook-form](https://react-hook-form.com/v6/api#useForm)

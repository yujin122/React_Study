# React
React는 UI 자바스크립트 라이브러리로써 **SPA(Single Page Application)의 사용자 인터페이스를 구축하는데 사용되는 라이브러리**

<br/>

### 사용하는 이유
사용자의 응답에 따라 인터페이스가 지속적으로 변해야 하는 웹페이지의 경우 기존 방식(HTML, CSS)으로는 관리하기가 어렵지만 React를 사용하면 **사용자와 상호 작용 할 수 있는 UI를 쉽게 구현**하고 **대규모 웹페이지를 관리하기에 용이**하다.

<br/>

### 특징
#### 1. Component 기반 구조
Component는 **독립적인 단위의 소프트웨어 모듈**로 UI를 하나의 큰 덩어리로 생각한다면 컴포넌트는 그 덩어리를  이루는 **요소**이다.

```JavaScript
// 컴포넌트 
const Title = () => { 
	return <h1>Hello world</h1>; 
}; 
// 컴포넌트 
const Button = () => { 
	return <button>This is a Button</button>; 
}; 

const App = () => { 
	return ( 
		<div> <Title /> <Button /> </div> 
	); 
};
```
- 컴포넌트 단위로 쪼개져 있기 때문에, 중복되는 코드가 적어지며(**높은 재사용성**) 전체 코드를 파악하기 상대적으로 쉽고 변경 사항을 반영하는데 상당히 좋다.

- 테스트 하기가 쉬워 코드의 **유지보수, 관리가 용이**해진다.

<br/>

#### 2. 단방향 데이터 흐름
데이터의 흐름이 한 방향으로만 흐르는 **단방향 흐름**을 가진다.

- 데이터의 흐름이 부모 → 자식으로 단방향적이기 때문에 디버깅에 용이하며, 다른 라이브러리에 비해 **안정성이 높다.**

<br/>

#### 3. Virtual DOM
가상의 Document Object Model

- 기존의 방식은 DOM 객체의 변화를 감지하면 DOM을 다시 그리는 방식으로 DOM을 다시 그리게 되면 브라우저의 리소스를 사용하기 때문에 성능 이슈가 발생

- 가상 DOM의 경우 이벤트가 발생할 때마다 Virtual DOM을 만들고 실제 DOM과 비교해 **변화된 부분만 업데이트**하기 때문에 **효율성**과 **속도**를 높일 수 있다.

<br/>

#### 4. Props and State

리액트는 내부적으로 Props와 State를 가진다.

- Props
	- 부모 컴포넌트에서 자식 컴포넌트로 전달해 주는 읽기 전용 데이터
	- 자식 컴포넌트에서 전달 받은 props는 변경이 불가능하고 부모 컴포넌트에서만 props를 변경할 수 있다.

- State

	- 컴포넌트 내부에서 선언하여 사용하는 동적인 데이터
	- 독립적인 데이터이기 때문에 다른 컴포넌트에서 접근이 불가능하다.

[참고예제](https://studyingych.tistory.com/52)

<br/>

#### 5. JSX

JSX(JavaScript XML)는 **JavaScrip에 XML을 추가한 확장한 문법**으로 브라우저에서 실행하기 전에 바벨을 사용하여 일반 자바스크립트 형태의 코드로 변환된다.

```JavaScript
function App() { 
	return ( 
		<div> <h1>Hello!</h1> </div> 
	); 
}
```

- 자바스크립트에서 HTML을 작성하듯이 하기 때문에 **가독성**과 **활용도**가 높다.

- React에서 JSX 사용이 필수가 아니기 때문에 JavaScript로도 작성 가능

<br/>

### 장단점

#### 장점
- 간편한 UI 수정과 재사용이 용이하다.
- 다른 프레임워크나 라이브러리와 혼용하여 사용할 수 있다.
- 뛰어난 Garbage Collection, 메모리 관리, 성능을 가지고 있다.

#### 단점
- 보여지는 부분만 관여하기 때문에 데이터 모델링, Routing, Ajax 등의 기능을 제공하지 않는다.
- view 외 기능들은 직접 구현하거나 라이브러리를 사용하여 구현해야 한다.
- 뛰어난 Garbage Collection, 메모리 관리, 성능을 가지고 있다.

<br/>

### jQuery VS React

#### 크기
jQuery 라이브러리의 크기가 React에 비해 18% 작기 때문에 페이지 로드 시간에 영향을 미친다.

<br/>
  
#### 속도
jQuery의 경우, 기존 DOM을 사용하기 때문에 크고 복잡한 웹일 경우 DOM 업데이트에 많은 시간이 소요될 수 있다.

React의 경우, Virtual DOM을 사용하기 때문에 DOM 업데이트 속도가 빨라진다.

<br/>
  
#### NPM Packages
jQuery에 비해 React가 사용할 수 있는 NPM Package가 훨씬 많기 때문에 타사 라이브러리를 사용할 때 React가 더 유리하다.

<br/>
  
#### 대규모 웹
jQuery의 경우, 스파게티 코드를 만들 수 있고 DOM 업데이트 시간이 느려진다.

React의 경우, 컴포넌트 구조로 인해 코드를 유지, 관리하기에 좋고 가상 DOM 사용으로 DOM 업데이트 프로세스가 빨라진다.

<br/>

##### [참고]
[1](https://velog.io/@stampid/React%EB%9E%80)
[2](https://dev-yakuza.posstree.com/ko/react/create-react-app/react/)
[3](https://goddaehee.tistory.com/296?category=395445)
[4](https://www.educative.io/answers/jquery-vs-react)

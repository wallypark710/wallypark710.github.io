---
layout : post
title : "[React] Life Cycle"
date : 2019-01-21 09:00:00
---

# LifeCycle API



## Intro

처음 리액트를 개발할 때는 모든 로직을 render함수에 전부 구현했다. 간단한 프로젝트에서는 별 문제가 없었지만 API를 연결하고 나니 문제가 생기기 시작했다. API를 불러오는동안 아무것도 그려지지 않은 화면을 보고있어야 했다. 다루는 데이터가 많아질수록 로딩시간은 길어져만 갔다. 당장 바로 보여져야하는 데이터가 아님에도 기다려야 했다. 급하지 않은 데이터의 로딩이 끝나기 전에 먼저 돔을 그려줬으면 했다.

해결책은 리액트 라이프사이클을 이해하는 것이었다. 이젠 리액트 개발을할때 가장 중요한 부분중에 하나가 바로 라이브사이클이라 생각한다. 라이프사이클이란  컴포넌트가 브라우저에 나타날때, 사라질때, 업데이트될때 호출되는 API이다. 이는 각각의 이벤트가 발생할때 항상 실행된다. 라이프사이클을 잘 파악하고 있으면 리액트의 동작 흐름을 명확하게 알 수 있고, 원하는 흐름을 만들어 낼 수 있다. 또한 라이프사이클을 잘 이용하면, 성능을 향상 시킬 수 있다.






## Component 생성

##### *1. constructor()*

##### *2. render()*

##### *3. componentDidMount()*

```javascript
componentDidMount(){
  // 외부 라이브러리 연동: D3, masonry, etc
  // 컴포넌트에서 필요한 데이터 요청: Ajax, GraphQL, etc
  // DOM 에 관련된 작업: 스크롤 설정, 크기 읽어오기 등
}
```





## Component 업데이트

##### *1. componentWillReceiveProps()*

```javascript
//컴포넌트가 새로운 props를 받게됐을 때 호출한다. 새로 받게될 props는 nextProps로 조회할 수 있다.
componentWillReceiveProps(nextProps){
	//this.props는 아직 바뀌지 않은 상태이다.
}
```

##### *2. shouldComponentUpdate()*

```javascript
//컴포넌트가 변화가 있는지 없는지를 판단. 변화가 없다면 render()함수를 호출하지 않는다.
shouldComponentUpdate(nextProps, nextState){
    //return false를 하면 업데이트를 하지 않음.
    //기본적으로 true를 반환함.
    return true;
}
```

##### *3. componentWillUpdate()*

```javascript
//이 함수는 shouldComponentUpdate가 true일때만 호출된다.
componentWillUpdate(nextProps, nextState){
    ...
}
```

##### *4. render()*

##### *5. componentDidUpdate()*

```javascript
componentDidUpdate(prevProps, prevState, snapShot){
//이 시점에서 this.props 와 this.state가 바뀌어있다. 그리고 파라미터를 통해 이전 props와 state를 조회할 수 있다.
}
```





## Component 제거

##### *1. componentWillUnmount*

```javascript
// 컴포넌트가 더 이상 필요하지 않게 되면 이 함수가 호출된다.
componentWillUnmount(){
    //이벤트, setTimeOut, 외부 라이브러리 인스턴스 제거
}
```




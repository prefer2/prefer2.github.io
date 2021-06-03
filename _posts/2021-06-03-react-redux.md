---
title: "[React] Redux란?"
date: 2021-06-03 21:25:28
categories: React
tags: react redux
use_math: true
---

<p align="center"><img src="https://user-images.githubusercontent.com/67692759/110626820-8ba05800-81e4-11eb-97cb-9c2f45d93455.jpg"  width="400" height="400"></p>
## Redux

애플리케이션 상태를 관리하기위한 오픈 소스 JavaScript 라이브러리

Redux 는 자신이 관리하는 데이터 모음인 `상태(state)` 를 `스토어(Store)` 라는 저장소에 두고 이 상태를 변경할 수 있는 것은 `액션(action)` 으로 제한한다. 액션은 단순한 문자열이며 이 액션으로 상태를 변경하기 위해서는 `스토어(Store)` 에 `디스패치(dispatch)` 하는 행위가 필요하다.

### 사용 원칙

1. 애플리케이션 상태는 모두 한 곳에서 집중 관리된다. (동기화 필요 ✘)
2. 상태는 불변(읽기 전용) 데이터 이며, 오직 액션 만이 상태 교체를 요청 할 수 있다. (예측 가능)
3. 리듀서(함수)를 통해 상태의 최종 값만 설정한다. (단순화)

## 구성요소

- State (상태)
- Store (스토어)
- Action (액션)

![그림2](https://user-images.githubusercontent.com/67692759/120644063-e084ff00-c4b1-11eb-9a96-663b13075b07.png)


### state

컴포넌트 내부에서 사용하는 데이터의 집합

### store

state의 전체 트리를 가지고 있다. state 관리를 하는 전용 장소로, state들이 객체 형식으로 저장된다

스토어는 언제나 단 한개이다.

### action

state에 어떤 변화가 필요할 때 action을 발생시킨다. 

하나의 객체로 표현되고, 액션 객체는 `type` 필드를 필수적으로 가지고 있어야 한다.

### reducer

변화를 일으키는 함수(function). `state`와 `action` 파라미터를 받아옴.

현재 상태와 전달받은 액션을 참고하여 새로운 상태를 만들어서 반환한다.

리듀서는 순수 함수여야 한다. 순수 함수란 동일한 파라미터를 주었을 때 항상 같은 값을 리턴하고, 외부의 상태를 변경하지 않음을 뜻한다.

`불변성(Immutability)`을 고려하여 상태를 변경해야한다. 이를 위해 상태 자체를 변경하는 것이 아니라 복제하여 변경한다.

### 주요 메서드

`createStore(reducer)` 를 통해 store를 생성

`getState()` 를 통해 state를 가져옴

`dispatch(action)` 을 사용하여, store의 reducer에 action을 전달. redux의 상태 변화를 일으킴

## 참조

[https://opentutorials.org/module/4078/24935](https://opentutorials.org/module/4078/24935)

[https://blog.javarouka.me/2019/04/02/redux-saga-1/](https://blog.javarouka.me/2019/04/02/redux-saga-1/)

[https://이듬.run/react-master/lecture/rd-redux.html#상태-관리의-필요성](https://xn--xy1bk56a.run/react-master/lecture/rd-redux.html#%E1%84%89%E1%85%A1%E1%86%BC%E1%84%90%E1%85%A2-%E1%84%80%E1%85%AA%E1%86%AB%E1%84%85%E1%85%B5%E1%84%8B%E1%85%B4-%E1%84%91%E1%85%B5%E1%86%AF%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A5%E1%86%BC)

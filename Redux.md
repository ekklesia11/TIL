# 리덕스

---

## 리덕스란?

자바스크립트의 예측 가능한 상태 저장소 이다.



## actions

a plain JavaScript object that has a type field.

action = event

centralized store for state



Action object

```react
const addTodoAction = {
  type: 'todos/todoAdded',
  payload: 'Buy milk'
}
```



Action creator

```react
const addTodo = text => {
  return {
    type: 'todos/todoAdded',
    payload: text
  }
}
```



## reducers

a function that receives the current state and an action object, decides how to update the state if necessary, and returns the new state: (state, action) => newState

Must Rules:

1. state 와 action 에 의거해 새로운 state 를 계산 해야한다.
2. 항상 이뮤터블하게 업데이트되어야 한다.
3. 비동기적인 로직은 사용할 수 없다.



## store

an object in where the state lives.

reducer 를 통해서 생성되며, getState 메소드를 이용해 현재 상태를 가져올 수 있다.



## dispatch

store 가 가지는 메소드

스토어의 상태를 변경할 수 있는 유일한 메소드: store.dispatch( action object )

ex)

```react
store.dispatch({ type: 'counter/increment' })

console.log(store.getState())
// {value: 1}
```

Thus, dispatching actions === "triggering an event"

일반적으로 action creator 를 호출해 dispatch 한다.

```react
const increment = () => {
  return {
    type: 'counter/increment'
  }
}

store.dispatch(increment())

console.log(store.getState())
// {value: 2}
```



## selectors

functions that know how to extract specific pieces of informantion from a store state value.

As an application grows bigger, this can help avoid repeating logic as differenct parts of the app need to read the same data:

```react
const selectCounterValue = state => state.value

const currentValue = selectCounterValue(store.getState())

console.log(currentValue)
// 2
```


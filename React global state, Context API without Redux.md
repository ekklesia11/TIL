# React global state, Context API without Redux

---

React 를 사용하면서 하나 두개 depths 정도의 컴포넌트는 크게 문제가 되지 않았다. Depth 가 깊어질 수록 props 의 전달이 비효율적으로 어려워진다. 버스도 아닌데 계속 타고타고 또 타고 내려줘야만 props 를 사용할 수 있다.

그래서 우리는 Redux 나 MobX 를 활용해서 어떤 컴포넌트에서든 원하는 변수를 가져다 쓸 수 있도록 설계했었다.

React 16.3.0 버전에서 이러한 문제를 해결하기 위해 Context API 를 이용해서 어디서든 호출해서 사용할 수 있도록 제공한다. Hook을 사용하는 방법으로 useContext() 나 useReducer() 와 같은 기능들이 제공되고, 이번에는 간단하게 변수만 가져와 사용하는 방법을 알아보도록 하자.



## Context 만들기

```react
# src/ContextAPI.js
import { createContext } from "react";

const ContextAPI = createContext({ defaultValue: "checked!" });

export const ContextProvider = ContextAPI.Provider;
export const ContextConsumer = ContextAPI.Consumer;
export default ContextAPI;
```

1. 먼저 createContext 를 이용해 context 를 만들어준다. 여기서 default value 를 넣어줘야만 한다. String 이거나 Object 이거나는 상관 없다.
2. 그리고 나서 어디서든 해당 context 를 import 할 수 있도록 export 해준다.
3. Provider 는 context 를 받을 수 있는 모든 컴포넌트를 감싸줄 역할을 한다.
4. Consumer 는 원하는 컴포넌트에서 Provider 로 넘겨진 context 를 가져오는 역할을 한다.



## Parent Component 에서 전달하기

```react
# src/App.js
import React from "react";
import "./App.css";

import FirstChild from "./FirstChild";
import { ContextProvider } from "./ContextAPI";

function App() {
  const user = {
    name: "daniel",
    age: 25,
    occupation: "developer"
  };

  return (
      <ContextProvider value={user}>
        <FirstChild />
      </ContextProvider>
  );
}

export default App;
```

1. 전달해주고 싶은 data 가 있다면 Provider 로 감싸서 내려준다.
2. FirstChild 뿐만 아니라 하위 모든 컴포넌트에서 해당 data 를 받을 수 있다.



## Second Child Component 에서 props 받기

```react
# src/FirstChild.js
import React from "react";

import SecondChild from "./SecondChild";

const FirstChild = () => {
  return (
    <div>
      App > First child component
      <SecondChild />
    </div>
  );
};

export default FirstChild;

# src/SecondChild.js
import React, { useContext } from "react";

import ContextAPI, { ContextConsumer } from "./ContextAPI";

const SecondChild = () => {
  const { name, age, occupation } = useContext(ContextAPI);

  console.log("props called inside of a function", name, age, occupation);
  
  return (
    <div>
      App > First child component > Second child component
      <ContextConsumer>
        {props => {
          console.log("props called for rendering", props);
          return <div>{props.name}</div>;
        }}
      </ContextConsumer>
    </div>
  );
};

export default SecondChild;
```

1. 컴포넌트로 원하는 data 를 바로 받아서 보여주려면 Consumer 를 활용해 보여줄 수 있다.
2. 만약 컴포넌트에서 다른 작업이 필요하다면 useContext 를 활용해 data 를 가져와 가공해서 사용하면 된다.



너무 쉽다!

이렇게 글로벌하게 변수를 사용하거나 parent-child 에 관계없이 props 를 전달하고 전달 받을 수 있다. 이렇게 react 가 가진 스토어 시스템을 활용하면 훨씬 편하게 개발할 수 있다.
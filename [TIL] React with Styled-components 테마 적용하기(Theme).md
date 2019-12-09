# [TIL] React with Styled-components 테마 적용하기(Theme)

---

요즘 react에 styled components적용하는 재미에 빠졌다. 일단 좋은점은 CSS 파일을 만들지 않아도 된다는 것 ㅎㅎ 그리고 컴포넌트 파일에서 바로바로 적용되는 스타일이기 때문에 프론트 만지는 재미가 있다! 기본적으로 전체 어플리케이션에 CSS 를 적용하는 방법과 반복적으로 사용할 테마를 직접 만들고 적용하는 방법을 알아보자!

```bash
$ npx create-react-app my-app
```

```bash
$ npm i -D styled-components
```

이렇게 리액트와 스타일드 컴포넌트를 만들고 App.js를 열어준다.



## App.js

```react
import React from 'react';
// 전체 테마를 적용하기 위해 필요한 컴포넌트를 가져온다.
import { ThemeProvider, createGlobalStyle } from 'styled-components';

const App = () => {
  return <div>hello world</div>
}
```

ThemeProvider 는 App 에 포함될 모든 컴포넌츠에게 테마를 전달해줄 wrapping component 이다.

createGlobalStyle 은 my-app 전체에 적용할 스타일을 만들어주는 컴포넌트이다.



```react
import React from 'react';
import { ThemeProvider, createGlobalStyle } from 'styled-components';

// 임의의 컴포넌트를 가져온다.
import AnyComponent from './AnyComponent';

// ThemeProvider 로 모든 컴포넌트들을 감싸준다.
// GlobalStyle 은 컴포넌트처럼 가장 위쪽에 넣어준다.
const App = () => {
  return (
    <ThemeProvider theme={theme}>
      <GlobalStyle />
    	<AnyComponenet />
    </ThemeProvider>
  );
}

// createGlobalStyle 은 `` <== 백틱으로 CSS 와 같은 방식으로 작성한다.
const GlobalStyle = createGlobalStyle`
  html {
		font-size: 16px;
	}

  body {
    margin: 0;
    padding: 0;
  }
`;

// 테마는 객체이므로 키값과 적용될 스타일을 스트링으로 작성한다.
const theme = {
  color: {
    primary: 'skyblue',
    secondary: 'green',
  },
  size: {
    sm: '20px',
    md: '50px',
    lg: '100px',
  }
}
```



## AnyComponent.js

```react
import React from 'react';
import styled from 'styled-components';

const AnyComponent = () => {
  return (
    <Container>
      <Title>
      	Hello, styled-component!
      </Title>
    	<Contents>
      	Theme applied contents are here. Easy-peasy!
      </Contents>
    </Container>
  );
}

const Container = styled.div`
  padding: 50px;
`;

const Title = styled.h1`
  color: ${props => props.theme.color.primary};
`;

const Contents = styled.p`
  color: ${props => props.theme.color.secondary};
  font-size: ${props => props.theme.size.md};
`;
```



살짝 자세히 들여다 보면 생각보다 어렵지 않게 적용할 수 있다. 눈으로 보는 것보다 한번 직접 코딩하면서 브라우저에 띄워보면 바로 이해가 된다. 리액트에 자신감을 가지고 웹페이지를 만들어보자! 고고!
# React Native

---

> 자바스크립트로 모바일 어플리케이션을 만들 수 있는 라이브러리



### 어떻게 동작할까?

아이폰이나 안드로이드에서 작동하려면 네이티브 언어가 있다. 

아이폰은 Swift 나 Object-C, 안드로이드는 Java 나 Kotlin 이 있다.

하지만 위와 같은 언어는 러닝커브가 높다. 그래서 자바스크립트를 이용해서 모바일 어플리케이션을 만들 수 있다.

그냥 자바스크립트로는 작동하지 않고 자바스크립트를 네이티브 언어로 감싸주어야 한다. 그렇기 때문에 빌드와 컴파일이 필요하다.

리액트 네이티브의 경우,

1. 자바스크립트를 빌드하면 아이오에스와 안드로이드 파일이 나온다. 각 모듈에 따라 다를 수는 있다.
2. 하지만 높은 생산성!!



단점

1. 감싸주어야 하기 때문에 다소 무거워 진 어플리케이션이 될 수 있다.
2. 모바일 환경과 연결하기가 까다롭다. (하드웨어와 연결)



### 리액트 네이티브 시작하기

CRNA create react native app >> expo init

- 편하다(엄청엄청) mapview 등
- 맥이 없어도 개발 가능(배포할 때는 필요)
- 단점은 엄청 무겁다.
- 네이티브 API를 쓸 때 제약이 많다.
- 그럼에도 불구하고 쓸 이유가 많다.

React-native init

- 가볍다
- 네이티브 API 가 편하다.
- 커스텀이 가능하다. 그래서 일일이 다 해줘야 한다.



### 라우팅의 중요성

- 네이게이션이 필수이다.
- App state가 중요하다. 홈버튼을 눌렀을 때, 일시정지? 펜딩? 바로 이러한 부분 때문에 스테이트가 중요하다
- 리액트와 마찬가지로 Life Cycle이 존재한다. 또한 스크린 라이프 사이클이 있다. will focus, did focus, will blur, did blur
- 한 화면에 각각의 컴포넌트는 각각의 라이프사이클을 따라가고 그 화면 하나도 라이프 사이클을 가진다. 그게 위에 나열한 포커스 블러 등이다.
- UX 디자인이 중요하다.



### 네비게이션

1. 스택 네비게이션

   - 하나하나씩 쌓이는 방식

2. 바텀 탭 네비게이션

   - 하단 메뉴

   > 가장 아래에 바텀 탭을 깔고 그 위에 스택을 쌓는 방법이 일반적이다.

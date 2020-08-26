# React Strict Mode

---

StrictMode 는 애플리케이션 내의 가능한 문제를 미리 하이라이팅 해주는 툴이다.

자식 컴포넌트들의 상태를 추가적으로 체크하고 감시한다.

StrictMode 는 개발자모드에서만 동작하며, 프로덕션 레벨에는 반영되지 않는다.



1. 문제가 될 만한 라이프사이클을 가진 컴포넌트를 찾아낸다.
   - Deprecated lifecycle 를 사용한 third-party library 가 있을 때 유용하다.
2. Legacy string ref API 사용시 경고
   - String 타입의 ref API 를 사용했을 때 찾아낸다.
3. Deprecated DOM node 사용시 경고
4. 예상 밖의 사이드 이펙트를 찾아낸다.
   - Render phase: 어느 부분이 변경되었는지 확인한다. - 렌더를 호출해 이전 렌더 결과와 비교한다.
   - Commit phase: 변경된 부분을 반영한다.
     - 새로운 react dom 를 수정/추가 하고 기존의 dom node 를 삭제한다. 
     - 여기서 라이프사이클이 실행된다.
   - Commit phase 는 매우 빠르게 실행되고 rendering phase 는 보통 느리게 실행 된다. 그 이유는 render phase 에서 렌더링해야 하는 부분을 브라우저 화면의 블록킹 없이 가져와 비교하기 때문이다. 이 과정에서 라이프사이클을 여러번 호출해 committing 전에 발생할 수 있는 에러나 문제를 발견할 수 있다.
   - Strict Mode 가 자동으로 사이드이펙트를 찾아내기 보다는 사용자가 조금 더 쉽게 에러나 이슈를 발견할 수 있도록 돕는다. 이러한 이유에서 의도적으로 double-invoking 이 발생한다. - 개발자모드에서만 일어나며 프로덕션 레벨에서 double-invoking 은 일어나지 않는다.
5. Legacy context API 를 찾아낸다.



Refs 를 사용해야 할 때:

1. 포커스나 텍스트를 선택하고, 미디어를 플레이 할 때
2. 원하는 애니메이션을 동작시켜야 할 때
3. 서드파티 돔 라이브러리를 조작해야 할 때 (믹싱)


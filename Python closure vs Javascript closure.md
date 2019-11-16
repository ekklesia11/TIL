# Python closure vs Javascript closure

---

## Javascript Closure

자바스크립트에 익숙해져 있다보니 파이썬과의 차이점을 인지하지 못하고 면접때 자바스크립트 개념으로 코딩테스트를 봤다.

왜 접근이 안되는 걸까...

정말 진땀을 빼면서 결국 풀지 못하고 인터뷰를 마쳤다.



### Closure 란?

정의된 함수 안에 또 다른 함수, nested function 를 정의해 주고, 이 내부함수는 외부함수의 변수에 접근이 가능하다. 일반적으로 클로저(closure) 함수는 외부함수가 내부함수를 리턴하게 된다. 자바스크립트의 경우 리턴된 내부함수가 외부함수의 변수를 계속 가지고 있을 수도 있다.

포인트는, 자바스크립트는 아래처럼 외부함수에 선언된 변수를 내부함수에서 외부함수의 변수에 접근해서 읽기 뿐만 아니라 변경도 가능하다.

```javascript
function outerFunc() {
	let x = 10;
	function innerFunc() {
		x = x + 5;
		return x;
	}
	return innerFunc();
}

outerFunc();
>> 15
```



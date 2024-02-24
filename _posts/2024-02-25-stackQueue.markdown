---
layout: post
title:  "[알고리즘] Stack & Queue"
date:   2024-02-25
categories: jekyll update
---

<br/>
<br/>

### **# 스택(Stack)?**

<br/>

스택은 데이터를 집어넣을 수 있는 선형(Linear) 자료 구조로, 가장 나중에 넣은 데이터를 가장 먼저 꺼냅니다.  (LIFO_Last In First Out) 아래가 막혀있는 통이 있고 거기에 1,2,3 을 넣는다면, 1을 빼고 싶을 때 가장 나중에 들어갔던 3과2를 먼저 꺼내야합니다.  들어가는 입구와 자료가 나오는 출구가 동일 지점이라고 보시면 됩니다.스택은 서로 관계가 있는 여러 작업을 연달아 수행하며 이전의 작업 내용을 저장해둘 필요가 있을 때 사용됩니다. 스택과 관련된 주요 메소드는 아래와 같습니다.

<br/>

	- Push(넣을 아이템) : 데이터를 넣을 때 사용합니다.
	- Pop() : 데이터를 꺼내는 작업을 할 때 사용합니다.
	- Peek() : 스택의 가장 위에 있는 항목을 조회할 때 사용합니다.

<br/>

여기 ㅁ을 사용해 빈 스택을 만들어보겠습니다.

<br/>

```
ㅁ
ㅁ
ㅁ
ㅁ

```

<br/>

그럼 여기에 push를 사용해 A,B를 넣었다는 가정하에 pop()을 사용한다면 어떤 게 나올까요? 스택은 나중에 들어간 것이 가장 먼저 나오기 때문에 이 경우에는 B가 나올 겁니다.

<br/>

```
ㅁ   ㅁ
ㅁ   ㅁ
ㅁ   B
A   A

```

<br/>

자바스크립트에서는 배열을 사용해 스택을 사용하기 때문에, 코드로 표현한다면 아래와 같습니다. constructor는 클래스의 생성자 함수로 객체를 생성할 때 자동으로 호출되어 생성된 객체의 초기화를 담당합니다. 여기서도 마찬가지로 constructor함수에서 스택 요소 저장에 사용될 배열을 초기화 했습니다. 각 줄에 대한 설명은 주석으로 첨부하겠습니다.

<br/>

```javascript

class Stack { 
	constructor() { 
		 //초기화 
		this._arr = [];
	} 
	push(item) { 
		 //Stack 인스턴스의 _arr 배열을 참조해 push()를 사용했습니다. 
		this._arr.push(item);
	} 
	pop() {
		//배열의 마지막 요소를 제거하고 값을 반환합니다. 여기에서도 _arr의 배열을 참조했습니다. 
		return this._arr.pop();  
	} 
	peek() {
		//배열의 마지막 요소를 참조해 반환합니다. 배열의 길이에서 1을 빼면 마지막 요소의 인덱스가 됩니다. 단, peek는 반환해도 pop과 달리 제거하지 않습니다.
		 return this._arr[this._arr.length - 1]; 
	 }  
} 
	 const stack = new Stack(); 
	 
	 stack.push(1); 
	 stack.push(2); 
	 stack.push(3); 
	 stack.pop(); // 3

```

<br/>

스택은 보통 아래와 같은 사례에서 사용됩니다.

<br/>

	- 재귀 알고리즘(재귀적으로 함수를 호출해야하는 경우, 임시 데이터를 스택에 넣어줍니다.)
	- 메소드 호출 스택
	- 웹 브라우저 방문기록(뒤로가기)
	- 실행취소
	- 역순 문자열 만들기
	- 후위 표기법 계산
	- 수식의 괄호 검사

<br/>

### **# 큐(Queue)?**

<br/>

큐는 스택과 마찬가지로 데이터를 저장하기 위한 선형(Linear) 자료구조지만, 데이터를 꺼내는 건 스택과 반대입니다. 큐는 가장 먼저 들어간 데이터를 가장 먼저 꺼냅니다.(FIFO_First In first Out)  스택이 아래가 막힌 원통이라면, 큐는 매표소를 예로 들 수 있습니다. 가장 먼저 온 사람이 표를 살 수 있듯이 큐 또한 가장 먼저 들어간 데이터가 우선적으로 나옵니다. 큐는 순서대로 처리해야하는 작업을 임시로 저장해주는 버퍼(buffer)로서 많이 사용됩니다. 큐와 관련된 용어는 아래와 같습니다.

<br/>

- front : 데이터를 꺼내는 쪽(맨 앞) 입니다.
- rear: 데이터를 넣는 쪽(맨 뒤) 입니다.
- enqueue(넣을 아이템) : 데이터를 넣을 때 사용합니다.
- dequeue() :  데이터를 꺼내는 작업을 할 때 사용합니다.
- peek() : 큐의 가장 앞에 있는 항목을 조회할 때 사용합니다.

<br/>

여기에서도 ㅁ을 사용해 빈 큐를 반들어보겠습니다.

<br/>

```
ㅁ ㅁ ㅁ ㅁ
```

<br/>

그럼 여기에 enqueue를 사용해 A,B를 넣었다는 가정하에 pop()을 사용한다면 어떤 게 나올까요? 스택은 나중에 들어간 것이 가장 먼저 나오기 때문에 이 경우에는 B가 나올 겁니다.

```

A B ㅁ ㅁ

```

<br/>

큐도 배열을 사용해 코드를 짜본다면 아래와 같습니다. 

<br/>

```javascript

class Queue { 
	constructor() { 
		this._arr = []; 
	} 
	enqueue(item) { 
		this._arr.push(item); 
	} 
	dequeue() { 
		return this._arr.shift(); //shift() 배열의 앞부분 삭제
	} 
} 

const queue = new Queue(); 

queue.enqueue(1); 
queue.enqueue(2); 
queue.enqueue(3); 
queue.dequeue(); // 1


```

<br/>

큐는 보통 순서가 중요한 상황이나 데이터가 들어온 순서대로 처리되어야 할 때 주로 사용됩니다. 주로 아래와 같은 상황에서 사용할 수 있습니다.
- 작업 스케줄링
- 데이터 스트림 처리
- 인쇄 작업 관리
- 고객 서비스 대기열 


<br/>

📌 참고

- [https://helloworldjavascript.net/pages/282-data-structures.html](https://helloworldjavascript.net/pages/282-data-structures.html)
- [자료구조알고리즘-스택-큐](https://velog.io/@roro/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EC%8A%A4%ED%83%9D-%ED%81%90)
- [https://xionwcfm.tistory.com/129](https://xionwcfm.tistory.com/129)
- [https://chamdom.blog/queue-using-js/](https://chamdom.blog/queue-using-js/)

<br/>
<br/>
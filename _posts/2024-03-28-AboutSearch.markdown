---
layout: post
title:  "[알고리즘] 그리디와 이분탐색 알고리즘"
date:   2024-03-28
categories: jekyll update
---

<br/>
<br/>


### #탐욕 알고리즘(Greedy algorithm)? 

<br/>

가장 알맞은 해인 '최적해'를 찾기 위한 방법으로, **여러 경우 중 하나를 결정해야 할 때마다 그 순간에 최적이라고 생각되는 걸 선택해나가는 방식으로 진행해 최종적인 해답에 도달한다.** (눈 앞에 있는 최선을 '탐욕스럽게' 취하는 알고리즘.) 그리디 알고리즘은 다양한 최적화 문제를 해결하는데 사용된다. 전체 문제를 부분으로 쪼개고, 각 부분에서 최선인 선택을 함으로써 전체적인 문제를 해결한다. 

<br/>

때문에 순간 마다 하는 선택은 그 순간에 대해 지역적으로는 최적이지만, 그 선택들을 계속 수집해 최종적인(전역적인) 해답을 만들었다고 해서 이게 최적이라는 보장은 없다. 하지만 그리디 알고리즘을 적용할 수 있는 문제들은 지역적으로 최적이면서 전역적으로 최적인 문제들이다. 왜냐하면 그리디 알고리즘이 효과적으로 작동하려면 문제가 📎'탐욕스러운 선택 속성(Greedy Choice Property)'과 '최적 부분 구조(Optimal Substructure)'를 갖추고 있어야 하기 때문이다. 

<br/>

이런 성질을 만족하는 문제들에서는 지역적으로 최적인 결정이 곧 전역적으로도 최적인 결정이 된다. 최소 신장 트리(Minimum Spanning Tree) 문제나 최단 경로(Shortest Path) 문제가 이에 해당되며,  이런 문제들에서는 각 단계에서의 최적의 선택이 전체 문제의 최적 해결책으로 이어지게 된다.

<br/>
---

📎 
- 탐욕스러운 선택 속성(Greedy Choice Property): 각 단계의 선택이 이후 선택에 영향을 주지 않는다.
- 최적 부분 구조(Optimal Substructure): 문제의 최적 해결책이 그 문제의 부분 문제의 최적 해결책으로부터 구성될 수 있는 성질.

---

<br/>

위의 조건을 충족하지 않더라도, 그리디 알고리즘은 구현이 쉽고 빠르기 때문에 다양한 문제에 활용할 수 있다. 특히 반드시 최적의 해를 구하지 못하더라도 어림 짐작해서 답을 구해야하는 경우에도 사용된다. 예를 들어 인공지능에 활용되는 알고리즘 중 휴리스틱 탐색(Heuristic Search)이나 빔 탐색(Beam Search), A* 알고리즘 등에서 탐욕 알고리즘이 적용되고 있다.


<br/>

### #이진 검색 알고리즘(Binary Search Algorithm)?


<br/>

**오름차순으로 정렬된 리스트에서 특정한 값의 위치를 찾는 알고리즘이다.** 처음 중간의 값을 임의의 값으로 선택하여, 그 값과 찾고자 하는 값의 크고 작음을 비교하는 방식. 처음 선택한 중앙 값이 만약 찾는 값보다 크면 그 값은 새로운 최댓값이 되며, 작으면 그 값은 새로운 최솟값이 된다. 정렬된 리스트에만 사용할 수 있는 단점이 있지만, 검색이 반복될 때마다 목표값을 찾을 확률은 두배가 되므로 속도가 빠르다면 장점이 있다. (배열의 중간 요소를 선택하고 찾고자 하는 값과 비교, 탐색 범위를 절반으로 줄여나가는 방식.) 

<br/>

위키에서 제공하는 📎의사코드는 아래와 같다.

<br/>

---

📎 의사코드(Pseudo Code)
: 프로그램을 작성할 때 각 모듈이 작동하는 논리를 표현하기 위한 언어. 프로그래밍 언어 문법에 따라 쓰인 게 아니라 일반적인 언어로 코드를 흉내 내어 알고리즘을 써놓은 코드. 말 그대로 흉내만 내는 코드이기 때문에 실제로는 실행할 수 없다. 



---

```javascript

BinarySearch(A[0..N-1], value, low, high) {
  if (high < low)
    return -1 // not found
  mid = (low + high) / 2
  if (A[mid] > value)
    return BinarySearch(A, value, low, mid-1)
  else if (A[mid] < value)
    return BinarySearch(A, value, mid+1, high)
  else
    return mid // found
}

```


<br/>


📌 참고

- [https://ko.wikipedia.org/wiki/%ED%83%90%EC%9A%95_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98](https://ko.wikipedia.org/wiki/%ED%83%90%EC%9A%95_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98)
- [https://yozm.wishket.com/magazine/detail/2478/](https://yozm.wishket.com/magazine/detail/2478/)
- [https://ko.wikipedia.org/wiki/%EC%9D%B4%EC%A7%84_%EA%B2%80%EC%83%89_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98](https://ko.wikipedia.org/wiki/%EC%9D%B4%EC%A7%84_%EA%B2%80%EC%83%89_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98)
- [https://ko.wikipedia.org/wiki/%EC%9D%98%EC%82%AC%EC%BD%94%EB%93%9C](https://ko.wikipedia.org/wiki/%EC%9D%98%EC%82%AC%EC%BD%94%EB%93%9C)


<br/>
<br/>
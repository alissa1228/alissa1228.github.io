---
layout: post
title:  "[알고리즘] 완전탐색 알고리즘, Brute Force(브루트 포스)"
date:   2024-03-14
categories: jekyll update
---

<br/>
<br/>

## #브루트 포스(Brute Force)?
---

<br/>

브루트 포스는 완전탐색 알고리즘으로써, **모든 경우의 수를 탐색 하면서 요구조건을 충족하는 결과만 가져오는 방식**이다. 영문 그대로(brute:난폭한 / force: 힘) 난폭하게 하나씩 다 때려박으면서(…) 탐색한다고 보면 된다. 어떤 방식으로든 전체 탐색으로 문제를 해결한다면 해당 알고리즘으로 풀었다고 할 수 있다. 

<br/>

+) Q. 완전 탐색 알고리즘 안에 브루트 포스가 있는건가요? 

👾 ChatGPT : 

  완전 탐색(Exhaustive Search) 알고리즘은 모든 가능한 경우의 수를 체크하여 문제의 해답을 찾는 방법입니다. 브루트 포스(Brute Force)는 이 완전 탐색의 방법 중 하나로, 가능한 모든 경우의 수를 시험해보며 문제의 해답을 찾는 가장 기본적이고 직접적인 접근 방식을 말합니다. 즉, **브루트 포스는 완전 탐색 알고리즘의 한 형태**로 볼 수 있습니다.

  완전 탐색 알고리즘은 모든 경우를 체크하기 때문에 해답을 찾을 수 있다는 것을 보장하지만, 경우의 수가 많을 때는 시간이 매우 오래 걸릴 수 있습니다. 반면, 브루트 포스는 해답을 찾기 위해 가능한 모든 방법을 단순하게 시도해보는 것이므로, **구현이 간단하다는 장점**이 있습니다. 다만, 브루트 포스 방식도 **경우의 수가 많아질수록 비효율적**일 수 있습니다. 따라서, 더 효율적인 알고리즘을 고려해볼 필요가 있습니다.

<br/>

<br/>

## #브루트 포스의 종류
---

<br/>

브루트 포스는 

데이터가 순차적으로 나열되어 있는 선형구조 탐색과 데이터 간의 관계가 계층적이거나 네트워크 형태를 이루는 비선형구조 탐색으로 나뉜다.

<br/>

- 선형 구조
    - 순차 탐색
        - 단순하게 배열 처음부터 내가 찾는 값이 있는지 확인.
        - O(n)의 시간 복잡도를 갖는다.
<br/>

- 비선형 구조
    - DFS(Depth First Search)
        - 트리나 그래프를 탐색하는 기법으로, 시작 노드에서 자식 노드를 순서대로 탐색하며 **깊이**를 우선으로 탐색하는 알고리즘
        - DFS의 기본 탐색 과정은 **특정 정점에서 시작하여 역추적(backtracking) 하기 전에 각 분기를 따라 가능한 한 멀리 탐색**하는 것.
        - 반복문이나 재귀문을 사용해 구현한다. (ex- stack)
    - BFS(Breadth First Search)
        - DFS처럼 트리나 그래프를 탐색하는 기법으로, 시작 노드에서 자식 노드를 순서대로 탐색하며 **너비**를 우선으로 탐색하는 알고리즘
        - 완전탐색 알고리즘에 속하며 같은 거리에 있는 모든 노드를 탐색 후, 다음 거리의 노드를 탐색하기 시작하는 방식. (그래프 최단거리를 구하는 문제에 활용될 수 있다)
        - 주로 Queue와 While 반복문을 통해 문제를 해결.

<br/>

아래는 0-9를 사용해 4개의 숫자로 구성된 자물쇠 비밀번호 찾기가 대표적인 브루트 포스로 풀어볼 수 있는 예이다. 1234으로 설정된 비밀번호를 찾아야한다는 가정하에 브루투 포스 알고리즘을 사용한다면 아래와 같다. 

<br/>

```jsx
function findPassword() {
    const targetPassword = [1, 2, 3, 4]; // 찾고자 하는 비밀번호
    for (let i = 0; i <= 9999; i++) {
        //4자리 숫자를 개별 자릿수로 분해하여 배열로.
        //숫자를 10, 100, 1000으로 나누어 각 자릿수를 위치에 맞게 조정한 후, 10 연산을 적용하여 각 자릿수를 추출
        let password = [Math.floor(i / 1000) % 10, Math.floor(i / 100) % 10, Math.floor(i / 10) % 10, i % 10];
        if (password[0] === targetPassword[0] && password[1] === targetPassword[1] &&
            password[2] === targetPassword[2] && password[3] === targetPassword[3]) {
            return password.join(''); // 목표 비밀번호와 일치할 경우
        }
    }
    return null; // 목표 비밀번호를 찾지 못한 경우
}

console.log(findPassword());


```

<br/>

📌 참고

- https://go-coding.tistory.com/67
- https://song-ift.tistory.com/259
- https://foreverhappiness.tistory.com/104
- https://yerinpy73.tistory.com/29
- https://olrlobt.tistory.com/35
- https://olrlobt.tistory.com/41
- https://olrlobt.tistory.com/33


<br/>
<br/>
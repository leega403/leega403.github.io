---
layout: post
title:  "[Algorithm]-3.Merge sort (병합정렬)"
subtitle:   "Merge sort"
categories: programming
tags: algorithms
comments: true
---
## 개요
> 이 글은 머지소트에 대해 정리한 글입니다.

머지소트도 재귀함수로 표현한 함수다. 아래 수도코드를 보면, 머지소트는 정렬안된 리스트 A와, 그리스트의 첫 번째 idx값p, 마지막 idx값 r을 받는다.

 ## Merge Sort 함수 코드
 ----

![merge-sort-code](/assets/merge-sort-code.jpg)

재귀함수의 기본단계는 p(첫 번째 idx값)가 r(마지막 idx값)과 같아지면( 즉, 쪼개고 쪼개서 배열이 하나밖에 안남으면) merge sort는 종료하고, 이전 호출스택으로 가서 merge를 하게 된다. (merge 함수에서 정렬이 되는 것.)

![merge-sort](/assets/merge-sort.png)

## Merge함수 코드
---

그렇다면, **Merge 함수**는 어떻게 구현되어 있길래, 정렬이 되는 것일까?

![merge-code](/assets/merge-code.jpg)

위 코드는 조금 복잡한데, 찬찬히 살펴보자.
**n1**=분할된 왼쪽 list의 길이
**n2**=분할된 오른쪽 list의 길이
**3~7라인** = 새로운 리스트 L과 R을 선언해준 뒤, 정렬되지 않는 list에서 해당 index를 받아와 L과 R을 채워준다.
**8~11라인** = 배열의 맨 끝 값들을 무한대로 한다. 여기서 첫 idx값을 1로 했다.
**12~17라인** = p~r( A 원본 리스트의 인덱스 값들)까지 L리스트와 R리스트를 비교하고, 더 작은 값을 원본 list의 왼쪽에, 더 큰 값을 원본 리스트의 오른쪽에 할당한다.

![merge-ex](/assets/merge-ex_z841hqumq.jpg)

- 위 예시에서 12~17라인을 더 분석해보자. idx 0부터 7까지  왼쪽과 오른쪽을 비교할꺼다. 왼쪽리스트의 3과 오른쪽리스트의 2를 비교했을 때, 왼쪽리스트의 3이 더 크다 -> else로 가서 원본리스트 A[1]은 오른쪽 리스트의 2로 할당되고, j는 증가한다. (j는 오른쪽리스트 idx값)
이제 j=2고, L[i=1] vs R[j=2]를 해보자. 3 vs 6은 3이 작다. ->if로 가서 A[2]=3이 되고 -> i는 증가한다.

- 만약 왼쪽리스트와 오른쪽리스트길이 n1,n2를 넘는 인덱스를 돈다면? (한쪽에 작은 값들이 몰려있어서 분할 리스트끼리 비교가 끝나면)
이미 무한대값을 넣어줬기 때문에 무한대보다 작은 값을 원본리스트에 넣고 끝나게 된다.

## Merge Sort의 시간복잡도

Recursion tree로 표현하면 다음과 같다.
함수의 높이는 logn +1 이고, 각 단계는 2개씩 분할된 것 2, 로 cn이 된다.
따라서, cn* (lgn+1) = 세타(nlogn)이다.


![merge-time](/assets/merge-time.jpg)

---
layout: post
title:  "[BFS]-타겟넘버"
subtitle:   "완전탐색"
categories: code-review
tags: programmers
comments: true
---
## Level 2
풀지 못한 문제다 ㅠㅠ
## 문제
https://programmers.co.kr/learn/courses/30/lessons/43165

## 풀이방법
1. 최상위노드가 0이고 numbers 요소에 +/-를 붙인 이진트리를 생각한다.
2.한 단계씩 내려올 수록 parent노드와 child 노드의 합을 트리에 저장한다.
 (나는 여기서 삽질했다. 이진트리를 먼저 구현하고, 이진트리순회를 돌려고 했다.)

 ## 코드
```python
    def solution(numbers, target):
      answer =[0]
      for i in numbers:
      tmp=[]
        for j in answer:
          tmp.append(j+i)
          tmp.append(j-i)
        answer = tmp
      return answer.count(target)
```


## 코드 풀이
>1. 합을 저장할 리스트 answer=[]를 만든다.
>2. numbers=[1,2,3]이라 하자. 첫 번째 요소인 1을 돌 때, answer는 0밖에 없으니 tmp에는 1, -1이 추가된다. answer는 [1,-1]이 된다.
>3. 두 번째 요소 2를 돌 때는 tmp=[]에 j=answer:1,-1/i=numbers:2,-2 의 순열로 4가지 값이 나온다. tmp에[3,-1,1,-3]이 추가된다.
>4. 루트노드 0으로부터 +/-연산의 결과값이 포화 이진트리 형태로 자라나게 된다.
>5. 리스트의 내장함수 count를 이용하여 target의 개수를 찾아 반환한다.

시간이 지나고... 다시한번 직접 구현해볼 수 있기를 ㅠㅠ

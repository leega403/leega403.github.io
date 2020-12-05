---
layout: post
title:  "[BFS]-네트워크"
subtitle:   "BFS"
categories: code-review
tags: programmers
comments: true
---
## Level 3
풀이법 봤다. 복기필요하다. 네트워크 탐색을 위한 큐, 탐색기록을 위한 배열 2가지 자료구조를 이용했다.
https://cocojelly.github.io/algorithm/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%97%B0%EC%8A%B5-DFS-BFS-(2)/

## 문제
https://programmers.co.kr/learn/courses/30/lessons/43162

## 풀이방법
 ![network](https://leega403.github.io/assets/img/code/network.jpg)

## 코드
아마 2~3일 뒤 직접 복기해서 짜야 기억에 남을 것 같다.

```python
def solution(n, computers):
  answer=0
  bfs =[ ]
  visited=[0]*n
  while 0 in visited
    x=visited.index(0)#아직 방문하지않은 노드(idx)
    bfs.append(x)
    visited[x]=1
    while bfs:
      node=bfs.pop(0)#큐에서 꺼내기
      visited[node]=1
      for i in range(n):
        if visited[i]==0 and computers[node][i]==1:
          bfs.append(i)
          visited[i]=1
    answer+=1
  return

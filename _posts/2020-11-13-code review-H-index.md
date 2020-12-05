---
layout: post
title:  "[정렬]-H-index"
subtitle:   "정렬"
categories: code-review
tags: programmers
comments: true
---
## Level 2
코테 연습하려고 일부러 다른 IDE 안쓰고 프로그래머스안에서 디버깅했다.

## 문제
https://programmers.co.kr/learn/courses/30/lessons/42747

## 풀이방법
1. 제어문 기준값을 h로 뒀다. 헷갈렸던게, h를 리스트내 값으로 뒀더니 히든 테스트케이스를 통과못했다. 그래서 h를 0부터 시작하게 했더니 통과.
2. 마지막 테스트케이스인 [0,0,0]을 계속 통과 못해서 고민했는데, while문 조건에서 아예 통과를 못한다는 것을 발견하고 등호를 넣어줬더니 통과.

## 코드
```python
def solution(citations):
    h_list=[]
    h=0
    while h<=citations[len(citations)-1]:
        count=0
        for item in citations:
            if item>=h:
                count+=1
        if (count>=h)&(len(citations)-count<=h):
            h_list.append(h)
        h+=1
    answer=max(h_list)
    print(answer)
    return answer

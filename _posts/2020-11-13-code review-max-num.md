---
layout: post
title:  "[정렬]-가장 큰 수"
subtitle:   "정렬"
categories: code-review
tags: programmers
comments: true
---
## Level 2
아쉬운 점 : 직접 정렬 알고리즘 구현하지 않았다는 점.
그리고 왜인지는 모르겠는데, 테스트케이스는 통과하는데 채점하면 꽝으로 나온다.. 뭐지?

## 문제
https://programmers.co.kr/learn/courses/30/lessons/42746

## 풀이방법
1. permutations함수를 재귀로 구현
2. main함수에서 먼저 string list로 변환후 perm함수에 넣고 가장 큰 수를 찾기 위해 sort()후 max값을 찾아준다.
## 코드
```python
def perm(str_lst,n):
  ret=[]
  if n==1:
      for i in str_lst:
          ret.append(i)
  elif n>1:
      for item in str_lst:
          temp=[i for i in str_lst]
          temp.remove(item)
          for k in perm(temp,n-1):
              ret.append(item+k)
  return ret

def solution(numbers):
  str_lst=[]
  for i in numbers:
      str_lst.append(str(i))
  n=len(str_lst)
  ret_str=perm(str_lst,n)
  ret_int=[]
  for item in ret_str:
      ret_int.append(int(item))
  ret_int.sort(reverse=True)
  answer = str(ret_int[0])

  return answer
  ```

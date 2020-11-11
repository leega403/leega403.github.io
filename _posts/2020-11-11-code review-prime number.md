---
layout: post
title:  "[완전탐색]-소수찾기와 순열 조합"
subtitle:   "완전탐색"
categories: code-review
tags: programmers
comments: true
---

## Level 2

## 문제
https://programmers.co.kr/learn/courses/30/lessons/42839



## 풀이방법
1. 완전탐색을 위한 Permutation 함수 구현
2. 소수판단 함수 구현
3. Solution 함수에서 순열 리스트 생성 -> set으로 중복제거 -> 소수판단

## 시간복잡도 줄이기
테스트 케이스 에러때문에 질문게시판을 참고했다.
https://programmers.co.kr/questions/11572

소수 판단시 2부터 i까지 나눴을 때 나머지가 0이 아니면 소수라고 판단 기준을 마련했다. 

근데 이러면 시간이 너무 느려진다고 한다.

**주어진 숫자의 제곱근 이하(math.sqrt(i))로만 나눠도 소수인지 판단이 가능하다고 한다**

예를 들어

	24 = 2 * 12
	24 = 3 * 8
	24 = 4 * 6
    대칭구조
	24 = 6 * 4
	24 = 8 * 3
	24 = 12 * 2

24의 대략적 제곱근 4를 기준으로 대칭인 것을 알 수 있다. 4이하로만 나눠지는지 판단해도 충분히 소수인지 아닌지를 알 수 있는 것이다. 

그래서 import math 라이브러리를 불러오고, math.sqrt(i)로 제곱근을 구해서 나눠주면 히든 테스트케이스를 통과할 수 있다. 

## 완전탐색 순열 조합
이 사이트에 친절하게 구현되어 있다. 완전탐색을 풀려고 한다면, 순열과 조합 구현은 외워두는 것도 좋겠다.

 https://medium.com/@dltkddud4403/python-%EC%88%9C%EC%97%B4-%EC%A1%B0%ED%95%A9-%EA%B5%AC%ED%98%84-5e496e74621c

# 1. 파이썬 itertool라이브러리
	p=[]
	items=['A','B','C','D']
	from itertools import permutations
	print(permutations(items,2)
	print(list(permutations(items,2))

프린트값은 다음과 같다.

	><itertools.permutations object at 0x7ff8044acbf8>
	>[('A', 'B'), ('A', 'C'), ('A', 'D'), ('B', 'A'), ('B', 'C'), ('B', 'D'), ('C', 'A'), ('C', 'B'), ('C', 'D'), ('D', 'A'), ('D', 'B'), ('D', 'C')]

파이썬 permutation은 ~~주소에 있는 객체라고만 알려주기 때문에 list를 이용해 캐스팅(형변환)을 해주어야 한다. 

# 2. 재귀함수로 순열조합 구현하기 
재귀함수는 기본단계, 재귀단계 두가지만 잘 나눠놓고 호출스택 단계에 따른 결과값이 어떻게 되는지만 잘 따라가서 구현하면 된다. 

기본단계는 **배열이 비어 있거나, 원소가 1개남도록** 하면 된다. 

[A,B,C,D] 4개의 문자에서 순서가 있는 문자 2개를 뽑는 경우는 1. 먼저 문자 하나를 뽑고, 2. 나머지 문자들의 순열을 구해서 3. 합친다. 

permutation([A,B,C,D],2) = 
([A] + permutation([B,C,D],1)) and
([B] + permutation([A,C,D],1)) and ([C] + permutation([A,B,D],1)) and
([D] + permutation([A,B,C],1))

(조합의 경우는 순서가 상관이 없으니, 앞에서 뽑았던 문자는 후에 안 뽑으면 된다.)

	def perm(lst,n):
		ret = []
	
		if n==1: #<-기본단계. 원소가 1개인 순열이 된다면, 끝남.
			for item in lst:
				ret.append(item)

		elif n>1: #<-재귀단계
			for i in range(len(lst)):
				temp = [i for i in lst] 
				temp.remove(lst[i])# 문자 한개를 제외한 나머지 문자리스트

				for p in perm(temp,n-1):
					ret.append(lst[i]+p)# 나머지 문자리스트의 순열과 앞에 문자한개를 합친다. 
	
		return ret




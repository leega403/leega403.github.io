---
layout: post
title:  "[Algorithm]-2.분할정복을 위한 재귀함수 이해"
subtitle:   "recursion"
categories: programming
tags: algorithms
comments: true
---
## 개요
> 이 글은 분할정복을 이해하기 위한 재귀함수의 기본단계, 호출스택에 대해 정리한 글입니다.

- [기본단계와 재귀단계](#기본단계와-재귀단계)
- [Call stack](#call-stack)
- Example : [팩토리얼 함수](#팩토리얼-함수)

---
## 기본단계와 재귀단계

재귀함수는 자기자신을 호출하기 때문에 실수로 무한반복을 하는 함수를 만들기 쉽습니다. 예를 들어, 다음과 같이 카운트 다운을 하는 함수를 만들었습니다.

	def countdown(i):
		print(i)
		coutdown(i-1)

이 코드를 실행시키면 곧 문제가 있는 것을 눈치 챌 수 있습니다. 그 이유는 함수가 끝없이 실행되기 때문입니다. 

	>3...2...1...0...-1...-2

따라서, 재귀함수를 만들 때는 언제 재귀를 멈출지 알려줘야 합니다. 그래서 모든 재귀함수는 기본단계(Base Case)와 재귀단계(Recursive Case)라는 두 부분으로 나누어져 있습니다. 
**기본단계는 재귀함수가 자기 자신을 다시 호출하지 않게, 즉 무한반복으로 빠지지 않게 하는 부분입니다.**

이제 함수에 기본단계를 추가하면?

	def countdown(i):
		print(i):
		if (i<=1): # <-이부분이 기본단계
			return
		else:
			coutdown(i-1) # <-이부분은 재귀단계

## Call stack



## 팩토리얼 함수






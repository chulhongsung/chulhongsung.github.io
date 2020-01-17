
---
title: "Britten-Jones(1999) 정리"
excerpt: "포트폴리오 정규화 방법"
toc: true
toc_sticky: true
use_math: true

author_profile: true

date: 2020-01-15 15:00:00 -0000

categories: 
  - 논문 읽기
tags:
  - 포트폴리오 최적화
---

### <span style="color:#F7DC6F;">The Sampling Error in Estimates of Mean-Variance Efficient Portfolio Weights</span>

이 논문은 ["Optimal Portfolio Selection using Regularization"](https://chulhongsung.github.io/논문%20읽기/포트폴리오정규화(1)/) 논문을 이해하는데 좋은 참고자료가 되기에 내용을 정리한다. 1장에서 포트폴리오와 회귀분석과의 관계를 이해시켜준다. 따라서 그 부분만을 정리한다. Notation은 기존의 "Optimal Portfolio Selection using Regularization"의 논문과 동일하다.

###  <span style="color:#00ADB5;"> The Regression Approach to Portfolio Analysis</span>

$N$개의 자산에 대한 $t$시점의 excess return vector, $r_{t}$는 다음과 같이 정의한다.

$$
r^{\top}_t = (r_{1,t}, \dots, r_{N,t} ).
$$

그리고 $T \times N$ 행렬 $R$은 다음과 같다.

$$
R^{\top} = (r_1, \dots, r_{T}).
$$ 

Theorem 1. OLS regression of a constant $1_T$ onto a set of asset's excess returns $R$, without an intercept term,

$$
1_T = R\beta + u,
$$

의 결과
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg5MDc5NjU4MywyMDQwNTExNDgxXX0=
-->

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
1_T = R\beta + u, \tag {1}
$$

에서 회귀계수 추정치 $\hat{\beta}$는 

$$
\hat{\beta} = (R^{\top}R)^{-1}R^{\top}1_T.
$$

(1) 회귀식은 일반적이지 않다. 계수도 없고 종속변수가 랜덤하지 않다. 그리고 $u$ 또한 $R$과 독립이 아니다.

하지만 해석은 매우 쉽다. $R\beta$, 포트폴리오 수익률이 1에 least-squares 거리 기준으로 가깝게 한다. 

<span style="color:#DAF7A6;">1?<span>
>논문에서 단순하게 "arbitrage profit"에 대응되는 개념이라고 하는데 양수 수익률과 분산이 0인 수익률로 매우 "desirable" 수익률이라고 소개한다. 1이라는 특정한 값이 중요한 것은 아닌거 같다. 결과를 구해보니 1이었던 것이 아닐까? 라는 생각을 해본다.


 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU5MTA5NzI1LDQ1NDkwNjcxOSwyMDQwNT
ExNDgxXX0=
-->
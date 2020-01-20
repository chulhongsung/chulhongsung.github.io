---
title: "Britten-Jones(1999) 정리(작성중)"
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
-------------
이 논문은 ["Optimal Portfolio Selection using Regularization"](https://chulhongsung.github.io/논문%20읽기/포트폴리오정규화(1)/) 논문을 이해하는데 좋은 참고자료가 되기에 내용을 정리한다. 1장에서 포트폴리오와 회귀분석과의 관계를 이해시켜준다. 따라서 그 부분만을 정리한다. Notation은 기존의 "Optimal Portfolio Selection using Regularization"의 논문과 동일하다.

###  <span style="color:#00ADB5;"> The Regression Approach to Portfolio Analysis</span>
---------------
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

<span style="color:#DAF7A6;">꼭 1이어야만 하나?<span>
>논문에서 단순하게 "arbitrage profit"에 대응되는 개념이라고 하는데 양수 수익률과 분산이 0인 수익률로 매우 "desirable" 수익률이라고 소개한다. 1이라는 특정한 값이 중요한 것은 아닌것 같다. 


![mean-sd diagram](https://user-images.githubusercontent.com/37679460/72590792-ef612500-3941-11ea-9768-562e8a73661e.PNG)
 
위의 그림에서  x축은 포트폴리오 수익률의 표준편차, y축은 포트폴리오 수익률의 평균이다. $(0,1)$이 있는 곳이 $1_T$를 의미한다고 생각하면 된다(평균수익률은 1이고 표준편차가 0). 그리고 포트폴리오는 C자형 곡선 위를 움직인다. 즉, feasible set이고 feasible set은 원점 $O$와 $d$를 잇는 직선을 상한으로 가진다. 

잔차 $u$를 평균 $\bar{u}1$와 에러항 $e$로 나눌 수 있다.

$$
u = \bar{u}1 + e,
$$

여기서 $\bar{u} = (1/T)u^{\top}1$.

위의 식을 이용해 Mean squared residual(MSR)은 다음과 같이 나눌 수 있다.

$$
\begin{aligned}
MSR &= Mean^{2} + SD^{2} \\
u^{\top}u/T &= \bar{u}^2 + e^{\top}e/T.
\end{aligned}
$$

잔차의 평균, $\bar{u}$는 $\bar{r}^{\top}\hat{\beta} = 1-\bar{u}$를 만족한다. 위의 그림에서 y축에서 '$1-u$' 값을 확인할 수 있다. 그리고 포트폴리오의 표준편차는 $\sqrt{e^{\top}e/T} = SD$로 생각할 수 있다. 

![enter image description here](https://user-images.githubusercontent.com/37679460/72707027-d60ae380-3ba2-11ea-97b7-ca2c1d0e2d54.jpg)

위의 그림에서 $MSR$은 피타고라스 정리에 의해 상한인 $\overline{Od}$와 $(0,1)$ 사이의 거리로 표현된다. 

결국 OLS 방법은 $MSR$을 가장 작게하는 $\hat{\beta}$를 찾고 $mean-standard ~ deviation$ 공간(위의 그림에서 C자형 곡선) 위의 점 중에서 $\overline{Od}$과 $(0,1)$의 직교하는 점과 만나는 점을 만족하게 하는 $\beta$가 $\hat{\beta}$이 된다.

사실 위의 논문을 읽으면서 왜
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIyNjgwMTkxMSwtNDk5ODUzNjA3LDEzNz
QwNjQxMTksLTEyODQ0NjUxNSwtODQ3Nzk2NzEzLDY5NzgzNDMx
MCwxMzg5NjAzNjkwLDUxMTU0MTY0MSwxNTkxMDk3MjUsNDU0OT
A2NzE5LDIwNDA1MTE0ODFdfQ==
-->
---
title: "Variational Inference"
excerpt: Variational Inference Basic

toc: true
toc_sticky: true
use_math: true

author_profile: true

date: 2020-07-04 19:00:00 -0000

categories: 
  - 딥러닝
  - 베이지안
  
tags:
  - bayesian neural network
----
-------------------------
몇 년 전, Variational Autoencoder(VAE)를 공부하기 위해 Google scholar에서 Variational autoencoder를 친 기억이 있다. 하지만 내가 원하는 Kingma의 논문은 나오지 않았다. 사실 논문의 제목은 "Auto-Encoding Variational Bayes"인 걸 알게 되었고 variational bayes 단어는 당시에 너무 무서웠다(지금도지만). Variational는 거의 생소한 단어였고 bayes는 통계학과에서도 어려운 과목이라고 생각했기 때문이다. 몇 년이 지나고 다시 공부하면서 생각이 어느 정도 잡히고 이해가 되는 것 같아서 VAE의 근본이 되는 variational inference에 대해서 정리를 하고자 한다. 이 포스팅은 [수학의 즐거움](https://www.youtube.com/watch?v=OiG80VcUqbE&t=465s) 채널에서 최성준님의 발표와 Ian Goodfellow의 'Deep Learning' 책의 내용을 바탕으로 작성되었음을 미리 공지합니다.
## <span style="color:#00ADB5;"> Variational Inference</span>
 

### <span style="color:#F7DC6F;">Variational Inference(VI)</span>


<!--stackedit_data:
eyJoaXN0b3J5IjpbNjQwNDQ2NDIzLDkyMjY5NTE3NCwxMDczNj
Q5MzQsLTc3NTEyMjU1LC03NTA5MjkzOF19
-->
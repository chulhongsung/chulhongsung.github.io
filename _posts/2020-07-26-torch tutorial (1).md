---
title:  "Pytorch 튜토리얼 (1)"
excerpt: Pytorch tutorial (1)

toc: true
toc_sticky: true
use_math: true

author_profile: true

date: 2020-07-26 21:00:00 -0000

categories: 
  - 딥러닝
  - 머신러닝
  - python
  
tags:
  -  pytorch
---

신경망 모형을 만들때 Tensorflow를 자주 사용했다. Tensorflow도 2.0버전이후로는 매우 편리해진 느낌이다.  하지만 아직도 많은 논문들의 구현 코드는 Pytorch로 되어있는 경우가 많고 편리성도 훨씬 뛰어난 느낌이다. 둘 다 사용할 줄 알면 더 좋으니 Pytorch도 공부하고자 포스팅을 한다. 공부자료는 유투브 공개강좌인 [모두를 위한 딥러닝 시즌2 - PyTorch](https://www.youtube.com/playlist?list=PLQ28Nx3M4JrhkqBVIXg-i5_CVVoS1UzAv)에서 사용한 소스코드를 사용한다. 그리고 Tensorflow와의 비교도 하면서 차이점을 알아본다.

먼저 사용자가 custom model의 class를 만드는 것부터 알아보자.
## <span style="color:#00ADB5;"> nn.Module</span>

```python
import torch.nn as nn

class model(nn.Module):
    def __init__(self):
        super().__init__()
        self.linear = nn.linear(3, 1)

    def forward(self, x):

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI3NDkzMjMxOV19
-->
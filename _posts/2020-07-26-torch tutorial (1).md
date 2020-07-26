---
title:  "PyTorch 튜토리얼 (1)"
excerpt: PyTorch tutorial (1)

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

신경망 모형을 만들때 Tensorflow를 자주 사용했다. Tensorflow도 2.0버전이후로는 매우 편리해진 느낌이다.  하지만 아직도 많은 논문들의 구현 코드는 PyTorch로 되어있는 경우가 많고 편리성도 훨씬 뛰어난 느낌이다. 둘 다 사용할 줄 알면 더 좋으니 PyTorch도 공부하고자 포스팅을 한다. 공부자료는 유투브 공개강좌인 [모두를 위한 딥러닝 시즌2 - PyTorch](https://www.youtube.com/playlist?list=PLQ28Nx3M4JrhkqBVIXg-i5_CVVoS1UzAv)에서 사용한 소스코드를 사용한다. 그리고 Tensorflow와의 비교도 하면서 차이점을 알아본다.

## <span style="color:#00ADB5;"> $\textsf{nn.Module}$</span>

먼저 사용자가 custom model의 class를 만드는 것부터 알아보자. 간단한 linear regression model을 생각하자.

```python
import torch.nn as nn

class CustomModel(nn.Module):
    def __init__(self):
        super(CustomModel, self).__init__()
        self.linear = nn.linear(3, 1)

    def forward(self, x):
        return self.linear(x)
```

위의 pytorch 코드와 똑같은 tensorflow 코드를 만들어보자.

```python
from  tensorflow  import  keras

class CustomModel(tf.keras.models.Model):
    def __init__(self): 
        super(CustomModel, self).__init__()
        self.linear = keras.layers.Dense(1)
    
    def call(self, x):
        return self.linear(x)
```

위의 프레임워크들의 magic method들의 이름을 보면 둘 다 굉장히 잘 지었다고 생각이 든다. pytorch에서는 신경망에서 순방향으로의 진행을 나타내기위해 'forward'라고 했고 tensorflow 역시 계산을 위해 불러진다면(called) 순방향으로 계산하기 때문에 'call'이라고 한 것 같다. 결론은 똑같다.

## <span style="color:#00ADB5;"> $\textsf{Dataset}$ & $\textsf{DataLoader}$</span>

pytorch에서 데이터를 다루는 것도 상당히 편리하다.
```python
from torch.utils.data import Dataset

class CustomDataset(Dataset):
    def __init__(self):
        super(CustomDataset, self).__init__()
        self.x = [[70, 80, 75],[50, 60, 70]]
        self.y = [[80, 65]]

    def __len__(self):
        return len(self.x)
    
    def __getitem__(self, idx):
        x = torch.FloatTensor(self.x[idx])
        y = torch.FloatTensor(self.y[idx])
        
        return x, y

dataset = CustomDataset()
```
위의 class에서 magic method $\textsf{\_\_len\_\_}, \textsf{\_\_getitem\_\_}$의 역할도 직관적이다. 이제 $\textsf{DataLoader}$를 통해 batch size 정하거나 shuffle을 수행할 수 있다.

```python
from torch.utils.data import DataLoader

dataloader = DataLoader(
    dataset,
    batch_size=2,
    shuffle=True
)
```

위에서 생성한 _dataloader_ 객체와 $\textsf{enumerate}$ 함수를 통해 학습시에 편리하게 학습을 진행할 수 있다.

```python
for epoch in range(max_epoch+1):
    for batch_idx, samples in enumerate(dataloader):
    x_train, y_train = samples
```
위와 같이 $\textsf{enumerate}$ 함수를 통해서 batch의 index와 데이터 sample을 받을 수 있다.

참고로 Tensorflow2.0에도 [$\textsf{tf.data}$](https://www.tensorflow.org/guide/data)가 있는데 pytorch만큼 쉽지는 않은 것 같다. 공식 문서 링크를 걸어놨으니 참고하면 도움이 될 듯하다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkwNDQwMjE5Myw1OTU4MjQ1Nyw3NzQ2MD
Q1NjQsMTA4MTQ5MDUyNywxOTA0NDQ1NDQ3LDEwOTU3NDcwNTcs
LTI3NDkzMjMxOV19
-->
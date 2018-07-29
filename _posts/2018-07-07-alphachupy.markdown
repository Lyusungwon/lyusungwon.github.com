---
layout: post
title:  "[Pytorch] Alphachu (Ape-X DQN)"
date:   2018-07-07 16:45:59
author: Sungwon Lyu
categories: Pytorch-Implementation
---

피카츄 배구에 대한 [Ape-X DQN](https://lyusungwon.github.io/rl/2018/07/07/apex.html)을 Pytorch로 구현

[https://github.com/Lyusungwon/pytorch](https://github.com/Lyusungwon/pytorch)

## Reference
- https://github.com/rlcode/reinforcement-learning-kr
- https://github.com/hunkim

## Note 
- 사실 이 구현은 Distributed prioritized experience replay를 읽기 전에 혼자서 구현한 것 (구현하고 보니 똑같았다... 신기)
- 1대의 GPU만으로도 효율적인 학습이 가능
- 모델 크기가 중요할 것으로 보임
- 이제 CPU가 문제

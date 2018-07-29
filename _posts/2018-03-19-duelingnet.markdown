---
layout: post
title:  "Dueling Network Architectures for Deep Reinforcement Learning"
date:   2018-03-19 09:56:59
author: Sungwon Lyu
categories: Reinforcement Learning
---
## WHY? 
기존의 DQN은 특정 지점에서의 action-value function을 근사하기 위하여 모든 state와 action의 값을 모두 평가해야 한다는 단점이 있다. 하지만 대부분의 경우, state의 가치가 중요하고 action으로 인한 가치의 변화가 극명한 경우는 많지 않다. 또한 어차피 행동을 고르기 위해서 action-value function을 근사하기 때문에 모든 state와 action에 대하여 정확한 값을 아는 것이 중요한 것이 아니라 다른 action과 비교한 상대값이 중요하다. 

## WHAT?
Dueling Network는 한번에 state와 action을 평가하는 네트워크를 만드는 것이 아니라 state와 action을 만드는 네트워크를 분리한다. CNN을 통하여 이미지를 받아와 feature를 처리한 후, 각각 다른 feedforward network를 거쳐 하나는 state를 평가하고 나머지는 action을 평가한다. 즉, $$\alpha, \beta$$를 각 feedforward network의 parameter라고 할때, \\
$$Q(s,a;\theta, \alpha,\beta)=V(s;\theta,\beta) + A(s,a;\theta,\alpha)$$\\
로 구성되는 것이다. 이때, action의 평가는 상대적으로 이루어져도 괜찮으므로 모든 action에 대하여 그 action의 maximum, 혹은 mean값을 빼주게 된다. 즉,\\
$$Q(s,a;\theta, \alpha,\beta)=V(s;\theta,\beta) + (A(s,a;\theta,\alpha) - max_{a'\in \mathcal{A}} A(s,a';\theta,\alpha)$$ 혹은 \\
$$Q(s,a;\theta, \alpha,\beta)=V(s;\theta,\beta) + (A(s,a;\theta,\alpha) - \frac{1}{\|\mathcal{A}\|} \Sigma_{a'}A(s,a';\theta,\alpha)$$의 형태로 학습하게 된다. 

## So?
이를 통하여 기존보다 효율적으로 학습하고 좋은 결과를 낼 수 있게 되었다. 
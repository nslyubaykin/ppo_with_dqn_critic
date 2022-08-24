# Two Actors at the Price of One
__or Training PPO with DQN as a critic with [ReLAx](https://github.com/nslyubaykin/relax)__

# Overall Idea

PPO needs and estimation of advantages to run the training process. Typically advantages for PPO are estimated with GAE-$\lambda$ algorithm. 

This notebook explores the possibility of training PPO in pair with DDQN critic.

While PPO is trained in on-policy mode using transitions sampled with its policy network, DQN is trained on off-policy data stored in replay buffer (which is filled with train batches sampled with PPO actor)

Theoretically, such procedure should allow us to train 2 agents (`PPO`+`DQN` and `ArgmaxQValue`+`DQN`) on the same samples.

Plot below shows smoothed training runs (evaluated on a separate environments) for `PPO`+`DQN` and `ArgmaxQValue`+`DQN`:

![ppo_dqn_training](https://github.com/nslyubaykin/ppo_with_dqn_critic/blob/master/ppo_dqn_training.png)

As we can see, `PPO`+`DQN` outperforms `ArgmaxQValue`+`DQN` over the entire course of training:

__Trained policies__

__PPO__

https://user-images.githubusercontent.com/67604207/186506192-c5c3e906-6b0a-4f09-9574-72a2a2047a7c.mp4

__DQN__

https://user-images.githubusercontent.com/67604207/186506232-78bb3b54-77ab-497f-9d10-40ccb40c6d7b.mp4

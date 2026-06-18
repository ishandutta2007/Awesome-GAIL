# Awesome-GAIL
## Generative Adversarial Imitation Learning (GAIL) Variants

Generative Adversarial Imitation Learning (GAIL) bypasses traditional Inverse Reinforcement Learning (IRL) by directly extracting a policy from expert demonstrations. It uses a GAN-like framework where a Generator (the agent's policy) tries to mimic the expert, and a Discriminator tries to distinguish between expert actions and agent actions.

## 1. Standard GAIL (Base GAIL)
* **Definition:** The foundational framework introduced by Ho and Ermon (2016).
* **Mechanism:** Employs a model-free adversarial setup using a surrogate reward function derived from the discriminator's output.
* **Optimization:** Typically uses Trust Region Policy Optimization (TRPO) or Proximal Policy Optimization (PPO) to update the agent's policy.
* **Core Benefit:** Allows agents to learn complex, continuous control tasks directly from raw expert trajectories without manually designing reward functions.

## 2. Sample-Efficiency & Stability Variants
Standard GAIL suffers from high sample complexity and training instability. These variants optimize data usage and reward signals:

| Variant | Year | Paper Link | Description |
| :--- | :---: | :--- | :--- |
| [**SAM-GAIL**](docs/sam-gail.md) | 2019 | [arXiv:1809.02064](https://arxiv.org/abs/1809.02064) | Integrates off-policy RL (like SAC or TD3) to reuse past transition data, reducing environment interactions. |
| [**InfoGAIL**](docs/infogail.md) | 2017 | [arXiv:1703.08840](https://arxiv.org/abs/1703.08840) | Uses Information Maximization to learn interpretable, latent sub-skills from heterogeneous demonstrations. |
| [**DAC**](docs/dac.md) | 2018 | [arXiv:1809.02925](https://arxiv.org/abs/1809.02925) | Addresses "surrogate reward bias" by treating the discriminator as a dynamic reward function in an actor-critic framework. |

## 3. Partially Observable & Multi-Agent Adaptations
| Variant | Year | Paper Link | Description |
| :--- | :---: | :--- | :--- |
| [**PO-GAIL**](docs/po-gail.md) | 2020 | [arXiv:2011.04642](https://arxiv.org/abs/2011.04642) | Modifies the discriminator to handle partially observable environments using historical observation sequences. |
| [**MAGAIL**](docs/magail.md) | 2018 | [arXiv:1807.09936](https://arxiv.org/abs/1807.09936) | Extends GAIL to multi-agent environments, training decentralized policies from coordinate demonstrations. |
| [**Third-Person GAIL**](docs/third-person-gail.md) | 2017 | [arXiv:1703.01703](https://arxiv.org/abs/1703.01703) | Corrects for domain shifts, allowing learning from expert demonstrations recorded from different perspectives. |

## 4. Safety & Robustness Variants
| Variant | Year | Paper Link | Description |
| :--- | :---: | :--- | :--- |
| [**Safe-GAIL**](docs/safe-gail.md) | 2020 | [Link](https://www.researchgate.net/publication/341545454_Safe_Generative_Adversarial_Imitation_Learning) | Constrains policy generation using Cost Functions or Control Barrier Functions to ensure safety during exploration. |
| [**Robust GAIL**](docs/robust-gail.md) | 2019 | [arXiv:1905.04418](https://arxiv.org/abs/1905.04418) | Models bounded noise or expert sub-optimality to prevent mimicking bad habits and ensure robustness. |

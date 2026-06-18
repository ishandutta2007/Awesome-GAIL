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
* **SAM-GAIL (Sample-Efficient GAIL):** Integrates off-policy Reinforcement Learning (like SAC or TD3) to reuse past transition data, drastically reducing the number of environment interactions needed.
* **InfoGAIL:** Incorporates Information Maximization to learn interpretable, latent sub-skills from unlabelled, heterogeneous expert demonstrations.
* **DAC (Discriminator-Actor-Critic):** Addresses the "surrogate reward bias" by treating the discriminator as a dynamic reward function inside an actor-critic framework, fixing off-policy training bugs.

## 3. Partially Observable & Multi-Agent Adaptations
* **PO-GAIL (Partially Observable GAIL):** Modifies the discriminator to handle environments where the agent cannot see the full state vector, relying only on historical observation sequences.
* **MAGAIL (Multi-Agent GAIL):** Extends the adversarial framework to cooperative or competitive multi-agent environments, training decentralized policies from multi-agent coordinate demonstrations.
* **Third-Person GAIL:** Corrects for domain shifts, allowing an agent to learn a policy even if the expert demonstrations are recorded from a different camera angle or perspective.

## 4. Safety & Robustness Variants
* **Safe-GAIL:** Constraints the policy generation step using Cost Functions or Control Barrier Functions to ensure the agent does not violate safety parameters during the adversarial exploration phase.
* **Robust GAIL:** Models bounded noise or expert sub-optimality, preventing the student policy from mimicking bad habits or failing when faced with environmental perturbations.

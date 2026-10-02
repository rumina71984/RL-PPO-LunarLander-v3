# 🚀 PPO Agent Training for LunarLander-v3  

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rumina71984/RL-PPO-LunarLander-v3/blob/Main/src/ppo_lunarlander_training.ipynb)  
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)  

This repository contains the **training pipeline** and **notebooks** for training a Proximal Policy Optimization (PPO) agent on the **LunarLander-v3** environment using [Stable-Baselines3](https://github.com/DLR-RM/stable-baselines3).  

After training, the notebook saves the model locally as `ppo_lunarlander_v3_25hk_v01.zip`.  


## 📊 Performance  

- **Environment:** `LunarLander-v3`  
- **Algorithm:** PPO  
- **Mean Reward:** `289.24 ± 12.88` (over 10 evaluation episodes)  
- **Training Steps:** 2.5M  


## 📂 Repository Structure  

RL-PPO-LunarLander-v3/

```bash
│── src
│   │── ppo_lunarlander_training.ipynb # Main training notebook
│── LICENSE # License file
│── README.md # This file
```

## 🧑‍💻 Training

You can run the training pipeline locally or in Colab.  

### Run in Colab  
Click below to open the training notebook:  
👉 [Open Notebook in Colab](https://colab.research.google.com/github/rumina71984/RL-PPO-LunarLander-v3/blob/Main/src/ppo_lunarlander_training.ipynb)  

### Run Locally  

```bash
# Clone the repository
git clone https://github.com/rumina71984/RL-PPO-LunarLander-v3.git
cd RL-PPO-LunarLander-v3

# Open the notebook
jupyter notebook src/ppo_lunarlander_training.ipynb
```

## Using the Trained Model

Training writes `ppo_lunarlander_v3_25hk_v01.zip` in the working directory. Load that file and run it:

```python
import gymnasium as gym
from stable_baselines3 import PPO

# Load the model saved by the training notebook
model = PPO.load("ppo_lunarlander_v3_25hk_v01")

# Create environment
env = gym.make("LunarLander-v3", render_mode="human")

obs, info = env.reset()
done, truncated = False, False

while not (done or truncated):
    action, _ = model.predict(obs)
    obs, reward, done, truncated, info = env.step(action)
    env.render()

env.close()
```

## 📚 References

- [Stable-Baselines3](https://stable-baselines3.readthedocs.io/en/master/)

- [Gymnasium LunarLander-v3 Environment](https://gymnasium.farama.org/environments/box2d/lunar_lander/)

- [Original PPO Paper](https://arxiv.org/abs/1707.06347)


## 📝 License

This repository is licensed under the MIT License.
See the LICENSE file for more details.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)  

---

### 🙌 If you find this repo useful, please ⭐ it!

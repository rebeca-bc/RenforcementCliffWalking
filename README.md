# 🚀 Reinforcement Learning: Q-Learning on Cliff Walking

**Watch an AI learn to walk across a cliff in real time!** Starting from complete chaos (1,368 steps, falling off immediately), the agent masters the optimal path (14 steps, walking the cliff edge) by episode 499.

## 🎯 The Problem

```
Row 0: [ ][S][ ]...  (Safe zone)
Row 1: [ ][ ][ ]...  (Safe zone)
Row 2: [ ][ ][ ]...  (Safe zone)
Row 3: [S][C][C]...[C][G]  (Cliff walking!)

S = START (bottom-left)
C = CLIFF (red danger zone) = -100 penalty
G = GOAL (bottom-right) = +0 if safe path
```

**Challenge:** Get from START to GOAL without falling in the CLIFF!

## 📊 Results: MASSIVE IMPROVEMENT

|   Phase   | Episodes | Avg Reward | Path Length  | Status      |
| :-------: | :------: | :--------: | :----------: | :---------- |
| **Early** |   1-50   |  -11,281   | 1,000+ steps | ❌ Chaos    |
|  **Mid**  | 200-250  |    -240    |  150+ steps  | ⚠️ Learning |
| **Late**  | 450-500  |    -46     |   14 steps   | ✅ Expert   |

**Improvement: 11,235 reward points!** 🚀

### Progress by Episode:

- **Episode 1:** 1,368 steps (keeps falling off)
- **Episode 20:** 516 steps (long safe path)
- **Episode 100:** 171 steps (faster)
- **Episode 300:** 32 steps (walking cliff edge!)
- **Episode 499:** 14 steps (optimal speedrun!)

## 🧠 The Algorithm: Q-Learning

Q-Learning learns by building a **Q-Table**: for each state, it stores the value of each action.

```
Q(state, action) += α * (reward + γ * max(Q(next_state)) - Q(state, action))

α   = Learning rate (0.1 = update 10% of the way)
γ   = Discount factor (0.99 = future matters)
reward = -1 per step (costs energy) OR -100 (fell in cliff!)
```

## 📁 Project Files

- [`ReinforcementLearning.ipynb`](./reinforcementlearning.ipynb) - Full notebook with training + visualization
- [`ReinforcementLearning.ipynb`](./reinforcementlearning.html) - HTML version for easy viewing
- [`rl_training_videos`](./rl_training_videos) - 5 animated GIFs + learning curve chart
  - [`episode_001.gif`](/rl_training_videos/episode_001.gif) - Total chaos (1.7 MB)
  - [`episode_020.gif`](/rl_training_videos/episode_020.gif) - Learning starts (706 KB)
  - [`episode_100.gif`](/rl_training_videos/episode_100.gif) - Getting good (264 KB)
  - [`episode_300.gif`](/rl_training_videos/episode_300.gif) - Expert mode (59 KB)
  - [`episode_499.gif`](/rl_training_videos/episode_499.gif) - Optimal path (30 KB)
  - [`learning_analysis.png`](/rl_training_videos/learning_analysis.png) - Learning curves

## 🎓 Key Insights

✅ **Q-Learning works on simple grids**

- 48 states × 4 actions = learnable Q-Table
- Clear rewards (-1 per step, -100 for cliff)
- Agent finds optimal path naturally

✅ **Exploration matters early**

- Episode 1 with epsilon=1.0: 100% random = learns what NOT to do
- Episode 500 with epsilon=0.08: 92% exploitation = uses learned knowledge

✅ **Path length shows learning clearly**

- Episode 1: 1,368 steps (terrible!)
- Episode 499: 14 steps (perfect!)
- **99% improvement visible in GIFs!**

✅ **The cliff edge strategy emerges naturally**

- Agent doesn't need to be told "walk the edge"
- Q-Learning discovers it's optimal (-1 penalty per step is worth it)
- By episode 300+, agent actively chooses the risky path!

## 🔧 Technologies

- **Gymnasium** - RL environment (CliffWalking-v1)
- **NumPy** - Q-Table and computations
- **Matplotlib** - Learning curves
- **PIL** - GIF generation
- **Python 3.13** - Implementation

## 📝 Summary

This project demonstrates that **Q-Learning actually works**. In just 500 episodes, an agent goes from falling off a cliff immediately to finding the optimal path. The progression is visible in GIFs showing:

- Episode 1: Total chaos ❌
- Episode 499: Perfect control ✅

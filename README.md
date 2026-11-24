# Multi-Delivery Robot (tabular reinforcement learning)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Qwup2112/multi-delivery-robot-colab/blob/main/MultiDeliveryRobot_Colab.ipynb)

A robot moves on a grid, picks up and delivers several parcels, and decides the order by itself.
The code is in one notebook, [`MultiDeliveryRobot_Colab.ipynb`](MultiDeliveryRobot_Colab.ipynb), written in Vietnamese and saved with its outputs.
The report is in English: [`Report_Topic13_EN_Overleaf.pdf`](Report_Topic13_EN_Overleaf.pdf) (IEEE format, 10 pages).

## How to run

Click the badge above, then choose `Runtime → Run all`. A CPU runtime is enough.
A full run takes about 9–10 minutes on Colab; set `QUICK = True` in the first code cell for a quick run of about 3 minutes.

## Contents

| Section | Topic |
|---|---|
| 1–2 | Setup and the MDP model (state, action, reward, transition, terminal, Markov property) |
| 3–4 | Four maps and the custom `gymnasium.Env`, state encoding, state-space size |
| 5 | Game: drive the robot yourself with buttons |
| 6 | Dynamic programming: Policy Evaluation, Policy Iteration, Value Iteration |
| 7 | Monte Carlo (exploring starts), SARSA, Q-learning |
| 8–9 | Training over several seeds, learning curves, comparison tables, policy plots |
| 10 | How the policy changes with the reward and the environment parameters |
| 11 | Failure cases and slow convergence |
| 12 | Animated episodes, and playing alongside the AI |
| 13–14 | Saving the results, summary |

## Maps

| Map | Setting | Constraint |
|---|---|---|
| L1 | 2 independent parcels | can carry both at once |
| L2 | 3 parcels | carries 1 at a time, so the order matters |
| L3 | one parcel has a deadline | a clock `t` is added to the state |
| L4 | booster tile | can carry 2 parcels for one trip; `b` is added to the state |

## Main results

Full run (`QUICK = False`), 3 seeds. "Optimal" means the learned route from the start cell matches the dynamic-programming solution.

| Algorithm | Optimal from the start |
|---|---|
| Policy Iteration, Value Iteration | same optimal value on all 4 maps |
| Q-learning | all 4 maps, every seed |
| SARSA | L2 and L4; L1 in 1 of 3 seeds, L3 in 0 of 3 |
| Monte Carlo (exploring starts) | L1–L3; L4 in 0 of 3 seeds after 300,000 episodes |

# Interpretable Reinforcement Learning for Insulin Dosage

This repository contains the code and experiments for our project: **Explainable Recurrent Proximal Policy Optimization (RPPO)** for determining proper insulin dosage in Type 1 Diabetes patients using the SimGlucose environment.

We explore how interpretability and temporal modeling can enhance clinical reliability in reinforcement learning (RL) systems. Specifically, we compare:

- A feedforward PPO baseline
- A Recurrent PPO with LSTM
- An Attention-augmented Recurrent PPO model that provides feature-level interpretability

## 🚀 Project Highlights

- **Domain**: Medical decision-making (Type 1 Diabetes)
- **Environment**: SimGlucose (based on the FDA-approved UVA/Padova simulator)
- **Goal**: Maintain blood glucose in the target range of 70–180 mg/dL through autonomous insulin dosing
- **Models**: PPO, Recurrent PPO, Attention Recurrent PPO
- **Interpretability**: Feature-level attention to highlight influence of CGM, meal intake, insulin history, and time

## 🏗️ Repository Structure
```text
  Interpretable_RL
  ├── code  # Training scripts for all 3 models and evaluation script
  │ ├── Explainable_RPPO_models.py
  │ └── Final_Test_and_Demonstration.py
  ├── model_weights/ # Pretrained model weights for PPO, Recurrent PPO, Attention PPO
  ├── Explainable_RPPO.pdf # Final report with architecture, methodology, and results
  └── README.md
  ```

## 📊 Key Results

- Recurrent models (with or without attention) significantly outperformed the PPO baseline in glucose control and reduced dangerous episodes.
- Feature-level attention aligned with clinical expectations (e.g., higher weight on meals post-intake).
- Quantitative results averaged over 10 simulated patients:

| Model                | Glucose in Range | Dangerous Episodes |
|---------------------|------------------|--------------------|
| PPO (Baseline)      | 25.7% ± 5.9%     | 6                  |
| Recurrent PPO       | 63.8% ± 9.7%     | 2                  |
| Attention RPPO      | 61.4% ± 9.4%     | 3                  |

## 🧠 Architecture Overview

- **PPO Baseline**: 3-layer feedforward actor-critic
- **Recurrent PPO**: Two stacked LSTM layers followed by dense layers
- **Attention RPPO**: MLP-based feature-level attention → LSTM → Policy/Value heads

Each model is trained with a reward function based on the risk index from Kovatchev et al. (2006), encouraging stable and safe glucose levels.




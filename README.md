# 🧠 Assignment 2 – Q-Learning on Taxi-v3

### 📘 Course: Reinforcement Learning Programming – CSCN 8020
**Student:** Srinu Babu Rai  
**Student ID:** 8994032  
**Instructor:** David Espinosa Carrillo  
**Institution:** Conestoga College  
**Date:** October 2025  

---

## 🚀 Project Overview
This assignment implements the **Q-Learning algorithm** on the **Taxi-v3** environment from **OpenAI Gym**.  
The objective is to train an agent to efficiently navigate the 5×5 taxi grid, pick up passengers, and drop them off at their destinations while minimizing penalties.  

The project explores the effects of **Learning Rate (α)** and **Exploration Factor (ϵ)** on training performance and stability.  

---

## 🧩 Problem Definition
- Environment: **Taxi-v3** (Discrete 500-state problem)  
- Actions: 6 (South, North, East, West, Pickup, Dropoff)  
- Rewards:  
  - `+20` for successful drop-off  
  - `-1` per time-step  
  - `-10` for illegal pickup/drop-off  

---

## ⚙️ Implementation Details
- **Algorithm:** Q-Learning (off-policy TD control)  
- **Hyperparameters (Base Run):**  
  - Learning Rate (**α**) = 0.1  
  - Discount Factor (**γ**) = 0.9  
  - Exploration Rate (**ϵ**) = 0.1  
  - Episodes = 5000  
  - Max Steps per Episode = 200  

---

## 📊 Parameter Experiments
After training the base model, parameter sweeps were performed to observe learning stability and performance:

| Parameter | Tested Values | Observation |
|------------|----------------|-------------|
| **Learning Rate (α)** | 0.001, 0.01, 0.1, 0.2 | α = 0.2 achieved the best performance (fastest convergence, least negative rewards). |
| **Exploration Factor (ϵ)** | 0.1, 0.2, 0.3 | ϵ = 0.1 provided the most stable results; higher exploration delayed convergence. |

---

## 🧮 Key Metrics

| Configuration | Avg Steps | Avg Return | Episodes |
|----------------|------------|-------------|-----------|
| Base (α=0.1, ϵ=0.1) | 30.14 | −21.15 | 5000 |
| α = 0.001 | 185.35 | −258.64 | 5000 |
| α = 0.01 | 127.27 | −160.73 | 5000 |
| α = 0.2 | 23.44 | −11.41 | 5000 |
| ϵ = 0.2 | 32.85 | −32.72 | 5000 |
| ϵ = 0.3 | 35.86 | −46.86 | 5000 |

✅ **Best combination:**  
**Learning Rate α = 0.2, Exploration Factor ϵ = 0.1**  
→ *Achieved the highest average return and lowest average steps.*

---

## 📈 Generated Graphs
The notebook produces 8–9 key plots:
1. Return per Episode (Base Run)  
2. Steps per Episode (Base Run)  
3. Moving Average of Return  
4. Average Return – All Configurations  
5. Average Steps – All Configurations  
6. Learning Rate (α) Sweep – Average Return  
7. Exploration Rate (ϵ) Sweep – Average Return  
8. Return vs Steps Scatter  
9. (Optional) Exploration Rate (ϵ) Sweep – Steps  

---

## 🧰 Repository Contents
```
Assignment2/
│
├── Assignment 2.ipynb          # Main Jupyter notebook with full code
├── Assignment 2.html           # HTML export of notebook with outputs and plots
├── assignment2_utils.py        # Helper functions for environment and agent setup
├── Assignment2.pdf             # Final formatted report (generated)
├── Assignment2.docx            # Editable Word version of the report
├── requirements.txt            # Dependency file for environment setup
└── README.md                   # Project overview and instructions
```

---

## 🧑‍💻 How to Run

1. **Clone or extract the project folder.**  
   ```bash
   git clone <repository-url>
   cd Assignment2
   ```

2. **Create and activate a virtual environment.**  
   ```bash
   python -m venv .venv
   source .venv/bin/activate   # (macOS/Linux)
   .venv\Scripts\activate      # (Windows)
   ```

3. **Install dependencies.**  
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the notebook.**  
   ```bash
   jupyter notebook "Assignment 2.ipynb"
   ```

5. **View HTML output (optional).**  
   Open `Assignment 2.html` in any web browser.

---

## 🧩 Results Summary
- The Q-Learning agent successfully learned optimal routes in the Taxi-v3 grid.  
- Higher learning rates improved training speed and policy accuracy.  
- Excessive exploration (ϵ ≥ 0.2) slowed convergence and reduced reward consistency.  
- **Optimal configuration (α=0.2, ϵ=0.1)** achieved the **best return (−11.41)** and **lowest average steps (23.44)**.

---

## 🏁 Conclusion
The experiment demonstrates that parameter tuning significantly impacts Q-Learning performance.  
For discrete environments like Taxi-v3, **a moderately high learning rate** and **low exploration rate** yield the most stable and efficient learning outcomes.

---

## 📚 References
- OpenAI Gym Documentation: [https://gymnasium.farama.org/](https://gymnasium.farama.org/)  
- Q-Learning Lecture Notes – Conestoga College (David Espinosa Carrillo)  
- Raju, A. (2024). *Implementing Q-Learning in Python: Taxi Environment Case Study.* Medium.  

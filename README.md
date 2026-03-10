# 🤖 Snapbot Olympics: Reinforcement Learning for Robotic Athletics

**Author:** Gina Hong

**Date:** June 21, 2025 

This project focuses on training a Snapbot to compete in three distinct Olympic events: **Side Walk**, **High Jump**, and **Long Jump**. By utilizing Deep Reinforcement Learning (RL), the robot learned to navigate complex physical constraints to achieve task-specific locomotive excellence.

## 📑 Project Overview

The core objective was to develop robust policies using simple yet effective reward structures and tuned hyperparameters. The project demonstrates the trade-offs between exploration and stability in high-dimensional action spaces.

---

## 🏃 Olympic Events & Reward Design

A key finding of this project was that **simple reward structures** often outperformed complex, multi-phase approaches.

### 1. Side Walk (Lateral Locomotion)

* **Primary Goal:** Maximize lateral movement along the y-axis.


* **Reward Function:** Speed-based (distance divided by time).


* **Behavior:** Developed efficient, consistent sideways locomotion patterns.



### 2. High Jump (Vertical Elevation)

* **Primary Goal:** Maximize the maximum vertical height achieved.


* **Reward Formula:** 
$$r_{height} = 100 \times (p\_torso\_cur[2] - h\_base)$$


.


* **Mechanics:** Encouraged proper jumping posture and knee extension.


* **Penalty:** Hip motor noise reduction to stabilize the torso.



### 3. Long Jump (Forward Projection)

* **Primary Goal:** Maximize forward distance while maintaining stability.


* **Reward Formula:** Combined $r_{height}$ with a heavily weighted forward component ($300 \times p\_torso\_cur[0]$).


* **Stability:** Utilized a lateral stability penalty ($r_{lane}$) to prevent deviation from the track.



---

## ⚙️ Training Settings & Hyperparameters

The training was conducted over **1000 episodes** per task with a maximum episode length of **5.0 seconds**.

| Hyperparameter | Side Walk | High Jump | Long Jump |
| --- | --- | --- | --- |
| **Warmup Episodes** | 10 

 | 40 

 | 40 

 |
| **Learning Rate (Actor)** | 0.0005 

 | 0.0001 

 | 0.0001 

 |
| **Learning Rate (Critic)** | 0.0001 

 | 0.0003 

 | 0.0003 

 |
| **Alpha (Entropy)** | 0.1 

 | 1.0 (Increased) 

 | 1.0 

 |
| **Batch Size** | 256 

 | 256 

 | 256 

 |

> 
> **Note:** Alpha values were increased for jumping tasks to encourage better exploration of the vertical action space.
> 
> 

---

## 📊 Results & Analysis

### Quantitative Performance

| Task | Performance Metric | Result |
| --- | --- | --- |
| **Side Walk** | Lateral efficiency | Consistent sideways motion 

 |
| **High Jump** | Max vertical height | Successful upward jumping 

 |
| **Long Jump** | Forward distance | Coordinated lift & projection 

 |

### Key Technical Insights

* **Heavy Weighting:** Applying a 300x weight to the primary objective in Long Jump was crucial for success.


* **Stability Trade-offs:** There is a significant conflict between initial exploration and training stability. Attempts to force stability often reduced overall task performance.


* **Simplicity Wins:** Complex reward designs do not guarantee better outcomes; well-tuned simple functions proved more reliable.



---

## 🚀 Future Work

To further improve performance and resolve the exploration-stability trade-off, future iterations will explore:

* **Advanced Exploration Strategies**.


* **Curriculum Learning** to gradually increase task difficulty.


* **Robust Training Algorithms** to minimize learning instability.

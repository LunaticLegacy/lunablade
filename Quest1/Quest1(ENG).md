# 🧠 "Reassign your Teacher"
中文版本：[这里](Quest1/Quest1.md)

## 📚 Background

In an experimental educational policy, a high school evaluates its teachers based on the proportion of students achieving an **"Excellent"** score in a standardized exam. 

A teacher will be **reassigned** if their class fails to meet the standard of **at least 75% of students scoring 70 or above**, and this result is **statistically significant at a 5% level**.

Teacher A, known for a rigid teaching style, is disliked by a number of students. These students aim to manipulate the exam outcome to cause the teacher to fail the evaluation. However, students also care about their academic performance and must weigh **personal academic cost** against the **collective goal**.

Your task is to design a **behavioral strategy** that **maximizes the probability** of the teacher being reassigned.

---

## 📝 Problem Statement

- **Teacher A** teaches **100 students**.
- A standardized exam will be held in **15 days**.
- Exam scores are integers from **0 to 100** and follow a **normal distribution**.
- A score of **70 or above** is considered **Excellent**.

### 📊 Initial Uninfluenced Score Distribution

If a student is not influenced:

- 90% chance of scoring **≥ 70**
- 10% chance of scoring in **[60, 70)**

---

## 🌀 Persuasion Mechanism

Students can be influenced via a behavioral mechanism called **“persuasion”**, which alters their performance tendencies.

### 🎯 Persuasion Stages and Effects

| Times Persuaded | Score Distribution |
|------------------|-------------------|
| 0 (Uninfluenced) | 90% ≥70, 10% [60,70) |
| 1 time           | 30% ≥70, 70% [60,70) |
| 2 times          | 0% ≥70, 90% [60,70) |
| 3 times          | 90% [0,30), 20% chance of exactly 0 |
| 4+ times         | 100% score exactly 0 |

> Within each score range, scores are **uniformly distributed**.

---

## 🎮 Persuasion Rules

- You have **2 persuasion attempts per day**.
- Each attempt can target **up to 10 students**.
- Success probability depends on group size:

| Group Size | Success Probability |
|------------|---------------------|
| 1 student  | 95%                 |
| 2 students | 90%                 |
| ...        | ...                 |
| 10 students| 50%                 |

- Minimum success probability: **50%**
- A **failed persuasion** permanently reduces that student’s **future persuasion success rate by 10%** (minimum 0%)
- If a student is not persuaded again within **2 days**, their persuasion **level decays** by **1 per day**

---

## ⚖️ Evaluation Criterion

Teacher A will be reassigned if a hypothesis test **rejects the null hypothesis**:

- **Null Hypothesis (H₀):** p ≥ 0.75  
- **Alternative Hypothesis (H₁):** p < 0.75  
- **Significance level:** α = 0.05  

Assume normal approximation for binomial distribution is valid.

---

## ✅ Your Tasks

### 1. 📐 Modeling

- Represent each student’s state (e.g., persuasion level, success probability)
- Define score distributions for each persuasion level
- Capture transition dynamics from daily persuasion

---

### 2. 🧠 Strategy Design

- Design a daily strategy for selecting students to persuade
- Balance:
  - **Depth**: pushing individuals to stage 4
  - **Breadth**: persuading more students at lower levels
- Avoid influence decay with strategic persistence

---

### 3. 📊 Simulation and Analysis

- Simulate exam outcomes under your strategy
- Estimate the number of **Excellent** students
- Perform hypothesis testing to check if reassignment occurs

---

## 🧩 Optional Extensions

- What if **some students act as informants** to Teacher A? How should your strategy adapt?
- What if the school **also evaluates class average score**? What changes in your strategy?

---

## 📤 Output Requirements

- Present your **mathematical model**, **algorithmic/simulation strategy**, and **justification**
- Include visual aids:
  - State diagrams
  - Persuasion/score evolution plots
- Clearly summarize:
  - Strategy performance
  - Whether reassignment is expected to occur

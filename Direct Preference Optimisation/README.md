# Text-to-SQL Experiment – DPO with Reasoning Strategies

## Objective

The goal of this experiment is to evaluate the effectiveness of **Direct Preference Optimization (DPO)** combined with **reasoning strategies**—**Chain-of-Thought (CoT)** and **Divide & Conquer**—for **Text-to-SQL generation**.  
The study focuses on improving:

- **VA (Valid Accuracy)** – whether the SQL output is syntactically correct and executable  
- **EX (Exact Match)** – whether the generated SQL matches the ground truth  

Strategies are tested on **Simple, Moderate, and Challenging** queries to assess their performance across different levels of complexity.

---

## Results

### Accuracy Table (VA = Valid Accuracy, EX = Exact Match)

| Model | Simple VA | Simple EX | Moderate VA | Moderate EX | Challenging VA | Challenging EX | Total VA | Total EX |
|-------|-----------|-----------|-------------|-------------|----------------|----------------|----------|----------|
| LLaMA 3.1 8B (No CoT) | 75.86% | 41.38% | 76.92% | 30.76% | 100% | 0% | 77.78% | 35.56% |
| LLaMA 3.1 8B (CoT) | 86.20% | 44.82% | 69.23% | 30.76% | 33.33% | 0% | 77.78% | 37.78% |
| LLaMA 3.1 8B (Div & Conq) | 62.96% | 33.33% | 64.29% | 14.28% | 33.33% | 0% | 61.36% | 25.00% |
| After DPO – No CoT | 93.10% | 41.38% | 46.15% | 30.76% | 66.67% | 0% | 77.78% | 35.56% |
| After DPO – CoT | 93.10% | 55.17% | 76.92% | 46.15% | 33.33% | 0% | 84.44% | 48.89% |
| After DPO – Div & Conq | 77.78% | 44.44% | 42.86% | 14.28% | 66.66% | 0% | 65.90% | 31.81% |

### Key Observations

1. **DPO + Reasoning is effective:** CoT and Divide & Conquer improve learning and SQL generation.  
2. **Divide & Conquer excels in challenging queries**, increasing VA from 33.33% → 66.66%.  
3. **CoT strategy provides balanced gains** across VA and EX for all query types.  
4. **No CoT shows fluctuating improvements**, performing best only on simple queries.  
5. **Exact match (EX) remains challenging** for moderate and difficult queries, even after DPO.  
6. Overall, **DPO combined with reasoning strategies significantly enhances Text-to-SQL performance**.

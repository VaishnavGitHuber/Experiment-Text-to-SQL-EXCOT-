# Text-to-SQL Experiment with LLaMA 3.1 8B Instruct

## Overview
This project evaluates the **LLaMA 3.1 8B Instruct** model for **text-to-SQL generation** using different prompting strategies:  
- No CoT (No Chain-of-Thought)  
- Simple CoT  
- Divide & Conquer CoT  

The experiment provides baseline accuracy for **simple, moderate, and challenging queries** from the **California_school** database (BIRD dataset).

## Experiment Setup
- **Platform:** Google Colab (GPU / TPU support)  
- **Model:** LLaMA 3.1 8B Instruct  
- **Framework:** Hugging Face Transformers  
- **Quantization:** 4-bit NF4 with double quantization, FP16 computation  
- **Max Tokens:** 2000  
- **Temperature:** 0.1 (deterministic generation)  
- **Dataset:** 50 queries from the California_school database  

## Methodology
1. Load the model with 4-bit NF4 quantization.  
2. Initialize tokenizer and apply LLaMA chat template.  
3. Define system and user prompts for different CoT strategies.  
4. Tokenize inputs and generate SQL queries deterministically.  
5. Process dataset prompts sequentially and save outputs for evaluation.

## Results

### Overall Baseline Accuracy
| Strategy           | Execution Accuracy (EX) | Validation Accuracy (VA) |
|------------------|-----------------------|-------------------------|
| No CoT             | 0.70                  | 0.20                    |
| Simple CoT         | 0.70                  | 0.21                    |
| Divide & Conquer   | 0.62                  | 0.16                    |

### Accuracy by Query Difficulty
| Strategy           | Simple EX | Simple VA | Moderate EX | Moderate VA | Challenging EX | Challenging VA |
|-------------------|-----------|-----------|-------------|-------------|----------------|----------------|
| No CoT             | 0.72      | 0.23      | 0.60        | 0.13        | 1.00           | 0.00           |
| Simple CoT         | 0.78      | 0.28      | 0.63        | 0.13        | 0.40           | 0.00           |
| Divide & Conquer   | 0.61      | 0.22      | 0.70        | 0.07        | 0.20           | 0.00           |

**Observation:**  
- Simple CoT improves accuracy for **simple queries**.  
- Moderate and challenging queries remain difficult for all strategies.  
- Provides a **baseline** before applying **SFT** or **DPO** for further improvements.

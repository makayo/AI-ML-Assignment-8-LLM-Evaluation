# LLM Evaluation with Confusion Matrix  
Author: MARK YOSINAO  
Artificial Intelligence — Fine-Tuning, Classification Metrics, and Error Analysis  

## Environment  
- Python 3.9 (Anaconda environment)  
- Hugging Face Transformers 4.57.3  
- Datasets 4.4.1  
- Evaluate 0.4.6  
- Scikit-learn 1.5.1  
- Matplotlib 3.9.2 / Seaborn 0.13.2  
- Jupyter Notebook  

## Project Overview  
This project formally evaluates the performance of a fine‑tuned LLM (from Assignment 7) on a text classification task (e.g., Sentiment or Topic Classification).  
The evaluation focuses on **in-depth classification metrics** and visualization to gain critical insights into model performance.  

Key goals:  
- Compute Accuracy, Precision, Recall, and F1‑Score (Macro‑averaged).  
- Visualize predictions with a normalized confusion matrix.  
- Perform error analysis on misclassified examples.  
- Justify the choice of F1‑Score (Macro) as the primary evaluation metric.  

## Dataset / Input  
- Held‑out **Test Set** from Assignment 7.  
- Labels: *Negative* and *Positive* sentiment (binary classification).  
- Predictions generated using the fine‑tuned LLM.  

Example metrics (Validation set):  
- Accuracy: 0.725  
- Precision (Macro): 0.927  
- Recall (Macro): 0.500  
- F1‑Score (Macro): 0.650  

## Workflow Summary  
**Metric Calculation**  
- Predictions compared against ground truth labels.  
- Accuracy, Precision, Recall, and F1‑Score computed with Hugging Face `evaluate` and Scikit‑learn.  

**Confusion Matrix Visualization**  
- Confusion matrix generated from predictions.  
- Normalized to show percentages for interpretability.  

**Error Analysis**  
- Identified worst‑performing class (Positive, Recall = 0.50).  
- Selected two misclassified examples for analysis.  
  - Example A: Sarcasm misclassified as Negative.  
  - Example B: Mixed sentiment misclassified as Negative.  
- Probable reasons: ambiguity, conflicting context, and class imbalance.  

**Metric Justification**  
- Accuracy alone can be misleading in imbalanced datasets.  
- F1‑Score (Macro) balances precision and recall across all classes.  
- Ensures minority classes are equally weighted in evaluation.  

## Evaluation  

| Metric      | Value   | Notes                                      |
|-------------|---------|--------------------------------------------|
| Accuracy    | 0.725   | Overall correctness across 200 samples     |
| Precision   | 0.927   | High precision, especially for Positive    |
| Recall      | 0.500   | Positive class recall is weakest           |
| F1‑Score    | 0.650   | Balanced measure, chosen as primary metric |

### Confusion Matrix (Validation)  
|               | Predicted Negative | Predicted Positive |
|---------------|--------------------|--------------------|
| **Negative**  | 94                 | 4                  |
| **Positive**  | 51                 | 51                 |

---

## Results  
- Model achieved **72.5% accuracy** overall.  
- Strong precision but weaker recall for Positive class.  
- Confusion matrix highlights imbalance in correctly identifying Positive samples.  
- Error analysis shows misclassifications often stem from subtle language or conflicting sentiment.  
- F1‑Score (Macro) provides a fairer evaluation than Accuracy, making it the preferred metric.  

This evaluation demonstrates how detailed metrics and visua
## Metric Justification
Accuracy alone (80%) suggests strong performance, but macro-averaged F1-Score (0.80) is a better primary metric because:  
- It balances precision and recall.  
- It treats both classes equally, regardless of dataset size.  
- It exposes weaknesses in detecting positive sentiment that accuracy alone would overlook.  

Thus, F1-Score provides the fairest and most informative evaluation of the model’s true performance.

# LLM Evaluation — Sentiment Classification  
Author: MARK YOSINAO  
Artificial Intelligence — Fine-Tuned Language Models, Classification Metrics, and Error Analysis  

## Environment  
- Python 3.11.3  
- Hugging Face Transformers 4.x  
- Jupyter Notebook (Anaconda environment)  
- Scikit-learn 1.x  
- Pandas 2.x  
- Matplotlib / Seaborn  

---

## Project Overview  
This project evaluates the performance of a fine-tuned Large Language Model (LLM) on a binary sentiment classification task. The evaluation includes calculation of key metrics, visualization of a confusion matrix, error analysis, and a comparison between baseline and fine-tuned results.  

---

## Environment  
- Python 3.11.3  
- Hugging Face Transformers 4.x  
- Jupyter Notebook (Anaconda environment)  
- Scikit-learn 1.x  
- Pandas 2.x  
- Matplotlib / Seaborn  

---

# Model Evaluation

## Metrics (Test Results)
| Metric              | Value |
|---------------------|-------|
| Accuracy            | 0.80  |
| Precision (Macro)   | 0.80  |
| Recall (Macro)      | 0.80  |
| F1-Score (Macro)    | 0.80  |

These results show balanced performance across both classes. The model achieves 80% accuracy overall, with macro-averaged precision, recall, and F1 all near 0.80 — indicating consistent detection of both positive and negative sentiment.

---

## Classification Report (Test)
| Class     | Precision | Recall | F1-Score | Support |
|-----------|-----------|--------|----------|---------|
| Negative  | 0.78      | 0.87   | 0.82     | 53      |
| Positive  | 0.83      | 0.72   | 0.77     | 47      |

- Negative class: Strong recall (0.87) and solid F1 (0.82).  
- Positive class: Precision is high (0.83), recall is lower (0.72), but much improved compared to earlier validation results.  

---

## Confusion Matrix (Test Results)
| True Class | Predicted Negative | Predicted Positive |
|------------|--------------------|--------------------|
| Negative   | 87%                | 13%                |
| Positive   | 28%                | 72%                |

---

## Error Analysis
- Positive class: Recall improved to 0.72 (vs. 0.50 in validation). The model now correctly identifies most positive reviews, though nuanced or mixed sentiment remains challenging.  
- Negative class: Slightly less dominant than validation (87% vs. 96%), but still strong overall.  
- Misclassifications often occur with subtle or conflicting language, e.g.:  
  - “The film left a lasting impression.” → implicit positivity without explicit keywords.  
  - “The acting was poor, but the ending was beautiful.” → mixed signals confuse the model.  

---

## Inference Results on Custom Reviews
| Test Case | Review Text                                        | Predicted Sentiment |
|-----------|----------------------------------------------------|---------------------|
| Test 1    | This movie was amazing!                            | Positive            |
| Test 2    | Terrible acting and a boring plot.                 | Negative            |
| Test 3    | The visuals were stunning, but the story was weak. | Negative            |

---

## Conclusion
- Baseline: Struggled with positives, often defaulting to negatives.  
- LoRA Fine-Tuning: Improved balance, with measurable gains in accuracy and F1 score.  
- Strengths: High precision for positives, strong recall for negatives.  
- Limitations: Positive recall, while improved, is still lower than negative recall; nuanced sentiment remains difficult.  

---

## Metric Justification
Accuracy alone (80%) suggests strong performance, but macro-averaged F1-Score (0.80) is a better primary metric because:  
- It balances precision and recall.  
- It treats both classes equally, regardless of dataset size.  
- It exposes weaknesses in detecting positive sentiment that accuracy alone would overlook.  

Thus, F1-Score provides the fairest and most informative evaluation of the model’s true performance.

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

## Metrics (Validation Results)  

| Metric              | Value   |
|---------------------|---------|
| Accuracy            | 0.725   |
| Precision (Macro)   | 0.79    |
| Recall (Macro)      | 0.73    |
| F1-Score (Macro)    | 0.71    |

These results show strong precision for the positive class but weaker recall, indicating difficulty in consistently identifying positive sentiment.  

---

## Confusion Matrix (Normalized Percentages)  

| True Class | Predicted Negative | Predicted Positive |
|------------|--------------------|--------------------|
| Negative   | 96%                | 4%                 |
| Positive   | 50%                | 50%                |

Interpretation: The model is highly effective at identifying negative reviews but struggles with positive reviews, correctly classifying only half of them.  

---

## Error Analysis  
The worst-performing class is **Positive**, with recall = 0.50 and F1 = 0.65. Misclassifications often occurred due to:  

1. **Subtle Language**  
   - Example: *“The film left a lasting impression.”*  
   - Reason: Implicit positivity without explicit sentiment keywords led to misclassification.  

2. **Conflicting Context**  
   - Example: *“The acting was poor, but the ending was beautiful.”*  
   - Reason: Mixed signals confused the model, which weighted negative cues more heavily.  

---

## Inference Results on Custom Reviews  

| Test Case | Review Text                                       | Predicted Sentiment |
|-----------|---------------------------------------------------|---------------------|
| Test 1    | This movie was amazing!                           | Positive            |
| Test 2    | Terrible acting and a boring plot.                | Negative            |
| Test 3    | The visuals were stunning, but the story was weak.| Negative            |

---

## Conclusion  
- **Baseline:** Failed to recognize positives, predicting only negatives.  
- **LoRA Fine-Tuning:** Improved performance with measurable gains in accuracy and F1 score.  
- **Strengths:** High precision for positives, strong recall for negatives.  
- **Limitations:** Positive recall remains low; the model struggles with mixed or nuanced sentiment.  

---

## Metric Justification  
Accuracy alone (72.5%) suggests moderate performance but hides class imbalance. **Macro-averaged F1-Score** is a better primary metric because:  
- It balances precision and recall.  
- It treats both classes equally, regardless of dataset size.  
- It exposes weaknesses in detecting positive sentiment that accuracy alone would overlook.  

Thus, F1-Score provides a fairer and more informative evaluation of the model’s true performance.  

---

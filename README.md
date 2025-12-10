# LLM Evaluation with Confusion Matrix  
Author: MARK YOSINAO  
Artificial Intelligence — Fine-Tuning, Classification Metrics, and Error Analysis  

## Environment  
- Python 3.9 (Anaconda environment)  
- Hugging Face Transformers 4.57.3  
- Datasets 4.4.1  
- Evaluate 0.4.6  
- Scikit-learn 1.5.1  
- Matplotlib / Seaborn  
- Jupyter Notebook  

## Project Overview  
This project formally evaluates the performance of a fine‑tuned LLM (from Assignment 7) on a text classification task (Sentiment Analysis).  
The evaluation includes:  
- Computing Accuracy, Precision, Recall, and F1‑Score (Macro‑averaged).  
- Visualizing predictions with a normalized confusion matrix.  
- Performing error analysis on misclassified examples.  
- Testing the model on custom reviews to validate behavior.  

---

## Validation Metrics  

The fine‑tuned LLM was evaluated on the held‑out **Validation Set**.  
The following metrics were computed:

- Accuracy: 0.695  
- Precision (Macro): 0.80  
- Recall (Macro): 0.70  
- F1‑Score (Macro): 0.67  

### Classification Report

| Class        | Precision | Recall | F1‑Score | Support |
|--------------|-----------|--------|----------|---------|
| Negative     | 0.62      | 0.99   | 0.76     | 98      |
| Positive     | 0.98      | 0.41   | 0.58     | 102     |
| Accuracy     |           |        | 0.69     | 200     |
| Macro Avg    | 0.80      | 0.70   | 0.67     | 200     |
| Weighted Avg | 0.80      | 0.69   | 0.67     | 200     |

### Interpretation
- Negative class: High recall (0.99) → the model correctly identifies almost all negative samples.  
- Positive class: Lower recall (0.41) → the model misses many positive samples, often misclassifying them as negative.  
- Accuracy (0.69): Reflects overall correctness but hides imbalance between classes.  
- F1‑Score (Macro 0.67): Provides a balanced measure across both classes, making it the preferred evaluation metric.  

---

## Normalized Confusion Matrix (Validation Set)

This matrix shows the proportion of correct and incorrect predictions for each class.  
It highlights that the model performs well in identifying Negative cases (99% accuracy), but struggles with Positive cases (only 41% correctly predicted).

| True Label ↓ / Predicted → | Negative | Positive |
|----------------------------|----------|----------|
| Negative                   | 0.99     | 0.01     |
| Positive                   | 0.59     | 0.41     |

- True Negative (Negative → Negative): 99%  
- False Positive (Negative → Positive): 1%  
- False Negative (Positive → Negative): 59%  
- True Positive (Positive → Positive): 41%  

Interpretation:  
The model is highly confident in identifying negative sentiment, but tends to misclassify positive sentiment as negative — consistent with the lower recall and F1‑score for the Positive class.

---

## Custom Review Classification  

To further evaluate the model, three custom reviews were tested to observe how well it handles clear and ambiguous sentiment:

### Test Cases and Results
- **Test 1 (Clear Positive):**  
  *Input:* “This movie was amazing!”  
  *Output:* Positive  
  *Interpretation:* The model correctly identified strong positive sentiment.

- **Test 2 (Clear Negative):**  
  *Input:* “Terrible acting and a boring plot.”  
  *Output:* Negative  
  *Interpretation:* The model correctly classified clear negative sentiment.

- **Test 3 (Mixed/Ambiguous):**  
  *Input:* “The visuals were stunning, but the story was weak.”  
  *Output:* Negative  
  *Interpretation:* The model leaned toward negative sentiment in mixed reviews, consistent with its lower recall for positives.

### Summary
The model performs well on clear sentiment cases but struggles with mixed or nuanced reviews, often defaulting to negative classification. This behavior aligns with the quantitative metrics, where recall for the Positive class is significantly lower.

---

## Error Analysis  

The Positive class had the weakest performance (Recall = 0.41, F1 = 0.58).  

**Example 1**  
- True Label: Positive  
- Predicted Label: Negative  
- Text: “I loved the product, but the shipping was terrible.”  
- Reason: Conflicting sentiment caused the model to focus on the negative aspect.  

**Example 2**  
- True Label: Positive  
- Predicted Label: Negative  
- Text: “Wow, just great… not!”  
- Reason: Sarcasm confused the model; subtle cues were missed.  

Interpretation:  
- The model struggles with ambiguous or conflicting context.  
- Sarcasm and nuanced language are not well captured.  
- Additional training data or augmentation focusing on nuanced language could improve recall for positives.  

---

## Metric Justification  

- Accuracy alone can be misleading in imbalanced datasets.  
- F1‑Score (Macro‑averaged) balances precision and recall across all classes.  
- Macro‑averaging ensures minority classes are equally weighted.  
- For sentiment classification, F1‑Score (Macro) is a more robust and fair evaluation metric than Accuracy.  

---

## Results  

- Model achieved 69.5% accuracy overall.  
- Strong precision but weaker recall for Positive class.  
- Confusion matrix highlights imbalance in correctly identifying Positive samples.  
- Custom review tests confirm the model’s tendency to misclassify mixed sentiment as Negative.  
- F1‑Score (Macro) provides a fairer evaluation than Accuracy, making it the preferred metric.  

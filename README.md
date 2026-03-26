# fairness-aware-decision-systems
---

## Overview

This project studies fairness in machine learning using the Adult Income dataset. Income prediction is used as a proxy for automated decision-making (e.g., loan approval), and the goal is to evaluate whether fairness can be improved without changing the underlying model.

---

## Research Question

Can group-specific decision thresholds reduce disparities in false negative rates across racial groups while maintaining predictive performance?

---

## Key Idea

Rather than modifying the model itself, this project separates:

- Prediction: probability estimates from a classifier  
- Decision: threshold used to convert probabilities into outcomes  

By assigning different thresholds to different groups, we can reduce disparities in error rates.

---

## Methodology

- Dataset: Adult Income (UCI)
- Target: Income > $50K (binary classification)
- Groups: White vs Black
- Model: Logistic Regression

### Steps

1. Train a baseline classifier  
2. Generate predicted probabilities  
3. Apply a global threshold (baseline)  
4. Apply group-specific thresholds (fairness-aware system)  
5. Compare performance and fairness metrics  

---

## Results

| Metric | Baseline | Fairness-Aware |
|--------|----------|----------------|
| Accuracy | 0.8483 | 0.8444 |
| Precision | 0.7307 | 0.6744 |
| Recall | 0.5929 | 0.6929 |
| F1 Score | 0.6547 | 0.6835 |
| ROC AUC | 0.9050 | 0.9050 |

### False Negative Rates

| Group | Baseline | Fairness-Aware |
|--------|----------|----------------|
| White | 0.4033 | 0.3070 |
| Black | 0.4853 | 0.3088 |

### Fairness Outcome

- FNR disparity reduced from 0.0819 to 0.0018  
- Approximately 97.8% reduction in disparity  
- Accuracy decreased by 0.39 percentage points  

---

## Key Insights

- A single global threshold produces unequal error rates across groups  
- Fairness can be improved through post-processing without retraining the model  
- ROC AUC remains unchanged, since the underlying model is the same  
- The baseline model is not Pareto optimal  
- There is a tradeoff: improved fairness increases false positives and reduces precision  

---

## Tradeoff Analysis

The system evaluates multiple threshold combinations and identifies solutions that balance fairness and accuracy.

The selected fairness-aware solution achieves near-zero disparity while maintaining high overall performance.

---

## Limitations

- Only two racial groups (White and Black) are considered  
- Group-specific thresholds introduce differential treatment across groups  
- Does not address bias in the training data  
- Focuses only on post-processing methods  

---

## Future Work

- Extend analysis to additional demographic and intersectional groups  
- Explore fairness-aware training objectives  
- Evaluate other model types  
- Apply the framework to healthcare and other high-stakes settings  

---

## Conclusion

This project shows that fairness in classification systems can be substantially improved through threshold adjustments, with minimal loss in accuracy.

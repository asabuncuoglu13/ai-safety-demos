# **Tabular Data Classification Technical Audit Plan**

## **1. Overview**
This audit plan provides a structured approach to evaluate the robustness, security, privacy, and fairness of a traditional shallow Machine Learning (ML) model (e.g., Decision Tree, Gradient Boosting) applied to tabular data classification. The audit will be conducted using Python-based tools to ensure reproducibility and effectiveness.

> If model card, datasheets, or other technical documentation such as UML diagrams are available for your use, request them. Guide your research with the considerations already listed in this documentation. In the end, compare the results of this technical audit with the results recorded in the documentation.

> Track all your experiments with [W&B][https://wandb.ai/site/], [MLflow](https://mlflow.org/), or any other experiment tracking tool for reproducibility and auditability of the audit.

## **2. Audit Phases**
1. **Task Performance Evaluation**
2. **Robustness Testing**
3. **Security Assessment**
4. **Privacy Assessment**
5. **Fairness & Bias Analysis**
6. **Explainability & Interpretability Review**
7. **Final Reporting & Recommendations**

---

## **3. Audit Steps & Tools**

### **Step 0: (Optional - based on data availability) Task Performance Evaluation:**
**Objective:** Measure how well the model performs on the classification task.

- **Tools:** [scikit-learn](https://scikit-learn.org/), 
- **Method:**
  1. Define key "reliable" metrics (accuracy, precision, recall, F1-score, AUC-ROC).
  2. Evaluate on a holdout test dataset.
  3. Use cross validation methods.
  4. Document findings and potential improvements.

### **Step 1: Robustness Testing**
**Objective:** Assess the model's resilience to data perturbations and adversarial changes.

- **Tools:** [Alibi Detect](https://github.com/SeldonIO/alibi-detect), [Foolbox](https://github.com/bethgelab/foolbox)
- **Method:**
  1. Apply noise and perturbations to input data.
  2. Evaluate performance degradation.
  3. Use adversarial attack methods (if applicable) to test vulnerabilities.
  4. Identify and document robustness weaknesses.

#### **Step 2. Security Vulnerability Testing**
**Objective:** Identify security threats affecting model deployment.

- **Tools:** [Adversarial Robustness Toolbox (ART)](https://github.com/Trusted-AI/adversarial-robustness-toolbox)
- **Method:**
  1. Check for adversarial robustness using ART.
  2. Test against poisoning and evasion attacks.
  3. Identify patterns of model exploitation.
  4. Report security risks.

### **Step 3. Privacy Risk Analysis**
**Objective:** Detect potential data leaks or privacy risks in model outputs.

- **Tools:** [PANORAMIA](https://github.com/ubc-systopia/panoramia-privacy-measurement)
- **Method:**
  1. Analyse model predictions for potential data leakage.
  2. Quantify the privacy measurement using a reliable metric.
  3. Document privacy risks and mitigation strategies.

### **Step 4: Fairness & Bias Analysis**
**Objective:** Ensure the model provides equitable predictions across different demographic groups.

- **Tools:** [Fairlearn](https://github.com/fairlearn/fairlearn), [Aequitas](https://github.com/dssg/aequitas.git), [Themis-ML](https://github.com/cosmicBboy/themis-ml)
- **Method:**
  1. Define protected characteristics for the use case.
  2. Define fairness metrics (e.g., demographic parity, equal opportunity).
  3. Use `Fairlearn` to compute disparities across subgroups.
  4. Validate bias using `Aequitas` audit tool.
  5. Document fairness risks and recommend mitigation measures.

### **Step 5: Explainability & Interpretability Review**
**Objective:** Evaluate the interpretability of the model’s predictions. Use this analysis to guide the overall assessment of this auditing and mitigation recommendations.

- **Tools:** [SHAP](https://github.com/shap/shap), [LIME](https://github.com/marcotcr/lime), [InterpretML](https://interpret.ml/)
- **Method:**
  1. Use `SHAP` and `LIME` to explain individual predictions.
  2. Apply `InterpretML` for global and local explanations.
  3. Compare feature importance across different explanation methods.
  4. Summarize findings in a transparency report.

### **Step 6: Final Reporting & Recommendations**
- Compile all findings into a structured audit report.
- Include key risks, detected issues, and mitigation strategies.
- Provide recommendations for improving model safety, fairness, and robustness.

---

## **4. Deliverables**
- **Audit Report:** Summarizes findings, risks, and recommendations.
- **Code & Logs:** Scripts and logs used during the audit.
- **Mitigation Plan:** Steps to address identified vulnerabilities.


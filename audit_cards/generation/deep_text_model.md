# **LLM Technical Audit Plan**

## **1. Overview**
This audit plan provides a structured approach to evaluate the robustness, security, privacy, and fairness of a Large Language Model (LLM) application where only a black-box API is available. The audit will be conducted using Python-based tools to ensure reproducibility and effectiveness.

> If model card, datasheets, or other technical documentation such as UML diagrams are available for your use, request them. Guide your research with the considerations already listed in this documentation. In the end, compare the results of this technical audit with the results recorded in the documentation.

> Track all your experiments with [W&B][https://wandb.ai/site/], [MLflow](https://mlflow.org/), or any other experiment tracking tool for reproducibility and auditability of the audit.

## **2. Audit Phases**

1. **Task Performance Evaluation**
2. **Robustness Testing**
3. **Security Assessment**
4. **Privacy Assessment**
5. **Overall Safety Assessment**
6. **Fairness & Bias Analysis**
7. **Explainability & Interpretability Review**
8. **Final Reporting & Recommendations**

---

## **3. Audit Steps & Tools**

### **Step 0: Task Performance Evaluation**
**Objective:** Measure how well the LLM performs for the intended application.

- **Tools:** [Ragas](https://docs.ragas.io/en/stable/)
- **Method:**
  1. Define task-specific metrics (accuracy, relevance, fluency, coherence).
  2. Use `ragas` to evaluate answer quality in RAG-based applications.
  3. Compare outputs with a ground truth dataset (if available).
  4. Document findings.

> Also, utilise tools like [comet-ml/opik](https://github.com/comet-ml/opik) to structure the experimentation process.

### **Step 1: Robustness Testing**
**Objective:** Evaluate the model's resilience to adversarial prompts and perturbations.

- **Tools:** [JailbreakBench](https://github.com/JailbreakBench/jailbreakbench)
- **Method:**
  1. Generate adversarial prompts to test jailbreaking risks.
  2. Log cases where the model violates expected behavior.
  3. Identify patterns in failure cases.
  4. Recommend mitigation strategies.

### **Step 2: Security Testing**
**Objective:** Evaluate the model's resilience to adversarial prompts and perturbations.

- **Tools:** [Garak](https://github.com/NVIDIA/garak/), 
- **Method:**
  1. Run garak tests including prompt injection, toxicity generation, encoding-based bypass, automatic soak test.
  2. Log cases where the model violates expected behavior.
  3. Identify patterns in failure cases.
  4. Recommend mitigation strategies.

### **Step 3: Privacy Assessment**
**Objective:** Detect if the LLM unintentionally leaks sensitive information.

- **Tools:** [Chirps](https://github.com/mantiumai/chirps.git)
- **Method:**
  1. Input queries containing personal/private data.
  2. Check if responses include leaks or sensitive details.
  3. Document risks and propose mitigation (e.g., prompt filtering, differential privacy techniques).

### **Step 4: General Safety & Vulnerability Assessment**
**Objective:** Identify potential security threats in model responses.

- **Tools:** [Inspect](https://inspect.ai-safety-institute.org.uk/)
- **Method:**
  1. Use `Inspect` and suggested benchmarks for general safety evaluations.
  2. Report security vulnerabilities.

### **Step 5: Fairness & Bias Analysis**
**Objective:** Ensure that the model provides equitable responses across different user groups.

- **Tools:** [Fairlearn](https://github.com/fairlearn/fairlearn), [Aequitas](https://github.com/dssg/aequitas.git)
- **Method:**
  1. Define sensitive attributes (e.g., gender, race, age).
  2. Use `Fairlearn` to compute fairness metrics.
  3. Use `Aequitas` for bias audits on response distributions.
  4. Document fairness risks and mitigation plans.

### **Step 6: Explainability & Interpretability Review**
**Objective:** Assess how understandable the model’s decisions are.

- **Tools:** [LIT](https://github.com/PAIR-code/lit), [SHAP](https://github.com/shap/shap), [LIME](https://github.com/marcotcr/lime), [LLM Comparator](https://github.com/PAIR-code/llm-comparator)
- **Method:**
  1. Use `LIT` for interactive analysis.
  2. Apply `SHAP` and `LIME` to generate feature attributions for responses.
  3. Compare outputs across different LLMs using `LLM Comparator`.
  4. Provide transparency reports on explainability findings.

### **Step 7: Final Reporting & Recommendations**
- Compile all findings into a structured audit report.
- Include key risks, detected issues, and mitigation strategies.
- Provide recommendations for improving LLM safety, fairness, and robustness.

---

## **4. Deliverables**
- **Audit Report:** Summarizes findings, risks, and recommendations.
- **Code & Logs:** Scripts and logs used during the audit.
- **Mitigation Plan:** Steps to address identified vulnerabilities.

## **5. Conclusion**
This audit ensures that the LLM application meets essential robustness, security, privacy, and fairness standards. Following this structured process will help developers and stakeholders build safer, more reliable AI systems.
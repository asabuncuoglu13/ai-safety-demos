# Explainability

This repo includes examples of SHAP, LIME, and Integrated Gradients methods. They are model agnostic feature explainability techniques.

**SHAP (SHapley Additive exPlanations)** is an interpretability method that assigns importance scores to each feature in a model. It explains a model’s predictions by considering the contribution of each feature to the final output across different coalitions of input features.

**Integrated Gradients** assigns importance to individual input tokens by comparing a model's predictions on a baseline (e.g., zero vector) with the actual input. It calculates the gradient of the model's output with respect to the input tokens and integrates these gradients along the path from the baseline to the input, helping identify which tokens contribute most to the prediction. 

When model's gradient information is not available, **LIME (Local Interpretable Model-agnostic Explanations)** is a model-agnostic explanation method that can be utilised to explain individual predictions. It works by perturbing the input data slightly and observing changes in the output, then fitting a simpler, interpretable model (like a linear model) to approximate the original model's behavior in that local region. This helps identifying which features are most influential in a specific prediction.
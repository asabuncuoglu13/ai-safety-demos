# Audit Cards

Based on our test execution methodology:
1. Identify tasks (classification, regression, clustering, generation, etc.)
2. Validate architecture:(shallow ML models, deep ML models, AI orchestration, agentic systems, etc.)
3. Validate input types: (tabular, text, image, multimodal)
4. For each trustworthiness characteristic, evaluate components: Data, algorithm, interaction

We have developed a set of audit cards to serve as an initial framework for the technical auditing process.  

These cards are intended as templates rather than comprehensive, end-to-end solutions. They provide structured guidance but should be adapted to your specific use case. A thorough audit requires reviewing similar existing applications, consulting relevant literature, and identifying appropriate libraries for testing hypotheses. However, these audit cards facilitate a significant portion of the auditing process by recommending libraries identified through our previous experiments. 

## List of Audit Cards:

**Classification:**
1. [Shallow Model - Tabular Data](./classification/shallow_tabular.md)


**Generation:**
1. [Deep Model - Text Data](./generation/deep_text_model.md)
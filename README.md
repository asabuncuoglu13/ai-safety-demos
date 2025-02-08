# AI Safety - Test Methodology

This methodology assumes that the tester has access to model training and inference APIs, but no internal mechanism information such as data sources and model architecture information.

Let's think about traditional risk-based testing in a system design process, we would consider:

- Test case generation,
- Test data generation,
- Test case execution,
- Test monitoring and control,
- Overall management of this process

It is standardised in ISO/IEC/IEEE 29119.

## Generate Test Cases

1. It is a risk-based test generation. So, a risk register is required. Use the latest AI Safety report for the risk register creation: <https://www.gov.uk/government/publications/international-ai-safety-report-2025>
2. Define specific tests for each trustworthy AI characteristic: 
```mermaid
graph TD
    A[Trustworthy AI] --> B[Valid and Reliable--Robust]
    A --> C[Safe]
    A --> D[Secure and Resilient]
    A --> E[Explainable and Interpretable]
    A --> F[Privacy-Enhanced]
    A --> G[Fair with harmful bias managed]
```
> Note that "accountable and transparent" is another characteristic that spans all model lifecycle.
3. Assess test coverage to adequately assess every risk item in the register. Define new test cases if needed.

## Generate Test Data

1. This is the trickiest stage. Finding or generating the right, reliable, private, safe data that can cover the test cases perfectly is challenging. So, the first step is identifying limitations.
2. Check existing datasets and benchmarks (the list is not exhaustive):
   - Huggingface
   - UCI ML Repository
   - Kaggle
   - Stanford HELM
   - MLCommons Benchmarks
3. Run an EDA on selected test data. Do not over analyse: It can unconciously affect the test design to perform well in benchmark. Do not under analyse: See if the data is reliable and cover the test cases.

## Test Case Execution

See the demo notebooks to understand the overall execution process.

```mermaid
graph TD;
    A[Machine Learning System] --> B[Data Collection and Pre-Processing]
    B --> C[Data]
    B --> D[Algorithm]
    B --> E[Interaction]

    A --> F[Model Training and Evaluation]
    A --> G[Deployment and Inference]

    C --> H[Evaluation Techniques]
    C --> I[Mitigation Techniques]

    H --> J[Risk Analysis and Scoring]
    I --> J

    J --> K[Security and Privacy]
    J --> L[Infrastructure and Maintenance]
    J --> M[Environment and Sustainability]
    J --> N[Usability and Inclusivity]
```

Follow a structured framework. Above diagram shows this repository's approach. It helps structuring the test case development process as well as communicating the results.

-	**ML Steps:** A traditional ML pipeline includes data collection, data pre-processing, training, validation, deployment and monitoring steps.
-	**Components:** For each development stage, consider data, algorithm and interaction components.
-	**Assessment:** For each component of each step, select evaluation and mitigation techniques.
    - **Evaluation:** Define security, privacy and fairness metrics and apply evaluation techniques based on the selected metrics. 
    - **Potential harm analysis:** Follow a categorical harm analysis approach, based on AHA! and CSET-AIID harm taxonomies:
        -	Quality of service harms
        -	Representational harms
        -	Legal and reputational harms
        -	Social, societal, and well-being harms
        -	Loss of rights or agency
        -	Allocational harms
    - **Mitigation:** Define tangible steps to increase security, privacy and fairness overall.
- **Implications:** The implications can be specific steps to be taken or generalized perspectives to consider in future iterations of the development process. Whether specific or generalized, they should lead to developing some tangible steps. Categorize implications under four headlines: “Security and privacy,” “environment and sustainability,” “usability and inclusivity,” and “infrastructure and maintenance.” 



## Test Monitoring and Control

Almost all ML-testing is compute heavy, which means it requires close monitoring to use the resources efficiently. 

## Overall Management

Generation, execution, monitoring and control are only a few processes in a risk-based test management process. Test environment implementation and maintenance throughout this lifecycle, as well as communication of test results are other important stages in this process.
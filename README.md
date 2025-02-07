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

## Test Monitoring and Control

Almost all ML-testing is compute heavy, which means it requires close monitoring to use the resources efficiently. 

## Overall Management

Generation, execution, monitoring and control are only a few processes in a risk-based test management process. Test environment implementation and maintenance throughout this lifecycle, as well as communication of test results are other important stages in this process.
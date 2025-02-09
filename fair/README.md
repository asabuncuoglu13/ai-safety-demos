# Fairness

Auditing the fairness of AI models is a challenging process as defining what fairness means depends on the context of a specific application. Auditing an algorithm, regardless of its type, is a dynamic and non-linear process. [Koshiyama et al.](https://www.ssrn.com/abstract=3778998) demonstrated the interrelation between development stages and auditing verticals in five main steps:

**Stages:** | Data and Task Setup | Feature pre-processing | Model selection | Post-processing and Reporting| Productionizing and Deploying
----|---- | ---- | ----| ---- | ---- |
**Explainability**| Data collection and labelling | Dictionary of variables | Model complexity | Auxiliary tools | Interface and documentation
**Fairness** | Population balance | Fair representations | Fairness constraints | Bias metrics assessments | Real-time monitoring of bias metrics

## Use a Standardised Fairness Ontology:
One option is using Franklin et al.'s Fairness Metrics Ontology as the standard relational map of fairness notions and metrics. So, any fairness experiment report follows the organisational hierarchy of this ontology:

![Fairness Ontology](https://github.com/frankj-rpi/fairness-metrics-ontology/blob/main/diagrams/FairnessOntologyFull.png?raw=true)

> See the ontology schema here: <https://github.com/frankj-rpi/fairness-metrics-ontology/tree/main>

And for each fairness metric, each bias evaluation and mitigation result follows this schema in the reporting:

```yaml
bias_metrics:
  groups:
    group_name:
      description: ""
      label: ""
      metrics:
        - name: ""
          description: ""
          value: 0
          threshold: 0
          bigger_is_better: ""
          label: ""
          notes: ""
          sg_params: {}
```

## Algorithmic Fairness Checks:

- **Model Explainability**: Use explainability methods to kickstart the fairness hypothesis generation process. Explore which features affect the model how. models
- **Chose Bias Evaluation Metrics**
   - **Group Fairness Metrics**: Ensure that the prediction or error rates are similar across groups.
   - **Individual Fairness**: Verify that similar individuals receive similar predictions, regardless of sensitive attributes.
   - **Calibration across Groups**: Ensure that predicted probabilities are well-calibrated across different demographic groups.


## Linking Fairness Evaluation Results to UK Equality Act 2010

The Equality Act (such as the UK's Equality Act 2010) aims to protect individuals from discrimination and promote equality across various protected characteristics, including age, disability, gender reassignment, race, religion or belief, sex, sexual orientation, marriage and civil partnership, and pregnancy and maternity. Here, we summarised how bias evaluation and mitigation principles can align with Equality Act considerations to ensure compliance and ethical alignment. Each item starts with the corresponding entity of our standardised recording format:

- *[fairness:data:sensitive_characteristics]* In the data quality assessment, we can ensure that datasets are inclusive of all protected characteristics to avoid direct or indirect discrimination. Data collection should represent protected groups to avoid underrepresentation, which could lead to unfavorable treatment of certain demographics. Further, identifying and mitigating any imbalances to prevent discrimination against underrepresented groups can support achieving fairness by balancing groups.
- *[fairness:data:preprocessing]* Augmenting data for underrepresented groups is tricky. It can help fulfilling the Act’s requirement to ensure all groups have equal representation and opportunities. However, it can also create inorganic scenarios and create some kind of indirect discrimation.
-  *[fairness:data:preprocessing]* Removing sensitive attributes is a standard approach in "fairness through unawareness". It can prevent direct discrimination. To comply with the Act, data should be processed in such a way that no undue bias related to protected characteristics is introduced.
- *[fairness:data:variable_profile]* Practitioners should further explore whethr new features reintroduce protected characteristic information in unintended ways. Derived features must be assessed to avoid indirect discrimination.
- *[fairness:model]* Algorithm choice should align with the Act’s requirements to ensure fair and equal treatment.
- *[fairness.yml:postprocessing]* Understanding how models make decisions helps ensure fairness across protected groups. Transparent model behavior supports accountability and compliance with anti-discrimination standards.
- *[fairness.yml:bias_metrics]* Fairness metrics directly address the requirements for non-discrimination and equal treatment. Models should be evaluated using these metrics to ensure no group or individuals within protected groups experiences unfair treatment or disadvantage.
- *[fairness.yml:postprocessing]* Adjusting thresholds in model decision making can help balance outcomes, reducing the risk of adverse effects on vulnerable groups. These kind of post-processing adjustments align with promoting equal outcomes as per the Equality Act’s provisions. However, it should also be carefully monitored.

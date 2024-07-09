# Mitigating Bias

[](./challenges.md) demonstrated possible challenges in identifying bias and [](./examples.md) presented some use cases on challenging bias sources to identify throughout the ML pipeline. Mitigating bias is a challenging issue that ideally we cannot achieve due to the nature of model learning mechanisms. We are developing a model with limited parameters with a given sample to create some patterns based on this data that can minimize some error function for the possible future values. In this system, we will have misclassifications, and due to misclassification some individuals from disadvantaged/protected groups will be harmed more. The aim is to minimise this as much as possible and establish an active human-in-the-loop approach to identify mis-represented individuals better.

## Generating Counterfactual Data Samples

We can generate data samples that modifies the protected attributes to help model focus on the rest of the data atrributes.

We can also utilise counterfactual samples in the alignment process of the LLM models, which is an essential step of building human-value aligned (or just aligned) models {cite}`butcher24`
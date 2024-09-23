# Mitigating Bias

[Bias Types](./bias.md) chapter demonstrated possible challenges in identifying bias and [Fairness of Finance LLMs](../usecases/finance/introduction.md) presents some use cases from finance sector son challenging bias sources to identify throughout the ML pipeline. Mitigating bias is a challenging issue that ideally we cannot achieve due to the nature of model learning mechanisms. We are developing a model with limited parameters with a given sample to create some patterns based on this data that can minimize some error function for the possible future values. In this system, we will have misclassifications, and due to misclassification some individuals from disadvantaged/protected groups will be harmed more. The aim is to minimise this as much as possible and establish an active human-in-the-loop approach to identify mis-represented individuals better.

## Data Balancing and Augmentation

Data balancing techniques can be used to mitigate bias in machine learning models. These techniques aim to address the imbalance in the distribution of different classes or groups within the dataset. We can randomly remove samples from the majority class or synthesize more data for minority class to increase their representation in the dataset. These methods simply aim to assign balanced weights to the minority and majority classes to achieve a more balanced representation considering the selected fairness notions. In this section, we mainly focus on counterfactuals and balancing data by generating new counterfactual samples.

### Counterfactuals

Counterfactuals are hypothetical scenarios or instances that represent alternative outcomes or observations that could have occurred under different conditions. In the context of machine learning and fairness, counterfactuals are used to generate new data samples by modifying the protected attributes while keeping the remaining attributes unchanged. These modified samples can help the model focus on the non-protected attributes and provide insights into how the model's predictions would change if certain attributes were different. Counterfactuals are often used in mitigating bias and evaluating fairness in machine learning models.

### Generating Counterfactual Data Samples

We can generate data samples that modify the words linked with protected attributes using various techniques such as perturbation, inversion, or interpolation. We can also utilise this mitigation technique in the training or alignment process {cite}`butcher24`.
# Mitigating Bias

[Bias Types](./bias.md) chapter demonstrated possible challenges in identifying bias. Mitigating this harmful bias is a challenging issue due to the complex and sociotechnical nature of model learning development pipelines. In this process, developers aim to develop a model with prediction or generation capabilities using a vast amount of data. This model eventually produces false predictions or unexpected outputs. Due to this unexpected behaviours, some individuals from disadvantaged/protected groups are harmed more. The aim of mitigating bias is to minimise this as much as possible by establishing an active human-in-the-loop approach to identify mis-represented individuals better.

## Data Balancing and Augmentation

Data balancing techniques can be used to mitigate bias in machine learning models. These techniques aim to address the imbalance in the distribution of different classes or groups within the dataset. We can randomly remove samples from the majority class or synthesize more data for minority class to increase their representation in the dataset. These methods simply aim to assign balanced weights to the minority and majority classes to achieve a more balanced representation considering the selected fairness notions. In this section, we mainly focus on counterfactuals and balancing data by generating new counterfactual samples.

### Counterfactuals

Counterfactuals are hypothetical scenarios or instances that represent alternative outcomes or observations that could have occurred under different conditions. In the context of machine learning and fairness, counterfactuals are used to generate new data samples by modifying the protected attributes while keeping the remaining attributes unchanged. These modified samples can help the model focus on the non-protected attributes and provide insights into how the model's predictions would change if certain attributes were different. Counterfactuals are often used in mitigating bias and evaluating fairness in machine learning models.

### Generating Counterfactual Data Samples

We can generate data samples that modify the words linked with protected attributes using various techniques such as perturbation, inversion, or interpolation. We can also utilise this mitigation technique in the training or alignment process {cite}`butcher24`.
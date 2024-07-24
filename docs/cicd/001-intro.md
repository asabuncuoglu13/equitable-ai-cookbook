# Continuous Delivery of Safe AI

![](../media/systemdesign.png)

The above diagram illustrates a simplified ML development pipeline. A typical pipeline consists of multiple branches with iterative processes, involving multiple contributors. Different forms of bias types can occur in each step. 

Defining fairness-aware CI/CD type flows that can automate building multiple artefacts for different teams can support building a common understanding in bias mitigation for organisations. In this notebook, we demonstrate potential approaches to monitor ML pipelines throughout the development lifecycle.

## Maintaining a Healthy Codebase

The key requirement to monitor the potential fairness (or security, privacy, etc.) issues is maintaining a clean and maintainable code. There are many great books about maintaining a healthy codebase, so I will not go into details here. You can also quickly check [NCSC's guidance](https://www.ncsc.gov.uk/collection/developers-collection/principles/produce-clean-maintainable-code) to self-assess your knowledge before adding the recommended books into your basket!

```{admonition} Recommended books:

- Structure and Interpretation of Computer Programs (SICP) by Ableton, Sussman, Sussman
- The Pragmatic Programmer by David Thomas, Andrew Hunt
- Architecture Patterns with Python: Enabling Test-Driven Development, Domain-Driven Design, and Event-Driven Microservices by Bob Gregory and Harry Percival
```

## CI/CD: Continuous Integration and Delivery

Once you have a clean codebase, you can also automate the parts where you test your code against adversarial scenarios and build releases. It is commonly known as continuous integration and continuous delivery (CI/CD). Based on your needs, integration and delivery parts can be automated via different libraries, and you can maintain the overall pipeline through tools provided by Github.

```{admonition} Check these examples:

- A Good Example of a Complete RAG Application: https://github.com/octodemo/contoso-chat-dhanachavan
- Example Actions: https://github.com/microsoft/security-devops-action

```

## Using Tools for Experiment Tracking

You can use tools like [wandb](https://wandb.ai/site) and [mlflow](https://mlflow.org/) to keep records of your ML experiments. Both platforms are open-source and allow you to register your models and experiments for easy maintainability.

If you are using these libraries, you are already familiar with FAID's logging behaviour.

```python

import random
import wandb
import mlflow
from faid import faidlog

project = "test-project"
config = {
    "learning_rate": 0.02,
    "architecture": "BERT",
    "dataset": "data/processed/financial-phrasebank.csv",
    "epochs": 10,
}

```

You first initialise the project with the name and config details. These functions basically creates the metadata for the experiment. 

```python
run = wandb.init(project= project, config= config)
```

```python
mlflow.set_experiment(project)
```

```python
faidlog.init(project_name= project, config= config)
```

You need to create an MLFlow session if you want to log the parameters automatically. Alternatively, you can log the parameters manually.

```python
with mlflow.start_run():
```

Then, you can log whatever metric you want to store and monitor using these libraries.

```python
# Log the hyperparameters
# simulate training
epochs = 10
offset = random.random() / 5
for epoch in range(2, epochs):
    acc = 1 - 2 ** -epoch - random.random() / epoch - offset
    loss = 2 ** -epoch + random.random() / epoch + offset

    # log metrics to wandb
    metrics = {"acc": acc, "loss": loss}
```

```python
wandb.log(metrics)
```

```python
mlflow.log_params(metrics)
```

```python
faidlog.log(metrics)
```

## Why Do You Need a Separate Logging Library for Fairness?

When experimenting with data and models, you generate a large amount of information. However, not all of this information is relevant to fairness. Fairness researchers require a specific set of data points and metrics to assess and ensure fairness throughout the machine learning pipeline. Extracting and providing this specific information can become an additional burden for ML engineers, who may already be managing numerous tasks.

A dedicated logging library for fairness can streamline this process. By proactively defining fairness requirements and automatically monitoring the parameters related to these requirements, we can:

1. **Reduce Workload**: Automate the extraction and logging of relevant fairness metrics, freeing ML engineers from the manual task of selecting and providing this information.
2. **Minimize Errors**: Decrease the likelihood of mistakes that can occur with manual data handling and reporting.
3. **Ensure Consistency**: Maintain a standardized approach to logging fairness-related data, which can enhance the reliability and comparability of fairness assessments.
4. **Enhance Focus**: Allow fairness researchers to concentrate on analyzing the relevant data without the distraction of unrelated information.

## Using FAID with [CMF](https://hewlettpackard.github.io/cmf/) and [DVC](https://dvc.org/)

The design principles of our metadata management shares the similar design decisions with CMF. While developing our tool, we also checked the compatability of using the tool together with CMF and DVC to allow version control throughout the fairness research lifecycle.


## Opening Data and Models

Creating an open-source ML repository demands additional requirements to responsibly release the outputs. Model Openness Framework defines three layers while assessing openness and completeness of AI development artifacts. 

- [ ] Open Model layer includes model architecture, model parameters, technical report, evaluation results, model card, data card and sample model outputs.
- [ ] Open Tooling layer includes the codes of training, inference, evaluation, data used for evaluation, supporting libraries and tools, and all components from Open Model layer.
- [ ] Open Science layer includes research paper, all datasets, data pre-processing code, model parameters, model metadata, and all components of Open Tooling layer.

Delivering all these artifacts continuously in a transparent way requires a good carefully designed comprehensive orchestration flow.


## Useful Readings

1. [How To Organize Continuous Delivery of ML/AI Systems: a 10-Stage Maturity Model](https://outerbounds.com/blog/continuous-delivery-of-ml-ai/)
2. [Examples from Neptune AI](https://neptune.ai/blog/build-mlops-pipelines-with-github-actions-guide)
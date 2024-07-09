# Continuous Delivery of Safe AI

![](../media/systemdesign.png)


Model Openness Framework defines three layers while assessing openness and completeness of AI development artifacts. 

Open Model layer includes model architecture, model parameters, technical report, evaluation results, model card, data card and sample model outputs.

Open Tooling layer includes the codes of training, inference, evaluation, data used for evaluation, supporting libraries and tools, and all components from Open Model layer.

Open Science layer includes research paper, all datasets, data pre-processing code, model parameters, model metadata, and all components of Open Tooling layer.

Delivering all these artifacts continuously in a transparent way requires a good carefully designed comprehensive orchestration flow.

## Using Github

Plan > Develop > Secure > Automate

Automate review > CodeQL (Can we develop an action that can check against fairness issues?)

A Good Example of a Complete RAG Application

https://github.com/octodemo/contoso-chat-dhanachavan

Example Actions:

https://github.com/microsoft/security-devops-action


# Using [CMF](https://hewlettpackard.github.io/cmf/) and [DVC](https://dvc.org/)

CMF: 



## Useful Readings

1. [How To Organize Continuous Delivery of ML/AI Systems: a 10-Stage Maturity Model](https://outerbounds.com/blog/continuous-delivery-of-ml-ai/)
2. [Examples from Neptune AI](https://neptune.ai/blog/build-mlops-pipelines-with-github-actions-guide)
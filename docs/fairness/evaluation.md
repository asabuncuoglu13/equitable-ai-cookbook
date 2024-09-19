# Evaluating Bias

:::{note}
See our paper: 
:::

In the development of LLMs and other machine learning (ML) models, researchers and developers focus on defining fairness in social and technical terms and measuring it mathematically. However, when it comes to LLMs, many institutions are still exploring whether assessing fairness in natural language outputs differs from other types of models and if this task is inherently more complex. 

In this notebook, we report some practical applications for bias evaluation by following an example bias evaluation of FinBERT model. Here, we follow a three-step bias evaluation approach to understand and reduce bias gradually. We demonstrate the approach to improving the fairness of FinBERT. The first step of evaluation is to check the behaviour of the model against prompts related to countries from \textit{Global South} (GS) and \textit{Global North} (GN). We created a synthetic dataset to test the FinBERT's classification accuracy when the prompt explicitly reveals country information. Next, we monitored the performance on Indian financial news to check if the model performance is consistent when the data source includes different technical jargon, currency and other implicit bias sources.  Finally, we run interpretability methods such as LIME and saliency maps to see the word-level impact in individual level. We release the dataset and model open source on GitHub. 
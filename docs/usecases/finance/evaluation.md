# Evaluating Bias

:::{note}
See the experiment notebooks:
:::

In the development of LLMs and other machine learning (ML) models, researchers and developers focus on defining fairness in social and technical terms and measuring it mathematically. However, when it comes to LLMs, many institutions are still exploring whether assessing fairness in natural language outputs differs from other types of models and if this task is inherently more complex. 

In this document, we report some practical applications for bias evaluation by following an example bias evaluation of FinBERT model. Here, we follow a three-step bias evaluation approach to understand and reduce bias gradually. We demonstrate the approach to improving the fairness of FinBERT. The first step of evaluation is to check the behaviour of the model against prompts related to countries from \textit{Global South} (GS) and \textit{Global North} (GN). We created a synthetic dataset to test the FinBERT's classification accuracy when the prompt explicitly reveals country information. Next, we monitored the performance on Indian financial news to check if the model performance is consistent when the data source includes different technical jargon, currency and other implicit bias sources.  Finally, we run interpretability methods such as LIME and saliency maps to see the word-level impact in individual level. We release the dataset and model open source on GitHub. 

## Bias in Finance LLMs

Bias encompasses a broad and complex spectrum of factors. The first challenge is generalisable to a wide variety of machine learning models. Within an algorithmic system, bias plays a necessary role in pattern recognition. However, throughout learning these patterns, the system can amplify bias while trying to increase the overall accuracy. Ideally, in LLM-powered systems, we aim for non-discrimination against specific groups while avoiding positive discrimination that could compromise model accuracy. Achieving this balance requires a delicate balance.

The second challenge is specific to financial models (but it is also shared with other domains). While various datasets exist for testing general-purpose LLMs against discrimination, the domain lacks datasets to assess LLMs tailored for financial services. Since there is no shared widely-used dataset to evaluate against discrimination, this assessment is constrained by the sociotechnical skills of financial organizations.

Further, bias in finance can also refer to various meanings. We listed some well-known bias types in financial-decision making. Despite all efforts shown to reduce bias in financial data and algorithm, an LLM still can suffer the following biases like a typical financial decision-maker. In the fair development process, we would like to prevent LLMs to demonstrating these behaviour or unconciously promoting this kind of behavior for a human decision-maker.

1. Confirmation bias: Favoring information that confirms existing beliefs.
2. Overconfidence bias: Overestimating one's own abilities or the accuracy of information.
3. Anchoring bias: Relying too heavily on the first piece of information encountered.
4. Loss aversion bias: Preferring to avoid losses over acquiring equivalent gains.
5. Availability bias: Judging the likelihood of an event based on how easily instances come to mind.
6. Herding bias: Following the actions of a crowd without considering personal judgment.
7. Endowment bias: Overvaluing what one already possesses compared to equivalent alternatives.
8. Framing bias: Making decisions based on how information is presented rather than its substance.
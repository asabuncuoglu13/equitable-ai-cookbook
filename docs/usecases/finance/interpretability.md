# Interpretability tools for improving fairness and equity

Explainable and interpretable AI fields have a long history of developing tools to better explain the models to improve robustness and reliability in the decision making process. We can also use the existing tools for improving fairness of the overall system. In this article, we discuss how we can use recently developed Language Interpretability Tool (LIT) for improving fairness in NLP-powered systems and how different stakeholders can communicate and interpret the findings of this tool. 

## Language Interpretability Tool (LIT)

LIT is an open-source tool developed by Google Research to help practitioners understand and interpret the behavior of their language models. It provides a set of interactive visualisations and methods to explore and analyze models in a production setting. The tool offers: **(1) Interactive visualization**: of model outputs to grasp how different parts of a model contribute to its overall behavior. **(2) Support for multiple models**: allows users to compare the performance and behavior of different models side-by-side. **(3) Interpretability methods**, such as feature importance, saliency maps, and counterfactuals are integrated.

## Use Case: Use LIT for Interpreting Financial Sentiment Analysis Model

A practitioner can use LIT to compare different sentiment analysis models (e.g., FinBERT, FinMA) to determine which model best captures financial sentiment from news articles, social media, or other sources. For example, we can use saliency maps to identify which words or phrases in a financial document contribute most to the model's sentiment prediction. For example, understanding why certain terms like "profit warning" or "strong earnings" lead to positive or negative sentiment predictions. Or, by altering specific words or phrases (counterfactual inputs), the practitioner can observe how changes affect the model's sentiment prediction. This can help in understanding the model's sensitivity to different types of financial language.

LIT can also allow practitioners to drill down into instances where the model misclassifies sentiment, helping to identify common patterns in these errors. For instance, a model might struggle with sarcastic comments or mixed sentiment in financial discussions, which can be critical for accurate market predictions. Further, practitioners can repeatedly test and refine models based on feedback from the tool, ensuring that the final sentiment signal is robust and accurate.

### Improving the Fairness of FinBERT

#TODO: Add screenshots and notebook samples for each item.

We can use LIT to analyze how the model’s sentiment predictions might be biased towards certain types of financial news or language. For example, if the model consistently rates news from certain regions more negatively, this could indicate a regional bias.

1. LIT’s visualization tools can help in identifying whether certain types of companies (e.g., large-cap vs. small-cap) or sectors are systematically receiving more positive or negative sentiment scores. This analysis is critical to uncovering unintended biases.
2. Practitioners can use counterfactual analysis in LIT to test whether changing certain attributes (e.g., replacing the name of a well-known company with a lesser-known one) affects the sentiment score. This helps to identify whether the model is unfairly influenced by factors like company size, reputation, or geography.
3. By interpreting why the model makes certain predictions, practitioners can ensure that the model’s reasoning aligns with fair and ethical principles, avoiding discriminatory outcomes.
4. Practitioners should use LIT to evaluate the model on diverse financial data sets that include different sectors, regions, and company sizes. LIT can help ensure that the model performs equally well across these diverse contexts, which is essential for fairness.
5. LIT allows practitioners to examine model performance across different subgroups (e.g., technology vs. manufacturing sectors). This helps in ensuring that the model does not favor or disadvantage any particular subgroup.
6. LIT supports an iterative workflow where practitioners can continuously monitor and adjust the model to address any fairness concerns that arise during testing. Regular audits using LIT ensure that fairness remains a focus throughout the model's lifecycle.
7. If we can reveal disparities in how the model treats different types of financial entities, we can adjust the training data, model architecture, or post-processing techniques to reduce these disparities.

## Stakeholder Collaboration for Fairness

This kind of interpretability and fairness tools produce a variety of outputs that requires collaboration among various stakeholders. Here we listed the roles of different stakeholders to achieve effective fairness analysis and mitigation:

#TODO: Add diagram

1. **Data Scientists and Machine Learning Practitioners** Analyse, test, and improve the model’s fairness by identifying and addressing biases in the data and model predictions.
2. **Financial Analysts and Domain Experts** Ensure that the model’s outputs align with real-world financial contexts and do not unintentionally favor certain market conditions or entities.
3. **Ethicists and Fairness Experts** Define what fairness means in the context of financial sentiment analysis and ensure that the system aligns with broader ethical principles.
4. **Regulatory and Compliance Teams** Ensure that the financial sentiment system complies with relevant regulations and guidelines, particularly those related to fairness and non-discrimination in financial markets.
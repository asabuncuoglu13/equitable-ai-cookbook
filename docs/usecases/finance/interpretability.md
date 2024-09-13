# Interpretability tools for improving fairness and equity

Explainable and interpretable AI fields have a long history of developing tools to better explain the models to improve robustness and reliability in the decision making process. We can also use the existing tools for improving fairness of the overall system. 

Deck et al.'s recent survey identifies seven archetypal claims about the relationship between Explainable AI (XAI) and fairness {cite}`deck_critical_2024`:

1. XAI helps achieve (a generic notion of) fairness *(without specifying what kind of fairness is meant.)*
2. XAI enables humans to report on (formal) fairness *(often by analyzing how sensitive features influence model decisions.)*
3. XAI enables humans to analyze sources of (formal) unfairness *(to identify the factors or data points that contribute to unfair outcomes.)*
4. XAI enables humans to mitigate (formal) unfairness *(to reduce unfairness through interventions like retraining models or adjusting features.)*
5. XAI informs human judgment of fairness *(aids stakeholders in assessing whether AI systems are fair based on the explanations provided.)*
6. XAI improves human perceptions of fairness *(to enhance users' trust and confidence in the fairness of AI systems.)*
7. XAI enables humans to implement subjective notions of fairness, *(allows stakeholders to incorporate their personal or context-specific fairness criteria into AI systems.)*

**Limitations of using XAI tools to improve fairness:** It is important to note that understanding AI's inner workings can be an essential mechanism for ensuring fairness, however even transparent algorithms can still produce unfair outcomes. XAI methods can detect bias by analyzing feature importance, however current XAI tools often lack the necessary capabilities to reliably identify bias. These methods can also result in the risk of oversimplifying the underlying causes of unfairness. Further, developers might intentionally deceive vulnerable stakeholders, such as auditors or decision subjects, by creating misleading interfaces or explanations, for example, using adversarial attacks on explanation methods {cite}`chromik2019dark`.

Ehsan et al.'s sociotechnical XAI framework {cite}`ehsan_charting_2023` uses **trust**, **actionability**, and **values** as the three main components of social aspects in the explainability. **Trust component asks:** Where does trust breakdown in the AI system? Why? How might we re-calibrate trust (if needed)? How can we identify the AI’s blind spots and address them? **Actionability component asks:** What are barriers preventing informed actionability? What do users need to boost decision-making confidence? How can we empower users to confidently contest the AI? **And the values component asks:** How are values in tension & alignment amongst stakeholders? How is accountability distributed in the Human-AI tasks? What are organizational priorities around ethics? Together, the answers to these questions can bridge the gap between social and technical development of explainability component. 

In this article, we start with some technical approaches to explain and interpret the outputs of financial language models. We discuss how we can use recently developed local explanation techniques and Language Interpretability Tool (LIT) for improving fairness in NLP-powered systems. Then, we discuss the social aspects of interpretability and how we can involve different stakeholders to communicate and interpret the findings of this tool.

## Explanation Methods (Background)

Liao et al. categorises explainability methods under four categories {cite}`liao2020questioning`:

1. We can explain the global model behaviour by,
   - **Global feature importance**: Describes the weights of features used by the model.
   - **Decision tree approximation**: Approximates the model to an interpretable decision-tree.
   - **Rule extraction**: Approximates the model to a set of rules (e.g., if-then rules).
2. Or, we can create local explanations by using **local feature importance** and **saliency methods** and describe the rules that the instance fits to guarantee the prediction.
3. Another approach is innspecting counterfactuals:
    - **Feature influence or relevance method**: Shows how the prediction changes corresponding to changes in a feature.
    - **Contrastive or counterfactual features**: Describes features that will change the prediction if perturbed, absent, or present.
4. Finally, we can use example-based approaches:
   - **Prototypical or representative examples**: Provides examples similar to the instance with the same prediction.
   - **Counterfactual example**: Provides examples with small differences from the instance but with a different prediction.

In this article, we focus on local explanations, saliency methods and example-based approaches. Then, we use Language Interpretability Tool (LIT) to interpret these outputs in one single interface.

## Local Explanations to Interpret Global Behaviour

```{note}
- See the use of LIME: https://github.com/asabuncuoglu13/faid-test-financial-sentiment-analysis/notebooks/lime-finbert.ipynb
- See the use of Integrated Gradients: https://github.com/asabuncuoglu13/faid-test-financial-sentiment-analysis/notebooks/FinBERT-demo.ipynb
```

## Language Interpretability Tool (LIT)

```{note}
See the use of LIT with custom FinBERT model: https://github.com/asabuncuoglu13/faid-test-financial-sentiment-analysis/notebooks/demo-lit-nlp.ipynb
```

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

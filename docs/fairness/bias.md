# Common Bias Types in ML Pipeline (and some solutions)

Bias, in technical terms, means deviation from the "standard", and it is essential to find the patterns in the data to power classification and generation algorithms. And, to assess "problematic" bias in algorithm, we should assess the complete development process (modelling, training and usage) from a cross-disciplinary perspective {cite}`ferrer_bias_2021`. 

![Bias types in ML Pipeline](../media/systemdesign.png)

Here, we summarised potential bias sources and types found in data, algorithmic design, and human use:

## Bias in the Data

### Measurement Bias

This bias stems from errors or inconsistencies in how data is collected, measured, or stored. While measurement bias can affect data generally, it may disproportionately impact certain groups. For example, if data collection practices are less rigorous in one area compared to another, it can introduce bias.

### Bias in the Tail

When we train our models using large datasets, there is a risk of prioritizing accuracy/fairness on the data-rich head of the distribution. In this case, we forgot the tail of the distribution, which can potentially have a large impact in the bias.

#### Proposed Solutions from the Literature

- **Adversarial Filters of Dataset Biases** `cite`{bras_adversarial_2020}: *"bottom-up approach to algorithmic bias reduction".... AFLITE seeks to minimize the ability of a model to exploit biases in the head of the distribution, while preserving the inherent complexity of the tail.*

### Historical Bias

This bias arises from past societal inequalities or prejudices reflected in historical data. For example, if residents in a specific area historically experienced higher loan default rates, an algorithm trained on this data might unfairly penalize loan applicants from that area. This bias can be perpetuated in a feedback loop, where biased outcomes further reinforce the bias in subsequent data iterations. Addressing historical bias requires not only debiasing techniques but also critical examination of the data sources (distribution) and the societal context (contacting with all stakeholders) in which they were generated.

### Representation/Sample Bias

Even after reducing the impact of historical bias, representation bias can occur when the data is misaligned with the real-life state. This bias occurs when the data used to train an AI is not representative of the population it's meant to serve.  For instance, an insurance algorithm trained on a dataset primarily composed of claimants from a particular region might inappropriately inflate premiums for individuals from that area. Another example is when a facial recognition system is primarily trained on images of light-skinned individuals, it may perform poorly on darker-skinned individuals. Ensuring diverse and representative training data is crucial for reducing this type of bias. So, it is essential to ask which communities will be affected after deploying our solution.

### Intersectional/Proxy Bias

Proxy bias occurs when seemingly neutral variables used in an algorithm correlate with sensitive attributes. Even when protected characteristics are excluded from the data, using proxy variables like geographic location, which might be correlated with ethnicity, can lead to discriminatory outcomes. Intersectional bias refers to the compounded disadvantage that individuals may face when they belong to multiple marginalized groups. For example, an algorithm might be biased against women of color in a way that is not evident when examining gender or race in isolation. Addressing intersectional bias requires a nuanced approach that considers the interactions between multiple protected attributes.

### Emergent Bias

This bias arises after an algorithm is deployed due to shifts in societal values, knowledge, or population dynamics. The COVID-19 pandemic provides a relevant example. Algorithms relying on income data must now account for factors like furlough payments, while insurance algorithms need to adapt to changing risk profiles associated with different occupations. Failing to adjust for these emergent biases can lead to unfair outcomes, potentially favoring those least impacted by societal changes. 

### Bias in Data Labeling

Bias can be introduced during the data labeling process, where human annotators may bring their own prejudices and biases into the labels they assign. This is particularly problematic in tasks requiring subjective judgments, such as sentiment analysis or facial emotion recognition. Ensuring diverse and unbiased labeling practices, along with regular audits, can help mitigate this issue.

### Bias in Feature Selection

Bias can also be introduced during the feature selection process, where certain features might be chosen or discarded in a way that introduces or exacerbates bias. This can be intentional or unintentional. For example, excluding features that are correlated with protected attributes might reduce apparent bias but also remove valuable context that could lead to better decision-making. Transparent and careful feature selection processes are necessary to balance fairness and performance.


### Feedback Loop Bias

Feedback loop bias happens when the output of a biased model influences the future data that is collected, creating a cycle of increasing bias. For example, if a predictive policing algorithm disproportionately targets certain neighborhoods based on biased historical data, it will lead to more arrests in those areas, further reinforcing the initial bias. Breaking this cycle requires intervention strategies that monitor and adjust for bias continuously.


## Bias in the Algorithmic Design

### Objective Bias

This bias stems from the algorithm's primary goal. An algorithm focused on maximizing the overall accuracy of credit default predictions might achieve high overall accuracy but still exhibit bias by being more accurate for certain groups, disadvantaging others.

### Evaluation Bias

Evaluation bias arises when the metrics and benchmarks used to assess model performance do not adequately capture fairness or bias. Standard accuracy metrics might not reflect disparate impacts on different demographic groups. Consequently, models might appear to perform well overall while still being biased. Developing and using fairness-aware evaluation metrics is essential to identify and mitigate this issue.

### Weighting Bias

In algorithms, different features are assigned weights to indicate their importance in predicting the outcome. If these weights are not carefully calibrated, it can introduce bias. For example, an auto insurance algorithm that heavily weights credit scores over driving records might result in customers with good credit scores but poor driving records paying less than those with excellent driving records but lower credit scores, even if their overall risk is statistically similar.

### Algorithmic Transparency and Interpretability

A major challenge in addressing bias is the lack of transparency and interpretability in many machine learning models, especially complex ones like deep learning networks. Without understanding how decisions are made, it is difficult to identify and correct sources of bias. Developing methods for explaining model decisions and making algorithms more interpretable can help stakeholders trust and verify the fairness of the models.

## Bias in Human Use

As AI systems often learn from data labeled or generated by humans, they can inherit and amplify existing conscious or unconscious biases. If an algorithm learns from insurance underwriters' decisions, it might perpetuate those underwriters' biases, regardless of whether they are intentional. We further addresses these challenges in our finance use case: [Human-System Interaction View on Fairness](../usecases/finance/interaction.md)

# Useful Resources
- Bias and Discrimination in AI: A Cross-Disciplinary Perspective {cite}`ferrer_bias_2021`
- [KPMG, Algorithmic Bias and Financial Services: A Report prepared for Finastra International](https://www.finastra.com/sites/default/files/documents/2021/03/market-insight_algorithmic-bias-financial-services.pdf)
- See Bias in AI Course by the Alan Turing Institute: https://github.com/alan-turing-institute/bias-in-AI-course/tree/main
- See Bias and Mitigation Card by the Turing Commons: https://github.com/alan-turing-institute/turing-commons/blob/resources/resources/activities/bias-and-mitigation-cards.pdf


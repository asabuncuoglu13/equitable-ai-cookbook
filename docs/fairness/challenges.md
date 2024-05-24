# Fairness Challenges (and some solutions)

Bias, in technical terms, means deviation from the "standard", and it is essential to find the patterns in the data to power classification and generation algorithms. And, to assess "problematic" bias in algorithm, we should assess the complete development process (modelling, training and usage) from a cross-disciplinary perspective {cite}`ferrer_bias_2021`. 

## Challenge 1: Unintended Bias

The characteristics of protected attributes (such as race or gender) are often indirectly encoded in other data features. This means that even if an algorithm does not explicitly use these protected attributes, it can still exhibit bias. For example, data points like a person's name, address, or educational background might indirectly reveal their race or socioeconomic status, making it difficult to measure and address bias directly.

### Proposed Solutions from the Literature


## Challenge 2: Bias in the Tail

When we train our models using large datasets, there is a risk of prioritizing accuracy/fairness on the data-rich head of the distribution. In this case, we forgot the tail of the distribution, which can potentially have a large impact in the bias.

### Proposed Solutions from the Literature

- **Adversarial Filters of Dataset Biases** `cite`{bras_adversarial_2020}: *"bottom-up approach to algorithmic bias reduction".... AFLITE seeks to minimize the ability of a model to exploit biases in the head of the distribution, while preserving the inherent complexity of the tail.*

## Challenge 3: Historical Bias

Historical bias arises when the data used to train machine learning models reflects past discrimination or prejudice. This is often the case with historical data, where social and institutional biases have influenced the recorded information. As a result, models trained on such data can perpetuate and even exacerbate existing biases, leading to unfair outcomes. Addressing historical bias requires not only debiasing techniques but also critical examination of the data sources (distribution) and the societal context (contacting with all stakeholders) in which they were generated.

### Proposed Solutions from the Literature

- 

## Challenge 4: Representation Bias

Even after reducing the impact of historical bias, representation bias can occur when the data is misaligned with the real-life state. This can happen due to under-sampling of minority groups or over-reliance on data from specific demographics. For example, if a facial recognition system is primarily trained on images of light-skinned individuals, it may perform poorly on darker-skinned individuals. Ensuring diverse and representative training data is crucial for reducing this type of bias. So, it is essential to ask which communities will be affected after deploying our solution.

### Proposed Solutions from the Literature

- 


## Challenge 5: Feedback Loop Bias

Feedback loop bias happens when the output of a biased model influences the future data that is collected, creating a cycle of increasing bias. For example, if a predictive policing algorithm disproportionately targets certain neighborhoods based on biased historical data, it will lead to more arrests in those areas, further reinforcing the initial bias. Breaking this cycle requires intervention strategies that monitor and adjust for bias continuously.



## Challenge 6: Evaluation Bias

Evaluation bias arises when the metrics and benchmarks used to assess model performance do not adequately capture fairness or bias. Standard accuracy metrics might not reflect disparate impacts on different demographic groups. Consequently, models might appear to perform well overall while still being biased. Developing and using fairness-aware evaluation metrics is essential to identify and mitigate this issue.


## Challenge 7: Bias in Feature Selection

Bias can also be introduced during the feature selection process, where certain features might be chosen or discarded in a way that introduces or exacerbates bias. This can be intentional or unintentional. For example, excluding features that are correlated with protected attributes might reduce apparent bias but also remove valuable context that could lead to better decision-making. Transparent and careful feature selection processes are necessary to balance fairness and performance.


## Challenge 8: Algorithmic Transparency and Interpretability

A major challenge in addressing bias is the lack of transparency and interpretability in many machine learning models, especially complex ones like deep learning networks. Without understanding how decisions are made, it is difficult to identify and correct sources of bias. Developing methods for explaining model decisions and making algorithms more interpretable can help stakeholders trust and verify the fairness of the models.


## Challenge 9: Bias in Data Labeling

Bias can be introduced during the data labeling process, where human annotators may bring their own prejudices and biases into the labels they assign. This is particularly problematic in tasks requiring subjective judgments, such as sentiment analysis or facial emotion recognition. Ensuring diverse and unbiased labeling practices, along with regular audits, can help mitigate this issue.


## Challenge 10: Intersectional Bias

Intersectional bias refers to the compounded disadvantage that individuals may face when they belong to multiple marginalized groups. For example, an algorithm might be biased against women of color in a way that is not evident when examining gender or race in isolation. Addressing intersectional bias requires a nuanced approach that considers the interactions between multiple protected attributes.

These challenges highlight the complexity of addressing bias in machine learning and underscore the importance of comprehensive strategies that tackle bias at various stages of the model development and deployment process.

# Useful Resources
- Bias and Discrimination in AI: A Cross-Disciplinary Perspective {cite}`ferrer_bias_2021`
- See Bias in AI Course by the Alan Turing Institute: https://github.com/alan-turing-institute/bias-in-AI-course/tree/main
- See Bias and Mitigation Card by the Turing Commons: https://github.com/alan-turing-institute/turing-commons/blob/resources/resources/activities/bias-and-mitigation-cards.pdf


# Understanding Fairness Notions in Data-Driven Decision Making

Fairness in data-driven decision-making has emerged as a critical concern to ensure equitable outcomes for different social groups. These notions can be broadly categorized into group fairness and individual fairness, each addressing different dimensions of fairness. **Group fairness**, also known as "statistical fairness", focuses on treating different social groups equally. **Individual fairness** advocates for similar treatment for similar individuals. 

## Group Fairness

The key objective of group fairness is satisfying the independence by ensuring sensitive characteristics are independent of the prediction results. It seeks to provide statistically fair guarantees for groups defined by sensitive attributes like race or education level.  These fairness notions aim to prevent biases against specific groups, promoting equal treatment in decision-making processes. Four commonly used group fairness notions are:

1.	Statistical parity (or equalised odds) {cite}`zemel_13, hardt_equality_2016` demands equal prediction rates across groups defined by sensitive attributes such as race or gender. It ensures that individuals from different social groups receive equal treatment in the decision-making process, regardless of their background.
    
    In a binary classification problem, where each sample point is represented by a given feature set X, binary sensitive feature A, true outcome Y, and predictions ˆ𝑌, we can define statistical parity formally as:

    $$
    P(\hat{Y} | A = 0) = P(\hat{Y} | A = 1)
    $$

    We will use the same notations for the rest of this article.

2.	Equal opportunity, another group fairness metric, focuses on ensuring that individuals from different demographic groups have an equal chance of positive outcomes (true positives), such as being hired for a job or receiving a loan {cite}`hardt_equality_2016`.

    $$
    P(\hat{Y} = 1|Y = 1, A = 0) = P(\hat{Y} = 1|Y = 1, A = 1)
    $$

3.	Predictive equality seeks the predicted outcomes are balanced across different demographic groups by measuring false positive rates {cite}`hardt_equality_2016`.
    
    $$
    P(\hat{Y} = 0 | A = 0) = P(\hat{Y} = 0 | A = 0)
    $$

4.	Calibration, a key aspect of group fairness, focuses on ensuring that the predicted probabilities align with the true probabilities of positive outcomes for different demographic groups. Calibration within groups means having equal true positive probability for the same predicted score (\(S=s\)) irrespective of the sensitive feature {cite}`kleinberg_inherent_2016`.

    $$
    P(Y = 1|S = s, A = 0) = P(Y = 1|S = s, A = 1) \quad \forall s \in [0, 1]
    $$

## Individual Fairness

Individual fairness can be seen as fine-grained fairness by demanding comparable predictions for individuals with similar characteristics. The motivation behind individual fairness is to avoid favouring less qualified individuals over more qualified ones. Examples of individual fairness notions include causal discrimination, fairness through awareness, counterfactual fairness, and no unresolved discrimination. These notions strive to ensure fairness at an individual level, promoting equal opportunities for all individuals regardless of their background.

1.	Fairness through awareness advocates for fairness by incorporating awareness of sensitive attributes into the decision-making process. It acknowledges the impact of factors like race or gender on outcomes and seeks to mitigate biases by explicitly considering these attributes {cite}`dwork_fairness_2012`.
    
    $$
    D(P(X_i), P(X_j)) \leq d(X_i, X_j)
    $$

    This equation represents a fairness criterion where the distance between the probability distributions $P(X_i)$ and $P(X_j)$ is less than or equal to the similarity distance between the individuals $X_i$ and $X_j$. It reflects the idea that the difference in predictions should not exceed the similarity between the individuals, ensuring fairness in the decision-making process.

2. Causal discrimination demands that individuals with similar characteristics or qualifications receive comparable treatment in decision-making processes {cite}`galhotra_fairness_2017`. For example, an algorithm is fair with respect to "sensitive attributes" if for all pairs of individuals with the same features other than these sensitive attributes.

    $$
    P(\hat{Y} = 1 | \text{similar}(X_i, X_j)) = P(\hat{Y} = 1 | \text{similar}(X_i, X_j), A = 0)
    $$

3.	Counterfactual fairness aims to ensure that individuals would receive the same outcome regardless of their sensitive attributes, had their attributes been different. It considers counterfactual scenarios where individuals' attributes are changed while keeping other factors constant.
    
    $$
    P(\hat{Y}(i, d) = y | A = a) = P(\hat{Y}(j, d) = y | A = a)
    $$
    
    Where:
    - $\hat{Y}(i, d)$ represents the predicted outcome for individual $i$ under counterfactual scenario $d$.
    - $y$ denotes the predicted outcome.
    - $A$ denotes the sensitive attribute.
    - $a$ denotes the value of the sensitive attribute.
    - $i$ and $j$ represent individuals.
    - $d$ represents the counterfactual scenario.

The mathematical implementation of fairness notions varies and can target different stages of the decision-making process. This includes correcting input data, exploring feasible solution spaces, representing features graphically, or leveraging fair representation learning techniques. However, combining multiple fairness notions can present challenges, such as inadvertently treating individuals unfairly despite satisfying group fairness or facing mathematical limitations in simultaneously satisfying multiple fairness criteria.

Addressing fairness mathematically has raised concerns about the trade-offs between accuracy and fairness. While efforts have been made to optimize both, there remains a need to ensure fairness from a societal perspective. This entails aligning the metrics used to measure fairness with societal values and operationalizing fairness in a way that reflects real-world equity concerns.

## Counterfactual Explanations for Fairness and Privacy

Utilising counterfactual explanations can also improve privacy in the model development process, while providing a satisfying level of explainability to the users. Wachter et al. explores this concept to *"bridge the gap between the interests of data subjects and data controllers"* {cite}`wachter_counterfactual_2017`. 

An example counterfactual explanation:

"Your loan application is denied, because your annual income is lower than £40,000. If your annual income had been £65,000, your loan could be approved."

Providing these explanations can help both fairness researchers and end users to understand the model without interfering the privacy constraints.


In conclusion, understanding and implementing fairness notions in data-driven decision-making processes is essential for promoting equity and mitigating biases. By incorporating both group and individual fairness considerations, alongside addressing implementation challenges, we can strive towards more just and equitable outcomes in algorithmic decision making.

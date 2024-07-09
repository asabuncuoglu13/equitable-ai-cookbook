# Fairness of Large Language Models in Finance

Achieving fairness in AI-powered financial services requires addressing biases and disparities that may inadvertently affect certain demographic groups (protected characteristics). It is suggested to maintain a proactive (“by design” solutions) and iterative (continuous monitoring, evaluation, and development) process to effectively implement fairness strategies throughout the development.

We can define three major stages in a traditional AI development pipeline: (1) Data collection and pre-processing, (2) Algorithm development, training and testing, (3) Evaluation, red-teaming and deployment. Developing a fair AI pipeline begins with the collection of diverse and representative data, ensuring equitable representation across all customer segments. Transparent and explainable ML models play a crucial role, allowing users to understand the reasoning behind decisions and fostering trust in the system. Implementing fairness metrics and conducting regular audits enable proactive identification and mitigation of biases throughout the model's lifecycle. Human oversight remains essential, providing a safeguard against algorithmic biases and ensuring that decisions align with fairness principles.

By combining these bias mitigation strategies, financial institutions can cultivate AI systems that not only detect and prevent discrimination effectively but also uphold accuracy, security and privacy of the overall pipeline. So, in this sense, fairness applications should not be seen as a potential trade-off element that requires an extra effort (and money, and time), but should be organically integrated into the overall flow.

In this exploratory review, we will present an overall view of fairness in financial services and their practical implications in the LLM space. The main goal of this article is to help practitioners grasp fundamental concepts of fairness and implement some of the best practices in their application domain.

# LLMs in Financial Services

LLMs are the subject of significant interest from governments, regulators and many industry sectors, and are heavily featured in both the academic literature and the popular press. This shared interest underpins a thriving market valued at 10.5 billion USD in 2022 and is anticipated to reach 40.8 billion USD by 2029, demonstrating a compound annual growth rate of 21.4% between 2023 and 2029 {cite}`prnewswire_large_2023`.

The finance sector has always been one of the early adopters of cutting-edge technology.  Existing financial services are highly regulated and highly data-driven with machine learning (ML) playing a significant role in many services. A joint Bank of England (BoE) and FCA survey of financial services firms in the United Kingdom (UK) revealed that 72% of respondents use ML applications in their day-to-day applications {cite}`boe_machine_2022`.  The 2023 report of the Financial Policy Committee meeting states that, with the recent advances in LLMs, several financial firms have generated interest in the possibilities of integrating this technology into their services. Some financial companies and service providers to the financial sector have publicly expressed their experimentation with LLMs. However, the report reveals that the current exploration of use cases primarily involves low-risk activities, such as information search and retrieval or generating internal outputs, rather than automating business decisions .

A further 2023 survey from UK Finance, a trade association for the UK banking and financial services sector, revealed that more than 70% of participating financial institutions are in the proof of concept (PoC) stage for generative AI solutions, of which LLMs {cite}`boe_financial_2023`. One significant investment made by financial software and media company Bloomberg, BloombergGPT {cite}`wu_bloomberggpt_2023`,  has produced a 50 billion parameter model that can be utilised for an array of financial tasks such as news analysis and question answering. With such development, understanding the implications of large-language models in financial services advances the opportunity to set best practices for a critical economic sector, and provide examples that may be relevant to other industries.

`````{admonition} Read more at …
:class: tip
You can find more information about impact of LLMs in financial services, you can read our [March 2024 Report]( https://www.turing.ac.uk/news/publications/impact-large-language-models-finance-towards-trustworthy-adoption). I also listed some background reading materials [on Github]( https://github.com/alan-turing-institute/fairness-monitoring/blob/main/docs/READINGS.md).
`````

## Example Applications

### Financial news sentiment analysis

Understanding public sentiment regarding company-specific developments as well as broader economic and political events is a common yet challenging task. In the finance sector, analysts combine a wide range of information sources to build comprehensive company profiles. NLP solutions, such as classification and clustering algorithms, are frequently used to assist with this analysis. Recently, LLMs have been increasingly utilized in this domain. Their advanced memory and context-understanding capabilities significantly enhance the ability to analyse and interpret vast amounts of text-based data, leading to more accurate and insightful assessments.

We can list three main challenges to define and measure fairness in news sentiment analysis:

1. News diversity is a multifaceted concept: Several sources (source diversity), topics (content diversity), and stances (viewpoint diversity) {cite}`alam_towards_2022`
2. The pre-trained LLM carries some bias for each source, topic and stance on a given topic.
3. Human monitoring is also open to bias depending on the socioeconomic and political view

A robust recipe is necessary to overcome these challenges and enable a proactive fairness evaluation. For example, in a news sentiment analysis application, we can define following steps beyond comparing some fairness metrics (Of course, also compare the metrics like FMR and FNMR):

- [Counterfactual inputs] Does the model behaviour change when the source changes? (e.g. Chinese vs German sources)
- [Comparative analysis of demographic parities between topic clusters] How do fairness metrics change in different topic clusters?
- [Interpret the results] And, we also need to answer what does it mean to reduce bias? Bias is an essential component of achieving pattern recognition. So, the model eventually has some bias based on the data. And when we develop a model, this model should also answer some business needs. Any financial services try to increase their profit. But it should also align with the greater good, considering environmental, social and governance (ESG) aspects. 

`````{admonition} Experiment
:class: tip
Analysing BABE dataset (https://huggingface.co/datasets/mediabiasgroup/BABE) with BERT News Sentiment Classification Model (https://huggingface.co/newsmediabias/Bert_Sentiment_Classification) and also a zere-shot classification: https://huggingface.co/sileod/deberta-v3-base-tasksource-nli
`````

### Extended Tabular Analysis

LLMs can also be utilised in more complex tasks such as improving credit scoring applications by bringing multiple knowledge sources together. Although LLMs are not specifically developed for classification based on tabular data, with some tweaks like chain of tables and hierarchical learning mechanisms, they demonstrated some advanced capabilities also for tabular data. 

`````{admonition} Experiment
:class: tip
Use popular bias recognition datasets (Adult, German Credit, COMPAS) in a similar context. Compare fairness notions (and find some baseline fairness studies using these datasets.)
`````

### Stock Movement Prediction

With the increasing flux of financial news and other knowledge source, analysing a complex set of tabular and text data gained importance. Researchers and practitioners explored using deep attentive mechanisms to effectively utilise the blend of chaotic temporal signals {cite}`sawhney_deep_2020`. 

Shi et al. demonstrated that LLMs have the potential to outperform traditional models in sequential event prediction {cite}`shi_language_2023` ([See their open-source repo for more details](https://github.com/iLampard/lamp/tree/main)). 

`````{admonition} Experiment
:class: tip

`````
# Developing a Fair ML Development Pipeline

In the modern era of financial landscape, machine learning (ML) and other quantitative techniques stand as the driving force behind many applications. These technologies are revolutionizing various application areas, from risk assessment and fraud detection to portfolio management and customer service optimization. 

We can list a six-step flow for developing a fairness-aware ML {cite}`das_fairness_2021`:

- **Define a use case with measurable objectives:** Implementing a FAML pipeline is challenging due to variety in the fairness notions and lack of clarity on the prioritisation. While making an algorithm fair for one metric, the algorithm can become unfair on another metric. So, defining a use-case with clear, measurable and atomic objectives is critical.
- **Understand possible sources of bias:** Historical bias in the datasets (in the labelling process), curation bias (selecting/dropping some features), objective functions (removing outliers, focusing specific features), homogenisation (synthetic data can amplify bias), active bias (fake news, satires, jokes), unanticipated machine decisions (a model with a purpose can also show unexpected behaviours). 
- **Measure bias:** As model developers, we have the responsibility of developing models that gives equal opportunity for advantaged and disadvantaged groups. You can define “opportunity” in multiple ways for different use cases. In this article, we focused on binary classification cases to simplify the explanation of these different notions. We explained approaches to measuring and interpreting bias in another article: [Fairness Notions](./notions.md).
- **Analyse pre-training and post-training metrics:** Before training process, it is essential to analyse the class imbalance and differences in the proportions of the representations (e.g. labels in a supervised setting). 
- **Counterfactual analysis:** Flip the protected characteristics in the dataset to test if the model results in same predictive outputs.
- **Updating the model and dataset:** In the iterative and continuous evaluation/development environment, the last step is updating the dataset and model parameters based on the bias analysis findings.


## Understanding the UK Social and Legislative Context

Fairness is an ideal, has been emphasized in various manifestos over time, with its significance expanding to reach more people with an emphasis to “equity”. The UN Universal Declaration of Human Rights (1948) is the most recent and comprehensive expression of this principle. Before and after this document, many of the legal foundations for fairness were established following public demonstrations, civil rights movements, and other events. So, when researchers and practitioners discuss “fairness” in different context, they mostly use definitions and notions established as a result of long history of events.

In finance industry, regulations protect costumers against discriminative actions.

``` **TODO:** Add related regulations from finance sector. ```

The Equality Act 2010 in the UK makes it illegal to discriminate against individuals because of protected characteristics like age, race, and sex. Organisations must adhere to these rules when carrying out their public duties, which also extend to algorithmic decision-making processes. However, a report by the CDEI (now DSIT’s RTAU) after a decade of the Act's implementation showed a significant disparity between policies and their actual implementation. This is mainly due to the fact that the regulations are often open to interpretation, especially in the context of algorithmic processes {cite}`cdei_2020`.

In 2019, the EU High-Level Expert Group on AI proposed the ethics guidelines for “trustworthy” AI. The below excerpt is directly taken from this document to provide a practical checklist for avoiding unfair bias:

```
- Did you establish a strategy or a set of procedures to avoid creating or reinforcing unfair bias in the AI system, both regarding the use of input data as well as for the algorithm design?
    - Did you assess and acknowledge the possible limitations stemming from the composition of the used data sets?
    - Did you consider diversity and representativeness of users in the data? Did you test for specific populations or problematic use cases?
    - Did you research and use available technical tools to improve your understanding of the data, model and performance?
    - Did you put in place processes to test and monitor for potential biases during the development, deployment and use phase of the system?

- Depending on the use case, did you ensure a mechanism that allows others to flag issues related to bias, discrimination or poor performance of the AI system?
    - Did you establish clear steps and ways of communicating on how and to whom such issues can be raised?
    - Did you consider others, potentially indirectly affected by the AI system, in addition to the (end)-users?
    - Did you assess whether there is any possible decision variability that can occur under the same conditions?
    - If so, did you consider what the possible causes of this could be?
    - In case of variability, did you establish a measurement or assessment mechanism of the potential impact of such variability on fundamental rights?

- Did you ensure an adequate working definition of “fairness” that you apply in designing AI systems?
    - Is your definition commonly used? Did you consider other definitions before choosing this one?
    - Did you ensure a quantitative analysis or metrics to measure and test the applied definition of fairness?
    - Did you establish mechanisms to ensure fairness in your AI systems? Did you consider other potential mechanisms?
```

Improving fairness in automated decision-making systems has been a longstanding research focus. Recent advancements in deep learning (DL) mechanisms have brought this issue to the forefront of public attention. Current systems employ monitoring solutions to identify privacy and fairness concerns through explainability and bias detection techniques applied to datasets and algorithms. Depending on system requirements, a certain level of assurance is provided before deployment. However, with the rapid progress in DL mechanisms, comprehending, evaluating, and interpreting these systems has become challenging. In this new era of DL, models consist of billions of parameters and can process vast amounts of data, making it nearly impossible to ensure privacy and security assurance.

# Recommendations: Proactive Fairness Monitoring

In this article, we defined three use cases and explored mitigating bias following three different approaches (Experiment [#1](), [#2](), [#3]()). Below, we summarised some recommendations in non-technical language to summarise our recommendations to achieve proactive fairness in AI development environments.

## Define Accountabilities Clearly

In the accountability ethics, transparency and accountability guidance {cite}`cabinet_24`, practical measures are offered along with the offered framework:

* **Problem specification:** Prioritize policy specification during testing phases, focusing on the problem at hand and the desired outcomes.
* **Evaluation metrics:** Clearly define the parameters being tested, whether it pertains to accuracy, security, reliability, fairness, or explainability of the system.
* **Diverse testing criteria/team:** Conduct tests using high-quality, relevant, accurate, diverse, ethical, and appropriately sized datasets to ensure sustainable and intended outcomes. This includes ensuring that training datasets for fully automated decision-making, devoid of human judgment, uphold the characteristics of those affected. Ensure that testing is conducted by qualified individuals, preferably independent experts where feasible.
* **Risk assessment:** Perform regular impact and risk assessments, such as Data Protection Impact Assessment and Equality Impact Assessment when applicable.
* **Red teaming:** Implement 'red team testing', operating under the assumption that all algorithmic systems have the potential to cause harm to some extent.

You can use our monitoring tool to support these practical steps in various ways:

## Define a Risk Management Flow

Risk assessment should be use-case specific. Typically, algorithmic system risks can be summarised as follows {cite}`cabinet_24`:

-	**Input data:** Bias can exist in input data (mostly historical bias),
-	**Algorithm design:** The algorithm design might assume the data and evaluation methods cover all the cases and business logic comprehensively,
-	**Output decisions:** It can be open to interpretation, or falsely interpreted,
-	**Technical flaws:** Development and testing might not be adequate to reveal the issues,
-	**Usage flaws:** In a complex business logic, interoperability issues might occur.

## Define an Active Algorithm Auditing Flow

Auditing an algorithm, regardless of its type, is a dynamic and non-linear process. Koshiyama et al. demonstrated the interrelation between development stages and auditing verticals in five main steps {cite}`koshiyama_towards_2021`:

**Stages:** | Data and Task Setup | Feature pre-processing | Model selection | Post-processing and Reporting| Productionizing and Deploying
----|---- | ---- | ----| ---- | ---- |
**Explainability**| Data collection and labelling | Dictionary of variables | Model complexity | Auxiliary tools | Interface and documentation
**Fairness** | Population balance | Fair representations | Fairness constraints | Bias metrics assessments | Real-time monitoring of bias metrics

## Support Active Public Engagement 

As we already mentioned in the very beginning of this cookbook, we can use the following six considerations to build an active public engagement {cite}`cdei_24`:

1. **Focus on equitable AI/Data:** How society can benefit from the use of data or AI equally.
2. **Secure data flow:** Building confidence that organisations will be responsible for their actions.
3. **Image of AI:** With the increasing AI experience, the public becomes more pessimistic about the outcomes.
4. **Apprehensions about change:** Although increasing productivity in the day-to-day jobs are expected, there is also a concern mostly about job displacement.
5. **The preference is situation-dependent:** Utilising AI in social good projects such as cancer detection and financial support is highly favourable. However, clear risk management strategies can help public to support the rest of the use cases. 
6. **Low digital familiarity:** If the end users have lower digital literacy, they tend to be more pessimistic about the use of AI/data.


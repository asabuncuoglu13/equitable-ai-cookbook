# Scanning and Monitoring Tools

A comprehensive risk assessment requires a use-case specific vulnerability, threat and asset analysis. Risk is the potential for loss or harm to an asset due to threats exploiting vulnerabilities. Although there are several risk assessment frameworks available, we can summarise these different strategies in a systematic way following a component-based strategy, as it is summarised in [^1]:

[^1]: 'Ethics, Transparency and Accountability Framework for Automated
Decision-Making', GOV.UK. Accessed: Oct. 12, 2023.
<https://www.gov.uk/government/publications/ethics-transparency-and-accountability-framework-for-automated-decision-making/ethics-transparency-and-accountability-framework-for-automated-decision-making>

-   **Input data:** Adversarial data (e.g. bias, malicious content) can exist in input,
-   **Algorithm design:** The algorithm design might assume the data and evaluation methods cover all the cases and business logic comprehensively,
-   **Output decisions:** It can be open to interpretation, or falsely interpreted,
-   **Technical flaws:** Development and testing might not be adequate to reveal the issues,
-   **Usage flaws:** In a complex business logic, interoperability issues might occur.

In this five-level taxonomy, several sub-components should be scanned against multiple factors. A scanning/monitoring solution can help researchers and practitioners to track and evaluate these critical metrics and support keeping the system safe and trustworthy. Based on monitoring task, we can categorise monitoring/scanning tools into five: 

- **Model performance/resource utilisation:** Tracking the performance metrics of deep learning models, such as accuracy, precision, recall, F1 score, etc., over time or across different datasets. Monitoring the resource utilization of hardware resources
like CPU, GPU, memory, and storage during model training or inference. (e.g. [Tensorboard](https://www.tensorflow.org/tensorboard), [Weight&Biases](https://wandb.ai/site))

- **Data quality and privacy:** Monitoring the quality, volume, and distribution of data used for training and inference to detect data anomalies or biases that may affect model performance. (e.g. [Privado](https://www.privado.ai/), [Soda Core](https://www.soda.io/platform))

- **Security:** Monitoring for security vulnerabilities or unauthorized access attempts in both the deep learning models and software applications to ensure data integrity and resilience. (e.g. [CodeQL](https://codeql.github.com/), [Neptune](https://security.neptune.ai/))

- **Compliance:** Ensuring that models and software applications comply with regulatory requirements and industry standards, such as GDPR, HIPAA, EU AI Act etc. (e.g. [Seclea](https://www.seclea.com/solution/regulatory-compliance), [ComplianceAI](https://www.compliance.ai/))

- **Fairness:** Despite achieving fairness in DL development being a huge interest, limited solutions are available in the domain. For example, [Microsoft RAI Toolbox](https://github.com/microsoft/responsible-ai-toolbox) and [IBM Fair360](https://aif360.res.ibm.com/) provide an all-in-one marketplace for reactive methods rather than offering a proactive monitoring solution. [Fairlearn](https://github.com/fairlearn/fairlearn) is a useful library to quickly and easily call common fairness metrics in fairness assessments.

- **Safety Benchmark Testing:** A recent solution [Giskard](https://github.com/Giskard-AI/giskard) can be used to scan a set of ML models (including LLMs) against common vulnerabilities such as hallucinations and privacy breaches following a brute-force example-based strategy. [AISI's Inspect AI](https://github.com/UKGovernmentBEIS/inspect_ai) provides a set of tools to evaluate LLM safety.

With the rapid progress in DL mechanisms, comprehending, evaluating, and
interpreting these systems has become challenging. In this new era of
DL, models consist of billions of parameters and can process vast
amounts of data, making it nearly impossible to ensure privacy and
security assurance.

Practitioners can achieve continuous evaluation and monitoring of secure, private, and fair deep learning models through utilising monitoring tools effectively. The transparency of the results can also increase the collaboration between data scientists, developers, and domain experts by providing visibility into model monitoring results. Below, we summarised the main benefits of these tools from the security, privacy and fairness perspectives:

*From a security perspective:*

- Tracking access to models and data, detecting any unauthorized access attempts or security breaches.
- Monitoring model inputs and outputs for potential adversarial attacks or poisoning attempts.
- Employing anomaly detection techniques to identify unusual behaviour in model predictions, which may indicate security threats.

*From a privacy perspective:*

- Measuring the impact of privacy-enhancing techniques (e.g. differential privacy) to actively check individual data points cannot be extracted from the model's outputs.
- Tracking data access and ensuring compliance with privacy regulations such as GDPR or HIPAA.
- Detecting any unintentional internal/external data leakage.

*From the fairness perspective:*

- Utilizing different fairness metrics to assess the fairness of model predictions across different demographic groups or sensitive attributes.
- Real-world testing (A/B like model testing) to identify and mitigate any disparities or unfairness.
- Implementing state-of-the-art techniques such as adversarial debiasing or fairness-aware training quickly and evaluating their effectiveness over time.


# Practical Steps and Integrating Monitoring Solutions

In the accountability ethics, transparency and accountability guidance
[^1], practical measures are offered along with the offered framework:

-   **Problem specification:** Prioritize policy specification during testing phases, focusing on the problem at hand and the desired outcomes.
-   **Evaluation metrics:** Clearly define the parameters being tested, whether it pertains to accuracy, security, reliability, fairness, or explainability of the system. See the [A Structured Evaluation Approach Section](./evaluation.md) for more details.
-   **Diverse testing criteria/team:** Conduct tests using high-quality, relevant, accurate, diverse, ethical, and appropriately sized datasets to ensure sustainable and intended outcomes. This includes ensuring that training datasets for fully automated decision-making, devoid of human judgment, uphold the characteristics of those affected. Ensure that testing is conducted by qualified individuals, preferably independent experts where feasible.
-   **Risk assessment:** Perform regular impact and risk assessments, such as Data Protection Impact Assessment and Equality Impact Assessment when applicable.
-   **Red teaming:** Implement *red team testing*, operating under the assumption that all algorithmic systems have the potential to cause harm to some extent. See the [Red Teaming Section](./red-teaming.md) to see more details.
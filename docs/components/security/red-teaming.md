# Red Teaming

> See <https://github.com/asabuncuoglu13/ai-safety-demos> for safety evaluation templates.

Red teaming is a structured evaluation process that challenges and improves the effectiveness of plans, policies, systems, and assumptions. The concept is originating from defence and security. Typically, the process involves creating a "red team," which operates independently from the organization's primary team, the "blue team." The red team's objective is to simulate the perspectives, strategies, and tactics of adversaries/competitors.

In the context of AI, particularly in the development of more complex and data-heavy models like generative AI applications (LLMs, diffusion models for image generation, etc.), red teaming is an essential step towards robustness, safety, and integrity of these models. 

We can list some evaluation activities during the red teaming as following:

1. **Adversarial Testing**: Crafting inputs designed to trick or exploit vulnerabilities in the model, such as generating misleading or toxic responses.
2. **Ethical and Bias Analysis**: Adopting diverse perspectives and backgrounds, red team members can uncover hidden issues such as discriminative behaviour.
3. **Security Assessment**: Identifying vulnerabilities in the underlying infrastructure, data privacy risks, and potential avenues for malicious exploitation. 
4. **Scenario Planning**: Anticipating potential misuse or unintended consequences of LLMs by building hypothetical scenarios such as the spread of misinformation, manipulation of public opinion, or unintended reinforcement of harmful stereotypes.


## Some Best Practices from previous Read Teaming Events

### 2023 DEFCON

A policy briefing report {cite}`friedler_ai_2023` highlighted both the benefits and challenges associated with conducting red teaming activities. The report underscores the importance of thorough task definition for effective assessment and emphasizes that these activities serve as valuable initial steps in evaluating LLMs. However, it notes that attendees often lack the technical skills necessary to develop robust attack strategies. The report outlines four key elements for successful red teaming activities:

- Clear definition of the targeted flaws.
- Integration of transparency, disclosures, and external group access to the system.
- Inclusion of red teaming within a broader assessment framework.
- Commitment from stakeholders to allocate necessary plans and resources for addressing findings.


## Open-Source Tools for Red Teaming

Throughout the development of our fairness monitoring tool, we integrated some open-source repositories. Or, we created workflows that are compatible with these repositories. Below, we listed them with a brief explanation:


### Model performance/resource utilisation

Tracking the performance metrics of deep learning models, such as accuracy, precision, recall, F1 score, etc., over time or across different datasets. Monitoring the resource utilization of hardware resources
like CPU, GPU, memory, and storage during model training or inference. (e.g. [Tensorboard](https://www.tensorflow.org/tensorboard), [Weight&Biases](https://wandb.ai/site))


### Overall Analysis and Monitoring

**Inspect AI**
- https://github.com/UKGovernmentBEIS/inspect_ai.git
- Recently developed by AISI, the tool is designed to run safety benchmarks on LLMs.

**Giskard**
- https://github.com/Giskard-AI/giskard.git
- Focusing mainly on the security, the tool has built-in evaluation metrics and datasets to evaluate LLMs.

**AI Verify**
- https://github.com/aiverify-foundation/aiverify
- AI governance testing framework

**Langtest**
- https://github.com/JohnSnowLabs/langtest.git
- Conduct mutliple safety evaluations for an LLM in one line of code.

### Utiliy tools

**Prompto**
- https://github.com/alan-turing-institute/prompto
- Facilitates processing of experiments of LLMs

### Fairness

Despite achieving fairness in DL development being a huge interest, limited solutions are available in the domain. For example, [Microsoft RAI Toolbox](https://github.com/microsoft/responsible-ai-toolbox) and [IBM Fair360](https://aif360.res.ibm.com/) provide an all-in-one marketplace for reactive methods rather than offering a proactive monitoring solution. [Fairlearn](https://github.com/fairlearn/fairlearn) is a useful library to quickly and easily call common fairness metrics in fairness assessments.

**Fairlearn**
- https://github.com/fairlearn/fairlearn/
- Fairness evaluation metrics and mitigation methods.

**Aequitas**
- https://github.com/dssg/aequitas.git
- Easily integrate common fairness techniques into ML code.

### Explainability/Interpretability

**LIT (Learning Interpretability Tool)**
- https://github.com/PAIR-code/lit
- Visual tool to interactively explore model capabilities.

**LLM Comparator**
- https://github.com/PAIR-code/llm-comparator
- Another visual tool by Google PAIR team to explore different model outputs side by side.

### Data Quality and Privacy

Monitoring the quality, volume, and distribution of data used for training and inference to detect data anomalies or biases that may affect model performance. (e.g. [Privado](https://www.privado.ai/), [Soda Core](https://www.soda.io/platform))

**Chirps**
- https://github.com/mantiumai/chirps.git
- Find sensitive data stored in the vectorstores.

### Security

Monitoring for security vulnerabilities or unauthorized access attempts in both the deep learning models and software applications to ensure data integrity and resilience. (e.g. [CodeQL](https://codeql.github.com/), [Neptune](https://security.neptune.ai/))

### Alignment

**Huggingface Alingment Handbook**
- https://github.com/huggingface/alignment-handbook.git
- [Huggingface's Zephyr model collection](https://huggingface.co/collections/HuggingFaceH4/zephyr-7b-6538c6d6d5ddd1cbb1744a66) is a living example of using alignment techniques to develop a safer model.

**Google PAIR Model Alignment Tool**
- https://github.com/PAIR-code/model-alignment.git
- The library can be used to define alignment recipes in a dialog-based flow by utilising another LLM (default model is Google's Gemini).

### Compliance

Ensuring that models and software applications comply with regulatory requirements and industry standards, such as GDPR, HIPAA, EU AI Act etc. (e.g. [Seclea](https://www.seclea.com/solution/regulatory-compliance), [ComplianceAI](https://www.compliance.ai/))

### Guardrails

**NVIDIA NeMo**
- https://github.com/NVIDIA/NeMo-Guardrails
- End-to-end multimodal deep model development toolkit with a functionality of including custom safety guardrails.

## Some notes on using many different toolkits

Hollanek {cite}`hollanek_2024`, in their recent paper, coined a term "toolkitification", as trend in AI ethics, where toolkits are increasingly used to translate ethical theories into practice. The author argues that most AI ethics toolkits embody a reductionist approach to ethics, often dissociating it from politics and reducing ethical considerations to a checklist for engineers. This limits their capacity to drive meaningful change in AI development. The paper also explores alternative toolkits informed by feminist theory, posthumanism, and critical design, which emphasize the inseparability of ethics and politics. These alternative toolkits aim to foster power-sensitive dialogues among stakeholders and challenge dominant design paradigms.

Toolkitisation in AI safety, privacy, and trustworthiness might also face similar limitations. By focusing on compliance with predefined standards, these toolkits often simplify complex ethical issues into technical fixes, potentially neglecting broader socio-political and environmental implications. Alternative approaches that integrate diverse ethical frameworks, such as feminist and decolonial theories, could provide a more holistic understanding of these components, ensuring that toolkits do not merely enforce existing power structures but contribute to more equitable and inclusive AI practices.




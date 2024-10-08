# Overview of open-source repositories used in this cookbook

Throughout the development of our fairness monitoring tool, we integrated some open-source repositories. Or, we created workflows that are compatible with these repositories. Below, we listed them with a brief explanation:

## Overall Analysis and Monitoring

**Inspect AI**
- https://github.com/UKGovernmentBEIS/inspect_ai.git
- Recently developed by AISI, the tool is designed to run safety benchmarks on LLMs.

**Giskard**
- https://github.com/Giskard-AI/giskard.git
- Focusing mainly on the security, the tool has built-in evaluation metrics and datasets to evaluate LLMs.

**Langtest**
- https://github.com/JohnSnowLabs/langtest.git
- Conduct mutliple safety evaluations for an LLM in one line of code.

## Fairness

**Fairlearn**
- https://github.com/fairlearn/fairlearn/
- Fairness evaluation metrics and mitigation methods.

**Aequitas**
- https://github.com/dssg/aequitas.git
- Easily integrate common fairness techniques into ML code.

## Explainability/Interpretability

**LIT (Learning Interpretability Tool)**
- https://github.com/PAIR-code/lit
- Visual tool to interactively explore model capabilities.

**LLM Comparator**
- https://github.com/PAIR-code/llm-comparator
- Another visual tool by Google PAIR team to explore different model outputs side by side.

## Privacy

**Chirps**
- https://github.com/mantiumai/chirps.git
- Find sensitive data stored in the vectorstores.

## Alignment

**Huggingface Alingment Handbook**
- https://github.com/huggingface/alignment-handbook.git
- [Huggingface's Zephyr model collection](https://huggingface.co/collections/HuggingFaceH4/zephyr-7b-6538c6d6d5ddd1cbb1744a66) is a living example of using alignment techniques to develop a safer model.

**Google PAIR Model Alignment Tool**
- https://github.com/PAIR-code/model-alignment.git
- The library can be used to define alignment recipes in a dialog-based flow by utilising another LLM (default model is Google's Gemini).

## Guardrails

**NVIDIA NeMo**
- https://github.com/NVIDIA/NeMo-Guardrails
- End-to-end multimodal deep model development toolkit with a functionality of including custom safety guardrails.

## Some notes on using many different toolkits

Hollanek {cite}`hollanek_2024`, in their recent paper, coined a term "toolkitification", as trend in AI ethics, where toolkits are increasingly used to translate ethical theories into practice. The author argues that most AI ethics toolkits embody a reductionist approach to ethics, often dissociating it from politics and reducing ethical considerations to a checklist for engineers. This limits their capacity to drive meaningful change in AI development. The paper also explores alternative toolkits informed by feminist theory, posthumanism, and critical design, which emphasize the inseparability of ethics and politics. These alternative toolkits aim to foster power-sensitive dialogues among stakeholders and challenge dominant design paradigms.

Toolkitisation in AI safety, privacy, and trustworthiness might also face similar limitations. By focusing on compliance with predefined standards, these toolkits often simplify complex ethical issues into technical fixes, potentially neglecting broader socio-political and environmental implications. Alternative approaches that integrate diverse ethical frameworks, such as feminist and decolonial theories, could provide a more holistic understanding of these components, ensuring that toolkits do not merely enforce existing power structures but contribute to more equitable and inclusive AI practices.
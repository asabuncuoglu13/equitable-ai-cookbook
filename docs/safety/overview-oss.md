# Overview of Open-Source Repositories for AI Safety

Throughout the development of our monitoring tool, we integrated (or be inspired by) some open-source repositories into our tool. Below, we listed these repositories with a brief discussion on the ways using these tools for AI safety.

## Overall Analysis and Monitoring

**Inspect AI**
- https://github.com/UKGovernmentBEIS/inspect_ai.git
- Recently developed by AISI, the tool is designed to run safety benchmarks on LLMs.

**Giskard**
- https://github.com/Giskard-AI/giskard.git
- Focusing mainly on the security, the tool has built-in evaluation metrics and datasets to evaluate LLMs.

**Aequitas**
- https://github.com/dssg/aequitas.git
- Easily integrate common fairness techniques into ML code.

**Langtest**
- https://github.com/JohnSnowLabs/langtest.git
- Conduct mutliple safety evaluations for an LLM in one line of code.


## Security


## Fairness


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

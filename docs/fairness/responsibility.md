# Fairness Management Flow

```{note}
See our paper on this subject: [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.11280155.svg)](https://doi.org/10.5281/zenodo.11280155)
```

Achieving fairness in product development is a shared responsibility among all stakeholders, including developers, business analysts, product owners, designers, and user researchers. Expecting developers alone to analyse and apply all fairness notions throughout the entire development pipeline is unrealistic. They are also human and may have other work-related tasks, or personal distractions, or just be affected by current events.

In a product development process, each team member brings a unique skill set with different capabilities. This skill and capability difference makes it challenging to establish a common language across the development process. To address this, we created fairness team templates, or "*team*plates," to facilitate collaboration and integrate diverse expertise into a cohesive codebase.

## Responsible, Fair, Equitable...

While developing these complex systems, we mostly overload some words that we use in our daily lives. For example, one can use responsible, fair, equitable terms interchangible especially if it is not their native language. In this cookbook, we define responsible development as a subset of equitable AI and a superset of fair AI. 

```{note}
Responsible AI toolkit by Google: https://ai.google.dev/responsible
```

Incorporating interpretability and fairness into the ML development process requires the development team to manage insights from various tools and processes. Effectively utilizing information on model behavior and output disparities can enhance overall system fairness throughout the ML lifecycle by (1) providing insights into how features influence outcomes, (2) making model decisions understandable, (3) ensuring models meet fairness criteria, and (4) supporting informed decision-making. However, it's essential to recognize the limitations of current methods and to use them alongside other fairness-enhancing strategies, rather than as standalone solutions.

These limitations can be mitigated by fostering collaboration among different stakeholders. Given that our focus is on developing a sentiment signal analysis system, we’ve outlined how various stakeholders can use interpretability and fairness information throughout the development process:

1. **Data Scientists and ML Practitioners**: Analyze, test, and improve model fairness by identifying and addressing biases in data and model predictions.
2. **Financial Analysts and Domain Experts**: Ensure that model outputs align with real-world financial contexts and do not unintentionally favor certain market conditions or entities.
3. **Ethicists and Fairness Experts**: Define what fairness means in the context of financial sentiment analysis and ensure that the system adheres to broader ethical principles.
4. **Regulatory and Compliance Teams**: Ensure that the financial sentiment system complies with relevant regulations and guidelines, especially those related to fairness and non-discrimination in financial markets.

After collecting relevant information, stakeholders should document the process and outcomes. Typically, we create documentation for both the overall process and specific project outputs. FAID's logging framework includes four main categories: (1) System-level fairness log, (2) Model log, (3) Data log, and (4) Risk log.

## Managing Fairness-Related Information in the Development Process

Documenting fairness-related information is crucial to ensure transparency and accountability in the development process. FAID’s logging framework supports comprehensive documentation by categorizing information into four key areas:

1. **System-Level Fairness Log**: Tracks high-level fairness considerations across the entire system, ensuring that all components align with the overarching fairness objectives.
2. **Model Log**: Captures detailed information about model performance, including fairness metrics, bias assessments, and adjustments made during the development process. FAID's model metadata logging capability follows Google's model metadata format. For instance, their open-source LLM model, Gemma 2, is documented here: https://ai.google.dev/gemma/docs/model_card_2. The model card includes an "Ethics and Safety" section with benchmark scores from nine dataset evaluations.
3. **Data Log**: Documents the data sources, preprocessing steps, and any biases identified in the data, ensuring that data integrity is maintained throughout the lifecycle.
4. **Risk Log**: Records potential risks related to fairness and how they are mitigated, including any ethical concerns, compliance issues, and the steps taken to address them.

These logs are vital for creating a transparent audit trail that stakeholders can use to review and verify that fairness considerations have been adequately addressed at every stage of development.

## Continuous Improvement

Fairness is not a one-time achievement but an ongoing process. As models and systems evolve, so too must the strategies for ensuring fairness. This involves:

- **Regular Audits**: Periodic reviews of system performance and fairness metrics to identify and rectify any emerging biases.
- **Updating Documentation**: Continuously updating logs and documentation to reflect any changes in the system, model, data, or risk assessments.
- **Stakeholder Feedback**: Actively seeking and incorporating feedback from all stakeholders to refine fairness strategies and ensure that the system remains aligned with ethical and regulatory standards.
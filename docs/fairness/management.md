# Fairness Metadata Management Flow

```{note}
See our paper on this subject: [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.11280155.svg)](https://doi.org/10.5281/zenodo.11280155)
```

Achieving fairness in product development is a shared responsibility among all stakeholders, including developers, business analysts, product owners, designers, and user researchers. Each team member brings a unique skill set with different capabilities in a product development lifecycle. Although it is valuable, this skill and capability difference makes it challenging to establish a common language across the development process. To address this, we created fairness team templates, or "*team*plates," to facilitate collaboration and integrate diverse expertise into a cohesive codebase.

## Design Decisions

We structured this management flow from a HCI point of view and conducted a "knowledge analysis" considering the following knowledge facets {cite}`young1990knowledge`:

1. **Affordances**: This refers to the ways in which the system allows users to interact with it. In the context of fairness monitoring, affordances would involve clear, user-friendly tools that enable developers, data scientists, and stakeholders to easily apply fairness checks, monitor biases, and understand how they can affect the system at different stages of the development pipeline.

2. **Conceptual Model**: The conceptual model involves the user’s mental representation of how the system works. In this case, a fairness management flow must be designed in such a way that users (e.g., developers, business analysts) can easily understand the structure of fairness checks in the CI/CD pipeline, how responsibilities are distributed across teams, and the flow of data and metadata through the system (Figure 2 in the paper illustrates this flow).

3. **Specialized Meanings**: This includes technical or domain-specific meanings that users need to understand within the system. In fairness monitoring, this involves understanding fairness concepts like "demographic parity," "equalized odds," or "bias evaluation metrics," as well as the tools used for bias detection, such as Fairlearn and AI Fairness 360.

4. **Everyday Semantics**: This facet refers to meanings that come from everyday language, making sure that technical terms are simplified for broader audiences. In the fairness management flow, it is important that non-technical stakeholders (such as business owners or legal experts) can understand fairness outcomes without needing deep technical knowledge. Clear language and intuitive visualizations, such as those discussed for bias reports and fairness dashboards, are key here.

5. **Specific Item Knowledge**: This relates to the user's knowledge about specific components within the system. For example, developers must have a clear understanding of how individual fairness checks (e.g., the fairness metrics embedded in the CI/CD pipeline) work and how changes in the code could affect model fairness. They should also know which specific stages in the pipeline are prone to bias, such as data collection or model training.

6. **Locational Knowledge**: Locational knowledge refers to understanding where items are located within a system. In this case, users need to know where fairness tools, scripts, or configurations are located within the CI/CD pipeline, and where bias reports are stored and accessed by different team members, such as developers, data scientists, or business leaders (as illustrated by the YAML configuration file in Figure 3 of the paper).

7. **Decomposition**: This entails breaking down complex tasks into manageable parts. The fairness management flow achieves this by splitting the monitoring process into stages such as data preprocessing, bias evaluation, and model deployment. Each stage is assigned to specific stakeholders with specialized tasks, ensuring a modular approach to addressing fairness.

8. **Translation**: Translation involves converting between different formats or levels of abstraction. In the context of fairness, this may refer to converting complex fairness metrics or technical results into reports or dashboards that can be easily understood by non-technical stakeholders. It can also mean translating legal or ethical fairness requirements into actionable development tasks within the pipeline.

## Importance of Metadata Management

ML pipeline metadata can provide a rich source of information that can be leveraged to enhance our understanding of model behavior, particularly in the context of fairness. This metadata includes details about data preprocessing steps, feature engineering, model training parameters, and evaluation metrics. By systematically analyzing this metadata, researchers can identify potential sources of bias introduced at various stages of the machine learning pipeline. So, utilising pipeline metadata can lead developing more transparent, accountable, and fair AI systems.

In the book, "Expert Systems for Experts" {cite}`parsaye1988expert` Parsaye and Chignell explains **metarules** and **frames** as abstraction mechanisms to present gradual information. We can follow the same abstraction steps in the metadata creation with a focus on AI Fairness research:

## Choosing the Right Level of Abstraction

Storing development process knowledge is possible via: (1) Predicate calculus/formal logic, (2) Set of production rules, (3) Semantic networks (graph data) to represent relationships, and (4) Frames to store all structural knowledge of a specific object in one place {cite}`beynon_davies_expert_1991`.

**Metarules** are rules that govern the application and organization of other rules within an expert system. They help manage the execution of rules, particularly in complex systems where many rules interact. In the context of AI fairness, metarules can be used to ensure that fairness constraints are consistently applied throughout the decision-making process. For example, a metarule might enforce that any rule applied to model predictions must first check for potential biases in the data, ensuring that sensitive attributes like race or gender are handled appropriately. Constructing metarules requires careful consideration to avoid exceptions or unintended biases. For example, even if a metarule is designed to prioritize fairness in model outcomes, there may be edge cases where this rule conflicts with other important criteria, such as accuracy or efficiency.

**Frames** are structured representations of stereotypical situations or objects, used to package and organize knowledge within an expert system. A frame typically includes slots that represent attributes or properties of the concept, with values that can be filled in as specific instances or defaults. Frames can be organized hierarchically, allowing for inheritance of properties from more general to more specific frames. Frames can be used to represent different scenarios or cases that an AI system might encounter, particularly in fairness research. For example, a frame for a "Loan Applicant" might include slots for income, credit score, and demographic information. A fairness-oriented frame could ensure that certain sensitive attributes are flagged and handled with care, ensuring that decisions like loan approval are not biased by race or gender. These frames can also be used to simulate different scenarios to test for potential biases across various demographic groups.

## Developing Recipes and *Team*plates

*Teamplates* are a combination of metarules and frames to create a recipe-like knowledge representation for different teams. These templates includes pre-defined folder structures, fairness tests, CI/CD workflows and codebase structures that promote fairness and equitable AI development.

The aim is enabling different teams to create customised templates for specific tasks. For example, a business analyst can request a specific type of report. In this case, developers can easily choose a predefined flow/template (probably a YAML file) and integrate it into the repository to get this report in the next deployment.

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
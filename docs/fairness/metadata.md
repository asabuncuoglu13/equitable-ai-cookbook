# Using Metadata Effectively in AI Fairness Research

A critical component of AI Assurance is ensuring fairness of the overall system. ML pipeline metadata can provide a rich source of information that can be leveraged to enhance our understanding of model behavior, particularly in the context of fairness. This metadata includes details about data preprocessing steps, feature engineering, model training parameters, and evaluation metrics. By systematically analyzing this metadata, researchers can identify potential sources of bias introduced at various stages of the machine learning pipeline. So, utilising pipeline metadata can lead developing more transparent, accountable, and fair AI systems.

In the book, "Expert Systems for Experts" {cite}`parsaye1988expert` Parsaye and Chignell explains **metarules** and **frames** as abstraction mechanisms to present gradual information. We can follow the same abstraction steps in the metadata creation with a focus on AI Fairness research:

## Choosing the Right Level of Abstraction

Storing development process knowledge is possible via: (1) Predicate calculus/formal logic, (2) Set of production rules, (3) Semantic networks (graph data) to represent relationships, and (4) Frames to store all structural knowledge of a specific object in one place {cite}`beynon_davies_expert_1991`.

**Metarules** are rules that govern the application and organization of other rules within an expert system. They help manage the execution of rules, particularly in complex systems where many rules interact. In the context of AI fairness, metarules can be used to ensure that fairness constraints are consistently applied throughout the decision-making process. For example, a metarule might enforce that any rule applied to model predictions must first check for potential biases in the data, ensuring that sensitive attributes like race or gender are handled appropriately. Constructing metarules requires careful consideration to avoid exceptions or unintended biases. For example, even if a metarule is designed to prioritize fairness in model outcomes, there may be edge cases where this rule conflicts with other important criteria, such as accuracy or efficiency.

**Frames** are structured representations of stereotypical situations or objects, used to package and organize knowledge within an expert system. A frame typically includes slots that represent attributes or properties of the concept, with values that can be filled in as specific instances or defaults. Frames can be organized hierarchically, allowing for inheritance of properties from more general to more specific frames. Frames can be used to represent different scenarios or cases that an AI system might encounter, particularly in fairness research. For example, a frame for a "Loan Applicant" might include slots for income, credit score, and demographic information. A fairness-oriented frame could ensure that certain sensitive attributes are flagged and handled with care, ensuring that decisions like loan approval are not biased by race or gender. These frames can also be used to simulate different scenarios to test for potential biases across various demographic groups.

## Developing Recipes and *Team*plates

*Teamplates* are a combination of metarules and frames to create a recipe-like knowledge representation for different teams. These templates includes pre-defined folder structures, fairness tests, CI/CD workflows and codebase structures that promote fairness and equitable AI development.

The aim is enabling different teams to create customised templates for specific tasks. For example, a business analyst can request a specific type of report. In this case, developers can easily choose a predefined flow/template (probably a YAML file) and integrate it into the repository to get this report in the next deployment.
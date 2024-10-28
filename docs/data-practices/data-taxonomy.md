# The ODI's Data Taxonomy

#TODO: Add "equity" and "fairness" considerations for each data item.

See the original document: <https://theodi.org/news-and-events/blog/a-data-for-ai-taxonomy/>

| Category | Type of Data | Description|
|----------|--------------|------------|
| Developing AI systems        | Existing data             | Data not directly used for model training but as the basis for creating training datasets.              |
| Developing AI systems        | Training data             | Data processed to train AI models by helping them recognize patterns and improve accuracy.              |
| Developing AI systems        | Reference data            | Data used to enrich training datasets with context, such as knowledge graphs or linguistic resources.   |
| Developing AI systems        | Fine-tuning data          | Smaller datasets used to adapt pre-trained models for specialized tasks while preserving their capabilities.|
| Developing AI systems        | Testing and validation data | Data used to test models during development to ensure accuracy and representativeness.                  |
| Developing AI systems        | Benchmarks                | Datasets used to evaluate a model's performance and accuracy against unseen data.                       |
| Developing AI systems        | Synthetic data            | Algorithmically generated data used for training, fine-tuning, or benchmarking models.                  |
| Developing AI systems        | Data about the data       | Information about the datasets used to develop AI models, such as their size, source, and composition.  |
| Deploying AI systems         | Model weights             | Numerical values representing the relationships learned by a model during training.                     |
| Deploying AI systems         | Local data                | Data an AI model processes in a specific deployment context, depending on its purpose and architecture. |
| Deploying AI systems         | Prompts                   | Instructions or queries given to AI systems to generate responses, commonly in generative models.       |
| Deploying AI systems         | Outputs from models       | Generated data from AI systems, such as text, audio, video, or structured outputs.                      |
| Monitoring AI systems        | Data about models         | Information disclosed about AI models, including version, performance, and ethical considerations.      |
| Monitoring AI systems        | Data about model usage and performance in context | Data collected during model use, such as query logs and performance metrics, used for improvements.     |
| Monitoring AI systems        | Registers of model deployments | Authoritative lists of AI models deployed in specific contexts or sectors, maintained by governments or organizations. |
| Monitoring AI systems        | Data about the AI ecosystem | Data about the broader AI ecosystem, including models, incidents, policies, and workforce statistics.   |

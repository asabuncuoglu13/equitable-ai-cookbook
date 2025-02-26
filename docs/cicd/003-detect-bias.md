# Bias Detection throughout the Pipeline

Monitoring, detecting and evaluating bias throughout an ML development pipeline is crucial for ensuring fairness and equity in your models. Here’s a structured approach to incorporating bias evaluation and continuous monitoring in your pipeline, along with recommended tools and libraries.

```{seealso}
Checkout our [financial sentiment analysis fairness evaluation repository](https://github.com/asabuncuoglu13/faid-test-financial-sentiment-analysis) that demonstrates how we converted a bias analysis notebook to a maintainable and automated codebase with CI/CD integrations.
```

# Proactive Fairness Monitoring

We view bias as a systemic error with multiple components. To evaluate bias in a machine learning model, practitioners typically use "protected attributes" to divide a population into groups. According to the EHRC guide, these attributes include age, disability, gender reassignment, pregnancy and maternity (including breastfeeding), race, religion or belief, sex, and sexual orientation {cite}`ehrc_24`. For each protected attribute, we can identify privileged and underprivileged groups based on whether the group has a systematic advantage. Our goal throughout the pipeline is to assess whether any bias occurs that could lead to discrimination at the individual or group level (see [Fairness Notions](../fairness/notions.md) for a detailed explanation).

## Bias Sources throughout the Pipeline

The below table demonstrates bias sources listed in the recent [International AI Safety Report](https://www.gov.uk/government/publications/international-ai-safety-report-2025). The bias sources and descriptions are directly obtained from the report:

| Lifecycle Stage          | Bias Source              | Description  | Example (Credit Scoring Risk) |
|-------------------------|-------------------------|-------------|--------------------------------|
| **Data Collection**      | Sampling Bias          | Certain perspectives, demographics, or groups are overrepresented or underrepresented in the data. | Credit scoring data primarily collected from urban customers may not generalize well to rural populations. |
|                         | Selection Bias         | Only certain data types or contexts are included, limiting representativeness. | Excluding alternative credit data, such as rent or utility payments, may disadvantage individuals without traditional credit history. |
| **Data Annotation**      | Labeller Bias         | Annotators' backgrounds, perspectives, and cultural biases affect their classification of data, influencing the labeling process. | Loan officers manually classifying high-risk applicants may unconsciously rate applicants from certain backgrounds as riskier. |
| **Data Curation**        | Historical Bias        | Reflecting or perpetuating past societal biases within curated data. | Using past loan approval data that historically favored certain demographics may lead to models reinforcing systemic discrimination. |
| **Data Pre-processing**  | Feature Selection Bias | Excluding relevant features from a dataset. | Removing non-traditional financial indicators, like employment stability, can reduce the accuracy of risk assessments for self-employed individuals. |
| **Model Training**       | Label Imbalance       | Unequal representation in labeled data, leading to biased model outputs. | Training a credit scoring model primarily on high-income applicants may cause it to inaccurately assess low-income borrowers. |
| **Deployment Context**   | Contextual Bias       | A model is trained on data from a context that differs from its application, leading to worse outcomes for certain groups. | A credit scoring model trained in a high-income country may not perform well in a developing economy with different financial behaviors. |
| **Evaluation & Validation** | Benchmark Bias      | Evaluation benchmarks favor certain groups or knowledge bases over others. | Testing a credit model primarily on data from prime borrowers may result in poor predictions for subprime borrowers. |
| **Feedback Mechanisms**  | Feedback Loop Bias   | Models learn from biased user feedback, reinforcing initial biases. | A credit scoring system that lowers scores for rejected applicants (assuming they are high-risk) may prevent them from improving their credit over time. |


## Through Data Collection, Preprocessing and Feature Engineering

The following state diagram summarizes the main steps of possible bias evaluation points in a traditional ML flow.

```{mermaid}
stateDiagram-v2
    [*] --> VersionControl
    VersionControl --> DataPipeline
    VersionControl --> ModelPipeline

    state DataPipeline {
    DataIngestion --> DataCleaning: Analyze Data \n Distribution
    DataIngestion --> DataCleaning: Raw Data
    DataIngestion --> DataCleaning: External Data
    DataCleaning --> FeatureEngineering: Check for \n Missing Values
    DataCleaning --> FeatureEngineering: Handle \n Missing Values
    DataCleaning --> FeatureEngineering: Cleaned Data
    }

    state ModelPipeline {
        ModelTraining --> ModelEvaluation: Monitor \n Training Metrics
        ModelTraining --> ModelEvaluation: Train \n Model
        ModelTraining --> ModelEvaluation: Training \n Metrics
        ModelEvaluation --> ModelDeployment: Evaluate Bias \n in Metrics
        ModelEvaluation --> ModelDeployment: Evaluation \n Metrics
        ModelEvaluation --> ModelDeployment: Bias \n Evaluation
        ModelDeployment --> PostDeploymentMonitoring: Check for \n Deployment Bias
        ModelDeployment --> PostDeploymentMonitoring: Deploy \n Model
    }

    FeatureEngineering --> [*]: Monitor Bias \n in Data

    PostDeploymentMonitoring --> [*]: Monitor \n Real-Time Bias
    PostDeploymentMonitoring --> [*]: Monitor \n Model Performance
    PostDeploymentMonitoring --> [*]: Collect \n User Feedback

```


### Data Pipeline: Collection, Preprocessing, Feature Engineering

An essential step in identifying bias is checking the data distribution in both raw and processed data. There are effective tools available to analyze feature distribution and identify imbalances. For instance, [**ydata-profiling**](https://github.com/ydataai/ydata-profiling) can generate profiling reports from a pandas DataFrame, and the [**Great Expectations**](https://github.com/great-expectations/great_expectations) library can validate, document, and profile data. 

It's crucial to ensure that data cleaning and feature engineering processes do not inadvertently introduce bias. The selected/generated features can introduce bias. Or, features can be proxies for the sensitive attributes (can carry hidden correlation). Therefore, it's important to run profiling after each step using a human-in-the-loop approach.

**The generated report should include**:
- Summary statistics and distribution visualizations.
- Details of missing values and imbalanced classes.
- Findings regarding assumptions and experiments conducted on the data.
- Correlation analysis between features and sensitive attributes.

## Model Pipeline: Training, Evaluation, Deployment

In this step, we should evaluate models using fairness metrics along with traditional performance metrics. Based on the evaluation results, we will apply bias mitigation techniques. We can also use A/B testing (or similar methodologies) to ensure new models do not introduce bias compared to previous versions.

We can evaluate the model performance with different evaluation metrics using fairness mitigation libraries such as [**fairlearn**](https://fairlearn.org/) and [**AI Fairness 360 (AIF360)**](https://aif360.readthedocs.io).

For the monitoring, we can utilise **Prometheus**, **Grafana**, **Evidently**. Thesese platforms provide different capabilities with different customisation levels for AI production pipelines. 


**The generated report should include**:
- Evaluation results of models using fairness metrics like disparate impact, equal opportunity difference, and others.
- Steps of bias mitigation techniques.

## How is this process proactive?

In this ML pipeline, we created a workflow that you can monitor the development process of an ML project. However, establishing clear fairness metrics and thresholds for each stage depends on the use case. For example, a credit scoring application might require a different setup than a financial news analyser NLP model.

For each use case, using lifecycle management tools to integrate continuous monitoring into your CI/CD pipeline, setting up automated alerts for when bias metrics exceed predefined thresholds, building mechanisms to support running regular external audits of the entire pipeline, and engaging with diverse stakeholders to gather feedback is essential to align the fairness evaluation scores with real-world impacts.

By integrating these tools and following this structured approach, you can proactively evaluate and mitigate bias throughout the entire ML lifecycle, ensuring fairness and equity in your models.
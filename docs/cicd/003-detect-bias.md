# Bias Detection throughout the Pipeline

Monitoring, detecting and evaluating bias throughout an ML development pipeline is crucial for ensuring fairness and equity in your models. Here’s a structured approach to incorporating bias evaluation and continuous monitoring in your pipeline, along with recommended tools and libraries.

```{seealso}
Checkout our [financial sentiment analysis fairness evaluation repository](https://github.com/asabuncuoglu13/faid-test-financial-sentiment-analysis) that demonstrates how we converted a bias analysis notebook to a maintainable and automated codebase with CI/CD integrations.
```

# Proactive Fairness Monitoring

We view bias as a systemic error with multiple components. To evaluate bias in a machine learning model, practitioners typically use "protected attributes" to divide a population into groups. According to the EHRC guide, these attributes include age, disability, gender reassignment, pregnancy and maternity (including breastfeeding), race, religion or belief, sex, and sexual orientation {cite}`ehrc_24`. For each protected attribute, we can identify privileged and underprivileged groups based on whether the group has a systematic advantage. Our goal throughout the pipeline is to assess whether any bias occurs that could lead to discrimination at the individual or group level (see [Fairness Notions](../fairness/notions.md) for a detailed explanation).

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

After integrating DVC with FAID, you can also integrate many other open-source tools (i.e. MLFlow, TFX, TorchServe.) to ease the ML lifecycle management.
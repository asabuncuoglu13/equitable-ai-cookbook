# Holistic Evaluation

Evaluating the fairness of AI models is a challenging process as defining what fairness means depends on the context of a specific application.

A fairness evaluation generally requires a step-by-step analysis that considers each step of the development process individually and holistically. For example, identifying any biases or imbalances that could lead to unfair outcomes in training data is an essential step at the very beginning of the development process. However, choosing the right metrics is critical, as it might amplify other tpes of bias in the output generation stage.

So, choosing appropriate metrics to evaluate the model's fairness performance requires a holistic understanding. A well-known recent effort is Stanford's HELM (Holistic Evaluation of Language Models) [^helm]. The project, with a specific focus on transparency, measures seven metrics including *accuracy*, *calibration*, *robustness*, *fairness*, *bias*, *toxicity*,
and *efficiency*.


[^helm]: <https://crfm.stanford.edu/2022/11/17/helm.html>

## A Structured Evaluation Approach

We developed a structured hierarchical evaluation (and mitigation) framework aimed at accelerating the adoption of equitable AI practices. 

![Hierarchical representation of the proposed framework](./media/hierarchical-framework.png)

We identified a set of evaluation and mitigation strategies.

![Hierarchical representation of the proposed framework](./media/framework-all.png)


## Limitations

This structured approach serves to initiate the evaluation process rather than providing an all-encompassing guarantee of fairness, privacy, or security. While structured, goal-oriented methodologies are valuable, they may overlook adversarial impacts that are less obvious or require innovative approaches. This tendency is reminiscent of the "invisible gorilla" phenomenon, a concept originating from cognitive science.

The "invisible gorilla" experiment (Chabris and Simons, 2010)illustrates this phenomenon. In the experiment, participants were asked to watch a video of people passing basketballs and count the number of passes. Amidst this task, a person dressed in a gorilla suit would walk through the scene. Many participants failed to notice the gorilla due to their focused attention on counting passes. This experiment highlights the human tendency to overlook unexpected or irrelevant stimuli when our attention is narrowly focused on a specific task.

Similarly, in the context of AI evaluation, a structured approach may inadvertently lead evaluators to overlook certain aspects, such as subtle biases or unintended consequences, especially if they are not explicitly defined in the evaluation criteria. This underscores the importance of complementing structured methodologies with a critical awareness of potential blind spots, encouraging a more holistic assessment of AI systems.

In this sense, we promote our approach as a proactive framework to detect issues, however in a red-teaming activity we suggest using a mixed of methods including creative ways to trick systems.
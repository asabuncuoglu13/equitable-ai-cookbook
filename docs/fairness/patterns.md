# Design Patterns for Monitoring Fairness/Safety

```{note}
We shared more generalisable, system-level patterns in [Safety Recipes Chapter](../safety/recipes.md). This chapter focuses on structuring the development codebase for monitoring fairness and broader safety characteristics.
```

"Design patterns" are reusable solutions to common problems that arise during software design and development.These patterns support designers and developers to mitigate many software development concerns "by design." Using patterns in development naturally supports developers in building their solutions with the previously established best practices. For example, design patterns in object-oriented programming define creational, behavioural, and structural relations between objects and their main classes in a codebase. Writing code following the patterns prevents common security and privacy issues. Although it is a common practice in traditional application development, we have not seen a corresponding set of rules within the fairness domain. 

The design patterns developed as part of our research aims to support interdisciplinary teams in structuring their development flows following best practices.  Patterns support transferring knowledge between different disciplines, producing concrete and actionable outputs, and ensuring effective technical development "by design". We have seen similar success in software development with object-oriented design patterns, which helped developers maintain their basic security and maintenance principles through coding.

Beyond being reusable patterns, design patterns presents a structured cognitive style. Following the success of patterns in software engineering, recent efforts ([Lu-et-al.(2022)], [Hutiri(2023)]) propose design patterns for responsible-AI. However, translating existing research into specific software architecture implications is a challenge due to their broad guidance for development pipelines. Building upon these recent scholar works, we formed a more structured "cognition"-based approach in design patterns.

**An example design pattern from OOP:** Object-oriented programming (OOP) patterns represent a widely adopted approach to software design, particularly since the 1990s. They have become standard practices in languages such as Java and Kotlin, as well as other object-oriented programming paradigms. For example, **Abstract Factory** design pattern provides an interface for creating families of related or dependent objects without specifying their concrete classes. Abstract factory and other methods that create interfaces are generally based on *abstraction,* which involves identifying common features among different entities and creating a generalized representation. This executive function is fundamental to human thinking. The cognitive base of these design patterns are actually based on executive functions such as planning, inhibition, monitoring, and prioritising.

## Defining Patterns for AI Fairness

As the design patterns in OOP naturally fits to the "world" of "objects" in the programming paradigm, the fairness design patterns should fit into the "world" of "achieving fair decision making processes." The closest candidate of design patterns in the world of fairness is designing "policy" and "test" recipes/strategies for fairness experiments. These recipes can be utilised in designing structured unit tests for continuous integration processes. In this sense, designing patterns for fairness is more close to designing patterns for unit testing.

Fairness lacks a precise definition and an ideal quantification metric. However, by combining various notions and metrics, we can approach a more comprehensive understanding of fairness. Designing patterns to guide developers in adopting a structured approach to enhancing fairness in their applications seems promising.

## Possible Design Pattern Suggestions

1. Test Patterns
2. Structural Patterns
3. Behavioral Patterns

### Test Patterns

#### Defining Context

1. **Fixtures:** A fixture in unit testing refers to the fixed state of a set of objects used as a baseline for running tests. It ensures that there is a well-known and consistent environment in which tests are run, so that results are reliable and repeatable. Fixtures typically involve setting up the necessary objects, data, or conditions before tests are executed and cleaning up afterward.

```python
# tests/code/fairtest.py
import pytest
from faid.data import BiasMitigationPreprocessor

# Arrange
@pytest.fixture
def dataset_loc():
    return "./datasets/dataset.csv"

@pytest.fixture
def preprocessor():
    return BiasMitigationPreprocessor()

def test_bias_mitigation():
    # Act
    dataset = load_dataset(dataset_loc)
    preprocessed_data = preprocessor.preprocess(dataset)
    fair_data = apply_fairness_algorithm(preprocessed_data)
    
    # Assert
    assert check_fairness(fair_data)

```

### Structural Patterns

In their seminal work {cite}`NIPS15_hiddendebt`, Sculley and other Google researchers discuss several ML system anti-patterns that can arise in machine learning systems, particularly concerning system design. These anti-patterns can contribute to technical debt, making the system difficult to maintain, update, and improve over time. We can interpret these debt patterns as the main patterns that can lead uninterpretable, hence unfair ML models.

**Glue Code Problem:** This pattern emerges when using general-purpose ML packages, leading to a large amount of supporting code (glue code) being written to adapt data for the packages.  Glue code makes it expensive to explore alternative approaches and can lock the system into the specific package, hindering improvements. A key mitigation strategy is wrapping black-box packages into common APIs. This promotes reusability and simplifies the process of switching between packages.

**Pipeline Jungles Problem:** This anti-pattern often arises in data preparation.  As new data sources and signals are incorporated, the system for preparing data can become a complex and tangled web of processes, making it challenging to manage, test, and debug. A holistic approach to data collection and feature extraction is crucial for avoiding this pattern.  While it demands significant upfront effort, refactoring a pipeline jungle can lead to substantial long-term cost savings and faster innovation.

**Dead Experimental Codepaths Problem:** This anti-pattern refers to the accumulation of conditional branches or experimental codepaths within the main production code. While seemingly harmless individually, these codepaths can exponentially increase system complexity, making maintenance and testing difficult. Regularly reviewing experimental branches to identify and remove unused ones is essential. Often, only a small fraction of these branches remain relevant, and removing the rest can significantly simplify the system.

**Abstraction Debt Problem:** The lack of strong, standardized abstractions in ML system design contributes to this debt. This absence of clear interfaces for handling data streams, models, and predictions can lead to blurred boundaries between system components, making it difficult to maintain and update. The development of widely accepted abstractions for core ML concepts is crucial for mitigating this debt. These abstractions would provide a more structured and modular approach to building and maintaining ML systems. The sources note that the parameter-server abstraction for distributed learning, while not without competition, is a potentially more robust approach compared to MapReduce.

**Plain-Old-Data Type Smell:** Using simple data types like floats and integers to encode complex ML information can lead to ambiguity and complicate system understanding.

**Multiple-Language Smell:** Using multiple programming languages within a single ML system can hinder effective testing, increase maintenance complexity, and make knowledge transfer more difficult. 

**Prototype Smell:** Over-reliance on prototyping environments for testing new ideas can indicate a brittle and inflexible production system.  It can also tempt developers to deploy prototype code in production due to time pressures. 

#### Technical Debt and Bias in ML Systems

In [Common Bias Types in ML Pipeline (and some solutions)](./bias.md) chapter, we introduced potential bias types that can occur throughout the ML pipeline. Technical debt, in various forms, can exacerbate or even directly lead to bias in machine learning systems, particularly within the financial AI domain.  **Entanglement**, a key concept from the sources, describes how changes in one part of an ML system can cascade and impact other components in unexpected ways. For instance, if an ML system incurs technical debt through a "**pipeline jungle**" – a convoluted data processing pipeline –  even seemingly small modifications to address one data issue could inadvertently introduce or amplify biases in the data used for training. This entanglement can make it extremely difficult to isolate and mitigate bias, as fixing one problem might unknowingly create another. 

Technical debt often manifests as poorly documented systems, convoluted code, or an over-reliance on quick fixes rather than robust solutions.  This lack of clarity can mask potential biases in data, algorithmic design, or human use. For example, **"glue code"**, or ad-hoc code written to integrate different parts of a system, can create opaque data dependencies that obscure the origin and potential biases present in input data. This obfuscation makes it challenging to identify and address issues like **historical bias**, where past inequalities embedded in data continue to perpetuate discriminatory outcomes.  Similarly, **"dead experimental codepaths"** - remnants of past experiments left in the codebase - can introduce unforeseen feedback loops that exacerbate biases.  Without a clear understanding of how different components interact due to accumulated technical debt, identifying the root cause of bias becomes increasingly difficult. 

Mitigating bias in ML systems requires a multifaceted approach that explicitly addresses technical debt. The sources emphasize the importance of **well-defined abstractions, modular design, and comprehensive documentation**.  These practices can help untangle complex systems and make data lineage and algorithmic processes more transparent, facilitating the identification and mitigation of bias. Regularly reviewing and refactoring code, particularly data pipelines and experimental codepaths, can prevent technical debt from escalating and further entrenching bias. Implementing robust configuration management systems with version control and automated checks can also minimize the risk of introducing bias through configuration errors. Fundamentally, fostering a culture that values system maintainability, transparency, and ethical considerations alongside performance is essential to proactively address technical debt and mitigate the risk of bias in financial AI systems. 

### Behavioral Patterns

Behavioral patterns support the proactive application of *test* and *structural* patterns. We can adopt these patterns from OOP mostly as it is, just by modifying the code objects to higher level fairness artifacts.

1. **Observer Pattern:** Continuously monitor the environment for changes or patterns. In the context of fairness, the Observer pattern facilitates ongoing monitoring of data and model outputs for potential biases or unfair outcomes.


```python
class Subject:
    def __init__(self):
        self._observers = []

    def attach(self, observer):
        self._observers.append(observer)

    def detach(self, observer):
        self._observers.remove(observer)

    def notify(self, data):
        for observer in self._observers:
            observer.update(data)

class FairnessObserver:
    def update(self, data):
        if self.detect_bias(data):
            print("Bias detected in data:", data)

    def detect_bias(self, data):
        # Simple bias detection logic (for demonstration purposes)
        return data.get('bias', False)

subject = Subject()
observer = FairnessObserver()
subject.attach(observer)
```

2. **Strategy Pattern:** The Strategy pattern corresponds to the ability to adapt to different situations by selecting and executing appropriate strategies. In fairness design, this pattern allows developers to adapt to diverse fairness requirements or contexts by choosing and implementing suitable fairness algorithms or approaches as interchangeable strategies.

3. **Chain of Responsibility Pattern** The Chain of Responsibility delegates the responsibility for handling tasks or decisions passed along a chain of entities. In fairness design, this pattern delegates fairness-related decisions or interventions to different components in the system, promoting modular and distributed fairness management.


### Architectural Patterns

MVC (Model-View-Controller) remains a viable architecture for many systems. And, it is particularly useful for building a modular and reusable components. However, AI-enabled systems might demand some enhancements in MVC, due to their dynamic and data-intensive nature. AI systems often rely heavily on data pipelines, which MVC does not explicitly address. These system introduces probabilistic outputs that may affect all layers.
Further, continuous learning requires integration of data flow and feedback mechanisms. So, we suggest the following updates to MVC for AI-Enabled Systems:

1. **Model Layer Evolution**:
   - Extend the model to include a **data pipeline** for preprocessing, feature extraction, and model updates.
   - Incorporate modules for managing trained models, inference, and retraining workflows.
   - Add feedback mechanisms to loop user actions and outcomes back into the data pipeline for model improvement.

2. **Controller as Orchestrator**:
   - Expand the controller's role to manage **data flows** and **AI model interactions**.
   - Use middleware or microservices to integrate AI model calls, reducing tight coupling.

3. **Enhanced View Layer**:
   - Adapt the view to handle **dynamic outputs** like uncertainty or confidence scores.
   - Support interactive and adaptive user interfaces for real-time adjustments.


Augment MVC with a pipeline-first mindset, where data preprocessing, model serving, and user interactions seamlessly interconnect.


## Conclusion

In the context of building fairness, developers can choose between selecting individual examples to inform a fair algorithm (inductive approach) or opting for group fairness notions to optimize the entire model based on selected criteria (deductive approach).

## Useful Links

### Testing:

1. https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices
2. https://raygun.com/blog/unit-testing-patterns/
3. https://docs.pytest.org/en/6.2.x/contents.html
4. http://xunitpatterns.com/List%20of%20Patterns.html

### OOP Patterns:

1. https://refactoring.guru/design-patterns/behavioral-patterns
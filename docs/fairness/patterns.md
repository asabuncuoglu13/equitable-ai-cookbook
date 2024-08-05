# Design Patterns for Fairness/Equitable AI

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

1. **Decorator Pattern** The Decorator pattern enables modifying or augmenting existing behaviors or processes as needed. In fairness design, decorators can offer a flexible mechanism for modifying or enhancing fairness-related algorithms without rigidly altering the underlying system architecture.

2. **Composite Pattern** The Composite pattern supports integrating diverse information or elements into coherent structures. In fairness design, this pattern facilitates the integration and analysis of data from multiple sources or dimensions to assess fairness comprehensively across various aspects of the system.

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
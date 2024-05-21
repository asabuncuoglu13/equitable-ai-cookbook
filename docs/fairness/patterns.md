# Design Patterns for Fairness/Equitable AI

"Design patterns" originated from the design domain established good practices in software development and resulted in mitigating many security concerns "by design." Using patterns in development naturally supports developers in building their solutions with the previously established best practices. For example, design patterns in object-oriented programming define creational, behavioural, and structural relations between objects and their main classes in a codebase. Writing code following the patterns prevents common security and privacy issues. Although it is a common practice in traditional application development, we have not seen a corresponding set of rules within the fairness domain. The design patterns developed as part of our solution will support SMEs in structuring their development flows following best practices and guide development of "fairness rules" that will power up the code analysis tool.

"Design patterns" are reusable solutions to common problems that arise during software design and development. Patterns support transferring knowledge between different disciplines, producing concrete and actionable outputs, and ensuring effective technical development "by design". We have seen similar success in software development with object-oriented design patterns, which helped developers maintain their basic security and maintenance principles through coding.

Beyond being reusable patterns, design patterns presents a structured thinking style. Following the success of patterns in software engineering, recent efforts ([Lu-et-al.(2022)], [Hutiri(2023)]) propose design patterns for responsible-AI. However, translating existing research into specific software architecture implications is a challenge due to their broad guidance for development pipelines. Building upon these recent scholar works, we will try to form a more structured "cognition"-based approach in design patterns.

## An Example from OOP

Object-oriented programming (OOP) patterns represent a widely adopted approach to software design, particularly since the 1990s. They have become standard practices in languages such as Java and Kotlin, as well as other object-oriented programming paradigms.

**Cognitive Basis - Abstraction**: Abstraction involves identifying common features among different entities and creating a generalized representation. This cognitive process is fundamental to human thinking.

**Related Pattern - Factory Method**: The creation of an Abstract Factory to produce instances sharing similar characteristics in object-oriented programming mirrors the human cognitive process of forming higher-order structures.

## Extending to Fairness Design

As the design patterns in OOP naturally fits to the "world" of "objects" in the programming paradigm, the fairness design patterns should fit into the "world" of "achieving fair decision making processes." The closest candidate of design patterns in the world of fairness is designing "policy recipes" for fairness experiments. These policy recipes can be utilised in designing structured unit tests for continuous integration processes. In this sense, designing patterns for fairness is more close to designing patterns for unit testing.

See <https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices> and <https://raygun.com/blog/unit-testing-patterns/> for some unit testing patterns.

Fairness lacks a precise definition and an ideal quantification metric. However, by combining various notions and metrics, we can approach a more comprehensive understanding of fairness. Designing patterns to guide developers in adopting a structured approach to enhancing fairness in their applications seems promising.

**Cognitive Basis - Reasoning**: Human reasoning typically follows two main approaches: inductive and deductive.

- **Inductive Reasoning**: This involves drawing generalized conclusions from specific observations or examples.
- **Deductive Reasoning**: Here, we start with general principles and apply them to specific situations to derive logical conclusions.

Similarly, in the context of building fairness, developers can choose between selecting individual examples to inform a fair algorithm (inductive approach) or opting for group fairness notions to optimize the entire model based on selected criteria (deductive approach).

## Possible Design Pattern Suggestions

In addition to this "reasoning-based" pattern, several other design patterns can be applied to enhance fairness in software systems:

1. **Observer Pattern**
   - **Cognitive Base**: Awareness
     - This pattern aligns with the cognitive process of awareness, where individuals continuously monitor their environment for changes or patterns. In the context of fairness, the Observer pattern facilitates ongoing monitoring of data and model outputs, akin to human vigilance for potential biases or unfair outcomes.

2. **Strategy Pattern**
   - **Cognitive Base**: Adaptation
     - The Strategy pattern corresponds to the cognitive ability to adapt to different situations by selecting and executing appropriate strategies. In fairness design, this pattern allows developers to adapt to diverse fairness requirements or contexts by choosing and implementing suitable fairness algorithms or approaches as interchangeable strategies.

3. **Decorator Pattern**
   - **Cognitive Base**: Flexibility
     - The Decorator pattern reflects the cognitive capacity for flexibility, enabling individuals to modify or augment existing behaviors or processes as needed. In fairness design, decorators offer a flexible mechanism for modifying or enhancing fairness-related algorithms without rigidly altering the underlying system architecture.

4. **Composite Pattern**
   - **Cognitive Base**: Integration
     - The Composite pattern mirrors the cognitive process of integrating diverse information or elements into coherent structures. In fairness design, this pattern facilitates the integration and analysis of data from multiple sources or dimensions to assess fairness comprehensively across various aspects of the system.

5. **Chain of Responsibility Pattern**
   - **Cognitive Base**: Delegation
     - The Chain of Responsibility pattern aligns with the cognitive principle of delegation, where responsibility for handling tasks or decisions is passed along a chain of entities. In fairness design, this pattern delegates fairness-related decisions or interventions to different components in the system, promoting modular and distributed fairness management.

By grounding these design patterns in cognitive principles, developers can leverage human cognition to design more intuitive, adaptable, and equitable software systems.
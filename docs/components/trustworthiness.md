# Trustworthiness: Key Components

The National Institute of Standards and Technology (NIST) has defined trustworthy AI systems through seven key characteristics: validity and reliability, safety, security and resilience, accountability and transparency, explainability and interpretability, privacy enhancement, and fair management of harmful bias. Each of these characteristics involves numerous subcomponents, contributing to the complexity of achieving a shared understanding and realisation of truly trustworthy AI.

```{note}
#TODO: Complete examples for each trustworthiness chracteristics.
```

## Valid and Reliable

ISO 9000:2015 defines validation as the confirmation of requirements for a particular use case. ISO/IEC 5723:2022 defines reliability as the ability of an item to perform a specific action under certain conditions. The main challenge of adopting learning-based mechanisms in critical systems is providing reliable benchmarks for given different conditions. A rule-based system is in this sense much more reliable. However, with the industry-wide collaborations, we see an integration of AI-powered mechanisms by reinforcing the outcome reliability with human-in-the-loop approaches. 

Beyond the validity and reliability of a single product, we believe that these characteristics rely on the behaviour of the overall ecosystem. In this sense, industry collaborations and establishing standards are crucial. In addition, creating interoperable standards and protocols ensure compatibility and seamless communication between different systems and platforms. Connectivity plays a crucial role in facilitating interoperability, enabling data exchange and integration across diverse digital environments.

```{note}
**Examples**:

We have seen promising progress since generative AI has become widely available. For example, a recent industry-wide collaboration, including Adobe, Leica, Nikon, Sony, BBC, etc., is established to achieve digital content provenance. The [content credentials](https://contentauthenticity.org/how-it-works) are a digital watermark that proves the authenticity of the content. 
```

## Secure and Resilient

ISO/IEC TS 5723:2022 defines AI security and resilience as their ability of withstanding unexpected adverse events/changes. It requires a comprehensive analysis of the attack vector, possible threats and mitigations. Businesses follow different structured threat analysis approaches based on their needs and potential attack vectors. In our previous research, we offered a comprehensive approach encompassing three principal stages: (1) Human behaviour analysis, (2) Threat assessment (STRIDE and MITRE ATT\&CK), and (3) Enhancing resilience by analysing extended components (MITRE ATLAS). 

```{note}
**Examples**:

-	Map of adversarial attacks
-	Interdisciplinary and holistic security approach
```

Robust security protocols and privacy measures protect sensitive data and ensure confidentiality, integrity, and availability. Connectivity is essential for implementing and maintaining these measures, facilitating secure data transmission and storage across digital networks.

## Accountable and Transparent

NIST defines AI transparency as the meaningful and appropriate level of access to the information related to AI lifecycle and its outputs. The accountability depends on this transparency.

Enhancing accountability requires a comprehensive analysis of organisational structures and responsibilities. Further, current regulations and policies do not adequately covers the level of required responsibilities.  

```{note}
**Examples**:

- Signing AI models (https://github.com/google/model-transparency?tab=readme-ov-file#projects) 
- Open initiatives make government data and information available to the public in accessible and machine-readable formats, fostering transparency, innovation, and collaboration. Connectivity enables widespread access to open data platforms, empowering users to leverage data for various purposes, including research, analysis, and decision-making.
```

## Explainable and Interpretable

NIST defines AI explainability as representing the underlying mechanisms of AI systems’ operation. The interpretability concept refers to the meaning of AI systems’ output in the context of their designed functional purposes.

```{note}
**Examples**:

- Explainability and visualisation studies
```

## Privacy Enhanced

The definition of privacy historically and philosophically changes over time, but in general it refers to the norms and practices to protect humans from potential harms related to human autonomy, identity, and dignity.

```{note}
**Examples**:

-	Federated models
-	Differential privacy
```

## Fair – with Harmful Bias Managed

Aligned with NIST, we define AI fairness as the overall effort to sustain equality and equity by preventing harmful bias and discrimination. Despite the exhaustive efforts in the field, most AI models tend to demonstrate bias towards discrimination. Existing libraries/toolkits like AI360 has limited capabilities to uncover the bias in complex systems. The AI360 and similar tools works like a marketplace for existing techniques, which depends on the expertise of the user and nature of the selected problem. In an engineering project, we require more proactive approaches to capture potential fairness issues in multiple stages.  

```{note}
**Examples**:

```

## Safe

ISO/IEC TS 5723:2022 defines AI safety as its capability to prevent potential harm such as threats to human life, health, property, or the environment. Last year, the AI Summit put an initial effort into establishing a consensus and a shared language for AI safety among countries. Achieving safety in the AI and DPI systems only possible if we have "good-enough" metric results of other characteristics. 

```{note}
**Examples**:

- METR AI Evaluation from DeepMind team (<https://metr.org/blog/2023-03-18-update-on-recent-evals/>)
- Human-value alignment is key to achieving AI safety.
```
# Fairness in Face Biometrics

The concept of fairness in the context of face biometrics centres on the principle that algorithms should operate equitably, providing consistent and unbiased results regardless of an individual's readily observable characteristics such as age, gender, skin color, or nationality. This implies that the technology should not systematically disadvantage or treat certain groups of people differently based on these attributes. The goal is to ensure that face biometric systems do not penalise individuals due to their membership in a particular demographic group. Understanding fairness in this domain requires considering various perspectives, including individual fairness, which posits that similar inputs should yield similar predictions, and group fairness, which focuses on whether protected and unprotected groups are treated in a comparable manner.

The increasing integration of face biometrics into numerous critical societal applications -- ranging from authentication to everyday apps to national ID biometrics, underscores the importance of ensuring fairness. If these algorithms exhibit bias and do not perform equitably across different demographic groups, they can lead to adverse effects on certain populations. Unfair algorithms have the potential to cause discrimination, restrict access to essential services, and lead to wrongful accusations. Furthermore, biases embedded within these systems can exacerbate existing societal inequalities, particularly in sensitive areas like law enforcement, where the consequences of misidentification can be severe. The growing reliance on face biometrics in high-stakes scenarios amplifies the potential for harm arising from unfair systems, thereby necessitating proactive and comprehensive measures to guarantee equity for all individuals.

## Core Principles of Fairness in Face Biometrics

Several core principles underpin the concept of fairness in face biometrics, guiding the development and deployment of these technologies.

- **Non-discrimination**: The technology should not unlawfully discriminate against individuals based on legally protected attributes. This principle should be explicitly embedded in the terms of service governing the use of such technologies.
- **Equity and equal performance**: Ideally, the technology should behave consistently and without performance disparities, regardless of an individual's visible characteristics. (accuracy and reliability for all individuals, including those who have been historically underrepresented in training datasets)
- **Transparency**: Transparency is another crucial principle, and has different definitions/meanings in terms of development requirements. This article defines it as thorough documentation of the capabilities and limitations of the system.
- **Accountability**: With transparent documentation, accountability can be established with appropriate levels of human oversight and control over the uses of the technology.

## Understanding Bias in Face Biometric Systems

Bias in face biometric systems can manifest in various forms, leading to unfair outcomes for certain groups. Two prominent types of bias are demographic bias and bias related to image quality.

### Bias related to representation

The source of this bias can be over or under representation of different demographic groups, resulting in performance disparities across the groups. For instance, a research project from the MIT Media lab has documented error rate differences exceeding 20-30% between light-skinned men and darker-skinned women (See: <https://www.media.mit.edu/projects/gender-shades/overview/>).

The lack of diversity in training data means the algorithms may not learn to effectively extract and compare facial features across the full spectrum of human appearances. This can lead to a higher likelihood of misidentification or non-identification for individuals belonging to underrepresented demographics.

### Bias related to image quality

Bias in face recognition can also stem from issues related to image quality, such as blur, low resolution, poor lighting, and variations in pose or facial expression. Historically, camera technology has often been calibrated to perform optimally with lighter skin tones (See [Turing's Technical Report](https://www.turing.ac.uk/sites/default/files/2020-10/understanding_bias_in_facial_recognition_technology.pdf)). This has resulted in poorer image quality, such as underexposure, for individuals with darker skin, which in turn negatively impacted the accuracy of face recognition algorithms for this demographic.

Variations in pose and facial expression can also introduce bias. If the training data predominantly features individuals with neutral expressions and frontal poses, the system may struggle to accurately recognise individuals from demographic groups that are more likely to be captured in non-ideal conditions or with a wider range of expressions.

Furthermore, environmental factors such as extreme temperatures and background noise can affect the performance of facial biometric systems, and these factors might disproportionately impact certain communities or settings. The quality of the capture equipment, including the camera or sensor, also plays a crucial role. Low-quality images captured with inferior equipment may lack the necessary detail for accurate identification, leading to both false negatives and false positives.

## Metrics for Evaluation

Evaluating the fairness of face biometric algorithms requires the use of specific metrics that can quantify performance disparities across different demographic groups.

> See a sample report from NIST FRVT to observe metrics in action: <https://pages.nist.gov/frvt/html/frvt11.html>

- **The Equal Error Rate (EER)** is a common metric used in biometrics, representing the point at which the False Match Rate (FMR) and the False Non-Match Rate (FNMR) are equal. The FMR is the proportion of impostor attempts that are falsely accepted as a match, while the FNMR is the proportion of genuine attempts that are incorrectly rejected as non-matches. To assess fairness, the EER is calculated separately for different demographic groups, and these rates are then compared.
- **Fairness Discrepancy Rate (FDR):** This metric, proposed by researchers at the Idiap Research Institute, quantifies the maximum difference in false match rate (FMR) and false non-match rate (FNMR) performance between any two demographic groups at a given discrimination threshold.  
- **Gini Aggregation Rate for Biometric Equitability (GARBE):** Developed as a fairness measure, GARBE can be used in conjunction with Pareto optimisation to select among alternative algorithms based on the trade-off between accuracy and fairness.  
- **Fair Sensitivity Analysis (Fair SA):** This evaluation framework measures group fairness through the lens of robustness. It jointly assesses a model's vulnerability to image perturbations and variations in demographics, allowing for the analysis of how different subgroups are treated under varying levels of perturbation.  
- **Equal Opportunity:** This fairness criterion ensures that individuals from different groups who are qualified for a positive outcome have an equal chance of receiving it, focusing on the true positive rate across groups.  
- **Equality of Odds:** This metric requires that both the true positive rate and the false positive rate are the same across different groups, aiming for similar error distributions.  
- **Predictive Parity:** This metric ensures that the positive predictions made by the model have the same precision across different groups, meaning that when the model predicts a positive outcome, the probability of it being correct is the same for all groups.  
- **Treatment Equality:** This metric focuses on balancing the ratio of the false positive rate to the false negative rate across different groups, often used in contexts like predictive policing to ensure equitable error rates.  

## Techniques and Strategies for Mitigating Bias and Improving Fairness

Several techniques and strategies are being explored and implemented to mitigate bias and enhance fairness in face biometric technologies. These approaches can be broadly categorised as data-centric, algorithm-level interventions, post-processing techniques, and human oversight and evaluation.

### Data-Centric Approaches

One of the primary strategies for mitigating bias involves focusing on the data used to train these algorithms. Collecting diverse datasets that accurately represent the global population, including various demographic groups, races, genders, and ages, is crucial. Ensuring a balanced representation of these groups within the training data can help reduce performance disparities. However, achieving balance in terms of numbers alone may not be sufficient to address all forms of bias.

> Leverage the existing large-scale research. For example, you can use Google's Skin Tone reseach (Monk Scale) to compare the representativeness of your dataset. <https://skintone.google/>

Techniques like data augmentation, which involves applying transformations such as rotations and brightness adjustments to existing images, can be used to create more varied and robust datasets. Additionally, the use of AI-generated imagery is being explored as a way to enhance dataset diversity, potentially addressing issues of underrepresentation while also mitigating privacy concerns associated with real-world images.

To ensure the quality and fairness of training data, external and independent audits of datasets are essential. These audits can help identify imbalances and biases that might not be immediately apparent. Furthermore, ensuring that the data is accurately and consistently labeled is critical, as poorly labeled data can introduce or exacerbate biases in the trained models.

### Algorithm-Level Interventions

Beyond the data itself, modifications to the algorithms play a significant role in improving fairness. Enhancing the overall accuracy of face recognition algorithms often leads to a reduction in demographic differentials. Techniques such as multi-scale feature vision and spatial attention, which allow algorithms to focus on relevant facial features at different resolutions, can contribute to improved accuracy and potentially reduce bias.

> Test your algorithm with "what-if" kind of experiments regularly. See examples: https://pair-code.github.io/what-if-tool/

Adversarial training is another promising approach, where models are trained on datasets that include both biased and unbiased samples to help them learn to identify and correct biases during the recognition process. Debiasing variational autoencoders (DB-VAE) are an example of such techniques that aim to automatically discover and mitigate hidden biases within the training data.

Imposing fairness constraints directly into the algorithm's learning process can also force classifiers to perform more equitably across different sensitive groups . Finally, the continuous upgrading of algorithms as new and more advanced versions are developed is important for addressing evolving challenges related to bias.

### Human Oversight and Evaluation

Human involvement remains crucial in ensuring fairness in face biometrics. Maintaining an appropriate level of human control over the deployment and use of these technologies is essential, particularly in high-stakes applications. Implementing blind taste tests, where human evaluators assess the performance of algorithms without knowing the demographic attributes of the individuals being evaluated, can help minimise unconscious biases in the assessment process.

Regular data audits and algorithmic audits are vital for identifying and addressing biases that may arise over time or in specific use cases. Engaging with communities that are disproportionately affected by biases in face recognition technology and seeking their input can provide valuable insights and help ensure that mitigation strategies are effective and address the real-world concerns of these groups.
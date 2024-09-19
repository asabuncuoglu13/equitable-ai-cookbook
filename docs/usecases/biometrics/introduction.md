# Face Fairness Benchmark

Bias in facial imaging has been a persistent challenge, spanning from the early days of analogue photography to the modern digital era. Historically, cameras were often designed with a bias towards accurately capturing lighter skin tones, which led to an inherent disadvantage for individuals with darker skin tones. This issue, rooted in the sensor technology and the way cameras were calibrated, has evolved over time but continues to affect the accuracy of facial recognition systems {cite}`leslie_understanding_2020`. In addition to these sensor-level biases, unbalanced representation of different demographic groups in training datasets amplifies the bias in the existing sysmtes.

In the digital public infrastructure systems, especially in ID-based services, facial biometrics is gaining traction. To ensure the reliability and security of these applications, governments and regulatory bodies have instituted standards such as ISO/IEC 19794-5, which set the benchmarks for facial recognition algorithms. Despite these standards, achieving accurate and fair biometrics remains a challenge, primarily due to demographic dependencies.

Variations in skin color, facial features, and proportions across different demographics can significantly affect the performance of facial recognition models. These variations often lead to disparities in accuracy, which can result in biases against certain demographic groups. Therefore, it is crucial to benchmark these algorithms across a diverse spectrum of users to ensure fairness and accuracy. This presents a significant challenge, as it requires comprehensive testing and validation against a wide array of demographic factors to create truly equitable biometric systems.

The current biometric benchmarks, such as [Face Recognition Vendor Test (FRVT)]( https://www.nist.gov/programs-projects/face-recognition-vendor-test-frvt), aim to address these issues by providing a framework for evaluating the performance of facial recognition systems. These benchmarks run performance analysis metrics such as processing and memory failures, average, maximum and minimum times, memory allocations, and localisation accuracies. They also report overall and subgroup accuracies based on different metrics such as EER, FMR, FMR/FRNMR and DET(t) Curve. They incorporate a diverse set of facial images that encompass a wide range of demographic characteristics, including variations in age, gender, ethnicity, and facial expressions.

However, despite these efforts, these existing benchmarks still fall short in representation of certain demographic groups or fail to account for subtle but significant variations within these groups. Further, this lacks the open-source implementation and test use cases. Consequently, there is a pressing need for more open, robust and inclusive benchmarks that can better capture the diversity of the global population and accelerate the open-innovation.

By establishing open face fairness benchmark, developers can identify and mitigate biases, promoting more equitable and trustworthy AI applications that serve everyone fairly and reliably. An open benchmark can also help establishing clear and standardized metrics for evaluating fairness ensures that all facial recognition systems are held to the same criteria, making comparisons across different systems more meaningful. We have observed that in the AI space (Huggingface leaderboards, NeurIPS and CVPR challenges, etc.) that public benchmarks and results can increase transparency in AI development and accelerate the pace of innovation. Further, demonstrating that facial recognition systems have been rigorously tested for fairness can help build trust among users, particularly those from historically marginalized groups.

We planned a set of five experiments as the first iteration of this benchmark:

- Skin Tone Representation
- Facial Proportions Representation
- Comparing Fairness Notions and Metrics
- Performance with Synthetic Data

Following these experiments, fairness auditors can build their analysis step-by-step and achieve a level of granularity to present the results in a more interpretable way. In this report, we present the first experiment (Skin Tone Representation) in detail, then we introduce the rest of the experiments with a brief explanation.

## Example: Face Skin Tone Representation

There is a growing availability of face image datasets that could researchers and practitioners use. For example, the Celeb-A dataset is a popular dataset that contains over 200,000 images of celebrities.However, the representativeness of the skin colour and other demographic physical features is limited. 

:::{note}
For example,the Celeb-A dataset is also available in the [Know-Your-Data tool](https://knowyourdata-tfds.withgoogle.com). A sample exploration: (1) Select Blond Hair attribute, Check Male and Female Disparity, (2) Sect Bald attribute, Apply the same gender disparity. As you will also see, blonde-haired females are overrepresented in the dataset by a factor of 1.61. And blonde-hair males are underrepresented by a factor of 0.14. In the same experiment, you can see female-baldness is significantly underrepresented by a factor of 0.01!
:::

Defining skin color and quantifying it is an active research area. One commonly utilised metric is *individual typology angle* (ITA), which is originated from dermatology research.

This experiment is based on Monk Skin Tone dataset (Google Research), which contains images of individuals with different skin tones. The goal of this experiment is: 

- To evaluate the representation of different skin tones in the dataset compared to the representation obtained from Monk dataset.
- To identify any biases that may exist in the facial biometrics model.

Their dataset consists of images of individuals with six different skin tones, ranging from very light to very dark. The results of this experiment will provide insights into how well facial recognition models can generalize across different skin tones and help identify any biases that may exist.

:::{seealso}
The next page is a sample experiment of our benchmark: [Face Skin Tone Experiment](./face-skin-tone.ipynb). See all the experiments and benchmark on our Github repository: <https://github.com/asabuncuoglu13/fair-face>
:::

## Next Steps

The Face Fairness Benchmark is an ongoing project that aims to provide a comprehensive evaluation of facial recognition systems across a diverse range of demographic factors. The next steps in this project include:

- Expanding the benchmark to include additional demographic factors such as age, facial expressions, and environmental conditions.
- Developing a standardized set of metrics for evaluating fairness in facial recognition systems.
- Establishing an open-source platform for sharing benchmark data and results to promote transparency and collaboration in the AI community.
- Collaborating with industry partners and regulatory bodies to ensure that the benchmark aligns with industry standards and best practices.
- Conducting further experiments to evaluate the performance of facial recognition systems under different conditions and scenarios.
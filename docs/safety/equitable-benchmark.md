# Benchmarking AI Models Efficiently

Efficient benchmarking is critical to reduce the cost and power consumption. Considering the impact of the overall development process in terms of sustainability is part of equitable AI research.

- A comprehensive tutorial on LLM benchmarking: https://github.com/borgr/tutEval (LREC-COLING 2024 Tutorial)

**Some good benchmarks start playing with:**
- https://github.com/felipemaiapolo/tinyBenchmarks
- https://mixeval.github.io/
- 

## Pathways

1. **Running Benchmarks on Pre-trained Propriety LLMs with APIs**  
   - Many LLM providers offer API endpoints to interact with their models. You can leverage these endpoints, but ensure your benchmark adheres to their terms of use. If unsure, reach out to their support teams to clarify whether your research or testing aligns with their policies.
   - A flexible alternative is to use platforms like *Azure Machine Learning Studio* ([ml.azure.com](https://ml.azure.com/)). Their model catalog allows you to select models and deploy serverless endpoints, following a pay-as-you-go pricing model.
   - Either way, use your local compute to store your dataset and send queries to server-side applications that are managed by 3rd party vendors. For querying you can use:
     - https://github.com/alan-turing-institute/prompto
     - https://github.com/andrewyng/aisuite
     - https://python.langchain.com/docs/integrations/providers/microsoft/
   - To calculate a potential breakdown of inferencing cost, use online price calculators such as https://llmpricecheck.com/calculator/.

2. **Running Benchmarks on Pre-training Open-Source LLMs**
    - If it is a small model (<=3B parameters), you might be able to run these models on your local compute. 
    - If the model is larger than 3B parameters, you need a GPU > 16GB, so it is more convenient and efficient to run the benchmark on server side. You can use Azure ML or other cloud GPU providers to run your benchmark.
    -  Assuming it is an R&D project, you might have access to a national tier HPC system. For example, UKRI supports both universities and businesses to conduct their research on specific HPC systems, such as Baskerville (https://www.baskerville.ac.uk/) You can use these systems to run the inference model. Create a batch job to run multiple datasets at the same time to maximise your use of the system.

3. **Fine-tuning Open-source Models**
   You can find most of the open source models available on Huggingface. You have several options to fine-tune your model:
   - Keep in mind that, although it is cheaper than training from scratch, it is significantly more expensive compared to inferencing. A typical fine-tuning job requires around 8x80GB GPUs.
   - You can use Azure ML Studio or any other cloud GPU providers. Based on the model architecture you might need multiple GPUs. Make sure that the GPU provider supports mutliple node computing.
   - Assuming it is an R&D project, you might have access to a national tier HPC system. For example, UKRI supports both universities and businesses to conduct their research on specific HPC systems, such as Baskerville (https://www.baskerville.ac.uk/)

   - You can also find lots of open-source fine tuning examples on Huggingface and Github. An example: https://github.com/cohere-ai/cohere-finetune
    After fine-tuning, follow Pathway#2 to run your benchmark.

4. **Training from Scratch**
   This requires a significant technical expertise. So, probably you already know what you are doing!

## Practical Considerations

1. **Understanding Model Limitations and Capabilities**  
   Every LLM has different strengths, weaknesses, and constraints (e.g., input token limits or specific fine-tuning capabilities). Before benchmarking, review the model’s documentation to understand:  
   - Token limits per request  
   - Supported languages  
   - Output constraints (e.g., response length, generation styles)  

2. **Choosing Metrics for Evaluation**  
   Define clear metrics based on your use case. Common metrics include:  
   - Accuracy (for tasks like classification or question answering)  
   - Perplexity (for evaluating language models’ fluency)  
   - Latency (time taken to generate a response)  
   - Cost-efficiency (model cost per inference)  

3. **Data Privacy and Security Considerations**  
   When sending data to LLMs, ensure you’re compliant with privacy regulations (e.g., GDPR). Avoid uploading sensitive or confidential data unless you have guarantees about how data is handled. Some platforms offer data redaction or zero-retention policies.

4. **Handling Rate Limits and Quotas**  
   LLM APIs often have usage limits. Plan for:  
   - Rate limits (requests per second/minute)  
   - Quota management (total token usage per month)  
   If your benchmark requires extensive testing, discuss quota adjustments with the provider.

5. **Optimizing Cost and Engergy Efficiency**  
   Benchmarking large models can be expensive. Tips to optimize costs:  
   - Use smaller models for initial tests.  
   - Batch requests where possible.
   - Consider using tiny benchmarks that also guarentees comprehensiveness. See https://github.com/felipemaiapolo/tinyBenchmarks

6. **Documenting and Reproducing Results**  
   Ensure your benchmark is repeatable by documenting:  
   - Model version and configurations  
   - Input data and prompts  
   - Exact evaluation metrics  

7.  **Monitoring and Debugging**  
    Monitor for unusual outputs or errors during benchmarking. Use logs to identify:  
    - API failures   
    - Input and output formatting issues
    And, share them with the IT and other researchers to make the upcoming experiments more cost-effective.


```{note}
**Do you want to contribute to this document?**

You can use the following HackMD Collaborative Document to suggest edits:
https://hackmd.io/@j5E9lRB-RFmXy2lzUosX4Q/r1KMW1L7yx/edit

Or, fork these repo, make your edits, and create a new pull request on Github.
```
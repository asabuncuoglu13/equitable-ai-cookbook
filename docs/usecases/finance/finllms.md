# A Practical Review of Financial Large Language Models

The rapid progress and adoption of large language models (LLMs) have accelerated the development of sector-specific models for finance. This paper provides a concise, practical review of financial LLMs (finLLMs), examining their training methods, functionalities, and performance metrics. We explore use cases such as sentiment analysis, market prediction, fraud detection, and customer service automation. By synthesizing current research and industry practices, this review aims to guide practitioners and researchers in leveraging finLLMs to their full potential and fostering open-source innovations in this field.

**Limitation:** Focused on English language datasets. The next step is to extend it to the Turkish language. If the project gets popular, researchers fluent in other languages are welcome to make contributions.

Apart from BloombergGPT, all the models discussed in this paper are open-source, allowing for an effective examination of their training stages and performance. BloombergGPT is included due to its significance, as it was trained from scratch using a vast amount of financial data, and its technical report provides a detailed explanation of the process.

## BloombergGPT

BloombergGPT is a large language model that was developed by Bloomberg specifically for the financial sector. It is used to generate financial news and analysis, as well as to develop new financial products and services.

## FinGPT

FinGPT is an open large language model that is trained on a massive dataset of financial data. It can be used for a variety of financial tasks, such as generating financial reports, performing financial analysis, and developing new financial products and services.

## FinBERT

FinBERT is a pre-trained NLP model to analyze sentiment of financial text. It is built by further training the BERT language model in the finance domain, using a large financial corpus and thereby fine-tuning it for financial sentiment classification.

## InvestLM

InvestLM, tuned on lLaMA-65B. InvestLM shows capabilities such as processing financial text and provides helpful responses to investment related questions. Financial experts, including hedge fund managers and research analysts, rate InvestLM’s response as comparable to those of state-of-the-art commercial models (GPT-3.5, GPT-4, and Claude-2).

## PIXIU (FINMA)

[ArXiv](https://arxiv.org/pdf/2211.00083)  
[GitHub](https://github.com/SALT-NLP/FLANG)

A comprehensive framework including the first financial LLM based on fine-tuning Llama with instruction data, the first instruction data with 136K data samples to support the fine-tuning and a holistic evaluation benchmark with four financial NLP tasks and one financial prediction task.

## FLANG

FLANG (Financial LANGuage model) leverages financial data alongside English datasets to train a relatively small transformer model family called [ELECTRA](https://huggingface.co/docs/transformers/en/model_doc/electra).

## Available Datasets

Below, we summarised some commonly used financial text datasets. You can run [our exploratory interactive notebook](./eda-fin-data.ipynb) to preview and play with these data.

### Loughran-McDonald Sentiment Word Lists

The Loughran-McDonald Sentiment Word Lists are a set of word lists specifically designed for sentiment analysis in financial texts. These lists include positive, negative, and uncertain words commonly found in financial documents.

### Financial PhraseBank

The Financial PhraseBank is a collection of phrases commonly used in financial news and reports. It is often used for sentiment analysis and other NLP tasks in the financial domain.

### FinQA

FiQA (Financial Question Answering) is a dataset designed for question answering. It includes a variety of financial documents, such as news articles and earnings reports, along with questions and answers related to those documents.

### Financial News Dataset

The Financial News Dataset is a collection of news articles from various financial news sources. It is often used for tasks such as news classification, sentiment analysis, and event detection in the financial domain.

### Financial Time Series Dataset

The Financial Time Series Dataset includes historical price data for various financial instruments, such as stocks, bonds, and commodities. It is used for tasks such as price prediction, volatility forecasting, and risk management.

### SEC Filings Dataset

The SEC Filings Dataset is a collection of documents filed with the U.S. Securities and Exchange Commission (SEC), including annual reports, quarterly reports, and other regulatory filings. It is used for tasks such as information extraction, sentiment analysis, and financial forecasting.

## Available Benchmarks

### FLEU

FLEU contains five tasks. It is not maintained for the last two years. BloombergGPT is used this benchmark to evaluate the model. (They also used 12 different closed-source tasks from Bloomberg data.)

### BizBench

It is a a *quantitative reasoning benchmark for business and finance* LLMs. The benhmakr consists of eight quantitative reasoning tasks including Q&A over data via program synthesis, code-generation tasks from newly collected and augmented QA data, reading comprehension of text and tables, and understanding financial concepts and formulas {cite}`koncelkedziorski2024bizbenchquantitativereasoningbenchmark`. 
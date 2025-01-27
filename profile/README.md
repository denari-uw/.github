## Project Overview

Welcome to the **Retrieval-Augmented Generation (RAG) Pipeline Discovery and Optimization** project! You are now part of an exciting collaboration between Denari and UW Madison, where you'll design and optimize a cutting-edge RAG pipeline tailored for contextually accurate and time-sensitive data synthesis.

## Understanding RAG Pipelines

A **RAG pipeline** integrates retrieval mechanisms with generative models to produce more accurate and contextually relevant outputs. Here's a [great introduction to the concept of Attention](https://www.3blue1brown.com/lessons/attention) by 3Blue1Brown to get you started. This shows the basics of how we can "embed" information into a smaller, indexible vector. We can then use math (specifically [cosine similarity](https://medium.com/@arjunprakash027/understanding-cosine-similarity-a-key-concept-in-data-science-72a0fcc57599)) to see similarity between vectors, thus providing a way for us to query a database and get related references. 

### Key Components of a RAG Ingest Pipeline

1. **Data Ingestion**
   - **Storage:** Data will be hosted in Amazon S3, a blob storage engine.
   - **Database:** You'll have access to **TimescaleDB**, a PostgreSQL database enhanced with extended vector support for efficient storage and retrieval of embeddings.

2. **Embeddings**
   - Utilize **OpenAI embedding models** to convert textual data into meaningful vector representations.

3. **Retrieval Mechanism**
   - Index and retrieve from vector databases to perform similarity searches, enabling the retrieval of relevant information based on query embeddings.

4. **Generation**
   - Leverage Large Language Models (LLMs) to generate coherent and contextually appropriate responses using the retrieved data.

5. **Optimization**
   - Fine-tune the pipeline by experimenting with different hyperparameters and system configurations to achieve optimal performance. This will likely result in finetuning of the ingest pipeline as well as the query and prompting logic.

## Tools and Technologies

Throughout this project, you will work with a variety of technologies and frameworks, including:

- **Programming Languages:** TypeScript
- **Mathematics:** Linear Algebra
- **AI Technologies:** Large Language Models (LLMs), Embeddings
- **Databases:** TimescaleDB (PostgreSQL with extended vector support)
- **Cloud Services:** Amazon S3
- **APIs:** OpenAI Embedding Models & LLMs

## Project Features

### Continuous Benchmarking System

To foster a competitive and collaborative environment, we have implemented a **continuous benchmarking system** where the two participating teams will compete to optimize their RAG pipelines. This system will provide real-time feedback and performance metrics to help you refine your solutions.

### Data Hosting

All project testing data will be securely hosted in **Amazon S3**, ensuring that you have reliable and scalable access to the datasets required for developing and testing your RAG pipelines.

### Access to OpenAI Embedding Models

Leverage the power of **OpenAI's embedding models** to transform and utilize data effectively within your pipeline, enhancing the quality and relevance of your retrieval and generation processes.

## Meet Your Mentors

**Max Newcomer** | *UW Alum w/ Degrees in Computer Science, Mathematics, and Data Science*

**Sawyer Herbst** | *CEO + Founder of Denari*

## Resources

- 📚 **Attention by 3Blue1Brown:** [Understanding Attention](https://www.3blue1brown.com/lessons/attention)
- 👾 **Cosine Similarity** [Unlocking the Power of Cosine Similarity](https://medium.com/@arjunprakash027/understanding-cosine-similarity-a-key-concept-in-data-science-72a0fcc57599)
- 🛠️ **TimescaleDB Documentation:** [TimescaleDB Docs](https://docs.timescale.com/)
- ☁️ **Amazon S3 Documentation:** [AWS S3 Docs](https://aws.amazon.com/s3/)
- 🤖 **OpenAI Embedding Models:** [OpenAI API](https://beta.openai.com/docs/api-reference/embeddings)

---

*Empowering the next generation of AI innovators in the accounting industry.*

---

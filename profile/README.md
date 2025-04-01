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

# Benchmarking System Integration Guide

This document outlines how your system (Remus or Romulus) will be evaluated using our benchmarking framework.

## Input Format

Your system will receive JSON input via stdin in the following format:

```json
{
  "question": "The full question text goes here?",
  "options": [
    "A. First option",
    "B. Second option",
    "C. Third option",
    "D. Fourth option"
  ]
}
```

## Expected Output Format

Your system should output JSON to stdout in the following format:

```json
{
  "answer": "1",  // A number between 1-4 corresponding to the correct option
  "explanation": "Your detailed explanation of why this answer is correct"
  "citations": ["citation text here", ...]
}
```

Note:
- The `answer` field should be a string with a single number (1, 2, 3, or 4) that corresponds to the option index
- The `explanation` should provide comprehensive reasoning for the selected answer
- the `citations` field should be an array of strings

## Technical Requirements

- **Remus (Python)**: Should implement `main.py` that accepts stdin input and returns JSON output
- **Romulus (TypeScript)**: Should implement `src/index.ts` that accepts stdin input and returns JSON output
- Both systems must handle the complete format exactly as specified above
- Response time will be measured but is not a primary evaluation criterion

## Example

**Input:**
```json
{
  "question": "Which of the following standards-setting bodies has authority to issue auditing standards for financial statement audits of nonissuers?",
  "options": [
    "A. I only",
    "B. II only",
    "C. Both I and II",
    "D. Neither I nor II"
  ]
}
```

**Expected Output:**
```json
{
  "answer": "1",
  "explanation": "The Auditing Standards Board (ASB) has authority to issue auditing standards for nonissuers. While the Public Company Accounting Oversight Board (PCAOB) sets standards for audits of publicly traded entities (issuers), the ASB is responsible for setting standards for nonissuers.",
  "citations": ["...", "..."]
}
```

Training data has been provided to help you understand the question format, correct answers, and expected explanation quality.


# Stdin/Stdout Implementation Examples

## For Romulus (Python)

Here's a minimal implementation example for `main.py`:

```python
import json
import sys

def main():
    # Read JSON input from stdin
    input_data = sys.stdin.read().strip()
    
    try:
        # Parse JSON
        data = json.loads(input_data)
        question = data["question"]
        options = data["options"]
        
        # Your actual implementation would go here
        # This is just a placeholder example
        answer = "1"  # Replace with your actual logic
        explanation = f"This is the explanation for the answer to the question: {question}"
        
        # Format and output JSON response
        response = {
            "answer": answer,
            "explanation": explanation
        }
        
        # Write to stdout
        sys.stdout.write(json.dumps(response))
        sys.stdout.flush()
        
    except Exception as e:
        # Handle errors
        error_response = {
            "error": str(e)
        }
        sys.stderr.write(json.dumps(error_response))
        sys.exit(1)

if __name__ == "__main__":
    main()
```

## For Remus (TypeScript)

Here's a minimal implementation example for `src/index.ts`:

```typescript
import * as readline from 'readline';

interface Question {
  question: string;
  options: string[];
}

interface Response {
  answer: string;
  explanation: string;
}

// Create interface for reading from stdin
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
  terminal: false
});

let inputData = '';

// Read input line by line
rl.on('line', (line) => {
  inputData += line;
});

// Process data when stdin closes
rl.on('close', () => {
  try {
    // Parse JSON
    const data = JSON.parse(inputData) as Question;
    const { question, options } = data;
    
    // Your actual implementation would go here
    // This is just a placeholder example
    const answer = "1";  // Replace with your actual logic
    const explanation = `This is the explanation for the answer to the question: ${question}`;
    
    // Format and output JSON response
    const response: Response = {
      answer,
      explanation
    };
    
    // Write to stdout
    process.stdout.write(JSON.stringify(response));
    
  } catch (error) {
    // Handle errors
    const errorResponse = {
      error: error instanceof Error ? error.message : String(error)
    };
    process.stderr.write(JSON.stringify(errorResponse));
    process.exit(1);
  }
});
```

## Testing Your Implementation

You can test your implementation with these commands:

### For Romulus:
```bash
echo '{"question":"Which of the following is correct?","options":["A. Option 1","B. Option 2","C. Option 3","D. Option 4"]}' | python main.py
```

### For Remus:
```bash
echo '{"question":"Which of the following is correct?","options":["A. Option 1","B. Option 2","C. Option 3","D. Option 4"]}' | npx ts-node src/index.ts
```

The benchmarking system will use this exact mechanism to send questions to your system and receive responses.


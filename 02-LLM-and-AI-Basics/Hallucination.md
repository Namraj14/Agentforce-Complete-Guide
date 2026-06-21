# Hallucinations in AI

## Overview

Hallucination in AI refers to a situation where a model generates information that appears convincing and confident but is factually incorrect, misleading, or completely fabricated.

Hallucinations are one of the biggest challenges in Large Language Models (LLMs) such as ChatGPT, Gemini, Claude, and Agentforce-powered agents.

---

## Definition

A hallucination occurs when an AI model generates content that is not grounded in its training data, retrieved information, or actual facts.

The response may sound correct but contains false information.

---

## Why Do Hallucinations Occur?

LLMs are designed to predict the next token in a sequence based on probabilities.

They do not inherently know what is true or false.

As a result, when sufficient information is unavailable, the model may generate the most probable-looking answer rather than the correct answer.

---

## Example 1

### User Prompt

```text
Who won the FIFA World Cup in 2038?
```

### AI Response

```text
Brazil won the FIFA World Cup 2038.
```

This is a hallucination because the event has not happened yet.

---

## Example 2

### User Prompt

```text
Give me the official Salesforce documentation for XYZ API.
```

### AI Response

```text
Salesforce provides XYZ API under the URL:
https://developer.salesforce.com/docs/xyz-api
```

If such documentation does not exist, the AI has hallucinated the URL.

---

## Example 3

### User Prompt

```text
Who is the CEO of ABC Corporation?
```

### AI Response

```text
John Smith is the CEO of ABC Corporation.
```

If no such company exists or the information is fabricated, it is a hallucination.

---

## Types of Hallucinations

### 1. Factual Hallucination

The model generates incorrect facts.

Example:

```text
The Sun revolves around the Earth.
```

---

### 2. Citation Hallucination

The model invents references, links, articles, or sources.

Example:

```text
According to a Harvard study published in 2025...
```

when no such study exists.

---

### 3. Logical Hallucination

The reasoning process itself is flawed.

Example:

```text
All birds can fly.
Penguins are birds.
Therefore penguins can fly.
```

---

### 4. Data Hallucination

The model invents records, numbers, or data.

Example:

```text
Your organization has 1,247 open cases.
```

when no such data was provided.

---

## Common Causes of Hallucinations

### Insufficient Context

The model lacks enough information to answer accurately.

### Ambiguous Questions

The prompt is unclear or incomplete.

### Missing Knowledge

The required information was not part of training data.

### Probability-Based Generation

The model predicts likely text rather than verifying facts.

### Lack of Grounding

No external source or database is available to validate the answer.

---

## Hallucinations in Agentforce

Consider an Agentforce agent receiving the prompt:

```text
Show the last five opportunities for ABC Corp.
```

### Without Grounding

The AI might generate:

```text
Opportunity A
Opportunity B
Opportunity C
```

even if these records do not exist.

This is a hallucination.

### With Grounding

The agent retrieves actual Salesforce records before generating the response.

```text
Salesforce Data
      ↓
Agent Action
      ↓
LLM Response
```

This significantly reduces hallucinations.

---

## How RAG Helps Prevent Hallucinations

### Without RAG

```text
User Question
      ↓
LLM
      ↓
Answer
```

The model relies only on its training data.

---

### With RAG

```text
User Question
      ↓
Retrieve Relevant Data
      ↓
Provide Context
      ↓
LLM
      ↓
Answer
```

The model generates answers using real retrieved information.

---

## How to Reduce Hallucinations

### Use Grounding

Connect the model to trusted data sources.

### Use RAG

Retrieve relevant information before generating a response.

### Provide Clear Prompts

Specific prompts reduce ambiguity.

### Use Verified Sources

Supply documents, databases, or APIs.

### Implement Validation

Verify outputs before presenting them to users.

### Reduce Temperature

Lower temperatures generally produce more deterministic responses.

---

## Hallucination vs Accuracy

| Scenario | Hallucination Risk |
|-----------|-------------------|
| General Chat | Medium |
| Coding | Medium |
| Legal Advice | High |
| Medical Advice | High |
| Salesforce Data Queries | Low (with grounding) |
| RAG-Based Systems | Lower |

---

## Hallucinations in Salesforce Agentforce

### Without Grounding

```text
User Prompt
      ↓
LLM
      ↓
Generated Answer
```

Risk of hallucination is higher.

---

### With Grounding

```text
User Prompt
      ↓
Agent Action
      ↓
Salesforce Data
      ↓
LLM
      ↓
Response
```

Responses are based on actual records.

---

## Interview Questions and Answers

### 1. What is a Hallucination in AI?

#### Answer

A hallucination occurs when an AI model generates information that appears correct but is actually inaccurate, fabricated, or unsupported by facts.

---

### 2. Why Do LLMs Hallucinate?

#### Answer

LLMs predict the next token based on probabilities and do not inherently verify facts, which can lead to incorrect or fabricated responses.

---

### 3. What Are the Different Types of Hallucinations?

#### Answer

- Factual Hallucinations
- Citation Hallucinations
- Logical Hallucinations
- Data Hallucinations

---

### 4. How Can Hallucinations Be Reduced?

#### Answer

Hallucinations can be reduced using:

- Grounding
- Retrieval-Augmented Generation (RAG)
- Trusted data sources
- Clear prompts
- Output validation

---

### 5. How Does RAG Help Prevent Hallucinations?

#### Answer

RAG retrieves relevant information from trusted sources before the model generates a response, ensuring answers are based on actual data rather than assumptions.

---

### 6. How Does Agentforce Reduce Hallucinations?

#### Answer

Agentforce uses actions, grounding, Salesforce data, Data Cloud, and knowledge sources to provide factual context before generating responses.

---

### 7. What Is the Difference Between a Hallucination and a Wrong Answer?

#### Answer

A wrong answer may result from misunderstanding a question, while a hallucination involves generating fabricated information that appears factual and confident.

---

## Best Practices

- Always ground AI responses with trusted data.
- Use RAG for enterprise AI solutions.
- Validate critical outputs.
- Use lower temperatures for factual applications.
- Avoid relying solely on model memory for business-critical decisions.
- Monitor AI-generated responses in production environments.

---

## Key Takeaways

- Hallucinations are fabricated or incorrect AI-generated outputs.
- They occur because LLMs predict tokens rather than verify facts.
- RAG and grounding significantly reduce hallucinations.
- Agentforce uses Salesforce data and actions to improve accuracy.
- Hallucination prevention is a critical part of enterprise AI design.

---

## One-Line Interview Answer

> Hallucination is the generation of factually incorrect or fabricated information by an AI model while presenting it as a confident and valid response.

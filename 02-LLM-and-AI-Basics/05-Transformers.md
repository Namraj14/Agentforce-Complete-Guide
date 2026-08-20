# Transformers in AI
#### A Transformer is an AI model that understands the relationship between words by looking at all the words in a sentence at the same time. It uses a technique called Attention to identify which words are important and how they are connected.
## Overview

Transformers are a deep learning architecture that powers most modern Artificial Intelligence applications, including Large Language Models (LLMs) such as ChatGPT, Gemini, Claude, and Copilot.

The Transformer architecture was introduced in the 2017 research paper:

**"Attention Is All You Need"**

Transformers revolutionized Natural Language Processing (NLP) by replacing sequential processing with a mechanism called **Self-Attention**, allowing models to process entire sequences simultaneously.

---

# Why Transformers Were Introduced

Before Transformers, AI models primarily used:

- Recurrent Neural Networks (RNNs)
- Long Short-Term Memory Networks (LSTMs)

### Limitations of RNNs and LSTMs

- Process words one at a time
- Slow training
- Difficulty remembering long-range dependencies
- Poor scalability for large datasets

### Advantages of Transformers

- Parallel processing
- Better context understanding
- Faster training
- Handles long-range dependencies
- Scales to billions of parameters

---

# Real-World Example

Sentence:

> The animal didn't cross the street because it was too tired.

Question:

What does **"it"** refer to?

A Transformer uses attention mechanisms to understand that **"it"** refers to **"animal"** rather than **"street"**.

---

# Transformer Architecture

```text
Input Text
    ↓
Tokenization
    ↓
Embeddings
    ↓
Positional Encoding
    ↓
Multi-Head Attention
    ↓
Feed Forward Network
    ↓
Transformer Layers
    ↓
Output Prediction
```

---

# Core Components of Transformers

## 1. Tokenization

Text is broken into smaller units called tokens.

Example:

```text
I love Salesforce
```

Tokens:

```text
["I", "love", "Salesforce"]
```

### Purpose

- Converts text into machine-readable units
- First step before processing

---

## 2. Embeddings

Tokens are converted into numerical vectors.

Example:

```text
"I"          → [0.2, 0.8, ...]
"love"       → [0.5, 0.1, ...]
"Salesforce" → [0.9, 0.3, ...]
```

### Purpose

Represent words mathematically while preserving semantic meaning.

---

## 3. Positional Encoding

Transformers process all words simultaneously.

To understand word order, positional information is added.

Example:

```text
Dog bites man
```

vs

```text
Man bites dog
```

Same words, different meanings.

### Purpose

Helps the model understand token positions.

---

## 4. Self-Attention

The most important component of a Transformer.

Every word looks at every other word and decides:

- Which words are important?
- How much importance should be given?

### Example

```text
Salesforce developers write Apex code.
```

When processing "Apex", attention may focus on:

- Salesforce
- developers
- code

This helps understand context.

---

# Query, Key, and Value (QKV)

Self-attention is built using:

## Query (Q)

What information am I looking for?

## Key (K)

What information do I contain?

## Value (V)

What information should I provide?

### Attention Formula

```text
Attention(Q,K,V)
=
softmax(Q × Kᵀ / √dk) × V
```

---

# Example of Attention

Sentence:

```text
The cat sat on the mat.
```

When processing:

```text
cat
```

The model may attend to:

```text
sat
mat
```

to understand relationships.

---

# Multi-Head Attention

Instead of one attention mechanism, multiple attention heads operate simultaneously.

Example:

```text
Head 1 → Grammar
Head 2 → Meaning
Head 3 → Relationships
Head 4 → Context
Head 5 → Sentiment
```

### Benefits

- Learns multiple patterns
- Better language understanding
- Improved contextual awareness

---

# Feed Forward Network (FFN)

After attention calculations, data passes through a neural network.

### Purpose

- Extract deeper patterns
- Improve feature representation
- Learn complex relationships

---

# Encoder and Decoder

## Encoder

Responsible for understanding input.

Example Models:

- BERT
- RoBERTa

Tasks:

- Classification
- Search
- Sentiment Analysis

---

## Decoder

Responsible for generating output.

Example Models:

- GPT
- ChatGPT

Tasks:

- Text Generation
- Code Generation
- Conversations

---

# Encoder-Decoder Architecture

Used for sequence-to-sequence tasks.

Examples:

- T5
- BART

Tasks:

- Translation
- Summarization
- Question Answering

---

# Types of Transformer Models

| Type | Example Models | Purpose |
|--------|----------------|----------|
| Encoder Only | BERT, RoBERTa | Understanding Text |
| Decoder Only | GPT, Llama | Text Generation |
| Encoder-Decoder | T5, BART | Translation & Summarization |

---

# Training Process

## Step 1

Collect large datasets.

Example:

- Books
- Websites
- Articles
- Code Repositories

---

## Step 2

Tokenize data.

---

## Step 3

Generate embeddings.

---

## Step 4

Train attention layers.

---

## Step 5

Optimize using backpropagation.

---

## Step 6

Fine-tune for specific tasks.

Examples:

- Chatbots
- Search Engines
- Coding Assistants

---

# Why Transformers Are Powerful

✅ Parallel Processing

✅ Better Context Understanding

✅ Long-Term Dependency Learning

✅ Highly Scalable

✅ Supports Multi-Modal AI

---

# Transformers in Large Language Models (LLMs)

Modern LLMs are built using Transformer architecture.

Examples:

- GPT Series
- Claude
- Gemini
- Llama
- Mistral

Workflow:

```text
User Prompt
      ↓
Tokenization
      ↓
Transformer Layers
      ↓
Attention Calculation
      ↓
Context Understanding
      ↓
Response Generation
```

---

# Transformers in Salesforce Agentforce

When a user asks:

```text
Show all open cases for Account ABC and summarize them.
```

The process is:

```text
User Prompt
      ↓
Transformer Processes Input
      ↓
Agent Understands Intent
      ↓
Action Invoked
      ↓
Salesforce Data Retrieved
      ↓
Transformer Generates Response
```

---

# Transformers vs RNN vs LSTM

| Feature | RNN | LSTM | Transformer |
|----------|------|------|-------------|
| Parallel Processing | ❌ | ❌ | ✅ |
| Long Context Handling | ❌ | Medium | ✅ |
| Training Speed | Slow | Slow | Fast |
| Scalability | Low | Medium | Very High |
| Used in Modern LLMs | ❌ | ❌ | ✅ |

---

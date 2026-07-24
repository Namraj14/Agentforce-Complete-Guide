# Embeddings in RAG (Complete Beginner to Advanced Guide)

# Table of Contents

1. What is an Embedding?
2. Why Do We Need Embeddings?
3. How Embeddings Fit into RAG
4. What is an Embedding Model?
5. How Embeddings are Generated
6. Understanding Vectors
7. High-Dimensional Space
8. Semantic Similarity
9. Embeddings During Data Ingestion
10. Embeddings During Retrieval
11. Types of Embeddings
12. Similarity Search
13. Embedding Dimensions
14. Popular Embedding Models
15. Best Practices
16. Real-Time Examples
17. Salesforce Agentforce Example
18. Interview Questions

---

# Before Understanding Embeddings

Let's remember what happens in RAG.

```
Large Document

↓

Chunking

↓

Embeddings

↓

Vector Database

↓

Retrieval

↓

LLM

↓

Answer
```

Embeddings are created **after chunking** and **before storing data in the Vector Database**.

Without embeddings...

The Vector Database cannot understand meaning.

---

# What is an Embedding?

An **Embedding** is a numerical representation of text that captures its meaning.

Instead of storing text directly for semantic search,

the text is converted into numbers.

Example

```
Text

Employees receive 20 casual leaves.

↓

Embedding

[0.42, -0.18, 0.91, 0.37, ...]
```

These numbers represent the **meaning** of the sentence.

---

# Simple Definition

> An embedding is a vector (list of numbers) that represents the semantic meaning of text, allowing computers to compare meanings instead of exact words.

---

# Why Do We Need Embeddings?

Computers cannot understand language like humans.

They understand numbers.

Suppose a document says

```
Warranty = 2 Years
```

The user asks

```
How long is the product covered?
```

Notice

The words are different.

```
Warranty

Covered
```

But the meaning is the same.

Embeddings convert both sentences into vectors that are close together.

---

# Real-Life Analogy

Imagine Google Maps.

Every city has coordinates.

Example

```
Mumbai

↓

Latitude

↓

Longitude
```

Similarly,

every sentence gets coordinates.

Example

```
Leave Policy

↓

[0.82, -0.31, 0.54...]
```

These are not GPS coordinates.

These are **semantic coordinates**.

Instead of representing location,

they represent meaning.

---

# What is an Embedding Model?

An Embedding Model is an AI model that converts text into embeddings.

Pipeline

```
Sentence

↓

Embedding Model

↓

Vector
```

Example

```
Employees receive
20 casual leaves.

↓

Embedding Model

↓

[0.42, -0.18, 0.91...]
```

The embedding model understands the meaning of the sentence and generates the vector.

---

# Important Difference

Many beginners think:

```
LLM

↓

Embeddings
```

This is not usually correct.

Instead,

```
Embedding Model

↓

Embeddings

↓

Vector Database

↓

LLM
```

The embedding model and the LLM are often **two different models**.

---

# How Embeddings are Generated

Suppose we have

```
Employees receive
20 casual leaves.
```

Step 1

Read the text.

↓

Step 2

Analyze its meaning.

↓

Step 3

Convert it into a vector.

↓

Step 4

Store it in the Vector Database.

Result

```
Employees receive
20 casual leaves.

↓

[0.42, -0.18, 0.91...]
```

---

# What is a Vector?

A vector is simply a list of numbers.

Example

```
Cat

↓

[0.12, 0.83, -0.41...]

Dog

↓

[0.11, 0.80, -0.39...]

Car

↓

[-0.88, 0.20, 0.73...]
```

Notice

Cat and Dog have similar vectors.

Car is very different.

Why?

Because the meanings are different.

---

# High-Dimensional Space

Embeddings are not just 3 or 4 numbers.

Modern embedding models produce vectors with hundreds or thousands of values.

Example

```
[0.12,
0.83,
-0.41,
0.74,
...
1536 values]
```

Each value represents one learned feature of the text.

Humans cannot interpret each individual number.

The model learns these patterns during training.

---

# Semantic Similarity

This is the biggest advantage of embeddings.

Example

Sentence 1

```
Product warranty lasts two years.
```

Sentence 2

```
The product is covered for two years.
```

Different words.

Same meaning.

The embedding model generates vectors that are very close together.

Another example

```
Apple is a fruit.
```

```
Car engine needs oil.
```

Completely different meanings.

Their vectors are far apart.

---

# Embeddings During Data Ingestion

During the Data Ingestion Pipeline,

every chunk gets an embedding.

```
Chunk 1

↓

Embedding

↓

Store

----------------

Chunk 2

↓

Embedding

↓

Store

----------------

Chunk 3

↓

Embedding

↓

Store
```

Now every chunk has its own semantic representation.

---

# Embeddings During Retrieval

When a user asks a question,

the same embedding model converts the question into a vector.

Example

```
Question

How many casual leaves do employees get?

↓

Embedding

↓

[0.41, -0.20, 0.88...]
```

The Vector Database compares this vector with stored vectors.

The closest vectors are retrieved.

---

# Complete Flow

```
Data Ingestion

Document

↓

Chunk

↓

Embedding Model

↓

Embedding

↓

Vector Database

================================

Retrieval

User Question

↓

Embedding Model

↓

Question Embedding

↓

Vector Database

↓

Similarity Search

↓

Relevant Chunks

↓

LLM

↓

Answer
```

---

# Types of Embeddings

There are different embedding models for different types of data.

### Text Embeddings

Used for

- Documents
- PDFs
- Emails
- Knowledge Articles

---

### Image Embeddings

Used for

- Photos
- Medical Images
- Product Images

---

### Audio Embeddings

Used for

- Speech
- Voice Recognition

---

### Video Embeddings

Used for

- Video Search
- Video Recommendations

---

# Similarity Search

The Vector Database compares vectors.

Not text.

Example

Stored Embeddings

```
Chunk A

[0.11, 0.42...]

Chunk B

[0.82, -0.11...]

Chunk C

[-0.65, 0.73...]
```

Question

```
[0.12, 0.40...]
```

The closest vector is

```
Chunk A
```

So Chunk A is retrieved.

---

# Embedding Dimensions

Every embedding model produces vectors of a fixed size.

Examples

```
384 Dimensions

768 Dimensions

1024 Dimensions

1536 Dimensions

3072 Dimensions
```

Dimension means

How many numbers exist inside one vector.

Example

```
4 Dimensions

[0.42, 0.13, -0.88, 0.72]
```

Example

```
1536 Dimensions

[0.42, 0.13, -0.88, ...1536 numbers]
```

Higher dimensions generally allow the model to capture more nuanced semantic relationships, but they also require more storage and computation.

---

# Popular Embedding Models

Some widely used embedding models include:

- OpenAI text-embedding models
- Sentence Transformers (Hugging Face)
- Cohere Embeddings
- Google Embedding Models
- Voyage AI Embeddings
- Amazon Titan Embeddings

Each model generates embeddings with its own architecture and vector dimensions.

---

# Best Practices

- Use the **same embedding model** during ingestion and retrieval.
- Chunk documents before generating embeddings.
- Store metadata along with embeddings.
- Choose an embedding model appropriate for your language and domain.
- Regenerate embeddings if documents change significantly.

---

# Common Mistakes

### Different Embedding Models

Wrong

```
Store

Model A

Search

Model B
```

Because vectors from different models usually live in different vector spaces and may not be comparable.

---

### Embedding Entire Documents

Wrong

```
500-page PDF

↓

One Embedding
```

Better

```
500-page PDF

↓

Chunk

↓

Embeddings
```

---

### Poor Chunking

Poor chunks

↓

Poor embeddings

↓

Poor retrieval

---

# Real-Time Example

Document

```
Employees receive
20 casual leaves.
```

Chunk

↓

Embedding

↓

```
[0.42, -0.18, 0.91...]
```

Stored inside the Vector Database.

Question

```
How many casual leaves do employees get?
```

↓

Embedding

↓

Similarity Search

↓

Retrieve Matching Chunk

↓

LLM

↓

Answer

```
Employees receive 20 casual leaves annually.
```

---

# Salesforce Agentforce Example

Knowledge Article

```
How to Reset Router
```

↓

Chunk

↓

Embedding

↓

Store in Vector Database

Customer asks

```
My router isn't working.
How do I restart it?
```

↓

Question Embedding

↓

Similarity Search

↓

Retrieve

```
How to Reset Router
```

↓

LLM

↓

Generate Answer

---

# Complete Architecture

```
Documents
      │
      ▼
Chunking
      │
      ▼
Embedding Model
      │
      ▼
Embeddings
      │
      ▼
Vector Database
      │
      ▼
User Question
      │
      ▼
Embedding Model
      │
      ▼
Question Embedding
      │
      ▼
Similarity Search
      │
      ▼
Relevant Chunks
      │
      ▼
LLM
      │
      ▼
Final Answer
```

---

# Interview Questions

## What is an Embedding?

> An embedding is a numerical vector representation of text that captures its semantic meaning. It allows computers to compare the meanings of different pieces of text instead of matching exact keywords.

---

## Why Do We Need Embeddings?

> Embeddings enable semantic search. They convert text into vectors so that similar meanings are placed close together in vector space, allowing relevant information to be retrieved even when different words are used.

---

## What is an Embedding Model?

> An embedding model is an AI model that converts text into numerical vectors (embeddings) while preserving semantic meaning.

---

## Why Must the Same Embedding Model Be Used?

> The same embedding model should be used during both data ingestion and retrieval because embeddings generated by different models are generally not directly comparable.

---

## What is the Difference Between an Embedding and a Vector?

Practically, they are often used interchangeably in RAG.

- **Vector**: Any list of numbers.
- **Embedding**: A vector specifically created to represent the semantic meaning of data.

So:

> **Every embedding is a vector, but not every vector is an embedding.**

---

# Quick Revision

```
Document
      │
      ▼
Chunking
      │
      ▼
Embedding Model
      │
      ▼
Embeddings
      │
      ▼
Vector Database
      │
      ▼
Question
      │
      ▼
Embedding Model
      │
      ▼
Question Embedding
      │
      ▼
Similarity Search
      │
      ▼
Relevant Chunks
      │
      ▼
LLM
      │
      ▼
Answer
```

---

# One-Line Summary

> **An embedding is a numerical vector representation of data that captures its semantic meaning. In RAG, embedding models convert both document chunks and user queries into vectors, enabling vector databases to perform semantic similarity searches and retrieve the most relevant information for the LLM.**

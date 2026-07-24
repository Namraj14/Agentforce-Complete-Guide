# RAG Architecture (Complete Beginner to Advanced Guide)

# Table of Contents

1. What is RAG Architecture?
2. Why Do We Need RAG Architecture?
3. High-Level RAG Architecture
4. Components of RAG Architecture
5. Offline Flow (Data Ingestion Pipeline)
6. Online Flow (Retrieval Pipeline)
7. End-to-End RAG Flow
8. Complete Architecture Explanation
9. Real-Time Example
10. Salesforce Agentforce Example
11. Advantages
12. Challenges
13. Interview Questions

---

# Before Understanding RAG Architecture

By now, we already know these concepts:

- Documents
- Chunking
- Embeddings
- Embedding Model
- Vector Database
- Retrieval
- LLM

Now the question is...

**How do all these components work together?**

The answer is:

**RAG Architecture**

Think of RAG Architecture as the **blueprint** that shows how every component works together to answer a user's question.

---

# What is RAG Architecture?

**RAG (Retrieval-Augmented Generation) Architecture** is the complete workflow that combines:

- Data Ingestion
- Embeddings
- Vector Database
- Retrieval
- Large Language Model (LLM)

to generate accurate and context-aware responses.

---

# Simple Definition

> RAG Architecture is the end-to-end system that prepares knowledge, retrieves the most relevant information, and uses an LLM to generate accurate answers.

---

# Why Do We Need RAG Architecture?

Imagine asking ChatGPT:

```
What is my company's leave policy?
```

ChatGPT doesn't know your company's internal documents.

Instead of guessing,

RAG Architecture performs these steps:

```
Find the document

↓

Retrieve the correct section

↓

Give it to the LLM

↓

Generate the answer
```

Without RAG

```
User

↓

LLM

↓

May Guess
```

With RAG

```
User

↓

Knowledge Base

↓

LLM

↓

Accurate Answer
```

---

# High-Level RAG Architecture

```
                    RAG ARCHITECTURE

              OFFLINE (Preparation)

Documents
      │
      ▼
Load Documents
      │
      ▼
Cleaning
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

==========================================

               ONLINE (Question Time)

User Question
      │
      ▼
Embedding Model
      │
      ▼
Question Embedding
      │
      ▼
Vector Database
      │
      ▼
Similarity Search
      │
      ▼
Top-K Retrieval
      │
      ▼
(Optional) Re-ranking
      │
      ▼
Relevant Chunks
      │
      ▼
Prompt Augmentation
      │
      ▼
LLM
      │
      ▼
Final Answer
```

---

# Components of RAG Architecture

Every RAG system contains these major components.

## 1. Knowledge Source

The source of information.

Examples

- PDFs
- Word Documents
- Websites
- Salesforce Knowledge Articles
- SharePoint
- Confluence
- Databases
- Emails

---

## 2. Data Ingestion Pipeline

The pipeline that prepares documents before users ask questions.

Responsibilities

- Load documents
- Clean documents
- Split into chunks
- Generate embeddings
- Store vectors

This pipeline runs **offline**.

---

## 3. Embedding Model

Converts text into vectors.

Example

```
Leave Policy

↓

Embedding Model

↓

[0.42, -0.18, 0.91...]
```

Both document chunks and user questions use the same embedding model.

---

## 4. Vector Database

Stores

- Embeddings
- Original chunks
- Metadata

Its job is to perform semantic similarity search.

Popular vector databases

- Pinecone
- Milvus
- Qdrant
- Weaviate
- Chroma
- PostgreSQL + pgvector

---

## 5. Retrieval Engine

Responsible for

- Similarity Search
- Metadata Filtering
- Top-K Retrieval
- Re-ranking

Its job is to find the most relevant chunks.

---

## 6. Prompt Augmentation

This is where **RAG gets its name ("Augmented")**.

The retrieved chunks are added to the user's prompt.

Instead of sending

```
Question
```

we send

```
Context

+

Question
```

Example

```
Context

Employees receive 20 casual leaves.

Question

How many casual leaves do employees get?
```

Now the LLM has the required knowledge.

---

## 7. Large Language Model (LLM)

The LLM reads

- User Question
- Retrieved Context

and generates a natural language answer.

Examples

- GPT
- Claude
- Gemini
- Llama
- Mistral

Notice

The LLM does **not** search the documents.

It only generates the response using the retrieved context.

---

# Offline Flow (Data Ingestion Pipeline)

This happens before any user asks a question.

```
Knowledge Sources
      │
      ▼
Load Documents
      │
      ▼
Cleaning
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
```

Purpose

Prepare all knowledge for fast retrieval.

---

# Online Flow (Retrieval Pipeline)

This happens every time a user asks a question.

```
User Question
      │
      ▼
Embedding Model
      │
      ▼
Question Embedding
      │
      ▼
Vector Database
      │
      ▼
Similarity Search
      │
      ▼
Retrieve Chunks
      │
      ▼
Prompt Augmentation
      │
      ▼
LLM
      │
      ▼
Answer
```

Purpose

Retrieve relevant knowledge and answer the user's question.

---

# End-to-End RAG Flow

```
STEP 1

Documents

↓

STEP 2

Chunk Documents

↓

STEP 3

Generate Embeddings

↓

STEP 4

Store in Vector Database

====================================

STEP 5

User Asks Question

↓

STEP 6

Generate Question Embedding

↓

STEP 7

Search Vector Database

↓

STEP 8

Retrieve Relevant Chunks

↓

STEP 9

Augment Prompt

↓

STEP 10

LLM Generates Final Answer
```

---

# Complete Architecture

```
                  KNOWLEDGE SOURCES
        (PDFs, Docs, Websites, Knowledge)

                     │
                     ▼
              Data Ingestion Pipeline
                     │
                     ▼
                 Load Documents
                     │
                     ▼
                   Cleaning
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
========================================================
                     │
                User Question
                     │
                     ▼
               Embedding Model
                     │
                     ▼
             Question Embedding
                     │
                     ▼
               Vector Database
                     │
                     ▼
              Similarity Search
                     │
                     ▼
              Top-K Retrieval
                     │
                     ▼
           (Optional) Re-ranking
                     │
                     ▼
             Relevant Chunks
                     │
                     ▼
            Prompt Augmentation
                     │
                     ▼
             Large Language Model
                     │
                     ▼
               Final Response
```

---

# Real-Time Example

Knowledge Base

```
HR Policy.pdf

Travel Policy.pdf

Laptop Policy.pdf
```

A user asks

```
How many casual leaves do employees get?
```

The RAG Architecture performs

```
Question

↓

Question Embedding

↓

Vector Search

↓

Retrieve

HR Policy Chunk

↓

Prompt Augmentation

↓

LLM

↓

Employees receive 20 casual leaves annually.
```

---

# Salesforce Agentforce Example

Knowledge Articles

```
Router Reset

Warranty

Returns

Shipping

Installation
```

Customer asks

```
How do I reset my router?
```

Architecture

```
Question

↓

Embedding Model

↓

Vector Database

↓

Retrieve

Router Reset Guide

↓

Prompt Augmentation

↓

LLM

↓

Generate Answer
```

---

# Advantages

- Reduces hallucinations
- Uses real company data
- Supports private knowledge
- Retrieves only relevant information
- Lower token usage
- More accurate answers
- Easy to update knowledge without retraining the LLM

---

# Challenges

- Poor chunking reduces retrieval quality
- Wrong embedding model affects similarity search
- Bad metadata limits filtering
- Outdated documents lead to outdated answers
- Large vector databases require efficient indexing

---

# Interview Questions

## What is RAG Architecture?

> RAG Architecture is an end-to-end AI system that combines data ingestion, embeddings, vector databases, retrieval, prompt augmentation, and a Large Language Model (LLM) to generate accurate answers using external knowledge.

---

## What are the two major pipelines in RAG?

1. **Data Ingestion Pipeline (Offline)** – Prepares documents by chunking them, generating embeddings, and storing them in a vector database.

2. **Retrieval Pipeline (Online)** – Converts the user's question into an embedding, retrieves relevant chunks from the vector database, augments the prompt, and sends it to the LLM.

---

## What is Prompt Augmentation?

> Prompt augmentation is the process of adding the retrieved context to the user's question before sending it to the LLM. This enables the LLM to answer using relevant external knowledge.

---

## Does the LLM Search the Database?

No.

The Vector Database performs the search.

The LLM only generates the answer using the retrieved context.

---

## Why is RAG Better Than Using Only an LLM?

Because RAG allows the LLM to use up-to-date, private, and domain-specific information instead of relying only on its training data.

---

# Quick Revision

```
Knowledge Sources
        │
        ▼
Data Ingestion Pipeline
        │
        ▼
Chunking
        │
        ▼
Embedding Model
        │
        ▼
Vector Database

===============================

User Question
        │
        ▼
Embedding Model
        │
        ▼
Vector Database
        │
        ▼
Retrieval
        │
        ▼
Prompt Augmentation
        │
        ▼
LLM
        │
        ▼
Answer
```

---

# One-Line Summary

> **RAG Architecture is the complete end-to-end workflow that prepares knowledge through the data ingestion pipeline, retrieves relevant information through the retrieval pipeline, augments the user's prompt with that information, and enables an LLM to generate accurate, context-aware responses.**

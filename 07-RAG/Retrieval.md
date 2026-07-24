# Retrieval in RAG (Complete Beginner to Advanced Guide)

# Table of Contents

1. What is Retrieval?
2. Why is Retrieval Needed?
3. How Retrieval Fits into RAG
4. Retrieval Pipeline
5. Step-by-Step Explanation
6. Similarity Search
7. Top-K Retrieval
8. Metadata Filtering
9. Re-ranking
10. Types of Retrieval
11. Retrieval Strategies
12. Challenges
13. Real-Time Example
14. Salesforce Agentforce Example
15. Interview Questions

---

# What is Retrieval?

**Retrieval** is the process of finding the **most relevant information** from a knowledge base before sending it to the Large Language Model (LLM).

Remember:

RAG stands for

```
Retrieval
Augmented
Generation
```

The **R** in RAG is Retrieval.

---

# Simple Definition

> Retrieval is the process of searching a knowledge base and returning the most relevant documents or chunks related to a user's question.

---

# Think of a Librarian

Imagine you're in a library.

You ask:

```
Where can I learn about Java?
```

The librarian doesn't explain Java.

Instead, the librarian

- Searches the shelves
- Finds the best books
- Gives them to you

The librarian is performing **Retrieval**.

The librarian is **NOT** teaching.

The teacher (LLM) teaches after reading the books.

```
User

↓

Librarian (Retrieval)

↓

Books

↓

Teacher (LLM)

↓

Answer
```

---

# Why is Retrieval Needed?

Imagine asking ChatGPT:

```
What is my company's leave policy?
```

Can ChatGPT know this?

No.

Because your company's documents were never part of its training.

So the system first searches:

```
HR Policy.pdf
```

Finds:

```
Employees receive 20 casual leaves.
```

Then sends that information to the LLM.

Without retrieval

```
LLM

↓

Guess
```

With retrieval

```
LLM

↓

Answer using company documents
```

---

# Where Does Retrieval Fit?

```
                RAG

User Question
      │
      ▼
Retrieval
(Search)
      │
      ▼
Relevant Chunks
      │
      ▼
Augmentation
(Add Context)
      │
      ▼
LLM
      │
      ▼
Generate Answer
```

Notice

Retrieval happens **before** the LLM generates an answer.

---

# Complete Retrieval Pipeline

```
User Question
      │
      ▼
Generate Question Embedding
      │
      ▼
Search Vector Database
      │
      ▼
Find Similar Vectors
      │
      ▼
Retrieve Best Chunks
      │
      ▼
(Optional) Re-rank Results
      │
      ▼
Send Context to LLM
      │
      ▼
Generate Final Answer
```

---

# Step 1 - User Asks a Question

Example

```
How many casual leaves do employees get?
```

---

# Step 2 - Convert Question into an Embedding

The question is converted into a vector.

```
Question

↓

Embedding Model

↓

[0.42, -0.18, 0.91...]
```

Why?

Because vector databases compare vectors, not text.

---

# Step 3 - Search the Vector Database

The Vector Database already contains embeddings created during the Data Ingestion Pipeline.

Example

```
Chunk 1

Employees receive
20 casual leaves.

Chunk 2

Laptop policy

Chunk 3

Travel reimbursement
```

Each chunk has its own embedding.

The database compares the question embedding with every stored embedding.

---

# Step 4 - Similarity Search

The Vector Database calculates which chunks are most similar.

Example

Question

```
Leave Policy
```

Results

```
Chunk 1

95% Similar

Chunk 2

42% Similar

Chunk 3

18% Similar
```

The closest chunk is selected.

This is called **Semantic Search** because it searches by meaning, not exact words.

---

# Step 5 - Retrieve the Best Chunks

The retrieved chunk is returned.

Example

```
Employees receive 20 casual leaves.
```

Notice

The system retrieves the original text, not the vector.

The vector is only used for searching.

---

# Step 6 - Re-ranking (Optional)

Sometimes the search returns several good chunks.

Example

```
Chunk A

92%

Chunk B

91%

Chunk C

89%
```

A re-ranking model examines them more carefully and changes the order.

Example

Before

```
Chunk A

Chunk B

Chunk C
```

After Re-ranking

```
Chunk B

Chunk A

Chunk C
```

Only the best chunks are sent to the LLM.

---

# Step 7 - Send Context to the LLM

The retrieved chunks are added to the prompt.

Example

```
Context

Employees receive 20 casual leaves.

Question

How many casual leaves do employees get?
```

---

# Step 8 - Generate Final Answer

The LLM reads the retrieved context and responds.

```
Employees receive 20 casual leaves per year.
```

---

# What is Similarity Search?

Similarity Search compares meanings rather than exact words.

Example

Question

```
How long is Product X covered?
```

Document

```
Warranty = 2 Years
```

The words are different.

The meaning is the same.

A Vector Database understands this using embeddings.

---

# What is Top-K Retrieval?

The system usually retrieves **more than one** chunk.

Instead of returning only one result, it returns the top K results.

Example

```
Top 3 Results

1.

Warranty

2.

Return Policy

3.

Support Contact
```

If K = 5

The system retrieves the five most relevant chunks.

Common values

```
Top 3

Top 5

Top 10
```

---

# Metadata Filtering

Sometimes similarity alone isn't enough.

Suppose your company has two HR policies.

```
India HR Policy

US HR Policy
```

The user asks

```
Show the India leave policy.
```

Metadata can filter the search.

Example

```
Department = HR

Country = India

Year = 2025
```

The Vector Database searches only matching documents.

---

# Re-ranking

Similarity search is fast.

But sometimes the best result isn't ranked first.

A Re-ranking Model performs a second, more accurate ranking.

Pipeline

```
Similarity Search

↓

Top 20 Results

↓

Re-ranking

↓

Best 5 Results

↓

LLM
```

This improves answer quality.

---

# Types of Retrieval

## 1. Dense Retrieval

Uses embeddings.

Searches by meaning.

Most modern RAG systems use this.

---

## 2. Sparse Retrieval

Uses keywords.

Example

```
BM25

TF-IDF
```

Good for exact keyword matches.

---

## 3. Hybrid Retrieval

Combines both.

```
Keyword Search

+

Vector Search
```

Many enterprise RAG systems use Hybrid Retrieval because it balances exact matches and semantic understanding.

---

# Retrieval Strategies

Different RAG applications retrieve information differently.

### Single Retrieval

Retrieve once.

```
Question

↓

Search

↓

Answer
```

---

### Multi-Step Retrieval

Retrieve multiple times.

Example

```
Question

↓

Search

↓

Find Related Document

↓

Search Again

↓

Answer
```

Useful for complex questions.

---

### Multi-Query Retrieval

The system rewrites the user's question into several versions.

Example

```
Warranty

↓

Coverage

↓

Guarantee
```

Each version is searched.

Results are combined.

---

# Common Challenges

## Poor Chunking

If chunks are too large,

retrieval quality decreases.

---

## Wrong Embeddings

Bad embeddings

↓

Wrong search results.

---

## Missing Metadata

Without metadata,

filtering becomes difficult.

---

## Outdated Documents

Old documents

↓

Old answers.

---

# Real-Time Example

Knowledge Base

```
HR Policy

Employees receive 20 casual leaves.

Laptop Policy

Every employee gets one laptop.

Travel Policy

Travel reimbursement is available.
```

Question

```
How many casual leaves do I get?
```

Retrieval

```
Generate Embedding

↓

Similarity Search

↓

Retrieve

Employees receive 20 casual leaves.
```

LLM

```
Employees receive 20 casual leaves annually.
```

---

# Salesforce Agentforce Example

Customer asks

```
How do I reset my router?
```

Retrieval

```
Generate Question Embedding

↓

Search Salesforce Knowledge

↓

Retrieve

Router Reset Guide

↓

Send Guide to LLM
```

LLM

```
Here are the steps to reset your router...
```

---

# Complete Retrieval Architecture

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
Top-K Retrieval
      │
      ▼
Metadata Filtering
      │
      ▼
Re-ranking
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
Generate Answer
```

---

# Interview Questions

## What is Retrieval?

> Retrieval is the process of searching a knowledge base and fetching the most relevant documents or chunks based on the user's query before sending them to the LLM.

---

## What is Similarity Search?

> Similarity Search compares embeddings to find documents with meanings that are closest to the user's question rather than matching exact keywords.

---

## What is Top-K Retrieval?

> Top-K Retrieval returns the K most relevant chunks instead of only one. The retrieved chunks are then used to generate the final response.

---

## What is Re-ranking?

> Re-ranking is a second-stage ranking process that improves the order of retrieved results before they are sent to the LLM.

---

## Difference Between Retrieval and Generation

| Retrieval | Generation |
|-----------|------------|
| Finds information | Creates the answer |
| Uses Vector Database | Uses LLM |
| Returns relevant chunks | Returns natural language |
| Happens before LLM | Happens inside the LLM |

---

# Quick Revision

```
User Question
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
Metadata Filtering
      │
      ▼
Re-ranking
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

# One-Line Summary

> **Retrieval is the process of finding the most relevant information from a knowledge base using semantic similarity search, filtering, and ranking, then passing that information to the LLM so it can generate an accurate answer.**

# Chunking in RAG (Complete Beginner to Advanced Guide)

# Table of Contents

1. What is Chunking?
2. Why is Chunking Needed?
3. How Chunking Fits into RAG
4. Chunking in the Data Ingestion Pipeline
5. How Chunking Works
6. Types of Chunking
7. Chunk Overlap
8. Chunk Size
9. Best Practices
10. Challenges
11. Real-Time Examples
12. Salesforce Example
13. Interview Questions

---

# What is Chunking?

**Chunking** is the process of breaking a large document into smaller, meaningful pieces called **chunks**.

Instead of storing an entire document as one large block, we divide it into multiple smaller sections.

---

# Simple Definition

> Chunking is the process of splitting a large document into smaller pieces so that a RAG system can retrieve only the relevant information instead of the entire document.

---

# Why is Chunking Needed?

Imagine you have a PDF with **500 pages**.

A user asks:

```
How many casual leaves do employees get?
```

Should we send all 500 pages to the LLM?

No.

Why?

- Too much unnecessary information
- Slower processing
- Higher token cost
- Lower accuracy
- Context window limitations

Instead, we retrieve only the relevant section.

---

# Real-Life Analogy

Imagine you're reading a book.

Someone asks:

```
What is the capital of Nepal?
```

Would you hand over the entire book?

No.

You would open the page that contains the answer.

That page is similar to a **chunk**.

```
Entire Book

↓

Relevant Page

↓

Answer
```

---

# How Chunking Fits into RAG

Chunking happens during the **Data Ingestion Pipeline**.

```
Documents
      │
      ▼
Load Documents
      │
      ▼
Clean Documents
      │
      ▼
Chunk Documents
      │
      ▼
Generate Embeddings
      │
      ▼
Store in Vector Database
```

Notice

Chunking happens **before embeddings are generated**.

---

# Why Before Embeddings?

Imagine a document with 300 pages.

If we create one embedding for the entire document,

the embedding represents **everything**.

Later, when someone asks

```
Leave Policy
```

the embedding is too general.

Instead

```
Chunk 1

Leave Policy

↓

Embedding

Chunk 2

Travel Policy

↓

Embedding

Chunk 3

Laptop Policy

↓

Embedding
```

Now each chunk has its own meaning.

This makes retrieval much more accurate.

---

# How Chunking Works

Suppose your document contains

```
Employee Handbook

Page 1

Company Introduction

Page 2

Leave Policy

Page 3

Travel Policy

Page 4

Laptop Policy
```

After chunking

```
Chunk 1

Company Introduction

Chunk 2

Leave Policy

Chunk 3

Travel Policy

Chunk 4

Laptop Policy
```

Each chunk gets its own embedding.

---

# Complete Flow

```
Large Document

↓

Split into Chunks

↓

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

---

# Types of Chunking

There are several ways to split documents.

---

## 1. Fixed-Size Chunking

The document is split after a fixed number of words or tokens.

Example

```
Chunk Size = 500 words

Chunk 1

Words 1–500

Chunk 2

Words 501–1000

Chunk 3

Words 1001–1500
```

### Advantages

- Very simple
- Fast
- Easy to implement

### Disadvantages

- May cut a sentence in half
- Can lose context

---

## 2. Sentence-Based Chunking

Split after complete sentences.

Example

```
Sentence 1

Sentence 2

Sentence 3

↓

Chunk
```

Advantages

- Preserves complete thoughts
- Easier for the LLM to understand

---

## 3. Paragraph-Based Chunking

Each paragraph becomes a chunk.

Example

```
Paragraph 1

↓

Chunk 1

Paragraph 2

↓

Chunk 2
```

Useful when each paragraph discusses a different topic.

---

## 4. Semantic Chunking (Most Intelligent)

Instead of counting words,

the system understands where the topic changes.

Example

Document

```
Leave Policy

Vacation Leave

Sick Leave

Travel Policy

Expense Policy
```

Semantic chunking produces

```
Chunk 1

Leave Policy

Vacation Leave

Sick Leave

------------------

Chunk 2

Travel Policy

Expense Policy
```

It keeps related ideas together.

This usually produces better retrieval quality.

---

## 5. Recursive Chunking

This is one of the most popular approaches.

The system tries to split by:

1. Headings
2. Paragraphs
3. Sentences
4. Words

It only moves to the next level if the current section is still too large.

Example

```
Document

↓

Heading

↓

Paragraph

↓

Sentence

↓

Words
```

This preserves document structure while keeping chunk sizes manageable.

---

# What is Chunk Overlap?

Suppose we split exactly here.

```
Chunk 1

Employees receive

20 casual

----------------

Chunk 2

casual leaves

every year
```

Notice

The sentence is broken.

To solve this,

we keep a few words in both chunks.

Example

```
Chunk 1

Employees receive

20 casual leaves

----------------

Chunk 2

20 casual leaves

every year
```

This is called **Chunk Overlap**.

---

# Why Use Chunk Overlap?

Without overlap

```
Sentence gets cut.

Context lost.
```

With overlap

```
Context preserved.

Better retrieval.
```

---

# Chunk Size

There is no universal chunk size.

It depends on the use case.

Typical ranges

```
Small

200 Tokens

Medium

500 Tokens

Large

1000 Tokens
```

General guideline

- Small chunks → More precise retrieval
- Large chunks → More context but may include unnecessary information

---

# Choosing the Right Chunk Size

| Chunk Size | Advantages | Disadvantages |
|------------|------------|---------------|
| Small | Precise retrieval | May lose context |
| Medium | Good balance | Most commonly used |
| Large | Rich context | Higher token cost |

---

# Best Practices

- Keep chunks meaningful.
- Avoid splitting sentences.
- Use overlap.
- Preserve document structure.
- Include metadata with every chunk.
- Choose chunk size based on your LLM's context window and document type.

---

# Common Challenges

## Chunk Too Large

```
Entire chapter

↓

One chunk
```

Problem

- Too much information
- Lower retrieval accuracy

---

## Chunk Too Small

```
One sentence

↓

One chunk
```

Problem

- Missing context
- Incomplete information

---

## Poor Splitting

Example

```
Chunk 1

The warranty

Chunk 2

period is two years.
```

The meaning is lost.

---

# Real-Time Example

Original Document

```
Employee Handbook

Employees receive

20 casual leaves

12 sick leaves

Work from home

2 days per week
```

After Chunking

```
Chunk 1

Employees receive
20 casual leaves.

Chunk 2

Employees receive
12 sick leaves.

Chunk 3

Work from home
2 days per week.
```

Each chunk gets its own embedding.

---

# Salesforce Agentforce Example

Knowledge Article

```
Router Setup

Router Reset

Router Troubleshooting

Warranty

Support Contact
```

After Chunking

```
Chunk 1

Router Setup

Chunk 2

Router Reset

Chunk 3

Router Troubleshooting

Chunk 4

Warranty

Chunk 5

Support Contact
```

Now if a customer asks

```
How do I reset my router?
```

The system retrieves

```
Chunk 2

Router Reset
```

instead of the entire article.

---

# Complete Architecture

```
Documents
      │
      ▼
Cleaning
      │
      ▼
Chunking
      │
      ▼
Chunk 1
Chunk 2
Chunk 3
Chunk 4
      │
      ▼
Generate Embeddings
      │
      ▼
Vector Database
      │
      ▼
Retrieval
      │
      ▼
LLM
```

---

# Interview Questions

## What is Chunking?

> Chunking is the process of splitting a large document into smaller, meaningful sections so that only the relevant parts are retrieved during RAG instead of the entire document.

---

## Why is Chunking Needed?

> Chunking improves retrieval accuracy, reduces token usage, lowers costs, and helps the LLM receive only the relevant context instead of an entire document.

---

## What is Chunk Overlap?

> Chunk overlap means repeating a small portion of text between consecutive chunks so that important context is preserved when information spans chunk boundaries.

---

## What is the Best Chunk Size?

There is no fixed answer.

It depends on:

- Document type
- LLM context window
- Retrieval requirements

Most applications use **medium-sized chunks with some overlap** because they balance context and precision.

---

## What Happens After Chunking?

```
Chunk

↓

Embedding

↓

Vector Database

↓

Retrieval

↓

LLM
```

---

# Quick Revision

```
Large Document
      │
      ▼
Chunking
      │
      ▼
Chunk 1
Chunk 2
Chunk 3
Chunk 4
      │
      ▼
Embeddings
      │
      ▼
Vector Database
      │
      ▼
Retrieval
      │
      ▼
LLM
```

---

# One-Line Summary

> **Chunking is the process of dividing large documents into smaller, meaningful pieces so that RAG systems can generate embeddings for each piece, retrieve only the most relevant chunks, and provide accurate, efficient responses while reducing token usage and preserving context.**

# Embeddings in AI

## Overview

Embeddings are numerical representations of text, words, sentences, images, or other data that allow AI models to understand meaning and relationships.

Since AI models cannot understand human language directly, embeddings convert data into vectors (arrays of numbers) that capture semantic meaning.

Embeddings are a foundational concept in Large Language Models (LLMs), Retrieval-Augmented Generation (RAG), Vector Databases, and Agentforce.

---

## Definition

An embedding is a dense vector representation of data where similar items are represented by vectors that are close together in a mathematical space.

In simple terms, embeddings convert human-readable information into machine-readable numerical representations while preserving meaning.

---

## Why Are Embeddings Important?

Computers cannot understand:

```text
Salesforce
Customer
Agentforce
```

directly.

They first convert them into vectors:

```text
Salesforce → [0.23, 0.89, 0.45, ...]
Customer   → [0.41, 0.12, 0.77, ...]
Agentforce → [0.35, 0.84, 0.52, ...]
```

The AI model processes these vectors instead of raw text.

---

## How Embeddings Work

### Input Text

```text
I love Salesforce
```

### Tokenization

```text
["I", "love", "Salesforce"]
```

### Embeddings

```text
I          → [0.12, 0.45, 0.67]
love       → [0.91, 0.23, 0.44]
Salesforce → [0.76, 0.88, 0.32]
```

### Transformer Processing

```text
Embeddings
      ↓
Attention
      ↓
Context Understanding
      ↓
Response Generation
```

---

## Position of Embeddings in LLM Flow

```text
User Prompt
      ↓
Tokenization
      ↓
Embeddings
      ↓
Transformer
      ↓
Attention
      ↓
Response
```

Embeddings are created after tokenization and before the Transformer processes the data.

---

## Semantic Meaning in Embeddings

Embeddings help AI understand relationships.

Example:

```text
King
Queen
Prince
Princess
```

These words will have similar embeddings because their meanings are related.

Similarly:

```text
Salesforce
CRM
Customer Management
```

will be located close together in vector space.

---

## Vector Space Representation

Imagine a graph where similar concepts are grouped together.

```text
CRM
  |
Salesforce ----- Service Cloud
  |
Agentforce
```

Their embeddings are mathematically close because they are semantically related.

---

## Example

### Sentence 1

```text
I love Salesforce.
```

### Sentence 2

```text
I enjoy Salesforce.
```

Although the words differ, the meaning is similar.

Their embeddings will be very close to each other.

---

## Types of Embeddings

### 1. Word Embeddings

Represents individual words.

Example:

```text
Salesforce
Developer
Agent
```

---

### 2. Sentence Embeddings

Represents complete sentences.

Example:

```text
I am learning Agentforce.
```

↓

```text
[0.23, 0.76, 0.44, ...]
```

---

### 3. Document Embeddings

Represents entire documents.

Example:

```text
Agentforce Documentation
```

↓

```text
[0.55, 0.78, 0.34, ...]
```

---

## Embeddings in RAG

### Without RAG

```text
Question
     ↓
LLM
     ↓
Answer
```

---

### With RAG

```text
Documents
      ↓
Embeddings
      ↓
Vector Database
      ↓
Similarity Search
      ↓
Relevant Documents
      ↓
LLM
      ↓
Answer
```

Embeddings allow the system to find relevant information efficiently.

---

## Embeddings and Vector Databases

A Vector Database stores embeddings.

Examples:

- Pinecone
- Weaviate
- Chroma
- FAISS

Flow:

```text
Document
      ↓
Embedding Model
      ↓
Vector
      ↓
Vector Database
```

---

## Similarity Search

Suppose the database contains:

```text
Salesforce CRM
Agentforce
Service Cloud
Marketing Cloud
```

User Query:

```text
What is Salesforce CRM?
```

The query is converted into an embedding.

The Vector Database finds embeddings that are closest to the query embedding.

This process is called Similarity Search.

---

## Embeddings in Agentforce

Agentforce uses embeddings for:

- Knowledge Search
- Semantic Search
- RAG
- Grounding
- Context Retrieval
- Data Cloud Search

### Flow

```text
User Question
      ↓
Embedding Generation
      ↓
Vector Search
      ↓
Relevant Context
      ↓
LLM
      ↓
Response
```

---

## Embeddings vs Tokens

| Feature | Token | Embedding |
|----------|---------|-----------|
| Type | Text Unit | Numerical Vector |
| Example | Salesforce | [0.45, 0.78, 0.12] |
| Purpose | Input Unit | Mathematical Representation |
| Used By | Tokenizer | Transformer |

---

## Embeddings vs Vector Database

| Embeddings | Vector Database |
|-------------|----------------|
| Numerical Representation | Storage System |
| Created by Models | Stores Vectors |
| Used for Similarity Search | Performs Fast Searches |

---

## Interview Questions and Answers

### 1. What is an Embedding?

#### Answer

An embedding is a numerical vector representation of data that captures semantic meaning and relationships between items.

---

### 2. Why Are Embeddings Needed?

#### Answer

AI models cannot understand text directly, so embeddings convert text into numerical vectors that models can process.

---

### 3. Where Do Embeddings Fit in an LLM?

#### Answer

Embeddings are generated after tokenization and before the Transformer processes the input.

```text
Text
 ↓
Tokens
 ↓
Embeddings
 ↓
Transformer
```

---

### 4. What Is Semantic Similarity?

#### Answer

Semantic similarity refers to how close two meanings are. Similar concepts produce embeddings that are close together in vector space.

---

### 5. What Is a Vector Database?

#### Answer

A vector database stores embeddings and enables similarity searches on those embeddings.

---

### 6. How Are Embeddings Used in RAG?

#### Answer

Documents are converted into embeddings and stored in a vector database. User queries are converted into embeddings and matched against stored vectors to retrieve relevant information.

---

### 7. What Is Similarity Search?

#### Answer

Similarity search finds vectors that are mathematically closest to a query vector.

---

### 8. How Does Agentforce Use Embeddings?

#### Answer

Agentforce uses embeddings for semantic search, grounding, knowledge retrieval, and RAG-based responses.

---

### 9. What Is the Difference Between a Token and an Embedding?

#### Answer

A token is a piece of text, while an embedding is the numerical representation of that token.

---

### 10. Why Are Embeddings Important for AI?

#### Answer

Embeddings allow AI models to understand meaning, relationships, and context rather than simply processing raw text.

---

## Best Practices

- Use embeddings for semantic search.
- Store embeddings in vector databases for RAG applications.
- Generate embeddings using trusted embedding models.
- Periodically refresh embeddings when source data changes.
- Use similarity thresholds to improve retrieval quality.

---

## Key Takeaways

- Embeddings convert data into numerical vectors.
- Similar meanings produce similar embeddings.
- Embeddings are created after tokenization.
- Embeddings enable semantic search and RAG.
- Vector databases store embeddings.
- Agentforce uses embeddings for grounding and knowledge retrieval.

---

## One-Line Interview Answer

> An embedding is a numerical vector representation of data that captures semantic meaning and enables AI systems to understand relationships, context, and similarity between items.

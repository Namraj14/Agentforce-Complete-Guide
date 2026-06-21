# Vector Databases

## Overview

A Vector Database is a specialized database designed to store, manage, and search vector embeddings efficiently.

Traditional databases search using exact matches, whereas vector databases search using similarity, making them ideal for AI applications such as RAG, semantic search, recommendation systems, and Agentforce.

---

## Definition

A Vector Database is a database that stores embeddings (vectors) and enables similarity-based retrieval by finding vectors that are mathematically closest to a query vector.

---

## Why Do We Need Vector Databases?

Traditional databases work well for structured data.

Example:

```sql
SELECT Name
FROM Account
WHERE Name = 'Salesforce'
```

This works for exact matches.

However, AI systems need answers for questions like:

```text
What is Salesforce CRM?
```

and

```text
Explain customer relationship management.
```

Although the wording is different, the meaning is similar.

Traditional databases cannot easily understand semantic meaning.

Vector databases solve this problem using embeddings.

---

## How Vector Databases Work

### Step 1: Create Embeddings

Document:

```text
Salesforce is a CRM platform.
```

Embedding:

```text
[0.23, 0.67, 0.89, 0.12]
```

---

### Step 2: Store Embeddings

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

### Step 3: User Query

User asks:

```text
What is CRM?
```

Query Embedding:

```text
[0.21, 0.69, 0.87, 0.14]
```

---

### Step 4: Similarity Search

The vector database compares the query vector with stored vectors.

```text
Query Vector
      ↓
Similarity Search
      ↓
Closest Vectors
      ↓
Relevant Documents
```

---

### Step 5: Return Results

The most relevant documents are returned to the LLM.

---

## Complete AI Flow

```text
Document
      ↓
Chunking
      ↓
Embeddings
      ↓
Vector Database
      ↓
--------------------
User Question
      ↓
Embedding
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

## What Does a Vector Database Store?

A vector database typically stores:

### Embedding

```text
[0.23, 0.45, 0.89, ...]
```

### Original Content

```text
Salesforce is a CRM platform.
```

### Metadata

```json
{
  "source": "salesforce-guide.pdf",
  "page": 5,
  "category": "CRM"
}
```

---

## Similarity Search

Instead of exact matching, vector databases perform similarity matching.

### Example

Stored Documents:

```text
1. Salesforce CRM
2. Service Cloud
3. Agentforce
4. Marketing Cloud
```

---

### User Query

```text
What is customer relationship management?
```

The query embedding will be closest to:

```text
Salesforce CRM
```

because their meanings are similar.

---

## Traditional Database vs Vector Database

| Feature | Traditional Database | Vector Database |
|-----------|--------------------|----------------|
| Stores Records | Yes | Yes |
| Stores Embeddings | No | Yes |
| Exact Search | Excellent | Good |
| Semantic Search | No | Yes |
| AI Workloads | Limited | Excellent |
| Similarity Search | No | Yes |

---

## Common Similarity Metrics

### Cosine Similarity

Most commonly used.

Measures how similar two vectors are.

```text
1 = Identical
0 = Completely Different
```

---

### Euclidean Distance

Measures the distance between vectors.

```text
Smaller Distance
      ↓
More Similar
```

---

### Dot Product

Measures vector similarity using multiplication and summation.

---

## Popular Vector Databases

### Managed Services

- :contentReference[oaicite:0]{index=0}
- :contentReference[oaicite:1]{index=1}
- :contentReference[oaicite:2]{index=2}

---

### Open Source

- :contentReference[oaicite:3]{index=3}
- :contentReference[oaicite:4]{index=4}
- :contentReference[oaicite:5]{index=5}

---

## Vector Databases in RAG

### Without RAG

```text
User Question
      ↓
LLM
      ↓
Answer
```

Risk:

- Hallucinations
- Outdated knowledge

---

### With RAG

```text
User Question
      ↓
Embedding
      ↓
Vector Database
      ↓
Relevant Documents
      ↓
LLM
      ↓
Answer
```

Benefits:

- More accurate answers
- Reduced hallucinations
- Domain-specific knowledge

---

## Vector Databases in Agentforce

Agentforce uses vector databases for:

- Knowledge Search
- Semantic Search
- Grounding
- Retrieval-Augmented Generation (RAG)
- Enterprise Knowledge Retrieval

### Agentforce Flow

```text
User Question
      ↓
Embedding Generation
      ↓
Vector Search
      ↓
Relevant Knowledge
      ↓
LLM
      ↓
Response
```

---

## Real-World Example

Suppose a company has:

```text
100,000 Support Articles
```

When a customer asks:

```text
How do I reset my password?
```

Flow:

```text
Question
      ↓
Embedding
      ↓
Vector Database
      ↓
Find Similar Articles
      ↓
Send Context to LLM
      ↓
Generate Response
```

The AI retrieves only the most relevant articles rather than searching every document manually.

---

## Vector Database vs Embeddings

| Embeddings | Vector Database |
|-------------|----------------|
| Numerical Representation | Storage System |
| Created by Embedding Models | Stores Embeddings |
| Represents Meaning | Enables Search |
| Input to Similarity Search | Performs Similarity Search |

---

## Vector Database vs LLM

| Vector Database | LLM |
|----------------|-----|
| Stores Knowledge | Generates Responses |
| Performs Retrieval | Performs Reasoning |
| Similarity Search | Language Understanding |
| Provides Context | Creates Answers |

---

## Interview Questions and Answers

### 1. What is a Vector Database?

#### Answer

A Vector Database is a specialized database designed to store embeddings and perform similarity-based searches efficiently.

---

### 2. Why Are Vector Databases Needed?

#### Answer

Vector databases enable semantic search and similarity matching, which traditional databases cannot efficiently perform.

---

### 3. What Is Stored in a Vector Database?

#### Answer

A vector database stores:

- Embeddings
- Original Content
- Metadata

---

### 4. What Is Similarity Search?

#### Answer

Similarity search finds vectors that are mathematically closest to a query vector.

---

### 5. What Is Cosine Similarity?

#### Answer

Cosine similarity measures how similar two vectors are based on the angle between them.

A value closer to 1 indicates higher similarity.

---

### 6. How Are Vector Databases Used in RAG?

#### Answer

Documents are converted into embeddings and stored in a vector database. User queries are also converted into embeddings, and the database retrieves the most relevant documents before the LLM generates a response.

---

### 7. What Is the Difference Between a Traditional Database and a Vector Database?

#### Answer

Traditional databases perform exact-match searches, while vector databases perform semantic similarity searches using embeddings.

---

### 8. How Does Agentforce Use Vector Databases?

#### Answer

Agentforce uses vector databases for semantic search, grounding, knowledge retrieval, and RAG-based responses.

---

### 9. What Is the Relationship Between Embeddings and Vector Databases?

#### Answer

Embeddings are numerical representations of data, while vector databases store and search those embeddings efficiently.

---

### 10. Can a Vector Database Replace an LLM?

#### Answer

No.

A vector database retrieves relevant information, while an LLM understands language and generates responses.

Both typically work together in RAG systems.

---

## Best Practices

- Store high-quality embeddings.
- Include metadata for filtering.
- Use chunking before creating embeddings.
- Regularly refresh embeddings when source data changes.
- Use vector databases alongside RAG for enterprise AI applications.
- Validate retrieved context before generating responses.

---

## Key Takeaways

- Vector databases store embeddings.
- They enable semantic search and similarity matching.
- They are a critical component of RAG systems.
- They help reduce hallucinations by retrieving relevant context.
- Agentforce uses vector databases for grounding and knowledge retrieval.
- Popular vector databases include Pinecone, Weaviate, ChromaDB, Milvus, and Qdrant.

---

## One-Line Interview Answer

> A Vector Database is a specialized database that stores embeddings and enables similarity-based retrieval, making it a key component of RAG, semantic search, and AI-powered applications.

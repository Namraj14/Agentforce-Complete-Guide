# Retrieval-Augmented Generation (RAG)

## What is RAG?

**RAG (Retrieval-Augmented Generation)** is an AI technique where the system **first searches for relevant information**, then **uses that information to generate an accurate answer**.

Instead of answering only from its own memory, the AI retrieves information from external sources like documents, databases, or knowledge articles before responding.

---

# The Simplest Definition

> **RAG = Search first → Answer later.**

---

# Breaking Down RAG

## R - Retrieval

The AI searches for relevant information.

It can search from:

- PDFs
- Company documents
- Salesforce Knowledge Articles
- Databases
- Data Cloud
- Websites

Think of it like searching on Google before answering a question.

---

## A - Augmented

The retrieved information is added to the AI's prompt.

Instead of asking the AI to answer from memory, it is given the relevant information to use while generating the response.

---

## G - Generation

The Large Language Model (LLM) reads the retrieved information and generates a natural language answer.

---

# Simple Example

Imagine your teacher asks:

> What is the capital of Australia?

## Without RAG

You answer from memory.

```
Question
      ↓
Memory
      ↓
Answer
```

You might say:

> Sydney

This is incorrect.

---

## With RAG

Before answering, you quickly open your textbook.

```
Question
      ↓
Search Textbook
      ↓
Find Answer
      ↓
Generate Response
```

You find:

> Canberra

Now your answer is accurate.

---

# Think of RAG Like an Open Book Exam

Without RAG

```
Teacher asks question

↓

You answer from memory
```

With RAG

```
Teacher asks question

↓

Open the book

↓

Find the answer

↓

Write the answer
```

Exactly the same concept.

---

# RAG Workflow

```
User asks a question
          │
          ▼
Retrieve relevant information
          │
          ▼
Add retrieved information to the prompt
          │
          ▼
LLM generates the answer
          │
          ▼
User receives an accurate response
```

---

# Real-Life Example

Suppose your company's HR policy document contains:

```
Casual Leaves : 20
Sick Leaves   : 12
Work From Home: 2 days/week
```

An employee asks:

> How many casual leaves do I get?

### Without RAG

The AI guesses.

```
Answer:
15 Casual Leaves
```

Incorrect.

### With RAG

The AI searches the HR document.

It finds:

```
Casual Leaves : 20
```

Then responds:

> You receive **20 casual leaves per year.**

---

# Everyday Example

Your mom asks:

> Where are the house documents?

You don't remember.

So you:

1. Search the cupboard.
2. Find the documents.
3. Tell her where they are.

This is exactly how RAG works.

---

# Salesforce Agentforce Example

A customer asks:

> What is the warranty period for Product X?

## Without RAG

The AI answers from memory.

```
Warranty: 1 Year
```

Possibly incorrect.

---

## With RAG

Agentforce searches:

- Salesforce Knowledge Articles
- Product Manuals
- Data Cloud
- CRM Records

It finds:

```
Warranty = 2 Years
```

It responds:

> The warranty period for Product X is **2 years**.

---

# Why Do We Need RAG?

Without RAG:

- AI answers only from its training.
- Information may be outdated.
- AI cannot access private company data.
- It may guess when unsure.

With RAG:

- Uses the latest company data.
- Provides more accurate responses.
- Can answer questions about private documents.
- Reduces hallucinations (guessing).

---

# RAG Architecture

```
                 User
                   │
                   ▼
         User asks a question
                   │
                   ▼
         Retrieve Relevant Data
     (Knowledge, PDFs, Database,
      Data Cloud, CRM Records)
                   │
                   ▼
     Retrieved Information Added
          to the LLM Prompt
                   │
                   ▼
      LLM Generates the Answer
                   │
                   ▼
            Final Response
```

---

# Key Points to Remember

- RAG does **not** replace the LLM.
- RAG simply provides the LLM with better information.
- The LLM still generates the final response.
- The better the retrieved information, the better the answer.

---

# Interview Definition

> **Retrieval-Augmented Generation (RAG) is an AI approach in which the system first retrieves relevant information from external data sources, augments the prompt with that information, and then uses a Large Language Model (LLM) to generate an accurate, context-aware response.**

---

# One-Line Formula

```
Question
      +
Search Relevant Data
      +
LLM
      =
Accurate Answer
```

Or simply:

> **RAG = Search first → Answer later.**

# RAG Pipelines (Data Ingestion & Retrieval Pipeline)

## How are these pipelines related to RAG?

Before understanding the pipelines, let's quickly understand **RAG**.

> **RAG (Retrieval-Augmented Generation)** is an AI technique where the system first retrieves relevant information from external data sources and then uses a Large Language Model (LLM) to generate an accurate answer.

However, for RAG to work, it needs two important pipelines:

1. **Data Ingestion Pipeline (Offline Pipeline)** – Prepares and stores the data so it can be searched efficiently.
2. **Retrieval (Query) Pipeline (Online Pipeline)** – Retrieves the right information and generates the final answer.

Think of it like a library.

- **Data Ingestion Pipeline** = Organizing all the books in the library before anyone visits.
- **Retrieval Pipeline** = Finding the correct book when someone asks a question.

Without the **Data Ingestion Pipeline**, there would be nothing to search.

Without the **Retrieval Pipeline**, the AI wouldn't know which information to use.

Together, these two pipelines make **RAG** work.

---

# Complete RAG Architecture

```text
                   RAG (Retrieval-Augmented Generation)

                 ┌──────────────────────────────────────┐
                 │         Data Ingestion Pipeline       │
                 │           (Offline Process)           │
                 └──────────────────────────────────────┘
                               │
                               ▼
                  Documents Prepared & Stored
                               │
                               ▼
                     Vector Database Ready
                               │
───────────────────────────────────────────────────────────────
                               │
                               ▼
                 ┌──────────────────────────────────────┐
                 │       Retrieval Pipeline             │
                 │        (Online Process)              │
                 └──────────────────────────────────────┘
                               │
                               ▼
                      User Gets Final Answer
```

---

# 1. Data Ingestion Pipeline (Offline)

## What is it?

The Data Ingestion Pipeline is responsible for preparing all the documents before users ask any questions.

This pipeline usually runs:

- When new documents are added
- When documents are updated
- On scheduled intervals

It is called **Offline** because it happens **before** a user asks a question.

---

## Data Ingestion Flow

```text
Documents
     │
     ▼
Load Documents
     │
     ▼
Clean & Process
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

---

## Step 1 – Load Documents

The system collects documents from different sources.

Examples:

- PDFs
- Word Documents
- Salesforce Knowledge Articles
- SharePoint
- Confluence
- Websites
- Databases
- Data Cloud

Example:

```
Employee Handbook.pdf
Warranty.pdf
HR Policy.docx
```

---

## Step 2 – Clean & Process

Documents often contain unnecessary information.

Example:

```
Page Number
Header
Footer
Company Logo
Blank Spaces
```

The system removes unnecessary content.

After cleaning:

```
Employees receive 20 casual leaves.
```

---

## Step 3 – Chunking

Large documents are divided into smaller sections called **chunks**.

Instead of searching a 200-page document, the system searches small pieces.

Example:

Original Document

```
200 Pages
```

After Chunking

```
Chunk 1

Chunk 2

Chunk 3

Chunk 4
```

### Why Chunking?

Because:

- LLMs have token limits.
- Smaller chunks improve search accuracy.
- Only relevant chunks are retrieved instead of the whole document.

---

## Step 4 – Generate Embeddings

Every chunk is converted into a numerical representation called an **embedding**.

Example

```
Chunk

↓

Employees receive 20 casual leaves.

↓

Embedding

↓

[0.23, -0.87, 0.44, ...]
```

### Why Embeddings?

Computers don't understand language the way humans do.

Embeddings help computers understand the **meaning** of text rather than just matching keywords.

---

## Step 5 – Store in Vector Database

The embeddings are stored inside a Vector Database.

Example:

```
Vector Database

Chunk 1 → Embedding

Chunk 2 → Embedding

Chunk 3 → Embedding
```

The original text and metadata are also stored, so that once a matching embedding is found, the actual text can be retrieved.

---

# Data Ingestion Summary

```text
PDFs
Word Files
Knowledge Articles
Websites
Databases
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

At this point, the system is ready to answer questions.

---

# 2. Retrieval Pipeline (Query Pipeline)

## What is it?

When a user asks a question, the Retrieval Pipeline finds the most relevant information and sends it to the LLM.

This happens **every time** a user asks a question.

It is called the **Online Pipeline** because it runs in real time.

---

## Retrieval Flow

```text
User Question
      │
      ▼
Generate Question Embedding
      │
      ▼
Search Vector Database
      │
      ▼
Retrieve Relevant Chunks
      │
      ▼
Augment Prompt
      │
      ▼
Send Prompt to LLM
      │
      ▼
Generate Answer
      │
      ▼
Return Response
```

---

## Step 1 – User Asks a Question

Example:

```
What is the warranty period of Product X?
```

---

## Step 2 – Generate Question Embedding

The user's question is converted into an embedding.

Example

```
Question

↓

"What is the warranty?"

↓

Embedding

↓

[0.61, -0.22, 0.98, ...]
```

---

## Step 3 – Search Vector Database

The question embedding is compared with the embeddings stored during the Data Ingestion Pipeline.

The system looks for the most similar embeddings.

---

## Step 4 – Retrieve Relevant Chunks

Suppose the vector database contains:

```
Chunk 1

Warranty = 2 Years

Chunk 2

Return Policy = 30 Days

Chunk 3

Shipping = Free
```

The system retrieves:

```
Warranty = 2 Years
```

---

## Step 5 – Augment the Prompt

The retrieved information is added to the user's question.

Example:

```
Question

What is the warranty period?

Context

Warranty = 2 Years
```

This step is called **Augmentation**.

---

## Step 6 – Send Prompt to LLM

The complete prompt is sent to the Large Language Model.

Example:

```
Use the following context to answer.

Context:

Warranty = 2 Years

Question:

What is the warranty period?
```

---

## Step 7 – Generate the Final Answer

The LLM generates a natural language response.

Example:

```
The warranty period of Product X is 2 years.
```

---

# Complete Retrieval Summary

```text
User Question
        │
        ▼
Generate Embedding
        │
        ▼
Search Vector Database
        │
        ▼
Retrieve Relevant Chunks
        │
        ▼
Add Context to Prompt
        │
        ▼
LLM Generates Response
        │
        ▼
Final Answer
```

---

# End-to-End RAG Flow

```text
                    DATA INGESTION PIPELINE
                 (Runs Before Users Ask Questions)

PDFs / Docs / Websites / Knowledge Articles
                     │
                     ▼
              Load Documents
                     │
                     ▼
             Clean & Process
                     │
                     ▼
             Split into Chunks
                     │
                     ▼
          Generate Embeddings
                     │
                     ▼
          Store in Vector Database

=============================================================

                 RETRIEVAL PIPELINE
               (Runs When User Asks)

User Question
      │
      ▼
Generate Question Embedding
      │
      ▼
Search Vector Database
      │
      ▼
Retrieve Best Chunks
      │
      ▼
Augment Prompt
      │
      ▼
Large Language Model
      │
      ▼
Generate Final Answer
      │
      ▼
User Receives Response
```

---

# Real-Time Example

### Documents Stored

```
HR Policy

Employees receive 20 casual leaves.
```

### User asks

```
How many casual leaves do I get?
```

### Retrieval Pipeline

```
Generate Embedding
        │
        ▼
Search Vector Database
        │
        ▼
Retrieve

Employees receive 20 casual leaves.
```

### LLM Response

```
Employees receive 20 casual leaves per year.
```

---

# Key Differences

| Data Ingestion Pipeline | Retrieval Pipeline |
|--------------------------|--------------------|
| Runs offline | Runs online |
| Executes before users ask questions | Executes when a question is asked |
| Loads documents | Accepts user questions |
| Cleans documents | Generates question embedding |
| Splits documents into chunks | Searches vector database |
| Generates document embeddings | Retrieves relevant chunks |
| Stores data in vector database | Builds prompt with retrieved context |
| Happens occasionally | Happens for every query |

---

# Interview Definition

### What is the Data Ingestion Pipeline?

> The Data Ingestion Pipeline is the offline process that prepares data for RAG by loading documents, cleaning them, splitting them into chunks, generating embeddings, and storing them in a vector database for efficient semantic search.

---

### What is the Retrieval Pipeline?

> The Retrieval Pipeline is the online process that converts a user's query into an embedding, searches the vector database for relevant chunks, augments the prompt with those chunks, and sends it to the LLM to generate the final response.

---

# Quick Revision

```
RAG
│
├── Data Ingestion Pipeline (Offline)
│       ├── Load Documents
│       ├── Clean Documents
│       ├── Chunk Documents
│       ├── Generate Embeddings
│       └── Store in Vector Database
│
└── Retrieval Pipeline (Online)
        ├── User Question
        ├── Generate Question Embedding
        ├── Search Vector Database
        ├── Retrieve Chunks
        ├── Augment Prompt
        ├── Send to LLM
        └── Generate Final Answer
```

## One-Line Formula

> **Data Ingestion Pipeline prepares the knowledge. Retrieval Pipeline finds the knowledge. The LLM uses that knowledge to generate the answer. Together, they form the complete RAG system.**

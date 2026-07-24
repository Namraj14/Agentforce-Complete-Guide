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

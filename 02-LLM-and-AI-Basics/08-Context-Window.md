# Context Window Explained

## What is a Context Window?

A **context window** is the amount of information an AI model can process and consider at one time while generating a response.

Think of it like the AI's **working memory for the current conversation**.

It can include:

* Your current question
* Previous messages
* Instructions
* Code
* Documents
* Other information provided in the conversation

The size of the context window is measured in **tokens**.

---

## What is a Token?

A token is a small piece of text that an AI model processes.

For example:

```text
Hello, how are you?
```

might be split into several tokens.

You don't need to think of tokens as exactly equal to words. A token can be:

* Part of a word
* A complete word
* Punctuation
* Spaces or other text fragments

---

## Simple Example

Imagine an AI has a context window that can hold **10,000 tokens**.

You have:

```text
Previous conversation = 6,000 tokens
Your new question     = 1,000 tokens
Instructions          = 1,000 tokens
```

Total:

```text
6,000 + 1,000 + 1,000
= 8,000 tokens
```

The AI still has approximately:

```text
10,000 - 8,000 = 2,000 tokens
```

available for processing/generating the response, depending on how the particular model allocates its context.

---

## Why Does Context Window Matter?

The context window determines **how much information the model can consider at once**.

For example, suppose you give an AI a large Salesforce Apex class:

```apex
public class OrderProcessor {
    // hundreds of lines...
}
```

Then you ask:

```text
Find the bug in the payment processing logic.
```

If the relevant code is inside the available context, the AI can reason about it using that code.

But if the total conversation + instructions + files become too large, some earlier information may no longer fit into the active context.

---

## Context Window vs Memory

These two concepts are different.

### Context Window

The **context window** is the information available to the model during the current interaction.

```text
Current conversation
        ↓
Context Window
        ↓
AI processes the information
        ↓
Response
```

### Memory

**Memory** is information that can be retained and used across conversations, depending on the AI system.

For example:

```text
Conversation 1:
"I prefer Salesforce examples."

          ↓

Saved Memory

          ↓

Conversation 2:
AI can use that preference
when appropriate.
```

So:

> **Context = information currently available to the model**

> **Memory = information that may be retained for future conversations**

Memory is not simply an extension of the context window. A system typically retrieves relevant memories and places them into the context when needed.

---

## Easy Analogy

Think of an AI as a developer working at a desk.

### Context Window = Desk

The developer can only have a certain amount of material on the desk at once.

```text
┌──────────────────────────────┐
│        CONTEXT WINDOW        │
│                              │
│  Question                    │
│  Previous messages           │
│  Code                        │
│  Instructions                │
│  Documents                   │
│                              │
└──────────────────────────────┘
```

### Memory = Filing Cabinet

Important information can be stored elsewhere and retrieved when needed.

```text
        ┌───────────────┐
        │    Memory     │
        │               │
        │ Preferences   │
        │ Past facts    │
        │ Useful info   │
        └───────┬───────┘
                │
                ↓
        ┌───────────────┐
        │ Context Window│
        └───────────────┘
```

---

## Context Window Example with ChatGPT

Imagine a conversation:

```text
User:
I am building a Salesforce integration.

AI:
Okay.

User:
We are using REST API.

AI:
Okay.

User:
We are also using Named Credentials.

AI:
Okay.

User:
Now explain how authentication works.
```

The AI can use the earlier conversation as context:

```text
Salesforce
   ↓
REST API
   ↓
Named Credential
   ↓
Authentication
```

This allows the answer to be more relevant than if the AI only saw the last question.

---

## What Happens When Context Gets Too Large?

Suppose the context window can hold:

```text
100,000 tokens
```

but the conversation grows to:

```text
120,000 tokens
```

Everything cannot necessarily remain in the active context.

The AI system may use techniques such as:

* Removing older messages
* Summarizing previous content
* Retrieving only relevant information
* Compressing context
* Using external memory or retrieval systems

The exact behavior depends on the AI system.

---

## Context Window in RAG

Context windows are especially important in **RAG (Retrieval-Augmented Generation)**.

Imagine you have:

```text
1,000 Salesforce documents
```

You don't normally send all 1,000 documents to the model.

Instead:

```text
User Question
      ↓
Retriever
      ↓
Find relevant documents
      ↓
Relevant chunks
      ↓
Context Window
      ↓
LLM
      ↓
Answer
```

For example:

```text
Question:
"How does our Case escalation process work?"
```

The system might retrieve:

```text
Case Escalation Policy
SLA Configuration
Escalation Flow Documentation
```

Only those relevant pieces are placed into the model's context.

---

## Key Point

A larger context window does **not automatically mean the AI has better memory**.

It simply means the model can potentially consider **more information at once**.

Think:

```text
Context Window
      =
How much information can be on the desk

Memory
      =
What information can be stored and retrieved later
```

---

## In One Sentence

> **A context window is the amount of information an AI model can work with at one time when generating a response.**


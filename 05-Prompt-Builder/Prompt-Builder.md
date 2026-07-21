# Prompt Builder (Salesforce)

## What is Prompt Builder?

**Prompt Builder** is a Salesforce tool that helps you create **AI prompts (instructions)** without writing complex code.

It allows you to tell the AI:

- What to do
- What data to use
- How the response should look

Simply put,

> **Prompt Builder is used to create reusable AI prompts for Salesforce.**

---

# Why Do We Need Prompt Builder?

Imagine asking ChatGPT the same question every day.

Example:

```
Summarize this case professionally.
```

Instead of typing this prompt repeatedly, you create it once in Prompt Builder.

Now Salesforce can use that prompt automatically whenever needed.

---

# Simple Example

Customer Case:

```
Customer:
Internet is not working.
Very unhappy.
Requested urgent support.
```

Prompt Builder Prompt:

```
Summarize this case in a professional tone.
```

AI Output:

```
The customer reported an internet connectivity issue and requested immediate assistance. The customer expressed dissatisfaction and requires urgent support.
```

---

# How Prompt Builder Works

```text
User
   │
   ▼
Prompt Builder
   │
   ▼
Collect Salesforce Data
   │
   ▼
Create Prompt
   │
   ▼
Send to AI Model
   │
   ▼
Generate Response
   │
   ▼
Return Result
```

---

# Components of Prompt Builder

A prompt generally contains:

1. Instructions
2. Input Data
3. Output Format

---

## 1. Instructions

Instructions tell the AI **what it should do**.

### Example

```
Summarize the customer case.
```

or

```
Write a polite email.
```

or

```
Generate meeting notes.
```

---

## 2. Input Data

Input data is the Salesforce information sent to the AI.

Example:

```
Case Subject

Description

Priority

Status

Account Name
```

The AI uses this data to generate its response.

---

## 3. Output Format

You can control how the AI responds.

Example

```
Return only three bullet points.
```

or

```
Return JSON.
```

or

```
Write a professional email.
```

---

# Types of Prompt Templates

Salesforce provides different prompt template types.

The most common are:

1. Field Generation
2. Flex Prompt Template
3. Record Summary
4. Sales Email
5. Service Reply

---

# 1. Field Generation Prompt

Used to automatically generate text for a Salesforce field.

### Example

Lead Description

Input

```
Name : John

Company : ABC Ltd

Interested Product : Laptop
```

Prompt

```
Generate a professional lead description.
```

Output

```
John from ABC Ltd expressed interest in purchasing laptops and requested additional product information.
```

The generated text is stored in the Lead Description field.

---

# 2. Flex Prompt Template

The most flexible prompt type.

You decide:

- Instructions
- Data
- Output

You can use it almost anywhere.

### Example

```
Summarize this case.
```

```
Write an email.
```

```
Translate into French.
```

```
Generate meeting notes.
```

---

# 3. Record Summary

Creates a summary of a Salesforce record.

Example

Case Record

```
Status : Open

Priority : High

Issue : Internet not working
```

AI Output

```
The customer has reported a high-priority internet connectivity issue. The case is currently open.
```

---

# 4. Sales Email

Generates personalized sales emails.

Example

Input

```
Customer

Products

Previous Purchases
```

Output

```
Dear John,

Thank you for your continued partnership.

Based on your recent purchases, we recommend our latest premium laptop...
```

---

# 5. Service Reply

Automatically generates customer support replies.

Example

Customer

```
I haven't received my refund.
```

AI

```
Dear Customer,

We apologize for the delay. Your refund request is currently being processed...
```

---

# Prompt Builder Architecture

```text
Salesforce Record
        │
        ▼
Prompt Builder
        │
        ▼
Collect Record Data
        │
        ▼
Build Prompt
        │
        ▼
Einstein Trust Layer
        │
        ▼
Large Language Model
        │
        ▼
AI Response
```

---

# Real Salesforce Example

Case Record

```
Customer

Issue

Priority

Status
```

Prompt

```
Summarize this case for a support manager.
```

Output

```
This is a high-priority customer issue involving internet connectivity. The customer requires immediate assistance.
```

---

# Prompt Builder vs Agentforce

| Prompt Builder | Agentforce |
|---------------|------------|
| Creates AI prompts | Uses prompts to complete work |
| Generates content | Performs business actions |
| Mostly text generation | Task automation + AI |
| Used inside Salesforce | AI Agent for Salesforce |
| No decision making | Can reason and plan |

---

# Prompt Builder vs Flow

| Flow | Prompt Builder |
|------|----------------|
| Automates business logic | Generates AI content |
| Uses conditions and actions | Uses AI prompts |
| Creates and updates records | Creates summaries, emails, replies |
| No AI generation | AI-powered text generation |

---

# Benefits of Prompt Builder

- No coding required
- Reusable prompts
- Uses Salesforce data
- Integrates with Einstein Trust Layer
- Generates high-quality content
- Saves time
- Can be used by Agentforce and Flows

---

# Easy Way to Remember

| Component | Question |
|-----------|----------|
| Instructions | What should the AI do? |
| Input Data | What information should it use? |
| Output Format | How should the response look? |

---

# Interview Questions

## Q1. What is Prompt Builder?

**Answer:**

Prompt Builder is a Salesforce feature used to create reusable AI prompts that generate content using Salesforce data.

---

## Q2. Why do we use Prompt Builder?

**Answer:**

It helps generate AI-powered content such as summaries, emails, service replies, and field values without writing complex prompts every time.

---

## Q3. What are the main parts of a prompt?

**Answer:**

- Instructions
- Input Data
- Output Format

---

## Q4. What is the difference between Prompt Builder and Agentforce?

**Answer:**

Prompt Builder is used to generate AI content, while Agentforce uses prompts along with reasoning and actions to complete business tasks.

---

## Q5. Does Prompt Builder use the Einstein Trust Layer?

**Answer:**

Yes. All prompts go through the Einstein Trust Layer, which protects Salesforce data, enforces permissions, masks sensitive information, and ensures safe AI interactions.

---

# Final Summary

| Feature | Description |
|---------|-------------|
| Purpose | Create reusable AI prompts |
| Input | Salesforce records and data |
| Output | AI-generated content |
| Uses | Summaries, emails, replies, field values |
| Security | Protected by Einstein Trust Layer |
| Coding | No coding required |

---

# One-Line Memory Trick

- **Prompt Builder** → *Build the prompt.*
- **Einstein Trust Layer** → *Protect the data.*
- **LLM** → *Generate the response.*
- **Agentforce** → *Use the response and perform actions.*

## Interview One-Liner

> **Prompt Builder is a low-code Salesforce tool used to create reusable AI prompt templates that combine instructions with Salesforce data to generate content such as summaries, emails, and service replies, while securely using the Einstein Trust Layer.**

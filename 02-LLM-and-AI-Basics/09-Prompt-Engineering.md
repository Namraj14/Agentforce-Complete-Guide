# Prompt Engineering Explained

## What is Prompt Engineering?

**Prompt Engineering** is the process of writing clear and effective instructions for an AI model so that it produces the desired output.

In simple terms:

> **Prompt Engineering = Giving the AI the right instructions to get the right result.**

Instead of simply asking:

```text
Tell me about Salesforce.
```

you can provide more specific instructions:

```text
Explain Salesforce Apex to a beginner.
Use simple language and give 3 real-world examples.
Keep the explanation under 500 words.
```

The second prompt gives the AI much more direction.

---

## Why is Prompt Engineering Important?

AI models don't automatically know exactly what you want.

For example:

```text
Write about Apex.
```

could produce:

* Apex basics
* Apex triggers
* Apex interview questions
* Advanced Apex
* Apex code examples

But:

```text
Explain Apex triggers to a Salesforce developer
with 2 years of experience. Explain the execution
order and give one real-world example.
```

is much more specific.

The AI now has a clearer objective.

---

# Basic Prompt Structure

A useful prompt can contain:

```text
Role
  +
Task
  +
Context
  +
Constraints
  +
Output Format
```

For example:

```text
You are a Salesforce developer.

Explain Apex triggers.

Context:
The learner has 2 years of Salesforce experience.

Requirements:
- Explain in simple language
- Explain before/after triggers
- Give one real-world example
- Include a small Apex example

Output:
Use headings and bullet points.
```

---

# 1. Role

A role tells the AI what perspective or expertise it should use.

Example:

```text
Act as a senior Salesforce developer.
```

or:

```text
Act as a Salesforce architect reviewing this design.
```

This can help frame the response appropriately.

---

# 2. Task

Clearly tell the AI what you want it to do.

Bad:

```text
Apex triggers
```

Better:

```text
Explain Apex triggers and when to use them.
```

Even better:

```text
Explain Apex triggers to a beginner,
including before vs after triggers and
a real-world Salesforce example.
```

---

# 3. Context

Context gives the AI information needed to understand the situation.

Example:

```text
I am a Salesforce developer with 4 years of experience.
I am preparing for a Senior Salesforce Developer interview.
```

Then:

```text
Explain Apex asynchronous processing
with interview-focused examples.
```

The AI can tailor the response based on that context.

---

# 4. Constraints

Constraints tell the AI what it should or should not do.

Examples:

```text
Keep the answer under 500 words.
```

```text
Use simple language.
```

```text
Give only Salesforce examples.
```

```text
Do not use advanced terminology without explaining it.
```

Constraints reduce unwanted output.

---

# 5. Output Format

You can specify exactly how you want the answer structured.

Example:

```text
Return the answer in this format:

1. Definition
2. How it works
3. Example
4. Common mistakes
5. Interview question
```

This makes the output more predictable.

---

# Example: Weak vs Strong Prompt

### Weak Prompt

```text
Explain REST API.
```

### Strong Prompt

```text
Act as a Salesforce integration expert.

Explain REST APIs to a Salesforce developer.

Cover:
1. What REST API is
2. How request/response works
3. HTTP methods
4. Authentication
5. Salesforce example
6. Common errors

Use simple language and provide one real-world
Salesforce integration example.
```

The second prompt provides:

```text
Role
 ↓
Task
 ↓
Context
 ↓
Requirements
 ↓
Output structure
```

---

# Few-Shot Prompting

**Few-shot prompting** means giving the AI examples of the kind of output you want.

For example:

```text
Convert these requirements into user stories.

Example:

Requirement:
Users should be able to reset their password.

Output:
User Story:
As a user, I want to reset my password
so that I can regain access to my account.

Now convert:

Requirement:
Users should be able to update their email.
```

The example teaches the model the expected pattern.

---

# Zero-Shot Prompting

You give the AI a task without providing an example.

```text
Convert this requirement into a user story:

Users should be able to update their email.
```

No example is provided.

This is called **zero-shot prompting**.

---

# One-Shot Prompting

You provide one example.

```text
Example:

Requirement:
Users can reset their password.

Output:
As a user, I want to reset my password
so that I can regain access.

Now convert:
Users can update their email.
```

---

# Few-Shot Prompting

You provide multiple examples.

```text
Example 1:
Requirement → User Story

Example 2:
Requirement → User Story

Example 3:
Requirement → User Story

Now convert the new requirement.
```

The model can identify the pattern from the examples.

---

# Chain-of-Thought

For complex problems, models can perform multi-step reasoning internally.

Instead of simply asking:

```text
What is the answer?
```

you can ask for a structured approach such as:

```text
Analyze the problem step by step and provide
the final conclusion with the key reasoning.
```

However, you generally don't need to request or expose hidden internal reasoning. A better practice is to ask for:

```text
Give the key steps used to reach the conclusion.
```

---

# Structured Prompting

For larger tasks, structure the prompt clearly.

Example:

```text
# Role
You are a Salesforce architect.

# Context
We have an Order Management System integration.

# Problem
Salesforce is receiving duplicate order updates.

# Task
Identify possible causes and recommend a solution.

# Requirements
- Consider integration patterns
- Consider Platform Events
- Consider idempotency
- Consider retry mechanisms

# Output
Provide:
1. Possible causes
2. Recommended architecture
3. Implementation approach
4. Risks
```

This is much easier for the AI to interpret than one large paragraph.

---

# Prompt Engineering and Context

Prompt engineering and context windows are closely related.

A prompt becomes part of the information the model processes.

For example:

```text
System Instructions
        +
User Prompt
        +
Conversation History
        +
Retrieved Documents
        +
Examples
        ↓
   Context Window
        ↓
       LLM
        ↓
     Response
```

If you provide unnecessary information, you consume context without improving the answer.

Therefore:

> **Good prompt engineering is not just about adding more words. It is about providing the right information.**

---

# Prompt Engineering in RAG

In a RAG system, the prompt might look like:

```text
You are a Salesforce support assistant.

Answer the user's question using only
the provided context.

Context:
{retrieved_documents}

Question:
{user_question}

If the answer is not present in the context,
say that you don't have enough information.
```

Here:

```text
User Question
      +
Retrieved Context
      +
Instructions
      ↓
     Prompt
      ↓
      LLM
```

This helps **ground** the model's answer in retrieved information.

---

# Prompt Engineering in Salesforce

Prompt engineering is also important in Salesforce AI features such as:

* Agentforce
* Prompt Builder
* Einstein features
* AI-generated summaries
* Record summarization
* Email generation
* Classification
* RAG-based responses

For example:

```text
You are a Salesforce Service Agent.

Summarize the Case using the provided
Case information.

Include:
- Customer issue
- Root cause
- Actions taken
- Current status
- Next action

Do not invent information that is not
present in the Case data.
```

This is a practical prompt-engineering pattern.

---

# Good Prompt vs Bad Prompt

### Bad

```text
Tell me what to do with this case.
```

### Better

```text
Analyze this Salesforce Case.

Identify:
1. Customer issue
2. Severity
3. Actions already taken
4. Recommended next action

Use only the information provided.
```

The second prompt is:

* Specific
* Structured
* Grounded
* Easier to evaluate

---

# Important Prompt Engineering Principles

### 1. Be Specific

```text
Explain Apex.
```

is vague.

```text
Explain Apex triggers with a Salesforce example.
```

is specific.

### 2. Give Relevant Context

Tell the model information that changes the answer.

### 3. Define Constraints

Specify length, scope, audience, or restrictions.

### 4. Specify Output Format

Tell the model whether you want:

```text
Table
JSON
Bullets
Steps
Code
Summary
```

### 5. Provide Examples When Useful

Examples are especially useful when the desired output has a specific pattern.

### 6. Avoid Unnecessary Information

More context isn't always better.

Relevant context > large amounts of irrelevant context.

---

# Simple Mental Model

Think of prompting like giving instructions to a developer.

Instead of saying:

```text
Build something for orders.
```

you say:

```text
You are a Salesforce developer.

Build an Apex service that retrieves
Order records using an external Order ID.

Requirements:
- Bulk-safe
- Use SOQL
- Handle missing records
- Include a test class

Return the Apex class and test class.
```

The second instruction gives the developer a much clearer specification.

Prompt engineering works similarly.

---

# Prompt Engineering in One Diagram

```text
          USER
           ↓
     Clear Prompt
           ↓
 ┌─────────────────────┐
 │ Role                 │
 │ Task                 │
 │ Context              │
 │ Constraints          │
 │ Examples             │
 │ Output Format        │
 └─────────────────────┘
           ↓
      Context Window
           ↓
          LLM
           ↓
        Response
```

---

# In One Sentence

> **Prompt engineering is the practice of designing clear, structured instructions and providing the right context so an AI model can produce a more useful and predictable output.**

---

## Quick Formula

```text
Good Prompt
=
Role
+
Task
+
Relevant Context
+
Constraints
+
Examples (when needed)
+
Output Format
```

The goal is **not to make prompts unnecessarily long**.

The goal is to make them **clear, relevant, and precise**.


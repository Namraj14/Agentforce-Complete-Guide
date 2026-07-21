# Agentforce Architecture

## What is Agentforce Architecture?

Agentforce Architecture describes **how a user's request flows through Salesforce AI**, how it retrieves data securely, performs business actions, and returns a response.

Think of it as the **end-to-end workflow** of Agentforce.

---

# High-Level Architecture

```text
                     User
                       │
                       ▼
              Agentforce Agent
                       │
         (Understands User Intent)
                       │
                       ▼
               Prompt Builder
                       │
        (Creates AI Prompt with Context)
                       │
                       ▼
          Einstein Trust Layer
   (Security, Grounding, Permissions,
      Masking, Audit, Safety Checks)
                       │
                       ▼
            Large Language Model
        (Reasoning & Response Generation)
                       │
                       ▼
         Agentforce Decision Engine
      (Chooses Tools / Actions to Run)
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
   Salesforce Data    Flows        Apex Actions
        │              │              │
        ├──────────────┼──────────────┤
                       ▼
              External APIs / MCP
                       │
                       ▼
             External Applications
      (ERP, GitHub, Slack, SAP, etc.)
                       │
                       ▼
               Final AI Response
                       │
                       ▼
                     User
```

---

# Step-by-Step Flow

## Step 1: User Sends a Request

Everything begins when a user asks a question.

Example:

```
Cancel my order.
```

or

```
Show my open cases.
```

---

## Step 2: Agentforce Understands the Request

The agent identifies the user's intent.

Example:

```
User:

Cancel my order.

↓

Intent:

Cancel Order
```

The AI understands **what the user wants**.

---

## Step 3: Prompt Builder Creates the Prompt

Prompt Builder prepares the prompt that will be sent to the AI.

It combines:

- Instructions
- Salesforce data
- User request
- Business context

Example:

```
You are a Customer Support Agent.

Summarize this case.

Use a professional tone.
```

---

## Step 4: Einstein Trust Layer

Before the prompt reaches the AI model, it passes through the Einstein Trust Layer.

The Trust Layer:

- Masks sensitive data
- Checks user permissions
- Retrieves Salesforce data (Grounding)
- Applies security policies
- Logs AI interactions
- Filters unsafe content

This ensures secure and compliant AI responses.

---

## Step 5: Large Language Model (LLM)

The LLM analyzes the prompt and reasons about the user's request.

The model:

- Understands intent
- Interprets context
- Determines what information is needed
- Helps generate a response

**Note:** The LLM does **not** directly access Salesforce.

---

## Step 6: Agentforce Decision Engine

After reasoning, Agentforce decides whether it needs to perform any actions.

Examples:

- Run a Flow
- Execute Apex
- Create a Case
- Update an Opportunity
- Call an external API
- Use an MCP Server

If no action is required, it simply returns a response.

---

## Step 7: Perform Business Actions

Agentforce can execute different types of actions.

### Salesforce Actions

- Create records
- Update records
- Delete records (if permitted)
- Run Flow
- Execute Apex
- Query Salesforce data

### External Actions

- Call REST APIs
- Use MCP Servers
- Connect to ERP systems
- Access GitHub
- Read Slack messages

---

## Step 8: Generate Final Response

Once the required work is complete, Agentforce prepares the final response.

Example:

```
Your order has been cancelled successfully.

Refund Amount:
₹2,500

Expected Refund:
3–5 Business Days
```

---

## Step 9: Response Sent to User

The response is returned to the user.

Conversation complete.

---

# Complete Architecture Example

Customer asks:

```
Cancel my order.
```

Flow:

```text
User

↓

Agentforce

↓

Prompt Builder

↓

Einstein Trust Layer

↓

LLM

↓

Decision Engine

↓

Run Flow

↓

Salesforce

↓

Order Cancelled

↓

Generate Response

↓

User
```

---

# Another Example (Using MCP)

Customer asks:

```
Show my GitHub pull requests.
```

Flow:

```text
User

↓

Agentforce

↓

LLM

↓

Decision Engine

↓

GitHub MCP Server

↓

GitHub API

↓

GitHub

↓

Results

↓

Agentforce

↓

User
```

---

# Components of Agentforce Architecture

## 1. User

Starts the conversation.

Example:

```
Create a support case.
```

---

## 2. Agentforce

Receives the request and manages the conversation.

Responsibilities:

- Understand intent
- Manage context
- Decide next steps

---

## 3. Prompt Builder

Creates the prompt using:

- User request
- Salesforce records
- Instructions
- Templates

---

## 4. Einstein Trust Layer

Provides:

- Security
- Grounding
- Data masking
- Permission checks
- Audit logging
- Safety filtering

---

## 5. Large Language Model

Performs:

- Reasoning
- Language understanding
- Response generation

Examples:

- OpenAI models
- Anthropic models
- Gemini models (depending on configuration)

---

## 6. Decision Engine

Determines:

- Does the AI just answer?
- Does it need Salesforce data?
- Does it need to execute a Flow?
- Does it need to call Apex?
- Does it need an external tool?

---

## 7. Actions

Possible actions include:

- Flow
- Apex
- SOQL
- REST API
- Platform Events
- Data Cloud
- MCP Tools

---

## 8. Salesforce Platform

Stores business data.

Examples:

- Accounts
- Contacts
- Cases
- Opportunities
- Leads

---

## 9. External Systems

Examples:

- GitHub
- Slack
- SAP
- Jira
- SQL Databases
- ERP Systems

Typically accessed through APIs or MCP Servers.

---

# Architecture Diagram (Detailed)

```text
                        User
                          │
                          ▼
                 Agentforce Agent
                          │
             Understand User Intent
                          │
                          ▼
                 Prompt Builder
                          │
                          ▼
              Einstein Trust Layer
    ┌─────────────────────────────────────┐
    │ • Data Masking                      │
    │ • Grounding                         │
    │ • Access Control                    │
    │ • Audit Trail                       │
    │ • Safety Filtering                  │
    └─────────────────────────────────────┘
                          │
                          ▼
                Large Language Model
                          │
                          ▼
               Agentforce Decision Engine
          ┌───────────────┼────────────────┐
          ▼               ▼                ▼
     Salesforce       Flow/Apex      External APIs
       Records                            │
                                           ▼
                                     MCP Server
                                           │
                                           ▼
                                   External Systems
                          │
                          ▼
                  Final AI Response
                          │
                          ▼
                         User
```

---

# Easy Way to Remember

| Component | Purpose |
|-----------|---------|
| User | Asks the question |
| Agentforce | Understands the request |
| Prompt Builder | Builds the AI prompt |
| Einstein Trust Layer | Protects and grounds data |
| LLM | Reasons and generates responses |
| Decision Engine | Chooses what actions to perform |
| Actions | Runs Flow, Apex, APIs, MCP tools |
| Salesforce | Stores business data |
| External Systems | Provide additional data or services |
| User | Receives the final answer |

---

# Interview Questions

## Q1. Explain the Agentforce Architecture.

**Answer:**

Agentforce Architecture starts with the user's request. The request is processed by Agentforce, Prompt Builder creates the prompt, the Einstein Trust Layer secures and grounds the data, the LLM reasons over the request, the Decision Engine selects the required actions, Salesforce Flows, Apex, APIs, or MCP tools are executed if needed, and the final response is returned to the user.

---

## Q2. Where does Prompt Builder fit?

**Answer:**

Prompt Builder creates the structured prompt by combining instructions, Salesforce data, and user input before sending it through the Einstein Trust Layer to the LLM.

---

## Q3. Why is the Einstein Trust Layer important?

**Answer:**

It protects Salesforce data, enforces user permissions, masks sensitive information, grounds prompts with Salesforce data, filters unsafe content, and logs AI interactions.

---

## Q4. Does the LLM access Salesforce directly?

**Answer:**

No. The LLM does not directly access Salesforce. Agentforce retrieves the required data through Salesforce services and the Einstein Trust Layer, then provides the necessary context to the model.

---

## Q5. Where does MCP fit into the architecture?

**Answer:**

MCP is used when Agentforce needs to interact with external applications. Agentforce communicates with an MCP Server, which translates MCP requests into the external application's native API calls and returns the results.

---

# One-Line Memory Trick

- **User** → Asks.
- **Agentforce** → Understands.
- **Prompt Builder** → Builds.
- **Trust Layer** → Protects.
- **LLM** → Reasons.
- **Decision Engine** → Decides.
- **Flow/Apex/API/MCP** → Acts.
- **Response** → Returns.

## Interview One-Liner

> **Agentforce Architecture consists of the user request, Prompt Builder, Einstein Trust Layer, Large Language Model, Decision Engine, Salesforce actions, and optional external integrations through APIs or MCP, working together to securely understand requests, execute business processes, and return intelligent responses.**

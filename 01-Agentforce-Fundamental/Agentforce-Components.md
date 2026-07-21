# Agentforce Components

## What are Agentforce Components?

Agentforce is made up of several components that work together to understand user requests, retrieve business data, execute actions, and generate intelligent responses.

Think of Agentforce like a human employee:

- The **User** asks a question.
- The **Agent** understands it.
- The **LLM** thinks about it.
- **Prompt Builder** prepares the instructions.
- **Trust Layer** ensures security.
- **Actions** perform the work.
- **Salesforce & External Systems** provide the data.
- The **Response** is sent back to the user.

---

# Agentforce Components Overview

```text
                    User
                      │
                      ▼
               Agentforce Agent
                      │
                      ▼
               Prompt Builder
                      │
                      ▼
          Einstein Trust Layer
                      │
                      ▼
           Large Language Model
                      │
                      ▼
              Agent Actions
        ┌─────────┼──────────┐
        ▼         ▼          ▼
     Salesforce  Flow      Apex
        │
        ▼
External APIs / MCP Servers
        │
        ▼
 External Applications
        │
        ▼
     Final Response
```

---

# 1. User

## What is it?

The person interacting with Agentforce.

Examples:

- Customer
- Sales Representative
- Service Agent
- Administrator
- Partner

### Example

```
Show my open opportunities.
```

The user starts the interaction.

---

# 2. Agentforce Agent

## What is it?

The AI agent that receives the user's request and manages the conversation.

Responsibilities:

- Understand user intent
- Maintain conversation context
- Decide whether an action is needed
- Coordinate the overall process

### Example

User:

```
Cancel my order.
```

Agent:

```
Intent:
Cancel Order
```

---

# 3. Prompt Builder

## What is it?

Prompt Builder creates the prompt sent to the Large Language Model.

It combines:

- User request
- Instructions
- Salesforce data
- Prompt templates
- Business context

### Example

```
You are a customer support agent.

Summarize this case professionally.

Case Details:
...
```

---

# 4. Einstein Trust Layer

## What is it?

The security layer between Salesforce and the Large Language Model.

Responsibilities:

- Data masking
- Permission checks
- Grounding
- Audit logging
- Safety filtering
- Secure data retrieval

### Why is it important?

Without it, sensitive Salesforce data could be exposed to the AI model.

---

# 5. Large Language Model (LLM)

## What is it?

The AI model responsible for reasoning and generating natural language.

Responsibilities:

- Understand language
- Interpret context
- Generate responses
- Plan actions

Examples:

- OpenAI models
- Anthropic models
- Gemini models (depending on configuration)

> **Important:** The LLM does not directly access Salesforce data. It receives only the context provided through Agentforce and the Einstein Trust Layer.

---

# 6. Agent Actions

## What are they?

Actions are the operations that Agentforce can perform to complete a task.

Examples:

- Create Record
- Update Record
- Delete Record
- Query Records
- Send Email
- Invoke Flow
- Execute Apex
- Call REST API

### Example

```
Create a support case.
```

↓

```
Run Flow
```

↓

```
Case Created
```

---

# 7. Salesforce Data

## What is it?

Business data stored in Salesforce.

Examples:

- Accounts
- Contacts
- Leads
- Opportunities
- Cases
- Knowledge Articles
- Data Cloud Records

This data is used to ground AI responses.

---

# 8. Flows

## What are they?

Declarative automations that Agentforce can invoke.

Examples:

- Create Case
- Cancel Order
- Update Opportunity
- Send Notification

### Benefit

No coding required.

---

# 9. Apex

## What is it?

Custom business logic written in Apex.

Used when:

- Complex calculations are needed
- External integrations are required
- Custom validation is required
- Advanced automation is needed

---

# 10. External APIs

## What are they?

APIs that connect Agentforce to systems outside Salesforce.

Examples:

- Payment Gateway
- ERP
- SAP
- Inventory System
- Shipping Service

---

# 11. MCP Server

## What is it?

An MCP Server connects Agentforce to external applications using the Model Context Protocol.

Examples:

```
Agentforce

↓

GitHub MCP Server

↓

GitHub
```

or

```
Agentforce

↓

Slack MCP Server

↓

Slack
```

The MCP Server translates between MCP and the application's native API.

---

# 12. External Applications

Examples:

- GitHub
- Slack
- Jira
- SAP
- SQL Database
- Google Drive
- Internal Enterprise Systems

Agentforce can retrieve data from or perform actions on these systems.

---

# 13. Final Response

After processing is complete, Agentforce returns the response to the user.

Example:

```
Your support case has been created successfully.

Case Number:
00012345
```

---

# Complete Component Flow

```text
User

↓

Agentforce Agent

↓

Prompt Builder

↓

Einstein Trust Layer

↓

Large Language Model

↓

Agent Actions

↓

Salesforce / Flow / Apex

↓

External APIs / MCP

↓

External Applications

↓

Generate Response

↓

User
```

---

# Components Summary

| Component | Purpose |
|-----------|---------|
| User | Starts the conversation |
| Agentforce Agent | Understands requests and manages conversations |
| Prompt Builder | Creates prompts for the LLM |
| Einstein Trust Layer | Security, grounding, permissions, masking |
| Large Language Model | Reasoning and language generation |
| Agent Actions | Executes business operations |
| Salesforce Data | Enterprise business data |
| Flows | Declarative automation |
| Apex | Custom business logic |
| External APIs | Connect to external services |
| MCP Server | Standardized bridge to external applications |
| External Applications | Third-party or internal systems |
| Final Response | Returns results to the user |

---

# Real-Life Example

### User

```
Show my open GitHub pull requests.
```

Flow:

```text
User

↓

Agentforce Agent

↓

Prompt Builder

↓

Einstein Trust Layer

↓

LLM

↓

GitHub Tool

↓

GitHub MCP Server

↓

GitHub API

↓

GitHub

↓

Results

↓

LLM generates response

↓

User
```

---

# Interview Questions

## Q1. What are the main components of Agentforce?

**Answer:**

The main components are the User, Agentforce Agent, Prompt Builder, Einstein Trust Layer, Large Language Model, Agent Actions, Salesforce Data, Flows, Apex, External APIs, MCP Servers, External Applications, and the Final Response.

---

## Q2. What is the role of the Agentforce Agent?

**Answer:**

The Agentforce Agent receives the user's request, understands the intent, manages conversation context, determines whether actions are needed, and coordinates the interaction between the LLM, Salesforce, and external systems.

---

## Q3. What is the purpose of the Einstein Trust Layer?

**Answer:**

The Einstein Trust Layer secures AI interactions by enforcing permissions, masking sensitive data, grounding prompts with Salesforce data, filtering unsafe content, and maintaining audit logs.

---

## Q4. What are Agent Actions?

**Answer:**

Agent Actions are executable operations that allow Agentforce to perform business tasks such as running Flows, executing Apex, creating or updating records, or calling external APIs and MCP tools.

---

## Q5. Why are MCP Servers considered part of the Agentforce ecosystem?

**Answer:**

MCP Servers enable Agentforce to interact with external applications through a standardized protocol. They translate MCP requests into application-specific API calls and return the results, allowing Agentforce to work with systems beyond Salesforce.

---

# Memory Trick

Remember **"UPTTL ASF MEF"**

- **U** → User
- **A** → Agentforce Agent
- **P** → Prompt Builder
- **T** → Trust Layer
- **L** → Large Language Model
- **A** → Agent Actions
- **S** → Salesforce Data
- **F** → Flows
- **A** → Apex
- **E** → External APIs
- **M** → MCP Server
- **E** → External Applications
- **F** → Final Response

---

# Interview One-Liner

> **Agentforce consists of the Agentforce Agent, Prompt Builder, Einstein Trust Layer, Large Language Model, Agent Actions, Salesforce data, automation components like Flows and Apex, and integration components such as external APIs and MCP Servers, all working together to securely understand requests, execute business processes, and deliver intelligent responses.**

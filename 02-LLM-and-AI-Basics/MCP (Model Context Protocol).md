# MCP (Model Context Protocol)

## What is MCP?

MCP (Model Context Protocol) → The protocol (the rules)
MCP Server → A software application that implements those rules and connects to external systems

An MCP Server is optional software that implements the Model Context Protocol for a specific application. It exposes that application's capabilities to AI models in a standardized way. Organizations, vendors, or the open-source community can build MCP Servers for applications that need AI integration.

**MCP (Model Context Protocol)** is an **open standard** that allows AI models (like ChatGPT or Agentforce) to securely connect to external tools, applications, databases, and services.

Think of it as a **USB-C port for AI**.

Just as a USB-C port lets you connect many devices (keyboard, mouse, monitor, hard drive) using one standard, MCP lets an AI connect to many different systems using one common protocol.

> **Simple Definition:**
>
> MCP is a standard communication protocol that enables AI models to access external tools and data in a consistent and secure way.

---

# Why Do We Need MCP?

Imagine an AI without MCP.

```
AI

↓

Can only answer from its own knowledge.
```

It **cannot**:

- Read your database
- Check Salesforce records
- Access Google Drive
- Read GitHub repositories
- Query SQL databases
- Use business applications

---

With MCP:

```
AI

↓

MCP

↓

Salesforce
Google Drive
GitHub
SQL Database
Slack
Jira
```

Now the AI can retrieve information and use external tools.

---

# Simple Real-Life Example

Imagine ChatGPT is a new employee.

Without MCP:

```
Employee

↓

No access to company systems.

↓

Can only answer general questions.
```

---

With MCP:

```
Employee

↓

Access to CRM

↓

Access to Database

↓

Access to Files

↓

Access to Calendar

↓

Can complete work.
```

That's exactly what MCP does for AI.

---

# How MCP Works

```text
User

↓

AI Model

↓

MCP Client

↓

MCP Server

↓

External Tool

↓

Result

↓

AI Response
```

---

# Components of MCP

There are three main components.

## 1. MCP Host

The application where the AI is running.

Examples:

- ChatGPT
- Agentforce
- Claude
- VS Code AI Extension

The host is where the user interacts with the AI.

---

## 2. MCP Client

The client sends requests from the AI to an MCP server.

Think of it as a messenger.

Example:

```
User:

Show today's Jira tickets.

↓

AI

↓

MCP Client

↓

Jira MCP Server
```

---

## 3. MCP Server

The MCP Server connects to the actual application or service.

Examples:

- Salesforce MCP Server
- GitHub MCP Server
- Google Drive MCP Server
- Slack MCP Server
- PostgreSQL MCP Server

It retrieves data or performs actions, then returns the result.

---

# Example 1: Salesforce

User:

```
Show all open cases assigned to me.
```

Flow

```
User

↓

ChatGPT

↓

MCP Client

↓

Salesforce MCP Server

↓

Salesforce Org

↓

Case Records

↓

ChatGPT

↓

User
```

Response

```
You have 5 open cases assigned to you.
```

---

# Example 2: GitHub

User

```
Show my open pull requests.
```

Flow

```
AI

↓

GitHub MCP Server

↓

GitHub

↓

Returns PR List
```

---

# Example 3: Google Drive

User

```
Summarize my meeting notes from Google Drive.
```

Flow

```
AI

↓

Google Drive MCP Server

↓

Meeting Notes

↓

AI Summary
```

---

# Example 4: SQL Database

User

```
Show today's sales.
```

Flow

```
AI

↓

Database MCP Server

↓

SQL Query

↓

Results

↓

AI
```

---

# MCP vs API

Many beginners confuse these.

| API | MCP |
|------|-----|
| Connects one application to another | Connects AI to many tools using one standard |
| Every API is different | One common protocol |
| Developer writes custom integration | AI understands the MCP standard |
| Mostly app-to-app communication | AI-to-tool communication |

### Example

Without MCP:

```
Salesforce API

GitHub API

Slack API

Google API

Different code for each integration.
```

---

With MCP:

```
AI

↓

MCP

↓

Salesforce

GitHub

Slack

Google Drive
```

One standard.

---

# MCP vs Agentforce

| MCP | Agentforce |
|------|------------|
| Communication protocol | AI Agent |
| Connects AI to tools | Performs business tasks |
| Standard | Product |
| Used by many AI platforms | Salesforce AI platform |

**Relationship:**

- **MCP** helps the AI connect to external systems.
- **Agentforce** uses those connections (or other integrations) to complete work.

---

# Real Salesforce Example

Customer asks:

```
Where is my order?
```

Agentforce:

```
Understand Request

↓

Need Order Details

↓

MCP connects to Order System

↓

Retrieve Order

↓

Generate Response

↓

Customer
```

Without MCP, the AI cannot access the external order system.

---

# Benefits of MCP

- Standard way to connect AI to tools
- Secure communication
- Reusable integrations
- Easy to add new tools
- Reduces custom integration work
- Works across multiple AI platforms

---

# Architecture

```text
             User
               │
               ▼
        AI (ChatGPT/Agentforce)
               │
               ▼
          MCP Client
               │
               ▼
          MCP Server
               │
      ┌────────┼─────────┐
      ▼        ▼         ▼
 Salesforce  GitHub   Google Drive
      ▼        ▼         ▼
      Data    Data      Data
               │
               ▼
        AI Generates Response
```

---

# Easy Way to Remember

| Component | Easy Meaning |
|-----------|--------------|
| MCP Host | Where the AI runs |
| MCP Client | Sends requests |
| MCP Server | Connects to external tools |
| External Tool | Salesforce, GitHub, Slack, SQL, etc. |

---

# Interview Questions

## Q1. What is MCP?

**Answer:**

MCP (Model Context Protocol) is an open standard that enables AI models to securely communicate with external tools, applications, databases, and services through a common protocol.

---

## Q2. Why do we need MCP?

**Answer:**

MCP allows AI models to access real-time data and use external tools instead of relying only on their built-in knowledge.

---

## Q3. What are the main components of MCP?

**Answer:**

- MCP Host
- MCP Client
- MCP Server

---

## Q4. How is MCP different from an API?

**Answer:**

An API is an interface for application-to-application communication, while MCP is a standardized protocol designed specifically for AI-to-tool communication across many different systems.

---

## Q5. Does MCP replace APIs?

**Answer:**

No. MCP **uses** existing APIs or other interfaces behind the scenes. It provides a standard way for AI applications to discover and use those tools without each AI needing a different integration.

---

# Final Summary

| Term | Meaning |
|------|---------|
| MCP | Standard protocol for AI to communicate with tools |
| Host | The application running the AI |
| Client | Sends requests from the AI |
| Server | Connects to external systems |
| Tool | Salesforce, GitHub, SQL, Slack, Google Drive, etc. |

---

# One-Line Memory Trick

- **Host** → Where the AI lives.
- **Client** → Sends the request.
- **Server** → Talks to the external tool.
- **Tool** → Provides the data or performs the action.

## Interview One-Liner

> **MCP (Model Context Protocol) is an open standard that enables AI applications like ChatGPT or Agentforce to securely discover, connect to, and interact with external tools and data sources through a common protocol, reducing the need for custom integrations.**

# What Exactly is an MCP Server?

The **MCP Server is NOT the actual application** (like Salesforce or GitHub).

It is a **translator (adapter)** that knows **how to talk to that application** and expose its capabilities in a standard MCP format.

Think of it like a waiter in a restaurant.

---

# Restaurant Example

Imagine this:

```
You (Customer)

↓

Waiter

↓

Kitchen

↓

Food
```

Who actually cooks the food?

✅ Kitchen

Who talks to you?

✅ Waiter

Who understands both you and the kitchen?

✅ Waiter

The **waiter is the MCP Server**.

The **kitchen is Salesforce (or GitHub, SQL, etc.)**.

---

# Real Salesforce Example

Suppose you ask ChatGPT:

> Show my open cases.

ChatGPT has no idea:

- How to log in to Salesforce
- Which API to call
- What SOQL query to write
- How Salesforce returns data

It only knows:

> "The user wants open cases."

So what happens?

```
You

↓

ChatGPT

↓

MCP Server

↓

Salesforce

↓

Open Cases

↓

MCP Server

↓

ChatGPT

↓

You
```

Notice:

**ChatGPT never talks directly to Salesforce.**

The MCP Server does.

---

# Why Can't ChatGPT Talk Directly?

Because every application is different.

Salesforce has its own APIs.

GitHub has different APIs.

Slack has different APIs.

SQL has SQL queries.

Google Drive has another API.

If ChatGPT had to learn every API, it would become extremely complicated.

Instead,

every application has an MCP Server.

---

# Think of MCP Server as a Translator

Suppose:

You only know English.

Salesforce only understands Salesforce APIs.

```
English

↓

Translator

↓

Salesforce API
```

The translator is the MCP Server.

---

# What Does the MCP Server Actually Do?

It mainly does five things.

## 1. Receives the AI request

ChatGPT says

```
Get all open cases.
```

The MCP Server receives it.

---

## 2. Understands the request

It knows

```
"Open cases"

means

SELECT Id, CaseNumber, Status
FROM Case
WHERE Status='Open'
```

It converts the request into something Salesforce understands.

---

## 3. Calls Salesforce

The MCP Server makes the API call.

```
Salesforce REST API

↓

Returns Records
```

---

## 4. Formats the Result

Salesforce returns something like

```json
{
  "records":[
      {
        "CaseNumber":"000123",
        "Status":"Open"
      }
  ]
}
```

The MCP Server converts it into the standard MCP format.

---

## 5. Sends it Back

Now ChatGPT receives

```
Case 000123

Status : Open
```

Now ChatGPT can answer naturally.

---

# Visual Flow

```
User

↓

ChatGPT

↓

MCP Server

↓

Salesforce API

↓

Salesforce Database

↓

Salesforce API

↓

MCP Server

↓

ChatGPT

↓

User
```

---

# Another Example (GitHub)

User says

```
Show my Pull Requests.
```

The MCP Server knows

```
GET /repos/.../pulls
```

ChatGPT doesn't know that.

The MCP Server does.

---

# Another Example (SQL Database)

User

```
How many employees joined this month?
```

ChatGPT doesn't know SQL.

The MCP Server writes

```sql
SELECT COUNT(*)
FROM Employee
WHERE JoiningDate >= '2026-07-01';
```

Executes it.

Returns

```
25 employees.
```

---

# Is MCP Server Different for Every Tool?

YES.

Usually each tool has its own MCP Server.

Example

```
Salesforce MCP Server

GitHub MCP Server

Slack MCP Server

Jira MCP Server

Google Drive MCP Server

MySQL MCP Server
```

Each one knows how to communicate with its own application.

---

# Why Not Connect Directly?

Without MCP

```
ChatGPT

↓

Salesforce API

↓

GitHub API

↓

Slack API

↓

SQL

↓

Google API
```

ChatGPT would need separate code for every system.

Very difficult.

---

With MCP

```
ChatGPT

↓

MCP

↓

Any Tool
```

Every tool follows the same protocol.

---

# Think of it Like a Universal Remote

Imagine you have

- Samsung TV
- LG TV
- Sony TV

Each remote is different.

Now imagine a **universal remote**.

```
Universal Remote

↓

Samsung

↓

LG

↓

Sony
```

You don't learn three remotes.

You learn one.

That's what MCP does for AI.

The **MCP Server makes every tool look the same to the AI**.

---

# Interview Answer

**What is an MCP Server?**

An MCP Server is a software component that sits between an AI application and an external system. It exposes the external system's capabilities using the Model Context Protocol. The server receives requests from the AI, translates them into the application's native API or commands, executes them, formats the results, and returns them to the AI in a standardized way.

---

# One-Line Memory Trick

**AI says:** "I need customer data."

**MCP Server says:** "Don't worry, I'll talk to Salesforce for you."

**Salesforce says:** "Here's the data."

**MCP Server says:** "I'll format it so the AI understands."

**AI says:** "Now I can answer the user."

# MCP (Model Context Protocol) - Interview Questions & Answers

These are some of the most commonly asked interview questions on MCP, especially if you're interviewing for AI, Salesforce Agentforce, or GenAI-related roles.

---

# Q1. What is MCP?

### Answer

MCP (Model Context Protocol) is an open standard that enables AI models to securely communicate with external applications, databases, and tools using a common protocol.

Instead of learning different APIs for every application, the AI communicates using MCP, while the MCP Server translates those requests into the application's native API.

---

# Q2. What is an MCP Server?

### Answer

An MCP Server is a software application that implements the Model Context Protocol.

It acts as a bridge between the AI and an external application.

Its responsibilities include:

- Receiving requests from the AI
- Calling the application's API
- Retrieving data
- Formatting the response according to the MCP protocol
- Sending the response back to the AI

---

# Q3. What is the purpose of an MCP Server?

### Answer

The purpose of an MCP Server is to hide the complexity of an application's APIs from the AI.

Instead of requiring the AI to understand thousands of different APIs, the MCP Server translates between the MCP protocol and the application's native API.

---

# Q4. Does the AI communicate directly with Salesforce?

### Answer

No.

The AI communicates with the Salesforce MCP Server using the MCP protocol.

The Salesforce MCP Server then communicates with Salesforce using Salesforce APIs.

Flow:

```text
AI
 ↓
Salesforce MCP Server
 ↓
Salesforce REST API
 ↓
Salesforce Org
```

---

# Q5. Is an MCP Server the same as MCP?

### Answer

No.

**MCP** is the protocol (the communication standard).

**MCP Server** is the software that implements that protocol and connects to an external system.

Example:

```
HTTP → Protocol

Web Server → Software

Similarly,

MCP → Protocol

MCP Server → Software
```

---

# Q6. What is an MCP Client?

### Answer

An MCP Client is the component inside the AI application that communicates with MCP Servers.

For example:

```
ChatGPT

↓

MCP Client

↓

Salesforce MCP Server
```

The client sends requests and receives responses.

---

# Q7. Why do we need MCP?

### Answer

Every application has different APIs.

Without MCP, AI would need to understand every API individually.

MCP provides one common protocol for all integrations.

This makes AI integrations:

- Simpler
- More scalable
- Easier to maintain

---

# Q8. Can an MCP Server connect to multiple systems?

### Answer

Yes.

An MCP Server can expose tools from multiple applications.

However, in most real-world implementations, each application has its own MCP Server for easier maintenance.

---

# Q9. Does every application have an MCP Server?

### Answer

No.

Applications typically provide APIs.

An MCP Server is optional and must be built if AI needs to communicate with the application using the MCP protocol.

Some vendors provide official MCP Servers, while others are developed by the community or by organizations themselves.

---

# Q10. What happens if an application doesn't have an MCP Server?

### Answer

If no MCP Server exists, you can build one.

The MCP Server will:

- Connect to the application's API
- Implement the MCP protocol
- Expose the application's capabilities to AI applications

---

# Q11. Can I build my own MCP Server?

### Answer

Yes.

You can build an MCP Server using languages like:

- Node.js
- Python
- Java
- Go
- C#

The server follows the MCP specification and communicates with the target application's APIs.

---

# Q12. How does the AI understand an MCP Server?

### Answer

Both the AI's MCP Client and the MCP Server follow the same MCP specification.

The AI sends requests using the MCP protocol.

The MCP Server understands those requests, communicates with the external system, and returns responses in the same protocol.

---

# Q13. What is the difference between an API and an MCP Server?

### Answer

| API | MCP Server |
|------|------------|
| Exposes an application's functionality | Exposes that functionality to AI using MCP |
| Application-to-application communication | AI-to-application communication |
| Specific to each application | Uses one common protocol (MCP) |

---

# Q14. Does an MCP Server replace APIs?

### Answer

No.

An MCP Server **uses existing APIs**.

It sits on top of them and translates MCP requests into API calls.

---

# Q15. What are the main responsibilities of an MCP Server?

### Answer

An MCP Server:

- Implements the MCP protocol
- Authenticates with external systems
- Calls APIs or databases
- Retrieves data
- Formats responses
- Returns results to the AI

---

# Q16. Explain the complete MCP flow.

### Answer

```text
User

↓

AI (ChatGPT / Agentforce)

↓

MCP Client

↓

MCP Server

↓

External API

↓

Application

↓

External API

↓

MCP Server

↓

MCP Client

↓

AI

↓

User
```

---

# Q17. Can one AI connect to multiple MCP Servers?

### Answer

Yes.

One AI application can connect to many MCP Servers.

Example:

```
ChatGPT

↓

Salesforce MCP Server

GitHub MCP Server

Slack MCP Server

SQL MCP Server
```

The AI uses the same MCP protocol for all of them.

---

# Q18. Can one MCP Server expose multiple tools?

### Answer

Yes.

An MCP Server can expose multiple tools.

Example:

```
Salesforce MCP Server

↓

Get Accounts

↓

Get Cases

↓

Create Lead

↓

Update Opportunity

↓

Delete Contact
```

Each tool performs a different task.

---

# Q19. What are MCP Tools?

### Answer

Tools are functions exposed by an MCP Server that the AI can invoke.

Examples:

```
getCases()

createLead()

updateAccount()

searchKnowledge()

cancelOrder()
```

The AI selects the appropriate tool based on the user's request.

---

# Q20. What are MCP Resources?

### Answer

Resources are data sources that the MCP Server exposes to the AI.

Examples:

- Files
- Documents
- Database records
- Knowledge articles
- Configuration files

The AI reads resources to answer questions or complete tasks.

---

# Q21. What are the benefits of MCP?

### Answer

- Standard communication protocol
- Easy AI integrations
- Reusable architecture
- Supports multiple applications
- Reduces custom integration code
- Easier maintenance
- Scalable

---

# Q22. Give a real Salesforce example.

### Answer

User:

> Show all open cases assigned to me.

Flow:

```
ChatGPT

↓

MCP Client

↓

Salesforce MCP Server

↓

Salesforce REST API

↓

Salesforce Org

↓

Salesforce REST API

↓

Salesforce MCP Server

↓

ChatGPT
```

Final Response:

> You have 5 open cases assigned to you.

---

# Q23. Why is MCP becoming popular?

### Answer

As AI applications need to interact with more external systems, MCP provides a standardized, reusable way to connect AI to those systems without requiring custom integrations for each one.

---

# Interview One-Liners

### What is MCP?

> MCP is an open standard that enables AI models to communicate with external tools and applications using a common protocol.

---

### What is an MCP Server?

> An MCP Server is software that implements the MCP protocol and translates AI requests into application-specific API calls.

---

### Why is MCP needed?

> MCP removes the need for AI models to understand every application's unique API by providing a single standardized communication protocol.

---

### Does MCP replace APIs?

> No. MCP builds on top of existing APIs and standardizes how AI applications access them.

---

### What is the biggest advantage of MCP?

> It allows AI to integrate with many different systems using one consistent protocol instead of learning thousands of different APIs.

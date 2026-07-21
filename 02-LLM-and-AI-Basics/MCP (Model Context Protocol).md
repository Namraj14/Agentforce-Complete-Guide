# MCP (Model Context Protocol)

## What is MCP?

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

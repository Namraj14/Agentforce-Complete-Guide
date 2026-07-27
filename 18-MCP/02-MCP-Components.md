# Model Context Protocol (MCP)
# Part 2 – MCP Components (Host, Client, Server, Tools, Resources, Prompts & Sampling)

> **Goal of this chapter**
>
> By the end of this README, you'll understand:
>
> - Every component of MCP
> - How each component communicates
> - Complete request lifecycle
> - Difference between Host, Client and Server
> - Difference between Tools, Resources and Prompts
> - What Sampling is
> - Why these components exist
> - Real-world examples

---

# Table of Contents

1. Recap
2. The Big Picture
3. MCP Host
4. MCP Client
5. MCP Server
6. Host vs Client vs Server
7. Tools
8. Resources
9. Prompts
10. Sampling
11. Complete Request Lifecycle
12. Real-world Examples
13. Interview Questions
14. Summary

---

# Recap

From Part 1 we learned:

```
User
   |
AI
   |
MCP
   |
External System
```

Looks simple...

But internally many components work together.

Today we'll understand every one of them.

---

# The Big Picture

Let's first see the complete architecture.

```
                  USER
                    |
                    |
             "Create a Case"
                    |
                    |
       +----------------------------+
       |         MCP HOST           |
       | (Claude Desktop, VS Code,  |
       | ChatGPT App, Cursor etc.)  |
       +----------------------------+
                    |
             MCP CLIENT
                    |
=========================================
          MODEL CONTEXT PROTOCOL
=========================================
          |                |
          |                |
     MCP SERVER       MCP SERVER
     Salesforce        GitHub
          |                |
      Salesforce API    GitHub API
          |                |
      Salesforce       GitHub
```

Every component has one responsibility.

This follows a software engineering principle:

> **One component should have one clear responsibility.**

---

# Think Like a Restaurant

We'll use one analogy throughout this chapter.

Imagine you're eating at a restaurant.

```
Customer
↓

Waiter

↓

Kitchen

↓

Chef

↓

Food
```

Each person has a role.

Nobody does everything.

Exactly the same happens inside MCP.

---

# Component 1 — MCP Host

## What is a Host?

The **Host** is the application where the user interacts with AI.

It is the application that contains the AI experience.

Examples:

- Claude Desktop
- Cursor
- VS Code
- ChatGPT Desktop (future MCP implementations)
- AI-powered IDEs
- Enterprise AI Chat Applications

The Host is what the user sees.

---

## Restaurant Analogy

Customer enters restaurant.

Restaurant building = Host

Without the restaurant,

there is nowhere to place the order.

---

## Example

You open Cursor.

You type:

```
Explain this code.
```

Cursor is the Host.

---

Another example.

You open Claude Desktop.

You ask:

```
Read my local files.
```

Claude Desktop is the Host.

---

# Responsibilities of the Host

The Host is responsible for:

- Showing chat UI
- Accepting user input
- Displaying AI responses
- Managing conversations
- Managing available MCP servers
- Starting MCP clients
- Managing permissions
- Displaying tool approval prompts (when required)

Think of it as:

> The operating environment for AI.

---

# Important

The Host **does NOT** directly communicate with Salesforce.

It communicates through an MCP Client.

---

# Component 2 — MCP Client

This is one of the most misunderstood parts.

Let's simplify it.

---

## What is an MCP Client?

The MCP Client is the component that speaks the MCP language.

It lives inside (or alongside) the Host.

Think of it as:

> The messenger between the Host and the MCP Server.

---

Restaurant analogy

Customer says

```
I want Pizza.
```

Customer does NOT walk into the kitchen.

Instead,

the waiter takes the order.

The waiter = MCP Client.

---

## Responsibilities

The Client:

- Discovers servers
- Discovers available tools
- Discovers resources
- Discovers prompts
- Sends requests
- Receives responses
- Returns results to the Host

---

## Visual

```
Host

↓

Client

↓

Server
```

Host never skips the client.

---

# Component 3 — MCP Server

The MCP Server is where the real work happens.

---

## What is a Server?

A server exposes capabilities to the AI.

Examples:

Salesforce Server

Can expose:

- Create Case
- Update Account
- Search Contact
- Get Opportunity

GitHub Server

Can expose:

- Create Issue
- Read Repository
- Commit Code
- Create Pull Request

Database Server

Can expose:

- Execute SQL
- Read Table
- Insert Record

---

Restaurant analogy

Kitchen = MCP Server

The kitchen knows how to cook.

The waiter doesn't.

---

## Responsibilities

The server:

- Receives requests
- Validates them
- Authenticates
- Calls APIs
- Reads files
- Queries databases
- Returns results

---

# What Lives Inside an MCP Server?

Think of a toolbox.

```
MCP Server

├── Tools
├── Resources
├── Prompts
└── Business Logic
```

We'll understand each one.

---

# Tools

One of the most important concepts.

---

## What is a Tool?

A Tool is an action.

It does something.

Usually it changes something or performs an operation.

Examples:

```
Create Case

Delete Contact

Send Email

Generate PDF

Search GitHub

Create Jira Ticket

Execute SQL

Create Calendar Event
```

Notice something?

Every tool is a verb.

Because actions are verbs.

---

## Real Example

Salesforce Server

Tool:

```
createCase()
```

Input

```
Subject

Priority

Description
```

Output

```
Case Number

Status

Id
```

---

User asks:

```
Create a high priority Case.
```

AI chooses

```
createCase()
```

---

# Characteristics of Tools

Tools:

✔ Accept inputs

✔ Perform work

✔ Return outputs

✔ Can call APIs

✔ Can modify data

✔ Can trigger workflows

---

# Resources

Resources are completely different.

---

## What is a Resource?

Resources are information.

They are read by AI.

Usually,

they don't perform actions.

Examples

```
Company Handbook

Employee Policy

Sales PDF

Knowledge Base

Documentation

CSV

Markdown

Configuration File

Database Record
```

Notice

These are all nouns.

Not actions.

---

Restaurant analogy

Menu Card

The menu doesn't cook food.

It provides information.

Exactly like a Resource.

---

Example

```
Employee Handbook.pdf
```

The AI reads it.

No data changes.

---

Another Example

```
API Documentation
```

AI reads it.

No action.

---

# Characteristics of Resources

Resources

✔ Readable

✔ Informational

✔ Usually don't modify data

✔ Used as context

---

# Difference

Tool

```
Create Employee
```

Action.

---

Resource

```
Employee Handbook
```

Information.

---

# Prompts

Prompts are reusable instructions.

---

Imagine every employee asks

```
Summarize this PDF.
```

Again.

Again.

Again.

Instead of typing it every day...

The server can provide a reusable prompt.

---

Example

Prompt

```
Summarize this meeting.

Mention

• Action Items

• Risks

• Timeline

• Next Steps
```

The AI simply uses the prompt.

---

Another Example

```
Review this Pull Request.

Check

Security

Performance

Naming

Coding Standards
```

Reusable.

---

Restaurant analogy

Chef's Special Recipe.

Instead of creating a recipe every day,

the restaurant already has one.

---

Characteristics

Prompts

✔ Reusable

✔ Save time

✔ Standardize AI behavior

✔ Reduce prompt engineering effort

---

# Sampling

Sampling is an advanced concept.

Many beginners confuse it.

Let's simplify.

---

Suppose

The Server wants AI to generate text.

Instead of generating text itself,

the Server asks the Model.

This is called

Sampling.

---

Visual

```
Host

↓

Client

↓

Server

↓

Model

↓

Server

↓

Client

↓

Host
```

Notice

The Server itself does not become intelligent.

It simply asks the AI model to generate or analyze content when needed.

---

Example

Suppose a GitHub server says

```
Please summarize these 100 changed files.
```

Instead of implementing a summarizer,

it asks the Model.

The generated summary is returned to the server, which then continues its work.

---

Why Sampling?

Because

The Server shouldn't reinvent AI capabilities.

The Model already knows language.

---

# Putting Everything Together

Suppose user says

```
Create a Salesforce Case.
```

Let's follow the journey.

---

Step 1

User types

```
Create a Case.
```

↓

Host receives it.

---

Step 2

Host sends it to

Client.

---

Step 3

Client asks

```
Which servers are available?
```

Available

```
Salesforce

GitHub

Slack
```

---

Step 4

Client asks Salesforce Server

```
Which tools do you have?
```

Response

```
Create Case

Search Case

Update Case

Close Case
```

---

Step 5

Model decides

```
Use Create Case.
```

---

Step 6

Client sends

```
Create Case
```

to

Salesforce Server.

---

Step 7

Server calls Salesforce API.

---

Step 8

Salesforce creates Case.

---

Step 9

Salesforce returns

```
Case Number

00012345
```

---

Step 10

Server returns result.

↓

Client.

↓

Host.

↓

User.

Done.

---

# Complete Lifecycle Diagram

```
User

↓

Host

↓

Model

↓

Client

↓

Server

↓

Salesforce API

↓

Salesforce

↓

Salesforce API

↓

Server

↓

Client

↓

Model

↓

Host

↓

User
```

Every request follows a similar path.

---

# Example 2

User

```
Read README.md
```

AI sees

No action.

Only reading.

Therefore

It chooses

```
Resource
```

instead of Tool.

---

# Example 3

User

```
Summarize README.md
```

Flow

Resource

↓

Read file

↓

Sampling

↓

Model summarizes

↓

Return answer

---

# Example 4

User

```
Send an Email.
```

AI chooses

```
Tool
```

because

Email changes something.

---

# Example 5

User

```
Explain company leave policy.
```

AI chooses

```
Resource
```

because

It only needs information.

---

# One Diagram Explaining Everything

```
                  USER
                    |
             "Create Case"
                    |
              MCP HOST
                    |
             MCP CLIENT
                    |
        ------------------------
        |          |          |
      Tools    Resources   Prompts
        |
        |
    MCP SERVER
        |
 Salesforce REST API
        |
   Salesforce Org
```

If the task only needs information, the server may return a Resource.

If the task requires an action, the server exposes a Tool.

If the task can benefit from standardized instructions, the server may also provide Prompts.

---

# Host vs Client vs Server

| Host | Client | Server |
|-------|--------|--------|
| User-facing application | Speaks MCP | Connects to external systems |
| Shows UI | Sends requests | Performs work |
| Displays responses | Discovers capabilities | Calls APIs |
| Starts conversations | Routes messages | Returns results |

---

# Tool vs Resource vs Prompt

| Tool | Resource | Prompt |
|------|----------|---------|
| Performs action | Provides information | Reusable instruction |
| Usually modifies something | Usually read-only | Guides the model |
| Accepts parameters | Usually doesn't | Often parameterized |
| Example: Create Case | Example: PDF | Example: Summarize Document |

---

# Common Interview Questions

## What is an MCP Host?

The application that provides the AI experience to the user and manages MCP clients and servers.

---

## What is an MCP Client?

A component that implements the Model Context Protocol, discovers server capabilities, sends requests, and returns responses between the Host and MCP Servers.

---

## What is an MCP Server?

A service that exposes tools, resources, and prompts to AI applications while communicating with external systems through their native APIs or SDKs.

---

## Difference between Tool and Resource?

A Tool performs an operation (such as creating or updating data), whereas a Resource provides information that the model can read and use as context.

---

## What is Sampling?

Sampling is the process where an MCP Server asks the AI model to generate or analyze content as part of completing a request, instead of implementing language-generation logic itself.

---

# Summary

Think of MCP like a restaurant:

| Restaurant | MCP |
|------------|-----|
| Restaurant Building | Host |
| Waiter | Client |
| Kitchen | Server |
| Cooking | Tool |
| Menu Card | Resource |
| Recipe Book | Prompt |
| Chef's Intelligence | AI Model (used via Sampling when needed) |

---

# Key Takeaways

- **Host** is the application users interact with.
- **Client** speaks the MCP protocol and coordinates communication.
- **Server** exposes capabilities and connects to external systems.
- **Tools** perform actions.
- **Resources** provide information.
- **Prompts** provide reusable instructions.
- **Sampling** allows a server to leverage the AI model for language tasks.
- Together, these components allow AI to interact with external systems in a standardized, secure, and extensible way.

---

## Next Chapter

In **Part 3**, we'll go deeper into the communication layer:

- JSON-RPC 2.0
- Requests
- Responses
- Notifications
- Transport Layer
- STDIO
- HTTP
- Server-Sent Events (SSE)
- WebSockets
- Authentication
- Message Flow
- Error Handling
- Complete Protocol Examples

After Part 3, you'll understand what actually travels "over the wire" when a Host communicates with an MCP Server.

---
**End of Part 2**

# Model Context Protocol (MCP)
# Part 4 – Building an MCP Server (Beginner → Advanced)

---

# Table of Contents

1. Introduction
2. What Happens Inside an MCP Server?
3. MCP Server Architecture
4. Folder Structure
5. Main Components
6. Server Startup Lifecycle
7. Registering Tools
8. Registering Resources
9. Registering Prompts
10. Request Flow
11. Validation
12. Error Handling
13. Logging
14. Configuration
15. Security
16. Real-World Example (Salesforce)
17. Best Practices
18. Summary

---

# Introduction

In the previous chapters, we learned:

```
User

↓

Host

↓

Client

↓

Server

↓

Salesforce
```

Now the question becomes...

> **What actually exists inside the Server?**

Imagine opening the engine of a car.

From outside...

You only see a car.

Inside...

Hundreds of components work together.

An MCP Server is the same.

---

# What Happens Inside an MCP Server?

Imagine someone asks

```
Create a Salesforce Case.
```

The server doesn't magically know what to do.

Internally, it follows a sequence:

```
Receive Request

↓

Authenticate User

↓

Validate Input

↓

Find Requested Tool

↓

Execute Tool

↓

Call Salesforce API

↓

Receive Result

↓

Convert to MCP Response

↓

Return to Client
```

Every request follows similar steps.

---

# High-Level Architecture

```
                    MCP SERVER

        +-------------------------------+
        |      Request Listener          |
        +-------------------------------+
                    |
                    ▼
        +-------------------------------+
        |      Authentication           |
        +-------------------------------+
                    |
                    ▼
        +-------------------------------+
        |       Validation              |
        +-------------------------------+
                    |
                    ▼
        +-------------------------------+
        |       Tool Manager            |
        +-------------------------------+
          |         |          |
          ▼         ▼          ▼
      Tools     Resources   Prompts
          |
          ▼
      Business Logic
          |
          ▼
      External APIs
          |
          ▼
        Response
```

Notice something important:

The server has multiple layers.

Each layer has only one responsibility.

This follows the **Single Responsibility Principle (SRP)**.

---

# Typical Folder Structure

There is no mandatory folder structure, but many MCP servers look something like this:

```
mcp-server/

│
├── src/
│
├── tools/
│      create_case
│      update_case
│      delete_case
│
├── resources/
│      handbook
│      faq
│
├── prompts/
│      summarize
│      code_review
│
├── services/
│      salesforce
│      github
│
├── auth/
│      oauth
│
├── config/
│
├── utils/
│
├── logger/
│
├── server
│
└── package.json
```

Notice the separation.

Everything has its own folder.

---

# Why Organize Like This?

Imagine putting everything into one file.

```
20,000 lines

Tools

Resources

Authentication

Logging

Configuration

Everything together.
```

Nightmare.

Instead,

keep responsibilities separated.

---

# Main Components

Every good MCP Server contains these logical parts:

```
Server

├── Configuration

├── Authentication

├── Tool Registry

├── Resource Registry

├── Prompt Registry

├── Logging

├── Error Handling

├── Business Logic

└── API Layer
```

---

# Server Startup Lifecycle

When the server starts, it doesn't immediately wait for requests.

It first prepares itself.

```
Start Server

↓

Read Configuration

↓

Load Environment Variables

↓

Initialize Logger

↓

Connect to Database (if needed)

↓

Authenticate (if needed)

↓

Register Tools

↓

Register Resources

↓

Register Prompts

↓

Start Listening
```

Only then can it accept requests.

---

# Think of Opening a Restaurant

Before customers arrive:

✔ Unlock doors

✔ Turn on lights

✔ Prepare kitchen

✔ Prepare menu

✔ Prepare staff

Only then...

Customers enter.

The server startup is similar.

---

# Registering Tools

Earlier we learned

A Tool = An Action

Examples

```
Create Case

Delete Case

Search Contact

Create Opportunity
```

When the server starts,

it registers every available tool.

Think of it like adding apps to your phone.

Until an app is installed,

you can't open it.

---

Example

Salesforce Server

Available Tools

```
Create Case

Update Case

Close Case

Search Cases

Create Lead

Search Account
```

The client can discover these tools.

---

# Why Register Tools?

Suppose the AI asks

```
Create Invoice
```

But the server only has

```
Create Case
```

The server immediately knows

the tool doesn't exist.

Instead of crashing,

it returns

```
Tool Not Found
```

---

# Registering Resources

Resources provide information.

Examples

```
Employee Handbook

Pricing PDF

Knowledge Base

API Documentation

Terms and Conditions
```

The server registers them during startup.

Then the client can discover them.

---

Example

```
Resources

Employee Handbook

Holiday Calendar

Coding Guidelines

Architecture Diagram
```

The AI can later request one of these resources.

---

# Registering Prompts

Prompts are reusable instructions.

Examples

```
Summarize Meeting

Review Code

Generate Documentation

Create User Story
```

The server exposes these prompts.

Instead of typing them repeatedly,

the AI simply uses them.

---

Think of Netflix.

Movies are registered.

You browse.

You select.

The server behaves similarly.

---

# Tool Execution Flow

Suppose the user says

```
Create a High Priority Case.
```

Flow

```
Request Received

↓

Locate Tool

↓

Validate Parameters

↓

Execute Tool

↓

Business Logic

↓

Salesforce API

↓

Response
```

Every tool follows a similar pipeline.

---

# Business Logic

This is where the real work happens.

Many beginners think

The Tool contains everything.

Not exactly.

Usually,

the Tool only coordinates work.

The actual business rules are handled elsewhere.

Example:

```
Create Case Tool

↓

Validate Input

↓

Call Case Service

↓

Case Service

↓

Salesforce API
```

Separating business logic makes the code easier to maintain and test.

---

# Validation

Imagine this request.

```
Create Case
```

No Subject.

No Priority.

No Description.

Can the server continue?

No.

It validates first.

---

Validation checks

✔ Required fields

✔ Data type

✔ Allowed values

✔ Length

✔ Business rules

---

Example

Priority

Allowed

```
High

Medium

Low
```

User sends

```
Super High
```

Validation fails.

The server responds with an error instead of calling Salesforce.

---

# Error Handling

No software is perfect.

Things go wrong.

Examples

```
Wrong Input

↓

Invalid Authentication

↓

Server Down

↓

Salesforce Timeout

↓

Network Failure

↓

Permission Denied
```

The server should never crash because of one request.

Instead,

it returns meaningful errors.

---

Good Error

```
Priority must be

High

Medium

Low
```

Bad Error

```
Unknown Error
```

Always be descriptive.

---

# Logging

Logging records what happened inside the server.

Imagine debugging without logs.

Impossible.

---

Typical Logs

```
Server Started

↓

Tool Registered

↓

Received Request

↓

Executing Tool

↓

Salesforce API Called

↓

Success

↓

Response Sent
```

If something fails,

logs tell you exactly where.

---

# Example Log Flow

```
10:30 Server Started

10:31 Tool Registered

10:32 Request Received

10:32 Validation Passed

10:32 Salesforce API Called

10:32 Case Created

10:32 Response Returned
```

---

# Configuration

Servers usually need configuration.

Examples

```
Salesforce URL

OAuth Client ID

API Endpoint

Timeout

Database URL

Environment
```

Instead of hardcoding,

store them separately.

Example

```
Development

↓

Sandbox

↓

Production
```

Each environment has different settings.

---

# Security

An MCP Server often has access to sensitive systems.

Security matters.

Common practices:

✔ Authenticate users

✔ Authorize actions

✔ Validate inputs

✔ Encrypt secrets

✔ Use HTTPS for remote servers

✔ Never expose credentials in code

✔ Limit permissions to what's needed

---

# Real-World Example: Salesforce MCP Server

Imagine your company builds a Salesforce MCP Server.

It might expose:

### Tools

```
Create Case

Update Opportunity

Search Account

Create Contact

Delete Lead
```

### Resources

```
Sales Playbook

Support Handbook

Product Catalog

Knowledge Articles
```

### Prompts

```
Summarize Opportunity

Generate Follow-up Email

Analyze Closed Cases

Create Meeting Notes
```

Now a user asks:

```
Create a high-priority case for customer ABC,
then summarize our support playbook.
```

The server:

1. Executes the **Create Case** tool.
2. Reads the **Support Handbook** resource.
3. Uses the **Summarize** prompt.
4. Returns both results to the AI.

All through the same MCP protocol.

---

# Multiple Tools in One Request

Modern AI can chain tools together.

Example

```
Search Account

↓

Create Case

↓

Create Task

↓

Send Slack Notification
```

The server executes each tool as requested, while the model coordinates the overall workflow.

---

# Best Practices

## 1. Keep Tools Small

Instead of

```
Do Everything Tool
```

Create

```
Create Case

Update Case

Delete Case

Search Case
```

Small tools are easier to understand, test, and reuse.

---

## 2. Separate Business Logic

Don't mix:

- API calls
- validation
- logging
- business rules

Keep each concern separate.

---

## 3. Validate Everything

Never trust incoming data.

Validate before execution.

---

## 4. Log Important Events

Useful logs include:

- Startup
- Shutdown
- Tool execution
- Errors
- External API calls

Avoid logging secrets like passwords or access tokens.

---

## 5. Return Helpful Errors

Instead of

```
Failed
```

Return

```
Case Subject is required.
```

Helpful errors make debugging much easier.

---

## 6. Design Stable Tool Interfaces

Changing a tool's inputs frequently can break clients.

Try to keep tool names and parameters consistent over time.

---

# Common Beginner Mistakes

### ❌ One Giant Tool

```
Manage Everything
```

Instead,

create focused tools.

---

### ❌ Hardcoding Credentials

Never write secrets directly into code.

Use secure configuration or secret management.

---

### ❌ Ignoring Validation

Invalid input should be rejected early.

---

### ❌ Mixing Responsibilities

Don't put authentication, logging, validation, and business logic into the same function.

---

### ❌ Returning Generic Errors

Specific errors help users and developers.

---

# Complete Request Lifecycle

```
User

↓

Host

↓

Client

↓

Server

↓

Authenticate

↓

Validate

↓

Find Tool

↓

Execute Tool

↓

Business Logic

↓

External API

↓

Receive Result

↓

Create Response

↓

Client

↓

Host

↓

User
```

This is the journey almost every successful request follows.

---

# Interview Questions

### What is the responsibility of an MCP Server?

An MCP Server exposes tools, resources, and prompts to AI applications and translates MCP requests into interactions with external systems.

---

### Why register tools during startup?

So clients can discover available capabilities before attempting to use them.

---

### Why separate business logic from tools?

It improves maintainability, testability, and reusability.

---

### Why is validation important?

To prevent invalid requests from reaching business logic or external systems.

---

### Why is logging necessary?

To monitor behavior, troubleshoot issues, and understand request execution.

---

# Summary

An MCP Server is much more than a simple API wrapper.

It is a structured application that:

- Starts and initializes itself
- Registers its capabilities
- Validates requests
- Authenticates users
- Executes business logic
- Calls external systems
- Logs activity
- Handles errors gracefully
- Returns standardized MCP responses

Think of the server as a well-organized company:

| Company Department | MCP Server Component |
|--------------------|----------------------|
| Reception | Request Listener |
| Security Guard | Authentication |
| HR | Validation |
| Team Manager | Tool Registry |
| Employees | Business Logic |
| Courier | External APIs |
| Audit Team | Logging |
| Customer Support | Error Handling |

Every department has a job, and together they deliver a reliable service.

---

---
**End of Part 4**

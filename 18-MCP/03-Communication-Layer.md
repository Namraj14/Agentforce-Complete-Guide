# Model Context Protocol (MCP)
# Part 3 – Communication Layer (JSON-RPC, Transports, Requests, Responses, Notifications & Authentication)

---

# Table of Contents

1. Recap
2. How Does Communication Actually Happen?
3. Why Can't AI Just Call APIs?
4. Communication Layers
5. What is JSON?
6. What is RPC?
7. What is JSON-RPC?
8. Anatomy of a JSON-RPC Message
9. Requests
10. Responses
11. Notifications
12. Message IDs
13. Error Responses
14. Transport Layer
15. STDIO
16. HTTP
17. SSE
18. WebSockets
19. Authentication
20. Complete Lifecycle
21. Summary

---

# Recap

So far we've learned:

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

But...

**How do they actually communicate?**

Do they send Java?

Do they send Apex?

Do they send SQL?

No.

They communicate using a standardized message format.

---

# Imagine You're Mailing a Letter

Suppose you send a letter.

```
Hello John
```

That isn't enough.

The post office also needs:

- Sender
- Receiver
- Address
- Tracking Number

Without structure...

Nothing works.

Computers are exactly the same.

---

# Why Can't AI Just Call APIs Directly?

Imagine Salesforce.

Salesforce API

```
POST /services/data/v65.0/sobjects/Case
```

GitHub

```
POST /repos/issues
```

Slack

```
POST /chat.postMessage
```

Each API is different.

Each authentication method is different.

Each response is different.

The AI would need to understand every API in the world.

That doesn't scale.

Instead,

every MCP Server translates between:

```
MCP

↓

Native API
```

---

# Communication Layers

Think of communication as multiple layers.

```
User
    ↓

Host
    ↓

MCP Client
    ↓

JSON-RPC Message
    ↓

Transport
    ↓

MCP Server
    ↓

API
```

Each layer has a job.

---

# What is JSON?

Before learning JSON-RPC...

Let's understand JSON.

JSON means

**JavaScript Object Notation**

Despite the name,

almost every programming language supports JSON.

---

Example

Instead of writing

```
Name = John

Age = 25
```

JSON writes

```json
{
  "name":"John",
  "age":25
}
```

Notice

Everything is organized.

---

Another Example

```json
{
   "caseNumber":"000123",
   "priority":"High",
   "status":"New"
}
```

Very easy for computers to understand.

---

# Why JSON?

Because JSON is

- Lightweight
- Human readable
- Machine readable
- Easy to parse
- Supported everywhere

---

# What is RPC?

RPC means

**Remote Procedure Call**

Let's break it.

Remote

Someone else.

Procedure

A function.

Call

Execute it.

---

Imagine this function.

```java
createCase()
```

Normally

```
Program

↓

createCase()
```

Easy.

But now

The function exists on another computer.

```
Your Computer

↓

Internet

↓

Another Computer

↓

createCase()
```

That's

Remote Procedure Call.

---

Real Life

Imagine ordering food.

You don't cook.

You call the restaurant.

The restaurant cooks.

You receive food.

You remotely executed a function.

---

# What is JSON-RPC?

Now combine both concepts.

JSON

+

RPC

=

JSON-RPC

Meaning

We call remote functions

using

JSON messages.

---

Instead of saying

```
Run createCase()
```

We send

```json
{
  "method":"createCase"
}
```

Simple.

---

# Why Did MCP Choose JSON-RPC?

Because JSON-RPC is

- Simple
- Lightweight
- Language independent
- Easy to debug
- Supports requests and responses
- Widely adopted

---

# JSON-RPC Structure

Every request has four important parts.

```json
{
   "jsonrpc":"2.0",
   "id":1,
   "method":"tools/call",
   "params":{}
}
```

Let's understand every field.

---

# jsonrpc

```json
"jsonrpc":"2.0"
```

This tells both sides

which protocol version they're speaking.

Think of it like saying

```
I speak English.
```

---

# id

```json
"id":1
```

Every request gets an ID.

Why?

Because multiple requests may happen simultaneously.

The response must know

which request it belongs to.

---

Example

```
Request 1

↓

ID = 1

↓

Response

↓

ID = 1
```

Perfect match.

---

# method

This tells

what should happen.

Examples

```
tools/list

resources/list

tools/call

initialize

prompts/list
```

Think of it as

the function name.

---

# params

These are the inputs.

Example

```json
{
   "priority":"High",
   "subject":"Login Issue"
}
```

Just like function parameters.

---

# Putting Everything Together

Suppose

User says

```
Create a Case
```

Client sends

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "method":"tools/call",
    "params":{
        "tool":"create_case",
        "subject":"Login Issue",
        "priority":"High"
    }
}
```

Notice

This is simply

a structured message.

---

# Requests

A Request asks

the server

to do something.

Examples

```
List Tools

Read Resource

Call Tool

Initialize Connection
```

Every request expects

a response.

---

Visual

```
Client

↓

Request

↓

Server

↓

Response
```

---

# Responses

The server answers

with a response.

Example

```json
{
    "jsonrpc":"2.0",
    "id":1,
    "result":{
        "caseNumber":"000123"
    }
}
```

Notice

The response has

the same ID.

---

Why?

Because the client knows

which request completed.

---

# Notifications

Notifications are different.

A notification says

```
I'm just informing you.

No reply needed.
```

---

Example

Imagine WhatsApp.

Single Tick

```
Message Sent
```

No reply required.

That's similar to a notification.

---

Example Notification

```
Server Started

Connection Closed

Progress Updated
```

No response expected.

---

Difference

Request

```
Need Response
```

Notification

```
No Response
```

---

# Why Notifications?

Imagine

Downloading

5GB file.

Instead of waiting

10 minutes...

Server sends

```
20%

40%

60%

80%

Done
```

These are notifications.

---

# Message IDs

Imagine

Five requests.

```
ID 1

ID 2

ID 3

ID 4

ID 5
```

Responses may arrive

in any order.

```
Response 3

↓

Response 1

↓

Response 5

↓

Response 2
```

Without IDs

Chaos.

---

With IDs

Everything matches.

---

# Error Responses

Suppose

Tool doesn't exist.

Instead of crashing

the server responds

```json
{
   "jsonrpc":"2.0",
   "id":1,
   "error":{
      "code":-32601,
      "message":"Method not found"
   }
}
```

Notice

Errors are also structured.

---

Another Example

Wrong parameters

```json
{
    "error":{
        "message":"Priority missing"
    }
}
```

The client understands

what went wrong.

---

# Transport Layer

JSON-RPC defines

the message format.

It does **NOT** define

how messages travel.

That's where

Transport

comes in.

Think of it like this.

Letter

↓

Envelope

↓

Truck

The truck is

Transport.

---

# Types of Transport

Common transports are:

```
STDIO

HTTP

SSE

WebSocket
```

Each has

different use cases.

---

# STDIO

STDIO means

**Standard Input / Standard Output**

This is the simplest transport.

---

Imagine

Two programs

running on the same computer.

```
Host

↓

stdin

↓

Server

↓

stdout

↓

Host
```

No internet required.

---

Example

Claude Desktop

↓

Starts

↓

Local Files Server

Both run

on your computer.

Communication happens

through STDIO.

---

Advantages

✔ Fast

✔ Local

✔ Secure

✔ Easy

---

Disadvantages

❌ Same machine only

---

# HTTP

Everyone knows HTTP.

Browser

↓

Website

HTTP

↓

Server

Exactly the same idea.

---

Example

```
Host

↓

HTTP POST

↓

Remote MCP Server
```

Perfect

for cloud deployments.

---

Advantages

✔ Internet

✔ Scalable

✔ Easy to deploy

---

Disadvantages

Slightly higher overhead than local STDIO.

---

# Server-Sent Events (SSE)

SSE means

Server

↓

Client

continuous updates.

Imagine

Cricket Score.

Instead of refreshing

every second...

The server automatically pushes updates.

---

Visual

```
Server

↓

Client

↓

Client

↓

Client

↓

Client
```

One-way communication.

---

Good for

- Progress updates
- Live logs
- Streaming output
- Notifications

---

# WebSockets

WebSockets allow

both sides

to communicate

at any time.

```
Host

⇅

Server
```

Unlike HTTP

the connection stays open.

---

Real Example

Chat application.

Messages

come instantly.

---

Advantages

✔ Real-time

✔ Bidirectional

✔ Low latency

---

Disadvantages

Slightly more complex.

---

# Which Transport Should You Use?

| Situation | Recommended Transport |
|-----------|-----------------------|
| Local MCP Server | STDIO |
| Cloud MCP Server | HTTP |
| Streaming updates | SSE |
| Real-time interaction | WebSocket |

---

# Authentication

Suppose

Your AI asks

```
Delete every Salesforce Account.
```

Should the server do it?

No.

First

it must verify

who is asking.

That's Authentication.

---

Common Methods

```
OAuth

API Keys

Bearer Tokens

Session Tokens

JWT
```

---

Example

Client

↓

Access Token

↓

Server

↓

Verified

↓

Salesforce API

---

Authentication vs Authorization

Many people confuse these.

Authentication answers:

> **Who are you?**

Authorization answers:

> **What are you allowed to do?**

Example:

You log into Salesforce.

Authentication ✔

You try deleting Accounts.

Salesforce checks your permissions.

Authorization ✔

---

# Complete Lifecycle

Let's see everything together.

User

```
Create a Case.
```

↓

Host

↓

Client

↓

JSON-RPC Request

↓

HTTP (Transport)

↓

MCP Server

↓

Salesforce API

↓

Salesforce

↓

Salesforce API

↓

MCP Server

↓

JSON-RPC Response

↓

HTTP

↓

Client

↓

Host

↓

User

---

ASCII Diagram

```
          USER
             |
             |
         MCP HOST
             |
         MCP CLIENT
             |
      JSON-RPC Message
             |
      ----------------
      |              |
    STDIO         HTTP
      |              |
      ----------------
             |
        MCP SERVER
             |
       Salesforce API
             |
        Salesforce Org
```

---

# Real-World Example

Imagine Cursor AI.

You ask

```
Commit my code.
```

The flow is:

1. Cursor (Host) receives the request.
2. MCP Client creates a JSON-RPC request.
3. The request is sent over STDIO to the local GitHub MCP Server.
4. The GitHub MCP Server authenticates with GitHub.
5. It calls the GitHub API.
6. GitHub creates the commit or pull request.
7. The server returns a JSON-RPC response.
8. Cursor displays the result.

The Host never needs to know the details of the GitHub REST API.

---

# Common Interview Questions

### Why does MCP use JSON-RPC?

Because it provides a simple, lightweight, language-independent way to invoke remote procedures using structured JSON messages.

---

### What is the difference between JSON-RPC and HTTP?

- **JSON-RPC** defines the structure of messages (methods, parameters, IDs, results, errors).
- **HTTP** is one possible transport used to carry those messages.

Think of JSON-RPC as the **letter** and HTTP as the **postal service**.

---

### What is a Notification?

A message that does not expect a response. It's used for events such as progress updates or status changes.

---

### Why are IDs important?

IDs let the client match responses to the correct requests, especially when multiple requests are in flight simultaneously.

---

### Difference between HTTP and WebSocket?

| HTTP | WebSocket |
|-------|-----------|
| Request/Response | Persistent connection |
| Client starts communication | Either side can send messages |
| Good for standard API calls | Good for live updates and chat |

---

# Summary

The communication stack in MCP looks like this:

```
User
   |
Host
   |
MCP Client
   |
JSON-RPC
   |
Transport (STDIO / HTTP / SSE / WebSocket)
   |
MCP Server
   |
External System
```

Key concepts to remember:

- **JSON-RPC** defines the language of communication.
- **Transport** defines how those messages travel.
- **Requests** expect responses.
- **Notifications** do not.
- **IDs** correlate requests and responses.
- **Authentication** verifies identity.
- **Authorization** controls permissions.

---

---
**End of Part 3**

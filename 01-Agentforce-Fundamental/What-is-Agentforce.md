# What is Agentforce?

Agentforce is Salesforce's AI Agent platform that allows organizations to build autonomous AI agents capable of understanding requests, reasoning over data, and executing actions.

Unlike traditional chatbots that follow predefined decision trees, Agentforce can dynamically determine how to respond to a user's request.

## Definition

Agentforce is an AI-powered conversational system that combines:

- Large Language Models (LLMs)
- Salesforce Data
- Business Processes
- Agent Actions
- Grounding
- Trust Layer

to solve customer and employee requests.

## Example

Customer:

"What's the status of my order?"

Agentforce:

1. Understands the intent.
2. Identifies required data.
3. Searches Salesforce records.
4. Retrieves order details.
5. Generates a natural language response.

## Key Capability

Agentforce doesn't simply answer questions.

It can:

- Retrieve Data
- Create Records
- Update Records
- Invoke Flows
- Execute Apex
- Call External APIs

## Real-world Example

Customer:

"I want to cancel my order."

Agentforce may:

1. Verify customer identity.
2. Find order.
3. Check cancellation policy.
4. Execute cancellation action.
5. Confirm cancellation.

All without human intervention.

# Agentforce - The 5 Main Attributes

Whenever you create an Agentforce Agent, there are **5 important attributes** that define how your agent behaves.

They are:

1. Role
2. Data
3. Actions
4. Guardrails
5. Channels

Think of it like hiring a new employee.

- **Role** → What is their job?
- **Data** → What information can they access?
- **Actions** → What work can they do?
- **Guardrails** → What rules must they follow?
- **Channels** → Where can customers talk to them?

---

# 1. Role

## What is Role?

The **Role** tells the AI agent **who it is** and **what its responsibility is**.

It defines the agent's purpose.

Without a role, the AI doesn't know what it is supposed to do.

### Simple Example

Imagine you hire someone in a company.

You tell them:

> "You are a Customer Support Executive."

Now they know their job.

Similarly, in Agentforce you define:

> "You are a Salesforce Customer Support Agent."

Now the AI understands its responsibility.

---

### Salesforce Example

Role:

```
You are a Service Cloud Support Agent.

Your job is to:
- Help customers
- Answer questions
- Create support cases
- Update case status
- Check order details
```

Now the AI knows exactly what it should do.

---

### Real-Life Example

Customer asks:

> Where is my order?

Because the role is "Customer Support Agent", the AI knows it should help with order tracking.

If the role were "Sales Agent", it would instead try to recommend products.

---

## Remember

Role answers:

> **Who am I?**

---

# 2. Data

## What is Data?

Data tells the AI **what information it is allowed to access**.

An AI cannot answer questions if it has no information.

Data can come from:

- Salesforce Records
- Knowledge Articles
- Data Cloud
- External APIs
- PDFs
- CRM Data

---

### Example

Customer asks:

> What is the status of my case?

Agentforce checks Salesforce Case records.

Example:

```
Case Number : 00012345

Status : Working

Priority : High

Owner : Support Team
```

Now it can answer:

> Your case is currently being worked on by our Support Team.

---

### Another Example

Customer asks:

> What is your refund policy?

Instead of guessing, Agentforce searches the company's Knowledge Articles and provides the correct answer.

---

## Remember

Data answers:

> **What information can I use?**

---

# 3. Actions

## What are Actions?

Actions tell Agentforce **what work it is allowed to perform**.

Without actions, the AI can only answer questions.

With actions, it can actually complete tasks.

---

### Salesforce Actions

Examples:

- Create Case
- Update Case
- Create Lead
- Update Opportunity
- Run Flow
- Execute Apex
- Call REST API
- Send Email

---

### Example

Customer:

> Please create a support case.

Agentforce:

```
Runs Flow

↓

Creates Case

↓

Returns Case Number
```

Response:

> Your support case has been created successfully.

---

### Another Example

Customer:

> Update my phone number.

Agentforce:

```
Find Customer

↓

Update Account Record

↓

Save Changes
```

The record is updated automatically.

---

## Remember

Actions answer:

> **What work can I do?**

---

# 4. Guardrails

## What are Guardrails?

Guardrails are **rules and restrictions** that control what the AI is allowed to do.

They help keep the AI safe, accurate, and within company policies.

Without guardrails, the AI could provide incorrect information or perform actions it shouldn't.

---

### Examples of Guardrails

- Don't reveal confidential customer data.
- Don't delete records unless authorized.
- Only answer questions related to customer support.
- Escalate sensitive issues to a human agent.
- Don't generate offensive or harmful content.

---

### Example

Customer:

> Delete all customer records.

Agentforce:

> Sorry, I'm not authorized to perform that action.

The guardrail blocks the request.

---

### Another Example

Customer:

> Tell me another customer's phone number.

Agentforce:

> Sorry, I can't share another customer's personal information.

---

## Remember

Guardrails answer:

> **What am I NOT allowed to do?**

---

# 5. Channels

## What are Channels?

Channels define **where users can interact with Agentforce**.

It is the communication platform through which the AI is available.

---

### Examples

- Salesforce Experience Cloud
- Company Website
- Mobile App
- WhatsApp
- Slack
- Microsoft Teams
- In-App Messaging
- Service Cloud Chat

---

### Example

Customer visits your website.

```
Website

↓

Chat Window

↓

Agentforce
```

The customer starts chatting with Agentforce directly.

---

Another example:

A sales team asks Agentforce questions from Slack.

```
Slack

↓

Agentforce

↓

Salesforce Data
```

---

## Remember

Channels answer:

> **Where can users talk to me?**

---

# Complete Example

Imagine you're creating an Agentforce agent for an online shopping company.

### Role

```
Customer Support Agent
```

### Data

- Orders
- Cases
- Customers
- Knowledge Articles

### Actions

- Create Case
- Cancel Order
- Update Address
- Send Email

### Guardrails

- Don't expose personal information.
- Don't process refunds above ₹50,000.
- Escalate payment disputes to a human agent.

### Channels

- Website Chat
- Mobile App
- WhatsApp
- Experience Cloud

---

# Easy Way to Remember

| Attribute | Easy Question | Example |
|-----------|---------------|---------|
| Role | Who am I? | Customer Support Agent |
| Data | What information can I access? | Salesforce Records, Knowledge |
| Actions | What work can I perform? | Create Case, Run Flow |
| Guardrails | What rules must I follow? | Don't share customer data |
| Channels | Where do users interact with me? | Website, WhatsApp, Slack |

---

# Interview Questions

### Q1. What is the Role in Agentforce?

**Answer:**
Role defines the agent's identity and responsibilities. It tells the AI what job it should perform.

---

### Q2. What is Data in Agentforce?

**Answer:**
Data is the information the AI can access, such as Salesforce records, Knowledge Articles, Data Cloud, or external systems.

---

### Q3. What are Actions?

**Answer:**
Actions are tasks that the AI can perform, such as creating records, running Flows, executing Apex, or calling APIs.

---

### Q4. What are Guardrails?

**Answer:**
Guardrails are safety rules and business policies that restrict what the AI can say or do.

---

### Q5. What are Channels?

**Answer:**
Channels are the platforms where users interact with Agentforce, such as websites, Experience Cloud, mobile apps, WhatsApp, Slack, or Microsoft Teams.

---

# Final Summary

| Attribute | Meaning |
|-----------|---------|
| Role | Defines the agent's job and responsibilities. |
| Data | Information the agent can access to answer questions. |
| Actions | Tasks the agent can perform. |
| Guardrails | Safety rules and business restrictions. |
| Channels | Places where users interact with the agent. |

## One-Line Memory Trick

- **Role** → Who am I?
- **Data** → What do I know?
- **Actions** → What can I do?
- **Guardrails** → What am I not allowed to do?
- **Channels** → Where can people talk to me?

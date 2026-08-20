# Agentforce Limitations

## What are Agentforce Limitations?

Although Agentforce is a powerful AI platform, it is **not a replacement for human judgment or traditional Salesforce automation**. Like any AI system, it has technical, business, and operational limitations that developers and administrators should understand before deploying it in production. Salesforce also documents platform limits around supported features, languages, actions, and timeouts. :contentReference[oaicite:0]{index=0}

---

# Top Agentforce Limitations

---

# 1. Depends on High-Quality Data

Agentforce can only provide good answers if the underlying Salesforce data is accurate and complete.

### Example

If an Opportunity has:

```
Amount = Blank

Stage = Incorrect

Close Date = Missing
```

The AI cannot produce a reliable sales summary.

### Limitation

Poor data quality leads to poor AI responses.

---

# 2. Can Produce Incorrect Answers (Hallucinations)

Like all Large Language Models, Agentforce may occasionally generate incorrect or misleading responses.

### Example

User:

```
What is the refund policy?
```

If the policy is not grounded from Salesforce Knowledge or another trusted source, the AI may provide an inaccurate answer.

### Best Practice

Always ground responses using:

- Salesforce Records
- Knowledge Articles
- Data Cloud
- Trusted External Sources

---

# 3. Requires Proper Grounding

Agentforce does **not automatically know all your Salesforce data**.

You must provide access through:

- Agent Actions
- Flows
- Apex
- Knowledge
- Data Cloud

Without grounding, the AI cannot answer organization-specific questions accurately.

### Example

```
List all premium customers.
```

If no action or retrieval mechanism exists, the agent cannot retrieve the data.

---

# 4. Doesn't Replace Business Logic

Agentforce is **not a substitute** for:

- Validation Rules
- Approval Processes
- Record-Triggered Flows
- Apex Triggers

These continue to enforce business rules.

### Example

A Validation Rule requiring an email address still runs even if the record is created by Agentforce.

---

# 5. Limited by User Permissions

Agentforce follows Salesforce security.

If a user cannot access a record, Agentforce should not expose it.

### Example

Sales Representative:

```
Show HR Salary Records.
```

Response:

```
Access Denied
```

### Benefit

Maintains Salesforce security and sharing rules.

---

# 6. External Integrations Need Configuration

Agentforce cannot automatically connect to:

- GitHub
- SAP
- Slack
- Jira
- ERP Systems

Developers must configure:

- REST APIs
- Named Credentials
- External Services
- MCP Servers

---

# 7. Complex Tasks May Need Apex or Flow

Some business requirements are too complex for prompt instructions alone.

### Example

```
Calculate insurance premium using 25 business rules.
```

This logic is better handled in Apex or Flow.

Agentforce orchestrates the process but often relies on existing business logic.

---

# 8. Performance Depends on External Systems

If an external API is slow or unavailable, Agentforce's response will also be delayed or fail.

### Example

```
Agentforce

↓

Payment Gateway

↓

Gateway Offline
```

↓

```
Request Fails
```

---

# 9. Language Support Has Limits

While Agentforce supports multiple languages, support varies by agent type and feature. Some instructions and action configurations are currently supported only in English, and unsupported languages may lead to inconsistent behavior. :contentReference[oaicite:1]{index=1}

---

# 10. Additional Cost

Using Agentforce may consume:

- Agentforce licenses
- AI requests
- Flex Credits
- Data Services Credits (depending on features used)

Organizations should plan usage carefully. :contentReference[oaicite:2]{index=2}

---

# 11. Not Fully Autonomous

Agentforce does not automatically know:

- Company policies
- Business workflows
- Custom processes

Developers must configure:

- Instructions
- Topics
- Actions
- Prompt Templates
- Knowledge Sources

---

# 12. Cannot Read Everything Automatically

Agentforce does not automatically access:

- Every Salesforce object
- Every custom object
- Every external database
- Every PDF
- Every API

Developers must explicitly expose the required data and capabilities.

---

# 13. Depends on Prompt Quality

Poor instructions produce poor results.

Example:

Bad Prompt:

```
Summarize this.
```

Better Prompt:

```
Summarize this Case in under 100 words, including the issue, current status, next action, and customer impact.
```

Good prompt engineering improves accuracy.

---

# 14. Long or Complex Conversations Have Limits

Very long conversations may lose context or require users to restart the conversation. Salesforce also documents limits on conversation history and action execution time. :contentReference[oaicite:3]{index=3}

---

# 15. Not a Complete Replacement for Humans

Agentforce assists users but should not replace human judgment in situations such as:

- Legal advice
- Medical decisions
- Financial approvals
- High-risk business decisions

Human review remains important.

---

# Real-World Example

### User

```
Cancel my order.
```

Possible limitations:

- Order does not exist
- User lacks permission
- Refund API is unavailable
- Flow contains an error
- Payment gateway is offline

Agentforce cannot complete the task until these issues are resolved.

---

# Limitations Summary

| Limitation | Description |
|------------|-------------|
| Data Quality | Poor data leads to poor responses |
| Hallucinations | AI can generate incorrect information |
| Grounding Required | Needs trusted business data |
| Business Logic | Cannot replace Flows, Apex, or Validation Rules |
| Security | Respects Salesforce permissions |
| External Systems | Require APIs or MCP integration |
| Complex Logic | Often needs Apex or Flow |
| API Dependency | External outages affect responses |
| Language Support | Varies by feature and agent type |
| Cost | AI usage consumes credits/licenses |
| Configuration | Requires setup of actions and prompts |
| Data Access | Cannot automatically access all enterprise data |
| Prompt Quality | Better prompts produce better results |
| Conversation Limits | Long interactions have practical limits |
| Human Oversight | Required for critical decisions |

---

# Interview Questions

## Q1. What are the major limitations of Agentforce?

**Answer:**

Agentforce depends on high-quality data, requires proper grounding, follows Salesforce security permissions, may produce hallucinations, cannot replace business logic like Apex or Flows, requires configuration for external integrations, and still needs human oversight for high-risk decisions.

---

## Q2. Can Agentforce replace Apex and Flows?

**Answer:**

No. Agentforce complements Apex and Flows but does not replace them. Apex and Flows continue to handle deterministic business logic, validations, and automation, while Agentforce focuses on understanding natural language, reasoning, and orchestrating actions.

---

## Q3. Why is grounding important?

**Answer:**

Grounding ensures that Agentforce uses trusted enterprise data such as Salesforce records, Knowledge articles, or Data Cloud instead of relying solely on the LLM's general knowledge. This improves accuracy and reduces hallucinations.

---

## Q4. Can Agentforce access all Salesforce data automatically?

**Answer:**

No. Administrators and developers must explicitly expose data and capabilities through actions, Flows, Apex, Knowledge, or other supported mechanisms. Agentforce does not automatically gain access to every object or record.

---

## Q5. Does Agentforce respect Salesforce security?

**Answer:**

Yes. Agentforce respects Salesforce security, including object permissions, field-level security, and record sharing. Users can only access data they are authorized to see.

---

# Memory Trick

Remember **"PHASED CAP"**

- **P** → Permissions
- **H** → Hallucinations
- **A** → API dependency
- **S** → Setup required
- **E** → External integrations

- **D** → Data quality

- **C** → Cost
- **A** → Apex/Flow still required
- **P** → Prompt quality

---

# Interview One-Liner

> **Agentforce is a powerful AI platform, but it depends on high-quality grounded data, respects Salesforce security, requires proper configuration of actions and integrations, cannot replace deterministic business logic like Apex or Flows, and still requires human oversight for critical business decisions.**

# Agentforce Use Cases

## What are Agentforce Use Cases?

Agentforce can be used across different Salesforce clouds and business functions to automate tasks, answer questions, perform actions, and improve productivity.

It is useful for:

- Customer Service
- Sales
- Marketing
- Commerce
- HR
- IT Support
- Healthcare
- Finance
- Manufacturing
- Custom Business Applications

---

# High-Level Use Cases

```text
                    Agentforce

        ┌──────────┼──────────┬──────────┐
        ▼          ▼          ▼
   Service      Sales      Marketing

        ├──────────┼──────────┤

        ▼          ▼          ▼
   Commerce       HR      IT Support

        ├──────────┼──────────┤

        ▼          ▼          ▼
 Healthcare    Finance    Manufacturing
```

---

# 1. Customer Service (Service Cloud)

One of the biggest use cases for Agentforce.

### What can it do?

- Create Cases
- Update Cases
- Close Cases
- Summarize Cases
- Search Knowledge Articles
- Escalate Cases
- Recommend Solutions
- Schedule Follow-ups

### Example

Customer:

```
My internet isn't working.
```

Agentforce:

- Creates a Case
- Suggests troubleshooting steps
- Searches Knowledge Articles
- Escalates if necessary

---

# 2. Sales Assistant (Sales Cloud)

Helps sales representatives become more productive.

### Examples

- Summarize Opportunities
- Create Leads
- Update Opportunities
- Recommend Next Best Action
- Draft Follow-up Emails
- Identify High-Value Deals
- Create Tasks

### Example

```
Show opportunities closing this month above ₹10 lakh.
```

Agentforce retrieves the records and summarizes them.

---

# 3. Knowledge Search

Instead of manually searching documentation,

users ask:

```
How do I process a refund?
```

Agentforce searches:

- Salesforce Knowledge
- Documents
- FAQs

and provides the answer.

---

# 4. Case Summarization

Support agents often read long case histories.

Instead, they ask:

```
Summarize Case 00012345.
```

Agentforce summarizes:

- Customer issue
- Current status
- Previous interactions
- Next steps

---

# 5. Email Generation

Generate emails automatically.

### Example

```
Write an email apologizing for a delayed shipment.
```

or

```
Draft a follow-up email after today's meeting.
```

---

# 6. Record Creation

Users can create records using natural language.

### Example

```
Create a lead for Rahul Sharma from ABC Pvt Ltd.
```

↓

Lead Created

---

# 7. Record Updates

Example:

```
Change the opportunity stage to Proposal.
```

↓

Opportunity Updated

---

# 8. Meeting Preparation

Sales representative asks:

```
Summarize everything about ABC Corporation before my meeting.
```

Agentforce retrieves:

- Account Details
- Open Opportunities
- Cases
- Previous Emails
- Activities

and generates a summary.

---

# 9. Customer Self-Service

Customers can ask:

```
Where is my order?
```

```
Reset my password.
```

```
Raise a support request.
```

without waiting for a human agent.

---

# 10. HR Assistant

Employees ask:

```
How many leave days do I have?
```

```
Download my salary slip.
```

```
Apply for leave.
```

Agentforce performs these actions if integrated with HR systems.

---

# 11. IT Help Desk

Employees ask:

```
Reset my VPN password.
```

```
Raise an IT ticket.
```

```
My laptop is slow.
```

Agentforce can:

- Create Tickets
- Search Knowledge
- Suggest Solutions
- Escalate Issues

---

# 12. Commerce Support

Customers ask:

```
Cancel my order.
```

```
Track my shipment.
```

```
Return my product.
```

Agentforce can:

- Check Order Status
- Cancel Orders
- Initiate Refunds
- Create Return Requests

---

# 13. Healthcare

Healthcare staff ask:

```
Show today's appointments.
```

```
Summarize patient history.
```

```
Schedule a follow-up visit.
```

Agentforce assists while respecting security and compliance requirements.

---

# 14. Financial Services

Financial advisors ask:

```
Show customers eligible for a home loan.
```

```
Summarize investment portfolio.
```

```
Schedule a financial review.
```

---

# 15. Manufacturing

Employees ask:

```
Check inventory for Product A.
```

```
Create a maintenance request.
```

```
Show delayed shipments.
```

---

# 16. External System Integration

Agentforce works beyond Salesforce.

Examples:

- GitHub
- Slack
- SAP
- Jira
- SQL Database
- ERP

using:

- REST APIs
- MCP Servers

### Example

```
Show my GitHub pull requests.
```

↓

GitHub MCP Server

↓

GitHub

↓

Response

---

# 17. Data Analysis

Ask:

```
Why are sales down this quarter?
```

or

```
Which region generated the highest revenue?
```

Agentforce analyzes Salesforce data and provides insights.

---

# 18. Multi-Step Automation

Example:

```
Create a case,
assign it to Tier 2,
notify the customer,
schedule a follow-up,
and send an email.
```

Instead of five manual steps,

Agentforce orchestrates the complete workflow.

---

# 19. Executive Dashboard Assistant

Executives ask:

```
Show today's sales performance.
```

```
Which opportunities are at risk?
```

```
Summarize this quarter.
```

---

# 20. Developer Productivity

Developers ask:

```
Explain this Apex class.
```

```
Generate SOQL.
```

```
Write a Flow description.
```

```
Summarize deployment changes.
```

---

# Real-Life Example

Customer:

```
Cancel my order.
```

Agentforce:

↓

Understand intent

↓

Retrieve order

↓

Check cancellation policy

↓

Run Flow

↓

Update Order

↓

Initiate Refund

↓

Notify Customer

↓

Complete

---

# Use Cases by Salesforce Cloud

| Salesforce Cloud | Common Use Cases |
|------------------|------------------|
| Service Cloud | Case management, summarization, Knowledge search, customer support |
| Sales Cloud | Lead creation, opportunity management, email drafting, forecasting |
| Marketing Cloud | Campaign content generation, customer segmentation assistance |
| Commerce Cloud | Order tracking, cancellations, returns, product recommendations |
| Health Cloud | Patient summaries, appointment management, care coordination |
| Financial Services Cloud | Portfolio summaries, customer onboarding, financial insights |
| Experience Cloud | Self-service portals, FAQs, community support |
| Data Cloud | Customer insights, segmentation, analytics |

---

# Industry Use Cases

| Industry | Example |
|----------|----------|
| Banking | Loan eligibility checks |
| Insurance | Claims processing assistance |
| Healthcare | Patient summaries |
| Retail | Order tracking and returns |
| Manufacturing | Inventory and maintenance |
| Education | Student support |
| Telecom | Complaint management |
| Government | Citizen service requests |

---

# Interview Questions

## Q1. What are the common use cases of Agentforce?

**Answer:**

Agentforce is used for customer support, case summarization, sales assistance, lead and opportunity management, knowledge search, email generation, record creation and updates, customer self-service, HR and IT support, commerce operations, healthcare workflows, financial services, manufacturing processes, external system integrations, and multi-step business automation.

---

## Q2. How is Agentforce used in Service Cloud?

**Answer:**

In Service Cloud, Agentforce helps create and update cases, summarize case histories, search Knowledge articles, recommend solutions, automate follow-up actions, and improve customer support efficiency.

---

## Q3. How does Agentforce help Sales teams?

**Answer:**

It assists sales teams by summarizing opportunities, creating leads, updating opportunity stages, drafting emails, recommending next-best actions, preparing meeting summaries, and providing sales insights.

---

## Q4. Can Agentforce work with external systems?

**Answer:**

Yes. Agentforce can integrate with external applications such as GitHub, Slack, SAP, Jira, ERP systems, and SQL databases using REST APIs, Apex callouts, or MCP Servers.

---

## Q5. What is an example of a multi-step Agentforce workflow?

**Answer:**

A user can ask Agentforce to create a support case, assign it to the appropriate queue, notify the customer, schedule a follow-up task, and send a confirmation email. Agentforce coordinates these actions through Flows, Apex, or integrations.

---

# Memory Trick

Remember **"SSM CHIEF MED"**

- **S** → Service
- **S** → Sales
- **M** → Marketing

- **C** → Commerce
- **H** → HR
- **I** → IT Support
- **E** → External Systems
- **F** → Finance

- **M** → Manufacturing
- **E** → Executive Insights
- **D** → Developer Productivity

---

# Interview One-Liner

> **Agentforce can be used across Service Cloud, Sales Cloud, Marketing Cloud, Commerce Cloud, Health Cloud, Financial Services Cloud, and custom applications to automate business processes, answer natural language questions, execute Salesforce actions, integrate with external systems, and improve employee and customer productivity.**

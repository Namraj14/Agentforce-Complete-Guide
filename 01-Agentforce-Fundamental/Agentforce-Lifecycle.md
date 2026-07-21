# Agentforce Lifecycle

The **Agentforce Lifecycle** is the complete journey of how an AI agent receives a user's request, understands it, retrieves the required data, performs actions, and returns a response.

Think of it as the **workflow** that Agentforce follows for every user request.

---

# Agentforce Lifecycle Flow

```text
User
   ↓
User asks a question
   ↓
Agent receives the request
   ↓
Understands the intent
   ↓
Checks Guardrails
   ↓
Retrieves Data (Grounding)
   ↓
Plans what to do
   ↓
Executes Actions
   ↓
Generates Response
   ↓
Returns Response to User
```

---

# Step 1: User Sends a Request

Everything starts when a user asks a question.

### Example

User:

> Cancel my order.

or

> Create a support case.

---

# Step 2: Agent Receives the Request

The Agentforce Agent receives the request.

It first reads and understands what the user is asking.

At this stage, it doesn't perform any action yet.

---

# Step 3: Understand the Intent

The AI identifies the **user's intent**.

Intent means:

> **What does the user actually want?**

### Example

User:

> I forgot my password.

Intent:

```text
Reset Password
```

---

Another example

User:

> My internet is not working.

Intent:

```text
Create Support Request
```

---

# Step 4: Check Guardrails

Before doing anything, Agentforce checks the guardrails.

It verifies:

- Is this request allowed?
- Does the user have permission?
- Is the request safe?
- Does it follow company policies?

---

### Example

User:

> Delete all customer records.

Guardrail:

❌ Not allowed.

Response:

> Sorry, I'm not authorized to perform that action.

---

# Step 5: Retrieve Data (Grounding)

Now the agent collects the required information.

It may retrieve data from:

- Salesforce Records
- Knowledge Articles
- Data Cloud
- External APIs

This process is called **Grounding**.

---

### Example

User:

> What is the status of my case?

Agent retrieves:

```text
Case Number : 00012345

Status : In Progress

Owner : Support Team
```

Now it has enough information to answer correctly.

---

# Step 6: Plan the Next Steps

The agent decides:

> What should I do next?

Unlike a traditional chatbot, Agentforce can plan multiple steps.

### Example

User:

> Cancel my order.

The plan might be:

```text
Find Order

↓

Check Order Status

↓

Verify Cancellation Eligibility

↓

Cancel Order

↓

Send Confirmation Email
```

This planning is what makes Agentforce an AI agent instead of a simple chatbot.

---

# Step 7: Execute Actions

Now the agent performs the required work.

Possible actions include:

- Run a Flow
- Execute Apex
- Create Records
- Update Records
- Delete Records (if allowed)
- Call External APIs
- Send Emails

---

### Example

User:

> Update my phone number.

Agent:

```text
Find Customer

↓

Update Account Record

↓

Save Changes
```

The task is completed automatically.

---

# Step 8: Generate the Response

After completing the work, Agentforce prepares a response.

Example

> Your phone number has been updated successfully.

---

Another example

> Your support case has been created successfully.

Case Number: 00012567

---

# Step 9: Return the Response

Finally, the response is sent back to the user.

Conversation complete.

---

# Complete Example

### User

> Cancel my order.

---

### Step 1

Receive request.

↓

### Step 2

Understand intent.

Intent:

```text
Cancel Order
```

↓

### Step 3

Check guardrails.

User has permission.

↓

### Step 4

Retrieve Order Details.

↓

### Step 5

Check if order is eligible for cancellation.

↓

### Step 6

Run Flow or Apex Action.

↓

### Step 7

Cancel Order.

↓

### Step 8

Generate Response.

↓

### Step 9

Return Response.

> Your order has been cancelled successfully.

---

# Lifecycle Diagram

```text
          User
            │
            ▼
   Receive Request
            │
            ▼
   Understand Intent
            │
            ▼
   Check Guardrails
            │
            ▼
 Retrieve Salesforce Data
      (Grounding)
            │
            ▼
      Plan the Task
            │
            ▼
     Execute Actions
            │
            ▼
    Generate Response
            │
            ▼
 Return Response to User
```

---

# Real Salesforce Example

### User

> Create a support case because my internet is not working.

Agentforce:

```
Receives Request

↓

Understands Intent

↓

Checks User Permission

↓

Looks for Existing Cases

↓

Creates New Case

↓

Assigns Support Queue

↓

Sends Confirmation Email

↓

Returns Case Number
```

Final Response:

> Your support case has been created successfully.
>
> Case Number: 00012567

---

# Lifecycle vs Traditional Chatbot

| Traditional Chatbot | Agentforce |
|---------------------|------------|
| Receives question | Receives request |
| Matches keywords | Understands intent |
| Gives fixed reply | Retrieves Salesforce data |
| No planning | Plans multiple steps |
| No actions | Executes actions |
| Ends conversation | Completes the business task |

---

# Easy Way to Remember

| Step | Question |
|------|----------|
| Receive Request | What did the user ask? |
| Understand Intent | What does the user want? |
| Guardrails | Is it allowed? |
| Grounding | What data do I need? |
| Planning | What should I do? |
| Actions | Perform the work |
| Response | Tell the user the result |

---

# Interview Questions

## Q1. What is the Agentforce Lifecycle?

**Answer:**

The Agentforce Lifecycle is the sequence of steps an AI agent follows to process a user's request, retrieve data, perform actions, and return a response.

---

## Q2. What happens after understanding the user's intent?

**Answer:**

The agent checks guardrails to ensure the request is allowed and the user has the necessary permissions.

---

## Q3. What is Grounding in the lifecycle?

**Answer:**

Grounding is the process of retrieving relevant Salesforce or external data so the AI can provide accurate and context-aware responses.

---

## Q4. Why is the planning step important?

**Answer:**

Planning allows Agentforce to determine the sequence of actions required to complete a task, making it capable of handling multi-step business processes.

---

## Q5. What types of actions can Agentforce execute?

**Answer:**

Agentforce can run Flows, execute Apex, create or update Salesforce records, call external APIs, send emails, and perform other configured business actions.

---

# Final Summary

| Step | Description |
|------|-------------|
| 1. Receive Request | User submits a request. |
| 2. Understand Intent | Identify what the user wants. |
| 3. Check Guardrails | Verify permissions and policies. |
| 4. Grounding | Retrieve relevant Salesforce data. |
| 5. Planning | Decide the sequence of actions. |
| 6. Execute Actions | Perform the required work. |
| 7. Generate Response | Prepare the final answer. |
| 8. Return Response | Send the result to the user. |

---

# One-Line Memory Trick

- **Receive** → What did the user ask?
- **Intent** → What do they want?
- **Guardrails** → Is it allowed?
- **Grounding** → Get the right data.
- **Planning** → Decide what to do.
- **Actions** → Do the work.
- **Response** → Tell the user the result.

## Interview One-Liner

> **The Agentforce Lifecycle is the end-to-end process in which an AI agent receives a user's request, understands the intent, validates permissions through guardrails, retrieves grounded Salesforce data, plans the required steps, executes business actions, and returns an accurate response.**

# Agent Lifecycle

## Step 1

User sends request.

## Step 2

Agent analyzes intent.

## Step 3

Topic identified.

## Step 4

Instructions evaluated.

## Step 5

Grounding performed.

## Step 6

Actions executed.

## Step 7

Response generated.

## Step 8

Response returned.

## Example

User:
"Reset my password."

Lifecycle:

Request
→ Intent Detection
→ Topic Selection
→ Execute Password Reset Flow
→ Generate Confirmation
→ Return Response

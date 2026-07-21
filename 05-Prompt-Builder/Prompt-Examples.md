# Prompt Builder Examples

Below are some real Salesforce examples that will help you understand how Prompt Builder works.

---

# Example 1: Case Summary

## Salesforce Record

```
Case Number : 00012345

Subject : Internet Issue

Description :
Customer is unable to connect to the internet since yesterday.
Customer is very unhappy and requested urgent support.

Priority : High

Status : Open
```

---

## Prompt

```
Summarize this case in 3 lines for the support manager.
```

---

## AI Output

```
• Customer reported an internet connectivity issue since yesterday.
• The issue is marked as High Priority and requires urgent attention.
• The case is currently Open.
```

---

# Example 2: Email Generation

## Salesforce Record

```
Customer Name : John

Product : MacBook Pro

Discount : 15%

Offer Ends : Friday
```

---

## Prompt

```
Write a professional sales email.
```

---

## AI Output

```
Hello John,

We are excited to offer you a 15% discount on the MacBook Pro.

This offer is valid until Friday.

Please let us know if you would like to place an order.

Regards,
Sales Team
```

---

# Example 3: Service Reply

## Customer Message

```
My refund has not been received.
```

---

## Prompt

```
Generate a polite customer support response.
```

---

## AI Output

```
Dear Customer,

We apologize for the delay.

Your refund request is currently being processed and should be completed shortly.

Thank you for your patience.
```

---

# Example 4: Lead Description

## Salesforce Record

```
Lead Name : Alex

Company : ABC Pvt Ltd

Interested Product : Salesforce CRM
```

---

## Prompt

```
Generate a professional lead description.
```

---

## AI Output

```
Alex from ABC Pvt Ltd has shown interest in Salesforce CRM and is a potential customer for future business discussions.
```

---

# Example 5: Opportunity Summary

## Opportunity Record

```
Customer : XYZ Ltd

Amount : $50,000

Stage : Negotiation

Close Date : 25 July
```

---

## Prompt

```
Summarize this opportunity for the sales manager.
```

---

## AI Output

```
XYZ Ltd opportunity is currently in the Negotiation stage with an expected value of $50,000. The anticipated close date is 25 July.
```

---

# Example 6: Meeting Notes

## Input

```
Meeting with ABC Ltd

Topics:
- Pricing
- Implementation
- Timeline
- Training
```

---

## Prompt

```
Generate meeting minutes.
```

---

## AI Output

```
Meeting Summary

• Pricing was discussed.
• Implementation will begin next month.
• Training sessions will be scheduled.
• Next meeting is planned for Friday.
```

---

# Example 7: Knowledge Article

## Customer Question

```
How do I reset my password?
```

---

## Prompt

```
Answer using the Knowledge Article.
```

---

## AI Output

```
To reset your password:

1. Click Forgot Password.
2. Enter your registered email.
3. Open the email.
4. Click the reset link.
```

---

# Example 8: Translation

## Input

```
Thank you for contacting Salesforce Support.
```

---

## Prompt

```
Translate into French.
```

---

## AI Output

```
Merci d'avoir contacté le support Salesforce.
```

---

# Example 9: Marketing Content

## Input

```
Product

Wireless Headphones

Noise Cancellation

20-hour Battery
```

---

## Prompt

```
Generate a product description.
```

---

## AI Output

```
Experience crystal-clear sound with our wireless headphones featuring advanced noise cancellation and up to 20 hours of battery life.
```

---

# Example 10: Social Media Post

## Input

```
Product Launch

AI CRM

Coming Next Week
```

---

## Prompt

```
Generate a LinkedIn post.
```

---

## AI Output

```
We're excited to announce the launch of our new AI-powered CRM solution next week. Stay tuned for more updates!
```

---

# Real Salesforce Developer Example

Suppose a Case is created.

```
Case

↓

Prompt Builder

↓

Prompt:
Summarize the issue professionally.

↓

AI

↓

Case Summary Field Updated
```

No Apex required.

---

# Prompt Template Structure

Every Prompt Builder template has three parts.

## 1. Instructions

```
Summarize the case.
```

---

## 2. Input

```
Case Description

Priority

Status
```

---

## 3. Output

```
Return only three bullet points.
```

---

# Real Flow Example

Imagine a Record-Triggered Flow.

```
New Case Created

↓

Flow Starts

↓

Prompt Builder

↓

Generate Summary

↓

Update Summary Field

↓

Case Saved
```

Everything happens automatically.

---

# Agentforce + Prompt Builder Example

Customer:

```
Cancel my order.
```

Agentforce:

```
Find Order

↓

Run Flow

↓

Cancel Order

↓

Prompt Builder

↓

Generate Confirmation Message

↓

Customer Receives Response
```

Prompt Builder generates the message, while Agentforce performs the business action.

---

# Interview Tip

### Prompt Builder generates **content**.

Examples:
- Emails
- Summaries
- Replies
- Product descriptions
- Meeting notes
- Field values

### Agentforce performs **actions**.

Examples:
- Create Case
- Update Record
- Run Flow
- Execute Apex
- Call APIs

**Easy way to remember:**

> **Prompt Builder = "Write something."**  
> **Agentforce = "Do something."**

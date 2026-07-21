# Prompt Builder Best Practices

A prompt is like giving instructions to a new employee.

- ❌ Bad instructions → Poor results
- ✅ Clear instructions → Better AI responses

The quality of the AI's response depends on how well you write the prompt.

---

# 1. Be Clear and Specific

Always tell the AI exactly what you want.

## ❌ Bad Prompt

```
Write something about this case.
```

The AI doesn't know what "something" means.

---

## ✅ Good Prompt

```
Summarize this customer case in three bullet points for a support manager.
```

Now the AI knows:
- What to do
- How to format the response
- Who the audience is

---

# 2. Give Context

Always explain the situation.

## ❌ Bad Prompt

```
Reply to this customer.
```

The AI doesn't know:
- Is the customer angry?
- Is this a sales email?
- Is it a refund request?

---

## ✅ Good Prompt

```
The customer has requested a refund due to a damaged product.
Write a polite and professional response.
```

---

# 3. Define the Role

Tell the AI who it should act as.

## ❌ Bad Prompt

```
Answer this customer.
```

---

## ✅ Good Prompt

```
You are a Salesforce Customer Support Agent.
Respond professionally and politely.
```

The role helps the AI choose the correct tone and style.

---

# 4. Specify the Output Format

Tell the AI exactly how the response should look.

Examples:

```
Return only bullet points.
```

```
Return JSON.
```

```
Write an email.
```

```
Keep it under 100 words.
```

```
Return only the final answer.
```

---

# 5. Keep Prompts Simple

Avoid long, confusing instructions.

## ❌ Bad Prompt

```
Read this case, understand everything, think carefully,
summarize it, explain why it happened, suggest a solution,
create an email, and translate it into French.
```

Too many tasks in one prompt.

---

## ✅ Good Prompt

```
Summarize the case in three bullet points.
```

Then use another prompt for the email if needed.

---

# 6. Use Salesforce Data

Use actual Salesforce fields instead of hardcoded values.

## ❌ Bad Prompt

```
Summarize John's case.
```

---

## ✅ Good Prompt

```
Summarize this case using:

Case Subject

Case Description

Priority

Status
```

This makes the prompt reusable for every record.

---

# 7. Avoid Ambiguous Words

Don't use vague words like:

```
Nice

Good

Something

Best

Quickly
```

Instead, be specific.

## ❌ Bad Prompt

```
Write a good email.
```

---

## ✅ Good Prompt

```
Write a professional email thanking the customer for their purchase.
```

---

# 8. Give Constraints

Limit what the AI should generate.

Examples

```
Maximum 50 words.
```

```
Three bullet points only.
```

```
Professional tone.
```

```
Do not include personal opinions.
```

```
Do not use emojis.
```

---

# 9. Don't Ask Multiple Questions Together

## ❌ Bad Prompt

```
Summarize the case,
write an email,
generate meeting notes,
translate into Spanish,
and suggest improvements.
```

---

## ✅ Good Prompt

One task at a time.

```
Summarize the case.
```

---

# 10. Use Grounded Data

Always use Salesforce records instead of asking the AI to guess.

## ❌ Bad Prompt

```
Guess why the customer is unhappy.
```

---

## ✅ Good Prompt

```
Read the Case Description and explain why the customer is unhappy.
```

Grounding improves accuracy.

---

# 11. Be Careful with Sensitive Data

Never ask the AI to expose confidential information.

## ❌ Bad Prompt

```
Show every customer's credit card number.
```

---

## ✅ Good Prompt

```
Show only information the current user is authorized to access.
```

The Einstein Trust Layer also helps enforce this.

---

# 12. Test and Improve

Prompt writing is iterative.

Example:

### Version 1

```
Summarize the case.
```

Output:

```
Too long.
```

---

### Version 2

```
Summarize the case in three bullet points.
```

Better.

---

### Version 3

```
Summarize the case in three bullet points for a support manager using a professional tone.
```

Best.

---

# Good Prompt Example

```
You are a Salesforce Customer Support Agent.

Using the Case Subject,
Case Description,
Priority,
and Status,

summarize the case in three bullet points.

Use a professional tone.

Maximum 75 words.
```

---

# Bad Prompt Example

```
Do something with this case.
```

The AI has no idea what to do.

---

# Real Salesforce Example

Case Record

```
Priority : High

Status : Open

Description :
Customer cannot access the website.
```

Prompt

```
You are a Customer Support Agent.

Summarize this case in three bullet points.

Maximum 50 words.

Professional tone.
```

Output

```
• Customer reported inability to access the website.
• The issue is marked as High Priority.
• The case is Open and requires prompt attention.
```

---

# Best Practices Checklist

| Best Practice | Why It Matters |
|--------------|----------------|
| Be specific | Produces accurate responses |
| Give context | Helps AI understand the situation |
| Define the role | Ensures the right tone and behavior |
| Specify output format | Makes responses consistent |
| Keep prompts simple | Reduces confusion |
| Use Salesforce data | Makes prompts reusable |
| Avoid ambiguity | Prevents unclear answers |
| Add constraints | Controls length and style |
| One task per prompt | Improves focus |
| Use grounded data | Reduces hallucinations |
| Protect sensitive data | Maintains security |
| Test and refine | Improves prompt quality over time |

---

# Easy Formula

A strong prompt usually follows this pattern:

```text
Role
      +
Task
      +
Salesforce Data
      +
Output Format
      +
Constraints
```

### Example

```text
You are a Customer Support Agent.

Summarize the case using
Case Subject,
Description,
Priority,
and Status.

Return exactly three bullet points.

Maximum 75 words.

Use a professional tone.
```

---

# Interview Questions

## Q1. Why should prompts be specific?

**Answer:**
Specific prompts reduce ambiguity and help the AI generate accurate, relevant responses.

---

## Q2. Why is context important?

**Answer:**
Context helps the AI understand the business scenario and produce more appropriate responses.

---

## Q3. Why should prompts include output constraints?

**Answer:**
Constraints ensure the response meets business requirements for length, format, and tone.

---

## Q4. Why should prompts use Salesforce data?

**Answer:**
Using Salesforce data makes prompts dynamic, reusable, and grounded in real business information.

---

## Q5. What is the ideal prompt structure?

**Answer:**

```
Role
↓

Task
↓

Relevant Salesforce Data
↓

Output Format
↓

Constraints
```

---

# One-Line Memory Trick

- **Role** → Who am I?
- **Task** → What should I do?
- **Data** → What information should I use?
- **Format** → How should I answer?
- **Constraints** → What rules should I follow?

## Interview One-Liner

> **A good Prompt Builder prompt is clear, specific, grounded in Salesforce data, defines the AI's role, specifies the desired output format, includes appropriate constraints, and is continuously tested and refined for better results.**

# Temperature in AI

## Overview

Temperature is a parameter used during response generation in Large Language Models (LLMs). It controls the randomness and creativity of the generated output.

## Definition

Temperature is a hyperparameter that influences how confidently an AI model selects the next token during text generation.

## Why Is Temperature Important?

Temperature determines whether the model produces:

- Predictable responses
- Balanced responses
- Creative responses

It helps tune the model for different use cases such as coding, customer support, content creation, and brainstorming.

## How Temperature Works

When predicting the next token, the model assigns probabilities to possible outputs.

Example:

Input:

```text
I love _____
```

Possible Predictions:

| Token | Probability |
|---------|------------|
| Salesforce | 60% |
| Coding | 25% |
| Pizza | 10% |
| Cricket | 5% |

Lower temperatures make the model prefer higher probability tokens, while higher temperatures allow selection of lower probability tokens.

## Temperature Scale

| Temperature | Behavior |
|------------|----------|
| 0.0 | Deterministic |
| 0.2 | Focused and factual |
| 0.5 | Balanced |
| 0.7 | Creative |
| 1.0 | Highly creative |

## Real-World Examples

### Coding Assistant

Recommended Temperature:

```text
0.1 - 0.3
```

Reason:

- Consistent output
- Accurate code generation

### Creative Writing

Recommended Temperature:

```text
0.7 - 1.0
```

Reason:

- More diverse ideas
- Better storytelling

## Temperature in Agentforce

Temperature affects how an Agentforce agent generates responses after retrieving data and executing actions.

### Low Temperature

Produces:

```text
Case is related to billing.
Status: Open.
```

### High Temperature

Produces:

```text
The customer is experiencing a billing-related issue and currently has an open support case.
```

## Interview Questions and Answers

### 1. What is Temperature in AI?

#### Answer

Temperature is a parameter that controls the randomness and creativity of AI-generated responses.

### 2. Does Temperature Affect Training?

#### Answer

No. Temperature only affects inference (response generation) and has no impact on model training.

### 3. Which Temperature Is Best for Coding?

#### Answer

A lower temperature (0.1–0.3) is preferred because it generates more deterministic and accurate outputs.

### 4. Which Temperature Is Best for Creative Writing?

#### Answer

A higher temperature (0.7–1.0) is preferred because it allows more diverse and creative responses.

### 5. What Happens When Temperature Is 0?

#### Answer

The model becomes highly deterministic and generally selects the most probable next token.

## Best Practices

- Use low temperature for coding and factual tasks.
- Use medium temperature for conversational AI.
- Use high temperature for creative content generation.
- Avoid extremely high temperatures in production systems requiring consistency.

## Key Takeaways

- Temperature controls randomness.
- Lower temperature increases consistency.
- Higher temperature increases creativity.
- Temperature is used during inference.
- It is an important tuning parameter for LLM applications.

## One-Line Interview Answer

> Temperature is a parameter that controls the randomness and creativity of AI-generated responses during inference.

# Agentforce Architecture

## High Level Flow

User
 ↓
Agent
 ↓
Topic Selection
 ↓
Instruction Evaluation
 ↓
Grounding
 ↓
Action Selection
 ↓
Data Retrieval
 ↓
LLM Response
 ↓
User

## Components

### User

Initiates request.

### Agent

Central orchestrator.

### Topics

Define capabilities.

### Instructions

Guide agent behavior.

### Grounding

Provides trusted data.

### Actions

Perform tasks.

### Trust Layer

Ensures security and compliance.

### LLM

Generates responses.

## Example

Customer:

"Show my open cases."

Agent:

1. Understand request.
2. Select topic.
3. Retrieve cases.
4. Format response.
5. Return result.

# Databricks Certified Generative AI Engineer Associate
# Application Development (30%) - Complete Study Notes

## Index

1. RAG Pipeline
2. LangChain Basics
3. Single Agents
4. Retrieval Agents
5. Multi-Agent Systems
6. Tool Calling
7. Memory
8. Knowledge Assistants
9. Guardrails
10. End-to-End Architectures
11. Final Revision Notes

---

# 1. RAG Pipeline

## Definition
RAG (Retrieval Augmented Generation) combines retrieval of relevant information with LLM response generation.

## Runtime Flow

```text
User Question
      ↓
Query Embedding
      ↓
Vector Search
      ↓
Top-K Chunks
      ↓
Prompt Construction
      ↓
LLM
      ↓
Answer
```

## Indexing Phase

```text
Documents
 ↓
Ingestion
 ↓
Cleaning
 ↓
Chunking
 ↓
Embeddings
 ↓
Vector Database
```

## Retrieval Phase

```text
Question
 ↓
Query Embedding
 ↓
Vector Search
 ↓
Retrieved Chunks
 ↓
LLM
 ↓
Answer
```

## Key Components
- Embedding Model
- Vector Database
- Vector Search
- Prompt Construction
- LLM

## Benefits
- Uses latest information
- Supports internal documents
- Reduces hallucinations
- No model retraining required

## Exam Notes
- Retrieval ≠ Generation
- Vector Search retrieves context
- LLM generates answers
- Prompt Construction combines question and context

---

# 2. LangChain Basics

## Definition
LangChain is a framework for building LLM-powered applications.

## Major Components

### Prompt Templates
Reusable prompts with variables.

Example:

```text
Context: {context}
Question: {question}
```

### LLM
Generates responses.

### Retriever
Finds relevant chunks.

### Chains
Fixed sequence of steps.

```text
Input
 ↓
Prompt
 ↓
LLM
 ↓
Output
```

### Memory
Stores conversation history.

### Tools
Access external systems.

### Agents
Reason and choose tools.

## Chain vs Agent

### Chain
- Fixed workflow
- Predictable path
- No tool selection logic

### Agent
- Dynamic workflow
- Reasoning
- Tool selection

## Exam Notes
- Prompt Template formats prompts.
- Retriever retrieves information.
- Memory stores chat history.
- Agent = Dynamic.
- Chain = Fixed.

---

# 3. Single Agents

## Definition
A Single Agent is one intelligent agent responsible for an entire workflow.

## Architecture

```text
User
 ↓
Agent
 ↓
Tools
 ↓
Response
```

## Capabilities
- Reasoning
- Planning
- Tool Selection
- Action Execution
- Response Generation

## Agent Loop

```text
Reason
 ↓
Act
 ↓
Observe
 ↓
Reason Again
```

## Common Tools
- Retriever
- SQL Tool
- API Tool
- Search Tool
- Calculator Tool

## Advantages
- Simpler
- Lower cost
- Lower latency
- Easier maintenance

## Limitations
- Less specialization
- Harder scaling
- Limited for very complex workflows

## Exam Notes
- Agent = LLM + Reasoning + Tools.
- Single Agent controls entire workflow.
- Agents can use RAG.

---

# 4. Retrieval Agents

## Definition
A Retrieval Agent is an Agent that uses retrieval as a tool.

## Architecture

```text
User
 ↓
Retrieval Agent
 ↓
Reasoning
 ↓
Retriever Tool
 ↓
Relevant Chunks
 ↓
Answer
```

## Key Concept
Retriever is treated as a Tool.

## Traditional RAG vs Retrieval Agent

### Traditional RAG
- Fixed workflow
- Always retrieves

### Retrieval Agent
- Uses reasoning
- Decides whether retrieval is needed

## Benefits
- Flexible
- Supports multiple question types
- Can combine retrieval with other tools

## Exam Notes
- Retrieval Agent = Agent + Retriever.
- Agent decides when retrieval is needed.

---

# 5. Multi-Agent Systems

## Definition
Multiple specialized agents collaborate to solve a task.

## Architecture

```text
User
 ↓
Coordinator Agent
 ├── Retrieval Agent
 ├── SQL Agent
 ├── Analysis Agent
 └── Report Agent
 ↓
Final Response
```

## Coordinator Agent
Responsibilities:
- Understand request
- Delegate work
- Combine outputs
- Return final answer

## Specialist Agents

### Retrieval Agent
Knowledge retrieval.

### SQL Agent
Database querying.

### Analysis Agent
Calculations and insights.

### Report Agent
Summarization and reporting.

## Advantages
- High specialization
- Scalability
- Better task separation

## Limitations
- Higher latency
- Higher cost
- More complexity

## Single-Agent vs Multi-Agent

Single-Agent:
- Faster
- Simpler

Multi-Agent:
- More specialized
- Better for complex workflows

## Exam Notes
- Coordinator Agent orchestrates work.
- Multi-Agent is part of Agentic AI.

---

# 6. Tool Calling

## Definition
Tool Calling allows agents to interact with external systems.

## Examples
- APIs
- Databases
- Calculators
- Search Engines
- Email Systems
- Retrievers

## Flow

```text
User
 ↓
Agent
 ↓
Reasoning
 ↓
Tool Selection
 ↓
Tool Execution
 ↓
Result
 ↓
Response
```

## Example

```text
Question:
What were sales last month?

Agent
 ↓
SQL Tool
 ↓
Sales Data
 ↓
Answer
```

## Benefits
- Real-time data
- Automation
- Better accuracy
- External actions

## Exam Notes
- Retriever can be a Tool.
- Agents choose tools dynamically.
- Tool Calling enables actions.

---

# 7. Memory

## Definition
Memory stores information from previous interactions.

## Purpose
- Context awareness
- Multi-turn conversations
- Personalization

## Example

```text
User: My name is Vinodh.

User: What is my name?
```

Memory provides the answer.

## Types

### Short-Term Memory
- Current session
- Temporary

### Long-Term Memory
- Cross-session
- Persistent

## Memory vs RAG

### Memory
Stores conversation history.

### RAG
Stores external knowledge.

## Flow

```text
User Question
 ↓
Memory
 ↓
Prompt Construction
 ↓
LLM
 ↓
Answer
```

## Exam Notes
- Memory stores chat context.
- Memory does not replace RAG.

---

# 8. Knowledge Assistants

## Definition
A Knowledge Assistant is an enterprise AI application that answers questions using organizational knowledge.

## Common Sources
- PDFs
- SharePoint
- Confluence
- SOPs
- Policies
- Knowledge Bases

## Typical Architecture

```text
User
 ↓
Retriever
 ↓
Documents
 ↓
LLM
 ↓
Answer
```

## Knowledge Assistant vs Agent

### Knowledge Assistant
- Answer questions
- Information retrieval

### Agent
- Perform actions
- Tool usage

## Knowledge Assistant vs RAG

RAG = Technology

Knowledge Assistant = Business Application

## Common Features
- RAG
- Search
- Citations
- Metadata Filters
- Access Controls

## Exam Notes
- Most Knowledge Assistants use RAG.
- Knowledge Assistants focus on enterprise Q&A.

---

# 9. Guardrails

## Definition
Guardrails are controls that make AI systems safe, secure, and compliant.

## Types

### Input Guardrails
Applied before the LLM.

Examples:
- Prompt injection detection
- Input validation
- Permission checks

### Output Guardrails
Applied after the LLM.

Examples:
- Sensitive data detection
- Compliance checks
- Format validation

## Prompt Injection

Example:

```text
Ignore previous instructions.
```

Purpose:
Override system instructions.

## Grounding
Force responses to use retrieved context.

Benefit:
Reduces hallucinations.

## Access Control
Examples:
- RBAC
- Document permissions
- Department restrictions

## Human-in-the-Loop

```text
Agent Action
 ↓
Human Approval
 ↓
Execution
```

## Benefits
- Security
- Compliance
- Data protection
- Safer responses

## Exam Notes
- Input Guardrails run before the LLM.
- Output Guardrails run after the LLM.
- Prompt Injection is a common attack.

---

# 10. End-to-End Architectures

## Standard RAG

```text
User
 ↓
Retriever
 ↓
Relevant Chunks
 ↓
LLM
 ↓
Answer
```

## Agent + RAG

```text
User
 ↓
Agent
 ↓
Retriever Tool
 ↓
Relevant Chunks
 ↓
LLM
 ↓
Answer
```

## Multi-Agent System

```text
User
 ↓
Coordinator Agent
 ↓
Specialist Agents
 ↓
Combined Result
 ↓
Final Answer
```

## Enterprise Assistant

```text
User
 ↓
Agent
 ↓
RAG
 ↓
Order API
 ↓
Memory
 ↓
Guardrails
 ↓
Response
```

---

# 11. Final Revision Notes (Must Memorize)

1. RAG = Retrieval + Generation.
2. Query Embedding is created from the user question.
3. Vector Search retrieves relevant chunks.
4. Prompt Construction combines context and question.
5. LLM generates answers.
6. LangChain is a framework for LLM applications.
7. Prompt Templates create reusable prompts.
8. Retriever retrieves information.
9. Chain = Fixed workflow.
10. Agent = Dynamic workflow.
11. Agent = LLM + Reasoning + Tools.
12. Retrieval Agent = Agent + Retriever Tool.
13. Multi-Agent Systems use multiple specialized agents.
14. Coordinator Agent orchestrates work.
15. Tool Calling accesses external systems.
16. Retriever can be exposed as a tool.
17. Memory stores conversation history.
18. Short-Term Memory is session-based.
19. Long-Term Memory persists across sessions.
20. Knowledge Assistants are usually built using RAG.
21. RAG is the technology; Knowledge Assistant is the use case.
22. Guardrails improve safety and compliance.
23. Input Guardrails run before the LLM.
24. Output Guardrails run after the LLM.
25. Grounding reduces hallucinations.
26. Prompt Injection attempts to override instructions.
27. Single-Agent = Simpler and faster.
28. Multi-Agent = More specialized but higher latency.
29. Tool Calling enables actions and real-time data access.
30. Enterprise GenAI commonly combines RAG + Agents + Memory + Guardrails.

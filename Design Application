# Databricks Generative AI Engineer Associate
# Design Applications (14%) - Complete Study Notes

## Index

1. LLM Fundamentals
2. Prompt Engineering
3. RAG vs Agents
4. Single-Agent vs Multi-Agent Systems
5. Use Case Selection
6. Latency vs Accuracy Tradeoffs

---

# 1. LLM Fundamentals

## What is an LLM?
LLM (Large Language Model) is an AI model trained on massive amounts of text data that can:
- Answer questions
- Generate content
- Summarize documents
- Translate languages
- Write code
- Perform reasoning

### Examples
- GPT
- Claude
- Llama
- Mistral
- DBRX

## Traditional Programming vs LLM

### Traditional Program
Input → Rules → Output

The logic is explicitly written by developers.

### LLM
Input → Model Reasoning → Output

The model learns patterns from data instead of fixed rules.

## Foundation Models
A pre-trained general-purpose model is called a Foundation Model.

Examples:
- GPT
- Claude
- Llama
- Mistral
- DBRX

Flow:
Foundation Model → Fine-Tuning → Domain-Specific Model

## Pretraining
Training on massive datasets such as:
- Books
- Websites
- Wikipedia
- Research papers

Produces a general-purpose model.

## Fine-Tuning
Additional training on domain-specific data.

Example:
Foundation Model → Medical Data → Medical Assistant

Used when behavior/style must change.

## RAG (Retrieval Augmented Generation)
No retraining required.

Flow:
User Question → Retrieve Documents → Add Context → LLM → Answer

Benefits:
- Uses latest knowledge
- Cheaper than fine-tuning
- Easy to update

## Fine-Tuning vs RAG

### Fine-Tuning
- Retrains model
- Expensive
- Slower updates
- Knowledge stored inside model
- Best for behavior/style changes

### RAG
- No retraining
- Cost-effective
- Easy updates
- Knowledge stored externally
- Best for knowledge retrieval

## Context Window
Maximum amount of tokens a model can process at once.

If documents exceed context window:
- Use chunking
- Use retrieval

## Temperature
Controls randomness.

### Low Temperature (0-0.3)
- More deterministic
- Better for enterprise applications
- Better for finance and compliance

### High Temperature (0.7-1.0)
- More creative
- Better for storytelling and marketing

## Hallucination
When a model generates incorrect information confidently.

Ways to reduce:
- RAG
- Grounding
- Better prompts
- Evaluation
- Verification

## Tokens
LLMs process text as tokens, not words.

Important:
More tokens → More cost → More latency

## Inference
Using a trained model to generate responses.

Training = Teaching the model
Inference = Using the model

### Key Exam Notes
- LLM = Large Language Model
- Foundation Model = Pretrained model
- Fine-Tuning = Retraining
- RAG = Retrieval-based knowledge augmentation
- Temperature controls randomness
- Context Window limits input size
- Hallucination = False generated information
- Tokens drive latency and cost
- Inference = Model generating output

---

# 2. Prompt Engineering

## Definition
Prompt Engineering is the practice of designing prompts that produce better outputs from LLMs.

## Why Prompt Engineering Matters
Better prompts lead to:
- Better accuracy
- Better structure
- Better reliability

## Components of a Good Prompt

### Task
What should the model do?

### Context
Additional information.

### Instructions
How should the response be generated?

### Output Format
Expected response structure.

## System Prompt vs User Prompt

### System Prompt
Defines behavior and rules.

Example:
"You are a professional assistant."

### User Prompt
Actual user request.

Exam Tip:
System Prompt usually has higher priority.

## Zero-Shot Prompting
No examples provided.

## One-Shot Prompting
One example provided.

## Few-Shot Prompting
Multiple examples provided.

Exam Tip:
Few-Shot = Multiple examples.

## Role Prompting
Assign a role.

Examples:
- Act as a teacher
- Act as a financial advisor
- Act as a data analyst

## Chain of Thought (CoT)
Ask model to reason step-by-step.

Benefits:
- Better reasoning
- Better problem solving

## Structured Output Prompting
Request outputs in formats such as:
- JSON
- XML
- Lists

Common in GenAI applications.

## Prompt Templates
Reusable prompt structures with placeholders.

Benefits:
- Consistency
- Scalability
- Easier maintenance

## Prompt Injection
A user attempts to override system instructions.

Example:
"Ignore previous instructions"

## Mitigation Techniques
- Strong system prompts
- Input validation
- Guardrails
- Output filtering
- Access controls

## Grounding
Instructing the model to answer using trusted context.

Benefits:
- Reduces hallucinations
- Improves reliability

## Prompt Length Impact
Longer prompts cause:
- More tokens
- Higher cost
- Higher latency

### Key Exam Notes
- Prompt = Instruction to LLM
- Zero-Shot = No examples
- One-Shot = One example
- Few-Shot = Multiple examples
- Role Prompting assigns expertise
- CoT improves reasoning
- Grounding reduces hallucinations
- Prompt Injection attempts to override instructions
- More tokens increase latency and cost

---

# 3. RAG vs Agents

## What is RAG?
Retrieval Augmented Generation.

Flow:
User Question → Retriever → Documents → LLM → Answer

Purpose:
Retrieve knowledge.

Use Cases:
- Document Q&A
- Knowledge assistants
- Policy lookup
- Internal search systems

## Why RAG?
Solves:
- Outdated knowledge
- Private company data access
- Context limitations
- Hallucinations

## What is an Agent?
Agent = LLM + Reasoning + Tools

Capabilities:
- Planning
- Decision making
- Tool usage
- Multi-step execution

## Agent Tools Examples
- Search
- Database access
- Calculator
- APIs
- Email

## Agent Workflow
User → Reasoning → Tool Selection → Tool Execution → Response

## RAG vs Agent

### RAG
- Focused on information retrieval
- Retrieves knowledge
- Answers questions

### Agent
- Focused on actions
- Uses tools
- Can perform workflows

## Can Agents Use RAG?
Yes.

Agent + RAG is common.

The retriever becomes one of the agent's tools.

## When to Use RAG
- Latest knowledge required
- Private documents
- Knowledge assistants
- Document search

## When to Use Agents
- Actions required
- Tool usage required
- Multi-step workflows
- Decision making required

## Limitations

### RAG
Cannot:
- Send emails
- Call APIs by itself
- Execute business actions

### Agents
- Higher cost
- Higher latency
- More complexity

### Key Exam Notes
- RAG = Retrieval
- Agent = Action + Reasoning + Tools
- Agent can use RAG
- RAG reduces hallucinations
- Knowledge systems often use RAG
- Workflow automation often uses Agents

---

# 4. Single-Agent vs Multi-Agent Systems

## Single-Agent System
One agent handles everything.

Flow:
User → Agent → Tools → Response

### Advantages
- Simpler
- Lower cost
- Lower latency
- Easier debugging

### Disadvantages
- Less specialization
- Harder for complex workflows
- Limited scalability

## Multi-Agent System
Multiple specialized agents collaborate.

Flow:
User → Coordinator → Specialist Agents → Final Response

## Common Agent Types

### Coordinator Agent
- Delegates tasks
- Manages workflow
- Combines outputs

### Specialist Agents
- Research Agent
- Retrieval Agent
- SQL Agent
- Coding Agent
- Reporting Agent

## Single-Agent vs Multi-Agent

### Single-Agent
- Faster
- Cheaper
- Simpler
- Best for straightforward tasks

### Multi-Agent
- More specialized
- Better scalability
- Better for complex workflows
- Higher latency
- More expensive

## When to Use Single-Agent
- FAQ bots
- Knowledge assistants
- Simple chatbots

## When to Use Multi-Agent
- Enterprise research
- Analytics systems
- Complex workflows
- Multi-step automation

## Agentic AI Relationship
Agentic AI
├── Single-Agent Systems
└── Multi-Agent Systems

Multi-Agent Systems are a subset of Agentic AI.

### Key Exam Notes
- Single-Agent = One agent
- Multi-Agent = Multiple specialized agents
- Multi-Agent uses orchestration
- Single-Agent is cheaper and faster
- Multi-Agent is more scalable and specialized

---

# 5. Use Case Selection

## Core Principle
Choose the simplest architecture that satisfies requirements.

## Selection Guide

### Need latest/private knowledge?
Use RAG

### Need actions/tools?
Use Agent

### Need specialized collaboration?
Use Multi-Agent

### Need behavior/style change?
Use Fine-Tuning

## Common Use Cases

### Document Question Answering
Best Choice: RAG

### Company Knowledge Assistant
Best Choice: RAG

### Content Generation
Best Choice: Foundation LLM + Prompt Engineering

### Summarization
Best Choice: LLM

### Sentiment Analysis
Best Choice: LLM or Traditional ML

### Database Query Assistant
Best Choice: Agent

### Workflow Automation
Best Choice: Agent

### Enterprise Research Assistant
Best Choice: Multi-Agent

### FAQ Chatbot
Best Choice: RAG

### Personalized Writing Style
Best Choice: Fine-Tuning

## RAG vs Fine-Tuning

### RAG
- New knowledge
- Dynamic updates
- External knowledge

### Fine-Tuning
- Style changes
- Behavior customization

## Agent vs RAG

### RAG
Document retrieval

### Agent
Actions and tool usage

### Agent + RAG
Knowledge retrieval plus actions

### Key Exam Notes
- Documents → RAG
- Latest knowledge → RAG
- Actions → Agent
- Specialized collaboration → Multi-Agent
- Style change → Fine-Tuning
- Content generation → Foundation Model + Prompting

---

# 6. Latency vs Accuracy Tradeoffs

## What is Latency?
Time required to generate a response.

Lower latency = Faster response

Higher latency = Slower response

## What is Accuracy?
How correct and relevant the answer is.

## Tradeoff
Improving accuracy often increases latency.

## Model Size Tradeoff

### Small Models
- Faster
- Cheaper
- Lower reasoning capability

### Large Models
- Better reasoning
- Better quality
- Higher cost
- Higher latency

## Retrieval Tradeoff

### Few Retrieved Chunks
- Faster
- Lower cost
- Less context

### Many Retrieved Chunks
- Better context coverage
- More tokens
- Higher latency
- Higher cost

## Prompt Length Tradeoff

### Short Prompt
- Faster
- Cheaper

### Long Prompt
- More context
- Higher latency
- Higher cost

## Agent Tradeoff

### Single-Agent
- Faster
- Simpler
- Lower cost

### Multi-Agent
- Higher specialization
- Better quality
- More latency
- More cost

## Fine-Tuning vs RAG

### Fine-Tuning
- No retrieval step during inference
- Potentially faster
- Expensive training

### RAG
- Retrieval + generation
- Easier knowledge updates

## Optimization Techniques

### Reduce Latency
- Smaller models
- Shorter prompts
- Better retrieval
- Fewer retrieved chunks
- Caching

### Improve Accuracy
- Better prompts
- Grounding
- Better embeddings
- Better retrieval
- Larger models


---

# Final Design Applications Revision (Must Memorize)

1. LLM = Large Language Model.
2. Foundation Model = Pretrained model.
3. Fine-Tuning changes behavior/style.
4. RAG retrieves external knowledge.
5. Agent = LLM + Reasoning + Tools.
6. Agentic AI includes Single-Agent and Multi-Agent systems.
7. Multi-Agent Systems are a subset of Agentic AI.
8. Grounding reduces hallucinations.
9. Prompt Injection attempts to override instructions.
10. Few-Shot Prompting uses multiple examples.
11. Chain of Thought improves reasoning.
12. Knowledge Assistant typically uses RAG.
13. Workflow Automation typically uses Agents.
14. Latest knowledge → RAG.
15. Style customization → Fine-Tuning.
16. Actions and tool calling → Agent.
17. Complex collaboration → Multi-Agent.
18. More tokens increase cost and latency.
19. Larger models improve quality but increase latency.
20. The best architecture is the simplest one that satisfies the requirement.

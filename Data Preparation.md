# Databricks Generative AI Engineer Associate
# Data Preparation (14%) - Complete Study Notes

## Index

1. Document Ingestion
2. Text Cleaning
3. Chunking Strategies
4. Embeddings
5. Metadata Management
6. Vector Search
7. End-to-End Data Preparation Flow
8. Final Revision Notes

---

# 1. Document Ingestion

## Definition
Document Ingestion is the process of bringing documents into a GenAI/RAG system for processing.

## Purpose
- Collect documents
- Load documents
- Prepare documents for parsing and processing

## Common Data Sources

### Unstructured Data
- PDF
- DOCX
- PPT
- HTML
- Emails
- Reports
- Articles

### Structured Data
- CSV
- Excel
- Database Tables

## Ingestion vs Parsing

### Ingestion
Load documents into the system.

### Parsing
Extract text and structure from documents.

## Common Sources
- Local File Systems
- SharePoint
- Cloud Storage
- Enterprise Applications
- Databases

## Ingestion Types

### Batch Ingestion
- Scheduled processing
- Large document volumes
- Lower operational cost

### Real-Time Ingestion
- Immediate processing
- Instant availability
- Suitable for user uploads

## Metadata During Ingestion
Examples:
- File Name
- Author
- Department
- Creation Date
- Source System

## Data Quality Considerations
- Duplicate files
- Corrupted documents
- Unsupported formats
- Missing metadata

## Exam Notes
- Ingestion is the first step in Data Preparation.
- Ingestion = Load documents.
- Parsing = Extract content.
- Most RAG systems primarily use unstructured data.

---

# 2. Text Cleaning

## Definition
Text Cleaning removes noise and improves the quality of extracted text before chunking.

## Position in Pipeline

Documents
→ Ingestion
→ Parsing
→ Cleaning
→ Chunking

## Why Text Cleaning?
Benefits:
- Better chunk quality
- Better embeddings
- Better retrieval
- Lower token usage
- Lower cost and latency

## Common Cleaning Operations

### Remove Headers
Example:
Repeated company title on every page.

### Remove Footers
Example:
Page 10 of 100.

### Remove Extra Spaces

Before:
Multiple spaces.

After:
Single spaces.

### Remove Blank Lines

### Remove Special Characters

### Fix Encoding Issues
Example:
Corrupted characters after extraction.

### Remove Duplicate Content

### Correct OCR Errors
Example:
P0licy → Policy

## What Should Not Be Removed?
- Business meaning
- Important numbers
- Dates
- Product names
- Policies

## Cleaning vs Chunking

### Cleaning
Remove noise.

### Chunking
Split content.

## Exam Notes
- Cleaning happens after parsing.
- Cleaning happens before chunking.
- Remove noise, not meaning.
- Better cleaning improves retrieval quality.

---

# 3. Chunking Strategies

## Definition
Chunking is the process of splitting large documents into smaller searchable units.

## Why Chunking is Needed
Benefits:
- Faster retrieval
- Better relevance
- Reduced token usage
- Better context management

## Chunk Size Tradeoff

### Small Chunks
Advantages:
- Higher precision

Disadvantages:
- Less context

### Large Chunks
Advantages:
- More context

Disadvantages:
- Lower precision
- Higher token usage

## Types of Chunking

### Fixed-Size Chunking
Split every fixed number of tokens/characters.

Advantages:
- Simple
- Fast

Disadvantages:
- Can break meaning

### Recursive Chunking
Splits intelligently using:
- Paragraphs
- Sentences
- Words

Advantages:
- Better context preservation
- Common production approach

### Semantic Chunking
Chunks are created based on meaning.

Advantages:
- Highest semantic quality
- Better retrieval

Disadvantages:
- More expensive

### Document-Based Chunking
Uses:
- Headings
- Subheadings
- Sections

## Chunk Overlap

### Definition
Shared content between adjacent chunks.

### Purpose
Preserve context near chunk boundaries.

Example:
Chunk 1: A B C D E
Chunk 2: D E F G H

## Impact of Chunking

Good Chunking
→ Better Embeddings
→ Better Retrieval
→ Better Answers

Bad Chunking
→ Poor Retrieval

## Exam Notes
- Chunking occurs before embeddings.
- Each chunk gets its own embedding.
- Chunk overlap preserves context.
- Recursive chunking is common.
- Semantic chunking preserves meaning best.

---

# 4. Embeddings

## Definition
An embedding is a numerical vector representation of text that captures semantic meaning.

## Purpose
Convert text into numbers that computers can compare.

Flow:
Text
→ Embedding Model
→ Vector

## Why Embeddings?
Enable semantic search.

Example:
- Vacation Policy
- Annual Leave Policy

Different words, similar meaning.

## Semantic Similarity
Similar meaning produces similar vectors.

## Embedding Model
Responsibilities:
- Convert text into vectors
- Capture semantic meaning

Does NOT:
- Generate answers
- Perform retrieval

## Chunk Embeddings
Every chunk receives an embedding.

Example:
100 chunks
→ 100 embeddings

## Query Embeddings
User questions are also converted into vectors.

Flow:
User Question
→ Embedding Model
→ Query Vector

## Embedding Dimensions
Examples:
- 384
- 768
- 1536
- 3072

Dimension = Number of values inside a vector.

## Benefits
- Semantic matching
- Better retrieval
- Better relevance

## Embedding Model vs LLM

### Embedding Model
Creates vectors.

### LLM
Generates answers.

## Exam Notes
- Embeddings represent meaning.
- Similar meanings create similar vectors.
- Documents and queries both get embeddings.
- Embedding models create vectors.
- LLMs generate responses.

---

# 5. Metadata Management

## Definition
Metadata is data about data.

It describes documents and chunks.

## Examples
- File Name
- Page Number
- Document ID
- Department
- Author
- Source
- Creation Date
- Section Name

## Why Metadata Matters
Benefits:
- Better retrieval
- Filtering
- Security
- Governance
- Traceability
- Citations

## Metadata Filtering

Examples:

### Department Filter
department = HR

### Date Filter
year = 2026

### Document Type Filter
document_type = policy

## Metadata and Security
Metadata can control access.

Example:
access_level = finance

Only finance users can retrieve content.

## Metadata and Citations
Example:
Source: Employee Handbook.pdf
Page: 15

## Metadata and Governance
Helps answer:
- Who created it?
- Where did it come from?
- When was it uploaded?

## Metadata vs Embeddings

Metadata:
- Describes content
- Used for filtering

Embeddings:
- Represent meaning
- Used for semantic search

## Exam Notes
- Metadata improves retrieval precision.
- Metadata enables filtering.
- File name is metadata.
- Page number is metadata.
- Department is metadata.
- Metadata supports governance and auditing.

---

# 6. Vector Search

## Definition
Vector Search finds semantically similar content by comparing embeddings.

## Purpose
Retrieve relevant chunks based on meaning rather than exact keywords.

## Why Vector Search?
Keyword Search:
Exact word matching.

Vector Search:
Meaning matching.

## Retrieval Flow

User Question
→ Query Embedding
→ Vector Search
→ Top-K Chunks
→ LLM
→ Answer

## How It Works

### Step 1
Generate embeddings for document chunks.

### Step 2
Store vectors in a vector database.

### Step 3
Convert user question into a query vector.

### Step 4
Compare query vector with stored vectors.

### Step 5
Return nearest matches.

## Similarity Search
Core Principle:

Similar Meaning
→ Similar Embeddings

## Top-K Retrieval

Examples:
- Top 3
- Top 5
- Top 10

### Small K
Advantages:
- Faster
- Lower cost

Disadvantages:
- Less context

### Large K
Advantages:
- More context

Disadvantages:
- Higher latency
- More token usage

## Metadata + Vector Search

Filter First:
- Department = HR
- Year = 2026

Then:
Perform similarity search.

Benefits:
- Better precision
- Faster retrieval

## Vector Database Responsibilities
- Store vectors
- Search vectors
- Return similar vectors

## Vector Database vs Traditional Database

Traditional Database:
Exact match.

Vector Database:
Semantic match.

## Exam Notes
- Vector Search performs semantic retrieval.
- Query and chunk embeddings are compared.
- Top-K determines number of retrieved chunks.
- Metadata filters improve search quality.
- Vector Search retrieves; LLM answers.

---

# 7. End-to-End Data Preparation Flow

```text
Documents
    ↓
Document Ingestion
    ↓
Parsing
    ↓
Text Cleaning
    ↓
Chunking
    ↓
Embeddings
    ↓
Metadata
    ↓
Vector Database
```

## RAG Retrieval Flow

```text
User Question
    ↓
Query Embedding
    ↓
Vector Search
    ↓
Top-K Chunks
    ↓
LLM
    ↓
Answer
```

---

# 8. Final Revision Notes (Must Memorize)

1. Document Ingestion = Load documents into the system.
2. Parsing = Extract text and structure.
3. Text Cleaning removes noise and improves quality.
4. Chunking splits documents into smaller searchable units.
5. Chunk Overlap preserves context.
6. Small chunks = Higher precision, less context.
7. Large chunks = More context, less precision.
8. Recursive chunking is common in production.
9. Semantic chunking preserves meaning best.
10. Embeddings are numerical representations of meaning.
11. Similar meaning produces similar vectors.
12. Every chunk receives its own embedding.
13. User queries are also embedded.
14. Metadata = Data about data.
15. File name, page number, and department are metadata.
16. Metadata filtering improves retrieval relevance.
17. Vector Search compares embeddings.
18. Vector Search performs semantic retrieval.
19. Top-K determines how many chunks are returned.
20. LLM generates answers; Vector Search retrieves context.
21. Better chunking improves retrieval quality.
22. Better embeddings improve retrieval quality.
23. Better metadata improves retrieval quality.
24. Better retrieval improves answer quality.
25. Data Preparation is the foundation of every RAG application.

# Prompt Engineering
> the way you design and structure inputs (prompts) to get the best possible output from AI models like ChatGPT, Copilot, etc.

## Prompt Engineering Types

Prompt engineering is the practice of designing effective inputs (prompts) to get accurate and useful outputs from AI models.

---

## 1. Zero-shot Prompting
Providing a task without any examples.

**Example:**
Translate "Hello" into French.

---

## 2. One-shot Prompting
Providing one example to guide the model.

**Example:**
English: Hello → French: Bonjour  
English: Thank you → French:

---

## 3. Few-shot Prompting
Providing multiple examples to improve accuracy.

**Example:**
Input: Cat → Animal  
Input: Rose → Plant  
Input: Dog →

---

## 4. Instruction-based Prompting
Giving a clear instruction to the model.

**Example:**
Write a professional email requesting leave for 2 days.

---

## 5. Role-based Prompting
Assigning a role or persona to the AI.

**Example:**
Act as a data scientist and explain machine learning in simple terms.

---

## 6. Chain-of-Thought (CoT) Prompting
Encouraging step-by-step reasoning.

**Example:**
Solve step-by-step: If a train travels 60 km in 1 hour, how far in 5 hours?

---

## 7. Self-consistency Prompting
Generating multiple reasoning paths and selecting the best answer.

**Concept:**
- Solve the same problem multiple times  
- Choose the most consistent output  

---

## 8. Iterative Prompting
Refining prompts step by step based on responses.

**Example Flow:**
1. Write an article  
2. Make it concise  
3. Add bullet points  

---

## 9. Contextual Prompting
Providing background or data along with the request.

**Example:**
Based on the following sales data, summarize trends: [data]

---

## 10. Output-format Prompting
Specifying the desired output format.

**Example:**
Provide the answer in JSON format with fields: name, age, role.

---

## 11. Constraint-based Prompting
Adding rules or limitations to the response.

**Example:**
Explain cloud computing in less than 100 words without technical jargon.

---

## 12. Prompt Chaining
Breaking complex tasks into multiple connected prompts.

**Example:**
1. Generate ideas  
2. Select the best idea  
3. Expand into full content  

---  

# RAG
**Without RAG:**  
Imagine ChatGPT itself.  
You ask:  
  - What is Eisai's internal Oncology SOP document?  
The model cannot answer because:  
  - It was trained on public data  
  - It does not know Eisai's internal documents  
  - It cannot access private company data  
Result:  
❌ Hallucination  or  ❌ "I don't know"

**The Boundaries of LLM/Prompting:**  
**The Knowledge Cutoff:** The model cannot answer questions about events that occurred after the cutoff date of its training data.  
Example Prompt: Who won the 2025 Nobel Prize in Physics?  

**Hallucination:** When asked for specific facts without external references, models often prioritize plausibility over truth, fabricating citations or data points.  
Example Prompt: Find a scientific reference proving that avocado reduces blood sugar levels  

**Ambiguity:** Without private context, models default to generic interpretations.  
Example Prompt: Explain how to secure a lakehouse. (This triggers advice on physical home security rather than Databricks Data Lakehouse governance.)  

### Retrival Agent:
A retrieval agent is like a smart assistant that first “searches for information” and then gives you an answer. it is a part of RAG. 
Normal AI Gives answers on Pre-trained data. Retrieval Agent gives real-time date. 

**With RAG:**
Before sending the question to the LLM:  
- Search company documents
- Find relevant information
- Send that information to the LLM
- LLM generates answer using retrieved content

Result:  
✅ Accurate answer
✅ Based on company documents
✅ Less hallucination

Think of RAG like an open-book exam:  
❌ Normal AI → answers from memory (may guess)  
✅ RAG → opens book → finds info → then answers  

RAG = Retrieval + Augmented + Generation  
Retrieval  
 - Find relevant documents.  
Augmented  
 - Add those documents into prompt.  
Generation  
 - LLM generates answer.

**End-to-End RAG Architecture:**
```
PDF/DOCX/PPT
      ↓
Databricks Volume
      ↓
Parsing
      ↓
Cleaning
      ↓
Chunking
      ↓
Embedding
      ↓
Vector Database
      ↓
User Question
      ↓
Embedding
      ↓
Similarity Search
      ↓
Top Relevant Chunks
      ↓
Prompt Construction
      ↓
     LLM
      ↓
Final Answer
```  
## How RAG Works (Step-by-step)
User asks a question  
System retrieves relevant data from:  
 - Documents (PDFs, SharePoint)
 - Databases
 - Websites / knowledge sources
AI reads the retrieved info  
AI generates a final answer based on that data








**Parsing**
Parsing the document to structured
Transform and chunk parsed document & save to Delta table


**EMBEDDING:**
 > Converting text to numbers (vector representation)

Databricks GTE Large: Text Embeding Model
 > for video, audio, images we use respective embeded models.

**VECTOR DATABASE:**
- A normal database finds exact matches  
  EG: Search: "car"  
  Result: documents containing the word "car"

- A Vector Database finds documents with similar meaning
  Search: "vehicle"  
  Result: documents about cars, trucks, automobiles, transport, etc. 

A vector database stores both document embeddings and query embeddings, but in different ways.  
1. Document Embeddings (Stored Permanently)
2. Query Embeddings (Temperary on the fly)

> Databricks Mosaic AI Vector Search : Vector DB

**Search Methods**
A. Similarity Search
B. Full-Text Search
C. Hybrid Search

**Search Strategies**
A. KNN (K-Nearest Neighbors)
B. ANN (Approximate Nearest Neighbors)

**What is Reranking?**
Reranking is a second quality check. WHERE WE RE-CHECK AND REORDER.
Retraval(fast, broad): vector search pulls top-20 chunks.
Reranking(slower, precise): a specialized reranking model looks at hte actual question + each chunk together and scores how relevent each one is. only top 3 to 5 reranked chunks gt passed into the augumented prompt template before sent to llm.

**Delta Sync**  
You add a new document to Delta Table.  
Automatically:  
 1. Embedding created  
 2. Vector index updated

**Vector Index:**
A Vector Index is a special data structure inside a vector database that helps find similar vectors very quickly.    

**Vector Search Endpoint:**
A Vector Search Endpoint is the service that receives search requests and performs similarity search on your vector indexes. The endpoint knows where the vector indexes are and executes the search when a query arrives.   

- Vector Database = Library
- Vector Index = Library Books/Catalog
- Vector Search Endpoint = Librarian
```
User Question
      ↓
Embedding Model
      ↓
Vector Search Endpoint
      ↓
 Vector Index
      ↓
Relevant Chunks
      ↓
    LLM
      ↓
Final Answer
```

**Log and Register the model**
```
Train Model
     ↓
Log Model with MLflow
     ↓
Register Model in Unity Catalog
     ↓
Model Version Created
     ↓
Load and Test the model
     ↓
Deploy / Serve Model
```

**DELTA**
Data Lake = data warehouse where all data exists
Delta Lake = data warehouse + Tracing ...etc(Technology) which supports ACID Transaction, Time Travel, Fast Query...etc
Delta Table = a table created with delta lake technology


## Agent Bricks

# FLOW


1. Data Layer (Sources + ingestion)  
2. AI Layer (Databricks + RAG + LLM Agent)  
3. Application Layer (UI + User interaction)  

## 1. Application Layer
**LangChain:**
Think of it as a connector/orchestrator that links all AI components together.  Without LangChain, You need to manually connect. 

When a user sends a query, LangChain receives it,  
creates a query embedding, searches the vector database  
through a retriever, retrieves relevant document chunks,   
builds a prompt containing the question and retrieved context,  
sends it to the LLM, and returns the generated answer.  
If memory or agents are enabled, LangChain also includes  
conversation history and tool calls in the workflow.   

> LangChain = Glue between LLM + Vector DB + Prompts + Tools

```
User Question
       ↓
LangChain
       ↓
Retriever
       ↓
Embedding Model
       ↓
Query Embedding
       ↓
Vector Search Endpoint
       ↓
Vector Index
       ↓
Top Matching Chunks
       ↓
Prompt Template
       ↓
      LLM
       ↓
Generated Answer
       ↓
     User
```
## 2.  AI Layer
```
1. Databricks Volume (Raw Documents)
   ↓
   Tools: Databricks Volume, MuleSoft, MS Graph API

2. Parsing (Extract Text + Structure)
   ↓
   Tools: LangChain Loaders, Unstructured, PyPDF, Tika

3. Cleaning (Remove Noise)
   ↓
   Tools: Python (regex), NLTK, spaCy, BeautifulSoup

4. Chunking (Split Text)
   ↓
   Tools: LangChain Text Splitters

5. Embeddings (Text → Vector)
   ↓
   Tools: Databricks Embedding Models / OpenAI / HF

6. Store in Delta Table
   ↓
   Tools: PySpark, Delta Lake (text + embedding + metadata)

7. Create Vector Index
   ↓
   Tools: Databricks Vector Search
```
## 3. Data Layer
**Data Sources (Where data comes from)**  
Primary Sources:  
Pulse SharePoint: HR, Compliance, Finance docs, Policies, SOPs, internal content  
Veeva eDocs:  Scientific / pharma documents  

Integration:  
MuleSoft → pulls Veeva content  
Copies to SharePoint (Pulse site)  
👉 So final central knowledge source = SharePoint + Veeva docs  

**Data Ingestion into Databricks:**
MS Graph API + Python notebooks: Pull files from SharePoint  
Store data in: Databricks Volume (raw files)  

## For Monitoring & Reporting: Tableau Dashboard
Tracks:  

User activity  
Query volume  
Response time  
Feedback (51% positive, 40% negative)  

👉 Used for: Weekly stakeholder review  

# Project Files
## 1. app.py → Main application entry point
This is the core file that runs your application. Contains the main logic, routes, API endpoints, or chatbot flow  

This will handle:  
User query  
Call to LLM / RAG pipeline  
Return response to UI  

## 2. app.yaml → Deployment configuration
Here’s how to start my app and what environment it needs.
**What it usually contains:**  
Runtime (Python version)  
Entry point command  
Scaling settings  
Environment variables  

## 3. requirements.txt → Dependencies list
Lists all Python libraries your project depends on  
pip install -r requirements.txt  

## utils.py
Stores reusable logic  
Keeps app clean  
Contains RAG pipeline, embeddings, LLM calls  

# Streamlit
You build a complete app (UI + logic) in one file. No need for HTML, React, etc.
Streamlit app
   ↓
UI + Python logic together
   ↓
LLM / RAG

# Databricks mainly has 3 types of endpoints:
1. Model Serving Endpoint → for LLM/model inference  
2. Vector Search Endpoint → for embedding similarity search  
3. SQL Warehouse Endpoint → for querying data  



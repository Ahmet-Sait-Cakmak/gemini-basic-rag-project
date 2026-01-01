# 📚 PDF-based Chatbot using Basic RAG (Gemini + LangChain)

## 📌 Project Overview
This project implements a *PDF-based Question Answering chatbot* using a *Basic Retrieval-Augmented Generation (RAG)* architecture.  
The chatbot answers user questions by retrieving relevant information from a given PDF document and generating grounded responses using a Large Language Model (LLM).

The main goal of the project is to *reduce hallucinations in LLM outputs* by grounding answers in external documents, rather than relying solely on the model’s internal knowledge.

---

## 🧠 Motivation
Large Language Models are prone to *hallucinations*, meaning they may generate fluent but factually incorrect answers when:
- The training data is incomplete or ambiguous
- The model lacks access to up-to-date or domain-specific information
- The prompt requires precise factual grounding

To address this problem, this project adopts a *Retrieval-Augmented Generation (RAG)* approach, which injects external knowledge into the generation process.

---

## 🏗️ System Architecture
The system follows a *Basic RAG pipeline*:

1. *Document Loading*
   - A predefined PDF document is loaded into the system.
2. *Text Chunking*
   - The document is split into smaller overlapping text chunks.
3. *Embedding*
   - Each chunk is converted into vector embeddings using *Google Generative AI Embeddings*.
4. *Vector Store*
   - Embeddings are stored in a vector database.
5. *Retrieval*
   - For each user query, the most relevant chunks are retrieved.
6. *Generation*
   - Retrieved contexts are passed to the Gemini LLM to generate a grounded answer.

⚠️ *Note:*  
This project intentionally does *not* use intent classification.  
The focus is strictly on evaluating *retrieval quality and grounding performance* of a pure RAG system.

---

## 🤖 Technologies Used
- *Python*
- *LangChain*
- *Google Gemini (LLM)*
- *Google Generative AI Embeddings*
- *Vector Store (Chroma / FAISS)*
- *RAGAS (RAG Assessment Framework)*

---

## 📊 Evaluation Methodology (RAGAS)
To evaluate the chatbot’s performance, the *RAGAS framework* is used.  
A synthetic evaluation dataset is created consisting of:
- question
- answer (model output)
- ground_truth (expected correct answer)
- contexts (retrieved document chunks)

### Metrics Used
- *Faithfulness*
  - Measures whether the generated answer is supported by the retrieved context.
- *Answer Relevancy*
  - Measures how well the answer addresses the question.
- *Context Precision*
  - Measures how relevant the retrieved contexts are.
- *Context Recall*
  - Measures how much of the required information was successfully retrieved.

These metrics together provide a *quantitative measure of hallucination reduction and retrieval quality*.

---

## 🧪 Test Scenario Design
- A fixed PDF document is used as the knowledge source.
- Multiple manually designed questions related to the PDF content are asked.
- Ground-truth answers are prepared based on the PDF.
- The RAG pipeline is executed for each question.
- Results are evaluated using RAGAS with Gemini as the judge LLM.

---

## 📈 Results
The evaluation results are exported into a tabular format using:
```python
report.to_pandas()

## 🎥 Tanıtım Videosu

Chatbot’un çalışır halini gösteren tanıtım videosuna aşağıdaki linkten ulaşabilirsiniz:

[▶️ Tanıtım videosunu izlemek için tıklayın](https://github.com/Ahmet-Sait-Cakmak/gemini-basic-rag-project/blob/master/Proje%20Tan%C4%B1t%C4%B1m%20Videosu.mp4)

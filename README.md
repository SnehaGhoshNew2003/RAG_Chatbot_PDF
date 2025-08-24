# RAG chatbot for PDFs
This README explains the provided **Google Colab** notebook that builds a simple **Retrieval-Augmented Generation (RAG)** pipeline over **PDF documents** using:

- **Sentence-Transformers** for embeddings  
- **FAISS** for vector search  
- **PyPDF2** for PDF text extraction  
- **Google Gemini (gemini-1.5-flash)** for answer generation  

The notebook loads one or more PDFs, splits them into chunks, builds a FAISS index, and then runs an interactive Q&A loop in the terminal cell.

---

## What the notebook does

1. Installs required packages (`faiss-cpu`, `PyPDF2`, `docx2txt`).  
2. (You should also install `sentence-transformers` and `google-generativeai` — see **Requirements** below.)  
3. Sets the **Google API key** ( hardcoded in the shared code; don’t do this in real projects).  
4. Defines helper functions:
   - `load_text_from_file(path)` → reads PDF text via `PyPDF2` (**only .pdf supported**).  
   - `split_text(text, chunk_size=1000, overlap=200)` → splits text into overlapping chunks.  
   - `build_faiss_index(chunks)` → embeds with `all-MiniLM-L6-v2`, normalizes vectors, and builds a FAISS inner-product index (cosine similarity).  
   - `rag_query(question, index, documents, embedding_model, top_k=3)` → retrieves top chunks and queries **Gemini 1.5 Flash** with a context-augmented prompt.  
5. Defines a `files = [...]` list of PDF paths, builds the index, then starts an **interactive loop**:
   - Type a question and press **Enter**.  
   - Type `exit` to stop.  

---

## Requirements

Install these (in Colab or locally):

```bash
pip install faiss-cpu
pip install PyPDF2
pip install docx2txt
pip install sentence-transformers
pip install google-generativeai
pip install python-dotenv  # optional, if you want to load env vars from .env

# RAG_Chatbot_PDF

This is a Retrieval-Augmented Generation (RAG) chatbot that:
- Lets you ask questions about your PDF/DOCX/TXT documents
- Uses **SentenceTransformers** + **FAISS** for retrieval
- Uses **Google Gemini 1.5 Flash** as the LLM
- Built with **Gradio** and deployed on Hugging Face Spaces 🚀

## Setup

1. Add your Gemini API key as a **Secret** in Hugging Face Spaces:
   - Go to **Settings > Repository secrets**
   - Add:  
     ```
     GEMINI_API_KEY=your_api_key_here
     ```

2. Upload documents in the `files = [...]` section of `app.py` or extend the UI to support uploads.

3. Run the app! 

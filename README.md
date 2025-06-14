# RAG_with_GroqAPI
<h1 align="center">Retrieval-Augmented Generation with Gradio and Groq API Key</h1>
<p align="center">Natural Language Processing Project</p>

<div align="center">

<img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54">

</div>

### Name : Muhammad Rahmad
### Tech Stack : Python, Gradio, LangChain, HuggingFace Embeddings, FAISS, Groq API

---

### 1. Analysis about how the project works

Proyek ini menggunakan pendekatan **Retrieval-Augmented Generation (RAG)** untuk menjawab pertanyaan dari file PDF.

#### Alur kerja:
1. **PDF Upload**: Pengguna mengunggah file PDF lewat Gradio.
2. **Loading dan Split**: PDF dibaca dan dipecah menjadi chunks (1000 karakter dengan overlap 200).
3. **Embedding**: Chunks diubah menjadi vektor menggunakan model `sentence-transformers/all-MiniLM-L6-v2`.
4. **Indexing**: Vektor disimpan di FAISS vector store.
5. **Retrieval**: Top 4 dokumen yang paling relevan diambil untuk setiap pertanyaan.
6. **LLM Response**: Dokumen + pertanyaan dikirim ke LLM dari Groq API untuk menghasilkan jawaban.

---

### 2. Analysis about how different every model works on Retrieval-Augmented Generation

Model dapat diubah lewat parameter `model_name` di fungsi `get_llm()`:

```python
def get_llm():
    return ChatGroq(
        groq_api_key=GROQ_API_KEY,
        model_name="llama-3.3-70b-versatile",  # Ubah di sini
        temperature=0.2
    )

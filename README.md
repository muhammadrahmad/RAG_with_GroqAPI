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

2.1 llama-3.3-70b-versatile
Model besar dan sangat akurat.

Jawaban panjang dan sesuai konteks PDF.

Cocok untuk pertanyaan mendalam atau teknis.

Waktu respons lebih lama.

2.2 deepseek-r1-distill-llama-70b
Distilasi model LLaMA.

Jawaban cepat dan tetap cukup akurat.

Gaya bahasa ringkas dan efisien.

Tidak sedalam llama-3.3, tapi cocok untuk user experience ringan.

2.3 gemma2-9b-it
Model kecil, respons sangat cepat.

Jawaban cenderung lebih umum dan kadang terlalu singkat.

Kurang cocok untuk detail teknis.

3. Analysis about how temperature works
Temperatur dikontrol di fungsi get_llm():

temperature=0.2  # nilai default, bisa diubah

3.1 Higher temperature (> 0.7)
Jawaban menjadi lebih kreatif dan beragam.

Meningkatkan risiko "halusinasi" atau informasi yang tidak sesuai dokumen.

Bisa digunakan untuk brainstorming, bukan fakta akurat.

3.2 Lower temperature (< 0.3)
Jawaban cenderung konsisten, deterministik, dan sesuai dokumen.

Cocok untuk Q&A berbasis fakta, seperti isi PDF.

Jawaban kurang variatif.

4. How to run the project
1. Clone repository
git clone https://github.com/arifian853/RAG_with_GroqAPI.git
cd RAG_with_GroqAPI

2. Install dependencies

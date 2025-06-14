# 📄 RAG_with_GroqAPI

<h1 align="center">Retrieval-Augmented Generation with Gradio and Groq API</h1>
<p align="center">Natural Language Processing Final Project</p>

<div align="center">
  <img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54">
</div>

### 👤 Name : Muhammad Rahmad  
### 🧠 Tech Stack : Python, Gradio, LangChain, HuggingFace Embeddings, FAISS, Groq API

---

## 🔍 1. Project Overview

Proyek ini menerapkan pendekatan **Retrieval-Augmented Generation (RAG)** untuk menjawab pertanyaan dari isi file PDF menggunakan model LLM dari Groq. Dibangun dengan antarmuka **Gradio**, proyek ini memungkinkan pengguna mengunggah PDF, mengajukan pertanyaan, dan mendapatkan jawaban yang relevan.

### 📌 Alur Kerja:
1. **Upload File PDF** melalui antarmuka Gradio.
2. **Split PDF** menjadi potongan teks (chunk) menggunakan `CharacterTextSplitter`.
3. **Embedding** menggunakan `sentence-transformers/all-MiniLM-L6-v2`.
4. **Indexing** dengan FAISS vector store.
5. **Retrieval** dokumen paling relevan.
6. **Generasi Jawaban** menggunakan model LLM dari Groq API.

---

## 🧪 2. Model Comparison

Model bisa diatur di fungsi `get_llm()` melalui parameter `model_name`.

```
def get_llm():
    return ChatGroq(
        groq_api_key=GROQ_API_KEY,
        model_name="llama-3.3-70b-versatile",
        temperature=0.2
    )
```

### ✨ 2.1 `llama-3.3-70b-versatile`
- Model besar dan akurat
- Jawaban lengkap dan relevan
- Cocok untuk pertanyaan teknis
- Waktu respons lebih lama

### ⚡ 2.2 `deepseek-r1-distill-llama-70b`
- Model distilasi dari LLaMA
- Lebih cepat dari llama-3.3
- Gaya jawaban lebih ringkas
- Kurang detail pada pertanyaan kompleks

### ⚙️ 2.3 `gemma2-9b-it`
- Model kecil dan sangat cepat
- Jawaban cenderung lebih umum
- Kurang cocok untuk pertanyaan teknis mendalam

---

## 🌡️ 3. Temperature Tuning

Parameter `temperature` digunakan untuk mengontrol tingkat kreativitas model.

```
temperature=0.2  # Nilai default (rekomendasi untuk akurasi)
```

### 🔥 3.1 Higher Temperature (> 0.7)
- Jawaban lebih kreatif dan variatif
- Berisiko menghasilkan informasi yang tidak akurat (halusinasi)

### 🧊 3.2 Lower Temperature (< 0.3)
- Jawaban lebih akurat dan konsisten
- Kurang fleksibel atau terlalu kaku

---

## 🚀 4. How to Run This Project

### ✅ Langkah-langkah:

1. **Clone Repository:**
```
git clone https://github.com/muhammadrahmad/RAG_with_GroqAPI.git
cd RAG_with_GroqAPI
```

2. **Install Dependencies:**
```
pip install -r requirements.txt
```

3. **Atur Environment Variable:**
- Copy `.env.example` lalu ubah nama menjadi `.env`
- Isi dengan Groq API Key:

```
GROQ_API_KEY=your-groq-api-key
```

- Dapatkan API key dari: https://console.groq.com/keys

4. **Jalankan Aplikasi:**
```
python app.py
```

5. **Gunakan Gradio di browser:**
- Unggah file PDF
- Ketik pertanyaan
- Dapatkan jawaban dari LLM berdasarkan isi dokumen

---

## 📁 File Structure

```
RAG_with_GroqAPI/
├── app.py
├── .env.example
├── requirements.txt
├── README.md
```

---

## 📌 Example Use Case

> PDF: SK KELULUSAN SDIT AN NAHL Seri Kuala Lobam
> Pertanyaan: "Ada berapakah jumlah anak yang dinyatakan lulus?"  
> Jawaban: *41 Anak*

---

## 🛠️ Future Work

- Tambahkan dukungan untuk multi-file
- Tambah fitur simpan riwayat pertanyaan
- UI lebih interaktif dengan chat-style

---

## 📃 License

This project is licensed under the MIT License.

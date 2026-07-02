# 🤖 Modul Praktikum RAG — Fondasi Retrieval-Augmented Generation

> **Mata Kuliah:** Big Data & Analitik  
> **Dosen Pengampu:** Herianto, S.Pd., M.T.  
> **Mahasiswa:** Andreas Rio Christian — NIM 2023230031  
> **Platform:** Google Colab · Bahasa Indonesia

---

## 📖 Deskripsi

Repositori ini berisi modul praktikum yang membangun sistem **Retrieval-Augmented Generation (RAG)** dari nol. RAG adalah teknik yang memungkinkan Large Language Model (LLM) menjawab pertanyaan berdasarkan dokumen sumber, bukan hanya dari pengetahuan bawaannya, sehingga jawaban yang dihasilkan lebih akurat dan dapat ditelusuri.

Praktikum ini mencakup seluruh pipeline RAG:

```
Dokumen  →  Chunking  →  Embedding  →  FAISS Index  →  Semantic Search  →  LLM Answer
```

---

## 📂 Struktur Repositori

```
Retrieval-Augmented-Generation/
└── Modul_Praktikum_RAG_Fondasi_v4 - Andreas Rio Christian 2023230031.ipynb
```

---

## 🎯 Kompetensi yang Dicapai

Setelah menyelesaikan praktikum ini, mahasiswa mampu:

- ✂️ **Memotong** dokumen panjang secara rekursif (*recursive chunking*) dengan LangChain
- 🔢 **Mengubah** teks berbahasa Indonesia menjadi vektor menggunakan model embedding multilingual
- 🗄️ **Membangun** basis data vektor lokal dengan **FAISS** dan melakukan pencarian semantik
- 💬 **Merangkai** pipeline RAG lengkap hingga LLM menghasilkan jawaban berbasis konteks

---

## 🛠️ Teknologi yang Digunakan

| Komponen | Library / Model |
|---|---|
| Framework RAG | [LangChain](https://www.langchain.com/) |
| Text Splitting | `langchain-text-splitters` · `RecursiveCharacterTextSplitter` |
| Embedding Model | `sentence-transformers/distiluse-base-multilingual-cased-v1` (~480 MB) |
| Vector Store | [FAISS](https://github.com/facebookresearch/faiss) (`faiss-cpu`) |
| LLM (Opsional) | [Groq](https://console.groq.com) via `langchain-groq` |
| Bahasa | Python 3 |
| Platform | Google Colab (CPU gratis sudah cukup) |

---

## 🚀 Cara Menjalankan

### 1. Buka di Google Colab

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

Upload file `.ipynb` ke Google Colab atau buka langsung dari GitHub.

### 2. Jalankan Sel Secara Berurutan

> ⚠️ **Penting:** Jalankan setiap sel **dari atas ke bawah**. Melewati sel adalah penyebab paling umum munculnya error `NameError`.

| # | Sel | Keterangan |
|---|---|---|
| 1 | Instalasi | Pasang semua dependensi (`langchain`, `faiss-cpu`, dll.) |
| 2 | Verifikasi | Pastikan semua pustaka berhasil di-import |
| 3 | Knowledge Base | Siapkan dokumen contoh berbahasa Indonesia |
| 4 | Chunking | Potong dokumen menjadi fragmen-fragmen kecil |
| 5 | Embedding | Ubah teks menjadi vektor 512 dimensi |
| 6 | FAISS Index | Bangun indeks vektor untuk pencarian cepat |
| 7 | Semantic Search | Cari potongan paling relevan dengan pertanyaan |
| 8 *(opsional)* | Generation | Susun jawaban menggunakan LLM via Groq API |

### 3. (Opsional) API Key Groq untuk Langkah Generation

Langkah 1–5 berjalan **tanpa API key**. Untuk Langkah 6 (generation), daftarkan akun gratis di [console.groq.com](https://console.groq.com) dan masukkan API key saat diminta.

---

## 📋 Prasyarat

- Akun Google (untuk Google Colab)
- Koneksi internet (untuk mengunduh model ~480 MB di pertama kali)
- API key Groq **(opsional, hanya untuk Langkah Generation)**

---

## ⚠️ Troubleshooting

| Gejala / Error | Solusi |
|---|---|
| `ModuleNotFoundError` setelah `%pip install` | **Runtime → Restart session**, lalu jalankan ulang dari atas |
| `NameError: ... is not defined` | Ada sel yang terlewat. Jalankan ulang dari sel pertama secara berurutan |
| Proses "menggantung" di Langkah Embedding | Normal — model 480 MB sedang diunduh. Tunggu hingga selesai |
| `AuthenticationError` / `401` | API key Groq salah atau kosong. Buat key baru di [console.groq.com](https://console.groq.com) |
| `model_decommissioned` | Nama model Groq berubah. Cek model aktif di [console.groq.com/docs/models](https://console.groq.com/docs/models) |
| `numpy` / `faiss` error saat import | **Runtime → Restart session**, lalu jalankan ulang sel instalasi |

---

## 📝 Tugas Praktikum

Notebook ini mencakup **3 soal evaluasi**:

1. **Soal 1** — Eksperimen `chunk_size=50` dan analisis dampak pemotongan terlalu pendek terhadap keutuhan makna
2. **Soal 2** — Uji pertanyaan di luar topik dokumen dan analisis risiko output FAISS yang tidak relevan
3. **Soal 3** — Perbandingan prompt *dengan* vs *tanpa* konteks untuk melihat peran retrieval dalam menekan halusinasi LLM

---

## 📚 Referensi

- [LangChain Documentation](https://python.langchain.com/)
- [Sentence Transformers — Multilingual Models](https://www.sbert.net/docs/sentence_transformer/pretrained_models.html)
- [FAISS — Facebook AI Similarity Search](https://github.com/facebookresearch/faiss)
- [Groq Console & API Docs](https://console.groq.com/docs)

---

> **Catatan:** Dokumen yang digunakan sebagai basis pengetahuan dalam praktikum ini bersifat **fiktif** dan hanya untuk keperluan latihan.

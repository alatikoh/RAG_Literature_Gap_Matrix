# RAG Literature GAP Matrix — Face Recognition

Pipeline RAG untuk menganalisis 10 artikel Face Recognition dan menghasilkan Literature GAP Matrix 8 kolom.

## Cara menjalankan
1. Buka `RAG_Literature_Gap_Matrix_Full_Colab.ipynb` di Google Colab.
2. Jalankan sel instalasi dan hubungkan Google Drive.
3. Masukkan PDF P01.pdf ... P10.pdf ke `MyDrive/RAG-Literature-Gap-Matrix/articles/`.
4. Jalankan document processing, chunking, embedding, retrieval.
5. Simpan `GROQ_API_KEY` di Colab Secrets; uji 1 paper, lalu proses seluruhnya.
6. Ekspor `outputs/gap_matrix.csv` dan periksa bukti dari `outputs/evidence.csv`.
7. Verifikasi jawaban secara manual dengan artikel asli.

## Model dan pendekatan
- Embedding: sentence-transformers/paraphrase-multilingual-mpnet-base-v2 (768 dimensi).
- Vector store: file NumPy lokal di runtime/Google Drive dan semantic retrieval cosine similarity.
- LLM generasi: qwen/qwen3.8-27b lewat Groq API.
- Struktur matrix: Paper, DOI, Problem, Metode, Dataset, Temuan, Keterbatasan, Future Work.

## Batasan
Ekstraksi PDF dua kolom/gambar dapat tidak akurat, retrieval bisa melewatkan informasi penting,
dan keluaran LLM harus diverifikasi manusia. Halaman merujuk urutan halaman PDF.

## Keamanan
API key tidak pernah dimasukkan ke notebook/commit GitHub. PDF sumber diunggah secara terpisah
ke Drive pribadi; unggah ke repository hanya bila Anda punya hak untuk mendistribusikannya.

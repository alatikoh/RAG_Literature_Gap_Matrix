# Draft Research Gap — Perlu Verifikasi Manusia

# Laporan Sintesis Awal: Sistem Absensi Berbasis Pengenalan Wajah

> **Catatan:**  
> Hasil ini merupakan *sintesis awal* dari keluaran AI dan belum tentu akurat.  
> Verifikasi manual diharapkan sebelum dipakai untuk keputusan ilmiah atau praktis.

---

## 1. Pola Metode yang Sering Dipakai

| ID Paper | Metode Utama | Karakteristik |
|----------|--------------|---------------|
| **P01** | CNN berbasis **MobileFaceNet** + model lain (transfer learning) | Fokus pada deteksi liveness, training pada CelebA‑Spoof & NUAA‑Imposter |
| **P02** | **LBPH** (Local Binary Patterns Histograms) | Algoritma klasik, low‑cost, penurunan fitur 160k ➜ 6k |
| **P03** | Haar‑cascade + **AdaBoost** (OpenCV) | Implementasi di Raspberry Pi, GUI sederhana |
| **P04** | OpenCV + **Dlib** + toleransi adaptif Euclidean | Serialisasi gambar ke SQLite, pilot lab |
| **P05** | Tiny‑ViT (LaED) + fusi keputusan + audit keadilan | Lightweight, explainable, multi‑serangan (spoof, deepfake) |
| **P06** | CNN ringan + kamera termal | Multi‑modal: wajah + suhu |
| **P07** | Survei kuantitatif + TAM | Tidak berbasis sistem, fokus pada penerimaan pengguna |
| **P08** | Deep‑face recognition (CNN) + sampling + ROI | Studi kasus FPT Poly, data batch |

**Observasi:**  
- **CNN (Lightweight)** menjadi pilihan utama untuk deteksi liveness/spoofing (P01, P05, P06).  
- **Algoritma tradisional** (LBPH, Haar‑cascade, Dlib) masih dipakai di lingkungan resource‑constraint (P02–P04).  
- **Multi‑modal** (wajah + suhu) muncul di P06.  
- **Toleransi adaptif** dan *serialisasi* data lebih jarang (P04).  
- **Explainable AI** dan audit keadilan menjadi tema baru di P05.

---

## 2. Perbedaan Dataset / Evaluasi

| ID | Dataset Utama | Jumlah/Distribusi | Metode Evaluasi | Hasil Kunci |
|----|---------------|-------------------|-----------------|-------------|
| P01 | CelebA‑Spoof (70k) + NUAA‑Imposter (5k) | 70k, 5k | EER, HTER, F1 | HTER 0.13% (CelebA) |
| P02 | 30–500 gambar per 6 k fitur | 6k fitur | Akurasi (unspecified metric) | Akurasi tinggi |
| P03 | 12 partisipan (8P/4W) | 12 | Akurasi (unspecified) | Kinerja “cukup baik” |
| P04 | Tidak dilaporkan | - | Akurasi (unspecified) | Peningkatan via toleransi adaptif |
| P05 | CASIA‑FASD, DFDC, FairFace, LFW, + 10 k StyleGAN3, + in‑house | Banyak | Akurasi, fairness rating, explainability | Akurasi tinggi, rating 4.2/5 |
| P06 | CASIA‑WebFace (masked), LFW, MFR2 | 17 orang real‑world | Akurasi (mask/non‑mask) | 94.1% mask, 91.8% non‑mask |
| P07 | Survey 161 mahasiswa | 161 responden | TAM model (fit) | N/A (keterbatasan tidak dilaporkan) |
| P08 | 120 mahasiswa ×9 gambar + 7,490 gambar uji | 120, 7,490 | Akurasi (unspecified) | “Bekerja dengan baik” |

**Catatan:**
- Beberapa paper tidak menyebutkan
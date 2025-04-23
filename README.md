# 🔬 Autoencoder for COVID-19 Image Denoising and Sharpening

Proyek ini mengimplementasikan sebuah *Convolutional Autoencoder* sederhana menggunakan PyTorch untuk memproses dataset gambar COVID-19. Autoencoder digunakan untuk mengkompres dan merekonstruksi gambar, diikuti dengan *sharpening* untuk meningkatkan kualitas hasil rekonstruksi.

---

## 📁 Struktur Proyek

```
.
├── frames/               # Folder hasil ekstraksi dataset (semua gambar disatukan di sini)
├── results/              # Folder hasil output gambar input/output dan grafik metrik
│   ├── input_epochX_imgY.png
│   ├── output_epochX_imgY.png
│   └── metrics.png
├── main.py               # File utama script pelatihan Autoencoder
└── README.md             # Dokumentasi proyek
```

---

## 📦 Dependensi

Instal semua dependensi yang diperlukan dengan:

```bash
pip install torch torchvision matplotlib kagglehub pillow
```

---

## 📂 Dataset

Dataset diambil dari Kaggle melalui [COVID-19 Image Dataset](https://www.kaggle.com/datasets/pranavraikokte/covid19-image-dataset). Unduhan dilakukan secara otomatis menggunakan `kagglehub`.

---

## 🧠 Arsitektur Model

Model ini merupakan autoencoder konvolusional yang terdiri dari dua bagian:

- **Encoder:** 3 lapisan `Conv2D` dengan `ReLU` dan downsampling menggunakan stride 2.
- **Decoder:** 3 lapisan `ConvTranspose2D` dengan `ReLU`, dan lapisan akhir `Sigmoid` untuk membatasi output antara 0-1.

---

## 🔍 Fungsi Tambahan

### PSNR (Peak Signal-to-Noise Ratio)

Digunakan untuk mengevaluasi kualitas rekonstruksi gambar. Semakin tinggi nilai PSNR, semakin baik kualitas hasil rekonstruksi.

### Sharpening

Setelah proses rekonstruksi oleh autoencoder, hasil gambar ditingkatkan dengan menerapkan kernel sharpening menggunakan `conv2d`.

---

## 🚀 Cara Menjalankan

1. Jalankan script utama:
   ```bash
   python main.py
   ```

2. Setelah pelatihan selesai, hasil berikut akan tersedia:
   - Gambar input dan output dari setiap epoch (`results/`)
   - Grafik metrik `Loss` dan `PSNR` (`results/metrics.png`)
   - Visualisasi perbandingan gambar input vs output pada akhir pelatihan

---

## 🏋️‍♀️ Training

Training dilakukan selama **5 epoch** dengan **batch size = 16**, menggunakan:
- Loss function: `MSELoss`
- Optimizer: `Adam` (learning rate = 1e-3)

---

## 📈 Visualisasi Hasil

Setelah training selesai, Anda dapat melihat perbandingan antara gambar input dan hasil keluaran (rekonstruksi yang sudah di-*sharpen*) serta grafik metrik `Loss` dan `PSNR` yang menunjukkan performa pelatihan dari waktu ke waktu.

Contoh:
![Training Metrics](results/metrics.png)

---

## ⚠️ Catatan

- Gambar hanya dimuat dari file `.jpg`, jadi pastikan dataset mengandung format tersebut.
- Script akan membuat folder `frames` dan `results` secara otomatis jika belum ada.

---

## 📬 Kontak

Jika Anda memiliki pertanyaan atau masukan, silakan hubungi melalui GitHub atau email.

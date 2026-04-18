# 🩸🔍📸 Blood Cell Detection (RBC, WBC, Platelets)

Proyek ini mengembangkan model _object detection_ untuk mendeteksi dan menghitung jumlah sel darah:

- **Red Blood Cells (RBC) -- Sel Darah Merah**
- **White Blood Cells (WBC) -- Sel Darah Putih**
- **Platelets -- Trombosit**

Model dibangun menggunakan arsitektur berbasis **YOLO (Ultralytics)** dan dilatih menggunakan dataset **Complete Blood Count (CBC)**.

---

## Struktur Project

```
├── dataset/                   # Original Dataset (Folder + ZIP), Processed Dataset (yolo_dataset)
├── notebooks/                 # Notebook eksperimen
│   ├── AoL_DL_1_Train.ipynb   # Output cell training semua dihapus karena terlalu besar sebelum dihapus 150MB
│   ├── AoL_DL_1_DataPreprocessing.ipynb
│   ├── AoL_DL_1_Testing.ipynb
│   └── AoL_DL_1_Train.ipynb
├── configs/                   # File konfigurasi (untuk YOLO)
│   └── wbc.yaml
├── outputs/                   # Hasil training & evaluasi
│   ├── runs/                  # Output training YOLO (tidak bisa dimasukan GitHub)
│   └── robustness_result/     # Hasil uji robustness
├── assets/                    # Contoh gambar untuk inference
│   ├── test.jpg
│   └── test2.jpg
├── comparison/                # Log eksperimen
│   └── comparison_experiment_log.xlsx
├── requirements.txt           # Library beserta versinya
├── README.md
└── .gitignore                 # Mengontrol biar tidak ada runs yang masuk (file besar)
```

---

## ⚙️ Setup Environment

### 1. Clone Repository

```bash
git clone https://github.com/s1pitz/AoL_DeepLearning_1.git
cd AoL_DeepLearning_1
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

Disarankan menggunakan:

- Python ≥ 3.9
- GPU (CUDA) untuk performa optimal

---

## 📊 Dataset

Dataset yang digunakan adalah **Complete Blood Count (CBC Dataset)**.

Sumber dataset: https://www.kaggle.com/datasets/orvile/complete-blood-count-cbc-dataset

```
dataset/
```

Struktur dataset harus sesuai format YOLO:

```
dataset/
└── yolo_dataset/
    ├── images/
    │   ├── train/
    │   ├── val/
    │   └── test/
    └── labels/
        ├── train/
        ├── val/
        └── test/
```

---

## 🚀 Training Model

Training dilakukan melalui notebook:

```
notebooks/AoL_DL_1_Train.ipynb
```

Konfigurasi dataset menggunakan:

```
configs/wbc.yaml
```

Hasil training akan disimpan pada:

```
outputs/runs/
```

---

## 🔍 Inference

Untuk melakukan deteksi pada gambar:

```
notebooks/AoL_DL_1_Inference.ipynb
```

Contoh gambar tersedia pada:

```
assets/
```

Output berupa:

- Bounding box
- Label kelas (RBC, WBC, Platelets)
- Confidence score

---

## 📈 Evaluasi Model

Evaluasi dilakukan menggunakan:

- **mAP@50**
- **mAP@50-95**
- **Precision**
- **Recall**

Validasi Hasil Percobaan dilakukan melalui:

```
notebooks/AoL_DL_1_Testing.ipynb
```

---

## Evaluasi Performa (FPS)

Performa model diukur menggunakan **Frames Per Second (FPS)** dengan metode berikut:

- Dilakukan warmup untuk menstabilkan GPU
- Menggunakan beberapa iterasi untuk mengurangi noise
- Menggunakan `torch.cuda.synchronize()` untuk akurasi timing

---

## Robustness Testing

Pengujian robustness dilakukan untuk mengevaluasi ketahanan model terhadap variasi input (misalnya perubahan pencahayaan atau noise).

Hasil disimpan pada:

```
outputs/robustness_result/
```

---

## Eksperimen & Perbandingan

Log eksperimen dan perbandingan model tersedia pada:

```
comparison/comparison_experiment_log.xlsx
```

---

## Reproducibility

Untuk memastikan hasil dapat direproduksi:

- Gunakan `requirements.txt`
- Gunakan dataset yang sama
- Gunakan konfigurasi `configs/wbc.yaml`
- Jalankan notebook dengan memastikan semua directory path benar

---

## Catatan

- Folder `outputs/runs` tidak disertakan untuk menjaga ukuran repository
- Notebook Train telah dibersihkan dari output
- File model (`.pt`) tidak disertakan

---

## 👨‍💻 Author

Nama: Richard Arthur

---

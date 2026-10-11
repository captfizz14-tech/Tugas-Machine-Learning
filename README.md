# 📊 Proyek Machine Learning: Prediksi Skor Produktivitas Mahasiswa

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Data-Pandas%20%7C%20Numpy-150458?logo=pandas)
![Status](https://img.shields.io/badge/Status-Completed-success)

Repository ini berisi implementasi pipeline **Machine Learning end-to-end** untuk memprediksi skor produktivitas mahasiswa (`productivity_score`) berdasarkan kebiasaan belajar, penggunaan gawai/media sosial, durasi tidur, dan faktor distraksi digital.

Proyek ini disusun untuk memenuhi tugas praktikum mata kuliah **Machine Learning** yang diampu oleh **Bapak Asep**.

---

## 👤 Identitas Praktikan
* **Nama** : Muhamad Hafizd Fahreza
* **Mata Kuliah** : Machine Learning
* **Dosen Pengampu** : Asep Erlan Maulana S.kom.,M.kom

---

## 📁 Ringkasan Dataset
* **Nama File** : `student_productivity_distraction_dataset_20000.csv`
* **Jumlah Sampel** : 20.000 baris (memenuhi syarat minimal 1.000 baris)
* **Jumlah Fitur** : 18 kolom
* **Jenis Masalah** : Supervised Learning - **Regresi** (karena kolom target bernilai kontinu/numerik)
* **Target Feature** : `productivity_score` (Skor produktivitas belajar mahasiswa)

### Deskripsi Fitur Utama
| Fitur | Tipe Data | Deskripsi |
| :--- | :--- | :--- |
| `study_hours_per_day` | Numerik | Rata-rata jam belajar mandiri per hari |
| `sleep_hours` | Numerik | Rata-rata jam tidur per hari |
| `phone_usage_hours` | Numerik | Waktu penggunaan ponsel per hari (jam) |
| `social_media_hours` | Numerik | Durasi bermain media sosial per hari (jam) |
| `gaming_hours` | Numerik | Durasi bermain game per hari (jam) |
| `focus_score` | Numerik | Tingkat fokus mahasiswa (skor terukur) |
| `final_grade` | Numerik | Nilai akhir akademik mahasiswa |
| `stress_level` | Numerik / Kategorikal | Tingkat stres yang dialami |
| `productivity_score` | Numerik | **(Target)** Skor produktivitas mahasiswa |

---

## ⚙️ Tahapan Pipeline Machine Learning
Pipeline yang diterapkan mengikuti materi praktikum lab dari pertemuan awal hingga data modeling:

1. **Import Library**  
   Menggunakan `pandas`, `numpy`, `matplotlib`, `seaborn`, serta modul-modul utama dari `scikit-learn`.
2. **Data Loading & Inspection**  
   Membaca dataset CSV dan memeriksa ringkasan data (`shape`, `info()`, `describe()`, `dtypes`).
3. **Data Cleaning**  
   Pengecekan missing values (`isnull().sum()`), deteksi serta penanganan duplikasi data.
4. **Exploratory Data Analysis (EDA)**  
   - Visualisasi distribusi kolom target (`productivity_score`) menggunakan histogram & KDE.  
   - Visualisasi distribusi fitur-fitur numerik utama.  
   - Analisis korelasi fitur terhadap target menggunakan **Heatmap Korelasi**.
5. **Data Preprocessing & Transformation**  
   - Memisahkan data menjadi Fitur (`X`) dan Target (`y`), serta menghapus identifier non-prediktif (`student_id`).  
   - Membangun `ColumnTransformer` dan `Pipeline`:
     - *Fitur Numerik*: Penanganan nilai kosong dengan median (`SimpleImputer`) dan standardisasi skala (`StandardScaler`).
     - *Fitur Kategorikal*: Penanganan nilai kosong dengan modus (`SimpleImputer`) dan encoding kategori (`OneHotEncoder`).
6. **Data Splitting**  
   Pembagian data menjadi **Training Set (80%)** dan **Testing Set (20%)** menggunakan `train_test_split` dengan `random_state` tetap agar hasil dapat direproduksi (*reproducible*).
7. **Model Building & Training**  
   Melatih 3 algoritma regresi:
   - **Linear Regression** (Baseline model)
   - **Decision Tree Regressor**
   - **Random Forest Regressor** (Ensemble learning)
8. **Evaluasi & Perbandingan Model**  
   Menggunakan tiga metrik evaluasi standar regresi:
   - **MAE** (*Mean Absolute Error*)
   - **RMSE** (*Root Mean Squared Error*)
   - **R² Score** (*Coefficient of Determination*)

---

## 📈 Hasil Evaluasi Model

Berdasarkan pengujian pada data testing (20% dari total data), berikut adalah perbandingan performa masing-masing model:

| Model | MAE | RMSE | R² Score |
| :--- | :---: | :---: | :---: |
| **Linear Regression** | **0.0025** | **0.0029** | **1.0000** |
| **Random Forest Regressor** | 2.0005 | 2.5367 | 0.9750 |
| **Decision Tree Regressor** | 4.0246 | 5.0145 | 0.9024 |

> **Catatan Analisis:**  
> Seluruh model menunjukkan performa prediksi yang sangat tinggi. Linear Regression memberikan tingkat galat (*error*) terendah pada dataset ini. Namun, Random Forest juga menunjukkan generalisasi yang sangat stabil dengan R² sebesar 0.9750.

---

## 📂 Struktur Repositori

```text
Machine-Learning-Productivity/
├── Prediksi_Produktivitas_Mahasiswa.ipynb       # Jupyter Notebook lengkap + output & visualisasi
├── student_productivity_distraction_dataset_20000.csv  # Dataset utama (> 1000 baris)
├── requirements.txt                            # Daftar library/dependensi Python
├── README.md                                   # Dokumentasi lengkap proyek untuk GitHub
├── .gitignore                                  # Mengabaikan file cache & checkpoint
└── Draft_Laporan_Machine_Learning.docx          # Format draft laporan praktikum untuk aslab
```

---

## 🚀 Cara Menjalankan di Lokal

### 1. Clone Repositori
```bash
git clone https://github.com/<username-kamu>/Machine-Learning-Productivity.git
cd Machine-Learning-Productivity
```

### 2. Buat & Aktifkan Virtual Environment (Opsional)
```bash
python -m venv venv
# Windows:
venv\Scripts\activate
# Linux/macOS:
source venv/bin/activate
```

### 3. Install Dependensi
```bash
pip install -r requirements.txt
```

### 4. Jalankan Jupyter Notebook
```bash
jupyter notebook
```
Buka file `Prediksi_Produktivitas_Mahasiswa.ipynb` dan jalankan setiap *cell* secara berurutan (*Run All*).

---

## 📤 Panduan Upload / Push ke GitHub

Untuk mengunggah proyek ini ke repositori GitHub pribadi:

1. Buka [GitHub](https://github.com/) dan buat repositori baru (misal: `machine-learning-productivity`).
2. Buka terminal/PowerShell di folder proyek ini:
   ```powershell
   git init
   git add .
   git commit -m "feat: complete end-to-end machine learning pipeline and documentation"
   git branch -M main
   git remote add origin https://github.com/<username-kamu>/machine-learning-productivity.git
   git push -u origin main
   ```
3. Link repositori GitHub dapat disalin dan dilampirkan pada form pengumpulan tugas untuk Asisten Lab dan Dosen.

---
*Dibuat untuk Praktikum Machine Learning 2026.*

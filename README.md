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
* **Nim**  : 21011400698
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
> Seluruh model menunjukkan performa prediksi yang sangat tinggi. Linear Regression memberikan tingkat galat (*error*) terendah pada dataset ini (mendekati 0), yang mengindikasikan fitur input memiliki korelasi linear yang sangat teratur terhadap target. Model ensemble seperti Random Forest juga menghasilkan akurasi yang luar biasa dengan R² sebesar 0.9750.

---

## 🎯 Kesimpulan & Insight Proyek

Berdasarkan keseluruhan proses eksperimen Machine Learning mulai dari pemrosesan awal data hingga tahap evaluasi, dapat ditarik beberapa kesimpulan utama:

1. **Efektivitas Pipeline Data:**  
   Penerapan `ColumnTransformer` dan `Pipeline` dari Scikit-Learn sangat membantu menciptakan alur pemrosesan data yang terstruktur, otomatis, dan terbebas dari kebocoran data (*data leakage*) antara data *training* dan *testing*.

2. **Performa Algoritma Terbaik:**  
   Dari ketiga model yang diuji, **Linear Regression** menghasilkan nilai evaluasi terbaik dengan tingkat galat terendah (**MAE = 0.0025**, **RMSE = 0.0029**) dan koefisien determinasi sempurna (**R² = 1.0000**). Hal ini menunjukkan bahwa target `productivity_score` pada dataset ini memiliki relasi linear langsung yang sangat kuat dengan kombinasi fitur input.

3. **Kemampuan Model Ensemble:**  
   Model **Random Forest Regressor** juga membuktikan kinerja yang sangat baik dengan **R² = 0.9750** dan **RMSE = 2.5367**. Model ini menunjukkan kestabilan tinggi dalam menangani variasi data kompleks tanpa mengalami *overfitting*.

4. **Insight Faktor Produktivitas Mahasiswa:**  
   - **Faktor Pendorong:** Fitur jam belajar mandiri (`study_hours_per_day`) dan tingkat fokus (`focus_score`) merupakan prediktor paling signifikan yang berkontribusi positif terhadap tingginya skor produktivitas.  
   - **Faktor Penghambat:** Penggunaan gawai berlebih (`phone_usage_hours`) dan durasi media sosial (`social_media_hours`) memiliki korelasi negatif terhadap produktivitas, mempertegas pentingnya pengelolaan distraksi digital selama masa perkuliahan.  
   - **Faktor Penyeimbang:** Kebutuhan istirahat yang cukup (`sleep_hours`) berperan penting dalam menjaga stabilitas stamina dan konsentrasi belajar mahasiswa.

---
*Dibuat oleh Muhamad Hafizd Fahreza (21011400698) untuk Praktikum Machine Learning 2026.*



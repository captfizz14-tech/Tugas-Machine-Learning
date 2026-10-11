# Prediksi Skor Produktivitas Mahasiswa

## Deskripsi
Proyek ini menerapkan alur kerja Machine Learning untuk memprediksi `productivity_score` menggunakan dataset kebiasaan belajar dan distraksi digital mahasiswa.

## Dataset
- File: `student_productivity_distraction_dataset_20000.csv`
- Jumlah awal: 20.000 baris dan 18 kolom
- Target: `productivity_score`
- Kolom `student_id` dikeluarkan dari fitur karena merupakan identitas.

Cantumkan sumber asli dan lisensi dataset apabila tersedia. Jangan unggah data yang mengandung informasi pribadi sensitif.

## Tahapan
1. Data loading dan pengenalan data
2. Data cleaning
3. Exploratory Data Analysis (EDA)
4. Data processing dan encoding
5. Train-test split (80:20)
6. Modeling: Linear Regression, Decision Tree Regressor, Random Forest Regressor
7. Evaluasi menggunakan MAE, RMSE, dan R²

## Cara menjalankan
1. Simpan notebook dan CSV di folder yang sama.
2. Instal dependensi:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn notebook
   ```
3. Jalankan:
   ```bash
   jupyter notebook
   ```
4. Buka `Produktivitas_Mahasiswa.ipynb` dan jalankan sel dari atas ke bawah.

## Catatan hasil
Pada satu pembagian data testing, Linear Regression menunjukkan skor yang hampir sempurna. Periksa definisi `productivity_score` dan kemungkinan target leakage sebelum membuat klaim performa akhir. Hasil yang sangat baik pada satu split tidak menjamin performa pada data baru.

## Struktur repository yang disarankan
```text
machine-learning-productivity/
├── Produktivitas_Mahasiswa.ipynb
├── student_productivity_distraction_dataset_20000.csv
├── Laporan_Machine_Learning.docx
├── README.md
└── requirements.txt
```

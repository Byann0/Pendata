# Laporan Analisis Klasifikasi Prediksi Pendapatan (Dataset Adult)

Laporan ini menyajikan analisis lengkap mengenai eksperimen machine learning yang dilakukan menggunakan software Orange3 untuk memprediksi kategori pendapatan (income) berdasarkan data demografis.

## 1. Ringkasan Dataset
Dataset yang digunakan adalah **adult.csv** (sering disebut sebagai dataset 'Census Income').
- **Target Variabel**: `income` (dua kategori: `<=50K` dan `>50K`).
- **Fitur Utama**: Umur, status pekerjaan, pendidikan, status perkawinan, pekerjaan, ras, jenis kelamin, keuntungan/kerugian modal, dan jam kerja per minggu.

## 2. Alur Kerja (Workflow) Orange3
Berdasarkan tangkapan layar workflow, proses dilakukan sebagai berikut:
1. **File**: Memuat dataset `adult.csv`.
2. **Data Sampler**: Membagi data menjadi data latih (training) dan data uji (testing).
3. **Model Klasifikasi**: Dua algoritma digunakan untuk perbandingan:
   - **Random Forest**: Algoritma berbasis ensemble tree.
   - **Naive Bayes**: Algoritma probabilitas berbasis teorema Bayes.
4. **Test and Score**: Mengevaluasi kinerja model menggunakan data uji.
5. **Confusion Matrix**: Visualisasi detail kesalahan prediksi model.

## 3. Parameter Model
- **Random Forest**: Menggunakan 10 pohon (trees) dengan opsi "Do not split subsets smaller than 5" dan "Limit maximal tree depth to 10" (seperti terlihat pada `rfl.png`).
- **Naive Bayes**: Menggunakan pengaturan standar Orange3.

## 4. Analisis Hasil Evaluasi (Test and Score)
Berdasarkan file `hasil_te.png`, berikut adalah perbandingan performa kedua model:

| Model | AUC | Classification Accuracy (CA) | F1 Score | Precision | Recall |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Random Forest** | **0.903** | **0.852** | **0.849** | **0.847** | **0.852** |
| **Naive Bayes** | 0.892 | 0.825 | 0.829 | 0.838 | 0.825 |

### Analisis Metrik:
- **AUC (Area Under ROC Curve)**: Random Forest (0.903) sedikit lebih unggul dari Naive Bayes (0.892). Hal ini menunjukkan kemampuan pemisahan kelas yang lebih baik pada Random Forest.
- **CA (Akurasi)**: Random Forest mencapai 85,2%, yang berarti 85% data diprediksi dengan benar secara keseluruhan.
- **F1 Score**: Random Forest (0.849) lebih stabil dibandingkan Naive Bayes (0.829) dalam menangani ketidakseimbangan kelas.

## 5. Analisis Confusion Matrix
### A. Random Forest (`cm_scorer.png`)
- **True Negative (<=50K)**: 6861 (Berhasil memprediksi pendapatan rendah dengan sangat baik).
- **True Positive (>50K)**: 1461.
- **Kesalahan (Misclassification)**: Terjadi lebih banyak pada kelas `>50K` yang diprediksi sebagai `<=50K` (893 kasus).

### B. Naive Bayes (`cm_scorer_nb.png`)
- **True Negative (<=50K)**: 6092.
- **True Positive (>50K)**: 1964.
- **Keunikan**: Naive Bayes jauh lebih baik dalam mendeteksi orang dengan pendapatan `>50K` (Recall lebih tinggi untuk kelas positif), namun memiliki tingkat **False Positive** yang tinggi (1322 orang berpendapatan rendah diprediksi sebagai pendapatan tinggi).

## 6. Kesimpulan
1. **Random Forest** adalah model yang lebih baik secara keseluruhan jika dilihat dari metrik Akurasi (CA) dan AUC. Model ini lebih presisi dan memiliki tingkat kesalahan yang lebih rendah secara total.
2. **Naive Bayes** cenderung lebih "berani" dalam memprediksi kelas `>50K`. Jika tujuan bisnis adalah untuk tidak melewatkan potensi orang berpendapatan tinggi (meminimalkan False Negative pada kelas >50K), maka Naive Bayes bisa dipertimbangkan meskipun akurasi totalnya lebih rendah.
3. Untuk dataset ini, **Random Forest** direkomendasikan karena memberikan keseimbangan yang lebih baik antara presisi dan recall.

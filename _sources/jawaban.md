# Laporan Analisis Klasifikasi Kesuburan Tanah

## 1. Pemrosesan Data (Data Preprocessing)

Tahap ini bertujuan untuk membersihkan dan menyiapkan dataset mentah agar dapat diproses secara optimal oleh algoritma. Berdasarkan data asli sebanyak 2.000 baris, berikut adalah langkah-langkah yang dilakukan:

- Pembersihan Data Kosong (Node: Missing Value): Dataset awal memiliki banyak data kosong (seperti pada kolom N Total, P Tersedia, dan C Organik). Proses imputasi dilakukan dengan menggunakan metode Median untuk kolom numerik (Float) guna menghindari pengaruh nilai ekstrem, serta Most Frequent Value untuk kolom teks (String). Hasilnya, seluruh missing values berhasil dihilangkan (menjadi 0).

- Transformasi Data Kategorikal (Node: One to Many): Fitur "Tekstur Tanah" yang bersifat teks diubah menjadi data biner (0 dan 1) menggunakan teknik One-Hot Encoding. Fitur ini dipecah menjadi 6 kolom baru (Debu, Lempung, Pasir, Liat, dll) agar algoritma dapat menghitung jarak matematisnya.

- Penyamaan Skala Data (Node: Normalizer): Dilakukan normalisasi menggunakan metode Min-Max untuk menyamakan rentang nilai seluruh fitur ke skala 0.0 hingga 1.0. Hal ini penting agar fitur dengan angka besar (seperti P Tersedia) tidak mendominasi fitur dengan angka kecil (seperti pH) dalam perhitungan jarak.

## 2. Analisis K-Nearest Neighbors (KNN)

Setelah data bersih dan terstandarisasi, dilakukan analisis klasifikasi untuk menentukan tingkat kesuburan tanah:

- Penerapan Model: Algoritma KNN digunakan untuk memprediksi label "Subur" atau "Tidak Subur".

- Mekanisme Kerja: Model bekerja dengan mencari tetangga terdekat ($k$) berdasarkan kedekatan fitur-fitur agronomis (pH, N, P, K, dll). Dalam analisis ini, model mengevaluasi seluruh sampel data (2.000 baris) untuk melihat performa klasifikasi secara menyeluruh.

## 3. Metrik Evaluasi

Evaluasi dilakukan dengan membandingkan nilai prediksi model terhadap label asli pada dataset. Berikut adalah hasil perhitungan metrik evaluasi yang diperoleh melalui node Scorer:

Tabel Metrik Evaluasi

|Metrik|Hasil Analisis|Keterangan|
|---|---|---|
|Accuracy|100%|Persentase prediksi benar dari total keseluruhan data.|
|Precision|1.00|Ketepatan model dalam memprediksi kelas positif (Subur).|
|Recall|1.00|Kemampuan model mendeteksi seluruh sampel kelas positif.|
|F1-Score|1.00|Keseimbangan antara Precision dan Recall (Harmonic Mean).|

Confusion Matrix
||Terprediksi: Tidak Subur|Terprediksi: Subur|
|Asli: Tidak Subur|1.000|0|
|Asli: Subur|0|1.000|

## Kesimpulan

Berdasarkan hasil di atas, model KNN mampu melakukan klasifikasi dengan sempurna tanpa adanya kesalahan prediksi (Zero Error). Hal ini menunjukkan bahwa fitur-fitur tanah yang digunakan memiliki pola yang sangat jelas untuk membedakan antara tanah yang subur dan tidak subur.

## Table Hasil perhitungannya

1. Csv Reader
![alt text](/gambaruts/datacsv.png)
2. Missing Value
![alt text](/gambaruts/missingvlue.png)
3. One to Many (untuk ubah katergorikal Tekstur tanah ke angka)
![alt text](/gambaruts/ubahangka.png)
4. Normalisasi (menggunakan min max)
![alt text](/gambaruts/normalisasi.png)
5. Knn
![alt text](/gambaruts/Knn.png)
6. Scorer
![alt text](/gambaruts/confussionmatrix.png)
7. Visualisai Workflow
![alt text](/gambaruts/overflow.png)

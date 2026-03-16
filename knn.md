# K-Nearest Neighbors (K-NN)

adalah algoritma klasifikasi yang sangat populer dalam
pembelajaran mesin, khususnya dalam kategori supervised learning. Algoritma ini pertama kali dikembangkan oleh Evelyn Fix dan Joseph Hodges pada tahun 1951. K-NN bekerja dengan cara mengklasifikasikan suatu data berdasarkan kedekatan jarak dengan data lain dalam kelompok tertentu.

## Prinsip Dasar KNN

adalah memanfaatkan jarak untuk menentukan kelompok atau kelas suatu data. Algoritma ini menghitung jarak antara data baru yang akan diklasifikasikan dengan data yang ada pada dataset, kemudian memilih sejumlah tetangga terdekat yang ditentukan oleh parameter kkk. Berdasarkan mayoritas kelas dari kkk tetangga tersebut, data baru diklasifikasikan.

## Euclidean Distance

Dua data, misalnya data $A$ dan data $B$ dengan koordinat $(x_1, y_1)$ dan $(x_2, y_2)$ dalam ruang dua dimensi, memiliki jarak Euclidean sebagai berikut:

$$d(A, B) = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$$

Prosedur Algoritma K-NN

1. Tentukan nilai $k$ (jumlah tetangga terdekat).
2. Hitung jarak antara data baru dengan seluruh data yang ada dalam dataset.
3. Urutkan data berdasarkan jarak terdekat.
4. Pilih $k$ data terdekat.
5. Tentukan kelas berdasarkan mayoritas kelas dari $k$ data tersebut.

## Jarak Manhattan

Menghitung jarak dalam ruang grid atau "kotak-kotak" seperti jalan-jalan di kota. Jarak Manhattan untuk dua titik $A$ dan $B$ adalah:

$$d(A, B) = \sum_{i=1}^{n} |x_i - y_i|$$

## Jarak Minkowski

Generalisasi dari jarak Euclidean dan Manhattan. Jika $p = 2$, hasilnya adalah jarak Euclidean; jika $p = 1$, hasilnya adalah jarak Manhattan.

$$d(A, B) = \left( \sum_{i=1}^{n} |x_i - y_i|^p \right)^{1/p}$$

## Jarak Chebyshev

Mengukur jarak maksimum di sepanjang satu dimensi koordinat. Sering digunakan dalam perhitungan untuk papan catur atau dalam kasus jarak tak terbatas.

$$d(A, B) = \max(|x_i - y_i|)$$

## Jarak Cosine

Digunakan untuk mengukur kesamaan antara dua vektor dalam ruang berdimensi tinggi. Dihitung berdasarkan sudut antara dua vektor, bukan panjang jarak absolut.

$$d(A, B) = 1 - \frac{\sum_{i=1}^{n} x_i y_i}{\sqrt{\sum_{i=1}^{n} x_i^2} \cdot \sqrt{\sum_{i=1}^{n} y_i^2}}$$

## Jarak Mahalanobis

Cocok untuk data dengan distribusi variabel berbeda. Jarak ini mempertimbangkan korelasi antara variabel.

$$d(A, B) = \sqrt{(X - Y)^T S^{-1} (X - Y)}$$

Di mana $S$ adalah matriks kovarians dari data.

## Prosedur Algoritma KNN

1. Tentukan nilai k (jumlah tetangga terdekat).
2. Hitung jarak antara data baru dengan seluruh data yang ada dalam dataset.
3. Urutkan data berdasarkan jarak terdekat.
4. Pilih k data terdekat.
5. Tentukan kelas berdasarkan mayoritas kelas dari k data tersebut.

## Kesimpulan

K-Nearest Neighbors (K-NN) adalah algoritma yang sederhana namun sangat efektif untuk klasifikasi. Dengan menggunakan jarak sebagai penentu kemiripan antar data, K-NN dapat digunakan dalam berbagai bidang, seperti pengenalan pola dan klasifikasi gambar. Namun, K-NN juga memiliki kelemahan dalam hal efisiensi jika jumlah data sangat besar, serta rentan terhadap outlier dan pemilihan nilai kkk yang kurang tepat.
Implementasi dalam Python juga cukup sederhana, dan dengan pemahaman mendalam tentang konsep K-NN, kita bisa mengaplikasikannya dalam berbagai kasus klasifikasi.

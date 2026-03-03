---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Mengukur Jarak

## Kesamaan dan Ketidaksamaan

Kesamaan 
- Mengukur secara numerik bagaimana kesamaan 2 objek
- Tinggi nilainya  bila benda yang lebih mirip
- Range [0,1]

Ketidaksamaan
- Ukuran numerik dari perbedaan dua objek
- Sangat rendah bila benda yang lebih mirip
- Minimum ketidaksamaan 0

## Data Matriks dan Ketidaksamaan Matriks

Data Matriks
- n titik data dengan p dimensi
- 2 Mode
![alt text](/gambar/Distance/image.png)

Ketidaksamaan Matriks
- n titik data yang didata adalah distance/jarak
- Matrik segitiga
- 1 Mode
![alt text](/gambar/Distance/image-1.png)

## Mengukur jarak untuk atribut nominal

- Misal terdapat 2 atau lebih nilai, misall red, yellow, blue, green(generalisasi dari atribut binary)
- Metode Simple Matching
![alt text](/gambar/Distance/image-2.png)

## Mengukur jarak untuk atribut Binary

- Tabel kontingensi untuk data biner
![alt text](/gambar/Distance/image-3.png)

- Mengukur jarak untuk variabel biner simetris
![alt text](/gambar/Distance/image-4.png)

- Mengukur jarak untuk variabel biner tidak simetris
![alt text](/gambar/Distance/image-5.png)

- Jaccard coefficient(Kesamaan mengukur variable tidak simetris biner)
![alt text](/gambar/Distance/image-6.png)

- Jaccard coefficient sama dengan "coherence":
![alt text](/gambar/Distance/image-7.png)

### Contoh

![alt text](/gambar/Distance/image-8.png)
- Jenis kelamin atribut simetris
- Atribut lain adalah tidak simetris biner
- Nilai Y dan P adalah 1, dan nilai N adalah 0 

![alt text](/gambar/Distance/image-9.png)
![alt text](/gambar/Distance/image-10.png)

## Atribut Ordinal

- Atribut ordinal dapat bernilai diskrit atau kontinu
- Mengandung urutan/tingkatan, misal ranking
- Dapat dinyatakan dengan type data interval-scaled
  - Gantikan x if dengan urutan rankingnya ![alt text](/gambar/Distance/image-11.png)
  - Petakan setiap nilai variable kedalam [0, 1] dengan menggantikan objek ke I dalam variable ke f dengan ![alt text](/gambar/Distance/image-12.png)
  - Hitung ketidaksamaan (disimilarity) dengan using method variable skala interval (numerik)

## Standarisasi data Numeric(normalisasi)

- Z-score: ![alt text](/gambar/Distance/image-13.png)
  - X: data yang akan dinormalissi, μ: mean , σ: standard deviation
- Cara lain : Menghitung mean absolute deviation

![alt text](/gambar/Distance/image-14.png) dengan

![alt text](/gambar/Distance/image-15.png)
  - Ukuran standarisasi dengan (z-score): 
  
  ![alt text](/gambar/Distance/image-16.png)
- Dengan menggunakan mean absolute deviation lebih handal daripada menggunakan standart deviation

### Contoh Data Matrik dan Ketidaksamaan Matrik

![alt text](/gambar/Distance/image-17.png)

- Data Matrik

![alt text](/gambar/Distance/image-18.png)

- Ketidaksamaan Matrik(with Ecludian Distance)

![alt text](/gambar/Distance/image-19.png)

## Jarak pada data Numerik : Minkowski Distance

- Minkowski :

![alt text](/gambar/Distance/image-20.png)

Dimana i= (xi1,xi2, ...,xip) dan j= (xj1,xj2, ...,xjp) dua objek dengan p dimensi data, dan h adalah pangkat (disebut juga dengan L-h norm)

- Sifatnya 
  - d(i, j) > 0 jika i ≠ j, dan d(i, i) = 0 (Positive definiteness)
  - d(i, j) = d(j, i)  (Symmetry)
  - d(i, j)  d(i, k) + d(k, j)  (Triangle Inequality)

## Special Cases of Minkowski Distance
- h = 1:  Manhattan (city block, L1 norm) distance 
  - Misal., the Hamming distance: Jumlah bit yang berbeda antara dua vektor biner

  ![alt text](/gambar/Distance/image-21.png)
- h = 2:  (L2 norm) Euclidean distance

![alt text](/gambar/Distance/image-22.png)
- h --> ∞  “supremum” (Lmax norm, L∞ norm) distance. 
  - Ini adalah selisih maksimum diantara atribut atributnyanya dalam suatu vektor
  
  ![alt text](/gambar/Distance/image-23.png)

### Contoh Minkowski Distance

![alt text](/gambar/Distance/image-24.png)
![alt text](/gambar/Distance/image-25.png)

Ketidaksamaan Matrik
- Manhattan (L1)
![alt text](/gambar/Distance/image-26.png)
- Ecludian (L2)
![alt text](/gambar/Distance/image-27.png)
- Supremum
![alt text](/gambar/Distance/image-28.png)

## Atribut Campuran

Database mungkin mengandung tipe campuran (semua tipe data ada (Nominal, symmetric binary, asymmetric binary, numeric, ordinal))
- Kita dapat menggunakan pembobotan untuk menggabungkan 
![alt text](/gambar/Distance/image.png)
  - f  adalah binary atau nominal: dij(f) = 0  if xif = xjf , atau j dij(f) = 1 untuk yang lainnya
  - Jika f  adalah numerik: gunakan normalisasi 
  - Jika f adalah ordinal
    - Hitung ranking rif dan
    - Cari zif sebagai skala interval

    ![alt text](/gambar/Distance/image-1.png)
  


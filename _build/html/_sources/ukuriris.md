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

# Ukur Jarak Data Iris

# Mengukur Jarak Iris

import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from scipy.spatial.distance import pdist, squareform
from sklearn.preprocessing import MinMaxScaler
df = pd.read_csv('IRIS.csv')

## Menampilkan 5 data teratas
print("Preview Data Iris:")
df.head()

## Menampilkan statistik deskriptif hanya untuk kolom numerik
deskriptif = df.describe()
print("Statistik Deskriptif Dataset Iris:")
display(deskriptif)

## Normalisasi Data
Karena fiturnya adalah numerik maka dilakukanlah normalisasi data dengan menggunakan min-max scaling untuk mengubah semua nilai ke dalam rentang 0 hingga 1

Memisahkan fitur (angka) dari label (spesies)
X = df.drop(columns=['species'])

Inisialisasi Scaler
scaler = MinMaxScaler()
X_norm = scaler.fit_transform(X)

Ubah kembali ke DataFrame untuk pengecekan
X_norm_df = pd.DataFrame(X_norm, columns=X.columns)
print("Data Setelah Normalisasi (5 Baris Pertama):")
X_norm_df.head()

## Menghitung Dissimilarity Matrix
* **Euclidean:** Jarak garis lurus (paling umum).
* **Manhattan:** Jumlah selisih absolut (jarak lintasan siku-siku).
* **Minkowski:** Generalisasi jarak dengan parameter $p$. Kita gunakan $p=3$.

1. Euclidean Distance
dist_euclidean = squareform(pdist(X_norm, metric='euclidean'))

2. Manhattan Distance
dist_manhattan = squareform(pdist(X_norm, metric='cityblock'))

3. Minkowski Distance (p=3)
dist_minkowski = squareform(pdist(X_norm, metric='minkowski', p=3))

Menampilkan matriks (10 data pertama)
def display_matrix(matrix, title):
    cols = [f'Data {i+1}' for i in range(10)]
    matrix_df = pd.DataFrame(matrix[:10, :10], columns=cols, index=cols)
    print(f"\n--- Matriks Jarak {title} (10x10) ---")
    display(matrix_df.round(3))

display_matrix(dist_euclidean, "Euclidean")
display_matrix(dist_manhattan, "Manhattan")
display_matrix(dist_minkowski, "Minkowski")

## Visualisasi Perbandingan Jarak
Warna yang semakin **gelap** menunjukkan jarak yang mendekati 0 (sangat mirip). 
Warna yang semakin **terang** menunjukkan perbedaan yang besar antar objek.

fig, axes = plt.subplots(1, 3, figsize=(22, 6))

1. Heatmap Euclidean
sns.heatmap(dist_euclidean[:15, :15], annot=True, cmap='YlGnBu', ax=axes[0])
axes[0].set_title('Euclidean Heatmap (15 Data)')

2. Heatmap Manhattan
sns.heatmap(dist_manhattan[:15, :15], annot=True, cmap='OrRd', ax=axes[1])
axes[1].set_title('Manhattan Heatmap (15 Data)')

3. Heatmap Minkowski
sns.heatmap(dist_minkowski[:15, :15], annot=True, cmap='Purples', ax=axes[2])
axes[2].set_title('Minkowski (p=3) Heatmap (15 Data)')

plt.show()
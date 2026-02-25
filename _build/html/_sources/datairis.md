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

# Data Iris Flower

## Eksplorasi Data Iris

**Dataset Iris** adalah dataset legendaris dalam dunia statistik dan machine learning yang diperkenalkan oleh Ronald Fisher pada tahun 1936. Eksplorasi data (EDA) adalah langkah awal untuk memahami "pola" dari data tersebut sebelum kita melakukan analisis yang lebih dalam.

- Jumlah Sampel: 150 baris (data bunga). Datanya seimbang, kalau tidak seimbang data bermasalah. Berikut datanya :

```{code-cell}
:tags: [hide-input]
import pandas as pd

df = pd.read_csv("IRIS.csv")
df.index = df.index + 1
df.head(150)
```

- Fitur (Variabel): Ada 4 fitur numerik dan 1 target kategori:
    1. sepal_length.
    2. sepal_width.
    3. petal_length.
    4. petal_width.
    5. species.
- Kualitas Data: tidak ada nilai yang kosong (missing values)

Data Iris Flower ini diambil dari kaggle, berikut link kagglenya : https://www.kaggle.com/datasets/arshid/iris-flower-dataset

## Data Deskriptif

Statistik deskriptif membantu untuk memberikan gambaran kuantitatif, dan penyebaran datanya. Berikut adalah gambarannya untuk seluruh sampel:

### Iris Data Visual
Deskripsi menggunakan aplikasi orange
![Grafik Data](/gambar/iris01.png)
![Grafik Data](/gambar/iris02.png)

Berikut juga implementasi menggunakan python :
```{code-cell}
:tags: [hide-input]
import pandas as pd
from scipy import stats

df=pd.read_csv("IRIS.csv",usecols=[0])
kolom = df['sepal_length']

print("Jumlah data        :", kolom.count())
print("Rata-rata          :", round(kolom.mean(), 2))
print("Nilai minimal      :", kolom.min())
print("Q1                 :", kolom.quantile(0.25))
print("Q2 (Median)        :", kolom.quantile(0.5))
print("Q3                 :", kolom.quantile(0.75))
print("Nilai maksimal     :", kolom.max())
print("Kemencengan (skew) :", round(kolom.skew(), 2))
mode = stats.mode(kolom, keepdims=True)
print("Nilai modus        :", mode.mode[0])
print("Jumlah modus       :", mode.count[0])

print("Standar deviasi    :", round(kolom.std(), 2))
print("Variansi           :", round(kolom.var(), 2))
```

Maka statistik ringkasannya sebagai berikut :
| Jenis Statistika Deskriptif | Nilai | Keterangan |
|----------------------------|-------|------------|
| Jumlah data (n) | 150 | Total observasi dalam dataset |
| Rata-rata (Mean) | 5.84 | Nilai rata-rata seluruh data, menunjukkan pusat distribusi |
| Median (Q2) | 5.8 | Nilai tengah data; 50% data berada di bawah dan 50% di atas |
| Modus (Mode) | 5.0 (10 kali) | Nilai yang paling sering muncul dalam data |
| Nilai Minimum (Min) | 4.3 | Nilai terkecil dalam dataset |
| Nilai Maksimum (Max) | 7.9 | Nilai terbesar dalam dataset |
| Kuartil 1 (Q1) | 5.1 | 25% data berada di bawah atau sama dengan nilai ini |
| Kuartil 3 (Q3) | 6.4 | 75% data berada di bawah atau sama dengan nilai ini |
| Standar Deviasi | 0.83 | Mengukur tingkat penyebaran data terhadap rata-rata |
| Variansi | 0.69 | Kuadrat dari standar deviasi, menunjukkan besar penyebaran data |

## Visualisasi Data

Visualisasi mengubah angka-angka deskriptif di atas menjadi pola yang mudah dipahami oleh mata manusia. Seperti data dalam bentuk grafik, diagram, atau gambar.

### Scatter Plot

Scatter plot ialah grafik yang digunakan untuk menampilkan hubungan antara dua variabel numerik dalam bentuk titik-titik pada bidang koordinat.
![Grafik Data](/gambar/scatteriris.png)

### Histogram

Histogram digunakan untuk menampilkan distribusi atau penyebaran data numerik dalam bentuk batang. Berikut salah satu contoh dari sampelnya :
![Grafik Data](/gambar/histoiris.png)
# prediksi-konsumsi-energi-sdg7
Project AI untuk memprediksi tingkat konsumsi energi rumah tangga menggunakan Decision Tree dan Random Forest.
# Prediksi Konsumsi Energi Rumah Tangga

## Deskripsi Project

Project ini merupakan penerapan kecerdasan buatan (Artificial Intelligence) untuk memprediksi tingkat konsumsi energi rumah tangga menggunakan algoritma **Decision Tree** dan **Random Forest**.

Project ini berkaitan dengan **Sustainable Development Goal (SDG) 7: Affordable and Clean Energy**, khususnya dalam mendukung upaya efisiensi dan penghematan energi melalui pemanfaatan teknologi dan data.

## Latar Belakang

Konsumsi energi rumah tangga dapat berbeda-beda pada setiap waktu. Penggunaan energi yang tinggi perlu diketahui agar dapat menjadi bahan evaluasi dalam upaya meningkatkan efisiensi energi.

Oleh karena itu, project ini menggunakan data konsumsi energi rumah tangga untuk membangun model AI yang dapat mengklasifikasikan tingkat konsumsi energi menjadi tiga kategori, yaitu:

* Rendah
* Sedang
* Tinggi

## Tujuan

Tujuan project ini adalah:

1. Mengolah dan membersihkan dataset konsumsi energi rumah tangga.
2. Membuat model klasifikasi menggunakan Decision Tree.
3. Membuat model klasifikasi menggunakan Random Forest.
4. Membandingkan hasil kedua algoritma berdasarkan performa pengujian.
5. Menggunakan hasil prediksi sebagai informasi yang dapat mendukung upaya penghematan dan efisiensi energi.

## Dataset

Dataset yang digunakan adalah **Household Power Consumption** yang diperoleh dari Kaggle.

Dataset berisi informasi mengenai penggunaan energi listrik rumah tangga, seperti:

* Global Active Power
* Global Reactive Power
* Voltage
* Global Intensity
* Sub Metering 1
* Sub Metering 2
* Sub Metering 3

Dataset Kaggle:

https://www.kaggle.com/datasets/shivsaar/dataset

## Preprocessing Data

Tahapan pengolahan data yang dilakukan:

1. Memasukkan dataset CSV ke Google Colab.
2. Mengubah data menjadi DataFrame.
3. Memeriksa data awal.
4. Memeriksa data duplikat.
5. Menghapus data duplikat.
6. Memeriksa nilai kosong.
7. Menghapus data yang memiliki nilai kosong.
8. Mengubah kolom waktu menjadi format datetime.
9. Membuat kategori konsumsi energi.

Jumlah data awal adalah **260.640 baris**.

Setelah proses pembersihan, diperoleh **256.844 baris**.

## Kategori Konsumsi Energi

Konsumsi energi diklasifikasikan menjadi tiga kategori:

* **Rendah**
* **Sedang**
* **Tinggi**

Kategori dibuat berdasarkan nilai `global_active_power` menggunakan batas kuartil dari dataset.

## Pembagian Data

Dataset dibagi menjadi:

* **80% data training:** 205.475 data
* **20% data testing:** 51.369 data

## Algoritma

### Decision Tree

Decision Tree merupakan algoritma klasifikasi yang menggunakan struktur seperti pohon untuk menentukan kategori berdasarkan kondisi pada data.

### Random Forest

Random Forest merupakan algoritma yang menggunakan beberapa Decision Tree dan menggabungkan hasilnya untuk menghasilkan prediksi.

## Hasil Pengujian

Hasil pengujian pada 51.369 data testing:

| Model         | Accuracy |
| ------------- | -------: |
| Decision Tree |   96,31% |
| Random Forest |   96,81% |

Random Forest memperoleh akurasi **96,81%**, sedangkan Decision Tree memperoleh akurasi **96,31%**.

## Classification Report

### Random Forest

| Kategori | Precision | Recall | F1-Score |
| -------- | --------: | -----: | -------: |
| Rendah   |      0,95 |   0,95 |     0,95 |
| Sedang   |      0,97 |   0,97 |     0,97 |
| Tinggi   |      0,99 |   0,99 |     0,99 |

### Decision Tree

| Kategori | Precision | Recall | F1-Score |
| -------- | --------: | -----: | -------: |
| Rendah   |      0,93 |   0,94 |     0,94 |
| Sedang   |      0,97 |   0,96 |     0,96 |
| Tinggi   |      0,99 |   0,99 |     0,99 |

## Prediksi Data Baru

Pada pengujian menggunakan satu data baru, diperoleh hasil:

* Decision Tree → **Sedang**
* Random Forest → **Sedang**

Kedua model memberikan hasil prediksi yang sama.

## Kesimpulan

Berdasarkan pengujian yang dilakukan, Decision Tree dan Random Forest dapat digunakan untuk mengklasifikasikan tingkat konsumsi energi rumah tangga menjadi kategori Rendah, Sedang, dan Tinggi.

Pada dataset dan pembagian data yang digunakan dalam project ini, Decision Tree memperoleh akurasi sebesar **96,31%**, sedangkan Random Forest memperoleh akurasi sebesar **96,81%**.

Hasil klasifikasi dapat digunakan sebagai informasi untuk membantu mengidentifikasi tingkat konsumsi energi dan mendukung upaya penghematan serta efisiensi energi yang berkaitan dengan SDG 7.

## Teknologi yang Digunakan

* Python
* Google Colab
* Pandas
* Scikit-learn
* Matplotlib
* Kaggle
* GitHub

## File Project

`prediksi_konsumsi_energi.ipynb` merupakan notebook Google Colab yang berisi proses pengolahan data, pembuatan model, pengujian, evaluasi, dan prediksi.

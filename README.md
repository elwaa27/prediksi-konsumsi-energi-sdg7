# Pemanfaatan Decision Tree dan Random Forest untuk Memprediksi Konsumsi Energi Rumah Tangga sebagai Upaya Penghematan Energi

## Deskripsi Proyek

Proyek ini menerapkan algoritma **Decision Tree** dan **Random Forest** untuk mengklasifikasikan konsumsi energi rumah tangga ke dalam tiga kategori, yaitu Rendah, Sedang, dan Tinggi. Proyek ini menggunakan dataset *Household Power Consumption* dan menerapkan tahapan preprocessing, analisis korelasi, standardisasi, normalisasi, pelatihan model, serta evaluasi performa.

Proyek ini merupakan bagian dari mata kuliah Kecerdasan Buatan yang dikaitkan dengan **Sustainable Development Goal 7 (SDG 7): Affordable and Clean Energy**.

## Latar Belakang

Konsumsi energi rumah tangga dapat berubah sesuai dengan penggunaan berbagai peralatan listrik. Pengelompokan tingkat konsumsi energi dapat membantu memahami pola penggunaan energi.

Machine learning digunakan untuk membangun model klasifikasi yang mampu mengelompokkan konsumsi energi berdasarkan fitur-fitur yang tersedia. Dalam proyek ini, algoritma Decision Tree dan Random Forest diterapkan dan dibandingkan untuk mengetahui performa masing-masing model.

## Identitas Kelompok

| Nama | NIM |
|---|---|
| Muh. Azriel Fabian | F1G125064 |
| Intan Aulia Zalzabila | F1G125008 |
| Fitria Rizki Oktavia | F1G125006 |

**Kelompok 7 — Program Studi Ilmu Komputer**

## Rumusan Masalah

1. Bagaimana mengklasifikasikan konsumsi energi rumah tangga menjadi kategori Rendah, Sedang, dan Tinggi?
2. Bagaimana menerapkan algoritma Decision Tree dan Random Forest untuk klasifikasi konsumsi energi rumah tangga?
3. Bagaimana performa kedua model berdasarkan hasil evaluasi?

## Tujuan

1. Melakukan preprocessing dan analisis data konsumsi energi rumah tangga.
2. Membangun model klasifikasi menggunakan algoritma Decision Tree dan Random Forest.
3. Mengevaluasi dan membandingkan performa kedua model untuk menentukan model dengan hasil pengujian yang lebih baik.

## Dataset

Dataset yang digunakan adalah **Household Power Consumption**, yang diperoleh dari Kaggle.

Sumber dataset: https://www.kaggle.com/datasets/shivsaar/dataset

Dataset awal memiliki 260.640 baris dan 8 kolom. Data tersebut memiliki 3.771 nilai kosong pada setiap kolom serta 2.356 baris duplikat berdasarkan pemeriksaan awal pada notebook.

Setelah preprocessing, dataset yang digunakan berjumlah **256.844 baris**, tanpa nilai kosong dan tanpa baris duplikat.

### Atribut Dataset

Dataset mencakup informasi waktu dan konsumsi listrik, dengan atribut:

- `time`
- `global_active_power`
- `global_reactive_power`
- `voltage`
- `global_intensity`
- `sub_metering_1`
- `sub_metering_2`
- `sub_metering_3`

## Tahapan Penelitian

### 1. Preprocessing Data

Preprocessing dilakukan untuk mempersiapkan data sebelum pemodelan, meliputi:

- Menghapus baris duplikat.
- Menghapus data yang memiliki nilai kosong.
- Mengubah kolom waktu ke format datetime.
- Memeriksa kembali kondisi data setelah pembersihan.

Hasil preprocessing menghasilkan 256.844 baris data yang siap digunakan untuk analisis dan pemodelan.

### 2. Pembentukan Kategori Konsumsi Energi

Kategori target dibentuk berdasarkan nilai `global_active_power` menjadi tiga kelas:

| Kategori | Rentang |
|---|---|
| Rendah | Lebih dari 0 hingga 0,296 |
| Sedang | Lebih dari 0,296 hingga 1,606 |
| Tinggi | Lebih dari 1,606 |

Distribusi kategori setelah pembentukan target:

| Kategori | Jumlah Data |
|---|---:|
| Rendah | 64.575 |
| Sedang | 128.118 |
| Tinggi | 64.151 |
| **Total** | **256.844** |

### 3. Analisis Korelasi

Analisis korelasi digunakan untuk melihat hubungan antarvariabel numerik dalam dataset dan membantu memahami keterkaitan fitur dengan konsumsi energi.

Pada hasil analisis yang ditampilkan dalam presentasi, nilai korelasi yang disorot adalah:

- `global_intensity`: 1,00
- `sub_metering_3`: 0,61
- `voltage`: -0,38

Nilai korelasi menunjukkan arah dan kekuatan hubungan linear antarvariabel yang dianalisis. Korelasi tidak dengan sendirinya membuktikan hubungan sebab-akibat.

### 4. Pemilihan Fitur dan Target

Fitur yang digunakan untuk pelatihan model terdiri dari enam atribut:

- `global_reactive_power`
- `voltage`
- `global_intensity`
- `sub_metering_1`
- `sub_metering_2`
- `sub_metering_3`

Target klasifikasi adalah `energy_category`, yang terdiri dari kategori Rendah, Sedang, dan Tinggi.

Atribut `global_active_power` digunakan untuk membentuk target dan tidak dimasukkan sebagai fitur prediksi agar model tidak memperoleh target secara langsung.

### 5. Pembagian Data

Dataset dibagi menjadi data pelatihan dan pengujian dengan perbandingan 80:20.

| Jenis Data | Jumlah | Persentase |
|---|---:|---:|
| Training | 205.475 | 80% |
| Testing | 51.369 | 20% |
| **Total** | **256.844** | **100%** |

Pembagian menggunakan `random_state=42` dan `stratify=y` untuk mempertahankan proporsi kategori pada kedua bagian data.

### 6. Standardisasi dan Normalisasi

Pemrosesan skala fitur dalam eksperimen menggunakan dua metode:

- **StandardScaler:** menstandarkan fitur berdasarkan rata-rata dan simpangan baku data pelatihan.
- **MinMaxScaler:** mengubah nilai fitur ke rentang 0–1.

Pada alur eksperimen yang ditampilkan, data terlebih dahulu melalui standardisasi menggunakan StandardScaler, kemudian normalisasi menggunakan MinMaxScaler. Parameter transformasi dipelajari dari data training dan diterapkan pada data testing.

Kedua transformasi ini menjadi bagian dari alur preprocessing yang digunakan dalam eksperimen model.

### 7. Pelatihan Model

Dua algoritma klasifikasi digunakan dalam penelitian ini.

**Decision Tree**

Decision Tree membentuk pohon keputusan dengan membagi data berdasarkan nilai fitur untuk menghasilkan prediksi kategori konsumsi energi. Model menggunakan `random_state=42`.

**Random Forest**

Random Forest menggabungkan prediksi dari 100 pohon keputusan. Model menggunakan `n_estimators=100` dan `random_state=42`.

## Hasil Evaluasi Model

Pengujian dilakukan menggunakan 51.369 data testing.

| Model | Akurasi |
|---|---:|
| Decision Tree | 96,31% |
| Random Forest | 96,81% |

Berdasarkan hasil yang ditampilkan dalam presentasi, Random Forest memiliki akurasi lebih tinggi sekitar **0,50 poin persentase** dibandingkan Decision Tree.

### Confusion Matrix

Baris menunjukkan kategori aktual, sedangkan kolom menunjukkan kategori prediksi. Urutan kategori adalah Rendah, Sedang, dan Tinggi.

**Decision Tree**

| Aktual / Prediksi | Rendah | Sedang | Tinggi |
|---|---:|---:|---:|
| Rendah | 12.186 | 729 | 0 |
| Sedang | 854 | 24.616 | 154 |
| Tinggi | 0 | 154 | 12.676 |

**Random Forest**

| Aktual / Prediksi | Rendah | Sedang | Tinggi |
|---|---:|---:|---:|
| Rendah | 12.220 | 695 | 0 |
| Sedang | 695 | 24.783 | 146 |
| Tinggi | 0 | 98 | 12.732 |

Berdasarkan hasil evaluasi pada presentasi, kedua model menunjukkan performa klasifikasi yang tinggi. Kesalahan prediksi terutama terjadi antara kategori yang berdekatan, yaitu Rendah dan Sedang atau Sedang dan Tinggi.

### F1-Score

| Kategori | Decision Tree | Random Forest |
|---|---:|---:|
| Rendah | 0,94 | 0,95 |
| Sedang | 0,96 | 0,97 |
| Tinggi | 0,99 | 0,99 |

Hasil tersebut menunjukkan bahwa Random Forest memperoleh F1-score lebih tinggi pada kategori Rendah dan Sedang, sedangkan kedua model memperoleh F1-score yang sama pada kategori Tinggi berdasarkan pembulatan yang ditampilkan.

## Prediksi Data Baru

Kedua model diuji menggunakan satu contoh data baru dengan enam fitur berikut:

| Fitur | Nilai |
|---|---:|
| `global_reactive_power` | 0,10 |
| `voltage` | 240,00 |
| `global_intensity` | 2,50 |
| `sub_metering_1` | 0,00 |
| `sub_metering_2` | 1,00 |
| `sub_metering_3` | 10,00 |

Hasil prediksi:

| Model | Prediksi |
|---|---|
| Decision Tree | Sedang |
| Random Forest | Sedang |

Kedua model menghasilkan prediksi yang konsisten, yaitu kategori **Sedang**, pada contoh data tersebut.

## Teknologi yang Digunakan

- Python
- pandas
- scikit-learn
- Jupyter Notebook
- Dataset Household Power Consumption
- Matplotlib dan Seaborn untuk visualisasi, apabila digunakan pada notebook

## Struktur Proyek

- `prediksi_konsumsi_energii.ipynb` — notebook yang memuat proses pengolahan data, analisis, pelatihan model, evaluasi, dan prediksi.

Nama file notebook perlu disesuaikan jika nama berkas di repositori berbeda.

## Kesimpulan

Berdasarkan hasil pengujian pada dataset dan pembagian data yang digunakan, Decision Tree memperoleh akurasi 96,31%, sedangkan Random Forest memperoleh akurasi 96,81%. Dengan demikian, Random Forest menjadi model dengan akurasi lebih tinggi dalam eksperimen ini.

Kedua model mampu mengklasifikasikan konsumsi energi rumah tangga ke dalam kategori Rendah, Sedang, dan Tinggi. Hasil penelitian ini dapat menjadi bahan pendukung untuk memahami pola konsumsi energi dan dikaitkan dengan upaya penggunaan energi yang lebih efisien. Namun, model klasifikasi ini tidak secara langsung menghemat listrik dan hasilnya bergantung pada data serta metode pengujian yang digunakan.

## Referensi

1. Dataset Household Power Consumption dari Kaggle: https://www.kaggle.com/datasets/shivsaar/dataset
2. Dokumentasi pandas: https://pandas.pydata.org/docs/
3. Dokumentasi scikit-learn: https://scikit-learn.org/stable/
4. Dokumentasi Matplotlib: https://matplotlib.org/stable/
5. Dokumentasi Seaborn: https://seaborn.pydata.org/

# Prediksi Konsumsi Energi Rumah Tangga

## Deskripsi Proyek

Proyek ini menerapkan kecerdasan buatan (*Artificial Intelligence*) untuk mengklasifikasikan tingkat konsumsi energi rumah tangga menjadi tiga kategori, yaitu **Rendah, Sedang, dan Tinggi**, menggunakan algoritma Decision Tree dan Random Forest.

Proyek ini bertujuan memberikan informasi mengenai kategori penggunaan energi berdasarkan data konsumsi listrik. Hasil klasifikasi dapat digunakan sebagai bahan pendukung evaluasi penggunaan listrik dan upaya efisiensi energi.

Proyek ini berkaitan dengan **Sustainable Development Goal (SDG) 7: Affordable and Clean Energy**, khususnya dalam mendukung penggunaan energi secara lebih efisien.

## Latar Belakang

Konsumsi energi listrik rumah tangga dapat bervariasi berdasarkan pola penggunaan peralatan listrik. Informasi mengenai tingkat konsumsi energi dapat membantu pengguna mengevaluasi penggunaan listriknya.

Untuk mendukung proses tersebut, proyek ini menggunakan algoritma machine learning untuk mempelajari pola dari data konsumsi listrik dan mengklasifikasikannya ke dalam kategori Rendah, Sedang, atau Tinggi.

Model tidak secara langsung menghemat listrik, tetapi menghasilkan informasi yang dapat mendukung evaluasi penggunaan energi.

## Anggota Kelompok

| No. | Nama | NIM |
|---|---|---|
| 1 | Muh. Azriel Fabian | F1G125064 |
| 2 | Intan Aulia Zalzabila | F1G125008 |
| 3 | Fitria Rizki Oktavia | F1G125006 |

## Rumusan Masalah

1. Bagaimana mengolah data konsumsi energi rumah tangga agar dapat digunakan untuk klasifikasi?
2. Bagaimana menerapkan algoritma Decision Tree dan Random Forest untuk mengklasifikasikan tingkat konsumsi energi?
3. Bagaimana menganalisis hubungan antarvariabel dalam dataset?
4. Bagaimana membandingkan performa kedua algoritma berdasarkan hasil pengujian?
5. Bagaimana menggunakan model terlatih untuk mengklasifikasikan data konsumsi energi baru?

## Tujuan

1. Melakukan preprocessing terhadap dataset konsumsi energi rumah tangga.
2. Menganalisis korelasi antarvariabel numerik.
3. Membentuk kategori konsumsi energi menjadi Rendah, Sedang, dan Tinggi.
4. Membangun model klasifikasi menggunakan Decision Tree dan Random Forest.
5. Menerapkan standardisasi dan menguji normalisasi data.
6. Mengevaluasi serta membandingkan performa kedua model.
7. Melakukan prediksi kategori konsumsi energi pada data baru.
8. Mendukung evaluasi dan peningkatan kesadaran terhadap efisiensi penggunaan energi.

## Dataset

Dataset yang digunakan adalah **Household Power Consumption** dari Kaggle.

Sumber dataset: [Household Power Consumption — Kaggle](https://www.kaggle.com/datasets/shivsaar/dataset)

Dataset memiliki delapan kolom awal:

| Kolom | Keterangan |
|---|---|
| `time` | Informasi waktu pengukuran |
| `global_active_power` | Konsumsi daya aktif global |
| `global_reactive_power` | Daya reaktif global |
| `voltage` | Tegangan listrik |
| `global_intensity` | Intensitas arus listrik |
| `sub_metering_1` | Pengukuran energi pada submeter 1 |
| `sub_metering_2` | Pengukuran energi pada submeter 2 |
| `sub_metering_3` | Pengukuran energi pada submeter 3 |

### Kondisi Dataset

| Keterangan | Jumlah |
|---|---:|
| Data awal | 260.640 baris |
| Data setelah preprocessing | 256.844 baris |
| Fitur input model | 6 |
| Kategori target | 3 |

## Metodologi dan Alur Pengerjaan

Proyek dilakukan melalui tahapan berikut:

1. Memuat dataset dan melakukan eksplorasi data.
2. Memeriksa serta membersihkan data duplikat dan nilai kosong.
3. Mengubah format kolom waktu.
4. Melakukan analisis korelasi antarvariabel numerik.
5. Membentuk kategori konsumsi energi sebagai target klasifikasi.
6. Menentukan fitur input dan target.
7. Membagi dataset menjadi data training dan testing.
8. Melakukan standardisasi fitur.
9. Menguji normalisasi sebagai transformasi tambahan.
10. Melatih model Decision Tree dan Random Forest.
11. Mengevaluasi dan membandingkan performa model.
12. Menggunakan model terlatih untuk memprediksi data baru.

## Preprocessing Data

Preprocessing dilakukan untuk mempersiapkan dataset sebelum digunakan dalam proses machine learning. Tahapannya meliputi pemeriksaan struktur data, penghapusan duplikasi, penanganan nilai kosong, perubahan format waktu, pembentukan kategori target, pemilihan fitur, pembagian data, dan standardisasi.

Setelah preprocessing, diperoleh **256.844 baris data** tanpa nilai kosong dan tanpa data duplikat.

## Analisis Korelasi

Analisis korelasi digunakan untuk mengetahui arah dan kekuatan hubungan linear antarvariabel numerik dalam dataset. Hasilnya dapat disajikan dalam bentuk heatmap agar hubungan antarvariabel lebih mudah diamati.

Nilai korelasi yang mendekati 1 menunjukkan hubungan positif yang kuat, sedangkan nilai yang mendekati -1 menunjukkan hubungan negatif yang kuat. Nilai yang mendekati 0 menunjukkan hubungan linear yang lemah.

Analisis ini membantu memahami karakteristik data dan hubungan antarfitur. Namun, korelasi tidak membuktikan hubungan sebab-akibat dan tidak menjadi satu-satunya dasar pemilihan fitur model.

## Pembentukan Kategori Konsumsi Energi

Kolom `global_active_power` digunakan untuk membentuk variabel target bernama `energy_category`.

| Kategori | Rentang `global_active_power` |
|---|---|
| Rendah | Lebih dari 0 sampai dengan 0,296 |
| Sedang | Lebih dari 0,296 sampai dengan 1,606 |
| Tinggi | Lebih dari 1,606 |

Distribusi kategori pada dataset:

| Kategori | Jumlah Data |
|---|---:|
| Rendah | 64.575 |
| Sedang | 128.118 |
| Tinggi | 64.151 |
| **Total** | **256.844** |

Pembentukan kategori tersebut menjadikan proyek ini sebagai masalah klasifikasi tiga kelas, bukan peramalan nilai konsumsi energi pada masa mendatang.

## Fitur Input dan Target

Model menggunakan enam fitur input:

1. `global_reactive_power`
2. `voltage`
3. `global_intensity`
4. `sub_metering_1`
5. `sub_metering_2`
6. `sub_metering_3`

Target yang diprediksi adalah `energy_category`, yang terdiri dari kategori Rendah, Sedang, dan Tinggi.

Kolom `global_active_power` tidak digunakan sebagai fitur input karena kolom tersebut digunakan untuk membentuk target kategori. Pemisahan ini membantu menghindari kebocoran target (*target leakage*) dalam pelatihan dan evaluasi model.

## Pembagian Data Training dan Testing

Dataset dibagi dengan proporsi 80% untuk training dan 20% untuk testing.

| Jenis Data | Jumlah Baris | Proporsi |
|---|---:|---:|
| Training | 205.475 | 80% |
| Testing | 51.369 | 20% |
| **Total** | **256.844** | **100%** |

Pembagian data menggunakan nilai acak tetap agar hasil dapat direproduksi dan mempertahankan proporsi kategori target pada data training dan testing.

Data training digunakan untuk melatih model, sedangkan data testing digunakan untuk mengevaluasi kemampuan model pada data yang tidak digunakan selama pelatihan.

## Standardisasi Data

Standardisasi dilakukan menggunakan metode StandardScaler untuk menyamakan skala fitur berdasarkan rata-rata dan standar deviasi data training.

Parameter standardisasi dihitung menggunakan data training, kemudian diterapkan pada data training dan testing. Data baru juga harus ditransformasikan menggunakan scaler yang sama sebelum diprediksi.

Proses ini membantu memastikan transformasi data testing tidak memengaruhi perhitungan parameter standardisasi.

## Normalisasi Data

Normalisasi merupakan proses mengubah skala nilai fitur ke rentang tertentu, umumnya 0 sampai 1. Salah satu metode yang dapat digunakan adalah Min-Max Scaling.

Dalam proyek ini, normalisasi dapat diuji sebagai eksperimen tambahan untuk melihat pengaruh transformasi skala terhadap performa model. Jika normalisasi diterapkan setelah standardisasi, hasil transformasi harus diproses dan dievaluasi secara terpisah.

Parameter normalisasi dihitung berdasarkan data training dan kemudian diterapkan pada data testing menggunakan parameter yang sama.

Decision Tree dan Random Forest umumnya tidak memerlukan standardisasi maupun normalisasi agar dapat bekerja. Oleh karena itu, hasil eksperimen transformasi skala perlu dibandingkan melalui evaluasi, bukan diasumsikan selalu meningkatkan akurasi.

## Algoritma yang Digunakan

### 1. Decision Tree

Decision Tree merupakan algoritma klasifikasi yang menggunakan struktur pohon keputusan untuk menentukan kategori berdasarkan aturan yang dipelajari dari fitur input pada data training.

Model ini dilatih menggunakan data training dan dievaluasi menggunakan data testing.

### 2. Random Forest

Random Forest merupakan algoritma klasifikasi yang menggabungkan prediksi dari sejumlah pohon keputusan untuk menghasilkan kategori akhir.

Pada proyek ini, Random Forest menggunakan 100 pohon keputusan. Kedua algoritma dilatih dan dievaluasi menggunakan pembagian data yang sama agar hasilnya dapat dibandingkan.

## Evaluasi Model

Evaluasi dilakukan menggunakan 51.369 baris data testing.

Metrik yang digunakan meliputi:

- **Accuracy:** proporsi prediksi yang benar dari seluruh data testing.
- **Precision:** ketepatan prediksi untuk suatu kategori.
- **Recall:** kemampuan model mengenali data yang benar-benar termasuk suatu kategori.
- **F1-score:** gabungan nilai precision dan recall.
- **Confusion matrix:** jumlah prediksi benar dan salah untuk setiap kategori.

## Hasil Pengujian Model

Hasil pengujian utama pada data testing:

| Model | Akurasi |
|---|---:|
| Decision Tree | 96,31% |
| Random Forest | 96,81% |

Random Forest memperoleh akurasi sekitar 0,50 poin persentase lebih tinggi dibandingkan Decision Tree.

### Classification Report Random Forest

| Kategori | Precision | Recall | F1-Score |
|---|---:|---:|---:|
| Rendah | 0,95 | 0,95 | 0,95 |
| Sedang | 0,97 | 0,97 | 0,97 |
| Tinggi | 0,99 | 0,99 | 0,99 |

Nilai pada tabel dibulatkan hingga dua angka desimal.

### Pemilihan Model

Berdasarkan hasil pengujian, Random Forest memperoleh akurasi sebesar 96,81%, sedangkan Decision Tree memperoleh akurasi sebesar 96,31%.

Dengan demikian, Random Forest dipilih sebagai model dengan akurasi pengujian lebih tinggi pada dataset yang digunakan. Hasil ini tidak berarti Random Forest selalu lebih unggul pada semua dataset.

## Prediksi Data Baru

Model terlatih digunakan untuk memprediksi data baru dengan nilai fitur berikut:

| Fitur | Nilai |
|---|---:|
| `global_reactive_power` | 0,10 |
| `voltage` | 240,00 |
| `global_intensity` | 2,50 |
| `sub_metering_1` | 0,00 |
| `sub_metering_2` | 1,00 |
| `sub_metering_3` | 10,00 |

Hasil prediksi:

| Model | Hasil Prediksi |
|---|---|
| Decision Tree | Sedang |
| Random Forest | Sedang |

Kedua model menghasilkan kategori Sedang untuk data tersebut.

Data baru ditransformasikan menggunakan scaler yang sesuai dengan model, kemudian diproses untuk menghasilkan prediksi. Proses penggunaan model terlatih untuk memprediksi data baru disebut *inference*.

## Teknologi dan Library

| Teknologi atau Library | Kegunaan |
|---|---|
| Python | Bahasa pemrograman |
| Google Colab | Lingkungan menjalankan notebook |
| Pandas | Membaca, membersihkan, dan mengolah dataset |
| NumPy | Mendukung operasi numerik |
| Scikit-learn | Pembagian data, transformasi fitur, pelatihan, prediksi, dan evaluasi model |
| Matplotlib | Visualisasi data |
| Seaborn | Visualisasi heatmap korelasi jika digunakan |
| Kaggle | Sumber dataset |
| GitHub | Penyimpanan dan dokumentasi proyek |

## Struktur Proyek

- `README.md` — dokumentasi proyek, metodologi, dan hasil pengujian.
- `prediksi_konsumsi_energii.ipynb` — notebook yang berisi proses pemuatan dataset, preprocessing, analisis korelasi, pembentukan kategori, pembagian data, transformasi fitur, pelatihan model, evaluasi, dan prediksi data baru.

## Cara Menjalankan Proyek

1. Unduh dataset dari [Kaggle — Household Power Consumption](https://www.kaggle.com/datasets/shivsaar/dataset).
2. Buka notebook `prediksi_konsumsi_energii.ipynb` melalui Google Colab.
3. Siapkan dataset sesuai lokasi file yang digunakan dalam notebook.
4. Jalankan setiap tahapan secara berurutan.
5. Periksa hasil preprocessing, analisis korelasi, evaluasi model, dan prediksi data baru.

## Keterbatasan Proyek

1. Kategori konsumsi energi dibentuk berdasarkan batas nilai `global_active_power` yang ditetapkan dalam pengolahan data.
2. Akurasi model mencerminkan hasil pengujian pada dataset dan pembagian data yang digunakan.
3. Hasil prediksi bergantung pada kualitas dan kesesuaian data masukan.
4. Analisis korelasi menunjukkan hubungan antarvariabel, tetapi tidak membuktikan hubungan sebab-akibat.
5. Standardisasi dan normalisasi merupakan metode transformasi skala yang berbeda. Pengaruhnya terhadap model perlu diperiksa melalui eksperimen.
6. Model mengklasifikasikan kategori konsumsi energi dan tidak secara langsung mengurangi pemakaian listrik.
7. Proyek ini berfokus pada klasifikasi, bukan peramalan konsumsi energi masa depan.

## Kesimpulan

Decision Tree dan Random Forest berhasil diterapkan untuk mengklasifikasikan konsumsi energi rumah tangga ke dalam kategori Rendah, Sedang, dan Tinggi.

Dataset melalui preprocessing, analisis korelasi, pembentukan target, pembagian data training dan testing, serta standardisasi sebelum digunakan untuk melatih model utama.

Hasil pengujian menunjukkan akurasi Decision Tree sebesar 96,31% dan Random Forest sebesar 96,81%. Berdasarkan hasil tersebut, Random Forest memiliki akurasi pengujian lebih tinggi pada dataset yang digunakan.

Normalisasi dapat digunakan sebagai eksperimen tambahan untuk memeriksa pengaruh transformasi skala terhadap performa model. Hasil klasifikasi dapat menjadi informasi pendukung untuk mengevaluasi penggunaan energi rumah tangga dan mendorong efisiensi energi yang berkaitan dengan SDG 7.

## Referensi

- Dataset: [Household Power Consumption — Kaggle](https://www.kaggle.com/datasets/shivsaar/dataset)
- Repository: [prediksi-konsumsi-energi-sdg7 — GitHub](https://github.com/elwaa27/prediksi-konsumsi-energi-sdg7)
- Dokumentasi Scikit-learn: [scikit-learn.org](https://scikit-learn.org/stable/)
- Dokumentasi Pandas: [pandas.pydata.org](https://pandas.pydata.org/docs/)

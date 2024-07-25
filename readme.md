# Laporan Proyek Machine Learning - Femi Nabila

## Domain Proyek

Abalone atau 'siput laut' merupakan moluska laut yang memiliki nilai ekonomi yang tinggi. Populasi abalone telah menurun drastis akibat penangkapan berlebihan, pencemaran, dan perubahan iklim. Hal ini membuat prediksi usia abalone menjadi penting untuk pengelolaan perikanan berkelanjutan dan konservasi spesies yang terancam punah. Dengan menggunakan data seperti ukuran fisik, berat, dan jumlah cincin pada cangkang, kita dapat menggunakan algoritma machine learning seperti KNN, Random Forest Regressor, dan Boosting Algorithm untuk memprediksi usia abalone. Pra-pemrosesan data, normalisasi, dan teknik evaluasi seperti cross-validation akan memastikan model yang dibangun akurat dan dapat diandalkan.

Prediksi usia abalone ini memiliki dampak signifikan terhadap industri perikanan dan upaya konservasi. Dengan prediksi usia abalone yang akurat, pengelola perikanan dapat membuat keputusan yang lebih bijak terkait penangkapan yang berkelanjutan, menjaga populasi abalone tetap stabil, dan mencegah penangkapan berlebihan. Selain itu, abalone yang lebih tua dan lebih berharga secara komersial dapat diidentifikasi dengan lebih mudah, meningkatkan nilai ekonomi bagi nelayan dan industri. Ketidakmampuan untuk mengelola populasi secara berkelanjutan akan memperburuk kondisi ekosistem laut, mengancam spesies lain yang bergantung pada abalone, dan dapat merusak keseimbangan ekologis secara keseluruhan. Oleh karena itu, tindakan segera diperlukan untuk menggunakan teknologi prediksi usia demi keberlanjutan dan kelestarian abalone.

## Business Understanding

### Problem Statements
- Bagaimana mengembangkan model yang dapat memprediksi umur abalone dengan error yang minim berdasarkan fitur tertentu?
- Model apa yang terbaik dalam memprediksi umur abalone berdasarkan fitur tertentu?

### Goals
- Mendapatkan model yang dapat memprediksi umur abalone dengan error yang minim berdasarkan fitur tertentu
- Mengetahui model yang terbaik dalam memprediksi umur abalone berdasarkan fitur tertentu

## Data Understanding
Dataset yang digunakan memiliki 4177 instances. Dataset berisi 8 feature yaitu Sex, Length, Diameter, Height, Whole_weight, Shucked_weight, Viscera_weight, dan Shell_weight, dengan Rings sebagai target. [Abalone](https://archive.ics.uci.edu/dataset/1/abalone).

### Variabel-variabel pada dataset adalah sebagai berikut:
| Name | Data Type | Measurement Unit | Description |
| -------- | ------- | ------- | ------- |
|Sex | nominal | -- | M, F, and I (infant) |
|Length | continuous | mm | Longest shell measurement |
|Diameter | continuous | mm | perpendicular to length |
|Height | continuous | mm | with meat in shell |
|Whole weight | continuous | grams | whole abalone |
|Shucked weight | continuous	 | grams | weight of meat |
|Viscera weight | continuous | grams | gut weight (after bleeding) |
|Shell weight | continuous | grams | after being dried |
|Rings | integer | -- | +1.5 gives the age in years |


## Data Preparation
1. Penanganan outlier menggunakan IQR
2. One Hot Enconding pada fitur 'Sex' 
3. Reduksi dimensi PCA untuk 'Diameter' dan 'Length'
4. Splitting dataset menjadi data train dan data test dengan rasio 80:20
5. Standarisasi data train dan data test

## Modeling
Pembuatan model dilakukan setelah data preparation, tahap ini mencakup pelatihan model dengan parameter yang ditentukan dan evaluasi hasil prediksi untuk menilai kinerja model. Ada 3 model dengan parameter yang digunakan dalam proyek ini yaitu:
1. KNN dilatih dengan melihat 15 titik terdekatnya (n_neighbors)
2. Random Forest dengan 50 pohon keputusan (trees) dengan kedalaman maksimal 8, dan proses pelatihan berjalan paralel menggunakan semua prosesor yang tersedia (n_jobs = -1)
3. Boosting Algorithm dengan learning rate sebesar 0.08 untuk mengurangi kesalahan secara bertahap melalui iterasi berturut-turut.

## Evaluation
Tujuan utama dari proyek ini adalah memprediksi umur abalone dengan error yang minim dan juga mengetahui model yang terbaik dalam memprediksi umur abalone, ini dilakukan untuk mendukung pengelolaan perikanan berkelanjutan dan konservasi. Digunakan Mean Squared Error (MSE) didapat dengan menghitung rata-rata dari kuadrat error

| Model | train_mse | test_mse |
| -------- | ------- | ------- |
| KNN  | 2.309799 |	2.870605   |
| RandomForest | 1.475024 | 2.735989 |
| Boosting	| 2.774085	| 3.10315 |

Hasil dari evaluasi menunjukkan bahwa Random Forest merupakan model yang terbaik dalam prediksi umur abalone dengan error paling sedikit yaitu ~1.5 pada pelatihan dan ~2.7 pada pengujian. Oleh karena itu, solusi ini berhasil menjawab problem statement dengan menyediakan metode prediksi yang dapat diandalkan untuk mengestimasi usia abalone.

Dengan prediksi Random Forest untuk usia abalone yang akurat, industri perikanan dapat meningkatkan nilai komersial abalone dengan pengelolaan perikanan dan upaya konservasi, juga dalam mengidentifikasi abalone yang lebih tua dan lebih bernilai, meningkatkan keuntungan ekonomi. 
# 📊 Laporan Proyek Machine Learning – *Leonard Bodhi Kumaro*

## 🌐 Domain Proyek

Industri **keuangan digital**, khususnya sektor *peer-to-peer (P2P) lending*, telah mengalami pertumbuhan pesat dalam beberapa tahun terakhir. Platform seperti **Lending Club** menyediakan alternatif pembiayaan yang fleksibel bagi individu dan pelaku usaha kecil, dibandingkan lembaga keuangan konvensional.

Salah satu komponen krusial dalam sistem pinjaman ini adalah **penetapan suku bunga**. Suku bunga yang terlalu tinggi dapat meningkatkan risiko gagal bayar, sementara suku bunga terlalu rendah dapat menurunkan keuntungan investor.

Karena penentuan suku bunga melibatkan banyak variabel seperti jumlah pinjaman, lama pinjaman, status verifikasi, skor kredit, dan lainnya, maka diperlukan pendekatan yang sistematis dan berbasis data. **Machine learning** memberikan solusi yang menjanjikan karena mampu mengenali pola-pola kompleks dari data historis [1].

Penelitian sebelumnya menunjukkan bahwa pendekatan supervised learning seperti **Random Forest** dan **XGBoost** efektif dalam prediksi risiko kredit dan penentuan suku bunga [2]. Oleh karena itu, proyek ini bertujuan membangun model prediktif berbasis machine learning untuk **menentukan suku bunga optimal** pada pinjaman Lending Club.

## 🎯 Business Understanding

### ❓ Problem Statements

- Bagaimana memprediksi suku bunga pinjaman berdasarkan fitur seperti jumlah pinjaman, pendapatan tahunan, status pekerjaan, dan lama pinjaman?
- Algoritma machine learning mana yang paling efektif dalam memprediksi tingkat suku bunga?
- Faktor-faktor apa saja yang paling berpengaruh dalam penentuan suku bunga pinjaman?

### 🎯 Goals

- Membangun model klasifikasi untuk memprediksi kelas suku bunga (*rendah*, *sedang*, *tinggi*).
- Membandingkan performa beberapa algoritma machine learning untuk menemukan model terbaik.
- Mengidentifikasi fitur penting yang paling memengaruhi penentuan suku bunga.

### 🛠️ Solution Statements

- Menerapkan tiga algoritma machine learning: **Random Forest**, **XGBoost**, dan **Artificial Neural Network (ANN)**.
- Melakukan **hyperparameter tuning** pada model XGBoost.
- Menggunakan metrik evaluasi seperti **accuracy, precision, recall, dan F1-score** untuk mengukur kinerja model.

## 📂 Data Understanding

Dataset yang digunakan adalah **Lending Club Loan Data** yang tersedia di Kaggle. Beberapa fitur utama yang digunakan adalah:

| Nama Fitur           | Deskripsi                                                                 |
|----------------------|--------------------------------------------------------------------------|
| `jumlah_pinjaman`    | Nominal pinjaman yang diajukan                                           |
| `lama_pinjaman`      | Durasi pinjaman dalam bulan                                              |
| `tujuan_pinjaman`    | Alasan pengajuan pinjaman                                                |
| `pendapatan_tahunan` | Total pendapatan tahunan peminjam                                        |
| `status_pekerjaan`   | Status pekerjaan peminjam                                                |
| `status_verifikasi`  | Status verifikasi penghasilan                                            |
| `kepemilikan_rumah`  | Status kepemilikan rumah                                                 |
| `kelas`              | Kelas kredit yang ditentukan oleh Lending Club                           |
| `suku_bunga`         | Tingkat bunga tahunan (target variabel), dikategorikan ke 3 kelas       |

Analisis eksploratif (*EDA*) dilakukan untuk memahami distribusi, korelasi, dan klasifikasi awal suku bunga ke dalam kategori: **rendah**, **sedang**, dan **tinggi**.

## 🧹 Data Preparation

Langkah-langkah utama:

1. **Pembersihan nama kolom**
2. **Penanganan missing values**
3. **Seleksi fitur yang relevan**
4. **Encoding variabel kategorikal (one-hot encoding)**
5. **Normalisasi data (MinMax Scaling)**
6. **Split data** ke dalam *training set* dan *testing set* dengan rasio 80:20

## 🤖 Modeling

### 🔍 Algoritma yang Digunakan

- **Random Forest Classifier**
  - `n_estimators = 100`, `max_depth = None`
- **XGBoost Classifier**
  - `learning_rate = 0.1`, `max_depth = 5`, `n_estimators = 100`
- **Artificial Neural Network (ANN)**
  - Arsitektur: Dense → BatchNorm → ReLU → Dropout → Output
  - Optimizer: Adam, Loss: categorical_crossentropy

### 🎛️ Hyperparameter Tuning (XGBoost)

Dilakukan dengan `RandomizedSearchCV` pada parameter:
- `learning_rate`
- `max_depth`
- `n_estimators`
- `subsample`

## 📈 Evaluation

### 📏 Metrik Evaluasi

- **Accuracy**: proporsi prediksi benar dari keseluruhan data
- **Precision**: ketepatan prediksi positif
- **Recall**: kemampuan model mendeteksi semua data positif
- **F1-Score**: harmonisasi antara precision dan recall
- **Confusion Matrix**: distribusi klasifikasi model terhadap data sebenarnya

### 🧪 Hasil Evaluasi

| Model                  | Accuracy | Precision | Recall | F1-Score |
|------------------------|----------|-----------|--------|----------|
| Random Forest          | 84%      | 0.83      | 0.84   | 0.83     |
| **XGBoost (tuned)**    | **87%**  | **0.86**  | **0.87** | **0.86** |
| ANN (Neural Network)   | 83%      | 0.82      | 0.83   | 0.82     |

✅ **XGBoost** adalah model terbaik berdasarkan akurasi dan skor evaluasi lainnya.

## ✅ Kesimpulan

- Model XGBoost menunjukkan kinerja terbaik dalam memprediksi suku bunga pinjaman, dengan **akurasi 87%** dan **F1-score 86%**.
- Hasil ini menunjukkan bahwa pendekatan machine learning dapat membantu lembaga keuangan menetapkan suku bunga secara lebih objektif dan efisien.

## 💡 Saran Lanjutan

1. Integrasikan model prediksi ke sistem real-time Lending Club.
2. Kembangkan fitur baru melalui teknik feature engineering.
3. Tangani ketidakseimbangan kelas dengan metode seperti **SMOTE**.
4. Gunakan teknik interpretasi model seperti **SHAP** untuk transparansi.
5. Uji model pada data dari platform pinjaman lain sebagai validasi eksternal.

## 📚 Referensi

[1] A. Nasrudi, "Brand Image Dan Suku Bunga Kredit Terhadap Peningkatan Nasabah Kredit di PT Bank Negara Indonesia (Persero) Tbk Kantor Cabang Kediri", *Jurnal Otonomi*, vol. 25(1), 2025. DOI: [10.32503/otonomi.v25i1.7032](https://doi.org/10.32503/otonomi.v25i1.7032)

[2] A. Namiera, F. Novika, & D. Kusdani, "Analisis Tingkat Suku Bunga pada Tarif Premi Tunggal Bruto Produk Asuransi Jiwa Kredit", *Premium Insurance Business Journal*, vol. 9(2), 2022. DOI: [10.35904/premium.v9i2.33](https://doi.org/10.35904/premium.v9i2.33)

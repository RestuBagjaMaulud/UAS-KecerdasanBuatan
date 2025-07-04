# UAS-KecerdasanBuatan
# Klasifikasi Penyakit Liver dengan Decision Tree & Neural Network
Proyek ini dibuat untuk memenugi tugas besar mata kuliah Kecerdasan Buatan, yang bertujuan membangun sistem klasifikasi penyakit liver (hati) menggunakan algoritma Decision Tree dan Neural Network.

# Tujuan Proyek
- Mendeteksi potensi penyakit liver berdasarkan data hasil pemeriksaan pasien.
- Membandingkan performa model Decision Tree dan Neural Network.
- Menghasilkan model yang akurat dan mudah dipahami (interpretable).

# Langkah-Langkah Pengerjaan
## 1. Business Understanding
- Menganalisis permasalahan dunia nyata: deteksi dini penyakit liver masih sulit.
- Merancang solusi AI sebagai sistem bantu keputusan untuk medis.
- Menentukan pengguna utama: dokter, klinik, tenaga medis.

## 2. Data Understanding
- Dataset: file CSV dari UCI-like atau dari Kaggle liver patient dataset.
- Fitur meliputi: usia, gender, bilirubin, SGPT, SGOT, albumin, dll.
- Label target: 1 = liver, 0 = non-liver.

## 3. Exploratory Data Analysis (EDA)
- Visualisasi distribusi: histogram, bar chart (age, gender, bilirubin).
- Korelasi antar fitur menggunakan heatmap.
- Deteksi imbalance pada kolom target.

## 4. Data Preparation
- Menghapus nilai null.
- Encoding kolom kategorik (Gender).
- Standardisasi fitur numerik (StandardScaler).
- Membagi data menjadi training dan testing (80:20).

## 5. Modeling
- Decision Tree: Kriteria yaitu entropy (C4.5) dan Library yaitu sklearn.tree.DecisionTreeClassifier.
- Neural Network: MLPClassifier dengan 1 hidden layer (8 neuron) dan Fungsi aktifitas yaitu ReLU.

## 6. Evaluation
- Confusion Matrix untuk tiap model.
- Metrik: Accuracy, Precision, Recall, F1-score, AUC.
- Perbandingan hasil Decision Tree vs Neural Network:
|      Model     | Accuracy |  AUC  |
| Decision Tree  |  75.56%  | 0.898 |
| Neural Network |  74.17%  | 0.671 |

## 7. Visualisasi
- Visualisasi pohon keputusan.
- Heatmap korelasi antar fitur.

# Hasil Akhir & Kesimpulan
- Model Decision Tree memberikan akurasi lebih tinggi dibanding Neural Network.
- Interpretasi model pohon lebih mudah dipahami oleh pengguna non-teknis.
- Neural Network masih potensial ditingkatkan melalui tuning dan dataset lebih besar.

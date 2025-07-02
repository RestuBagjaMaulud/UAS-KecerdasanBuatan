# Laporan Proyek UAS Kecerdasan Buatan
# Klasifikasi Penyakit Liver Menggunakan Algoritma Decision Tree dan Neural Network
## Nama Kelompok
- Restu Bagja Maulud (2306043)


# Business Understanding
## Permasalahan Dunia Nyata
Penyakit liver merupakan salah satu penyakit yang sering kali tidak menunjukkan gejala jelas pada tahap awal. Hal ini menyebabkan banyak pasien baru menyadari adanya masalah pada hati ketika penyakit sudah memasuki tahap lanjut. Dalam dunia medis, diagnosis dini terhadap penyakit ini sangat penting agar penanganan bisa lebih cepat dan tepat. Oleh karena itu, dibutuhkan sistem yang mampu membantu diagnosis dini berdasarkan data hasil tes laboratorium pasien.
## Tujuan Proyek
Tujuan dari proyek ini adalah membangun sistem berbasis kecerdasan buatan yang dapat memprediksi kemungkinan seseorang mengidap penyakit liver berdasarkan atribut hasil pemeriksaan laboratorium. Sistem ini akan memanfaatkan algoritma klasifikasi, khususnya Decision Tree dan Neural Network, untuk menghasilkan prediksi yang akurat dan dapat digunakan sebagai alat bantu pengambilan keputusan dalam dunia medis.
## Siapa Pengguna Sistem
Pengguna dari sistem ini meliputi:
- Dokter atau tenaga medis yang ingin melakukan diagnosa awal
- Peneliti atau pengembang sistem pakar medis
- Institusi kesehatan atau rumah sakit
- Mahasiswa dan akademisi dalam bidang Data Science dan Kesehatan
## Manfaat Implementasi AI
Dengan menggunakan metode kecerdasan buatan, proses diagnosis penyakit liver dapat menjadi lebih cepat, efisien, dan berbasis data. Model machine learning seperti Decision Tree dan Neural Network memungkinkan sistem untuk mendeteksi pola dari data medis yang kompleks dan membantu dokter dalam mendeteksi penyakit sebelum munculnya gejala klinis yang jelas. AI juga mengurangi kemungkinan kesalahan manusia dalam proses diagnosis.


# Data Understanding
## Sumber Data
Dataset diperoleh dari file CSV yang menyerupai "Indian Liver Patient Dataset (ILPD)" yang tersedia di UCI Machine Learning Repository. Dataset ini merupakan data simulasi medis yang sangat sering digunakan dalam proyek klasifikasi kesehatan, termasuk di jurnal CESS 2019 yang menjadi acuan.
## Deskripsi Fitur (Atribut)
Berikut ini adalah deskripsi masing-masing atribut yang terdapat dalam dataset:
| *No*|         *Nama Fitur*        |         *Deskripsi*                                                      |
|-----|-----------------------------|--------------------------------------------------------------------------|
|  1  | Age                         | Usia pasien dalam tahun                                                  |
|  2  | Gender                      | Jenis kelamin pasien (Male/Female)                                       |
|  3  | Total_Bilirubin             | Jumlah total bilirubin dalam darah                                       |
|  4  | Direct_Bilirubin            | Jumlah bilirubin langsung yang terikat dalam darah                       |
|  5  | Alkaline_Phosphotase        | Tingkat Enzim yang meningkat saat ada kerusakan hati atau saluran empedu |
|  6  | Alamine_Aminotransferase    | Tingkat Enzim SGPT yang menunjukkan kerusakan hati bila nilainya tinggi  |
|  7  | Aspartate_Aminotransferase  | Tingkat Enzim SGOT, juga menandakan peradangan atau kerusakan hati       |
|  8  | Total_Proteins              | Jumlah total protein dalam darah pasien                                  |
|  9  | Albumin                     | Protein utama dalam plasma darah                                         |
|  10 | Albumin_and_Globulin_Ratio  | Rasio antara albumin dengan globulin, menandakan fungsi hati             |
|  11 | Dataset                     | Label target, 1 = menderita penyakit liver, 0 = sehat                    |
|-----|-----------------------------|--------------------------------------------------------------------------|
## Ukuran dan Format Data
Data terdiri dari ratusan baris, dengan setiap baris mewakili satu pasien. Data disimpan dalam format CSV (Comma Separated Values) dan terdiri dari 11 kolom. Data ini siap digunakan dalam proses preprocessing dan pelatihan model.
## Tipe Data dan Targer Klasifikasi
Dataset terdiri dari kombinasi data numerik dan kategorikal. Fitur target adalah kolom "Dataset" yang memiliki dua nilai klasifikasi: 0 dan 1, menjadikan masalah ini sebagai tugas klasifikasi biner.


# Exploratory Data Analysis (EDA)
## Visualisasi Distribusi Data
Distribusi umur pasien sebagian besar berada di rentang 30–60 tahun. Gender menunjukkan distribusi tidak seimbang, dengan pasien laki-laki lebih banyak daripada perempuan. Nilai Total Bilirubin dan SGPT menunjukkan distribusi yang miring (skewed), yang mengindikasikan adanya outlier atau data ekstrem.
## Analisis Korelasi Antar Fitur
Heatmap korelasi mengungkapkan bahwa fitur Total_Bilirubin memiliki korelasi tinggi dengan Direct_Bilirubin. SGPT dan SGOT juga menunjukkan korelasi yang kuat satu sama lain. Ini menunjukkan bahwa beberapa fitur saling berkaitan erat secara medis.
## Deteksi Data Tidak Seimbang (Imbalanced Classes)
Data menunjukkan ketidakseimbangan pada target klasifikasi, di mana jumlah pasien yang menderita penyakit liver (label 1) lebih banyak dibanding yang tidak. Hal ini dapat menyebabkan model bias terhadap kelas mayoritas jika tidak ditangani dengan baik.
## Insight Awal dari Pola Data
Fitur-fitur yang berkaitan dengan kadar enzim hati dan bilirubin tampak berkontribusi besar dalam klasifikasi penyakit liver. Analisis awal ini memberikan petunjuk bahwa model dapat memanfaatkan fitur-fitur tersebut untuk klasifikasi yang akurat.


# Data Preparation 
## Pembersihan Data (Null Value, Duplikasi)
Data diperiksa dan dibersihkan dari nilai kosong dan duplikasi. Penghapusan dilakukan karena jumlah data kosong tidak terlalu banyak dan tidak memengaruhi distribusi data secara signifikan.
## Encoding Data Kategorik
Data kategorikal seperti Gender diubah menjadi bentuk numerik dengan teknik label encoding, yaitu Male = 1 dan Female = 0 agar bisa digunakan oleh algoritma machine learning.
## Normalisasi / Standardisasi Data Numerik
Beberapa fitur numerik memiliki skala berbeda-beda. Oleh karena itu, dilakukan standardisasi menggunakan StandardScaler agar model dapat belajar secara seimbang dari semua fitur.
## Split Data (Train-Test)
Dataset dibagi menjadi dua bagian: 80% untuk pelatihan (train) dan 20% untuk pengujian (test) dengan random_state untuk memastikan replikasi hasil yang konsisten.


# Modeling
## Pemilihan Algoritma
Model yang digunakan dalam proyek ini adalah:
- Decision Tree Classifier (dengan entropy/C4.5)
- Neural Network (MLPClassifier dari scikit-learn)
## Alasan Pemilihan Model
Decision Tree dipilih karena mudah diinterpretasikan dan cocok untuk dataset tabular. Neural Network digunakan sebagai pembanding karena mampu mempelajari relasi non-linear yang kompleks.
## Implementasi Model (dengan Kode)
Kedua model diimplementasikan dalam Google Colab dengan bahasa Python dan pustaka sklearn. Decision Tree menggunakan parameter criterion="entropy", sedangkan Neural Network menggunakan hidden layer berisi 8 neuron dan 1 output node.
## Visualisasi Model
Model Decision Tree divisualisasikan menggunakan plot_tree() agar aturan-aturan klasifikasi bisa dilihat secara langsung dan mudah dipahami oleh user non-teknis.


# Evaluation
## Confusion Matrix
Confusion matrix dari kedua model menampilkan hasil klasifikasi terhadap kelas 0 dan 1 (tidak sakit dan sakit liver), yang mencakup nilai TP, FP, TN, dan FN.
## Metrik Evaluasi
|     Metrik     | Akurasi |  AUC  | Precision |     Recall    |        F1-Score        | 
|----------------|-----------------------------|---------------|------------------------|
| Decision Tree  | 75.56%  | 0.898 |  Tinggi   |    Stabil     |        Seimbang        |
| Neural Network | 74.17%  | 0.671 |  Sedang   | Kurang stabil | Cenderung lebih rendah |
|----------------|-----------------------------|---------------|------------------------|
## Penjelasan Kinerja Model
Model Decision Tree menunjukkan performa yang lebih unggul dalam hal akurasi dan AUC. Selain itu, interpretasi yang mudah dari Decision Tree menjadikannya lebih cocok untuk aplikasi medis yang membutuhkan transparansi keputusan. Neural Network masih dapat ditingkatkan dengan tuning parameter dan penggunaan data yang lebih besar.


# Kesimpulan dan Rekomendasi
## Ringkasan Hasil Modeling dan Evaluasi
Decision Tree menghasilkan akurasi dan AUC yang lebih tinggi dibandingkan Neural Network. Hal ini menunjukkan bahwa untuk dataset penyakit liver ini, Decision Tree adalah model terbaik.
## Apakah Tujuan Proyek Tercapai?
Ya, proyek berhasil membangun sistem prediksi penyakit liver yang akurat dan dapat membantu proses diagnosis dini.
## Kelebihan dan Keterbatasan Model
Kelebihan Decision Tree adalah interpretasi mudah dan performa baik di dataset kecil. Kelemahannya: rawan overfitting. Neural Network unggul dalam fleksibilitas, namun butuh data dan tuning lebih.
## Rekomendasi Perbaikan
- Tambahkan jumlah data untuk pelatihan.
- Lakukan hyperparameter tuning untuk Neural Network.
- Uji model lain seperti Random Forest atau Gradient Boosting.
- Terapkan teknik balancing data seperti SMOTE untuk atasi kelas tidak seimbang.


# Referensi
1. 













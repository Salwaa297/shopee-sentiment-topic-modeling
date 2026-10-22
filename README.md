# Shopee Sentiment Analysis and Topic Modeling

## Deskripsi Proyek

Proyek ini bertujuan menganalisis sentimen dan mengidentifikasi aspek utama yang dibahas dalam ulasan pengguna aplikasi Shopee di Google Play Store. Pendekatan yang digunakan menggabungkan klasifikasi sentimen menggunakan **Multinomial Naive Bayes** dengan teknik penanganan ketidakseimbangan kelas **SMOTE**, serta *topic modeling* menggunakan **Latent Dirichlet Allocation (LDA)**.

Analisis ini dilakukan untuk memahami persepsi pengguna terhadap aplikasi Shopee, termasuk pengalaman berbelanja, kualitas produk, pengiriman, dan layanan aplikasi.

## Tujuan

- Mengklasifikasikan ulasan pengguna ke dalam sentimen positif, netral, dan negatif.
- Mengevaluasi performa Naive Bayes sebelum dan sesudah penanganan ketidakseimbangan kelas.
- Mengidentifikasi topik utama pada setiap kategori sentimen menggunakan LDA.
- Memvisualisasikan pola ulasan untuk memperoleh insight mengenai pengalaman pengguna Shopee.

## Dataset

Data diperoleh melalui proses web scraping ulasan aplikasi Shopee di Google Play Store.

- **Jumlah data:** 1.000 ulasan pengguna.
- **Atribut utama:** Nama pengguna, teks ulasan, rating, dan tanggal ulasan.
- **Target klasifikasi:** Sentimen positif, netral, dan negatif.

### Pelabelan Sentimen

Label sentimen ditentukan berdasarkan rating pengguna:

| Rating | Label Sentimen |
|---|---|
| 1–2 | Negatif |
| 3 | Netral |
| 4–5 | Positif |

## Metodologi

### 1. Text Preprocessing

Membersihkan dan menormalisasi teks melalui tahapan:

- Lowercasing.
- Penghapusan angka, emoji, dan tanda baca.
- Normalisasi kata tidak baku (*slangword normalization*).
- Penghapusan stopwords.
- Stemming bahasa Indonesia.
- Tokenisasi.

### 2. Exploratory Data Analysis (EDA)

Melakukan eksplorasi karakteristik ulasan melalui distribusi rating, panjang ulasan, distribusi sentimen, dan word cloud.

### 3. Feature Engineering

- **TF-IDF:** Mengubah teks menjadi representasi numerik untuk klasifikasi sentimen.
- **Bag-of-Words (CountVectorizer):** Merepresentasikan frekuensi kata sebagai input untuk model LDA.

### 4. Klasifikasi Sentimen dengan Naive Bayes

Menggunakan algoritma Multinomial Naive Bayes untuk mengklasifikasikan ulasan ke dalam tiga kategori sentimen. Performa model dievaluasi menggunakan accuracy, precision, recall, F1-score, dan confusion matrix.

### 5. Penanganan Imbalanced Data dengan SMOTE

Menerapkan Synthetic Minority Over-sampling Technique (SMOTE) pada data latih untuk meningkatkan representasi kelas minoritas. Data pengujian tidak mengalami oversampling agar evaluasi tetap menggunakan data asli.

### 6. Topic Modeling dengan LDA

Menggunakan Latent Dirichlet Allocation untuk mengidentifikasi topik utama secara terpisah pada sentimen positif, netral, dan negatif. Pemilihan jumlah topik dilakukan dengan mempertimbangkan coherence score.

### 7. Visualisasi Hasil

Menyajikan hasil melalui word cloud, bar plot kata dominan per topik, heatmap distribusi topik dan kata, serta visualisasi interaktif menggunakan pyLDAvis.

## Hasil dan Temuan

### Evaluasi Klasifikasi Sentimen

Model Naive Bayes setelah penerapan SMOTE menghasilkan akurasi sebesar **80%**.

| Metrik | Hasil |
|---|---:|
| Accuracy | 0,80 |
| Weighted F1-score | 0,82 |
| F1-score sentimen positif | 0,91 |
| F1-score sentimen negatif | 0,67 |
| F1-score sentimen netral | 0,11 |

Penerapan SMOTE meningkatkan macro average dari 0,50 menjadi 0,56. Meskipun demikian, sentimen netral masih sulit diklasifikasikan secara tepat, sehingga penanganan ketidakseimbangan kelas belum sepenuhnya menyelesaikan permasalahan klasifikasi.

### Hasil Topic Modeling

Model LDA menghasilkan lima topik untuk masing-masing kategori sentimen.

- **Sentimen positif:** Didominasi pembahasan mengenai kepuasan pengguna, kemudahan berbelanja, kepercayaan terhadap toko, promo, dan pengiriman.
- **Sentimen netral:** Banyak membahas informasi produk, waktu pengiriman, status pesanan, serta permintaan atau instruksi kepada penjual.
- **Sentimen negatif:** Didominasi keluhan terkait keterlambatan pengiriman, ketidaksesuaian barang, gangguan aplikasi, dan kualitas layanan.

Secara keseluruhan, aspek pengiriman dan layanan menjadi tema penting yang muncul dalam ulasan pengguna, terutama pada sentimen negatif.

## Tools dan Teknologi

- **Programming Language:** Python
- **Text Processing:** NLTK dan pustaka preprocessing bahasa Indonesia yang digunakan dalam notebook
- **Feature Engineering:** TF-IDF dan CountVectorizer
- **Machine Learning:** Scikit-learn, Multinomial Naive Bayes, dan SMOTE
- **Topic Modeling:** LDA dan Gensim
- **Visualization:** Matplotlib, WordCloud, Seaborn, dan pyLDAvis
- **Data Collection:** Web scraping Google Play Store

## Struktur Repository

- README.md: Dokumentasi proyek, metodologi, dan ringkasan hasil.
- Kelompok_6_PemrosesanTeks_Project.ipynb: Notebook berisi implementasi kode dan analisis.
- Data_pendukung_pemteks_kelompok6.zip: Arsip file pendukung yang digunakan dalam proses pemrosesan teks.

## Cara Menjalankan

1. Clone atau unduh repository ini.
2. Buka notebook menggunakan Google Colab atau Jupyter Notebook.
3. Siapkan dataset dan file pendukung preprocessing sesuai path yang digunakan dalam kode.
4. Instal pustaka yang dibutuhkan jika belum tersedia.
5. Jalankan notebook secara berurutan mulai dari preprocessing hingga klasifikasi sentimen, topic modeling, dan visualisasi.

## Keterbatasan

- Dataset terdiri atas 1.000 ulasan sehingga belum tentu merepresentasikan seluruh pengguna Shopee.
- Label sentimen ditentukan berdasarkan rating, yang tidak selalu sepenuhnya mencerminkan isi teks ulasan.
- Performa klasifikasi pada sentimen netral masih rendah.
- Interpretasi topik LDA bergantung pada kualitas preprocessing dan kata-kata dominan yang dihasilkan.

## Kontributor

- Putri Sofiyatus Salwa
- Nadine Putri Aulia
- Arya Abdi Wicaksana

# Clustering: Bank Customer Segmentation using RFM & K-Means Clustering
Bank customer segmentation using RFM and K-means Clustering

Link ke medium : https://kristalinaks.medium.com/clustering-bank-customer-segmentation-using-rfm-k-means-clustering-ongoing-f8ab23022b72

## 1. Background
Pada dasarnya, setiap bank memiliki jumlah nasabah (customer) yang besar dengan perilaku yang berbeda-beda. Untuk dapat memberikan layanan dan solusi terbaik bagi nasabah-nasabah tersebut perlu dilakukan segmentasi atau pengelompokan nasabah sesuai perilaku dan kebutuhannya masing-masing. Selain itu, segmentasi nasabah juga akan membantu bank dalam mengerahkan resource-nya secara efektif dan tepat sasaran.

Segmentasi nasabah ini akan dibuat dengan bantuan analisis RFM (Recency, Frequency, Monetary) dan K-means Clustering. Data yang digunakan adalah tanggal terakhir transaksi, frekuensi transaksi, dan jumlah nominal transaksi.

## 2. Dataset & Fitur
### 2.1. Deskripsi Dataset
Link: https://www.kaggle.com/datasets/shivamb/bank-customer-segmentation?resource=download

Dataset diambil dari kaggle.com yang berisi >1.000.000 transaksi dari >800.000 nasabah sebuah bank di India. Informasi yang terdapat dalam dataset ini antara lain yaitu usia, lokasi, jenis kelamin, saldo saat transaksi, detail transaksi, nominal transaksi, dsb.

## 2.2. Fitur yang Digunakan
Fitur yang digunakan dalam clustering ini adalah TransactionDate untuk mengukur Recency, TransactionID untuk mengukur Frequency, dan TransactionAmount untuk mengukur Monetary per CustomerID.

## 2.2. Preprocessing Dataset
Pada dataset ini dilakukan pula Preprocessing dengan membuang data nasabah yang hanya bertransaksi 1 kali dikarenakan perusahaan akan berfokus pada recurring customer. Selain itu, dilakukan pembersihan data outlier pada kolom Recency dan Monetary.

## 2.3. Normalization
Pada dataset ini dilakukan normalization dengan bantuan Min-Max Scaler untuk menyeragamkan rentang data. Dibuat pula ranking dari nilai Frequency untuk memudahkan operasi segmentasi dengan Rank Method.

## 3. Methods
Metode yang digunakan dalam segmentasi nasabah ini adalah RFM Analysis dan K-Means Clustering. Data nasabah akan diringkas menjadi 3 fitur yaitu recency, frequency, dan monetary. Ketiga fitur tersebut akan diolah dalam metode ranking dan K-Means Clustering menjadi beberapa segmen.

Jumlah segmen dalam metode ranking ditentukan sebanyak 5 segmen. Hal ini diambil dari asumsi bahwa perusahaan memiliki SDM yang cukup untuk memberikan perhatian pada 5 segmen nasabah.

Pada metode ranking, dilakukan pengelompokan Recency, Frequency, dan Monetary ke dalam beberapa kelompok. Batasan rentang nilai yang digunakan adalah 0.2, 0.4, 0.6, dan 0.8.

Pada metode K-Means Clustering, jumlah segmen akan ditentukan dari hasil analisis Elbow Method untuk mendapatkan jumlah segmen yang optimal.

## 4. Experiments/Results/Discussion
### 4.1. Metode Ranking
Dari metode ranking didapatkan RFM score sebagai berikut dari hasil pengelompokkan RFM berdasarkan rentang nilainya. Nama segment diberikan berdasarkan RFM score dengan kriteria berikut:

0–1 : “5. At Risk Customer”

1–2 : “4. Below Average Customer”

2–3: “3. Average Customer”

3–4: “2. Good Customer”

4–5: “1. Best Customer”

Semakin tinggi segmennya (angka segmen semakin kecil) maka nasabah tersebut cenderung memiliki recency yang kecil, frequency yang besar, dan monetary yang besar.

### 4.2. K-Means Clustering
Pada K-Means Clustering dilakukan elbow method untuk menentukan jumlah cluster yang optimum. Dari elbow method didapatkan siku terjadi di angka 3. Oleh karena itu, data akan dikelompokkan dalam 3 cluster. Berikut adalah centroid yang didapat dari ketiga cluster tersebut.

Dari hasil clustering, didapatkan 3 cluster (label 1,2,3). Dari hasil tersebut, diberikan nama segmen menurut labelnya.

Label 0 : “2. Average Customer”

Label 1 : “1. Best Customer”

Label 2 : “3. At Risk Customer”

Dari hasil clustering didapatkan karakteristik per segment sebagai berikut.

Best Customer : Recency sedang, Frequency tinggi, Monetary tinggi
Average Customer : Recency rendah (bagus), Frequency sedang, Monetary rendah
At Risk Customer : Recency tinggi (kurang bagus), Frequency rendah, Monetary sedang

## 5. Conclusion & Future Works
Dari kedua metode yang digunakan dalam segmentasi nasabah, diputuskan bahwa metode ranking lebih cocok karena lebih memiliki perbedaan yang jelas dan sesuai dengan SDM perusahaan.

Strategi yang bisa diterapkan untuk masing-masing segmen sesuai SDM perusahaan/bank yaitu sebagai berikut:

1. Best Customers
- di-maintain oleh Relationship Manager khusus tingkat pusat (termasuk kunjungan ke rumah/tempat usaha, dsb)
- mendapatkan rate khusus terbaik untuk berbagai transaksi seperti remittance, forex, dsb.
- dapat ditawarkan menjadi nasabah prioritas
- mendapatkan pelayanan wealth management skala besar
- mendapatkan apresiasi pada event-event tertentu
- menjadi perhatian bagi direksi

2. Good Customers
- di-maintain oleh Relationship Manager khusus tingkat wilayah (termasuk kunjungan ke rumah/tempat usaha, dsb)
- mendapatkan rate khusus untuk berbagai transaksi
- mendapatkan pelayanan wealth management skala sedang
- menjadi perhatian bagi kepala wilayah

3. Average Customers
- di-maintain oleh Relationship Manager tingkat cabang (termasuk kunjungan ke rumah/tempat usaha jika diperlukan)
- mendapatkan pelayanan terkait kebutuhan usaha atau investasi skala kecil
- menjadi perhatian bagi kepala cabang

4. Below Average Customers
- di-maintain oleh Solution Center via telepon
- pelayanan diberikan sesuai kebutuhan nasabah yang disampaikan via telepon

5. At Risk Customers
- pelayanan diberikan sesuai kebutuhan nasabah saat berkunjung ke cabang

Untuk future works, segmentasi bisa dilakukan dengan mempertimbangkan pengendapan dana, nilai investasi, dan nilai portofolio kredit. Selain itu, bisa dilakukan pembagian antara nasabah yang membutuhkan layanan wealth dengan nasabah yang membutuhkan layanan kredit/modal usaha.

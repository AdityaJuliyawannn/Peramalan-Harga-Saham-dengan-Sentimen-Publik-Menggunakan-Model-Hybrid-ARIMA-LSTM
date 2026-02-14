# Peramalan-Harga-Saham-dengan-Sentimen-Publik-Menggunakan-Model-Hybrid-ARIMA-LSTM
Studi Kasus: PT Bank Central Asia Tbk (BBCA)
==
Proyek ini mengimplementasikan peramalan harga saham menggunakan pendekatan statistik, deep learning, dan model hybrid, serta mengintegrasikan sentimen publik dari berita keuangan untuk meningkatkan akurasi prediksi.
--
📌 Deskripsi Proyek

Harga saham memiliki karakteristik kompleks yang mencakup pola linear dan nonlinear serta dipengaruhi oleh faktor eksternal seperti sentimen pasar. Model statistik tradisional seperti ARIMA efektif dalam menangkap pola linear, namun memiliki keterbatasan dalam memodelkan hubungan nonlinear. Sebaliknya, model deep learning seperti LSTM mampu mempelajari pola nonlinear dan dependensi jangka panjang.
Penelitian ini membandingkan lima model peramalan:
- ARIMA
- LSTM
- Hybrid ARIMA–LSTM
- LSTM dengan Sentimen
- Hybrid ARIMA–LSTM dengan Sentimen
Sentimen publik diperoleh dari berita keuangan dan dianalisis menggunakan model IndoRoBERTa, kemudian digunakan sebagai fitur tambahan dalam pemodelan.

📊 Dataset
#Data Harga Saham
- Sumber: Yahoo Finance
- Saham: BBCA (Bank Central Asia Tbk)
- Periode: Januari 2015 – Oktober 2025
- Frekuensi: Harian
- Variabel:
  Open
  High
  Low
  Close (target prediksi)
  Volume
Total data: 2.652 observasi
- Data Sentimen
- Sumber: Berita keuangan (Kompas, Detik, CNBC Indonesia)
- Periode: 2015–2025
- Tahapan:
Web scraping judul berita
Klasifikasi sentimen menggunakan IndoRoBERTa
Konversi menjadi skor probabilitas sentimen harian
Penyelarasan dengan tanggal data saham

⚙️ Metodologi
1. ARIMA
Digunakan untuk memodelkan pola linear pada data deret waktu.

2. LSTM
Digunakan untuk memodelkan pola nonlinear dan dependensi jangka panjang.

3. Hybrid ARIMA–LSTM
Pendekatan dua tahap:
ARIMA memodelkan komponen linear
Residual dari ARIMA digunakan sebagai input LSTM untuk mempelajari pola nonlinear
Prediksi akhir:
Prediksi Final = Prediksi ARIMA + Prediksi Residual LSTM

4. Integrasi Sentimen
Skor sentimen dari IndoRoBERTa digunakan sebagai fitur tambahan dalam model:
LSTM + Sentimen
ARIMA–LSTM + Sentimen
Sentimen membantu model memahami persepsi pasar yang tidak tercermin dalam data historis harga.

📏 Evaluasi Model
Metrik evaluasi yang digunakan:
MAE (Mean Absolute Error)
RMSE (Root Mean Square Error)
MAPE (Mean Absolute Percentage Error)

Pembagian data:
80% data latih
20% data uji

📈 Hasil Evaluasi
Model	MAE	RMSE	MAPE
ARIMA	902.89	656.24	7.58%
LSTM	803.20	844.42	8.74%
ARIMA–LSTM	275.95	362.23	2.92%
LSTM + Sentimen	165.19	207.22	1.81%
ARIMA–LSTM + Sentimen	288.21	355.60	3.06%

🛠️ Teknologi yang Digunakan
Python
TensorFlow / Keras
Statsmodels
Scikit-learn
Pandas
NumPy
Matplotlib
Yahoo Finance API
IndoRoBERTa (Transformer)
BeautifulSoup / Selenium (Web Scraping)

📂 Struktur Proyek
stock-forecasting-arima-lstm-sentiment/
│
├── data/
│   ├── stock_data.csv
│   ├── sentiment_data.csv
│
├── notebooks/
│   ├── preprocessing.ipynb
│   ├── arima_model.ipynb
│   ├── lstm_model.ipynb
│   ├── hybrid_model.ipynb
│   ├── sentiment_model.ipynb
│
├── models/
├── results/
└── README.md

👤 Penulis

Aditya Pratama Juliyawan
Departemen Matematika
Universitas Negeri Semarang

Email: adityajuliyawan@students.unnes.ac.id

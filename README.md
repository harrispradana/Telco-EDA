# Telco-EDA
Latihan melakukan Eploratory Data Analysis dengan menggunakan Python

## Data Yang Digunakan
* Sumber dataset: https://www.kaggle.com/blastchar/telco-customer-churn
* Dataset ini berisi informasi konsumen suatu perusahaan penyedia jasa telekomunikasi dalam suatu periode tertentu
* Terdapat 21 kolom dan 7043 baris dalam dataset ini
* Variabel yang ada di dalam dataset ini:
  * customerID: ID unik untuk setiap konsumen
  * gender: Jenis kelamin konsumen
  * SeniorCitizen: Indikator apakah usia konsumen lebih dari 65 tahun
  * Partner: Indikator apakah konsumen memiliki pasangan hidup
  * Dependents: Indikator apakah konsumen tinggal bersama orang yang ditanggung (tanggungan). Tanggungan dapat berupa anak, orang tua, kakek, nenek, dsb
  * tenure: Lama konsumen (dalam bulan) menggunakan layanan dari perusahaan
  * PhoneService: Indikator apakah konsumen menggunakan layanan telepon yang ditawarkan oleh perusahaan
  * MultipleLines: Indikator apakah konsumen menggunakan lebih dari satu jaringan telepon
  * InternetService: Indikator apakah konsumen menggunakan layanan internet yang ditawarkan oleh perusahaan dan jenis layanan internet yang digunakan
  * OnlineSecurity: Indikator apakah konsumen menggunakan layanan tambahan keamanan online yang ditawarkan oleh perusahaan
  * OnlineBackup: Indikator apakah konsumen menggunakan layanan tambahan pencadangan data online yang ditawarkan oleh perusahaan
  * DeviceProtection: Indikator apakah konsumen menggunakan layanan tambahan perlindungan perangkat internet yang ditawarkan oleh perusahaan
  * TechSupport: Indikator apakah konsumen menggunakan layanan tambahan dukungan teknis dengan waktu tunggu yang dipersingkat yang ditawarkan oleh perusahaan
  * StreamingTV: Indikator apakah konsumen menggunakan layanan internet yang digunakan untuk melakukan streaming TV dari jasa pihak ketiga
  * StreamingMovies: Indikator apakah konsumen menggunakan layanan internet yang digunakan untuk melakukan streaming film dari jasa pihak ketiga
  * Contract: Indikator jenis kontrak yang digunakan konsumen untuk berlangganan layanan
  * PaperlessBilling: Indikator apakah konsumen memilih menggunakan tagihan tanpa kertas atau tidak
  * PaymentMethod: Indikator bagaimana konsumen membayar tagihan mereka
  * MonthlyCharges: Jumlah tagihan bulanan yang harus dibayarkan oleh konsumen
  * TotalCharges: Jumlah total tagihan yang akan dibayar oleh konsumen sampai dengan akhir kuartal periode tertentu
  * Churn: Indikator apakah konsumen memilih untuk berhenti berlangganan (churn) pada kuartal ini


## Perangkat Analisis Yang Digunakan
Google Colab
* Python 3.7.12
* Python Packages:
  * Pandas
  * Numpy
  * Matplotlib
  * Seaborn
  * String


## Membersihkan Data
* Terdapat 11 missing value dalam bentuk whitespace pada kolom TotalCharges. Karena perhitungan untuk menghitung TotalCharges tidak diketahui, maka semua baris yang terdapat missing value dihapus
* Mengubah tipe data pada kolom TotalCharges yang sebelumnya bertipe data 'object' menjadi 'float'
* Tidak terdapat duplikasi data dalam dataset

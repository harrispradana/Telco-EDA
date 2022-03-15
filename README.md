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


## Basic EDA
Dalam melakukan basic EDA, kolom-kolom yang ada dalam dataset dibagi menjadi 2 berdasarkan tipe data yang ada di dalamnya yaitu numerik dan string. Kolom yang masuk ke dalam kelompok numerik adalah: 
 * tenure 
 * MonthlyCharges
 * Total Charges

Sedangkan kolom dengan tipe data string adalah:
 * gender
 * SeniorCitizen
 * Partner
 * Dependents
 * PhoneService
 * MultipleLines
 * InternetService
 * OnlineSecurity
 * OnlineBackup
 * DeviceProtection
 * TechSupport
 * StreamingTV
 * StreamingMovies
 * Contract
 * PaperlessBilling
 * PaymentMethod
 * Churn

Yang perlu diperhatikan adalah, untuk kolom customerID tidak dimasukkan ke dalam analisis karena hanya berisi informasi id pelanggan dan untuk kolom SeniorCitizen walaupun datanya berbentuk numerik (0 dan 1) tapi informasi data tersebut berupa informasi kategorik (0 untuk bukan usia senior dan 1 untuk usia senior) sehingga dimasukkan ke dalam kelompok kolom string.

### Analisis Univariate
Kesimpulan yang didapat dari hasil analisis univariate kolom numerik adalah:
* Rata-rata lama berlangganan dari seluruh user adalah 32.42 bulan dengan nilai median 29 bulan
* Rata-rata tagihan bulanan dari seluruh user adalah 64.80 dengan nilai median 70.35
* Rata-rata total tagihan dari seluruh user adalah 2283.30 dengan nilai median 1397.48
* Tidak terdapat outlier untuk kolom numerik (tenure, MonthlyCharges, dan TotalCharges)

Kesimpulan yang didapat dari hasil analisis univariate kolom string adalah:
* Jumlah user berimbang antara user dengan jenis kelamin pria dan perempuan
* Mayoritas user (83.75%) merupakan kelompok usia dibawah 65 tahun
* Jumlah user yang memiliki pasangan dengan yang tidak memiliki pasangan memiliki jumlah yang berimbang
* Mayoritas user (70.15%) masuk ke dalam kelompok yang tidak tinggal bersama tanggungan (anak, orang tua, kakek, nenek, dsb)
* Mayoritas user (90.32%) menggunakan layanan telepon yang ditawarkan
* Dari 6352 user yang menggunakan layanan telepon, sebanyak 46.8% user menggunakan lebih dari satu jaringan telepon
* Layanan internet yang paling populer adalah layanan internet berbasis fiber optik (56.1%)
* Layanan tambahan berupa keamanan online, pencadangan online, perlindungan perangkat, dan dukungan teknis kurang populer
* Jumlah user yang melakukan streaming TV dengan yang tidak cukup berimbang
* Jumlah user yang melakukan streaming film dengan yang tidak cukup berimbang
* Metode pembayaran yang paling populer adalah cek elektronik (33.6%)
* Jenis kontrak yang paling populer adalah kontrak per bulan (55%)
* Jenis tagihan yang paling populer adalah tagihan tanpa kertas (59.2%)
* Persentase user yang masih melanjutkan menggunakan layanan yang ditawarkan adalah sebesar 73.4%

### Analisis Bivariate
Kesimpulan yang didapat dari analisis bivariate adalah:
* Jika user yang berhenti berlangganan (churn) dilihat berdasarkan beberapa kategori, ada 5 kategori yang perlu menjadi perhatian yaitu usia user, tanggungan, layanan internet yang digunakan, kontrak, dan metode pembayaran
* Berdasarkan median datanya, kelompok user yang berhenti berlangganan memiliki tagihan bulanan yang lebih tinggi dibanding dengan user yang masih melanjutkan berlangganan
* Layanan internet berbasis fiber optik memiliki median tagihan paling tinggi jika dibandingkan dengan layanan internet DSL dan tanpa layanan internet
* Layanan telepon memiliki median tagihan yang lebih tinggi jika dibandingkan dengan tanpa layanan telepon
* Streaming TV dan film lebih populer pada kelompok user usia senior dan kelompok user yang tinggal bersama tanggungan
* Kelompok user yang menggunakan layanan telepon dan kelompok user yang tidak menggunakan layanan telepon memiliki karakteristik lama berlangganan yang hampir sama
* Kelompok user yang menggunakan layanan internet fiber optik dan kelompok user yang menggunakan layanan internet DSL memiliki karakteristik lama berlangganan yang hampir sama


## Pemahaman Bisnis
* Dari data yang ada dalam dataset ini, maka pertanyaan terkait kegiatan bisnis perusahaan yang dapat ditanyakan adalah:
  * Apakah konsumen yang menggunakan seluruh layanan yang ditawarkan lebih loyal?
  * Pada konsumen yang melakukan streaming, bagaimana karakteristiknya?
    * Jenis streaming apa yang lebih populer berdasarkan gender dan usia?
    * Apa jenis streaming yang lebih populer berdasarkan tanggungan?
    * Kegiatan streaming apa yang secara keseluruhan lebih populer?
    * Bagaimana perbandingan jumlah konsumen yang hanya melakukan salah satu streaming (TV atau film) dengan konsumen yang melakukan keduanya?
    * Bagaimana perbandingan jumlah konsumen yang melakukan streaming (TV, film, dan keduanya) terhadap konsumen yang tidak melakukan streaming?
  * Bagaimana karekteristik konsumen yang memutuskan untuk berhenti berlangganan?
    * Berapa rata-rata tagihan bulanan, median tagihan bulanan, standar deviasi tagihan bulanan, dan rata-rata lama berlangganan berdasarkan konsumen yang berhenti berlangganan?
    * Apa metode pembayaran yang paling banyak digunakan jika dilihat berdasarkan layanan internet yang digunakan dan user yang berhenti berlangganan?
    * Berapa jumlah user yang berhenti berlangganan berdasarkan tanggungan dan layanan internet?
    * Berapa jumlah user yang berhenti berlangganan berdasarkan usia dan layanan internet?
    * Berapa jumlah user yang berhenti berlangganan berdasarkan kontrak dan layanan internet?
    * Berapa rata-rata tagihan per bulan, rata-rata lama berlangganan user, dan jumlah user jika dikelompokkan berdasarkan layanan internet yang digunakan dan user yang berhenti berlangganan?


## Analisis Mendalam (Deep Dive Analysis)

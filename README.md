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
* Rata-rata lama berlangganan dari seluruh konsumen adalah 32.42 bulan dengan nilai median 29 bulan
* Rata-rata tagihan bulanan dari seluruh konsumen adalah 64.80 dengan nilai median 70.35
* Rata-rata total tagihan dari seluruh konsumen adalah 2283.30 dengan nilai median 1397.48
* Tidak terdapat outlier untuk kolom numerik (tenure, MonthlyCharges, dan TotalCharges)

Kesimpulan yang didapat dari hasil analisis univariate kolom string adalah:
* Jumlah konsumen berimbang antara konsumen dengan jenis kelamin pria dan perempuan
* Mayoritas konsumen (83.75%) merupakan kelompok usia dibawah 65 tahun
* Jumlah konsumen yang memiliki pasangan dengan yang tidak memiliki pasangan memiliki jumlah yang berimbang
* Mayoritas konsumen (70.15%) masuk ke dalam kelompok yang tidak tinggal bersama tanggungan (anak, orang tua, kakek, nenek, dsb)
* Mayoritas konsumen (90.32%) menggunakan layanan telepon yang ditawarkan
* Dari 6352 konsumen yang menggunakan layanan telepon, sebanyak 46.8% konsumen menggunakan lebih dari satu jaringan telepon
* Layanan internet yang paling populer adalah layanan internet berbasis fiber optik (56.1%)
* Layanan tambahan berupa keamanan online, pencadangan online, perlindungan perangkat, dan dukungan teknis kurang populer
* Jumlah konsumen yang melakukan streaming TV dengan yang tidak cukup berimbang
* Jumlah konsumen yang melakukan streaming film dengan yang tidak cukup berimbang
* Metode pembayaran yang paling populer adalah cek elektronik (33.6%)
* Jenis kontrak yang paling populer adalah kontrak per bulan (55%)
* Jenis tagihan yang paling populer adalah tagihan tanpa kertas (59.2%)
* Persentase konsumen yang masih melanjutkan menggunakan layanan yang ditawarkan adalah sebesar 73.4%

### Analisis Bivariate
Kesimpulan yang didapat dari analisis bivariate adalah:
* Jika konsumen yang berhenti berlangganan (churn) dilihat berdasarkan beberapa kategori, ada 5 kategori yang perlu menjadi perhatian yaitu usia konsumen, tanggungan, layanan internet yang digunakan, kontrak, dan metode pembayaran
* Berdasarkan median datanya, kelompok konsumen yang berhenti berlangganan memiliki tagihan bulanan yang lebih tinggi dibanding dengan konsumen yang masih melanjutkan berlangganan
* Layanan internet berbasis fiber optik memiliki median tagihan paling tinggi jika dibandingkan dengan layanan internet DSL dan tanpa layanan internet
* Layanan telepon memiliki median tagihan yang lebih tinggi jika dibandingkan dengan tanpa layanan telepon
* Streaming TV dan film lebih populer pada kelompok konsumen usia senior dan kelompok konsumen yang tinggal bersama tanggungan
* Kelompok konsumen yang menggunakan layanan telepon dan kelompok konsumen yang tidak menggunakan layanan telepon memiliki karakteristik lama berlangganan yang hampir sama
* Kelompok konsumen yang menggunakan layanan internet fiber optik dan kelompok konsumen yang menggunakan layanan internet DSL memiliki karakteristik lama berlangganan yang hampir sama


## Pemahaman Bisnis
* Dari data yang ada dalam dataset ini, maka pertanyaan terkait kegiatan bisnis perusahaan yang dapat ditanyakan adalah:
  * Apakah konsumen yang menggunakan seluruh layanan yang ditawarkan lebih loyal?
  * Pada konsumen yang melakukan streaming, bagaimana karakteristiknya?
    * Kegiatan streaming apa yang secara keseluruhan lebih populer?
    * Bagaimana perbandingan jumlah konsumen yang melakukan streaming (TV, film, dan keduanya) terhadap konsumen yang tidak melakukan streaming?
  * Bagaimana karekteristik konsumen yang memutuskan untuk berhenti berlangganan?
    * Berapa rata-rata tagihan bulanan, median tagihan bulanan, standar deviasi tagihan bulanan, dan rata-rata lama berlangganan berdasarkan konsumen yang berhenti berlangganan?
    * Apa metode pembayaran yang paling banyak digunakan jika dilihat berdasarkan layanan internet yang digunakan dan konsumen yang berhenti berlangganan?
    * Berapa jumlah konsumen yang berhenti berlangganan berdasarkan tanggungan dan layanan internet?
    * Berapa jumlah konsumen yang berhenti berlangganan berdasarkan usia dan layanan internet?
    * Berapa jumlah konsumen yang berhenti berlangganan berdasarkan kontrak dan layanan internet?
    * Berapa rata-rata tagihan per bulan, rata-rata lama berlangganan konsumen, dan jumlah konsumen jika dikelompokkan berdasarkan layanan internet yang digunakan dan konsumen yang berhenti berlangganan?


## Analisis Mendalam (Deep Dive Analysis)
Analisis mendalam dilakukan untuk menjawab pertanyaan-pertanyaan yang ada pada bagian pemahaman bisnis dengan melakukan analisis deskriptif dengan bantuan fitur groupby dan aggregate dari Python.

### Menambah Variabel
Penambahan variabel ini dilakukan untuk memberikan informasi tambahan yang dapat digunakan untuk melakukan analisis setelahnya. Data yang digunakan untuk mengisi variabel baru ini bersumber dari variabel yang sebelumnya sudah ada di dataset. Variabel-variabel baru tersebut adalah:
 * Internet: kolom boolean yang memberikan informasi apakah konsumen menggunakan layanan internet (baik berbasis DSL atau fiber optik) atau tidak
 * Streaming: kolom boolean yang memberikan informasi apakah konsumen menggunakan setidaknya salah satu layanan streaming (TV atau film)
 * StreamingAll: kolom boolean yang memberikan informasi apakah konsumen menggunakan layanan streaming TV dan film secara bersamaan
 * StreamTV: merupakan kolom boolean yang memberikan informasi apakah konsumen melakukan streaming TV 
 * StreamMov: merupakan kolom boolean yang memberikan informasi apakah konsumenr melakukan streaming film
 * CompletePack: adalah kolom boolean yang memberikan informasi apakah konsumen menggunakan seluruh layanan yang ditawarkan

### Analisis Deskriptif
* Apakah konsumen yang menggunakan seluruh layanan yang ditawarkan lebih loyal?

![image](https://user-images.githubusercontent.com/97722405/158360886-07ea4783-b294-4671-b5cf-ec9950c5d28a.png)

![image](https://user-images.githubusercontent.com/97722405/158364081-6d5ccb40-d1ad-4548-8b3b-f921e20817c1.png)

Dari hasil data di atas dapat diketahui bahwa **loyalitas konsumen yang menggunakan seluruh layanan lebih baik dibanding konsumen yang hanya menggunakan beberapa layanan**. Hal ini dapat dilihat dari persentase konsumen yang masih melanjutkan berlangganan pada kelompok konsumen yang menggunakan seluruh layanan mencapai 94.9%, sedangkan pada konsumen yang melanjutkan berlangganan pada kelompok tidak menggunakan seluruh layanan hanya sebesar 69.3%.

Selain itu, rata-rata lama berlangganan konsumen yang menggunakan seluruh layanan mencapai 60.7 bulan sedangkan untuk konsumen yang tidak menggunakan seluruh layanan nilainya hanya 30.9 bulan.

* Pada konsumen yang melakukan streaming, bagaimana karakteristiknya?
  * Kegiatan streaming apa yang secara keseluruhan lebih populer?

![image](https://user-images.githubusercontent.com/97722405/158363618-84eff28d-4345-4b1b-b11d-a483ffbcfa72.png)


   Mayoritas konsumen yang melakukan streaming melakukan kedua layanan streaming tersebut (TV dan film). Terdapat 3495 konsumen yang menggunakan layanan streaming (streaming TV, streaming film, atau keduanya). Sebanyak 55.48% konsumen menggunakan kedua layanan streaming secara bersamaan, 22.66% konsumen hanya menggunakan layanan streaming film, dan 21.86% hanya menggunakan layanan streaming TV
  * Bagaimana perbandingan jumlah konsumen yang melakukan streaming (TV, film, dan keduanya) terhadap konsumen yang tidak melakukan streaming?
  
  ![image](https://user-images.githubusercontent.com/97722405/158363902-14c721f9-ebad-458d-894a-852edd5bc623.png)

  
   Dari 3495 konsumen yang melakukan streaming. Nilai tersebut setara dengan 63.41% dari kelompok konsumen yang menggunakan layanan internet (5512 konsumen layanan internet) atau 49.7% dari total konsumen (7032 total konsumen). Sehingga dapat disimpulkan pada kelompok konsumen yang menggunakan layanan internet, mayoritas melakukan kegiatan streaming
     
* Bagaimana karekteristik konsumen yang memutuskan untuk berhenti berlangganan?
  * Berapa rata-rata tagihan bulanan, median tagihan bulanan, standar deviasi tagihan bulanan, dan rata-rata lama berlangganan berdasarkan konsumen yang berhenti berlangganan?

![image](https://user-images.githubusercontent.com/97722405/158394266-5cdd307c-9a0f-4a11-adc4-2450dab1000a.png)

  Dari hasil di atas dapat diketahui bahwa secara rata-rata dan median, tagihan bulanan kelompok konsumen yang berhenti berlangganan lebih tinggi jika dibandingkan dengan kelompok konsumen yang melanjutkan berlangganan. Selain itu nilai standar deviasi kelompok konsumen yang berhenti berlangganan yang lebih kecil menunjukkan bahwa sebaran nilai tagihan bulanan dalam kelompok tersebut semakin dekat dengan rata-rata nya

  Sedangkan dari rata-rata- lama berlangganan, kelompok konsumenyang berhenti berlangganan memiliki rata-rata lama berlangganan yang lebih rendah dibanding dengan kelompok konsumen yang melanjutkan berlangganan
   
  * Apa metode pembayaran yang paling banyak digunakan jika dilihat berdasarkan layanan internet yang digunakan dan konsumen yang berhenti berlangganan?
  
    ![image](https://user-images.githubusercontent.com/97722405/158488095-3b6c5232-e4f5-455a-9ac0-361f483a9fdb.png)
    
    ![image](https://user-images.githubusercontent.com/97722405/158488155-e8995461-2eda-41e5-a9e1-172dd6ef34ab.png)

  Dari hasil di atas dapat diketahui bahwa pada kelompok konsumen yang berhenti berlangganan, jika dibagi berdasarkan metode pembayaran dan layanan internet yang digunakan 3 dari 4 kategori metode pembayaran didominasi oleh konsumen yang menggunakan layanan internet berbasis fiber optik. Ketiga kategori tersebut adalah transfer bank (72.5% adalah konsumen fiber optik), kemudian kartu kredit (65% adalah konsumen fiber optik), dan terakhir cek elektronik (79.3%). Sedangkan pada kategori cek yang dikirim melalui surat didominasi oleh konsumen yang menggunakan internet DSL (41.2%) namun konsumen internet fiber optik juga memiliki persentase yang tinggi (35.7%).
   
  * Berapa jumlah konsumen yang berhenti berlangganan berdasarkan tanggungan dan layanan internet
    
    ![image](https://user-images.githubusercontent.com/97722405/158488321-7e0ea5a6-0a4a-432c-8351-528267833952.png)
   
  Dari data di atas dapat dilihat bahwa konsumen yang berhenti berlangganan lebih dipengaruhi oleh layanan internet yang digunakan. Hal ini bisa dilihat pada kelompok konsumen yang berhenti berlangganan yang tidak tinggal bersama tanggungan dan kelompok konsumen yang berhenti berlangganan yang tinggal bersama tanggungan, kedua kelompok ini didominasi oleh konsumen yang menggunakan layanan internet fiber optik. Pada kelompok konsumen yang berhenti berlangganan yang tidak tinggal bersama tanggungan, sebanyak 71% menggunakan layanan internet fiber optik. Pada kelompok konsumen yang berhenti berlangganan yang tinggal bersama tanggungan, sebanyak 62% menggunakan layanan internet fiber optik

  * Berapa jumlah konsumen yang berhenti berlangganan berdasarkan usia dan layanan internet?
  
    ![image](https://user-images.githubusercontent.com/97722405/158488562-fd298c59-e35a-4e5a-ba3f-b19d3f4c42ed.png)
  
  Dari data di atas dapat dilihat bahwa konsumen yang berhenti berlangganan lebih dipengaruhi oleh layanan internet yang digunakan. Hal ini bisa dilihat pada kelompok konsumen yang berusia senior dan berhenti berlangganan serta kelompok konsumen yang berusia bukan senior dan berhenti berlangganan, kedua kelompok ini didominasi oleh konsumen yang menggunakan layanan internet fiber optik. Pada kelompok konsumen usia senior dan memilih berhenti berlangganan, sebanyak 82.7% konsumen menggunakan layanan internet berbasis fiber optik. Pada kelompok konsumen usia bukan senior dan memilih berhenti berlangganan, sebanyak 65% konsumen menggunakan layanan internet berbasis fiber optik

  * Berapa jumlah konsumen yang berhenti berlangganan berdasarkan kontrak dan layanan internet?
    
    ![image](https://user-images.githubusercontent.com/97722405/158488916-544f518a-045c-4076-ad8e-a34280773edf.png)
    
  Dari data di atas dapat dilihat bahwa konsumen yang berhenti berlangganan lebih dipengaruhi oleh layanan internet yang digunakan. Hal ini bisa dilihat pada kelompok konsumen yang berhenti berlangganan yang terikat kontrak per bulan, kelompok konsumen yang berhenti berlangganan yang terikat kontrak 1 tahun, dan kelompok konsumen yang berhenti berlangganan yang terikat kontrak 2 tahun, ketiga kelompok ini didominasi oleh konsumen yang menggunakan layanan internet fiber optik. Pada kelompok konsumen yang terikat kontrak per bulan dan berhenti berlangganan, sebanyak 70.2% konsumen merupakan pengguna layanan internet fiber optik. Pada kelompok konsumen yang terikat kontrak 1 tahun dan berhenti berlangganan, sebanyak 62.6% konsumen merupakan pengguna layanan internet fiber optik. Pada kelompok konsumen yang terikat kontrak 2 tahun dan berhenti berlangganan, sebanyak 64.6% konsumen merupakan pengguna layanan internet fiber optik

  * Berapa rata-rata tagihan per bulan, rata-rata lama berlangganan konsumen, dan jumlah konsumen jika dikelompokkan berdasarkan layanan internet yang digunakan dan konsumen yang berhenti berlangganan?
    
    ![image](https://user-images.githubusercontent.com/97722405/158489074-8906ad31-46b9-40a8-90f3-1ec49846fa2e.png)

  Dari hasil di atas, informasi yang didapatkan adalah:
    * Jika dikelompokkan berdasarkan layanan internet yang digunakan dan konsumen yang berhenti berlangganan, konsumen yang masih melanjutkan menggunakan layanan yang ditawarkan memiliki rata-rata dan median tagihan bulanan lebih tinggi dibanding dengan konsumen yang telah berhenti berlangganan
    * Jika dikelompokkan berdasarkan layanan internet yang digunakan dan konsumen yang berhenti berlangganan, konsumen yang masih melanjutkan menggunakan layanan yang ditawarkan memiliki rata-rata lama langganan yang lebih lama jika dibandingkan dengan konsumen yang telah berhenti berlangganan
    * Jika dikelompokkan berdasarkan layanan internet yang digunakan, mayoritas konsumen yang berhenti berlangganan (69.4%) merupakan konsumen yang menggunakan layanan internet fiber optik

  Adanya perbedaan hasil dengan analisa sebelumnya, dimana kelompok konsumen yang berhenti berlangganan secara keseluruhan memiliki nilai median dan rata-rata tagihan bulanan lebih tinggi dapat dijelaskan oleh distribusi data yang digunakan untuk melakukan analisis. Pada analisis sebelumnya, data hanya dibagi berdasarkan 1 kategori saja yaitu konsumen yang berhenti berlangganan atau konsumen yang melanjutkan berlangganan.

  Sedangkan pada analisis ini selain dibagi berdasarkan konsumen yang berhenti berlangganan atau konsumen yang melanjutkan berlangganan, data juga dibagi lagi dengan layanan internet yang digunakan. Jika melihat data jumlah konsumen hasil pembagian tersebut dapat dilihat ada perbedaan distribusi data jika dibagi berdasarkan dengan layanan internet yang digunakan.

  Pada kelompok konsumen yang melanjutkan berlangganan dan dibagi berdasarkan layanan internet yang digunakan, sebaran konsumen yang menggunakan layanan internet DSL, internet fiber optik, dan tidak menggunakan layanan internet cenderung lebih merata dengan nilai persentase sebesar 37.9% untuk layanan internet DSL, 34.8% untuk layanan internet fiber optik, dan 27.3% untuk yang tidak menggunakan internet. Hal ini juga didukung oleh hasil analisa sebelumnya dimana nilai standar deviasi tagihan bulanan kelompok konsumen yang melanjutkan berlangganan (31.09) lebih tinggi dibanding kelompok konsumen yang berhenti berlangganan (24.66) yang menunjukkan pada kelompok konsumen yang melanjutkan berlangganan nilai datanya cenderung lebih tersebar menjauh dari nilai rata-ratanya.

  Sedangkan pada kelompok konsumen yang berhenti berlangganan, sebaran konsumen yang menggunakan layanan internet DSL, internet fiber optik, dan tidak menggunakan layanan internet cenderung lebih terpusat pada kelompok konsumen yang menggunakan layanan internet fiber optik. Komposisi sebaran data pada kelompok konsumen yang berhenti berlangganan adalah 69.4% untuk layanan internet fiber optik, 24.6% untuk layanan internet DSL, dan 6% untuk tidak menggunakan layanan internet. Hal ini menyebabkan nilai data pada kelompok ini cenderung lebih mendekati nilai rata-ratanya.

## Kesimpulan dan Rekomendasi
### Kesimpulan
* Dengan melihat persentase konsumen yang berhenti berlangganan dan rata-rata lama berlangganan, kelompok konsumen yang menggunakan seluruh layanan yang ditawarkan lebih loyal dibanding kelompok konsumen yang hanya menggunakan beberapa layanan
* Mayoritas konsumen (63.41%) yang menggunakan layanan internet melakukan kegiatan streaming
  * Mayoritas konsumen (55.48%) yang melakukan streaming menggunakan kedua jenis layanan (TV dan film)
* Secara keseluruhan, terdapat 1869 (26.6%) konsumen yang berhenti berlangganan dan mayoritas didominasi kelompok konsumen yang menggunakan internet fiber optik
  * Mayoritas konsumen yang berhenti berlangganan (69.4%) merupakan konsumen pengguna layanan internet berbasis fiber optik
  * Tingginya jumlah konsumen layanan internet berbasis fiber optik yang berhenti berlangganan menyebabkan secara keseluruhan, nilai rata-rata tagihan bulanan kelompok konsumen yang berhenti berlangganan lebih tinggi dibandingkan dengan konsumen yang melanjutkan berlangganan
  * Banyaknya konsumen layanan internet fiber optik yang berhenti berlangganan juga menyebabkan pada kategori dan sub-kategori yang lain menjadi bias karena seolah-olah pada kategori dan sub-kategori tersebut terdapat banyak konsumen yang berhenti berlangganan
  * Oleh karena itu konsumen yang menggunakan layanan internet berbasis fiber optik perlu memiliki perhatian khusus. Hal ini dikarenakan karakteristik konsumen pada kelompok tersebut memiliki tagihan per bulan yang tinggi jika dibandingkan dengan konsumen dari kelompok lain (konsumen layanan internet DSL dan konsumen yang tidak menggunakan layanan internet), namun tingkat loyalitas konsumen layanan fiber optik termasuk rendah (41.9% konsumen tidak melanjutkan berlangganan)

### Rekomendasi
* Diduga ada masalah dalam produk layanan internet fiber optik yang ditawarkan jika melihat tingginya jumlah konsumen produk tersebut yang memutuskan untuk berhenti berlangganan. Untuk itu disarankan kepada tim teknis terkait untuk melakukan evaluasi terhadap produk tersebut
* Tingginya loyalitas konsumen yang menggunakan seluruh layanan yang ditawarkan perlu diberi apresiasi sebagai bentuk pengakuan atas loyalitas mereka. Hal ini dapat berupa cinderamata, potongan harga, atau poin loyalitas yang dapat ditukar dengan sesuatu
* Populernya kegiatan streaming yang dilakukan oleh konsumen yang menggunakan layanan internet bisa menjadi peluang bagi perusahaan untuk bekerja sama dengan penyedia jasa streaming (misalnya dalam bentuk bundling paket internet dan paket berlangganan streaming) dengan tujuan untuk meningkatkan loyalitas konsumen yang sudah ada saat ini dan sebagai sarana untuk mendapatkan konsumen baru

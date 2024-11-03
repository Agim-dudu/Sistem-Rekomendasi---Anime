# Laporan Proyek Machine Learning - M. Gymnastiar

## Project Overview

![anime](https://www.hindustantimes.com/ht-img/img/2023/07/17/1600x900/anime_collage_1686917525783_1689613937349.webp)

Di era perkembangan digital saat ini, orang-orang semakin mudah mengakses berbagai informasi, baik yang bermanfaat untuk memperluas pengetahuan maupun untuk hiburan, salah satunya adalah anime [(_Wibowo et al., 2020_)](https://ieeexplore.ieee.org/abstract/document/9315363/). Anime adalah istilah yang digunakan untuk menyebut animasi atau gambar yang dibuat di Jepang, memiliki gaya visual yang khas dibandingkan dengan animasi dari negara lain. Ciri-ciri anime sering kali meliputi mata yang besar, mulut yang kecil, dan hidung yang lebih ramping. Anime dapat berupa komik atau ilustrasi, serta video dengan durasi sekitar 24 menit per episode [(_Aisyah et al., 2019_)](https://repository.uinjkt.ac.id/dspace/handle/123456789/45316). Popularitas anime semakin meluas di luar Jepang, terbukti dari banyaknya judul anime yang tersedia di platform terkenal seperti Netflix, Amazon Prime, dan Google Play [(_Aisyah et al.,2019_)](https://repository.uinjkt.ac.id/dspace/handle/123456789/45316). 
Selain itu, berbagai acara pameran seperti Anime Expo, Anime Matsuri, dan Comic Fest juga menunjukkan tingginya popularitas anime di kalangan penggemarnya [(_Jayaperwira et al., 2023_)](https://openlibrarypublications.telkomuniversity.ac.id/index.php/engineering/article/view/20612). Pada tahun 2021, tercatat ada 18.350 anime yang telah dirilis, termasuk yang masih berjalan maupun yang sudah selesai. Anime mencakup beragam genre, seperti shojo yang ditujukan untuk penonton wanita dan shonen untuk pria. Banyaknya pilihan genre ini sering membuat penonton bingung dalam menentukan anime yang sesuai dengan preferensi mereka. Oleh karena itu, dibutuhkan sebuah sistem rekomendasi yang dapat membantu pengguna menemukan anime yang ingin mereka tonton [(_Permadi & Raharjo, 2023_)](https://sistemasi.ftik.unisi.ac.id/index.php/stmsi/article/view/2473).

## Business Understanding

Pengembangan sistem rekomendasi anime memiliki potensi besar untuk memberikan berbagai keuntungan bagi pengguna dan platform streaming anime. Sistem ini dapat mempermudah pengguna dalam menemukan anime yang sesuai dengan selera mereka secara lebih efisien, serta membantu platform dalam meningkatkan keterlibatan pengguna, kepuasan pelanggan, dan efisiensi operasional [(_Roziqiin & Faisal, 2024_)](http://www.jurnal.stkippgritulungagung.ac.id/index.php/jipi/article/view/4222)

### Problem Statements

- Bagaimana cara membuat sistem rekomendasi anime yang merekomendasikan pengguna berdasarkan genre anime?
- Dengan menggunakan data rating yang dimiliki pengguna, bagaimana perusahaan jasa streaming dapat merekomendasikan anime yang belum pernah ditonton pengguna?
- Bagaimana cara membangun model sistem rekomendasi menggunakan pendekatan (content-based filtering) dengan Cosine Similiarity dan (Collaborative Filtering) model based Deep learning?
- Bagaimana cara mengukur performa model sistem rekomendasi yang telah dibangun?

### Goals

Untuk menjawab problem statements di atas, project memiliki goals sebagai berikut:

- Menghasilkan rekomendasi anime sebanyak Top-N Rekomendasi kepada pengguna berdasarkan genre.
- Menghasilkan rekomendasi anime yang sesuai dengan preferensi pengguna dan belum pernah ditonton. 
- Membangun model sistem rekomendasi menggunakan pendekatan (content-based filtering) dengan Cosine Similiarity dan (Collaborative Filtering) model based Deep learning berdasarkan fitur yang telah dipilih dari dataset.
- Mengukur performa model sistem rekomendasi menggunakan metrik evaluasi yang sesuai. 

### Solution statements

Untuk mencapai goals di atas, berikut adalah pendekatan algoritma yang akan digunakan dalam pengembangan sistem rekomendasi anime:

- Content-Based Filtering menggunakan Cosine Similarity 
  pendekatan ini akan merekomendasikan anime kepada pengguna berdasarkan kesamaan fitur genre. Cosine Similarity akan digunakan untuk mengukur seberapa mirip satu anime dengan anime lain berdasarkan representasi vektornya.

- Collaborative Filtering menggunakan model based Deep learning
  pendekatan ini akan memanfaatkan data rating dari pengguna lain untuk memberikan rekomendasi anime. Dengan menggunakan Deep Learning, sistem akan mencari pengguna dengan pola rating yang mirip dan merekomendasikan anime yang disukai oleh pengguna-pengguna tersebut.

- Pembangunan Model menggunakan pendekatan yang Dipilih
  dalam fase ini, model sistem rekomendasi akan dibangun menggunakan (content-based filtering) dengan Cosine Similiarity dan (Collaborative Filtering) model based Deep learningberdasarkan fitur yang telah dipilih dari dataset. Proses ini meliputi pemilihan fitur yang relevan dan penerapan algoritma yang telah ditentukan.

- Evaluasi Performa Model 
  setelah model dibangun, evaluasi performa akan dilakukan menggunakan metrik seperti Precision dan Root Mean Squared Error. Ini akan memberikan wawasan tentang efektivitas model dalam merekomendasikan anime yang relevan kepada pengguna.

## Data Understanding

Pada project yg dibuat ini dataset diambil dari situs repository terbuka kaggle [Tautan](https://www.kaggle.com/datasets/dbdmobile/myanimelist-dataset/data?select=anime-filtered.csv) dengan keterangan seperti table di bawah ini.

**Informasi Dataset**

| Jenis    | Keterangan                                                |
|----------|-----------------------------------------------------------|
| Title    | Anime Dataset 2023                                        |
| Source   |[Kaggle](https://www.kaggle.com/datasets/dbdmobile/myanimelist-dataset/data?select=anime-filtered.csv)                                                  |
| Maintainer | [Sajid](https://www.kaggle.com/dbdmobile)                                                   |
| License  | Database: Open Database, Contents: Database Contents      |
| Visibility | Publik                                                  |
| Tags     | Arts and Entertainment, Movies and TV Shows, Anime and Manga, Popular Culture, Japan |
| Usability | 10.00                                                     |

### Variabel-variabel dataset adalah sebagai berikut:

**anime-dataset-2023.csv**

- **anime_id**: ID unik untuk setiap anime.  
- **Name**: Nama anime dalam bahasa aslinya.  
-  **English name**: Nama anime dalam bahasa Inggris.  
-  **Other name**: Nama atau judul asli anime (bisa dalam bahasa Jepang, Cina, atau Korea).  
-  **Score**: Skor atau rating yang diberikan kepada anime.  
-  **Genres**: Genre anime, dipisahkan dengan koma.  
-  **Synopsis**: Deskripsi singkat atau ringkasan plot anime.  
-  **Type**: Jenis anime (misalnya, serial TV, film, OVA, dll.).  
-  **Episodes**: Jumlah episode dalam anime.  
-  **Aired**: Tanggal penayangan anime.  
-  **Premiered**: Musim dan tahun penayangan perdana anime.  
-  **Status**: Status anime (misalnya, Selesai Tayang, Sedang Tayang, dll.).  
-  **Producers**: Perusahaan produksi atau produser anime.  
-  **Licensors**: Pihak yang memiliki lisensi anime (misalnya, platform streaming).  
-  **Studios**: Studio animasi yang mengerjakan anime.  
-  **Source**: Sumber materi anime (misalnya, manga, novel ringan, original).  
-  **Duration**: Durasi setiap episode anime.  
-  **Rating**: Batasan usia untuk menonton anime.  
-  **Rank**: Peringkat anime berdasarkan popularitas atau kriteria lain.  
-  **Popularity**: Peringkat popularitas anime.  
-  **Favorites**: Jumlah pengguna yang menandai anime sebagai favorit.  
-  **Scored By**: Jumlah pengguna yang memberikan skor pada anime.  
-  **Members**: Jumlah anggota yang telah menambahkan anime ke daftar mereka di platform.  
-  **Image URL**: URL gambar atau poster anime.  

Dataset ini menawarkan informasi berharga untuk menganalisis dan memahami karakteristik, rating, popularitas, dan jumlah penonton berbagai acara anime. Dengan memanfaatkan dataset ini, seseorang dapat melakukan berbagai analisis, termasuk mengidentifikasi anime dengan rating tertinggi, mengeksplorasi genre paling populer, memeriksa distribusi rating, dan mendapatkan wawasan tentang preferensi serta tren penonton. Selain itu, dataset ini memfasilitasi pembuatan sistem rekomendasi, analisis deret waktu, dan pengelompokan untuk menyelami lebih dalam tren anime dan perilaku pengguna.

**users-details-2023.csv**

-  **Mal ID**: ID unik untuk setiap pengguna.  
-  **Username**: Nama pengguna dari pengguna.  
-  **Gender**: Jenis kelamin pengguna.  
-  **Birthday**: Tanggal lahir pengguna (dalam format ISO).  
-  **Location**: Lokasi atau negara pengguna.  
-  **Joined**: Tanggal ketika pengguna bergabung dengan platform (dalam format ISO).  
-  **Days Watched**: Total jumlah hari yang dihabiskan pengguna untuk menonton anime.  
-  **Mean Score**: Rata-rata skor yang diberikan oleh pengguna kepada anime yang telah ditonton.  
-  **Watching**: Jumlah anime yang sedang ditonton oleh pengguna.  
-  **Completed**: Jumlah anime yang telah diselesaikan oleh pengguna.  
-  **On Hold**: Jumlah anime yang ditunda oleh pengguna.  
-  **Dropped**: Jumlah anime yang dihentikan oleh pengguna.  
-  **Plan to Watch**: Jumlah anime yang direncanakan untuk ditonton oleh pengguna di masa depan.  
-  **Total Entries**: Total jumlah entri anime dalam daftar pengguna.  
-  **Rewatched**: Jumlah anime yang ditonton ulang oleh pengguna.  
-  **Episodes Watched**: Total jumlah episode yang ditonton oleh pengguna.  

Dataset Detail Pengguna ini menyediakan informasi berharga untuk menganalisis perilaku dan preferensi pengguna di platform anime. Dengan memeriksa skor rata-rata dan genre anime, Anda dapat mendapatkan wawasan tentang preferensi pengguna. Pengguna dapat dikelompokkan ke dalam berbagai kelompok berdasarkan perilaku menonton mereka, seperti pengguna aktif dan penonton kasual. Sistem rekomendasi yang dipersonalisasi dapat dibangun menggunakan daftar anime yang telah diselesaikan dan yang direncanakan untuk ditonton. Analisis berbasis lokasi mengungkapkan popularitas anime dan keterlibatan pengguna di berbagai negara. Tren perilaku menonton, retensi pengguna, dan perbedaan preferensi anime berdasarkan gender dapat diidentifikasi. Selain itu, Anda dapat mengeksplorasi kebiasaan menonton ulang dan melakukan analisis deret waktu untuk memahami pola keterlibatan pengguna dari waktu ke waktu.

**users-score-2023.csv**

-  **user_id**: ID unik untuk setiap pengguna.  
-  **Username**: Nama pengguna dari pengguna.  
-  **anime_id**: ID unik untuk setiap anime.  
-  **Anime Title**: Judul anime.  
-  **rating**: Skor yang diberikan oleh pengguna kepada anime.  

Dataset Skor Pengguna memungkinkan berbagai analisis dan wawasan tentang interaksi pengguna dengan anime. Dengan memeriksa penilaian pengguna untuk berbagai judul anime, Anda dapat mengidentifikasi anime yang memiliki rating tinggi dan populer di kalangan pengguna. Selain itu, Anda dapat mengeksplorasi preferensi pengguna dan pola menonton untuk judul anime tertentu. Dataset ini juga menjadi dasar untuk membangun sistem rekomendasi berdasarkan penilaian pengguna, membantu menyarankan anime yang sesuai dengan selera individu. Selanjutnya, Anda dapat melakukan pemfilteran kolaboratif dan analisis kesamaan untuk menemukan pola minat pengguna yang serupa. Secara keseluruhan, dataset ini menawarkan informasi berharga untuk memahami keterlibatan dan preferensi pengguna di platform anime.

### Exploratory Data Analysis - Deskripsi Variable

| No | Column       | Non-Null Count | Dtype  |
|----|--------------|----------------|--------|
| 1  | anime_id     | 24905 non-null | int64  |
| 2  | Name         | 24905 non-null | object |
| 3  | English name | 24905 non-null | object |
| 4  | Other name   | 24905 non-null | object |
| 5  | Score        | 24905 non-null | object |
| 6  | Genres       | 24905 non-null | object |
| 7  | Synopsis     | 24905 non-null | object |
| 8  | Type         | 24905 non-null | object |
| 9  | Episodes     | 24905 non-null | object |
| 10 | Aired        | 24905 non-null | object |
| 11 | Premiered    | 24905 non-null | object |
| 12 | Status       | 24905 non-null | object |
| 13 | Producers    | 24905 non-null | object |
| 14 | Licensors    | 24905 non-null | object |
| 15 | Studios      | 24905 non-null | object |
| 16 | Source       | 24905 non-null | object |
| 17 | Duration     | 24905 non-null | object |
| 18 | Rating       | 24905 non-null | object |
| 19 | Rank         | 24905 non-null | object |
| 20 | Popularity   | 24905 non-null | int64  |
| 21 | Favorites    | 24905 non-null | int64  |
| 22 | Scored By    | 24905 non-null | object |
| 23 | Members      | 24905 non-null | int64  |
| 24 | Image URL    | 24905 non-null | object |

Dari tabel di atas didapat informasi untuk dataset `anime-dataset-2023.csv` banyak fitur categorical dan numerik :

   - Terdapat 20 fitur dengan tipe categorical atau object yaitu `Name, English name, Other name, Score, Genres, Synopsis, Type, Episodes, Aired, Premiered, Status, Producers, Licensors, Studios, Source, Duration, Rating, Rank, Scored By, Image URL`.

   - Terdapat 4 feature dengan tipe numeric terdiri dari 4 int64 yaitu `anime_id, Popularity, Favorites, Members`.

| No | Column            | Non-Null Count   | Dtype    |
|----|-------------------|------------------|----------|
| 0  | Mal ID            | 731290 non-null   | int64    |
| 1  | Username          | 731289 non-null   | object   |
| 2  | Gender            | 224383 non-null   | object   |
| 3  | Birthday          | 168068 non-null   | object   |
| 4  | Location          | 152805 non-null   | object   |
| 5  | Joined            | 731290 non-null   | object   |
| 6  | Days Watched      | 731282 non-null   | float64  |
| 7  | Mean Score        | 731282 non-null   | float64  |
| 8  | Watching          | 731282 non-null   | float64  |
| 9  | Completed         | 731282 non-null   | float64  |
| 10 | On Hold           | 731282 non-null   | float64  |
| 11 | Dropped           | 731282 non-null   | float64  |
| 12 | Plan to Watch     | 731282 non-null   | float64  |
| 13 | Total Entries     | 731282 non-null   | float64  |
| 14 | Rewatched         | 731282 non-null   | float64  |
| 15 | Episodes Watched   | 731282 non-null   | float64  |

Dari tabel di atas didapat informasi untuk dataset `users-details-2023.csv` banyak fitur categorical dan numerik :

   - Terdapat 5 fitur dengan tipe categorical atau object yaitu `Username, Gender, Birthday, Location, Joined`.

   - Terdapat 1 feature dengan tipe numeric terdiri dari 1 int64 dan 10 float64 yaitu `Mal ID, Days Watched, Mean Score, Watching, Completed, On Hold, Dropped, Plan to Watch, Total Entries, Rewatched, Episodes Watched`.

| No | Column       | Dtype  |
|----|--------------|--------|
| 0  | user_id      | int64  |
| 1  | Username     | object |
| 2  | anime_id     | int64  |
| 3  | Anime Title  | object |
| 4  | rating       | int64  |

Dari tabel di atas didapat informasi untuk dataset `users-score-2023.csv` banyak fitur categorical dan numerik :

   - Terdapat 2 fitur dengan tipe categorical atau object yaitu `Username, Anime Title`.

   - Terdapat 3 feature dengan tipe numeric terdiri dari 3 int64 yaitu `user_id, anime_id, rating`.

| Statistic   | anime_id       | Popularity     | Favorites        | Members           |
|-------------|----------------|----------------|------------------|-------------------|
| Count       | 24905          | 24905          | 24905            | 24905             |
| Mean        | 29776.71       | 12265.39       | 432.60           | 37104.96          |
| Std Dev     | 17976.08       | 7187.43        | 4353.18          | 156825.18         |
| Min         | 1              | 0              | 0                | 0                 |
| 25%         | 10507          | 6040           | 0                | 209               |
| 50%         | 34628          | 12265          | 1                | 1056              |
| 75%         | 45240          | 18491          | 18               | 9326              |
| Max         | 55735          | 24723          | 217606           | 3744541           |

<br>

| No | Column             | Count      | Mean       | Std Dev     | Min  | 25%       | 50%       | 75%       | Max        |
|----|--------------------|------------|------------|-------------|------|-----------|-----------|-----------|------------|
| 1  | Mal ID             | 731290     | 507020.30  | 364014.70   | 1    | 201108.50 | 425170.50 | 775340.00 | 1291097.00 |
| 2  | Days Watched       | 731282     | 24.18      | 140.11      | 0    | 0.00      | 0.20      | 24.80     | 105338.60  |
| 3  | Mean Score         | 731282     | 3.95       | 4.14        | 0    | 0.00      | 0.00      | 8.04      | 255.00     |
| 4  | Watching           | 731282     | 4.77       | 20.50       | 0    | 0.00      | 0.00      | 4.00      | 4358.00    |
| 5  | Completed          | 731282     | 65.95      | 186.63      | 0    | 0.00      | 0.00      | 48.00     | 13226.00   |
| 6  | On Hold            | 731282     | 3.39       | 19.30       | 0    | 0.00      | 0.00      | 1.00      | 5167.00    |
| 7  | Dropped            | 731282     | 4.57       | 34.92       | 0    | 0.00      | 0.00      | 1.00      | 14341.00   |
| 8  | Plan to Watch      | 731282     | 17.55      | 90.29       | 0    | 0.00      | 0.00      | 5.00      | 21804.00   |
| 9  | Total Entries      | 731282     | 96.23      | 265.46      | 0    | 0.00      | 1.00      | 74.00     | 24817.00   |
| 10 | Rewatched          | 731282     | 4.44       | 29.69       | 0    | 0.00      | 0.00      | 0.00      | 13215.00   |
| 11 | Episodes Watched   | 731282     | 1658.83    | 50771.68    | 0    | 0.00      | 15.00     | 1489.00   | 3376442.00 |

<br>

| Statistic | user_id       | anime_id      | rating       |
|-----------|----------------|----------------|--------------|
| count     | 24,325,190     | 24,325,190     | 24,325,190   |
| mean      | 440,384.3      | 9,754.7        | 7.623        |
| std       | 366,946.9      | 12,061.9       | 1.662        |
| min       | 1              | 1              | 1            |
| 25%       | 97,188.0       | 873.0          | 7            |
| 50%       | 387,978.0      | 4,726.0        | 8            |
| 75%       | 528,043.0      | 13,161.0       | 9            |
| max       | 1,291,097.0    | 56,085.0       | 10           |

3 Table diatas memberikan informasi statistik pada masing-masing kolom di 3 dataset, antara lain:

- Count adalah jumlah sampel pada data.
- Mean adalah nilai rata-rata.
- Std adalah standar deviasi.
- Min yaitu nilai minimum setiap kolom.
- 25% adalah kuartil pertama. Kuartil adalah nilai yang menandai batas interval - dalam empat bagian sebaran yang sama.
- 50% adalah kuartil kedua, atau biasa juga disebut median (nilai tengah).
- 75% adalah kuartil ketiga.
- Max adalah nilai maksimum.

| Nama Dataset           | Jumah Baris             | Jumlah Kolom |
|------------------------|-------------------------|--------------|
| anime-dataset-2023.csv | 24905                   | 24           |

<br>

| Nama Dataset           | Jumah Baris             | Jumlah Kolom |
|------------------------|-------------------------|--------------|
| users-details-2023.csv | 731290                  | 16           |

<br>

| Nama Dataset           | Jumah Baris             | Jumlah Kolom |
|------------------------|-------------------------|--------------|
| users-score-2023.csv   | 24325191                | 5            |

### Exploratory Data Analysis - Missing Value

**Mengecek missing value, Duplikat**

| Nama Dataset           | Data Duplikat           |
|------------------------|-------------------------|
| anime-dataset-2023.csv | 0                       | 

<br>

| Nama Dataset           | Data Duplikat           |
|------------------------|-------------------------|
| users-details-2023.csv | 0                       | 

<br>

| Nama Dataset           | Data Duplikat           |
|------------------------|-------------------------|
| users-score-2023.csv | 0                         | 

tidak terdapat data duplikat pada ke-3 dataset.

<br>

| Field            | Count |
|------------------|-------|
| anime_id         | 0     |
| Name             | 0     |
| English name     | 0     |
| Other name       | 0     |
| Score            | 0     |
| Genres           | 0     |
| Synopsis         | 0     |
| Type             | 0     |
| Episodes         | 0     |
| Aired            | 0     |
| Premiered        | 0     |
| Status           | 0     |
| Producers        | 0     |
| Licensors        | 0     |
| Studios          | 0     |
| Source           | 0     |
| Duration         | 0     |
| Rating           | 0     |
| Rank             | 0     |
| Popularity       | 0     |
| Favorites        | 0     |
| Scored By        | 0     |
| Members          | 0     |
| Image URL        | 0     |

setelah dilakukan pengecekan untuk dataset `anime-dataset-2023.csv` tidak terdapat missing value.

| Field               | Count   |
|---------------------|---------|
| Mal ID              | 0       |
| Username            | 1       |
| Gender              | 506,907 |
| Birthday            | 563,222 |
| Location            | 578,485 |
| Joined              | 0       |
| Days Watched        | 8       |
| Mean Score          | 8       |
| Watching            | 8       |
| Completed           | 8       |
| On Hold             | 8       |
| Dropped             | 8       |
| Plan to Watch       | 8       |
| Total Entries       | 8       |
| Rewatched           | 8       |
| Episodes Watched    | 8       |

<br>

| Field          | Count |
|----------------|-------|
| user_id        | 0     |
| Username       | 232   |
| anime_id       | 0     |
| Anime Title    | 0     |
| rating         | 0     |

dari output diatas didapati bahwa terdapat missing value pada dataset `user-details-2023.csv` pada atribut Username dengan jumlah 1 , Gender berjumlah 506907, Birthday berjumlah 563222, Location berjumlah 578485 dan pada dataset `user-score-2023.csv` missing value berjumlah 232 pada atribut username.


### Exploratory Data Analysis - Univariate Analysis

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-5.png?raw=true)

Pada visualisasi Type Anime di atas dapat disimpulkan bahwa Type Anime TV menduduki jumlah paling tinggi disusul Movie dan OVA dan paling lalu ada Type anime UNKNOWN dengan jumlah paling sedikit.

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-7.png?raw=true)

Pada Visualisasi Sudios Anime di atas didapati bahwa Top 5 distribusi Studio Anime terbanyak sebesar 42.3% Tidak diketahui (UNKNOWN) lalu 3,3% untuk Studio Toei Animation, 2.1% Studio Sunrise, 1.5% Studio J.C.Staff, 1.3% Shanghai Animation Film Studio dan 49.4% untuk studio lainnya.

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-8.png?raw=true)

Hasil visualisasi di atas dapat disimpulkan untuk top 10 anime teratas berdasarkan jumlah membernya mulai dari shingeki no kyojin hingga hunter x hunter.

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-9.png?raw=true)

Hasil visualisasi di atas di dapati untuk top 10 anime teratas berdasarkan skor paling tinggi jika diambil 10 teratas berdasarkan score maka hasilnya berbeda dengan 10 anime teratas berdasarkan jumlah membernya.

### Exploratory Data Analysis - Multivariate Analysis

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-10.png?raw=true)

Dari visualisasi di atas didapati nilai korelasi negatif sebesar -0.36 menunjukkan adanya **hubungan negatif sedang** antara jumlah Members dan Popularity. Ini berarti bahwa anime dengan jumlah Members yang lebih tinggi cenderung memiliki nilai Popularity yang lebih rendah.

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-11.png?raw=true)

Pada visualisasi di atas didapati nilai korelasi negatif -0.19 ini menunjukkan **hubungan yang lemah** antara jumlah Favorites dan Popularity. Korelasi negatif berarti bahwa ketika jumlah Favorites meningkat, nilai Popularity (peringkat) cenderung menurun.

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-12.png?raw=true)

Pada visualisasi di atas didapati nilai korelasi 0.773 menunjukkan adanya hubungan positif yang kuat antara jumlah Favorites dan Members. Ini berarti bahwa anime dengan jumlah Members yang tinggi cenderung juga memiliki jumlah Favorites yang tinggi.


## Data Preparation

Teknik Data preparation yang dilakukan terdiri dari:

- Data Preprocessing
- TF-IDF Vectorizer Data Anime
- Encoding Data User Rating
- Train-test-split Data User Rating

### Data Preprocessing

sebelumnya kita memiliki 3 file csv dan setelah di cek untuk melakukan Content Based Filtering kita cukup menggunakan dataset `anime-dataset-2023` dan untuk Collaborative Filtering kita cukup menggunakan `users-score-2023` yang kemudian akan disimpan kedalam 2 data frame Anime dan Rating.

**Penanganan Missing Value**

- pada tahap Exploratory Data Analysis kita mengidentifikasi terdapat terdapat missing value pada dataset `user-details-2023.csv` pada atribut Username dengan jumlah 1 , Gender berjumlah 506907, Birthday berjumlah 563222, Location berjumlah 578485 dan pada dataset `user-score-2023.csv` missing value berjumlah 232 pada atribut username yang harus dihapus.

  ```user_detail.dropna()```
  
  ```user_rating.dropna()```

  total data setelah menghapus missig value pada kedua dataset seperti table berikut:

  | Nama Dataset           | Jumah Baris             | Jumlah Kolom |
  |------------------------|-------------------------|--------------|
  | user-details-2023.csv  | 731290                  | 16           |

  <br>

  | Nama Dataset           | Jumah Baris             | Jumlah Kolom |
  |------------------------|-------------------------|--------------|
  | user-score-2023.csv    | 24325191                | 5            |


**Hapus beberapa atribut yang tidak terlalu penting pada dataframe Rating**

```Rating = user_rating.drop(columns=['Anime Title', 'Username'])```

**Menyamakan Anime Genres**

| anime_id | Name                                                    | Genres  |
|----------|---------------------------------------------------------|---------|
| 485      | Mahou no Princess Minky Momo                            | UNKNOWN |
| 603      | Hikaru no Go: Hokuto Hai e no Michi                    | UNKNOWN |
| 894      | Shinshaku Sengoku Eiyuu Densetsu: Sanada Juu Y...     | UNKNOWN |
| 1096     | Nitaboh                                                | UNKNOWN |
| 1115     | Ame to Shoujo to Watashi no Tegami                     | UNKNOWN |
| ...      | ...                                                     | ...     |
| 24528    | Shayou (Music)                                         | UNKNOWN |
| 24549    | Telepath                                               | UNKNOWN |
| 24635    | Slash                                                  | UNKNOWN |
| 24729    | The IDOLM@STER Cinderella Girls: U149 Recap            | UNKNOWN |
| 24856    | Fins                                                   | UNKNOWN |

Karena setelah dicek terdapat value `UNKNOWN` pada atribut Genre maka akan kita hapus.

Karena dataframe Rating sangat banyak dan tidak sepadan dengan sumber daya yang saya miliki oleh karena itu kita akan mengambil beberap puluh ribu saja untuk dijadikan sample.

**Mengapa diperlukan tahapan Data Preprocessing?**

- Data preprocessing adalah tahap penting dalam analisis data dan pengembangan model machine learning, yang bertujuan untuk mempersiapkan data agar lebih bersih, relevan, dan siap digunakan. Tahapan ini diperlukan untuk mengurangi kebisingan (noise) dengan menghapus atribut yang tidak penting, seperti yang dilakukan pada dataframe Anime dan Rating, serta meningkatkan kualitas data dengan menghapus nilai yang tidak valid atau 'UNKNOWN' dalam atribut Genre. Selain itu, preprocessing mempercepat proses analisis dengan mengurangi jumlah data dan atribut yang tidak perlu, serta memudahkan pemrosesan data yang lebih terstruktur. Hal ini juga berkontribusi pada peningkatan kinerja model, karena model membutuhkan data yang bersih dan relevan untuk menghasilkan prediksi yang akurat. Dengan demikian, data preprocessing menyediakan basis yang solid untuk analisis lebih lanjut, memastikan bahwa data yang digunakan berkualitas tinggi dan mudah diolah.

### TF-IDF Vectorizer Data Anime

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image.png?raw=true)

 - Mengubah data kedalam representasi numerik dengan TF-IDF Vectorizer sebelum tahap Modeling **Cosine Similiarity**

**Mengapa diperlukan Mengubah data kedalam representasi numerik?**

- Data perlu diubah kedalam representasi numerik karena sistem rekomendasi berbasis konten membutuhkan representasi numerik dari teks atau fitur kategori agar dapat mengukur kemiripan antar-item. Misalnya, dalam rekomendasi film, kategori seperti "Action," "Drama," atau "Fantasy" diubah menjadi nilai numerik untuk dihitung kemiripannya.

### Encoding Data User Rating

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-1.png?raw=true)

- Encoding data untuk sebelum tahap pemodelan **Collaborative Filtering**

**Mengapa diperlukan melakukan Encoding data?**

- Encoding data perlu dilakukan karena pada Collaborative Filtering, model harus belajar dari pola interaksi pengguna terhadap item. Data perlu diubah ke dalam bentuk numerik agar model neural network dapat memprosesnya.


### Train-test-split User Rating

Selanjutnya, dilakukan train-test-split dengan pembagian data sebesar 80:20 antara data latih (train) dan data validasi.

**Mengapa diperlukan melakukan Train-test-split data?**

- Memisahkan data menjadi set pelatihan dan pengujian memungkinkan kita untuk mengevaluasi kinerja model pada data yang tidak pernah dilihat sebelumnya. Ini memberikan gambaran yang lebih akurat tentang seberapa baik model yg kita buat.

## Modeling

Pada tahapan model yang digunakan terdiri dari:

- Cosine Similarity
- RecomenderNet

### 1. Cosine Similarity

- **Cara Membuat Model**:

  1.   ```from sklearn.metrics.pairwise import cosine_similarity```

       - Mengimpor fungsi cosine_similarity dari modul sklearn.metrics.pairwise. Fungsi ini digunakan untuk menghitung kemiripan kosinus antar-vektor (contohnya, antar-vektor TF-IDF yang mewakili deskripsi atau genre anime).

  2.   ```cosine_sim = cosine_similarity(tfidf_matrix)```

       - Fungsi cosine_similarity menghitung kemiripan kosinus antara semua pasangan baris dalam matriks tfidf_matrix.  

  3.   ```cosine_sim = cosine_similarity(tfidf_matrix)```

       - Fungsi cosine_similarity menghitung kemiripan kosinus antara semua pasangan baris dalam matriks tfidf_matrix.

        - **Penjelasan Parameter**:

          - tfidf_matrix: Matriks yang berisi nilai TF-IDF untuk masing-masing anime.

    ![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-2.png?raw=true)

    pada kode di atas, dengan menggunakan argpartition, kita mengambil sejumlah nilai k tertinggi dari similarity data (dalam kasus ini: dataframe cosine_sim_df). Kemudian, kita mengambil data dari bobot (tingkat kesamaan) tertinggi ke terendah. Data ini dimasukkan ke dalam variabel closest. Berikutnya, kita perlu menghapus nama_anime yang yang dicari agar tidak muncul dalam daftar rekomendasi. Dalam kasus ini, nanti kita akan mencari anime yang mirip dengan Tarareba, sehingga kita perlu drop nama_anime Tarareba agar tidak muncul dalam daftar rekomendasi yang diberikan nanti.

- **Cara Kerja Pendekatan Content-based filtering:** 

    Content-based filtering mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna. Algoritma ini bekerja dengan menyarankan item serupa yang pernah disukai di masa lalu atau sedang dilihat di masa kini kepada pengguna. Semakin banyak informasi yang diberikan pengguna, semakin baik akurasi sistem rekomendasi.

  - **Kelebihan:**

    - Tidak Bergantung pada Data Pengguna Lain: Hanya membutuhkan data dari item yang direkomendasikan, bukan dari perilaku pengguna lainnya.
    - Personalisasi Berdasarkan Minat Pengguna: Memberikan rekomendasi berdasarkan profil pengguna atau riwayat preferensinya.
    - Efektif untuk Pengguna Baru: Content-based filtering efektif untuk pengguna baru yang belum memiliki riwayat interaksi, selama ada cukup informasi tentang konten.

  - **Kekurangan:**

    - Keterbatasan dalam Diversifikasi: Cenderung merekomendasikan item yang serupa dengan yang sudah disukai pengguna, yang bisa membuat rekomendasi menjadi monoton.
    - Ketergantungan pada Kualitas Fitur Konten: Jika fitur atau deskripsi konten terbatas atau kurang informatif, sistem akan sulit memberikan rekomendasi yang relevan.
    - Tidak Memanfaatkan Informasi dari Pengguna Lain: Sistem ini tidak belajar dari interaksi atau preferensi pengguna lain, yang dapat mengurangi variasi rekomendasi. 

- **Cara Kerja Model Cosine Similiarity:**  

    Cosine similarity adalah teknik yang digunakan untuk mengukur seberapa mirip dua vektor, terlepas dari ukuran atau panjang vektor tersebut. Pendekatan ini banyak digunakan dalam rekomendasi berbasis konten untuk menilai kesamaan antara dua item (seperti film atau buku) berdasarkan fitur-fitur atau kata kunci yang mereka miliki.

    - **Kelebihan**

      - Independensi Magnitudo: Mengukur kesamaan berdasarkan sudut antara vektor, bukan panjangnya, sehingga efektif untuk data berdimensi tinggi.
      - Efisiensi Komputasi: Perhitungan cepat dan sederhana, ideal untuk dataset besar.

    - **Kekurangan**

      - Mengabaikan Magnitudo: Tidak mempertimbangkan ukuran vektor, yang mungkin relevan dalam beberapa konteks.
      - Sensitif terhadap Noise: Hasil dapat terpengaruh oleh fitur yang tidak relevan atau bising.


### 2. RecomenderNet

- **Cara Membuat Model**:

  1.   ```import tensorflow as tflw```

       - Mengimpor pustaka TensorFlow dan memberi nama alias tflw.

  2.   ```from tensorflow import keras```

       - Mengimpor sub-pustaka Keras dari TensorFlow.

  3.   ```from tensorflow.keras import layers```

       - Mengimpor modul layers dari Keras yang ada di dalam TensorFlow.

    ![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-3.png?raw=true)

  membuat class RecommenderNet dengan keras Model class. Kode class RecommenderNet ini terinspirasi dari tutorial dalam situs Keras dengan beberapa adaptasi sesuai kasus yang ingin diselesaikan.

- **Cara Kerja Pendekatan Collaborative Filtering:**

  Collaborative filtering menganalisis interaksi pengguna dengan item untuk memberikan rekomendasi. Algoritma ini bekerja dengan mencari pola dalam penilaian atau perilaku pengguna dan menyarankan item yang mungkin disukai berdasarkan preferensi pengguna lain yang memiliki kesamaan. Ada dua jenis utama dalam collaborative filtering: user-based yang mencocokkan pengguna serupa, dan item-based yang mencocokkan item yang sering dinilai tinggi oleh pengguna yang sama. Semakin banyak interaksi yang diperoleh, semakin baik akurasi sistem rekomendasi

  - **Kelebihan:**

    - Rekomendasi yang Personalisasi: Memberikan rekomendasi berdasarkan interaksi nyata pengguna, sehingga lebih sesuai dengan preferensi individu.
    - Independen dari Konten: Tidak memerlukan pengetahuan mendalam tentang konten item, sehingga dapat digunakan untuk berbagai jenis item (film, buku, produk, dll).
    - Mendapatkan Rekomendasi Baru: Dapat merekomendasikan item yang tidak dikenal sebelumnya oleh pengguna, membuka kesempatan untuk penemuan baru.

  - **Kekurangan:**

    - Cold Start Problem: Sulit memberikan rekomendasi yang akurat untuk pengguna baru atau item baru yang belum memiliki cukup interaksi.
    - Data Sparsity: Jika data interaksi pengguna sangat sedikit, sulit untuk menemukan pola yang cukup untuk menghasilkan rekomendasi yang baik.
    - Bias terhadap Popularitas: Cenderung merekomendasikan item yang sudah populer, sehingga item yang kurang dikenal bisa terabaikan meskipun mungkin relevan untuk pengguna tertentu.

- **Cara Kerja Model RecommenderNet:**

  RecommenderNet adalah model yang dirancang untuk memberikan rekomendasi kepada pengguna berdasarkan interaksi mereka dengan item sebelumnya. Model ini menggunakan teknik pembelajaran mendalam untuk mempelajari pola dan preferensi pengguna dari data historis. Proses ini melibatkan pengkodean informasi pengguna dan item ke dalam representasi vektor, yang kemudian digunakan untuk memprediksi preferensi pengguna terhadap item yang belum mereka lihat.

  - **Kelebihan**

    - Personalisasi Tinggi: Mampu menghasilkan rekomendasi yang sangat sesuai dengan preferensi individu pengguna berdasarkan analisis data historis.
    - Kemampuan Menangkap Hubungan Kompleks: Dapat memahami dan memodelkan interaksi non-linear antara pengguna dan item, meningkatkan akurasi rekomendasi.

  - **Kekurangan**
    - Memerlukan Banyak Data: Kinerja optimal tergantung pada ketersediaan data yang cukup banyak dan beragam dari pengguna dan item.
    - Kompleksitas Model: Lebih rumit dalam hal arsitektur dan pelatihan dibandingkan metode rekomendasi tradisional, memerlukan lebih banyak sumber daya komputasi.

### Hasil Top-N Rekomendasi Model Cosine Similiarity

| anime_id | Name                  | Genres                        |
|----------|-----------------------|-------------------------------|
| 12335    | Hajimete no Gal       | Comedy, Romance, Ecchi        |


| No | Name                                                   | Genres                   |
|----|--------------------------------------------------------|--------------------------|
| 0  | High School DxD New: Oppai, Tsutsumimasu!            | Comedy, Romance, Ecchi   |
| 1  | Love Hina Final Selection                              | Comedy, Romance, Ecchi   |
| 2  | Mujaki no Rakuen                                      | Comedy, Romance, Ecchi   |
| 3  | 1+2=Paradise                                          | Comedy, Romance, Ecchi   |
| 4  | Kimi ga Aruji de Shitsuji ga Ore de                  | Comedy, Romance, Ecchi   |
| 5  | Gift: Eternal Rainbow - Ki no Saka Ryokan Kiki...    | Comedy, Romance, Ecchi   |
| 6  | Maji de Watashi ni Koi Shinasai!                     | Comedy, Romance, Ecchi   |
| 7  | Dakara Boku wa, H ga Dekinai. Mie Sugi! Mizugi...    | Comedy, Romance, Ecchi   |
| 8  | Sprite: Between Two Worlds                             | Comedy, Romance, Ecchi   |
| 9  | Megami no Café Terrace                                 | Comedy, Romance, Ecchi   |

Berdasarkan hasil tabel di atas model `Cosine Similiarity` berhasil merekomendasikan Top-N anime dengan genre yang sama dengan anime Hajimete no Gal.

### Hasil Top-N Rekomendasi RecommenderNet 

<br>

=============================================

**Menampilkan Rekomendasi untuk Pengguna: 707343**

=============================================

**Anime dengan Rating Tertinggi dari Pengguna**

=============================================

| Judul Anime | Genre |
|-------------|-------|
| **New Game!** | Comedy |

=============================================

**Rekomendasi 10 Anime Teratas**

=============================================

| No. | Judul Anime | Genre |
|-----|-------------|-------|
| 1   | **s.CRY.ed** | Action, Adventure, Drama, Sci-Fi |
| 2   | **Slam Dunk** | Sports |
| 3   | **Tactics** | Mystery, Supernatural |
| 4   | **One Piece Film: Strong World** | Action, Adventure, Fantasy |
| 5   | **Major S5** | Sports |
| 6   | **Naruto: Shippuuden Movie 3 - Hi no Ishi wo Tsugu Mono** | Action, Adventure, Fantasy |
| 7   | **Tegamibachi Reverse** | Adventure, Fantasy |
| 8   | **Natsume Yuujinchou San** | Drama, Slice of Life, Supernatural |
| 9   | **Haikyuu!! Karasuno Koukou vs. Shiratorizawa Gakuen Koukou** | Sports |
| 10  | **Bocchi the Rock!** | Comedy |

Berdasarkan hasil tabel di atas model `RecommenderNet` berhasil merekomendasikan anime dengan rating tertinggi dari pengguna dan merekomendasikan Top-N anime teratas pada Pengguna: 707343.

## Evaluation

Pada project ini ada 2 matrix yang digunakan untuk mengevaluasi model yaitu *Precision* dan *RMSE (Root Mean Squared Error)* dengan penjelasan seeperti berikut: 

### Evaluasi Model *Cosine Similiarity*

Model ini hanya menggunakan metrik Precision untuk mengetahui seberapa baik perforam model tersebut. Presisi adalah metrik yang biasa digunakan untuk mengevaluasi kinerja model pengelompokan. Metrik ini menghitung rasio antara nilai ground truth (nilai sebenarnya) dengan nilai prediksi yang positf. Perhitungan rasio ini dijabarkan melalui rumus di bawah ini:

$$ Precision = \frac{TP}{TP + FP} $$

Dimana:

- TP (*True Positive*), jumlah kejadian positif yang diprediksi dengan benar.
- FP (*False Positive*), jumlah kejadian positif yang diprediksi dengan salah.

Berdasarkan hasil yang terdapat pada tahap Model and Result dapat dilihat bahwasanya besar presisi jika dihitung adalah 10/10 untuk rekomendasi Top-10. Ini menunjukan sistem mampu memberikan rekomendasi sesuai dengan Genres Animenya.

### Evaluasi Model *RecommenderNet*

Evaluasi metrik yang dapat digunakan untuk mengukur kinerja model ini adalah metrik RMSE (*Root Mean Squared Error*). RMSE adalah metode pengukuran dengan mengukur perbedaan nilai dari prediksi sebuah model sebagai estimasi atas nilai yang diobservasi. RMSE dapat dijabarkan melalui pendekatan rumus berikut ini

$$ RMSE =  \sqrt{\frac{\sum_{t=1}^{n}(A_t - F_t)^2}{n}} $$

Dimana:

- $A_t$ : Nilai aktual
- $F_t$ : Nilai hasil prediksi
- n: Banyak data

*Collaborative Filtering* dengan model RecommenderNet memberikan hasil training yang divisualisasikan melalui gambar di bawah ini: 

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-14.png?raw=true)

Dengan epoch sebanyak 100, model ini memperoleh nilai error akhir sebesar sekitar 0.06 untuk training dan error pada data validasi sebesar 0.25. Nilai tersebut cukup bagus untuk sistem rekomendasi.

Berdasarkan hasil yang didapat pada tahap Model and Result untuk user dengan id 707343 model berhasil merekomendasikan Anime dengan rating tertinggi dari pengguna dan Rekomendasi Top-10 anime teratas untuk user 707343.

## Kesimpulan

Dari hasil evaluasi, solusi sistem rekomendasi dengan pendekatan Content-Based Filtering dengan model Cosine Similarity dan Collaborative Filtering menggunakan model RecommenderNet menunjukkan bahwa kedua pendekatan ini berhasil mencapai tujuan proyek. Content-Based Filtering dengan model Cosine Similiarity memberikan rekomendasi anime yang relevan berdasarkan kesamaan genre dengan presisi tinggi, mencapai rekomendasi Top-10 yang sesuai kategori. Sementara itu, pendekatan Collaborative Filtering dengan model RecommenderNet menghasilkan rekomendasi anime berdasarkan pola rating pengguna dengan error yang rendah (RMSE sekitar 0.06 untuk data training dan 0.25 untuk data validasi), menunjukkan kemampuannya dalam memprediksi preferensi pengguna dengan akurat. Secara keseluruhan, kedua pendekatan ini berhasil memberikan rekomendasi yang relevan dan sesuai dengan tujuan utama, yaitu menyediakan rekomendasi anime yang sesuai dengan preferensi genre dan pola rating pengguna.

## Referensi

Wibowo, A. T. (2020, December). *Leveraging side information to anime recommender system using deep learning*. In 2020 3rd International Seminar on Research of Information Technology and Intelligent Systems (ISRITI) (pp. 62-67). [Link](https://ieeexplore.ieee.org/abstract/document/9315363/)

Aisyah, I. (2019). *Anime dan gaya hidup mahasiswa (studi pada mahasiswa yang tergabung dalam Komunitas Japan Freak UIN Jakarta)*. (Bachelor's thesis, Fakultas Ilmu Tarbiyah dan Keguruan UIN Syarif Hidayatullah Jakarta). [Link](https://repository.uinjkt.ac.id/dspace/handle/123456789/45316)

Jayaperwira, I., Wibowo, A. T., & Nurjanah, D. (2023). *Anime rekomendasi menggunakan Collaborative Filtering*. eProceedings of Engineering, 10(3). [Link](https://openlibrarypublications.telkomuniversity.ac.id/index.php/engineering/article/view/20612)

Permadi, V. A., & Raharjo, R. P. (2023). *Improvement of KNN Collaborative Filtering Model in User-based Approach on Anime Recommendation System*. Sistemasi: Jurnal Sistem Informasi, 12(2), 381-389. [Link](https://sistemasi.ftik.unisi.ac.id/index.php/stmsi/article/view/2473)

Roziqiin, N. M., & Faisal, M. (2024). *Sistem rekomendasi pemilihan anime menggunakan user-based collaborative filtering*. JIPI (Jurnal Ilmiah Penelitian dan Pembelajaran Informatika), 9(1), 299-306. [Link](http://www.jurnalstkippgritulungagung.ac.id/index.php/jipi/article/view/4222)

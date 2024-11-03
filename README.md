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

| Jenis    | Keterangan                                                |
|----------|-----------------------------------------------------------|
| Title    | Anime Dataset 2023                                        |
| Source   |[Kaggle](https://www.kaggle.com/datasets/dbdmobile/myanimelist-dataset/data?select=anime-filtered.csv)                                                  |
| Maintainer | [Sajid](https://www.kaggle.com/dbdmobile)                                                   |
| License  | Database: Open Database, Contents: Database Contents      |
| Visibility | Publik                                                  |
| Tags     | Arts and Entertainment, Movies and TV Shows, Anime and Manga, Popular Culture, Japan |
| Usability | 10.00                                                     |

### Exploratory Data Analysis - Deskripsi Variabel

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

Pada bagian ini ada beberapa tahap persiapan data yang dilakukan, yaitu:

- Memuat dan Memeriksa Atribut Dataset
  - ```print(anime_data.columns.tolist())```
  
    Mencetak daftar atribut (kolom) dari dataset anime yang dimuat.

  - ```print(user_rating.columns.tolist())```

    Mencetak daftar atribut dari dataframe user_rating.

- Menyaring Atribut yang Tidak Perlu

  - ```Anime = anime_data.drop(columns=['English name', 'Other name', 'Synopsis','Episodes', 'Aired', 'Premiered','Status', 'Producers', 'Licensors', 'Studios', 'Source', 'Duration', 'Rating','Rank', 'Popularity', 'Favorites', 'Scored By', 'Members', 'Image URL', 'Score','Type'])```

    Menghapus kolom yang tidak relevan atau tidak diperlukan untuk modeling.

  - ```Rating = user_rating.drop(columns=['Anime Title', 'Username'])```

    Menghapus kolom yang tidak diperlukan dari dataframe rating.

- Mengecek Missing Values

  - ```Anime.isnull().sum()```

    Memeriksa jumlah missing values dalam dataframe Anime jika terdapat missing value nantinya akan dihapus.

- Mengecek Duplikasi

  - ```Anime.duplicated().sum()```

    Memeriksa jumlah baris yang duplikat dalam dataframe Anime jika terdapat data duplikat nantinya akan dihapus.

- Menghapus Data Atribut Dengan Nilai Yang Aneh

  - ```fix_anime = fix_anime[fix_anime['Genres'] != 'UNKNOWN']```

    Menghapus semua baris yang memiliki genre 'UNKNOWN'.

- Mengubah data kedalam representasi numerik dengan TF-IDF Vectorizer sebelum tahap pemodelan **Content Based Filtering**

- Encoding fitur kategori untuk sebelum tahap pemodelan **Collaborative Filtering**


**Mengapa diperlukan tahapan data preparation tadi?**

- Memeriksa atribut penting untuk memahami struktur dataset dan atribut mana yang releva/digunakan untuk tahapan modeling nantinya.

- Menyaring kolom yang tidak penting membantu menyederhanakan dataset, mengurangi kompleksitas, dan mengurangi kemungkinan kebisingan dalam analisis.

- Mengetahui apakah ada data yang hilang adalah penting karena missing values dapat memengaruhi hasil analisis dan model. Langkah ini membantu untuk mengambil tindakan yang diperlukan untuk menangani missing values, seperti pengisian atau penghapusan data.

- Data duplikat dapat merusak analisis dan memberikan hasil yang menyesatkan. Dengan mengecek dan menghapus data duplikat, memastikan integritas dataset.

- Menghapus data yang tidak valid atau tidak lengkap akan meningkatkan kualitas data yang digunakan untuk analisis. Data yang bersih dan relevan akan menghasilkan model yang lebih akurat dan dapat diandalkan.

- Data perlu diubah kedalam representasi numerik karena sistem rekomendasi berbasis konten membutuhkan representasi numerik dari teks atau fitur kategori agar dapat mengukur kemiripan antar-item. Misalnya, dalam rekomendasi film, kategori seperti "Action," "Drama," atau "Fantasy" diubah menjadi nilai numerik untuk dihitung kemiripannya.

- Encoding fitur kategori perlu dilakukan karena pada Collaborative Filtering, model harus belajar dari pola interaksi pengguna terhadap item. Karena data seperti ID pengguna dan ID item bersifat kategori, data ini perlu diubah ke dalam bentuk numerik agar model neural network dapat memprosesnya.

Tahapan data preparation sangat penting untuk memastikan bahwa data yang digunakan untuk analisis dan pemodelan berkualitas tinggi, lengkap, dan relevan. Dengan melakukan pembersihan, penyaringan, dan pemformatan data, dapat mempersiapkan dasar yang kuat untuk langkah-langkah analisis selanjutnya, baik untuk content-based filtering maupun collaborative filtering.

## Modeling

pada project ini ada 2 pendekatan yang digunakan untuk Sistem Rekomendasi Anime yaitu:

- Sistem rekomendasi berbasis konten (content-based filtering) dengan Cosine Similiarity.

  - **Cara Kerja:** 

    ![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-13.png?raw=true)

    Content-based filtering mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna. Algoritma ini bekerja dengan menyarankan item serupa yang pernah disukai di masa lalu atau sedang dilihat di masa kini kepada pengguna. Semakin banyak informasi yang diberikan pengguna, semakin baik akurasi sistem rekomendasi.  

  - **Kelebihan:**

    - Tidak Bergantung pada Data Pengguna Lain: Hanya membutuhkan data dari item yang direkomendasikan, bukan dari perilaku pengguna lainnya.
    - Personalisasi Berdasarkan Minat Pengguna: Memberikan rekomendasi berdasarkan profil pengguna atau riwayat preferensinya.
    - Efektif untuk Pengguna Baru: Content-based filtering efektif untuk pengguna baru yang belum memiliki riwayat interaksi, selama ada cukup informasi tentang konten.

  - **Kekurangan:**

    - Keterbatasan dalam Diversifikasi: Cenderung merekomendasikan item yang serupa dengan yang sudah disukai pengguna, yang bisa membuat rekomendasi menjadi monoton.
    - Ketergantungan pada Kualitas Fitur Konten: Jika fitur atau deskripsi konten terbatas atau kurang informatif, sistem akan sulit memberikan rekomendasi yang relevan.
    - Tidak Memanfaatkan Informasi dari Pengguna Lain: Sistem ini tidak belajar dari interaksi atau preferensi pengguna lain, yang dapat mengurangi variasi rekomendasi.

    - **Cara Membuat Model:**


- Sistem rekomendasi berbasis konten (Collaborative Filtering) model based Deep learning atau Neural Network .

  - **Cara Kerja:** 
  Menggunakan model neural network, untuk menemukan pola dalam interaksi pengguna terhadap item tertentu. Model ini umumnya melibatkan embedding untuk merepresentasikan pengguna dan item dalam ruang vektor, yang kemudian dilatih untuk memprediksi preferensi pengguna terhadap item.

  - **Kelebihan:**

    - Dapat Menangkap Preferensi Lebih Kompleks: Dengan model deep learning, sistem ini dapat mempelajari pola preferensi yang kompleks dan non-linear.
    - Mengatasi Masalah Cold Start (pada Konten): Collaborative filtering menggunakan data pengguna sehingga dapat merekomendasikan item baru yang belum memiliki cukup metadata.
    - Lebih Kaya dalam Diversifikasi: Dengan memanfaatkan data dari banyak pengguna, sistem bisa memberikan rekomendasi lebih bervariasi, termasuk item yang berbeda dari preferensi pengguna tetapi relevan dengan kelompok pengguna yang serupa.

  - **Kekurangan:**

    - Memerlukan Data Pengguna yang Banyak: Collaborative filtering membutuhkan interaksi pengguna dalam jumlah besar agar rekomendasi efektif.
    - Cold Start untuk Pengguna Baru: Pengguna baru tanpa riwayat interaksi mungkin tidak mendapatkan rekomendasi yang baik sampai ada cukup data interaksi.
    - Komputasi yang Lebih Intensif: Model deep learning, seperti RecommenderNet, membutuhkan daya komputasi yang tinggi dan sumber daya yang lebih besar untuk pelatihan dan inferensi.

## Evaluation

Pengukuran performa dari model sistem rekomendasi bergantung pada jenis sistem rekomendasi yang digunakan. Untuk model dengan Content-based Filtering, performa akan dihitung berdasarkan seberapa cocok produk yang direokmendasikan dengan kategorinya. Sedangkan Collaborative filtering akan menggunakan metrik pengukuran model based, contohnya RMSE.

### Pengujian Model Content Based Filtering

Model ini hanya menggunakan metrik Precision untuk mengetahui seberapa baik perforam model tersebut. Presisi adalah metrik yang biasa digunakan untuk mengevaluasi kinerja model pengelompokan. Metrik ini menghitung rasio antara nilai ground truth (nilai sebenarnya) dengan nilai prediksi yang positf. Perhitungan rasio ini dijabarkan melalui rumus di bawah ini:

$$ Precision = \frac{TP}{TP + FP} $$

Dimana:

- TP (*True Positive*), jumlah kejadian positif yang diprediksi dengan benar.
- FP (*False Positive*), jumlah kejadian positif yang diprediksi dengan salah.

**Testing Hasil Evaluasi Model Content Based Filtering**

|No        | anime_id | Name     | Genres |
|----------|----------|----------|--------|
| 15577    | 39568    | Tarareba | Drama  |

percobaan mencari rekomendasi anime yang mirip dengan anime Tarareba dengan Genre Drama.

| No | Name                                                | Genres |
|----|-----------------------------------------------------|--------|
| 0  | Cosmic Break                                        | Drama  |
| 1  | Shokugeki no Souma: San no Sara - Kyokuseiryou...   | Drama  |
| 2  | Ubasuteyama                                         | Drama  |
| 3  | IDOLiSH7 Vibrato                                    | Drama  |
| 4  | Akage no Anne                                       | Drama  |
| 5  | Yuki no Yoru no Yume                                | Drama  |
| 6  | Kinyoubi no Yakusoku                                | Drama  |
| 7  | Hibike! Euphonium                                   | Drama  |
| 8  | Piano no Mori (TV)                                  | Drama  |
| 9  | Drive Agent Personal: Shiawase wo Mamoru Mono       | Drama  |

Berdasarkan hasil yang dikeluarkan tabel di atas dapat dilihat bahwasanya besar presisi jika dihitung adalah 10/10 untuk rekomendasi Top-10. Ini menunjukan sistem mampu memberikan rekomendasi sesuai dengan Genres Animenya.

### Pengujian Model *Collaborative Filtering*

Evaluasi metrik yang dapat digunakan untuk mengukur kinerja model ini adalah metrik RMSE (*Root Mean Squared Error*). RMSE adalah metode pengukuran dengan mengukur perbedaan nilai dari prediksi sebuah model sebagai estimasi atas nilai yang diobservasi. RMSE dapat dijabarkan melalui pendekatan rumus berikut ini

$$ RMSE =  \sqrt{\frac{\sum_{t=1}^{n}(A_t - F_t)^2}{n}} $$

Dimana:

- $A_t$ : Nilai aktual
- $F_t$ : Nilai hasil prediksi
- n: Banyak data

*Collaborative Filtering* dengan model RecommenderNet memberikan hasil training yang divisualisasikan melalui gambar di bawah ini: 

![alt text](https://github.com/Agim-dudu/Sistem-Rekomendasi---Anime/blob/main/Resource/image-14.png?raw=true)

Dengan epoch sebanyak 100, model ini memperoleh nilai error akhir sebesar sekitar 0.06 untuk training dan error pada data validasi sebesar 0.25. Nilai tersebut cukup bagus untuk sistem rekomendasi.

**Testing Hasil Evaluasi Model Collaborative Filtering model based Deep learning**

| No  | Title                                                   | Genres                          |
|-----|---------------------------------------------------------|---------------------------------|
|     | **Anime dengan rating tertinggi dari pengguna**         |                                 |
| 1   | Final Approach                                          | Comedy, Drama, Romance          |
|-----|---------------------------------------------------------|---------------------------------|
|     | **Rekomendasi 10 anime teratas**                        |                                 |
| 1   | One Piece                                               | Action, Adventure, Fantasy      |
| 2   | s.CRY.ed                                                | Action, Adventure, Drama, Sci-Fi|
| 3   | Slam Dunk                                               | Sports                          |
| 4   | Tactics                                                 | Mystery, Supernatural           |
| 5   | One Piece Film: Strong World                            | Action, Adventure, Fantasy      |
| 6   | Major S5                                                | Sports                          |
| 7   | Naruto: Shippuuden Movie 3 - Hi no Ishi wo Tsugu Mono   | Action, Adventure, Fantasy      |
| 8   | Tegamibachi Reverse                                     | Adventure, Fantasy              |
| 9   | Haikyuu!! Karasuno Koukou vs. Shiratorizawa Gakuen Koukou | Sports                       |
| 10  | Bocchi the Rock!                                        | Comedy                          |

Berdasarkan hasil yang dikeluarkan tabel di atas rekomendasi untuk user dengan id 75809. Dari output tersebut, kita dapat membandingkan antara Anime dengan rating tertinggi dari pengguna dan Rekomendasi 10 anime teratas untuk user 75809.

## Kesimpulan

Dari hasil evaluasi, solusi sistem rekomendasi berbasis Content-Based Filtering dengan Cosine Similarity dan Collaborative Filtering menggunakan model deep learning RecommenderNet menunjukkan bahwa kedua pendekatan ini berhasil mencapai tujuan proyek. Content-Based Filtering memberikan rekomendasi anime yang relevan berdasarkan kesamaan genre dengan presisi tinggi, mencapai rekomendasi Top-10 yang sesuai kategori. Sementara itu, model Collaborative Filtering berbasis RecommenderNet menghasilkan rekomendasi anime berdasarkan pola rating pengguna dengan error yang rendah (RMSE sekitar 0.06 untuk data training dan 0.25 untuk data validasi), menunjukkan kemampuannya dalam memprediksi preferensi pengguna dengan akurat. Secara keseluruhan, kedua pendekatan ini berhasil memberikan rekomendasi yang relevan dan sesuai dengan tujuan utama, yaitu menyediakan rekomendasi anime yang sesuai dengan preferensi genre dan pola rating pengguna.

## Referensi

Wibowo, A. T. (2020, December). *Leveraging side information to anime recommender system using deep learning*. In 2020 3rd International Seminar on Research of Information Technology and Intelligent Systems (ISRITI) (pp. 62-67). [Link](https://ieeexplore.ieee.org/abstract/document/9315363/)

Aisyah, I. (2019). *Anime dan gaya hidup mahasiswa (studi pada mahasiswa yang tergabung dalam Komunitas Japan Freak UIN Jakarta)*. (Bachelor's thesis, Fakultas Ilmu Tarbiyah dan Keguruan UIN Syarif Hidayatullah Jakarta). [Link](https://repository.uinjkt.ac.id/dspace/handle/123456789/45316)

Jayaperwira, I., Wibowo, A. T., & Nurjanah, D. (2023). *Anime rekomendasi menggunakan Collaborative Filtering*. eProceedings of Engineering, 10(3). [Link](https://openlibrarypublications.telkomuniversity.ac.id/index.php/engineering/article/view/20612)

Permadi, V. A., & Raharjo, R. P. (2023). *Improvement of KNN Collaborative Filtering Model in User-based Approach on Anime Recommendation System*. Sistemasi: Jurnal Sistem Informasi, 12(2), 381-389. [Link](https://sistemasi.ftik.unisi.ac.id/index.php/stmsi/article/view/2473)

Roziqiin, N. M., & Faisal, M. (2024). *Sistem rekomendasi pemilihan anime menggunakan user-based collaborative filtering*. JIPI (Jurnal Ilmiah Penelitian dan Pembelajaran Informatika), 9(1), 299-306. [Link](http://www.jurnalstkippgritulungagung.ac.id/index.php/jipi/article/view/4222)

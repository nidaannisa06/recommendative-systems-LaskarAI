# Laporan Proyek Machine Learning - Nida Annisa Sholeha

## Sistem Rekomendasi Anime
## Project Overview
Animasi adalah konten dengan beragam elemen termasuk genre, skenario, gambar, mudik dan voice cover (Ota _et al._, 2017). Sementara itu, istilah anime merujuk pada industri animasi yang berasal dari negara Jepang pada awal abad ke-20 (Modayil, 2023). Gaya penggambaran yang unik membuat industri anime yang berasal dari Jepang ini menjadi populer tidak hanya di negara asalnya tetapi juga di seluruh dunia (Chen, 2025). Popularitas ini semakin meluas seiring dengan perkembangan teknologi digital dan kemudahan akses terhadap internet, yang memungkinkan pengguna dari seluruh dunia menikmati anime melalui layanan streaming daring (Roziqiin & Faisal, 2024). Perkembangan industri anime di luar Jepang dapat diamati melalui ketersediaan konten anime di berbagai platform streaming internasional, seperti Netflix dan Amazon Prime Video (Jayaperwira et al., 2023). Namun, seiring dengan bertambahnya jumlah judul dan variasi genre, penonton sering mengalami kesulitan dalam memilih tontonan yang sesuai dengan minat mereka. Fenomena ini dikenal sebagai paradox of choice, di mana terlalu banyak pilihan justru membuat proses pengambilan keputusan menjadi lebih sulit (Schwartz, 2015).

Untuk mengatasi permasalahan tersebut, dibutuhkan sistem rekomendasi yang mampu menyaring dan menyajikan pilihan anime yang relevan bagi pengguna. Sistem rekomendasi bekerja dengan memanfaatkan informasi dan data historis untuk menyarankan konten yang sesuai dengan preferensi pengguna. Pendekatan ini telah banyak diterapkan dalam berbagai studi sebelumnya. Misalnya, Geetha et al. (2018) mengembangkan sistem rekomendasi film menggunakan metode content-based filtering, collaborative filtering, dan pendekatan hybrid. Sementara itu, Girsang et al. (2020) menerapkan metode collaborative filtering dalam membangun sistem rekomendasi khusus untuk anime. Berdasarkan latar belakang tersebut, penelitian ini bertujuan untuk membangun sistem rekomendasi anime dengan menggunakan pendekatan utama: content-based filtering dan collaborative filtering. Tujuan akhirnya adalah menciptakan sistem rekomendasi yang mampu memberikan saran tontonan yang lebih akurat dan relevan bagi penikmat anime, sekaligus mengurangi beban kognitif dalam memilih konten

Referensi:

Chen, Y. X. (2025). A psychological study on social media use related to anime, comic, and game among adolescents. _Social Science and Management_. _2_(1), 21-24.

Geetha G., Safa, M., Fancy, C. & Saranya, D. (2018). [A hybrid approch using collaborative filtering and content based filtering for recommender system](https://iopscience.iop.org/article/10.1088/1742-6596/1000/1/012101/pdf). _Journal of Physics: Conference Series_, _1000_, 012101. https://doi.org/10.1088/1742-6596/1000/1/012101 

Girsang, A. S., Al Faruq, B., Herlianto, H. R. & Simbolon, S. (2020). [Collaborative Recommendation System in Users of Anime
Films](https://iopscience.iop.org/article/10.1088/1742-6596/1566/1/012057/pdf). _Journal of Physics: Conference Series, 1566_, 012057. https://doi:10.1088/1742-6596/1566/1/012057

Jayaperwira, I., Agung, T. W. & Dade, N. (2023). Anime rekomendasi menggunakan collaborative filtering. _e-Proceeding of Engineering_, _10_(3),3431-3440

Modayil, K. P. (2023). Evolution of contemporary anime in the Japanese pop culture: A study. International Journal of Engineering, Management and Humanities, _4_(2), 261–266.

Ota, S., Hayasaki, K., Masutani, M., Soh, H., & Hori, J. (2017). AniReco: Japanese Anime Recommendation System. Dalam N. Munekata, J. Hoshino, & I. Kunita (Eds.), _Entertainment Computing – ICEC 2017 - 16th IFIP TC 14 International Conference, Proceedings_ (Vol. 10507, pp. 400-403). Springer Verlag.

Roziqiin, N. M. & Faisal, M. (2024). Sistem rekomendasi pemilihan anime menggunakan user-based collaborative filtering. _JIPI (Jurnal Ilmiah Penelitian dan Pembelajaran Informatika)_, _9_(1), 299-306.

Schwartz, B. (2015). The paradox of choice. Positive psychology in practice: Promoting human flourishing in work, health, education, and everyday life, 121-138.

## Business Understanding
### Problem Statements
- Bagaimana cara membantu pengguna menemukan anime yang sesuai dengan preferensi mereka di antara banyaknya pilihan yang tersedia di platform streaming?
- Bagaimana sistem rekomendasi dapat meningkatkan user engagement dan retensi pengguna pada platform streaming anime?
- Bagaimana sistem rekomendasi dapat dimanfaatkan untuk memperluas eksposur anime yang kurang populer kepada audiens yang relevan?

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Membangun sistem rekomendasi yang efektif untuk membantu pengguna menemukan anime yang sesuai dengan preferensi mereka.
- Meningkatkan user engagement dan retensi pengguna pada platform streaming anime dengan menyediakan rekomendasi yang relevan dan personal.
- Meningkatkan eksposur anime yang kurang populer kepada audiens yang relevan.

### Solution statements/Solution approach
    Proyek ini akan mengimplementasikan dua pendekatan utama untuk membangun sistem rekomendasi anime:
1. Content-based Filtering: Pendekatan ini akan merekomendasikan anime kepada pengguna berdasarkan kemiripan fitur-fitur anime tersebut, seperti genre, sinopsis, dan tema. Dengan menganalisis preferensi pengguna terhadap anime yang telah mereka tonton sebelumnya, sistem akan mengidentifikasi anime lain yang memiliki karakteristik serupa dan merekomendasikannya.

2. Collaborative Filtering: Pendekatan ini akan merekomendasikan anime kepada pengguna berdasarkan preferensi pengguna lain yang memiliki pola tontonan yang mirip. Dengan mengidentifikasi kelompok pengguna dengan selera yang serupa, sistem akan merekomendasikan anime yang disukai oleh kelompok tersebut kepada pengguna target.

## Data Understanding
Proyek ini menggunakan dataset [Anime Recommendations Database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database) yang bersumber dari [Kaggle](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database). Dataset terdiri dari dua file .csv yaitu anime.csv dan rating.csv.

- Dataset anime.csv berisi informasi mengenai berbagai anime, seperti judul, genre, tipe, episode, rating, dan anggota. Dataset ini memiliki 12294 baris dan 7 kolom. Kondisi data menunjukkan adanya missing values pada kolom **genre**.

- Dataset rating.csv berisi informasi mengenai rating yang diberikan pengguna untuk anime-anime tersebut. Setiap baris menunjukkan rating seorang pengguna untuk anime tertentu. Dataset ini memiliki 7813737 baris dan 3 kolom. Kondisi data menunjukkan bahwa terdapat nilai "-1" pada kolom **rating** yang mengindikasikan bahwa pengguna tidak benar-benar memberikan rating pada anime tersebut.

Variabel-variabel pada Anime Recommendations Database dataset adalah sebagai berikut:
1. Dataset anime
- anime_id = ID unik dari setiap anime.
- name = Judul anime.
- genre = genre anime.
- type = Tipe tayang anime, seperti TV, OVA, etc.
- episodes = Banyaknya episode setiap anime.
- rating = Rata-rata rating setiap anime terhadap jumlah user yang memberi rating.
- members = Jumlah anggota komunitas setiap anime.

2. Dataset anime_rating
- user_id = ID unik dari setiap user
- anime_id = ID dari anime yang diberi peringkat oleh user
- rating = Rating yang diberikan oleh user.

### Exploratory Data Analysis (EDA):

Beberapa tahapan visualisasi data dan insight yang diperoleh:


### Data Preparation

Berikut adalah teknik-teknik data preparation yang diterapkan dalam proyek ini:

    Penanganan Missing Values pada Kolom genre: Missing values pada kolom genre diisi dengan nilai "Unknown".

    Penghapusan Rating -1 pada rating.csv: Baris-baris dengan nilai "-1" pada kolom rating dihapus karena nilai ini mengindikasikan bahwa pengguna tidak benar-benar memberikan rating.

    Penggabungan Data: Dataset anime.csv dan rating.csv digabungkan menggunakan kolom anime_id untuk menggabungkan informasi anime dengan rating pengguna.

    Pra-pemrosesan Teks pada Kolom genre: Kolom genre diproses menggunakan tokenisasi, penghapusan stop words, dan TF-IDF untuk mengubah data tekstual menjadi representasi numerik yang sesuai untuk pemodelan.

    Pengurangan Ukuran Data untuk Collaborative Filtering: Karena keterbatasan sumber daya, dilakukan pengambilan sampel acak pada data yang telah digabungkan untuk mengurangi ukuran data yang digunakan dalam pemodelan Collaborative Filtering. Selain itu, dilakukan pemfilteran user dan anime berdasarkan jumlah rating.

Tahapan-tahapan data preparation ini diperlukan untuk:

    Memastikan data bersih dan konsisten.

    Menangani missing values yang dapat mengganggu analisis.

    Mengubah data tekstual menjadi format numerik yang dapat dipahami oleh model machine learning.

    Mengurangi ukuran data agar sesuai dengan keterbatasan sumber daya komputasi.

Modeling
Proyek ini mengimplementasikan dua pendekatan sistem rekomendasi:

    Content-based Filtering: Sistem ini merekomendasikan anime berdasarkan kemiripan fitur-fitur anime, khususnya genre. TF-IDF digunakan untuk menghitung representasi numerik dari genre anime, dan cosine similarity digunakan untuk mengukur kemiripan antar anime. Sistem ini menghasilkan top-N recommendation anime yang paling mirip dengan anime yang disukai pengguna.

    Collaborative Filtering: Sistem ini merekomendasikan anime berdasarkan pola rating pengguna. Matriks user-item dibuat dari data rating, dan cosine similarity digunakan untuk mengukur kemiripan antar anime berdasarkan rating yang diberikan pengguna. Sistem ini menghasilkan top-N recommendation anime yang memiliki pola rating serupa dengan anime yang disukai pengguna.

    Hybrid Recommendation: Sistem ini menggabungkan hasil dari Content-based Filtering dan Collaborative Filtering untuk menghasilkan rekomendasi yang lebih baik. Dalam implementasi sederhana ini, skor similaritas dari kedua sistem dijumlahkan untuk mendapatkan skor hybrid, dan top-N recommendation diberikan berdasarkan skor hybrid tertinggi.

Berikut adalah contoh top-N recommendation untuk anime "Naruto":

Content-based Filtering (k=5):

    Naruto: Shippuuden

    Naruto

    Boruto: Naruto the Movie - Naruto ga Hokage ni Naru Hi

    Naruto x UT

    Naruto: Shippuuden Movie 4 - The Lost Tower

Collaborative Filtering (k=5):

    Death Note

    Sword Art Online

    Fullmetal Alchemist

    Code Geass: Hangyaku no Lelouch

    Fullmetal Alchemist: Brotherhood

Hybrid Recommendation (k=5):

    Naruto: Shippuuden

    Naruto

    Boruto: Naruto the Movie - Naruto ga Hokage ni Naru Hi

    Naruto x UT

    Naruto: Shippuuden Movie 4 - The Lost Tower

Kelebihan dan Kekurangan Pendekatan:

    Content-based Filtering:

        Kelebihan: Tidak ada masalah cold-start untuk anime baru, rekomendasi transparan.

        Kekurangan: Membutuhkan informasi fitur yang relevan, tidak dapat merekomendasikan di luar preferensi genre pengguna yang ada.

    Collaborative Filtering:

        Kelebihan: Dapat merekomendasikan anime yang tidak terduga, tidak memerlukan informasi fitur eksplisit.

        Kekurangan: Masalah cold-start untuk pengguna dan anime baru, rentan terhadap masalah sparsity.

    Hybrid Recommendation:

        Kelebihan: Mengatasi beberapa keterbatasan masing-masing pendekatan.

        Kekurangan: Lebih kompleks diimplementasikan.

Evaluation

Jawaban:

Metrik evaluasi yang digunakan dalam proyek ini adalah overlap antara rekomendasi yang dihasilkan oleh Content-based Filtering dan Collaborative Filtering. Overlap dihitung sebagai jumlah anime yang muncul di kedua daftar rekomendasi dibagi dengan panjang daftar rekomendasi. Metrik ini mengukur sejauh mana kedua sistem memberikan rekomendasi yang serupa.

[Sajikan hasil evaluasi overlap Anda di sini. Misalnya: "Hasil evaluasi menunjukkan overlap sebesar 0.3 untuk anime Naruto, yang menunjukkan bahwa 30% dari anime yang direkomendasikan oleh kedua sistem adalah sama."]

Overlap yang tinggi menunjukkan bahwa kedua sistem memberikan rekomendasi yang serupa, yang dapat meningkatkan kepercayaan pengguna terhadap sistem rekomendasi. Overlap yang rendah menunjukkan bahwa kedua sistem memberikan rekomendasi yang berbeda, yang mungkin menunjukkan bahwa mereka menangkap aspek preferensi pengguna yang berbeda.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

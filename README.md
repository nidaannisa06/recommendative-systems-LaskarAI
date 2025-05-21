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
Setelah melakukan proses loading data pada dataset [Anime Recommendations Database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database) ditemukan informasi dataset anime.csv dan rating.csv memiliki total pengguna kurang lebih sebesar 70.000 pengguna pada 12.294 anime. Untuk setiap dataset memiliki beberapa feature, diantaranya:
1. Dataset anime.csv:
   - anime_id: ID unik dari myanimelist.net yang mengidentifikasi sebuah anime.
   - name: nama lengkap anime.
   - genre: daftar genre yang dipisahkan koma untuk anime ini.
   - type: MOVIE, TV, OVA, dll.
   - episodes: jumlah episode dalam acara ini. (1 jika film).
   - rating: peringkat rata-rata dari 10 untuk anime ini.
   - members: jumlah anggota komunitas yang tergabung dalam "grup" anime ini.

2. Dataset rating.csv:
   - user_id: id pengguna yang dibuat secara acak dan tidak dapat diidentifikasi.
   - anime_id: anime yang telah diberi peringkat oleh pengguna ini.
   - rating: peringkat dari 10 yang diberikan oleh pengguna ini (-1 jika pengguna menontonnya tetapi tidak memberikan peringkat).

Selain itu ditemukan juga fakta jika dataset anime.csv memiliki missing value pada kolom genre (62), type (25), dan rating (230). Beberapa tahapan visualisasi data dan insight yang diperoleh:
![Distribusi rating anime](https://github.com/user-attachments/assets/fb6e5665-bfd8-4cc7-99e9-911a1e46a678)
Penjelasan:
Visualisasi ini menampilkan sebagian besar anime memiliki rating antara 6 hingga 8, dengan puncak distribusi berada di sekitar **rating 7**. Distribusi ini cenderung mendekati normal, meskipun *sedikit* miring ke kiri (positively skewed). Rata-rata rating anime adalah 6.47, sementara median rating adalah 6.55. Ini menunjukkan bahwa nilai rata-rata dan median hampir sama, mengkonfirmasi **distribusi yang cukup simetris**.

![Distribusi tipe anime](https://github.com/user-attachments/assets/97c590c0-59c0-4942-b670-279836ce2879)
Penjelasan:
Tipe TV adalah yang paling banyak jumlahnya, diikuti oleh OVA dan Movie. Tipe Special juga memiliki jumlah yang cukup signifikan. Sementara itu, tipe ONA (Original Net Animation) dan Music memiliki jumlah anime yang jauh lebih sedikit dibandingkan tipe lainnya. Ini menunjukkan bahwa serial anime televisi merupakan format yang paling umum dalam dataset ini.

![Top 10 Genre Anime](https://github.com/user-attachments/assets/3d56f2f3-823a-4514-b97e-460efa4c422e)
Penjelasan:
Visualisasi ini menampilkan 10 genre anime teratas berdasarkan jumlah kemunculannya. Terlihat jelas bahwa Comedy adalah genre yang paling dominan, diikuti oleh Action di posisi kedua. Genre-genre seperti Adventure, Fantasy, Sci-Fi, dan Drama juga memiliki jumlah yang cukup signifikan dan relatif berdekatan. Sementara itu, genre Shounen, Kids, Romance, dan Slice of Life memiliki jumlah anime yang lebih sedikit dibandingkan enam genre teratas. Secara keseluruhan, grafik ini memberikan gambaran tentang popularitas dan prevalensi berbagai genre dalam dataset anime.

![Distribusi Rating Pengguna](https://github.com/user-attachments/assets/c860f232-0560-4f9f-8caf-ec56894d9fd1)
Penjelasan:
Terlihat adanya puncak frekuensi yang sangat tinggi pada nilai rating -1. Setelah itu, frekuensi rating cenderung meningkat dari nilai 1 hingga mencapai puncak kedua pada nilai rating 8. Rating 7 dan 9 juga memiliki frekuensi yang tinggi, diikuti oleh rating 10. Rating 1 hingga 5 memiliki frekuensi yang relatif lebih rendah dibandingkan rating di atas 5. Distribusi ini menunjukkan bahwa sebagian besar interaksi pengguna ditandai dengan nilai -1 (yang mungkin mengindikasikan watched atau tidak relevan) dan rating positif di atas 5, dengan preferensi yang kuat pada rating 8.

![Rata-Rata Rating Berdasarkan Tipe Anime](https://github.com/user-attachments/assets/fbbe7385-6e21-4107-9250-7ea4f1b80ef7)
Penjelasan:
Visualisasi ini menampilkan perbandingan distribusi rating berdasarkan tipe anime menggunakan boxplot. Setiap boxplot menunjukkan sebaran rating untuk tipe anime yang berbeda (Movie, TV, OVA, Special, Music, ONA).

Terlihat bahwa secara umum, tidak ada perbedaan dramatis dalam rating rata-rata antar tipe anime, karena median (garis tengah kotak) untuk semua tipe berada di kisaran rating 6 hingga 7. Namun, terdapat perbedaan dalam sebaran rating (panjang kotak) dan jumlah outlier (lingkaran di luar whisker).

Misalnya, tipe Movie dan TV cenderung memiliki sebaran rating yang lebih luas dibandingkan tipe Music dan ONA. Selain itu, beberapa tipe seperti OVA dan Special memiliki lebih banyak outlier di kedua ujung distribusi rating, yang mengindikasikan adanya lebih banyak anime dengan rating yang sangat tinggi atau sangat rendah dalam kategori tersebut dibandingkan tipe lainnya.

![Rata-Rata Rating untuk Top 10 Genre (Alternative)](https://github.com/user-attachments/assets/45076411-a7a2-4af2-b4a2-aec4a73e6a37)
Penjelasan:
Dari visualisasi ini, terlihat bahwa Josei memiliki rata-rata rating tertinggi, diikuti oleh Thriller dan Mystery. Genre Police juga memiliki rata-rata rating yang cukup tinggi. Sementara itu, genre seperti Shounen, Psychological, Military, Romance, Supernatural, dan Drama memiliki rata-rata rating yang sedikit lebih rendah dan relatif berdekatan. Secara keseluruhan, rata-rata rating untuk 10 genre teratas ini berada di atas 6.9, menunjukkan bahwa genre-genre ini umumnya mendapatkan penilaian yang baik dari pengguna. Perbedaan rata-rata rating antar genre teratas ini tidak terlalu signifikan, namun Josei dan Thriller tampak sedikit lebih unggul dalam hal rata-rata rating.


### Data Preparation

Berikut adalah teknik-teknik data preparation yang diterapkan dalam proyek ini:
1. Penanganan Missing Values pada Kolom Dataset
- Jumlah missing value diperiksa pada tiap kolom
```python
# Memeriksa jumlah nilai yang hilang di setiap kolom
print("Jumlah nilai yang hilang sebelum penanganan:")
print(df_anime.isnull().sum())
```
- Ada mising value yang harus diatasi pada kolom genre (62), type (52) dan rating (230).
- Kolom genre dan type memiliki jumlah missing yang relatif sedikit, sehingga baris dengan nilai kosong pada kolom ini dihapus menggunakan .dropna().
```python
# Menghapus baris yang memiliki nilai yang hilang pada kolom 'genre', dan 'type'
df_anime = df_anime.dropna(subset=['genre', 'type'])
```
- Kolom rating memiliki jumlah missing yang lebih besar dan berpotensi mempengaruhi analisis, sehingga nilai kosong diisi dengan modus (nilai rating yang paling sering muncul) menggunakan .fillna().
```python
# Mengisi missing value di kolom rating dengan modus
df_anime['rating'].fillna(df_anime['rating'].mode()[0], inplace=True)
```

2. Pembersihan dan Konversi Kolom 'Episodes'
- Pada tahap Data Preparation, ditemukan adanya nilai non-numerik pada kolom 'episodes' yang menghambat proses Exploratory Data Analysis (EDA), terutama saat mencoba membuat visualisasi atau perhitungan. Untuk mengatasi ini, dilakukan pembersihan data dengan mengidentifikasi nilai non-numerik dan mengubahnya menjadi NaN (Not a Number), kemudian baris yang tidak valid tersebut dihapus. Langkah ini memastikan kolom 'episodes' memiliki tipe data numerik yang konsisten, sehingga data siap untuk analisis dan pemodelan lebih lanjut."

```python
# Memeriksa tipe data kolom 'episodes'
print("Tipe data kolom 'episodes' sebelum perbaikan:")
print(df_anime['episodes'].dtype)

# Memeriksa nilai non-numerik dalam kolom 'episodes'
non_numeric_episodes = df_anime[pd.to_numeric(df_anime['episodes'], errors='coerce').isna()]['episodes'].unique()
print("\nNilai non-numerik dalam kolom 'episodes':")
print(non_numeric_episodes)

# Mengubah nilai non-numerik menjadi NaN, lalu dikonversi menjadi numerik
df_anime['episodes'] = pd.to_numeric(df_anime['episodes'], errors='coerce')

# Drop nilai NaN yang mungkin muncul
# df_anime['episodes'] = df_anime['episodes'].dropna()

# Menghapus baris yang memiliki NaN di kolom 'episodes'
df_anime = df_anime.dropna(subset=['episodes'])

print("\nTipe data kolom 'episodes' setelah perbaikan:")
print(df_anime['episodes'].dtype)
```

3. Penggabungan Data: Dataset anime.csv dan rating.csv digabungkan menggunakan kolom anime_id untuk menggabungkan informasi anime dengan rating yang diberikan pengguna. Hasil penggabungan ini menjadi dasar bagi model collaborative filtering.
```python
# Menggabungkan data rating dengan data anime
merged_df = pd.merge(df_rating, df_anime, on='anime_id', suffixes=['_user', '_anime'])
```

4. Pra-pemrosesan Teks pada Kolom genre: Kolom genre diproses untuk pendekatan content based filtering. Kolom ini diproses menggunakan tokenisasi, penghapusan stop words, dan TF-IDF untuk mengubah data tekstual menjadi representasi numerik yang sesuai untuk pemodelan. Sintaks yang digunakan:

```python
# Pra-pemrosesan genre untuk Content-Based Filtering (Tokenisasi Dasar + Stop Words Removal)
stop_words = set(stopwords.words('english'))
def simple_process_text_with_stopwords(text):
    words = [word.lower() for word in text.split(', ')]
    words = [w for w in words if not w in stop_words]
    return ' '.join(words)
df_anime['processed_genre'] = df_anime['genre'].apply(simple_process_text_with_stopwords)
```
Tahapan-tahapan data preparation ini diperlukan untuk:
- Memastikan data bersih dan konsisten.
- Menangani missing values yang dapat mengganggu analisis.
- Mengubah data tekstual menjadi format numerik yang dapat dipahami oleh model machine learning.

# Modeling
Proyek ini mengimplementasikan dua pendekatan sistem rekomendasi:
1. Content-based Filtering: Sistem ini merekomendasikan anime berdasarkan kemiripan fitur-fitur anime, khususnya genre. TF-IDF digunakan untuk menghitung representasi numerik dari genre anime, dan cosine similarity digunakan untuk mengukur kemiripan antar anime. Sistem ini menghasilkan top-N recommendation anime yang paling mirip dengan anime yang disukai pengguna.
```python
# Inisialisasi TF-IDF Vectorizer
tfidf = TfidfVectorizer(stop_words='english')

# Menghasilkan matriks TF-IDF dari genre yang sudah diproses
tfidf_matrix = tfidf.fit_transform(df_anime['processed_genre'])

# Cosine similarity
cosine_sim_content = linear_kernel(tfidf_matrix, tfidf_matrix)
indices_content = pd.Series(df_anime.index, index=df_anime['name']).drop_duplicates()

def get_content_based_recommendations(title, cosine_sim=cosine_sim_content, df_anime=df_anime, indices=indices_content, k=5):
    if title not in indices:
        print(f"Anime '{title}' tidak ditemukan dalam dataset.")
        return None
    idx = indices[title]
    sim_scores = list(enumerate(cosine_sim[idx]))
    sim_scores = sorted(sim_scores, key=lambda x: x[1], reverse=True)
    sim_scores = sim_scores[1:k+1]
    anime_indices = [i[0] for i in sim_scores]
    recommendations_df = df_anime[['name', 'genre']].iloc[anime_indices].copy()
    recommendations_df['similarity_score'] = [i[1] for i in sim_scores]
    return recommendations_df

print("\nContoh Rekomendasi Content-Based untuk 'Death Note':")
print(get_content_based_recommendations("Death Note"))
```
Penjelasan:
    Kode ini mengimplementasikan sistem rekomendasi Content-Based Filtering berdasarkan genre anime. Pertama, menggunakan TF-IDF untuk mengubah genre anime menjadi vektor numerik. Kemudian, menghitung kemiripan antar anime berdasarkan vektor genre menggunakan cosine similarity. Terakhir, fungsi get_content_based_recommendations mengambil judul anime dan mengembalikan k anime paling mirip berdasarkan genre.

| No. | Judul Anime                    | Genre                                                                 | Similarity Score |
|-----|-------------------------------|------------------------------------------------------------------------|------------------|
| 1   | Death Note Rewrite            | Mystery, Police, Psychological, Supernatural, Thriller                 | 1.000000         |
| 2   | Mousou Dairinin               | Drama, Mystery, Police, Psychological, Supernatural, Thriller          | 0.967733         |
| 3   | Higurashi no Naku Koro ni Kai| Mystery, Psychological, Supernatural, Thriller                         | 0.879675         |
| 4   | Higurashi no Naku Koro ni Rei| Comedy, Mystery, Psychological, Supernatural, Thriller                 | 0.861303         |
| 5   | Mirai Nikki (TV)             | Action, Mystery, Psychological, Shounen, Supernatural, Thriller        | 0.815700         |


    Output menunjukkan 5 anime teratas yang direkomendasikan untuk "Death Note" berdasarkan kemiripan genre. "Death Note Rewrite" memiliki skor similaritas tertinggi (1.000000), diikuti oleh "Mousou Dairinin", "Higurashi no Naku Koro ni Kai", "Higurashi no Naku Koro ni Rei", dan "Mirai Nikki (TV)", beserta skor similaritas dan genre masing-masing. Rekomendasi ini didasarkan pada analisis kemiripan teks genre antar anime.

2. Collaborative Filtering: Sistem ini merekomendasikan anime berdasarkan pola rating pengguna. Matriks user-item dibuat dari data rating, dan cosine similarity digunakan untuk mengukur kemiripan antar anime berdasarkan rating yang diberikan pengguna. Sistem ini menghasilkan top-N recommendation anime yang memiliki pola rating serupa dengan anime yang disukai pengguna.

| No. | Judul Anime                          | Similarity Score |
|-----|--------------------------------------|------------------|
| 1   | Code Geass: Hangyaku no Lelouch      | 0.694266         |
| 2   | Code Geass: Hangyaku no Lelouch R2   | 0.668456         |
| 3   | Elfen Lied                            | 0.655481         |
| 4   | Shingeki no Kyojin                    | 0.645156         |
| 5   | Fullmetal Alchemist: Brotherhood      | 0.639580         |

Output menunjukkan 5 anime teratas yang direkomendasikan untuk "Death Note" berdasarkan pola rating pengguna yang serupa. "Code Geass: Hangyaku no Lelouch" memiliki skor kemiripan tertinggi (0.694266), diikuti oleh "Code Geass: Hangyaku no Lelouch R2", "Elfen Lied", "Shingeki no Kyojin", dan "Fullmetal Alchemist: Brotherhood", beserta skor kemiripannya. Rekomendasi ini didasarkan pada preferensi pengguna lain yang juga menyukai "Death Note".

Berikut adalah kelebihan dan kekurangan Pendekatan:
1. Content-based Filtering:
A. Kelebihan:
- Tidak Membutuhkan Data Pengguna Lain: Sistem dapat memberikan rekomendasi kepada pengguna baru (cold-start user) selama ada informasi genre anime. Dalam kasus Anda, selama anime memiliki informasi genre, rekomendasi dapat diberikan.
- Transparansi Rekomendasi: Alasan di balik rekomendasi relatif mudah dipahami. Pengguna dapat melihat bahwa anime direkomendasikan karena memiliki genre yang mirip dengan anime yang mereka sukai di masa lalu (dalam contoh, genre "Mystery, Police, Psychological, Supernatural, Thriller" untuk "Death Note").
- Mampu Merekomendasikan Anime Baru: Sistem dapat merekomendasikan anime baru yang memiliki genre serupa dengan preferensi pengguna, bahkan jika anime tersebut belum banyak ditonton atau di-rating.
- Fokus pada Minat Pengguna: Rekomendasi sangat dipersonalisasi berdasarkan riwayat preferensi genre pengguna. Jika seorang pengguna menyukai anime dengan genre psikologis dan thriller, sistem akan cenderung merekomendasikan anime dengan genre serupa.

B. Kekurangan:
- Keterbatasan pada Informasi Genre: Efektivitas sistem sangat bergantung pada kualitas dan detail informasi genre. Jika genre terlalu umum atau kurang deskriptif, kemiripan yang diukur mungkin tidak terlalu bermakna.
- Potensi Over-Specialization: Sistem cenderung merekomendasikan anime yang sangat mirip dalam genre. Pengguna mungkin kehilangan kesempatan untuk menemukan anime dari genre lain yang mungkin mereka sukai. Misalnya, jika seseorang hanya menonton shonen aksi, sistem mungkin tidak akan pernah merekomendasikan slice of life yang mungkin juga mereka nikmati.
- Tidak Memanfaatkan Preferensi Pengguna Lain: Sistem ini hanya mempertimbangkan riwayat preferensi genre pengguna itu sendiri dan mengabaikan informasi dari pengguna lain dengan selera yang mungkin serupa namun menyukai anime dengan kombinasi genre yang berbeda.
- Kurang Mempertimbangkan Aspek Subjektif: Kesukaan terhadap anime tidak hanya ditentukan oleh genre. Aspek seperti storytelling, karakter, animasi, dan mood juga berperan penting dan tidak tercakup dalam pendekatan berbasis genre ini.

2. Collaborative Filtering:
A. Kelebihan:
- Dapat Menangkap Preferensi yang Kompleks: Sistem dapat merekomendasikan anime berdasarkan pola rating pengguna lain yang memiliki selera serupa, bahkan jika kemiripan genre tidak terlalu kuat. Ini memungkinkan penemuan preferensi yang lebih halus dan tidak terbatas pada atribut konten eksplisit.
- Potensi untuk Penemuan (Discovery): Sistem dapat merekomendasikan anime yang mungkin tidak terduga oleh pengguna berdasarkan riwayat genre mereka, tetapi disukai oleh pengguna lain dengan pola rating yang mirip.
- Memanfaatkan Wisdom of the Crowd: Rekomendasi didasarkan pada preferensi banyak pengguna, sehingga dapat menangkap tren dan selera yang lebih luas.

B. Kekurangan:
- Masalah Cold-Start: Sistem kesulitan memberikan rekomendasi kepada pengguna baru (tanpa riwayat rating) atau untuk anime baru (belum banyak di-rating).
- Data Sparsity: Jika user-item matrix (matriks rating) sangat jarang (sebagian besar pengguna hanya me-rating sebagian kecil anime), kualitas rekomendasi dapat menurun karena sulit menemukan pengguna atau item yang serupa.
- Masalah Scalability: Menghitung kemiripan antar pengguna atau item dalam dataset yang besar bisa menjadi mahal secara komputasi.
- Potensi Popularity Bias: Sistem cenderung merekomendasikan anime yang populer karena anime tersebut kemungkinan besar di-rating oleh banyak pengguna, sehingga item yang kurang populer mungkin kurang direkomendasikan meskipun relevan untuk sebagian kecil pengguna.
- Masalah Filter Bubble: Pengguna mungkin hanya terpapar pada anime yang mirip dengan apa yang disukai oleh pengguna lain dengan pola rating yang serupa, yang dapat membatasi keragaman rekomendasi.

## 3. Top-N Recommendation

### A. Content-Based Filtering

#### Top 3 Recommendation
| No. | Judul Anime                                           | Genre                                              | Similarity Score |
|-----|-------------------------------------------------------|----------------------------------------------------|------------------|
| 1   | Naruto: Shippuuden                                   | Action, Comedy, Martial Arts, Shounen, Super Power| 1.000000         |
| 2   | Naruto                                                | Action, Comedy, Martial Arts, Shounen, Super Power| 1.000000         |
| 3   | Boruto: Naruto the Movie - Naruto ga Hokage ni Natta Hi | Action, Comedy, Martial Arts, Shounen, Super Power| 1.000000         |

#### Top 5 Recommendation
| No. | Judul Anime                                           | Genre                                              | Similarity Score |
|-----|-------------------------------------------------------|----------------------------------------------------|------------------|
| 1   | Naruto: Shippuuden                                   | Action, Comedy, Martial Arts, Shounen, Super Power| 1.000000         |
| 2   | Naruto                                                | Action, Comedy, Martial Arts, Shounen, Super Power| 1.000000         |
| 3   | Boruto: Naruto the Movie - Naruto ga Hokage ni Natta Hi | Action, Comedy, Martial Arts, Shounen, Super Power| 1.000000         |
| 4   | Naruto x UT                                           | Action, Comedy, Martial Arts, Shounen, Super Power| 1.000000         |
| 5   | Naruto: Shippuuden Movie 4 - The Lost Tower           | Action, Comedy, Martial Arts, Shounen, Super Power| 1.000000         |

#### Top 10 Recommendation
| No. | Judul Anime                                                                 | Genre                                                   | Similarity Score |
|-----|-----------------------------------------------------------------------------|----------------------------------------------------------|------------------|
| 1   | Naruto: Shippuuden                                                         | Action, Comedy, Martial Arts, Shounen, Super Power       | 1.000000         |
| 2   | Naruto                                                                      | Action, Comedy, Martial Arts, Shounen, Super Power       | 1.000000         |
| 3   | Boruto: Naruto the Movie - Naruto ga Hokage ni Natta Hi                     | Action, Comedy, Martial Arts, Shounen, Super Power       | 1.000000         |
| 4   | Naruto x UT                                                                 | Action, Comedy, Martial Arts, Shounen, Super Power       | 1.000000         |
| 5   | Naruto: Shippuuden Movie 4 - The Lost Tower                                 | Action, Comedy, Martial Arts, Shounen, Super Power       | 1.000000         |
| 6   | Naruto: Shippuuden Movie 3 - Hi no Ishi wo Tsugu Mono                       | Action, Comedy, Martial Arts, Shounen, Super Power       | 1.000000         |
| 7   | Naruto Shippuuden: Sunny Side Battle                                        | Action, Comedy, Martial Arts, Shounen, Super Power       | 1.000000         |
| 8   | Naruto Soyokazeden Movie: Naruto to Mashin to Mitsu no Onegai Dattebayo!!  | Action, Comedy, Martial Arts, Shounen, Super Power       | 1.000000         |
| 9   | Kyutai Panic Adventure!                                                    | Action, Martial Arts, Shounen, Super Power               | 0.980763         |
| 10  | Naruto: Shippuuden Movie 6 - Road to Ninja                                  | Action, Adventure, Martial Arts, Shounen, Super Power    | 0.947325         |

---

### B. Collaborative Filtering

#### Top 3 Recommendation
| No. | Judul Anime                | Similarity Score |
|-----|----------------------------|------------------|
| 1   | Death Note                 | 0.615486         |
| 2   | Sword Art Online          | 0.539170         |
| 3   | Fullmetal Alchemist       | 0.538463         |

#### Top 5 Recommendation
| No. | Judul Anime                        | Similarity Score |
|-----|------------------------------------|------------------|
| 1   | Death Note                         | 0.615486         |
| 2   | Sword Art Online                   | 0.539170         |
| 3   | Fullmetal Alchemist                | 0.538463         |
| 4   | Code Geass: Hangyaku no Lelouch    | 0.535956         |
| 5   | Fullmetal Alchemist: Brotherhood   | 0.535899         |

#### Top 10 Recommendation
| No. | Judul Anime                          | Similarity Score |
|-----|--------------------------------------|------------------|
| 1   | Death Note                           | 0.615486         |
| 2   | Sword Art Online                     | 0.539170         |
| 3   | Fullmetal Alchemist                  | 0.538463         |
| 4   | Code Geass: Hangyaku no Lelouch      | 0.535956         |
| 5   | Fullmetal Alchemist: Brotherhood     | 0.535899         |
| 6   | Bleach                               | 0.533249         |
| 7   | Shingeki no Kyojin                   | 0.531056         |
| 8   | Ao no Exorcist                       | 0.515478         |
| 9   | Code Geass: Hangyaku no Lelouch R2   | 0.514340         |
| 10  | Dragon Ball Z                        | 0.509128         |


Penjelasan:
- Content-Based Filtering: Untuk "Naruto", sistem Content-Based secara konsisten merekomendasikan sekuel, film, dan episode spesial dari seri "Naruto" itu sendiri dengan skor similaritas sempurna (1.0), karena mereka berbagi genre yang sama persis. Ketika k ditingkatkan menjadi 10, rekomendasi mulai mencakup anime lain dengan genre yang serupa namun tidak terkait langsung, seperti "Kyutai Panic Adventure!" dan "Naruto: Shippuuden Movie 6 - Road to Ninja", dengan skor similaritas yang sedikit lebih rendah.

B. Collaborative Filtering: Rekomendasi dari Collaborative Filtering untuk "Naruto" sangat berbeda dan mencakup anime populer seperti "Death Note", "Sword Art Online", "Fullmetal Alchemist", "Code Geass", "Bleach", dan "Shingeki no Kyojin". Anime-anime ini direkomendasikan berdasarkan pola rating pengguna yang serupa dengan pengguna yang menyukai "Naruto". Skor similaritas dalam Collaborative Filtering relatif lebih rendah dibandingkan dengan Content-Based, menunjukkan tingkat kemiripan preferensi pengguna yang bervariasi.

# Evaluation
A. Content Based Filtering
```python
mean_precision_cb, mean_recall_cb = evaluate_model_efficient('content_based', filtered_merged_df, k_values=[5, 10], sample_users=sample_users)
print("\n--- Hasil Evaluasi Content-Based Filtering (Sample) ---")
for k in [5, 10]:
    print(f"Precision@{k}: {mean_precision_cb.get(f'precision@{k}', 0):.4f}")
    print(f"Recall@{k}: {mean_recall_cb.get(f'recall@{k}', 0):.4f}")
```

Output:
### Hasil Evaluasi Content-Based Filtering

| Metric        | @5     | @10    |
|---------------|--------|--------|
| Precision     | 0.1174 | 0.0717 |
| Recall        | 0.0078 | 0.0102 |

B. Collaborative Filtering
```python
mean_precision_cf, mean_recall_cf = evaluate_model_efficient('collaborative', filtered_merged_df, k_values=[5, 10], sample_users=sample_users)
print("\n--- Hasil Evaluasi Collaborative Filtering (Sample) ---")
for k in [5, 10]:
    print(f"Precision@{k}: {mean_precision_cf.get(f'precision@{k}', 0):.4f}")
    print(f"Recall@{k}: {mean_recall_cf.get(f'recall@{k}', 0):.4f}")
```

Output:
### Hasil Evaluasi Collaborative Filtering (Sample)

| Metric        | @5     | @10    |
|---------------|--------|--------|
| Precision     | 0.3130 | 0.2804 |
| Recall        | 0.0301 | 0.0470 |

Penjelasan Kedua Pendekatan:
Kode yang telah dieksekusi bertujuan untuk mengevaluasi kinerja dua pendekatan sistem rekomendasi anime: Content-Based Filtering (CBF) dan Collaborative Filtering (CF). Evaluasi dilakukan dengan menghitung metrik precision@k dan recall@k pada sampel acak 50 pengguna dari dataset.

Untuk model Content-Based Filtering, hasil evaluasi menunjukkan precision@5 sebesar 0.1174 dan recall@5 sebesar 0.0077. Ini berarti bahwa dari 5 rekomendasi teratas yang diberikan oleh model CBF, sekitar 11.74% di antaranya relevan dengan preferensi pengguna. Sementara itu, model CBF berhasil merekomendasikan sekitar 0.77% dari total anime yang relevan bagi pengguna dalam 5 rekomendasi teratasnya. Pada k=10, precision menurun menjadi 0.0718, dan recall meningkat menjadi 0.0102.

Untuk model Collaborative Filtering, hasil evaluasi pada sampel yang sama menunjukkan kinerja yang lebih rendah dibandingkan CBF. Precision@5 tercatat sebesar 0.0308 dan recall@5 sebesar 0.0020. Ini mengindikasikan bahwa hanya sekitar 3.08% dari 5 rekomendasi teratas CF yang relevan, dan model ini hanya mencakup 0.20% dari total anime yang relevan dalam 5 rekomendasi teratasnya. Pada k=10, precision menjadi 0.0204 dan recall menjadi 0.0027.

Insight dari Output Kode:

  - Performa Relatif Model: Pada sampel 50 pengguna ini, model Content-Based Filtering secara signifikan mengungguli model Collaborative Filtering dalam hal precision dan recall. Ini menunjukkan bahwa berdasarkan fitur konten anime yang digunakan (kemungkinan judul dan/atau genre), model CBF lebih baik dalam memberikan rekomendasi yang relevan bagi pengguna dibandingkan dengan model CF dengan konfigurasi saat ini.

  - Akurasi Rekomendasi Awal (Precision): Precision yang lebih tinggi pada CBF mengindikasikan bahwa rekomendasi teratasnya lebih akurat dan cenderung sesuai dengan preferensi pengguna dibandingkan dengan rekomendasi dari CF.

  - Kemampuan Menangkap Seluruh Item Relevan (Recall): Nilai recall yang rendah untuk kedua model menunjukkan bahwa keduanya masih memiliki keterbatasan dalam mencakup seluruh anime yang mungkin relevan bagi pengguna. Ini bisa menjadi area untuk perbaikan lebih lanjut.

  - Pengaruh Nilai K: Seperti yang umum terjadi, precision cenderung menurun dan recall cenderung meningkat saat nilai k (jumlah rekomendasi yang dipertimbangkan) bertambah.

  - Potensi Masalah pada CF: Kinerja CF yang jauh lebih rendah mungkin disebabkan oleh sparsity data rating, masalah cold start, atau implementasi algoritma CF yang kurang optimal untuk dataset ini. Perlu dilakukan analisis lebih lanjut pada implementasi CF dan karakteristik data interaksi pengguna.

  - Validitas Sampel: Penting untuk diingat bahwa hasil ini didasarkan pada sampel 50 pengguna. Evaluasi pada sampel yang lebih besar atau seluruh dataset akan memberikan gambaran kinerja yang lebih stabil dan representatif.

Secara keseluruhan, output kode memberikan indikasi awal bahwa Content-Based Filtering mungkin menjadi pendekatan yang lebih efektif untuk sistem rekomendasi anime pada dataset ini, setidaknya dengan konfigurasi model saat ini. Namun, perlu dilakukan eksplorasi lebih lanjut untuk meningkatkan kinerja Collaborative Filtering.

# Kesimpulan
Laporan ini menguraikan proses pengembangan dan evaluasi sistem rekomendasi anime menggunakan pendekatan Content-Based Filtering (CBF) dan Collaborative Filtering (CF). Tujuan utama proyek ini adalah untuk mengatasi masalah kelebihan pilihan (paradox of choice) yang dihadapi pengguna platform streaming anime dan meningkatkan pengalaman pengguna melalui rekomendasi yang dipersonalisasi dan akurat.

Berdasarkan evaluasi awal menggunakan metrik precision@k dan recall@k pada sampel pengguna, model Content-Based Filtering menunjukkan kinerja yang lebih baik dalam memberikan rekomendasi yang relevan dibandingkan dengan model Collaborative Filtering dengan konfigurasi saat ini. CBF terbukti lebih akurat dalam rekomendasi teratasnya, meskipun kedua model masih memiliki keterbatasan dalam hal recall.

Kinerja CF yang relatif rendah mengindikasikan adanya potensi masalah seperti sparsity data atau kebutuhan untuk penyesuaian lebih lanjut pada implementasi dan parameter model. Eksplorasi lebih lanjut dan eksperimen dengan teknik CF yang lebih canggih, serta potensi pendekatan hibrida yang menggabungkan kekuatan CBF dan CF, direkomendasikan untuk meningkatkan kualitas rekomendasi secara keseluruhan.

Sistem rekomendasi yang efektif memiliki potensi signifikan untuk meningkatkan user engagement, retensi pengguna, dan memberikan eksposur yang lebih luas kepada beragam judul anime, termasuk yang kurang populer. Evaluasi yang berkelanjutan dan penyempurnaan model berdasarkan feedback pengguna akan menjadi kunci dalam mencapai tujuan ini dan memberikan pengalaman menonton anime yang lebih memuaskan dan personal.

### Penjelasan Metrik Evaluasi

#### Precision@k

- **Definisi**: Mengukur seberapa akurat *k* rekomendasi teratas yang diberikan oleh model.
- **Formula**:

![Precision@k](https://github.com/user-attachments/assets/78fc1165-6092-4046-bb2b-a16649702881)

- **Cara Kerja**: 
  Metrik ini menghitung proporsi dari *k* rekomendasi teratas yang benar-benar relevan atau disukai oleh pengguna. 
  Nilai Precision@k yang tinggi menunjukkan bahwa sistem memberikan rekomendasi yang tepat sasaran di posisi atas.

#### Recall@k

- **Definisi**: Mengukur seberapa banyak anime relevan yang berhasil direkomendasikan oleh model dari semua anime yang relevan untuk pengguna.
- **Formula**:

![Recall@k](https://github.com/user-attachments/assets/15437420-5ae2-49b6-90d8-855448e1a215)

- **Cara Kerja**: 
  Metrik ini menunjukkan seberapa baik model dalam mencakup seluruh preferensi pengguna. 
  Nilai Recall@k yang tinggi berarti model mampu merekomendasikan sebagian besar anime yang memang disukai oleh pengguna.

Catatan: Precision fokus pada **akurasi** dari rekomendasi yang diberikan, sedangkan Recall fokus pada **cakupan** dari rekomendasi terhadap seluruh item relevan.

**---Ini adalah bagian akhir laporan---**

# Laporan Proyek Machine Learning - Nama Anda

## 1. Project Overview

### Latar Belakang

Industri game telah berkembang cukup pesat dalam beberapa tahun terakhir. Hal ini dapat dipengaruhi oleh berbagai hal, seperti akses internet yang semakin mudah, perkembangan teknologi, serta popularitas eSport. Pada tahun 2017, pendapatan dari penjualan game oleh industri game terhitung sebesar $108.9 milyar USD.[^1] Di tahun 2018, terdapat sekitar 2 milyar pemain game aktif di seluruh dunia.[^2] Di Indonesia sendiri, pasar game di Indonesia masih tergolong muda. Meskipun begitu,  Indonesia tercatat telah mencapai jumlah yang sangat tinggi di tahun 2017, yakni $880 juta USD.[^3]

Perkembangan ini menciptakan peluang baru bagi pengembang dan penerbit game, tetapi juga tantangan dalam menjangkau dan mempertahankan pemain. Selain itu, dengan jumlah game yang tersedia di pasaran saat ini, menemukan game yang tepat untuk dimainkan bisa menjadi tantangan bagi banyak pengguna. Sistem rekomendasi game dapat membantu memecahkan masalah ini dengan memberikan saran yang disesuaikan dengan preferensi setiap pengguna. Hal ini tidak hanya meningkatkan pengalaman bermain game pengguna, tetapi juga membantu pengembang dan penerbit game untuk menargetkan game mereka kepada audiens yang tepat.

Tujuan proyek ini adalah untuk mengembangkan sistem rekomendasi game yang menggunakan dua pendekatan, yakni Content-Based Filtering (CBF) dan Collaborative Filtering (CF). CBF menganalisis konten game, seperti genre, tema, mekanisme gameplay, dan visual, untuk merekomendasikan game yang mirip dengan game yang disukai pengguna. CF menganalisis data rating dan interaksi pengguna dengan game untuk merekomendasikan game yang disukai pengguna lain dengan minat yang serupa.

## Business Understanding

### Problem Statements
Berdasarkan latar belakang di atas, perlu dikembangkan sebuah sistem rekomendasi game untuk menjawab permasalahan berikut:
- Berdasarkan data mengenai game, bagaimana perusahaan dapat merekomendasikan game serupa dengan teknik content-based filtering?
- Berdasarkan data review game, bagaimana perusahaan dapat merekomendasikan game yang mungkin disukai dan belum pernah dimainkan oleh pengguna?

### Goals
Untuk menjawab pertanyaan tersebut, sistem rekomendasi dibuat dengan tujuan atau *goals* sebagai berikut:
- Menghasilkan sejumlah rekomendasi game dengan teknik content-based filtering
- Menghasilkan sejumlah rekomendasi game yang sesuai dengan preferensi pengguna dan belum pernah dimainkan sebelumnya.

Keberhasilan proyek ML untuk rekomendasi game akan memberikan manfaat signifikan bagi bisnis, di antaranya:
- Keterjangkauan game baru ke pengguna, terutama dari penerbit yang berpotensi berkembang
- Memudahkan menemukan game yang tepat untuk dimainkan bagi pengguna

### Solution statements
Untuk mencapai tujuan tersebut, solusi yang perlu dilakukan adalah sebagai berikut:
- Mengembangkan sistem rekomendasi game dengan pendekatan Content-Based Filtering (CBF)
- Mengembangkan sistem rekomendasi game dengan pendekatan Collaborative Filtering (CF)

## Data Understanding

Dataset yang digunakan adalah [Game Recommendations on Steam](https://www.kaggle.com/datasets/antonkozyriev/game-recommendations-on-steam/data) oleh Anton Kozyriev. Dataset ini mengandung tiga kategori data, yakni data game, data user, dan data review atau recommendation user terhadap game. Pada dataset, terdapat 50.872 data game berbeda, 14.306.064 data user, dan 41.154.794 data review.

### Deskripsi Variable

Variable pada data game adalah sebagai berikut:
 - app_id: Id unik setiap game
 - title: Judul dari game
 - description: Deskripsi pada game
 - date_release: Tanggal rilis dari game
 - tags: Daftar tag yang diberikan pada game. Tag dapat mewakili genre game seperti tag "Horror", "RPG", dan "Puzzle", maupun sifat game secara umum seperti "Well-Written" , "Wholesome", dan "Indie". Satu game dapat memiliki lebih dari satu tag
 - win: Data boolean, apakah game tersedia untuk Windows
 - mac: Data boolean, apakah game tersedia untuk MacOS
 - linux: Data boolean, apakah game tersedia untuk Linux
 - steam_deck: Data boolean, apakah game tersedia untuk Steam Deck
 - rating: Rating sentiment dari game, mulai dari "_overwhelmingly positive_" hingga "_overwhelmingly negative_"
 - positive_ratio: Persentase feedback pada game yang bersifat positif 
 - user_reviews: Jumlah review pada game
 - price_original: Harga game sebelum diskon, dalam satuan USD
 - discount: Persentase diskon yang diberikan pada game
 - price_final: Harga game setelah diskon, dalam satuan USD

Variable pada data user adalah sebagai berikut:
- user_id: Id unik setiap user
- products: Jumlah game/add-ons yang dibeli user
- reviews: Jumlah review yang dibuat oleh user

Variable pada data review adalah sebagai berikut:
- review_id: Id unik setiap review
- app_id: Id dari game yang diberi review
- user_id: Id dari user yang memberi review
- is_recommended: Data boolean, apakah user merekomendasikan game ini ke user lain
- helpful: Berapa user yang merasa review ini berguna (helpful)
- funny: Berapa user yang merasa review ini menghibur atau lucu (funny)
- date: Tanggal dibuatnya review
- hours: Berapa jam user telah memainkan game tersebut

Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

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

## Referensi:

[^1]:	J. Che, “Study on videogame industry and its general developing trend,” in Proceedings at the 5th annual conference on business, economics, and management, 2018.
[^2]:	R. Baltezarević, B. Baltezarević, and V. Baltezarević, “The video gaming industry: From play to revenue,” Int. Rev., no. 3–4, pp. 71–76, 2018.
[^3]:	A. Mulachela, “Analisis Perkembangan Industri Game di Indonesia Melalui Pendekatan Rantai Nilai Global (Global Value Chain),” Indones. J. Glob. Discourse, vol. 2, no. 2, pp. 32–51, Dec. 2020, doi: 10.29303/ijgd.v2i2.17.

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
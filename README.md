# LAPORAN PROYEK SISTEM REKOMENDASI - AHMAD FAUZI

## Domain Proyek

Pandemi COVID-19 telah memberikan dampak signifikan terhadap industri retail global, terutama pada sektor usaha kecil yang mengandalkan interaksi fisik dengan pelanggan. Banyak toko buku kecil mengalami penurunan drastis dalam jumlah pelanggan karena pembatasan aktivitas publik dan perpindahan konsumen ke platform daring. Menurut [Mehta et al. 2021](https://www.frontiersin.org/journals/public-health/articles/10.3389/fpubh.2020.582932/full), adaptasi teknologi digital menjadi krusial bagi usaha kecil agar dapat bertahan dalam kondisi ekonomi yang sulit. Untuk menanggulangi penurunan interaksi langsung, toko-toko buku semakin mengandalkan e-commerce dan teknologi untuk menjangkau pelanggan, meningkatkan pengalaman berbelanja, serta membangun koneksi melalui alternatif daring, termasuk sistem rekomendasi berbasis data yang lebih personal [Mehta et al., 2021](https://www.frontiersin.org/journals/public-health/articles/10.3389/fpubh.2020.582932/full).

Sistem rekomendasi yang efektif dapat membantu toko daring untuk menarik minat pelanggan dengan menampilkan produk yang relevan, yang sesuai dengan preferensi unik mereka. Rekomendasi yang dipersonalisasi terbukti meningkatkan loyalitas pelanggan dan memperpanjang durasi interaksi di platform e-commerce [Zhang & Luo, 2022](https://centuryscipub.com/index.php/jtpes/article/view/493). Di bidang machine learning, pendekatan seperti content-based filtering dan collaborative filtering adalah teknik yang umum digunakan untuk mempersonalisasi pengalaman pelanggan. Dengan demikian, toko buku memiliki peluang untuk menerapkan sistem rekomendasi berbasis machine learning guna mempertahankan basis pelanggannya dan meningkatkan keterlibatan pelanggan baru di platform daring mereka.

Namun, pelaksanaan sistem rekomendasi untuk usaha kecil menghadirkan tantangan tersendiri, terutama dalam hal sumber daya data dan biaya implementasi. [Li et al. 2023](https://www.sciencedirect.com/science/article/pii/S0012825223000259?via%3Dihub) mengemukakan bahwa model yang efektif perlu dirancang dengan mempertimbangkan efisiensi computational dan keterbatasan data yang sering ditemui dalam usaha kecil. Dengan mengadopsi pendekatan yang hemat sumber daya, toko buku dapat mengembangkan model rekomendasi yang otomatis namun tetap relevan bagi pelanggannya, tanpa memerlukan intervensi manual yang intensif. Mengembangkan sistem rekomendasi berbasis machine learning yang responsif dan efisien tidak hanya akan membantu toko tersebut dalam mempertahankan kualitas layanan personalnya, tetapi juga akan meningkatkan daya saingnya di pasar daring yang semakin kompetitif.

## Business Understanding
Pandemi COVID-19 telah memberikan dampak signifikan terhadap industri retail global, terutama pada sektor usaha kecil yang mengandalkan interaksi fisik dengan pelanggan. Banyak toko buku kecil mengalami penurunan drastis dalam jumlah pelanggan karena pembatasan aktivitas publik dan perpindahan konsumen ke platform daring.
### Problem Statements
* Rekomendasi buku dilakukan langsung melalui pengamatan preferensi pelanggan, namun hal ini tidak lagi efisien di platform daring.
* Dengan meningkatnya jumlah katalog dan pelanggan, pendekatan manual menjadi tidak cukup untuk memberikan rekomendasi yang relevan.
* Bagaimana membuat sistem rekomendasi, dalam menjaga toko buku tidak kehilangan peluang untuk menarik minat pelanggan dan meningkatkan penjualan secara efektif.
### Goals
* Mengganti pendekatan manual dengan model rekomendasi berbasis data yang lebih efisien untuk memahami minat pelanggan.
* Memberikan rekomendasi buku yang relevan dan personal untuk menarik minat pelanggan dan meningkatkan konversi penjualan.
* Membantu toko buku kecil beradaptasi dengan perubahan menuju layanan daring, mengurangi ketergantungan pada interaksi fisik.
### Solution statements
* Menggunakan Content-Based Filtering untuk Rekomendasi Buku Berdasarkan Preferensi Individu: Menggunakan data seperti genre, penulis, dan tema buku yang disukai pelanggan untuk merekomendasikan buku serupa, membantu menciptakan pengalaman personal tanpa interaksi fisik langsung.
* Menggunakan Collaborative Filtering untuk Menyediakan Rekomendasi Berdasarkan Preferensi Pengguna Lain: Mengidentifikasi pola pembelian atau rating dari pelanggan dengan minat serupa untuk menawarkan rekomendasi buku yang relevan, meningkatkan peluang konversi penjualan.
## Data Understanding
Dalam tahapan Data Understanding, kita akan berfokus pada pemahaman mendalam terhadap dataset yang digunakan untuk proyek Sistem Rekomendasi Buku. Data diambil dari [Kaggle](https://www.kaggle.com/) [Book Recommendation](https://www.kaggle.com/datasets/oscarm524/book-recommendation), dataset terdiri dari tiga file csv dan satu file pdf, tiga file csv yaitu items.csv, transactions.csv, dan evalutation.csv. Sementara data file pdf adalah features_2021.pdf yang berisi informasi dari variabel dataset. 
> Berikut merupakan keterangan atau penjelasan dari masing-masing data:
> * File “items.csv” adalah kumpulan data induk yang berisi fitur deskriptif. Fitur tersebut dapat berupa kategoris atau numerik. Daftar fitur dijelaskan dalam file “features.pdf”. Setiap baris data berisi deskripsi untuk satu item.
> * File “transactions.csv” berisi informasi tentang klik, keranjang, dan pesanan selama periode tiga bulan. Setiap baris menampilkan satu transaksi untuk satu item. Semua atribut dijelaskan dalam file “features.pdf”.
> * File “evalutation.csv” berisi daftar ID produk. Daftar ini merupakan bagian dari produk dari “items.csv” dan referensi untuk pengajuan.
> Untuk melakukan rekomendasi buku variabel items dan transaksi yang akan digunakan sebagai variabel rekomendasi, sementara variabel evaluasi merupakan daftar nama itemID yang nantinya akan digabungkan pada variabel items.

Pada masing-masing dataset terdapat variabel yang sama dan berbeda seperti pada data **item** terdiri dari itemID, title,	author,	publisher,	main topic,	subtopics. Untuk data **transactions** terdiri dari sessionID,	itemID,	click,	basket,	order. Dan untuk data evaluation terdiri dari 	itemID.
Berikut tabel penjelasan variabel pada dataset buku;
| No | Variabel	| Deskripsi |
| -- | -------- | --------- |
| 1 | sessionID | Sesi atau kunjungan customer pada setiap transaksi |
| 2 | itemID | ID atau kode pada setiap Buku |
| 3 | click | Interaksi dari setiap buku yang dikunjungi atau dilihat |
| 4 | basket | Interaksi dari memasukan buku yang dipilih kedalam keranjang belanja |
| 5 | order | Interaksi customer yang melakukan pembelian |
| 6 | author | Pengarang atau penulis buku |
| 7 | publisher | Penerbit Buku |
| 8 | main topic | Kategori Tema atau topik buku |
| 9 | subtopics | Gabungan dari beberapa Kategori Tema atau topik buku |

## Data Preprocessing
Pertama pada tahap ini menggabungkan data evaluation dengan data items pada variabel itemID, dengan nama evaluation_all. hal ini untuk melihat nama pada masing-masing itemID yang terdapat pada data evaluation. parameter yang digunakan adalah:
* **on:** Parameter on digunakan untuk menentukan nama kolom atau list kolom yang akan digunakan sebagai kunci penggabungan, dalam kasus ini kita menggunkan variabel "itemID"
* **how:** Parameter how digunakan untuk menentukan metode penggabungan yang akan digunakan dalam kasus ini kta menggunakan "left"
> Ada empat opsi untuk parameter how:
> * **inner:** Menggabungkan hanya baris-baris yang memiliki nilai yang sama pada kolom kunci di kedua DataFrame. Ini adalah metode default jika parameter how tidak ditentukan.
> * **left:** Menggabungkan semua baris dari DataFrame kiri (df1) dengan baris-baris dari DataFrame kanan (df2) yang memiliki nilai yang sama pada kolom kunci. Jika ada baris di DataFrame kiri yang tidak memiliki nilai yang sama di DataFrame kanan, maka nilai kolom di DataFrame kanan akan diisi dengan NaN.
> * **right:** Menggabungkan semua baris dari DataFrame kanan (df2) dengan baris-baris dari DataFrame kiri (df1) yang memiliki nilai yang sama pada kolom kunci. Jika ada baris di DataFrame kanan yang tidak memiliki nilai yang sama di DataFrame kiri, maka nilai kolom di DataFrame kiri akan diisi dengan NaN.
> **outer:** Menggabungkan semua baris dari kedua DataFrame. Jika ada baris di salah satu DataFrame yang tidak memiliki nilai yang sama di DataFrame lainnya, maka nilai kolom di DataFrame lainnya akan diisi dengan NaN.

Langkah Selanjutnya kita akan menggabungkan data evaluation_all dengan data transaksi. tujuan penggabungan ini untuk melihat nama itemID yang dikunjungi pada setiap sesi dalam data transaksi. untuk parameter **on** menggunakan itemID dan **how** menggunkan inner. Berikut hasilnya:

Lik Gambar

Sampai langkah ini kita sudah dapat melihat nama buku apa saja yang dilihat pada setiap sesi dalam transaksi, namun ada hal yang sedikit menggangu dalam melihat sesinya yaitu variabel sessionID berada ditengah untuk memudahkan dalam melihat data maka kita akan memindahkan variabel sessionID kedepan atau pada kolom pertama berdampingan dengan itemID.

Setelah kita melihat data yang akan dijadikan data rekomendasi buku terlebih dahulu kita melihat missing value pada data kita, karena pada langkah diatas kita melihat missing value pada data maka dalam tahap ini akan kita selesaikan dan bersihkan datanya.

link gambar

Terlihat data missing pada 3 variabel yaitu variabel author, publisher dan main topic. karena data bertipe object dan keterbatasan dalam pengetahuan data maka data yang memiliki missing value akan dihapus.

Link Gambar

Setelah dihapus data berjumlah 5579 data dengan 10 kolom, dan sudah terlihat juga data yang kita miliki sudah bersih atau tidak ada lagi missing value.

Sebelum melangkah lebih jauh kita akan melihat berapa jumlah buku berdasarkan itemID.

Link Gambar

Dari gambar diatas dapat diketahu total jumlah buku sebanyak 448, kita juga dapat melihat isi dari judul buku tersebut. 

Selanjutnya, kita hanya akan menggunakan data unik untuk dimasukkan ke dalam proses pemodelan. Oleh karena itu, kita perlu menghapus data yang duplikat dengan fungsi drop_duplicates(). Dalam hal ini, kita membuang data duplikat pada kolom ‘itemID’. Dari hasil terdapat kolom subtopics yang tidak terlalu mempengaruhi data karena sudah ada pada kategory main topik maka kita akan menghapus kolom subtopic.

Setelah data tidak ada lagi yang duplikat dan lain sebagainya selanjutnya kita akan merubah nama pada variabel atau kolom dan mengkonversinya dalam berbagai bentuk yaitu:
* Merubah nama pada variabel atau kolom dalam bentuk list.
* Membuat dictionary untuk menentukan pasangan key-value pada data id, judul_buku, penulis_buku, penerbit_buku dan topik_buku yang telah kita siapkan sebelumnya.

  > Saran:
    > Simpan Data pada drive yang sudah bersih dan siap digunakan untuk memudahkan dalam membuat sistem rekomendasi.

## Model Development
Terdapat beberapa teknik dalam membuat sistem rekomendasi, rekomendasi yang diberikan berdasarkan kesamaan pengguna atau berdasarkan kesamaan pada variabel yang dipilih oleh para pengguna. Dalam sistem rekomendasi ini kita akan membuat dengan dua teknik sistem rekomendasi yang umum digunakan yaitu:
* content based filterin
* collaborative filtering

### Model Development Content Based Filtering 

Dalam tahap inilah Anda mengembangkan sistem rekomendasi dengan teknik content based filtering. Ingatlah, teknik content based filtering akan merekomendasikan item yang mirip dengan item yang disukai pengguna di masa lalu. Pada tahap ini, Anda akan menemukan representasi fitur penting dari setiap kategori buku dengan tfidf vectorizer dan menghitung tingkat kesamaan dengan cosine similarity. Setelah itu, Anda akan membuat sejumlah rekomendasi buku berdasarkan kesamaan yang telah dihitung sebelumnya. Pada Content Based Filtering kita dapat membuat sistem rekomendasi berdasarkan satu variabel kunci dan dengan banyak variabel kunci.
> Berikut adalah langkah-langkah Content-Based Filtering:
> 1. Pengumpulan Data: Kumpulkan data deskriptif (fitur) dari setiap item, seperti judul, genre, atau sinopsis.
> 2. Ekstraksi Fitur: Ubah data deskriptif menjadi vektor fitur menggunakan teknik seperti TF-IDF atau word embeddings.
> 3. Pembangunan Profil Pengguna: Buat profil pengguna berdasarkan rata-rata fitur dari item yang disukai atau diberi rating tinggi oleh pengguna.
> 4. Pengukuran Kemiripan: Hitung kemiripan antara profil pengguna dan setiap item menggunakan Cosine Similarity atau Euclidean Distance.
> 5. Pembuatan Rekomendasi: Pilih item dengan kemiripan tertinggi sebagai rekomendasi dan pastikan item tersebut belum pernah dilihat oleh pengguna.
> 6. Evaluasi dan Penyempurnaan: Evaluasi hasil rekomendasi untuk memastikan akurasi, kemudian lakukan penyesuaian pada model jika diperlukan.

* Membuat sistem rekomendasi dengan teknik Content Based Filtering dengan satu variabel kunci, dimana variabel yang dijadikan rujukan adalah variabel **topik_buku**. berikut langkahnya:
  * Langkah pertama kita akan memanggil data buku yang sudag dibersihan diatas yaitu df_buku.
  * Langkah kedua melakukan vektorisasi pada variabel topik_buku menggunakan TFIDF. berikut hasilnya:
    ![TFIDF](https://github.com/user-attachments/assets/aab403d6-ee09-408e-a9c1-eb8b1136c2cd)

    > F-IDF (Term Frequency-Inverse Document Frequency) adalah teknik dalam pemrosesan bahasa alami (NLP) yang digunakan untuk mengubah teks menjadi representasi numerik atau vektor. Ini adalah metode yang populer untuk mengekstraksi fitur dari teks dan mengukur pentingnya suatu kata dalam sebuah dokumen relatif terhadap kumpulan dokumen (corpus).

Selanjutnya, lakukan fit dan transformasi ke dalam bentuk matriks.
![FIT](https://github.com/user-attachments/assets/0e87f010-04d9-4b77-ab47-222f50b95f92)

Perhatikanlah, matriks yang kita miliki berukuran (448, 108). Nilai 448 merupakan ukuran data dan 108 merupakan matrik topik_buku.
Untuk menghasilkan vektor tf-idf dalam bentuk matriks, kita menggunakan fungsi todense().

> **Fit dan Transform**
> Fungsi .fit() mempelajari kosakata dari seluruh korpus, mencatat kata-kata unik, dan menghitung IDF untuk setiap kata. Setelah itu, .transform() akan mengonversi dokumen-dokumen dalam korpus menjadi representasi vektor berbasis nilai TF-IDF sesuai dengan kosakata yang dipelajari.



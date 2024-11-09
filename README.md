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


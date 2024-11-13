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
* Menggunakan Content-Based Filtering untuk Rekomendasi Buku Berdasarkan Preferensi Individu: Menggunakan data seperti judul buku, penulis, dan topik buku yang disukai pelanggan untuk merekomendasikan buku serupa, membantu menciptakan pengalaman personal tanpa interaksi fisik langsung.
* Collaborative Filtering: Gunakan interaksi pelanggan (buku yang dibaca atau diberi rating) untuk memberi skor dan merekomendasikan buku berdasarkan kesamaan perilaku pengguna. Sistem ini akan menyarankan buku yang disukai oleh pelanggan dengan preferensi serupa.
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
| 3 | title | Judul buku untuk masing-masing itemID |
| 4 | click | Interaksi dari setiap buku yang dikunjungi atau dilihat |
| 5 | basket | Interaksi dari memasukan buku yang dipilih kedalam keranjang belanja |
| 6 | order | Interaksi customer yang melakukan pembelian |
| 7 | author | Pengarang atau penulis buku |
| 8 | publisher | Penerbit Buku |
| 9 | main topic | Kategori Tema atau topik buku |
| 10 | subtopics | Gabungan dari beberapa Kategori Tema atau topik buku |

* Berikut informasi mengenai jumlah data ,tipe data dan informasi data pada dataset tansaksi:

![Info transaksi](https://github.com/user-attachments/assets/fe504596-4189-4d2b-a34f-2c6393c66efc)

* Melihat missing value pada dataset transaksi:

![Missing evaluasi transaksi](https://github.com/user-attachments/assets/ce918016-df19-4151-9b2b-24b362ea6433)

* Berikut informasi mengenai jumlah data ,tipe data dan informasi data pada dataset item:

![info item](https://github.com/user-attachments/assets/612ed634-c648-465d-b2bc-d5e9f3843cc1)

* Melihat missing value pada dataset item:

![missing item](https://github.com/user-attachments/assets/431030d5-ec10-444e-b4d6-cb688e4bc3e0)

* Berikut informasi mengenai jumlah data ,tipe data dan informasi data pada dataset evaluasi:

![info evaluasi](https://github.com/user-attachments/assets/a0a7a21a-de22-418d-8405-e8d4251cc5d3)

* Melihat missing value pada dataset evaluasi:

![Hasil missing evaluasi transaksi](https://github.com/user-attachments/assets/3a7a4152-df90-4e9f-a6ae-ffa53ebb143d)

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

![evaluasi transaksi](https://github.com/user-attachments/assets/432ad515-ed69-4627-816a-996fabc8d6d6)

Sampai langkah ini kita sudah dapat melihat nama buku apa saja yang dilihat pada setiap sesi dalam transaksi, namun ada hal yang sedikit menggangu dalam melihat sesinya yaitu variabel sessionID berada ditengah untuk memudahkan dalam melihat data maka kita akan memindahkan variabel sessionID kedepan atau pada kolom pertama berdampingan dengan itemID.

Setelah kita melihat data yang akan dijadikan data rekomendasi buku terlebih dahulu kita melihat missing value pada data kita, karena pada langkah diatas kita melihat missing value pada data maka dalam tahap ini akan kita selesaikan dan bersihkan datanya.

![Missing evaluasi transaksi](https://github.com/user-attachments/assets/79695e89-11f7-4d96-bc90-f5d4a6d91d93)


Terlihat data missing pada 3 variabel yaitu variabel author, publisher dan main topic. karena data bertipe object dan keterbatasan dalam pengetahuan data maka data yang memiliki missing value akan dihapus.

![Hasil missing evaluasi transaksi](https://github.com/user-attachments/assets/c5bca3eb-807b-4c1a-a999-2ad73cfd820a)


Setelah dihapus data berjumlah 5579 data dengan 10 kolom, dan sudah terlihat juga data yang kita miliki sudah bersih atau tidak ada lagi missing value.

Sebelum melangkah lebih jauh kita akan melihat berapa jumlah buku berdasarkan itemID.

![Total Buku](https://github.com/user-attachments/assets/c127793c-812b-4323-aad9-db1af3210df0)


Dari gambar diatas dapat diketahu total jumlah buku sebanyak 448, kita juga dapat melihat isi dari judul buku tersebut. 

Selanjutnya, kita hanya akan menggunakan data unik untuk dimasukkan ke dalam proses pemodelan. Oleh karena itu, kita perlu menghapus data yang duplikat dengan fungsi drop_duplicates(). Dalam hal ini, kita membuang data duplikat pada kolom ‘itemID’. Dari hasil terdapat kolom subtopics yang tidak terlalu mempengaruhi data karena sudah ada pada kategory main topik maka kita akan menghapus kolom subtopic.

Setelah data tidak ada lagi yang duplikat dan lain sebagainya selanjutnya kita akan merubah nama pada variabel atau kolom dan mengkonversinya dalam berbagai bentuk yaitu:
* Merubah nama pada variabel atau kolom dalam bentuk list.
* Membuat dictionary untuk menentukan pasangan key-value pada data id, judul_buku, penulis_buku, penerbit_buku dan topik_buku yang telah kita siapkan sebelumnya.

  > Saran:
    > Simpan Data pada drive yang sudah bersih dan siap digunakan untuk memudahkan dalam membuat sistem rekomendasi.

Selanjutnya melakukan vektorisasi pada variabel topik_buku menggunakan TFIDF. berikut hasilnya:

![TFIDF](https://github.com/user-attachments/assets/aab403d6-ee09-408e-a9c1-eb8b1136c2cd)

> F-IDF (Term Frequency-Inverse Document Frequency) adalah teknik dalam pemrosesan bahasa alami (NLP) yang digunakan untuk mengubah teks menjadi representasi numerik atau vektor. Ini adalah metode yang populer untuk mengekstraksi fitur dari teks dan mengukur pentingnya suatu kata dalam sebuah dokumen relatif terhadap kumpulan dokumen (corpus).

Lakukan fit dan transformasi ke dalam bentuk matriks.

![FIT](https://github.com/user-attachments/assets/0e87f010-04d9-4b77-ab47-222f50b95f92)

Perhatikanlah, matriks yang kita miliki berukuran (448, 108). Nilai 448 merupakan ukuran data dan 108 merupakan matrik topik_buku. Untuk menghasilkan vektor tf-idf dalam bentuk matriks, kita menggunakan fungsi todense().

> **Fit dan Transform**
> 
> Fungsi .fit() mempelajari kosakata dari seluruh korpus, mencatat kata-kata unik, dan menghitung IDF untuk setiap kata. Setelah itu, .transform() akan mengonversi dokumen-dokumen dalam korpus menjadi representasi vektor berbasis nilai TF-IDF sesuai dengan kosakata yang dipelajari.

Selanjutnya, mari kita lihat matriks tf-idf untuk beberapa buku (judul_buku) dan topik buku (topik_buku). hal ini untuk mengetahui hubungan antar variabel berikut hasilnya:

![Hasil Tfidf](https://github.com/user-attachments/assets/70a09487-d1a8-4e14-8051-d9cb521d6446)

Output matriks tf-idf di atas menunjukkan judul buku Companions memiliki kategori topik buku fd. Companions, matriks menunjukan bahwa judul buku tersebut merupakan buku dengan topik fd. Hal ini terlihat dari nilai matriks 1.0 pada topik buku fd.

Selanjutnya, untuk membuat sistem rekomendasi dengan collaborative filtering dataset yang akan digunakan adalah data transactions.csv dan data data buku yang sudah dibersihkan diatas.

Dalam data transactions, Data tidak memiliki variabel rating sebagai variabel kunci dari rekomendasi, namun kita bisa menganggap variabel klik, basket, dan order sebagai bentuk interaksi antara pengguna dan item (buku), dan menghitung skor implicit feedback untuk mewakili "ketertarikan" pengguna terhadap buku.

> Implicit feedback adalah data yang dikumpulkan secara tidak langsung dari tindakan pengguna, seperti riwayat pembelian, klik, atau tampilan halaman, yang menunjukkan preferensi mereka tanpa meminta peringkat atau ulasan eksplisit. Data ini digunakan dalam sistem rekomendasi untuk memahami preferensi pengguna dan memberikan rekomendasi yang relevan.
>
> Ada beberapa cara untuk membangun sistem rekomendasi berbasis implicit feedback: Pendekatan 1: Skoring Berdasarkan Interaksi Anda bisa membuat skor ketertarikan untuk setiap interaksi, misalnya:
> * Klik: 1 poin
> * Basket: 2 poin
> * Order: 3 poin
> * Skor ini akan menggambarkan tingkat ketertarikan pengguna pada suatu item. Misalnya, jika pengguna mengklik buku, skor ketertarikannya 1, jika memasukkan ke keranjang jadi 2, dan jika melakukan order, skornya 3.

![data transaksi](https://github.com/user-attachments/assets/7f4663aa-ed13-40c8-a4e0-748bbac12635)

Isi dari data transactions yaitu terdapat 4 vriabel sessionID, itemID, click, basket, order.

Selanjutnya kita akan menggabungkan data yang memiliki itemID yang sama, hal ini cukup penting karena akan membuat data lebih bersih dan tidak ada lagi data yang sama.

![transaksi data sama](https://github.com/user-attachments/assets/a42cc13e-f8f6-4c4e-b96f-da864ca33d70)

Hasil penggabungan dari data menghasilkan jumlah data menjadi 24909 baris dan 5 columns. 

Langkah selanjutnya adalah menghitung nilai bobot untuk semua jenis interaksi pada variabel click, basket, dan order. Berikut hasilnya:

![score](https://github.com/user-attachments/assets/60085949-048f-4be6-9925-9b5f45a4fb90)

Sampai disini kita sudah berhasil membuat data untuk teknik collaborative filtering menggunakan score yang dihasilkan dari penjumlahan interaksi pada variabel klik, basket, dan order.

Langkah persiapan lainnya adalah kita akan Mengubah sessionID menjadi list tanpa nilai yang sama, Melakukan encoding userID, dan Melakukan proses encoding angka ke ke userID.

```
#Mengubah sessionID menjadi list tanpa nilai yang sama
session_ids = df['sessionID'].unique().tolist()
print('list sessionID: ', session_ids)
#Melakukan encoding userID
session_to_session_encoded = {x: i for i, x in enumerate(session_ids)}
print('encoded sessionID : ', session_to_session_encoded)
#Melakukan proses encoding angka ke ke userID
session_encoded_to_session = {i: x for i, x in enumerate(session_ids)}
print('encoded angka ke sessionID: ', session_encoded_to_session)

```
Langkah berikutnya kita lakukan langkah yang sama pada variabel itemID yaitu menjadikan list, Melakukan encoding.

```
#Mengubah itemID menjadi list tanpa nilai yang sama
item_ids = df['itemID'].unique().tolist()
print('list itemID: ', item_ids)
#Melakukan encoding itemID
buku_to_buku_encoded = {x: i for i, x in enumerate(item_ids)}
print('encoded itemID : ', buku_to_buku_encoded)
#Melakukan proses encoding angka ke ke itemID
buku_encoded_to_buku = {i: x for i, x in enumerate(item_ids)}
print('encoded angka ke itemID: ', buku_encoded_to_buku)

```
Langkah selanjutnya Mapping sessionID ke dataframe session dan Mapping itemID ke dataframe buku. berikut hasilnya:

```
#Mapping sessionID ke dataframe session
df['session'] = df['sessionID'].map(session_to_session_encoded)
#Mapping itemID ke dataframe buku
df['buku'] = df['itemID'].map(buku_to_buku_encoded)
#Melihat dataframe
df.head()

```
![mapping](https://github.com/user-attachments/assets/d76f2ea0-0f38-4393-a944-5e7f34b0e771)

Dalam collaborative filtering sebelum melakukan rekomendasi terlebih dahulu Mendapatkan jumlah session pada data, Mendapatkan jumlah buku, Mengubah interaction_score menjadi nilai float, Nilai minimum interaction_score, Nilai maksimal interaction_score. Berikut hasilnya:

![image](https://github.com/user-attachments/assets/a57d5532-c51d-4386-b8ab-bfc6ab563901)

> Saran:
> kita dapat menyimpan data yang sudah dimapping ke drive.

Langkah selanjutnya kita akan mengacak data yang sudah di mapping tadi untuk menmberikan data yang lebih bervariasi

```
# Mengacak dataset
df = df.sample(frac=1, random_state=42)
df

```

![data acak](https://github.com/user-attachments/assets/573b4c6e-6401-4746-a9a6-f7955ad554b7)

**Membagi Data untuk Training dan Validasi**

Pada tahap ini kita akan melakukan pembagian data menjadi data training dan validasi. Kita bagi data train dan validasi dengan komposisi 80:20. Namun sebelumnya, kita perlu memetakan (mapping) data session dan buku menjadi satu value terlebih dahulu. dan score sebagai value y.

```
#Membuat variabel x untuk mencocokkan data session dan buku menjadi satu value
x = df[['session', 'buku']].values
#Membuat variabel y untuk membuat interaction_score dari hasil
y = df['score'].apply(lambda x: (x - min_rating) / (max_rating - min_rating)).values

```
```
# Membagi menjadi 80% data train dan 20% data validasi
train_indices = int(0.8 * df.shape[0])
x_train, x_val, y_train, y_val = (
    x[:train_indices],
    x[train_indices:],
    y[:train_indices],
    y[train_indices:]
)

print(x, y)
```
Setelah data siap kita akan melakukan modeling data dengan masing-masing teknik dalam sistem rekomendasi.

## Model Development
Terdapat beberapa teknik dalam membuat sistem rekomendasi, rekomendasi yang diberikan berdasarkan kesamaan pengguna atau berdasarkan kesamaan pada variabel yang dipilih oleh para pengguna. Dalam sistem rekomendasi ini kita akan membuat dengan dua teknik sistem rekomendasi yang umum digunakan yaitu:
* content based filterin
* collaborative filtering

### Model Development Content Based Filtering 

Terdapat dua pendekatan pada content based filtering yaitu:

* Content Based Filtering dengan satu variabel kunci.
* Content Based Filtering dengan banyak variabel kunci.

> Dalam content-based filtering dengan satu variabel kunci, sistem rekomendasi menggunakan satu karakteristik utama, seperti topik buku dalam rekomendasi buku atau film. Sistem ini membandingkan variabel kunci yang sama antar item untuk menemukan kesamaan, sehingga dapat memberikan rekomendasi yang sesuai dengan preferensi pengguna terhadap variabel tunggal ini.
>
> Namun, pendekatan ini sering kali terlalu sederhana karena tidak mempertimbangkan informasi tambahan yang relevan. Misalnya, jika hanya menggunakan genre, sistem mungkin melewatkan faktor lain seperti penulis atau gaya bahasa yang juga dapat memengaruhi preferensi pengguna.
>
> Di sisi lain, content-based filtering dengan banyak variabel kunci melibatkan penggunaan beberapa karakteristik atau fitur dari item untuk menghasilkan rekomendasi, seperti genre, penulis, tahun terbit, dan sinopsis pada buku. Dengan lebih banyak variabel, sistem dapat memberikan rekomendasi yang lebih kaya dan sesuai karena mempertimbangkan berbagai aspek yang mungkin relevan bagi pengguna.

* Evaluasi content based filtering dengan Matrix Precision: Evaluasi sistem rekomendasi menggunakan precision menilai seberapa tepat rekomendasi yang diberikan sistem terhadap kebutuhan pengguna. Dalam konteks sistem rekomendasi, precision mengukur persentase item yang direkomendasikan dan relevan di antara seluruh item yang direkomendasikan oleh sistem. Secara formal, precision dihitung sebagai rasio antara jumlah item relevan yang direkomendasikan (true positives) dengan total item yang direkomendasikan:

![image](https://github.com/user-attachments/assets/2d941b40-7fb1-4e83-be25-5e4be67d2725)

**Content Based Filtering dengan satu variabel kunci**

Pada tahap Data Preprocessing kita berhasil mengidentifikasi korelasi antara **judul buku dengan topik buku**. Sekarang, kita akan menghitung derajat kesamaan (similarity degree) antar judul buku dengan teknik cosine similarity. Di sini, kita menggunakan fungsi cosine_similarity dari library sklearn.

![Cosin](https://github.com/user-attachments/assets/d098ba25-29d2-4560-b7bf-8ba6f21351c4)

Pada kode diatas, kita menghitung cosine similarity dataframe tfidf_matrix yang kita peroleh pada tahapan sebelumnya. Dengan satu baris kode untuk memanggil fungsi cosine similarity dari library sklearn, kita telah berhasil menghitung kesamaan (similarity) antar buku. Kode di atas menghasilkan keluaran berupa matriks kesamaan dalam bentuk array.

> **Cosine Similarity**
> Cosine Similarity adalah metrik yang digunakan untuk mengukur kesamaan antara dua vektor dalam ruang berdimensi tinggi. Dalam konteks pemrosesan bahasa alami dan rekomendasi, cosine similarity sering digunakan untuk menilai kemiripan antara dua dokumen teks atau antara item dalam sistem rekomendasi berdasarkan fitur-fitur tertentu.
> Cosine similarity menghitung cosine dari sudut antara dua vektor dalam ruang vektor. Hasil perhitungan akan memberikan nilai antara -1 dan 1:
> * 1 berarti vektor benar-benar identik.
> * 0 berarti tidak ada kesamaan (sudut 90°).
> * -1 menunjukkan kebalikan sempurna (dalam beberapa konteks, biasanya jarang terjadi).

**Mendapatkan Rekomendasi Content Based Filtering dengan satu variabel kunci**

Pada langkah Sebelumnya, kita telah memiliki data similarity (kesamaan) antar judul buku. Kini, tibalah saatnya menghasilkan sejumlah judul buku yang akan direkomendasikan kepada pembaca. Untuk lebih memahami bagaimana cara kerjanya, lihatlah kembali matriks similarity pada tahap sebelumnya. Sebagai gambaran, mari kita ambil satu contoh berikut.

![rekomendasi](https://github.com/user-attachments/assets/e154d552-bb10-47ae-9a2f-e19f6c588f02)

> **Keterangan Gambar:**
> 
> Pengguna X pernah memesan buku **The Complete Works Of H.P Lovecraft** Kemudian, saat pengguna tersebut berencana untuk memesan buku dengan judul lain, sistem akan merekomendasikan sesuai topik yang dipesan sebalumnya yaitu **A Song of Ice and Fire 05. A Dance with Dragon, dan Gefangen in den Universen.** Nah, rekomendasi kedua buku ini berdasarkan kesamaan yang dihitung dengan cosine similarity pada tahap sebelumnya.

Di sini, kita membuat fungsi buku_recommendations dengan beberapa parameter sebagai berikut:

* Judul_buku : Nama Judul Buku (index kemiripan dataframe).
* Similarity_data : Dataframe mengenai similarity yang telah kita definisikan sebelumnya.
* Items : Nama dan fitur yang digunakan untuk mendefinisikan kemiripan, dalam hal ini adalah **‘judul_buku’ dan ‘topik_buku’.**
* k : Banyak rekomendasi yang ingin diberikan.

> Ingatlah kembali definisi sistem rekomendasi yang menyatakan bahwa keluaran sistem ini adalah berupa top-N recommendation.
> 
> Oleh karena itu, kita akan memberikan sejumlah rekomendasi buku pada pengguna yang diatur dalam parameter k.
> 
> Dalam sistem rekomendasi ini akan menggunakan kita menggunakan **nilai k=5**.

![image](https://github.com/user-attachments/assets/47c333c9-ecd3-41be-b1cd-7f33d0afb5f8)

> Perhatikanlah, dengan menggunakan argpartition, kita mengambil sejumlah nilai k tertinggi dari similarity data (dalam kasus ini: dataframe cosine_sim_df).
>
> Kemudian, kita mengambil data dari bobot (tingkat kesamaan) tertinggi ke terendah. Data ini dimasukkan ke dalam variabel closest.
>
> Berikutnya, kita perlu menghapus judul_buku yang yang dicari agar tidak muncul dalam daftar rekomendasi. Dalam kasus ini, nanti kita akan mencari judul buku yang mirip dengan Von der Erde zum Mond, sehingga kita perlu drop judul_buku Von der Erde zum Mond agar tidak muncul dalam daftar rekomendasi yang diberikan nanti.

Setelah membuat parameter pada sistem rekomendasi, Selanjutnya, dapat kita terapkan untuk menemukan rekomendasi buku yang mirip dengan yang dipesan customer dalam percobaan ini kita akan melihat rekomendasi dari pemesanan buku **Von der Erde zum Mond**. Berikut Hasilnya:

```
df_buku[df_buku.judul_buku.eq('Von der Erde zum Mond')]

```

![rekomendasi buku 1](https://github.com/user-attachments/assets/5951e6d2-369b-457a-bfa6-fa65b0abf097)

Dari gambar diatas kita bisa lihat buku dengan judul **Von der Erde zum Mond** yang sudah dipesan memiliki topik buku **FBC**. Sehingga hasil rokemdasi nantinya akan terkait dengan topik yang memiliki nilai **F B dan C**. Barikut hasil dari 5 rekomendasi berdasarkan topik buku:

```
# Mendapatkan rekomendasi buku yang mirip dengan Von der Erde zum Mond
buku_recommendations('Von der Erde zum Mond')

```

![5 rekomendasi](https://github.com/user-attachments/assets/e908a5ee-b84f-4fa9-9a21-a66a63a74421)

**SELAMAT** Kita sudah berhasil membuat rekomendasi buku berdasarkan dari topik buku.

## **Evaluasi Hasil Rekomendasi**

Dari Hasil dapat bahwa judul buku yang memilki topik yang sama pada judul Von der Erde zum Mond adalah Dune (Classics Hardcover) dan Durch die Wüste kedua masuk ke dalam topik FBC. Mari kita evaluasi hasil tersebut dengan Matrix Precision untuk sistem rekomendasi dengan teknik content based filtering:

* Jumlah rekomendasi = 5
* Jumlah Hasil rekomendasi dengan topik yang sama = 2

Precision = #of recomendation that are relevant / #of item we recommend

Precision = 2/5

Precision = 0.4 (40%)

> Hasil belum cukup baik namun yang harus dipahami pada proyek ini adalah setiap topik memiliki lebih dari 1 topik dan kalau dilihat topik buku Von der Erde zum Mond merupakan gabungan dari topik F B dan C, sehingga sebenarnya hasil rekomendasi mewakili dari salah satu topik buku Von der Erde zum Mond.

**Content Based Filtering dengan Banyak Variabel Kunci**

Selanjutnya kita akan membuat sistem rekomendasi dengan teknik content based filtering dengan banyak variabel. langkah awal adalah dengan menentukan variabel yang akan dijadikan kunci dari pencarian pada sistem rekomendasi. Pada Tahap ini kita akan mencoba melakukan rekomendasi buku dengan lebih dari satu variabel kunci yaitu variabel:

* penulis_buku.
* penerbit_buku.
* topik_buku.

Adapun langkah awal adalah dengan menggabungkan 3 varibel tertsebut menjadi satu kolom  dengan nama **combined_features** sebagai variabel yang akan divektorisasi. vektorisasi yang digunakan masih sama yaitu menggunakan tf-idf.

![image](https://github.com/user-attachments/assets/8228d601-153d-424b-bf95-9446164a4a9c)

Setelah Variabel berhasil digabungkan dengan nama **"combined_features"** selanjutnya kita akan melakukan vektorisasi data pada variabel **"combined_features"**.

Selanjutnya, mari kita lihat matriks tf-idf untuk beberapa buku pada variabel judul_buku dan (combined_features). 

![matrik tfidf](https://github.com/user-attachments/assets/4ad90a65-8992-4451-8489-47c158448ecc)

> Output matriks tf-idf di atas menunjukkan judul buku Collector memiliki hubungan dengan fls hal ini ditunjukkan dengan nilai matrix sebesar 0.41732.

Sampai di sini, kita telah berhasil mengidentifikasi representasi fitur penting dari setiap **combined_features** dengan fungsi tfidfvectorizer. Kita juga telah menghasilkan matriks yang menunjukkan korelasi antara combined_features dengan judul buku. 

Selanjutnya, kita akan menghitung derajat kesamaan antara satu judul_buku dengan judul_buku lainnya untuk menghasilkan kandidat buku yang akan direkomendasikan. penghitungan sama dengan langkah yang sudah kita lakukan pada content based filtering dengan satu variabel kunci.

Mari kita lihat matriks kesamaan setiap jdul buku dengan menampilkan **nama judul buku dalam 5 sampel kolom (axis = 1) dan 10 sampel baris (axis=0)**.

![kesamaan ke 2](https://github.com/user-attachments/assets/e068c137-7f8d-49b0-ba6f-74228f512964)

Setelah kita melihat kesamaan antar judul buku, maka dapat kita buat parameter Sistem Recomendasinya.

Membuat fungsi buku_recommendations dengan beberapa parameter sebagai berikut:

* Judul_buku : Nama Judul Buku (index kemiripan dataframe).
* Similarity_data : Dataframe mengenai similarity yang telah kita definisikan sebelumnya.
* Items : Nama dan fitur yang digunakan untuk mendefinisikan kemiripan, dalam hal ini adalah ‘judul_buku’ dan ‘topik_buku’.
* k : Banyak rekomendasi yang ingin diberikan.
  
> **nilai k=10** yang akan diberikan untuk menampilkan rekomendasi.

![Rekomendasi 10 k](https://github.com/user-attachments/assets/bc46663f-e0e4-4a82-806b-3057540f5143)

Pada pencarian rekomendasi buku kita akan menggunakan judul buku yang sama yaitu "Von der Erde zum Mond". 

Berikut hasil dari sistem rekomendasi dengan teknik content based filtering dengan banyak variabel kunci:

![Rekomendasi 10](https://github.com/user-attachments/assets/8f1b7cb2-6534-4348-940d-f22304fdce8b)

**Selamat** Kita sudah berhasil membuat sistem rekomendasi dengan banyak variabel kunci.

## **Evaluasi Hasil Rekomendasi**

Dari Hasil dapat bahwa judul buku yang memilki kemiripan yang sama pada judul Von der Erde zum Mond adalah Reise um den Mond, Durch die Wüste, Dune (Classics Hardcover), El Ratón Perdido, Das Wunder von Narnia / Der König von Narnia, Damaris (Band 2): Der Ring des Fürsten, Durch Magie erwacht (Die Magie-Reihe 1), Autumn & Leaf, Der silberne Schlüssel, Der Herr der Ringe, 10 rekomendasi masuk ke dalam Jules Verne Diogenes Verlag AG FBC. Mari kita evaluasi hasil tersebut dengan **Matrix Precision** untuk sistem rekomendasi dengan teknik content based filtering:

Jumlah rekomendasi = 10 Jumlah

* Hasil rekomendasi sama dengan Penulis buku = 1
* Hasil rekomendasi sama dengan penerbit buku = 5
* Hasil rekomendasi sama dengan topik buku = 2

Precision = #of recomendation that are relevant / #of item we recommend

Precision = 8/10

Precision = 0.8 (80%)

> Hasil sudah cukup baik dan kita memiliki rekomendasi-rekomendasi yang lebih bervariasi dari penulis, penerbit dan juga topik buku.

> **NOTE:**
> 
> * Dengan menggunakan satu variabel kunci sistem hanya mengacu pada satu variabel dan ini cukup baik jika kita ingin merekomendasikan sesuai dengan minat customer yang menyukai buku berdasarkan topik, namun jika customer memiliki minat yang lebih kompleks atau tidak hanya topiknya saja maka pendekatan ini akan sedikit kurang efektif.
> * content based filtering dengan banyak variabel kunci akan menberikan rekomendasi yang sangat beragam dan dapat menutupi kekurangan dari content based filteing dengan satu variabel kunci, namun sistem tidak dapat memberikan secara spesifik terhadap minat customer.

## Mendapatkan Rekomendasi dengan Collaborative Filtering 

Pada tahap Data Preparation kita sudah membuat dataset transaction yang memilki nilai score, data ini yang akan dijadikan data kunci untuk melakukan teknik Collaborative Filtering untuk mendapatkan rekomendasi dari cutomer yang belum pernah memesan pada toko buku.

Sebelumnya kita telah menerapkan teknik content based filtering pada data. Teknik ini merekomendasikan item yang mirip dengan preferensi pengguna di masa lalu. Pada tahap ini, kita akan menerapkan teknik collaborative filtering untuk membuat sistem rekomendasi.

Dalam kasus ini, Data tidak memiliki variabel rating sebagai variabel kunci dari rekomendasi, namun kita bisa menganggap variabel klik, basket, dan order sebagai bentuk interaksi antara pengguna dan item (buku), dan menghitung skor implicit feedback untuk mewakili "ketertarikan" pengguna terhadap buku.

> Implicit feedback adalah data yang dikumpulkan secara tidak langsung dari tindakan pengguna, seperti riwayat pembelian, klik, atau tampilan halaman, yang menunjukkan preferensi mereka tanpa meminta peringkat atau ulasan eksplisit. Data ini digunakan dalam sistem rekomendasi untuk memahami preferensi pengguna dan memberikan rekomendasi yang relevan.
>
> Ada beberapa cara untuk membangun sistem rekomendasi berbasis implicit feedback: Pendekatan 1: Skoring Berdasarkan Interaksi Anda bisa membuat skor ketertarikan untuk setiap interaksi, misalnya:
> * Klik: 1 poin
> * Basket: 2 poin
> * Order: 3 poin
> 
> Skor ini akan menggambarkan tingkat ketertarikan pengguna pada suatu item. Misalnya, jika pengguna mengklik buku, skor ketertarikannya 1, jika memasukkan ke keranjang jadi 2, dan jika melakukan order, skornya 3.

Langkah awal kita akan melihat statistik data:

![Statistik](https://github.com/user-attachments/assets/f2b19308-d888-49a0-97d5-2957a6ae7f7c)

Dari hasil diatas dapat dilihat pada kolom score memiliki jumlah score terkecil 1 dan yang terbesar 3655.

Selanjutnya kita dapat melihat 10 score terbaik yang diperoleh dari interaksi data.

![score tertinggi](https://github.com/user-attachments/assets/0efacf04-84fb-484e-997d-895980686a9c)

* Langkah selanjutnya kita akan Mengubah sessionID menjadi list tanpa nilai yang sama, Melakukan encoding userID, dan Melakukan proses encoding angka ke ke userID.

* Langkah berikutnya kita lakukan langkah yang sama pada variabel itemID yaitu menjadikan list, Melakukan encoding.

* Langkah selanjutnya Mapping sessionID ke dataframe session dan Mapping itemID ke dataframe buku.

* Membagi Data untuk Training dan Validasi

Pada tahap ini kita akan melakukan pembagian data menjadi data training dan validasi. Kita bagi data train dan validasi dengan komposisi 80:20. Namun sebelumnya, kita perlu memetakan (mapping) data session dan buku menjadi satu value terlebih dahulu. dan score sebagai value y.

Sebelum melakukan rekomendasi terlebih dahulu membuat training data untuk melihat seberapa baik data yang sudah kita buat.

* Proses Training

Pada tahap ini, model menghitung skor kecocokan antara session, buku dan score dengan teknik embedding. Pertama, kita melakukan proses embedding terhadap data session dan buku. Selanjutnya, lakukan operasi perkalian dot product antara embedding sesion dan buku. Selain itu, kita juga dapat menambahkan bias untuk setiap session dan buku. Skor kecocokan ditetapkan dengan fungsi aktivasi sigmoid.

Di sini, kita membuat class RecommenderNet dengan keras Model class. Kode class RecommenderNet ini terinspirasi dari tutorial dalam situs Keras dengan beberapa adaptasi sesuai kasus yang sedang kita selesaikan.

* Model ini menggunakan Binary Crossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer, dan root mean squared error (RMSE) sebagai metrics evaluation.

## **Evaluasi data dengan RMSE**

> **Root Mean Square Error (RMSE):**
> 
> Digunakan pada collaborative filtering berbasis rating atau score untuk mengukur perbedaan antara rating/score yang diprediksi dengan rating/score aktual yang diberikan oleh pengguna.
> 
> RMSE memberi bobot lebih besar pada kesalahan yang lebih besar, menjadikannya sensitif terhadap prediksi yang salah secara signifikan.
> 
> ![image](https://github.com/user-attachments/assets/77274921-22d0-46ae-a6f4-bbf19d2c5553)

* **Visualisasi Metrik**

Untuk melihat visualisasi proses training, mari kita plot metrik evaluasi dengan matplotlib. 

![evaluasi](https://github.com/user-attachments/assets/8a7d65b0-5a95-4ef2-9bee-6f736ffe175f)

Hasil Evaluasi pada data training cukup baik yaitu:
* **root_mean_squared_error: 0.0076**, walaupun pada data test perbedaan yang cukup jauh.
* **val_root_mean_squared_error: 0.4431.** Akan tetapi ini masih dalam kategori baik untuk sebuah hasil dalam melakukan rekomendasi.

## Mendapatkan Rekomendasi dengan collaborative filtering

Selanjutnya kita akan membuat sebuah rekomendasi berdasarkan nilai score dari interaksi yang diberikan oleh customer atau pengguna yang telah mengunjungi toko buku, dari data tersebut sistem akan memberikan rekomendasi pada pengunjung baru.

* Variabel buku_not_visited diperoleh dengan menggunakan operator bitwise (~) pada variabel resto_visited_by_user.
* Selanjutnya, untuk memperoleh rekomendasi buku, gunakan fungsi model.predict() dari library Keras.
* Dalam proyek ini kita menggunakan top 10 score tertinggi sebagai rekomendasi buku.
* Menampilkan Buku dengan nilai tertinggi pada setiap session.

Berikut parameter dan hasilnya:

![image](https://github.com/user-attachments/assets/27c77022-e66e-4cd3-bba8-7cd7741448c5)

![collaborative](https://github.com/user-attachments/assets/1b08f542-067f-40c2-9845-41833a60c52a)

**Selamat** Kita sudah dapat membuat sistem rekomendasi dengan teknik collaborative Filtering dengan melakukan top 10 buku yang memiliki nilai terbaik, dan buku dengan high score terbaik.

>
> Dari 10 rekomendasi yang diberikan hanya satu yang memiliki kemiripan dan nilai score tertinggi pada interaksi customer dengan **session: 3083** yaitu "Der rote Planet".
> Buku dengan score teringgi masih memiliki kemiripan terhadap hasil 10 rekomendasi dari salah satu topik buku.
> Dari hasil diatas terdapat kekurangan dalam menampilkan buku dengan score terbaik karena nilai score memiliki nilai yang sangat beragam atau bervariasi.

## **Kesimpulan**

Dalam proyek ini, sistem rekomendasi buku berbasis content-based filtering dan collaborative filtering berhasil memenuhi sebagian besar tujuan dan harapan dari problem statements. Model ini efektif dalam menggantikan pendekatan manual yang kurang efisien dan mampu mengatasi keterbatasan rekomendasi yang bergantung pada interaksi langsung. Namun, hasil menunjukkan bahwa masing-masing metode memiliki beberapa kelebihan dan kekurangan. berikut beberapa kesimpulan pada menjawab masalah pada proyek ini:

* Rekomendasi yang Efisien dan Otomatis: Sistem berhasil menggantikan metode manual dengan pendekatan berbasis data yang otomatis dan efisien, sehingga dapat mengatasi peningkatan jumlah katalog dan pengguna.
* Rekomendasi yang Relevan dan Menarik Minat Pelanggan: Model content-based filtering telah menunjukkan kemampuannya dalam mengidentifikasi buku dengan kesamaan topik, penulis, dan penerbit, meskipun hasil evaluasi dengan precision masih beragam (40%-80%). Hal ini berarti model cukup efektif dalam memberikan rekomendasi yang relevan dengan preferensi pelanggan, meskipun ada ruang untuk peningkatan.
* Adaptasi untuk Toko Buku Daring: Solusi ini membantu toko buku kecil beradaptasi dengan perubahan menuju platform daring, sehingga tidak lagi bergantung pada interaksi fisik untuk memberikan rekomendasi.
* Efisiensi dalam Mengganti Pendekatan Manual: Model ini berhasil menggantikan pendekatan manual dengan pendekatan berbasis data yang lebih praktis, sesuai dengan tujuan proyek.
* Relevansi Rekomendasi untuk Meningkatkan Konversi Penjualan: Dari segi relevansi, hasil rekomendasi yang sesuai dengan preferensi pelanggan diharapkan dapat membantu meningkatkan konversi penjualan, meskipun perlu dioptimalkan agar lebih akurat.
* Membantu Adaptasi ke Layanan Daring: Sistem rekomendasi ini sangat membantu toko buku untuk tetap berfungsi secara efektif dalam lingkungan daring, sesuai dengan tujuan adaptasi menuju layanan digital.
* Content-Based Filtering: Dengan menggunakan content-based filtering, sistem mampu merekomendasikan buku berdasarkan karakteristik buku yang serupa, seperti penulis dan topik. Precision dari content-based filtering menunjukkan hasil yang baik (80%) ketika merekomendasikan buku dengan topik dan penerbit yang serupa. Hal ini mendukung solusi untuk menciptakan pengalaman yang personal bagi pelanggan.
* Collaborative Filtering: Collaborative filtering cukup baik dalam merekomendasikan buku yang disukai oleh pelanggan dengan preferensi serupa. Meskipun hasil dari root mean squared error (RMSE) menunjukkan performa yang baik pada data training (0.0076), perbedaan pada data validasi (0.4431) menunjukkan bahwa model ini masih bisa ditingkatkan dalam memprediksi preferensi dengan lebih konsisten pada data baru.

**Dampak Solusi Terhadap Project**

Secara keseluruhan, solusi yang diimplementasikan memiliki dampak positif terhadap tujuan proyek:
* Pendekatan otomatis dengan content-based dan collaborative filtering efektif dalam menyarankan buku berdasarkan preferensi individu maupun interaksi historis pelanggan lain.
* Kedua metode ini bersama-sama memberikan rekomendasi yang lebih personal dan relevan, walaupun perlu dioptimalkan lebih lanjut untuk meningkatkan akurasi dan relevansi.

Model berhasil mencapai tujuan utama proyek dan membantu toko buku dalam memberikan rekomendasi buku secara efisien, menarik minat pelanggan, dan mendukung penjualan daring.

## Penutup

Proyek sistem rekomendasi buku ini telah berhasil mengembangkan dan menerapkan model rekomendasi yang efisien dan relevan dengan menggunakan content-based filtering dan collaborative filtering. Kedua pendekatan tersebut dirancang untuk memenuhi kebutuhan pelanggan dalam lingkungan daring, di mana pendekatan manual tidak lagi efisien dan relevan. Dengan memanfaatkan data preferensi dan perilaku pelanggan, sistem ini dapat merekomendasikan buku secara personal, membantu toko buku meningkatkan keterlibatan pelanggan dan potensi penjualan tanpa memerlukan interaksi langsung.

Hasil evaluasi menunjukkan bahwa sistem rekomendasi ini telah mencapai sebagian besar dari tujuan yang direncanakan dan memberikan dampak positif terhadap efisiensi serta relevansi rekomendasi. Meski demikian, ada peluang lebih lanjut untuk meningkatkan akurasi rekomendasi dengan penyempurnaan model dan teknik evaluasi yang lebih optimal.

Sebagai langkah berikutnya, pengembangan sistem ini dapat difokuskan pada eksplorasi metode-metode pembelajaran mesin yang lebih canggih, seperti hybrid recommender systems, untuk lebih menyelaraskan hasil rekomendasi dengan preferensi unik setiap pengguna. Dengan demikian, proyek ini dapat terus beradaptasi terhadap kebutuhan pelanggan yang dinamis serta tren dalam dunia digital. Harapannya, sistem ini dapat menjadi salah satu pilar penting dalam mendukung daya saing toko buku di era digital yang serba cepat.






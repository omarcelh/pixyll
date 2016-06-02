---
layout:     post
title:      Algoritma Dasar dalam Kompresi JPEG
date:       2016-05-27
summary:    Silakan klik pada judul untuk detailnya
categories: tugas
---

**Oleh: Albertus Kelvin / 13514100**

### Daftar isi

> * [Bagaimana solusinya?](#bagaimana_solusi)
> * &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;>[Apa itu kompresi file?](#apa_itu_kompresi)
> * &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;>[Apa itu kompresi JPEG?](#apa_itu_jpeg)
> * [Algoritma JPEG](#algoritma_jpeg)
> * &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;>[_Discrete Cosine Transform (DCT)_](#dct)
> * &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;>[Kuantisasi](#kuantisasi)
> * &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;>[_Entropi Encoding_](#entropi_encoding)
> * [Kesimpulan](#kesimpulan)
> * [Referensi](#referensi)

Pernahkah Anda mengalami kesulitan saat ingin mengirim file? 

Kesulitan seperti apakah itu? 

Umumnya, bentuk masalah yang sering dihadapi adalah ukuran file yang melebihi batas ukuran yang diperbolehkan oleh suatu sistem. Salah satu contoh kasusnya adalah saat Anda ingin mengirim sebuah file gambar untuk dijadikan pengganti foto profil dari suatu media sosial, namun proses tersebut tidak berhasil dikarenakan sistem hanya mengijinkan file gambar dengan suatu ukuran maksimal tertentu. 

### <a name="bagaimana_solusi"></a> **Lalu, bagaimana solusinya?**

Salah satu teknik paling umum adalah dengan melakukan kompresi file. Untuk bahasan kali ini, saya hanya akan membahas kompresi pada ruang lingkup file multimedia, khususnya file gambar berekstensi JPEG.

#### <a name="apa_itu_kompresi"></a> **_Apa itu kompresi file?_**

> **Wikipedia:**

> * Menurut _Wikipedia_, kompresi file/ data adalah sebuah cara untuk memadatkan data sehingga hanya memerlukan ruangan penyimpanan lebih kecil sehingga lebih efisien dalam menyimpannya atau mempersingkat waktu pertukaran data tersebut. 

Berdasarkan definisi yang diberikan tersebut, kita dapat menyatakan bahwa data yang dikompresi akan memiliki ukuran file yang lebih kecil daripada sebelum dikompresi. Namun, jika ukuran data tersebut menjadi lebih kecil, bagaimana pengaruhnya terhadap konsistensi informasi yang terkandung di dalamnya? 

Menjawab persoalan tersebut, terdapat 2 jenis kompresi (pemampatan) data, yaitu pemampatan tanpa kehilangan (_lossless data compression_) dan pemampatan berkehilangan (_lossy data compression_). Berikut definisi singkat mengenai kedua jenis pemampatan tersebut:

> **_Lossless data compression:_**

> * Teknik pemampatan dimana data yang dimampatkan dapat dikembalikan sama persis seperti semula tanpa ada informasi yang hilang atau harus dikurangi. 

> **_Lossy data compression:_**

> * Teknik pemampatan dimana kasus kehilangan data yang kecil masih dapat diterima. Teknik ini juga dapat menggunakan algoritma tertentu untuk memangkasdetil data yang kurang penting agar ukurannya dapat dikecilkan.

#### <a name="apa_itu_jpeg"></a> **_Apa itu kompresi JPEG?_**

JPEG yang merupakan kependekan dari **_Joint Photographic Experts Group_** adalah sebuah algoritma kompresi untuk file gambar yang berjenis _lossy data compression_. 

Berdasarkan jenis teknik kompresi yang diaplikasikan, algoritma kompresi JPEG ini menggunakan metode menampilkan detil data dalam file gambar dengan sifat yang 'cukup mewakili' gambar tersebut. Maksudnya adalah data yang disimpan sebagai hasil pemampatan file gambar merupakan data yang cukup dapat menampilkan file gambar itu sebagai sesuatu yang mirip dengan file gambar aslinya. Hal ini dilakukan agar memori yang digunakan sekecil dan seefisien mungkin, dimana file gambar hasil pemampatan cukup dapat merepresentasikan file aslinya. Kasus representasi file asli ini berhasil jika kualitas file tidak dikurangi secara signifikan, dimana akan ada kemungkinan file kompresi memiliki beberapa perbedaan dengan file asli.

> **Keuntungan algoritma JPEG:**

> * Algoritma ini memanfaatkan fakta bahwa manusia tidak dapat melihat warna pada frekuensi tinggi.
> * Semua ruang lingkup warna dengan frekuensi tinggi tersebut akan dijadikan detil data yang dihilangkan selama proses pemampatan (tidak menjadi masalah dikarenakan adanya fakta pada poin pertama).

### <a name="algoritma_jpeg"></a> **Algoritma JPEG**

Berikut merupakan prosedur umum dalam algoritma JPEG:

> **Prosedur algoritma JPEG:**

> * Mengambil sebuah file gambar dan membaginya kedalam beberapa kotak kecil berukuran 8 x 8 pixels. 
> * Untuk setiap kotak kecil tersebut akan diambil data yang terkandung di dalamnya untuk merepresentasikan jenis warna pada setiap kotak kecil.
> * Mengambil _Discrete Cosine Transform_ (DCT) untuk setiap kotak kecil berukuran 8 x 8 pixels tersebut.
> * Setelah mengambil nilai DCT untuk sebuah kotak, lakukan prosedur perkalian matriks DCT terhadap sebuah nilai yang dapat membuat beberapa nilai tertentu dalam matrix DCT menjadi nol.
> * Untuk mengambil data dari file gambar hasil kompresi, dapat dilakukan dengan mengambil matriks inverse dari matriks DCT setiap kotak kecil. Semua matriks inverse yang telah didapat akan digabungkan kembali ke dalam sebuah file gambar yang berukuran sama seperti file aslinya.

Contoh pembagian gambar menjadi beberapa blok berukuran 8x8 pixels:

<p>
<div align="center">
<img src="https://github.com/albertusk95/irk_assets/blob/master/img/eightblocks.png?raw=true" alt="EightByEightBlocks" title="http://www.ams.org/featurecolumn/images/september2007/desertwall.grid.gif" />
</div>
</p>

Berikut beberapa metode yang digunakan di dalam algoritma JPEG:


####<a name="dct"></a> **_Discrete Cosine Transform (DCT)_**

DCT merupakan sebuah metode untuk memisahkan file gambar menjadi bagian-bagian frekuensi yang berbeda dimana frekuensi kurang penting akan dibuang melalui kuantisasi dan frekuensi penting digunakan untuk mengambil gambar selama dekompresi. 

> **Beberapa keuntungan yang dimiliki metode DCT:**
> * DCT sudah dapat diimplementasikan dalam sirkuit terpadu, 
> * DCT memiliki kemampuan untuk mengelompokkan semua informasi dalam koefisien yang paling sedikit, 
> * DCT dapat meminimalkan penampilan blok seperti yang disebut memblokir artefak yang terjadi ketika batas antara sub-gambar menjadi terlihat.

Transformasi DCT dalam bentuk dua dimensi direpresentasikan dalam persamaan sebagai berikut:

<p>
<div align="center">
<img src="https://github.com/albertusk95/irk_assets/blob/master/img/dct00.png?raw=true" alt="DCTTransformation" title="https://2.bp.blogspot.com/-Bs9k5tm08Qg/UgZVMxKcmfI/AAAAAAAAATg/vG1qQ31LqOM/s400/New+Picture.png" />
</div>
</p>

_Dimana u,v=0,1,2,3,……………,N-1_

 Inverse 2D-DCT tranformasi diberikan persamaan sebagai berikut :

<p>
<div align="center">
<img src="https://github.com/albertusk95/irk_assets/blob/master/img/invdct00.png?raw=true" alt="DCTInverse" title="https://3.bp.blogspot.com/-qCvNsQ5DjV0/UgZVdjqrqBI/AAAAAAAAATo/jDPxoxy8E7g/s400/New+Picture+(1).png" />
</div>
</p>

_Dimana :_
_D(u)=(1/N) ^1/2 untuk u=0_
_D(u)=2(/N)^1/2 untuk u=1,2,3…….,(N-1)_

#### <a name="kuantisasi"></a> **_Kuantisasi_**

Kuantisasi merupakan metode untuk melakukan prosedur perkalian matriks DCT terhadap sebuah nilai yang dapat membuat beberapa nilai tertentu dalam matriks DCT menjadi nol.

Kuantisasi dicapai dengan memadatkan rentang nilai ke nilai kuantum tunggal. Ketika jumlah simbol diskrit dalam urutan tertentu berkurang, urutan menjadi lebih padat. Sebuah matriks kuantisasi digunakan dalam kombinasi dengan sebuah DCT koefisien matriks untuk melaksanakan transformasi. 

Metode utama yang diimplementasikan dalam kuantisasi adalah semua langkah tertentu di mana sebagian besar kompresi dapat mengambil tempat. Kuantisasi memanfaatkan fakta bahwa komponen frekuensi yang lebih tinggi kurang penting daripada komponen frekuensi rendah (_seperti fakta yang sudah dijelaskan sebelumnya_) . 

Oleh karena itu, dapat ditentukan suatu _range_ yang menunjukkan tingkat kualitas gambar, misalnya dari 1 sampai 100. Dalam asumsi batasan ini, dapat ditentukan suatu batasan lagi dimana nilai 1 memberikan kualitas gambar terendah dan kompresi tertinggi, sementara nilai 100 memberikan kualitas terbaik dan kompresi terendah. 

Untuk mendapatkan matriks kuantisasi dengan tingkat kualitas yang lain, perkalian skalar matriks kuantisasi standar digunakan. Kuantisasi dicapai dengan membagi matriks citra ditransformasi oleh matriks kuantisasi yang digunakan. Nilai dari matriks yang dihasilkan kemudian dibulatkan. Dalam matriks, koefisien resultan terletak di dekat sudut kiri atas memiliki frekuensi yang lebih rendah, dimana mata manusia lebih sensitif terhadap frekuensi yang lebih rendah. Untuk frekuensi yang lebih tinggi akan dieliminasi. Hasil akhirnya adalah menggunakan nilai frekuensi yang lebih rendah untuk merekonstruksi gambar.

#### <a name="entropi_encoding"></a> **_Entropi Encoding_**

Setelah melakukan prosedur kuantisasi, sebagian besar koefisien frekuensi tinggi bernilai nol. Untuk mengeksploitasi jumlah angka nol, dapat dilakukan prosedur analisa secara _zig-zag_ (_zig-zag scan_) dari matriks yang digunakan untuk menghasilkan string panjang nol. Setelah kotak kecil berukuran 8x8 pixels tersebut diubah menjadi spektrum dan dikuantisasi, algoritma JPEG akan mengambil hasil dan mengubahnya menjadi array satu dimensi linier atau vektor dari 64 nilai untuk kemudian melakukan _zig-zag scan_ dengan memilih unsur-unsur dalam urutan numerik yang diindikasikan oleh angka dalam grid di bawah ini:

<p>
<div align="center">
<img src="https://github.com/albertusk95/irk_assets/blob/master/img/entrocode.png?raw=true" alt="EntropyEncoding" title="https://1.bp.blogspot.com/-tEObrJvOJB8/UgZVtEcuTqI/AAAAAAAAATw/Vv60SKIeNxI/s400/New+Picture+(2).png" />
</div>
</p>

Prosedur _zig-zag scan_ yang diimplementasikan dapat berbentuk seperti di bawah ini:

<p>
<div align="center">
<img src="https://github.com/albertusk95/irk_assets/blob/master/img/zigzag.png?raw=true" alt="ScanZigZag" title="http://www.ams.org/featurecolumn/images/september2007/zigzag.gif" />
</div>
</p>

Akhir dari algoritma JPEG ini adalah menempatkan unsur-unsur kotak kecil koefisien dalam urutan yang wajar dari frekuensi yang terurut membesar. Karena frekuensi yang lebih tinggi lebih cenderung bernilai nol setelah proses kuantisasi, kelompok frekuensi tinggi ini lebih cenderung masuk ke dalam kelompok frekuensi dengan nilai nol pada hasil akhir dari vektor.

### <a name="kesimpulan"></a> **Kesimpulan**

> Algoritma JPEG menggunakan nilai ukuran 8x8 pixels sebagai ukuran standar sebuah kotak kecil (blok). Namun, ukuran blok yang lain dapat saja memberikan hasil yang lebih baik untuk beberapa gambar tertentu. Hal ini menunjukkan pemilihan ukuran blok menentukan kualitas gambar hasil kompresi.

> Selain itu, berdasarkan prosedur utama dalam algoritma JPEG yang mengimplementasikan teknik matriks DCT, kuantisasi, dan _Entropy Encoding_ dapat dilihat bahwa dengan membuat beberapa variasi nilai yang dijadikan sebagai pengali matriks, dapat mengubah kualitas dan ukuran file gambar.

### <a name="referensi"></a> **Referensi**

> (1) Zhang, Zhihua and Naoki Saito.  High-dimensional data compression via PHLCT. 
> https://www.math.ucdavis.edu/~saito/publications/saito_phlcthd.pdf

> (2) Austin,  David.   Image  Compression:  Seeing  What's  Not  There. 
> http://www.ams.org/samplings/feature-column/fcarc-image-compression

> (3) http://www.whydomath.org/node/wavlets/basicjpg.html

> (4) http://www.prepressure.com/library/compression-algorithm/jpeg

---
layout:     post
title:      Enkripsi pada BASE64 dan BASE32
date:       2016-06-02
summary:    Silakan klik pada judul untuk penjelasan tugas
categories: tugas
---

By:  Johan 13514026

# Kriptografi

Setiap manusia pasti memiliki *privacy*nya masing-masing. Ada informasi yang tidak boleh diketahui oleh orang lain. Di lain hal, seiring berkembangnya teknologi, informasi dapat diketahui dengan mudah dan cepat melalui internet. Untuk menjaga kerahasiaan, data-data informasi yang ada di internet biasanya disembunyikan menggunakan sistem kriptografi yaitu dengan menyandikan isi informasi (plaintext) tersebut menjadi isi yang tidak dipahami melalui proses enkripsi (enchiper). Dan untuk memperoleh kembali informasi yang asli, dilakukan proses dekripsi (decipher). Kriptografi berasal dari bahasa Yunani “cryptos” artinya secret dan “graphein” yang artinya writing (tulisan). Sehingga kriptografi berarti tulisan rahasia. Jadi kriptografi dapat didefinisikan sebagai perpaduan antara ilmu dan seni.

Biasanya enkripsi dan dekripsi ini banyak dipakai dalam pengiriman pesan. Enkripsi dilakukan pada saat pengiriman dengan cara mengubah data asli menjadi data rahasia, sedangkan dekripsi dilakukan pada saat penerimaan dengan cara mengubah data rahasia menjadi data asli. Jadi data yang dikirimkan selama proses pengiriman adalah data rahasia, sehingga data asli tidak dapat diketahui oleh pihak yang tidak berkepentingan. Beberapa caranya adalah dengan algoritma [Base64] (#base64) dan [Base32] (#base32) yang akan dibahas di bawah. Base64 dan Base32 sebenarnya bukan enkripsi, namun hanyalah sebuah standar dari encoding.

###<a name="base64"></a> BASE 64
Istilah Base64 berasal dari konten pengkodean MIME tertentu.
> **Cara kerja BASE 64**
> *	Kelompokkan pesan setiap 3 karakter (3byte = 24 bit). Bila terdapat sisa di akhir, tambahkan (padding) bit 0 sehingga panjangnya genap 24 bit.
> * Pecah 24 bit tadi menjadi 4 kelompok yang masing-masing beranggotakan 6 bit.
> * Setiap kelompok sekarang punya 2^6 kemungkinan susunan bit, berarti ada 2^6 = 64 karakter yang tersedia untuk merepresentasikan 6 bit ini. Petakan setiap kelompok dengan karakter yang terdapat dalam tabel base64.

Base64 disusun oleh 64 karakter yang dimana karakternya berdasarkan RFC 1421 yang terdiri dari (A-Z, a-z, 0-9, +, /) Sehingga totalnya 64. Ditambah satu karakter khusus untuk padding byte yaitu “=”. Bila dalam kelompok 3-byte itu, satu byte terakhir hanya berisi padding bit, maka satu karakter “=” ditambahkan. Bila dua, maka dua karaker “=” (menjadi “==”)

<div align="center">
<img src="https://github.com/Johansentosa/IRK-img/blob/master/tabel%20base64.PNG">
<br>
tabel indeks BASE 64
</div> 
<br><br>

contoh penggunaan base64 dalam melakukan encoding karakter
> _Plaintext_ = "ilmu rekayasa komputasi"

> Hasil yang didapatkan = "aWxtdSByZWtheWFzYSBrb21wdXRhc2k="

<img src = "https://github.com/Johansentosa/IRK-img/blob/master/Capture.PNG">

Pada contoh diatas dibagi per 3 karakter menjadi ilm, u r, eka, ….dst. Kata “ilm” diganti menjadi “aWxt”. Pada tabel ASCII, huruf i, l, m disimpan sebagai 105, 108, dan 109, atau dengan kata lain 01101001, 01101100, 01101101 pada binary atau bilangan berbasis 2. Apabila ketiga byte tersebut digabungkan, maka akan dihasilkan 24 bit buffer yaitu 011010010110110001101101. Angka tersebut dikonversi sehingga berbasis 64, dengan membagi 24bit tersebut menjadi masing-masing 6bit. Maka dihasilkan 4 bagian. Kemudian masing-masing bagian tersebut dikonversi ke nilai yang ada di Base64.
Jika pada terakhir terdapat sekelompok karakter yang dimiliki tidak bernilai 3Byte (24 bit) maka akan dilakukan padding. Pading dilakukan dengan menambahkan karakter ‘=’

<p>
<div align="center">
<img src="https://github.com/Johansentosa/IRK-img/blob/master/paddingB64.PNG">
</div>
</p>


###<a name="base32"></a> BASE 32
Base 32 pada dasarnya sama seperti base 64. Hanya saja pada base 32 menggunakan susunan 32 karakter yang terdiri dari (A-Z, 2-7) ditambah 1 karakter khusus untuk padding byte yaitu “=”. Ini merupakan standar yang sudah didefinisikan dari RFC 4648. 0 dan 1 dilewati karena adanya kemiripan dengan huruf O dan l.

> **Cara kerja BASE 32**
> *	Kelompokkan pesan setiap 5 karakter (5byte = 40 bit). Bila terdapat sisa di akhir, tambahkan (padding) bit 0 sehingga panjangnya genap 40 bit.
> * Pecah 40 bit tadi menjadi 8 kelompok yang masing-masing beranggotakan 5 bit.
> * Setiap kelompok sekarang punya 2^5 kemungkinan susunan bit, berarti ada 2^5 = 32 karakter yang tersedia untuk merepresentasikan 5 bit ini. Petakan setiap kelompok dengan karakter yang terdapat dalam tabel base32.

> <img src="https://github.com/Johansentosa/IRK-img/blob/master/contohB32.PNG">

<p>
<div align="center">
<img src="https://github.com/Johansentosa/IRK-img/blob/master/tabel%20base32.PNG">
<br>
tabel indeks BASE32
</div></p>
<br>
Untuk penggunaan padding juga sama seperti pada BASE 64. Contohnya bisa dilihat di bawah ini
<p>
<div align="center">
<img src="https://github.com/Johansentosa/IRK-img/blob/master/paddingB32.PNG">
</div></p>

### BASE 64 vs BASE 32
Base64 dan Base32 memiliki kelebihan dan kelemahannya masing-masing. Base64 memiliki jumlah karakter yang dapat dipakai yang lebih banyak. Sehingga kemungkinan bisa dikatakan akan lebih aman jika diencode menggunakan Base64. Selain itu representasi Base32 akan memakan 20% lebih banyak memory dibandingkan dengan Base64. Hal ini karena Base32 mengkodekan 5 bytes menjadi 8 karakter, Base64 mengkodekan 3 bytes menjadi 4 karakter.

|          |  Base64 | Base32 |
|:--------:|:-------:|:------:|
| 8-bit    |   133%  | 160%   |
| 7-bit    | 117%    | 140%   |
Panjang notasi Base64 dan Base32 sebagai persentase dari data biner

Tetapi di lain hal, Base32 lebih menguntungkan. Karakter yang dihasilkan Base32 semuanya satu kasus, yang seringkali bermanfaat saat menggunakan file sistem yang bersifat *case-insensitive*, bahasa lisan, atau memori manusia. Hasil dari Base32 tidak mengandung karakter '/' sehingga bisa digunakan dalam penamaan sebuah file dan dapat dimasukkan dalam sebuah link tanpa pengkodean karakter apapun.
<br><br>

#### Referensi
* [*The Base16, Base32, and Base64 Data Encodings* from RFC 4648.](https://tools.ietf.org/html/rfc4648)
* [*The Base16, Base32, and Base64 Data Encodings* from RFC 3548.](https://tools.ietf.org/html/rfc3548)
* [*Multipurpose Internet Mail Extensions: (MIME) Part One: Format of Internet Message Bodies*](https://tools.ietf.org/html/rfc2045)

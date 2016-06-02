---
layout:     post
title:      Penyalahgunaan Kriptografi
date:       2016-05-30
summary:    Silakan klik pada judul untuk detailnya
categories: tugas
---

# Penyalahgunaan Kriptografi: Kriptovirologi dan Penanganannya
Kriptografi merupakan suatu ilmu yang digunakan untuk menjaga kerahasiaan suatu informasi. Kriptografi biasanya digunakan untuk mengenskripsi suatu informasi sehingga tidak mudah diketahui oleh pihak yang tidak diinginkan. Contoh dari penggunaan kriptografi adalah pengiriman pesan rahasia pada badan intelijen dan militer. Dilihat dari kegunaannya, bisa dikatakan bahwa kriptografi dibuat dengan tujuan untuk melindungi. Namun, kriptografi bisa disalahgunakan untuk hal sebaliknya. Kriptografi justru bisa disalahgunakan untuk menghilangkan akses seseorang terhadap informasi, menghilangkan kerahasiaan informasi, dan menyebabkan kebocoran informasi, hal-hal yang biasanya justru dicegah dengan kriptografi. Hal-hal tersebut bisa terjadi jika ilmu kriptografi digabungkan dengan virus komputer yang menghasilkan ilmu baru bernama kriptovirologi.

## Daftar Isi
1. [Kriptovirologi](#kriptovirologi)
  1. [Metode Kriptografi yang Biasa Digunakan pada Kriptovirologi](#metode-kriptografi-yang-biasa-digunakan-pada-kriptovirologi)
    1. [Kriptografi simetris](#kriptografi-simetris)
    2. [Kriptografi dengan public-key](#kriptografi-dengan-public-key)
  2. [Virus Komputer](#virus-komputer)
  3. [Serangan Kriptovirologi](#serangan-kriptovirologi)
    1. [Virus One-Half](#virus-one-half)
    2. [Virus LZR](#virus-lzr)
    3. [AIDS Information Trojan](#aids-information-trojan)
    4. [Virus KOH](#virus-koh)
  4. [Penanganan](#penanganan)
2. [Referensi](#referensi)

## Kriptovirologi
Kriptovirologi adalah ilmu yang mempelajari penerapan kriptografi pada perangkat lunak yang dibuat untuk tujuan tidak baik. Yang dimaksud dengan tidak baik di sini adalah perangkat lunak yang dibuat untuk tujuan membuat suatu data tidak bisa diakses atau mengubah data yang disimpan. Ilmu kriptovirologi memang membantu orang-orang yang bermaksud buruk, namun kita juga perlu mempelajarinya untuk menangani masalah yang ditimbulkan oleh kriptovirologi. Kita tidak bisa menangani masalah yang ditimbulkan kriptovirologi jika kita tidak mengerti mengenai hal tersebut.

### Metode Kriptografi yang Biasa Digunakan pada Kriptovirologi
Ada dua metode kriptografi yang biasa digunakan pada kriptovirologi yaitu kriptografi simetris dan kriptografi dengan peblic-key.
#### Kriptografi simetris
Pada kriptografi simetris, enkripsi plainteks dan dekripsi cipherteks menggunakan kunci yang sama. Plainteks adalah data atau informasi yang dapat dibaca dan dimengerti maknanya. Cipherteks adalah pesan yang telah disandikan sehingga tidak memiliki makna lagi. Enkripsi adalah proses menyandikan plainteks menjadi cipherteks, sementara dekripsi adalah proses mengembalikan cipherteks menjadi plainteks. <br><br>

Berikut adalah ilustrasi kriptografi simetris :

<img src="http://www2.powayusd.com/pusdtbes/cs/symmetric.gif">

Pada pengiriman informasi antar dua pihak, ada suatu kunci yang digunakan bersama. Kunci tersebut digunakan untuk menjaga kerahasiaan informasi. Hal ini menyebabkan kedua pihak harus memiliki akses terhadap kunci rahasia tersebut. Contoh dari algoritma kriptografi simetris adalah Twofish, Serpent, AES, dan IDEA. 

#### Kriptografi dengan public-key
Kriptografi simetris memiliki kelemahan karena kunci enkripsi dan dekripsi yang sama. Hal ini menyebabkan kunci mudah diketahui oleh pihak lain sehingga mengurangi kerahasiaan informasi. Kelemahan ini diatasi pada kriptografi dengan public-key. Pada kriptogafi dengan public-key, digunakan dua kunci, yaitu public-key dan private-key. Public-key merupakan kunci yang digunakan untuk melakukan enkripsi, sementara private-key merupakan kunci yang digunakan untuk melakukan dekripsi. Jadi, semua orang bisa melakuka enkriipsi menggunakan public-key penerima, namun pesan tersebut hanya bisa didekripsi dengan private-key milik penerima. Public-key bisa diketahui oleh semua orang, sementara private-key hanya diketahui oleh penerima. Sementara pada kriptografi simetris, kunci harus diketahui oleh pengirim dan penerima. <br><br>

Berikut adalah ilustrasi kriptografi dengan public-key :

<img src="http://www.ooshutup.com/wp-content/uploads/2014/11/public_key_encryption.jpg"><br>
Contoh dari algoritma kriptografi dengan public-key adalah RSA.

### Virus Komputer
Ada 3 jenis virus komputer yang sering menyebabkan gangguan, yaitu virus biasa, trojan, dan worms. **Virus biasa** adalah kode yang bisa menggandakan dirinya dan menginfeksi komputer tanpa sepengetahuan penggunanya. **Trojan** adalah program yang merupakan bagian dari program lain yang mengeksekusi perintah tanpa sepengetahuan pemilik program. **Worms** adalah komputer program yang bisa memperbanyak diri sendiri dan menggunakan suatu jaringan untuk mengirimkan salinan dirinya ke tempat lain. Untuk selanjutnya, virus mengacu pada ketiga hal ini. Virus yang mengandung dan menggunakan public-key adalah **kriptovirus**.

### Serangan Kriptovirologi
Serangan kriptovirologi dilakukan dengan menggunakan kriptovirus. Perancang virus membuat private-key dan public-key untuk virus. Private-key disimpan oleh perancang virus di suatu media, biasanya berbentuk *_smartcard_*. Public-key disimpan pada kriptovirus. Kriptovirus kemudian dilepaskan untuk menginfeksi mesin-mesin milik orang lain. Kriptovirus kemudian menggabungkan diri dengan data-data. Kriptovirus kemudian mengenkripsi data milik orang lain dengan menggunakan _symmetric key_. Kemudian, pemilik data akan mendapat notifikasi bahwa telah terjadi penyerangan dan data hanya bisa diakses dengan private-key. Untuk mendapat private-key tersebut, pemilik data harus membayar uang sebanyak yang diinginkan oleh perancang virus atau datanya tidak akan bisa diakses lagi. Jika pemilik data membayar, barulah perancang virus mengirimkan private-key untuk melakukan dekripsi. Kriptovirus biasanya merupakan _high survivable virus_, yaitu virus yang bisa bertahan pada inangnya karena membuat inangnya harus bergantung pada virus tersebut. Ada beberapa contoh kriptovirus dan serangannya yang dibahas selanjutnya.
#### Virus One-Half
Virus ini ditemukan pada Oktober 1994. Virus ini bekerja dengan melakukan enkripsi pada hard drive dimulai dari silinder terakhir dan perlahan maju ke silinder berikutnya. Virus One-Half menggunakan cipher simetris dan menyimpan kunci pada diriya sendiri.
#### Virus LZR
Virus LZR merupakan variasi dari komputer virus sektor boot yang bernama Stoned. LZR mengambil alih terhadap proses baca dan tulis hard disk dengan menggunakan _system call_ yang tidak diketahui. LZR menulis informasi _error correction_ pada disk, meskipun hal itu jarang dilakukan sistem operasi. Pada saat informasi ditulis ke disk, data diikuti oleh data _error correction_ dari virus. Jika virus dihapus, rutinitas penting tidak akan dipanggil, sehingga arsip-arsip yang ada akan dianggap tidak dapat dimengerti oleh  program user.
#### AIDS Information Trojan
Program ini menyediakan infomasi pada pengguna yang menimbulkan AIDS, dan pada saat yang bersamaan mengenkripsi hard drive pengguna setelah 90 reboot. Pengguna kemudian diberi notifikasi bahwa _license fee_ harus dibayar oleh pengguna untuk mendapatkan kunci dekripsi.
#### Virus KOH
Virus ini juga melakukan enkripsi terhadap sistem inang. Tujuan utama dari virus ini adalah untuk membuat enkripsi berjalan pada background, sehingga tidak ada intervensi dari pengguna. Virus ini menggunakan sistem kriptografi IDEA dan dijual secara komersial.

### Penanganan
Ada beberapa cara penanganan terhadap serangan kriptografi, yaitu :
* Melakukan pengawasan terhadap memori.<br> Hal ini berguna untuk menangkap kriptovirus yang _self encrypting_ dan _polymorphic_. _Polymorphic_ berarti virus bisa membuat salinan dirinya sendiri yang berbeda-beda untuk mengelabui pengguna.
* Menggunakan dua bentuk otentikasi. Kata sandi (_password_) saja merupakan otentikasi yang lemah. Dua bentuk otentikasi, dengan kata sandi dan entitas biometrik pengguna seperti sidik jari bisa digunakan.
* Menggunakan aplikasi anti-virus yang _up-to-date_. Anti-virus juga bisa digunakan untuk menangani kriptovirus dikarenakan kriptovirus menggunakan cara penyebaran yang sama dengan virus biasa.
* Menggunakan _tools_ kriptografi dan API kriptografi. Hal ini bisa membantu admin sistem untuk mengidentifikasi penggunaan kriptografi yang mencurigakan.
* Melakukan pengawasan terhadap proses-proses yang memanggil rutinitas kriptografi dan mencegah eksekusi proses yang tidak memiliki akses yang seharusnya untuk memanggil _library/toolkit_ kripto. Jika ada rutinitas kriptografi yang kuat dan generator angka acak, akan menyebabkan virus lebih mudah untuk membuat kode dan menjalankan kode tersebut. Menjalankan _tool_ kriptografi tertentu dapat meningkatkan keamanan sistem, namun membuat sistem mudah terinfeksi virus karena virus dapat memanggil rutinitas ini.
* Menggunakan firewall dan Intrusion Detection System (IDS) untuk melindungi sistem yang terhubung dengan sistem lain maupun yang tidak.
* Melakukan back-up pada data secara teratur. Meskipun data kita terinfeksi kriptovirus dan tidak dapat dibuka, jika kita sudah memiliki back-up maka kita tidak perlu membayar perancang virus untuk mendapatkan data kita kembali.

## Referensi
* A. Young, M. Yung. 2004. _Malicious Cryptography: Exposing Cryptovirology_. New York: Wiley
* A. Young and Moti Yung, "Cryptovirology: extortion-based security threats and countermeasures," Security and Privacy, 1996. Proceedings., 1996 IEEE Symposium on, Oakland, CA, 1996, pp. 129-140
* Balepin, Ivan. 2003. "Superworms and Cryptovirology: a Deadly Combination". Department of Computer Science University of California, Davis
May 2003
* http://www.cryptovirology.com/, diakses pada 27 Mei 2016


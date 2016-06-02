---
layout:     post
title:      Monoalphabetic Substitution Cipher
date:       2016-05-30
summary:    Silakan klik pada judul untuk detail nya
categories: tugas
---

# Monoalphabetic Substitution Cipher

---

## Daftar Isi

1. [Definisi](#definisi)
2. [Algoritma Cipher yang digunakan](#algoritma-cipher-yang-digunakan)
  1. [Caesar Cipher](#caesar-cipher)
  2. [Atbash Cipher](#atbash-cipher)
  3. [Baconian Cipher](#baconian-cipher)
  4. [Polybius Square](#polybius-square)
  5. [Keyword Cipher](#keyword-cipher)
3. [Referensi](#referensi)

---

## Definisi

_Monoalphabetic Substitution Cipher_ adalah salah satu jenis penyandian yang umum pada kriptografi.
Setiap karakter pada teks di-enkripsi dengan algoritma tertentu dan perubahan ini dipakai 
secara konsisten pada kasus tersebut (selanjutnya akan disebut sebagai _Monoalphabetic Cipher_). Misalkan huruf A di-enkripsi dengan huruf D, maka dari awal
teks hingga akhir , huruf A akan selalu diganti dengan huruf D.

## Algoritma Cipher yang digunakan

Berikut ini adalah berbagai algoritma _cipher_ sederhana yang dipakai dan termasuk dalam 
_Monoalphabetic Cipher_ :

* Caesar Cipher
* Atbash Cipher
* Baconian Cipher
* Polybius Square
* Keyword Cipher

### Caesar Cipher

Mungkin kita sudah sering mendengar _cipher_ yang satu ini, karena _cipher_ yang satu ini sangat sederhana
dan mudah dipelajari dan diaplikasikan. Huruf pada sebuah _plain text_ akan digantikan dengan huruf lain sesuai jumlah 
pergeseran yang digunakan. Contoh : "Sample test" dengan jumlah pergeseran 3, akan di-enkripsi menjadi "Vdpsoh whvw".
_Caesar Cipher_ merupakan _cipher_ yang paling sederhana dan paling mudah dipecahkan, salah satunya dengan cara _frequency analysis", pada 
Bahasa Indonesia huruf a frekuensi nya paling banyak digunakan sehingga _cipher text_ dengan huruf terbanyak kemungkinan adalah huruf A.
Selain itu kita juga bisa melakukan _brute force_ dengan mencoba 25 kemungkinan pergeseran.
Dengan x adalah huruf yang ingin kita enkripsi (a = 0, b = 1, etc) dan k adalah jumlah pergeseran maka algoritma _Caesar Cipher_ 
dapat kita nyatakan dalam fungsi matematika sederhana berikut :

> _**e(x) = (x + k) mod 26**_

### Atbash Cipher

_Atbash Cipher_ merupakan jenis _cipher_ yang melakukan penyandian dengan melakukan pencerminan pada susunan alfabet. Misal huruf A akan diganti dengan Z,
huruf B diganti dengan Y dan seterusnya. Dengan x adalah huruf yang ingin kita enkripsi (a = 0, b = 1, etc) maka algoritma _Atbash Cipher_ dapat kita
nyatakan dalam fungsi matematika berikut :

> _**e(x) = 25 - x**_

_Atbash Cipher_ juga mudah sekali dipecahkan dan membutuhkan usaha yang lebih sedikit dibandingkan _Caesar Cipher_.

### Baconian Cipher

Nama _Baconian Cipher_ diambil dari nama penemunya yaitu Sir Francis Bacon. Pada _Baconian Cipher_, setiap alfabet digantikan dengan 5 karakter berurutan.
Pada algoritma aslinya, 5 karakter ini terdiri dari A dan B. Berikut ini adalah contoh tabel Baconian dan contoh bagaimana cara kerja _cipher_ ini :
Tabel Baconian Cipher :

> ![BaconianTable](https://github.com/varian97/assets/blob/master/images/baconian_table.PNG)

dan berikut ini merupakan contoh penyandian kata "STRIKE NOW" dengan algoritma _Baconian Cipher_ :

> ![BaconianExample](https://github.com/varian97/assets/blob/master/images/baconian_example.PNG)

Untuk memecahkan _Baconian Cipher_ dibutuhkan usaha lebih dibandingkan 2 Cipher sebelumnya, namun dengan _Cryptanalysis_ biasa _cipher_ ini dapat dipecahkan.

### Polybius Square

_Polybius Square_ adalah sebuah algoritma penyandian dengan menggunakan matriks untuk men-enkripsi sebuah alfabet menjadi 2 _cipher text_ bisa berupa angka maupun
alfabet lain. Dalam pembahasan ini, penulis akan menggunakan penyandian dengan angka.
Perhatikan matriks contoh berikut :

> ![polybiustable](https://github.com/varian97/assets/blob/master/images/Polybius_table.PNG)

Sebagai contoh, huruf D akan dienkripsi menjadi 14 dsb. Sehingga penggunaannya :

> Plain text  = Asisten IRK

> Cipher text = 11432443441533 244225

### Keyword Cipher

_Keyword Cipher_ mempunyai prinsip yang hampir sama seperti _Caesar Cipher_ hanya saja pada _Keyword Cipher_ alfabet pengganti dapat berupa _key_.
Berikut adalah langkah pembuatan/penyandian dengan _Keyword Cipher_ :

1. Tuliskan semua alfabet
2. Dibawahnya, tuliskan _key_ dan diikuti dengan alfabet yang belum muncul pada _key_ tersebut
3. Lakukan penyandian dengan mengganti alfabet dengan alfabet yang berada dibawahnya.

Lebih lengkapnya mari kita perhatikan contoh berikut :

> Key = keyword

> abcdefghijklmnopqrstuvwxyz

> keywordabcfghijlmnpqstuvxz

Dengan demikian, huruf a akan digantikan dengan k, b dengan e, dst.

## Referensi

* http://www.braingle.com/brainteasers/codes/index.php
* http://practicalcryptography.com/cryptanalysis/text-characterisation/identifying-unknown-ciphers/
* https://guides.github.com/features/mastering-markdown/

___
# Perbandingan Kompresi Lossy dan Lossless pada Berkas Suara #
___


## Berkas Suara
Rekaman suara terbagi menjadi dua tipe, yaitu analog dan digital. Suara analog direkam dengan cara mereplikasi bentuk gelombang suara sesuai dengan aslinya. Suara digital direkam dengan mengambil sampel dari gelombang suara asli pada nilai tertentu. 

Sebuah berkas suara adalah suatu berkas yang menyimpan data suara secara digital. Suara pada dunia nyata bersifat kontinu. Akan tetapi, pada rekaman suara digital tidak memiliki sifat kontinu namun berubah - ubah pada interval tertentu. 

Aproksimasi dari suara yang nyata ini awalnya dibuat pada tahun 1937 dengan Pulse-Code Modulation (PCM). Karakter dari PCm ini adalah adanya *sample rate* dan *bit depth*. *Sample rate* menyatakan seberapa sering amplitudo dari gelombang suara direkam. *Bit depth* menyatakan nilai digital yang mungkin. PCM merupakan dasar dari audio digital yang ada saat ini.

<img src="http://www.centerpointaudio.com/Images/Analog-Digital%20frequency%20examples.png">

Gambar 1. Perbandingan Gelombang Suara

## Berkas Suara tak Terkompresi
Seperti telah dijelaskan pada bagian sebelumnya, PCM memodelkan suara semirip mungkin dengan kenyataannya. Hasilnya, pemodelan menggunakan PCM membuat berkas yang Lossless dan tidak terkompresi. Hal ini membuat berkas yang dihasilkan akan memakan banyak ruang penyimpanan.

Saat ini, berkas suara yang tidak terkompresi umumnya termasuk dalam salah satu dari dua jenis berkas yaitu WAV atau AIFF. WAV merupakan berkas suara berdasarkan PCM yang sering kita temui dalam sistem operasi Windows, sedangkan AIFF dapat kita temui dalam sistem operasi OS X. Kedua jenis berkas ini merupakan berkas suara yang lengkap dan akan memakan banyak ruang penyimpanan. Berkas jenis ini umumnya digunakan ketika melakukan perekaman suara, mengedit suara dan menyimpan berkas suara dengan *sample rate* dan *bit rate* yang beragam. Jenis berkas ini juga digunakan pada CD Digital Audio.

## Kompresi Berkas Suara
Menyimpan berkas suara dengan jenis berkas yang tidak terkompresi tentu tidak efektif jika kita memiliki ruang penyimpanan yang terbatas. Oleh karena itu, seiring berjalannya waktu, muncul berbagai cara untuk mengurangi ukuran dari berkas suara sehingga dapat disimpan secara lebih efisien. Proses pengurangan itu dilakukan dengan melakukan kompresi. Kompresi dari berkas tersebut dapat menghasilkan berkas yang Lossy maupun berkas yang Lossless.

Proses kompresi suatu berkas suara melibatkan *library* yang disebut dengan audio codecs. Audio codecs merupakan program komputer yang berperan dalam proses kompresi maupun dekompresi dari suatu berkas suara. Setiap audio codecs akan membuat berkas suara dengan jenis berkas, kualitas, dan spesifikasi yang berbeda - beda. Umumnya, berbagai jenis codec yang umum digunakan telah menjadi bagian dari *installer* sistem operasi yang kita gunakan. Codec juga dapat kita *install* secara manual dengan cara mengunduh *installer* yang disediakan oleh pembuatnya. Codec yang umum digunakan untuk berkas suara diantaranya MPEG, WMA, AAC, FLAC.

## Berkas Suara Lossless
Berkas suara Lossless menyimpan seluruh kualitas dari berkas suara yang asli sehingga membentuk berkas suara sebagus berkas yang asli namun dengan ukuran yang lebih kecil. Saat ini, terdapat beberapa berkas suara Lossless yang umum dikenal:

- FLAC
- ALAS
- APE

FLAC merupakan singkatan dari Free Lossless Audio Codec. FLAC merupakan jenis berkas suara Lossless yang paling populer saat ini. FLAC memberikan kualitas suara yang sama dengan berkas suara aslinya dan memakan ruang penyimpanan yang lebih sedikit. FLAC juga merupakan codec yang gratis dan *open source*. Namun, rasio kompresi dari FLAC tidak terlalu besar.

ALAS, singkatan dari Apple Lossless Audio Codec merupakan codec Lossless yang digunakan dan dikeluarkan oleh Apple. Codec ini melakukan kompresi Lossless sama seperti FLAC namun lebih difokuskan untuk pengguna gawai keluaran Apple.

APE merupakan sebuah algoritma kompresi berkas suara yang bernama *Monkey's Audio*. Codec ini juga melakukan kompresi Lossless meskipun tidak sepopuler ALAS ataupun FLAC. Selain itu, kebanyakan pemutar berkas suara yang digunakan saat ini juga kurang kompatibel dengan berkas suara APE.

## Berkas Suara Lossy
Berkas suara Lossy menyimpan berkas suara dengan ukuran yang lebih kecil dari berkas suara Lossless, namun dengan mengorbankan bagian - bagian tertentu dari berkas suara sehingga mengurangi kualitas. Kualitas yang dihilangkan di sini adalah bagian - bagian dari berkas suara yang biasanya kurang terdengar bagi pendengaran manusia pada umumnya. Lagu yang sering kita dengan melalui gawai - gawai kita saat ini biasanya menggunakan berkas suara yang Lossy demi efisiensi ruang penyimpanan. Terdapat banyak jenis berkas suara Lossy, diantaranya:

- MP3
- AAC
- WMA
- OGG
- dll

MP3 atau MPEG Audio Layer III adalah jenis berkas yang paling sering kita temui saat ini. Meskipun jenis berkas ini bukanlah yang paling efisien, namun berkas MP3 merupakan paling berkas yang paling banyak didukung oleh berbagai gawai dan sistem. 

AAC (Advanced Audio Coding) merupakan berkas yang mirip dengan MP3 namun lebih efisien. AAC saat ini juga populer digunakan untuk audio digital dengan kualitas tinggi. Gawai - gawai keluaran Apple menggunakan jenis berkas AAC sebagai standar berkas suaranya.

WMA (Windows Media Audio) merupakan jenis berkas suara keluaran Microsoft. Jenis berkas ini tidak memiliki kelebihan khusus jika dibandingkan dengan MP3 ataupun AAC. Selain itu, berkas ini juga tidak terlalu kompatibel kebanyakan pemutar musik.

OGG merupakan jenis berkas suara dalam format Vorbis. OGG Vorbis merupakan sebuah audio codec bebas paten dan *open source* yang mirip dengan MP3 ataupun AAC. Jenis berkas ini juga kurang populer dan tidak terlalu kompatibel dengan kebanyakan pemutar musik.

## Konversi Antara Berkas Lossy dan Lossless
Dalam konversi antar berkas suara ada hal yang perlu diingat. Konversi dari berkas Lossless ke berkas Lossy akan menghasilkan berkas dengan kualitas yang sedikit menurun namun diikuti dengan turunnya ukuran berkas. Akan tetapi, jika kita melakukan konversi dari berkas Lossy ke berkas Lossless, kita tidak akan menghasilkan berkas dengan kualitas yang lebih baik sehingga justru hanya akan menaikkan ukuran berkas secara sia - sia. Hal ini disebabkan berkas hasil konversi tidak akan lebih baik dari berkas aslinya.

## Perbandingan Berkas Suara Lossy dan Lossless

Pada berkas suara dengan kualitas rendah, kita akan kesulitan dalam menemukan perbedaan antara berkas Lossy dan Lossless. Namun, untuk berkas dengan kualitas tinggi, suara yang didapat pada berkas Lossless akan terdengar lebih baik. Namun, kompresi berkas Lossy dengan *bit rate* yang tinggi mampu menghasilkan kualitas hampir sama dengan berkas Lossless. Umumnya, penyimpanan secara Lossy dengan *bit rate* yang tinggi sudah cukup untuk pengguna yang menginginkan berkas suara dengan kualitas yang bagus. Namun, jika kita ingin menyimpan berkas dengan tujuan untuk diubah - ubah, kompresi secara Lossless lebih dianjurkan.

Perbedaan lain yang cukup mencolok antara berkas Lossy dan Lossless adalah ukuran dari kedua jenis berkas tersebut. Meskipun ukuran dari berkas - berkas tersebut bergantung pada karakteristiknya (*bit rate*, *sampling rate*, *bit depth*, panjang berkas suara), namun ukuran berkas Lossless jauh lebih besar dibandingkan berkas Lossy. Berkas MP3 yang Lossy umumnya memiliki ukuran 3 MB hingga 15 MB untuk sebuah lagu, sedangkan berkas FLAC yang Lossless umumnya memiliki ukuran 25 MB hingga 40 MB untuk sebuah lagu.

Selain itu, berkas suara yang Lossy saat ini lebih umum digunakan pada berbagai gawai dalam kehidupan sehari - hari . Hampir seluruh gawai yang digunakan saat ini dapat memutar berkas MP3. Berkas suara Lossless seperti FLAC kurang umum jika dibandingkan dengan berkas Lossy. Hasilnya, tidak semua gawai yang umum digunakan dapat memutar berkas suara Lossless. Terkadang diperlukan pemutar suara tertentu agar gawai kita dapat memutar berkas suara yang Lossless. 

### Referensi
1. http://www.nch.com.au/acm/formats.html
2. http://www.howtogeek.com/142174/what-lossless-file-formats-are-why-you-shouldnt-convert-lossy-to-lossless/
3. http://www.howtogeek.com/howto/40465/htg-explains-what-are-the-differences-between-all-those-audio-formats/
4. http://www.file-extensions.org/filetype/extension/name/audio-and-sound-files
5. http://lifehacker.com/5927052/whats-the-difference-between-all-these-audio-formats-and-which-one-should-i-use
6. http://www.audioquest.com/audio_file_formats/
7. http://www.webopedia.com/DidYouKnow/Computer_Science/digital_audio_formats.asp
8. http://www.centerpointaudio.com/Analog-VS-Digital.aspx

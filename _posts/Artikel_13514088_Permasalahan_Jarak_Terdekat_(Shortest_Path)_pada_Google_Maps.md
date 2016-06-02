# Permasalahan Jarak Terdekat (Shortest Path) pada Google Maps


## Latar Belakang Masalah
Google Maps atau biasa disingkat *Maps* adalah sesuatu yang sangat tidak asing lagi bagi manusia. Maps merupakan aplikasi yang digunakan oleh milyaran orang di dunia ini untuk mencari jalan ke suatu tempat tertentu. Akibatnya, aplikasi ini sudah dapat dianggap tidak dapat dipisahkan dari kehidupan manusia. Dari perspektif pengguna, mereka berharap dapat menemukan jalan menuju suatu tempat, tanpa tersesat, dan dalam waktu yang singkat. Intinya mereka dapat mendapatkan jalur yang diharapkan dengan cepat. Akan tetapi, tidak semudah itu kelihatannya bagi sang developer. Bagi sang developer, permasalahan penemuan jalan terdekat merupakan suatu masalah besar sendiri, karena dibutuhkan algoritma yang optimal dan sangat cepat untuk mendapatkan jalur dan alternatif jalurnya secara cepat dan tepat (tanpa melalui jalan yang sebenarnya tidak ada).

Berikut ini akan dijelaskan pemakaian dan efektifitas algoritma-algoritma yang dapat digunakan terhadap aplikasi Google Maps.
## Algoritma yang Digunakan
Ada beberapa tahap dalam pencarian jalan terdekat ini. Tahap pertama yaitu menentukan *node-node* pada *Maps*, lalu mendapatkan jarak terdekatnya.

### Pencarian Node
Algoritma yang digunakan untuk mendapatkan *node-node* pada *Maps* adalah dengan menggunakan geometri. Saat bertemu dengan persimpangan, maka dapat kita dapat menganggap itu sebagai *vertex* "besar" yang dapat digunakan untuk calon jalan yang akan dilalui. Ada juga node yang merupakan tempat spesifik pada suatu jalan, kita anggap itu sebagai *vertex* "kecil" karena itu hanya digunakan sebagai tujuan awal atau tujuan akhir.

Semua *vertex* besar akan ditambahkan secara permanen ke daftar *node* yang mungkin dilalui.
Kedua *vertex* kecil tersebut akan ditambah secara sementara saja pada saat pencarian sebagai titik awal dan titik akhir.

### Pencarian Shortest Path
Ada beberapa algoritma *shortest path* yang digunakan secara luas dan umum, dan dapat digunakan pada aplikasi Google Maps. Dimulai dari Algoritma brute force, kita akan melihat dan menganalisis performansi dari algoritma tersebut.

#### Brute Force
Menggunakan Algoritma *Brute Force*, maka akan mencari ke semua arah (dengan asumsi tidak ada jalan yang sama bakal dilalui dua kali) dan semua kemungkinan jalan yang mungkin dari awal sampai akhir, dengan menganggap suatu jalan sebagai bit "0 berarti tidak dipakai, 1 berarti dipakai", dan mencari minimumnya. Hal ini tentunya sangat tidak efisien, melihat kompleksitasnya yang menjadi __O(2<sup>n</sup>)__, dimana n untuk satu kota saja, jumlahnya bisa mencapai puluhan - ratusan ribu, apalagi jika antar kota. Tentunya kompleksitas yang eksponensial dan n yang besar sudah tidak memungkinkan pencarian jalur menggunakan algoritma ini.

#### DFS
Menggunakan Algoritma DFS, kita akan mencari jalur dengan menelusuri setiap jalur yang ada. Jika diketemukan, maka keluarkan hasilnya. Hal ini dapat berakibat hasil yang tidak optimal karena DFS hanya berhasil apabila dipakai pada *unweighted graph* atau graf tidak berarah, sedangkan kita tahu bahwa jalan-jalan sebenarnya memiliki panjang yang berbeda-beda. Selain tidak optimal, algoritma ini juga lambat karena bisa saja menelusuri ke arah yang sebaliknya dengan arah tujuan (arah tujuan ke kanan, tetapi arah DFS malah ke kiri terus, mengakibatkan tidak ketemu-ketemu). Sebagai perhitungan, anggap banyaknya ekspansi adalah b, dan kedalamannya adalah d, maka kompleksitas algoritma tersebut bisa mencapai __O(b^d)__ dimana dapat dilihat naik secara eksponensial dengan bertambahnya kedalaman.
 
#### BFS
Dengan Menggunakan algoritma BFS, maka semua node akan terekspan. Hasilnya merupakan jalur yang ketemu untuk pertama kalinya. Akan tetapi, ternyata algoritma ini juga tidak optimal dalam mencari jarak terdekat, karena grafnya berbobot. Akan tetapi, kompleksitasnya jauh lebih kecil, hanya __O(n)__ saja dimana n adalah jumlah node atau persimpangan yang terdapat pada graf tersebut. Hal ini memiliki kompleksitas waktu yang cukup kecil dibandingkan dengan Brute Force dan DFS, akan tetapi masih termasuk sangat besar. Akan tetapi, karena algoritma ini juga tidak optimal, maka algoritma ini tidak digunakan dalam aplikasi *shortest path* pada Maps apapun.

#### Dijkstra's Algorithm
Algoritma ini merupakan algoritma shortest path yang digunakan pertama kalinya yang dapat menemukan solusi untuk graf berarah (asumsi graf tidak ada *negative cycle*). Algoritma ini dijalankan dengan menggunakan STL *priority_queue* dan menggunakan heap tree sebagai implementasinya (agar bisa mendapatkan query dan mengupdate tree dalam waktu log(n) saja). __(tulis sumber Dijkstra disini)__. Algoritma ini dimulai dari node pertama, dan akan berhenti ketika node yang diproses adalah node tujuan. Kompleksitas dari algoritma ini adalah __O(E + V log V)__ dimana E adalah jumlah jalan dan V adalah jumlah persimpangan yang terdapat pada *Maps*. Algoritma ini sudah cukup mereduksi dari Brute Force dan sudah dapat mengeluarkan hasil yang optimal, akan tetapi untuk ukuran yang sangat besar, ini belum bisa mengeluarkan hasil dalam waktu yang cukup cepat untuk dapat digunakan pengguna secara nyaman. __(Node di Maps : > 1000000)__

#### Greedy Best First Search Algorithm
Algoritma ini merupakan algoritma yang memakai pendekatan *heuristik* dalam penyelesaiannya, parameter pemilihannya hanya estimasi jarak ke tujuan saja. Estimasi ini dihitung berdasarkan jarak garis lurus antara titik sekarang ke titik tujuan. Kompleksitas ini sama seperti Dijkstra's Algorithm, yaitu __O(E + V log V)__, akan tetapi tidak selalu menghasilkan jalur yang optimal, karena hanya mengandalkan jarak estimasi saja, dan algoritma ini tidak pernah dipakai di Maps yang sebenarnya.
 
#### A-Star Algorithm
Algoritma ini merupakan algoritma yang menggabungkan Algoritma Dijkstra dan Greedy Best First Search, dimana parameter pembandingnya adalah Jarak antara titik awal - sekarang ditambah dengan jarak estimasi antara titik sekarang - titik tujuan. Algoritma ini bertujuan untuk mempersempit ruas pencarian yang dihasilkan oleh algoritma Dijkstra. Pada algoritma Dijkstra, yang penting yang jarak terkecil dari titik awal terlebih dahulu yang diprioritaskan, sedangkan untuk A-Star, yang terpenting adalah jarak total estimasinya. Estimasinya harus merupakan suatu heuristik yang *admissible*, yang berarti jarak estimasinya tidak boleh melebihi jarak terdekatnya. Dalam kasus ini, estimasinya dihitung berdasarkan garis lurus antara dua titik.

Algoritma ini memiliki kompleksitas __O(E)__ atau banyaknya jalan yang ada pada kasus terburuk, dan sudah cukup optimal dan lebih cepat dibandingkan Dijsktra, dan sudah cukup nyaman digunakan oleh pengguna dalam jarak cukup dekat (<= 100 km)(tidak banyak node yang diekspan sehingga bisa jauh lebih cepat). 

Akan tetapi, algoritma ini bukanlah yang tercepat untuk dipakai pada Google Maps, karena apabila jarak lebih dari 100 km (jarak jauh) maka akan performansinya akan berkurang (masih tetap lambat, node yang diekspan bisa lebih besar dari 1 juta).

#### Precompute + A-Star
Pada algoritma-algoritma sebelumnya, selalu pencarian dan perhitungan seluruh graf dilakukan ketika ada query yang masuk. Sekarang kita pikirkan sebagai berikut: mungkinkah ada banyak orang yang mencari jalur yang relatif sama untuk beberapa bagiannya? Bisakah kita mengoptimasinya? Jawabannya adalah bisa. Jika pencarian dilakukan setiap kali orang melakukan query, maka jika ada jalur yang relatif sama, perhitungan tersebut akan menjadi mubazir. 

Karena itu biasanya hasil query-query tersebut dipecah-pecah menjadi beberapa bagian dan dimasukkan ke database Google Maps sendiri. Jadi jika ada bagian yang sama, tinggal langsung memanggil bagian tersebut dan tidak perlu menghitung ulang jarak dan jalur yang dipakai. Jika belum ada query yang pernah dicari pada bagian tersebut, maka akan menghitung menggunakan A-star search algorithm, dengan maksimum node yang diekspan adalah 100.000 untuk tetap tidak harus menghitung terlalu lama. 

Pendekatan ini sudah cukup optimal dan dapat digunakan pada Google Maps karena diharapkan dapat mencari jalur terdekat untuk jarak jauh, tanpa harus menghitung simpul-simpul yang tidak diperlukan, dan bisa diterapkan dalam waktu yang cepat. Algoritma ini memiliki kompleksitas maksimum __O(E)__ dengan E adalah jumlah jalan yang diekspan (jika diperlukan).

## Kesimpulan
Ada sangat banyak algoritma *shortest path* yang dapat digunakan untuk *Google Maps*. Akan tetapi, walaupun begitu, hanya sedikit yang dapat menghasilkan solusi optimal dalam waktu polynomial (dijkstra, A-star, dan Precompute). Walaupun begitu, tidak semuanya dapat menghasilkan jalur dalam waktu yang cepat, dan tidak ada yang dapat menyelesaikan persoalan tersebut dalam waktu yang singkat tanpa menggunakan prekomputasional dan optimisasi lainnya, karena *node* yang ada sangat banyak. Berikut ini merupakan peta kota Jakarta:

![Image of Jakarta](https://github.com/raditya1710/aradityaa/blob/master/JakartaEdited.png)

Dapat dilihat bahwa pada gambar itu saja (kota besar di Indonesia), terdapat sangat banyak persimpangan / node didalamnya. 

Tentunya untuk solusi yang saya berikan __(Precompute + A-Star)__, sudah cukup lumayan untuk dapat memenuhi kriteria dan kenyamanan pengguna, akan tetapi baru dalam skala kota saja, belum bisa antar kota. Untuk persoalan antar kota, terdapat algoritma campuran yang tidak dapat dibahas di sini (terlalu panjang dan memasukkan bagian sistem *low level*).

## Referensi

* https://groups.google.com/forum/#!topic/Google-Maps-API/QMHKn-oaB24
* https://guides.github.com/features/mastering-markdown/
* Sumber Pribadi
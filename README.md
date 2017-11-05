# PKSJ-Tugas-2

Laporan Tugas PKSJ - Uji Penetrasi SQLInjection

## Pendahuluan

Keamanan adalah faktor penting untuk mengembangkan sebuah sistem. Menjadi tantangan sendiri bagi para pengembang aplikasi pada internet, karena pada awal mula pengembangan internet tujuan utama hadirnya internet adalah untuk mengakomodasi kebutuhan komunikasi yang menghubungkan berbagai perangkat tanpa terkendala jarak dan waktu, sehingga faktor keamanan menjadi salah satu kriteria penting, namun sering terlupakan.

Ada banyak cara untuk menguji apakah sebuah sistem rentan terhadap serangan SQL Injection. SQL Injection menjadi tantangan tersendiri untuk diuji karena celah ini sering digunakan oleh para penyerang untuk menyerang database melalui bahasa _Structured Query Language_ yang ditanamkan melalui back-end.

## Dasar Teori

 [SQL Injection](#sql-injection).
 
### SQL Injection
 
 SQL Injection adalah suatu serangan yang terdiri dari penyisipan atau *injection* query melalui input data dari client ke aplikasi. SQL Injection yang berhasil dilakukan akan membaca data sensitif dari database, memodifikasi isi database (insert, select, update) dan mengeksekusi operasi administrasi database (seperti shutdown DBMS).
 Serangan SQL Injection adalah serangan yang bertipe injeksi, dimana perintah SQL di inject atau di input untuk mendapatkan hasil dari perintah SQL yang telah dibuat.


#### Model Ancaman
 
 * SQL Injection memungkinkan penyerang untuk mengambil identitas, merusak data, juga menyebabkan kegagalan transaksi atau mengubah isi saldo, serta memungkinkan untuk membuka seluruh data pada sistem, menghancurkan data atau membuat data tersebut tidak tersedia, dan juga menjadi administrator dari database server.
 * SQL Injection sangat umum terjadi pada server berbasiskan PHP dan ASP.
 * Kekuatan dari serangan SQL Injection terbatas pada kemampuan penyerangnya, dan untuk mengurangi serangannya, maka pertahanan terhadap SQL Injection perlu dilakukan, karena SQL Injection akan mengakibatkan dampak yang sangat besar jika berhasil diimplementasikan.

#### Testing SQL Injection

Biasanya, langkah untuk mencari celah sistem untuk diinjeksi menggunakan metode SQL Injection adalah memahami kapan aplikasi terhubung dengan database untuk mengakses beberapa data. Contoh dari hubungan antara aplikasi dengan database adalah:

* Form Autentikasi: Saat autentikasi dilakukan dengan menggunakan web form, kemungkinan pengecekan user akan dilakukan terhadap database yang berisi seluruh username dan password.

* Search Engine: String yang dimasukkan oleh user dapat digunakan sebagai query SQL yang mengekstrak seluruh isi database yang ada.

* Halaman Product List: Situs e-commerce dan beberapa sistem umum selalu memiliki product listing, dan halaman-halaman tersebut biasanya disimpan pada database relasional.

Tester biasanya membuat daftar dari seluruh input

### Wordpress

WordPress adalah sebuah aplikasi sumber terbuka (open source) yang sangat populer digunakan sebagai mesin blog (blog engine). WordPress dibangun dengan bahasa pemrograman PHP dan basis data (database) MySQL. PHP dan MySQL, keduanya merupakan perangkat lunak sumber terbuka (open source software). Selain sebagai blog, WordPress juga mulai digunakan sebagai sebuah CMS (Content Management System) karena kemampuannya untuk dimodifikasi dan disesuaikan dengan kebutuhan penggunanya. WordPress adalah penerus resmi dari b2/cafelog yang dikembangkan oleh Michel Valdrighi. Nama WordPress diusulkan oleh Christine Selleck, teman Matt Mullenweg. WordPress saat ini menjadi platform content management system (CMS) bagi beberapa situs web ternama seperti CNN, Reuters, The New York Times, TechCrunch, dan lainnya.

Rilis terbaru WordPress adalah versi 4.8.1 (2 Agustus 2017). WordPress didistribusikan dengan Lisensi Publik Umum GNU.

### WPScan

WPScan adalah scanner keamanan yang memeriksa keamanan WordPress menggunakan metode _black box_. WpScan ini ditulis dengan bahasa Ruby.

Fitur dari WpScan:

1. Pencacah Username
2. Multithreaded Bruteforce Password Cracking
3. Plugin WordPress version Checker
4. Wordpress Plugin Vulnerabilities Scanner
 
### SQLMap

Sqlmap adalah tools opensource yang mendeteksi dan melakukan exploit pada bug SQL injection secara otomatis. dengan melakukan serangan SQL injection seorang attacker dapat mengambil alih serta memanipulasi sebuah database di dalam sebuah server.

## Instalasi
[Instalasi Wordpress](https://github.com/rafiarr/PKSJ-Tugas-2/blob/master/instalasi_wordpress.md).

[Instalasi LeagueManager 3.9.1.1](https://github.com/rafiarr/PKSJ-Tugas-2/blob/master/instalasi_leaguemanager.md).

[Instalasi WPScan](https://github.com/rafiarr/PKSJ-Tugas-2/blob/master/instalasi_wpscan.md).

[Instalasi SQLMap](https://github.com/rafiarr/PKSJ-Tugas-2/blob/master/instalasi_sqlmap.md).

## Uji Penetrasi SQL Injection
 [Uji Penetrasi SQL Injection](lalal)

## Kesimpulan dan Saran

 [Defence dan Countermeasure](lalala).

 Sebagaimana telah dijelaskan bahwa SQL Injection umum dilakukan karena:
 
 1. Vulnerabilities SQL selalu umum dan banyak diketahui orang sehingga lebih mudah melakukan injeksi karena metode-metode atau celah yang sudah sering ada dan mudah diterobos.
 2. Interaksi dengan data selalu menarik dan mengakibatkan dampak yang sangat signifikan bagi sistem, sehingga beberapa orang merasa tertantang, dan beberapa penyerang lain memang berusaha memberikan dampak serius bagi sistem.
 
 Dibawah ini dituliskan macam-macam metode pencegahan yang dapat digunakan untuk menghindari serangan SQL Injection.
 
 Perlindungan Inti/Primer:
 
 - Menggunakan __Prepared Statement__ (atau __*Parameterized Query*__)
 - Menggunakan __Stored Procedure__
 - Memiliki _Whitelist Input_ yang dibolehkan
 - Melakukan _escaping_ untuk semua Input dari user
 
 Perlindungan Tambahan:
 
 - Prinsip __Least Privilege__
 - Tambahan _Whitelist Input Validation_
 - Menggunakan Tool
 
 Contoh kode yang tidak terlindungi oleh SQL Injection
 
 ```Java
  String query = "SELECT account_balance FROM user_data WHERE user_name = "
    + request.getParameter("customerName");
  
  try {
  	Statement statement = connection.createStatement( … );
  	ResultSet results = statement.executeQuery( query );
  }
 ```
 
##### Perlindungan Primer 1: Menggunakan Prepared Statement (dengan Parameterized Query)
 
 Penggunaan Prepared Statement dengan _variable binding_ memaksa developer untuk pertama-tama mendefinisikan kode SQL dan mengirimkan masing-masing parameter kedalam query tersebut. Penulisan kode seperti ini memberikan pemisah/pengenal antara kode dan data, terlepas dari input yang diberikan oleh user.
 
 Prepared Statement memastikan bahwa penyerang tidak dapat mengganti maksud dari query, meskipun sebuah perintah SQL dimasukkan kedalam query awal oleh penyerang.
 
##### Perlindungan Primer 2: Menggunakan Stored Procedure

Stored Procedure tidak selalu memastikan keamanan dari SQL Injection

##### Perlindungan Tambahan 3: Menggunakan Tool

Terdapat beberapa tool tambahan yang dapat digunakan walaupun tidak secara langsung membantu, seperti salah satunya _Intrusion Deetection System (IDS)_

Salah satu yang marak digunakan adalah _Snort_, selain itu terdapat _Suricata_, _Bro_, _Kismet_.

Intrusion Detection System adalah sejenis perangkat lunak yang berfungsi untuk mendeteksi intrusi sistem. Intrusi disini adalah menganalisa segala macam serangan yang terjadi dari luar sistem.

# PKSJ-Tugas-2

Laporan Tugas PKSJ - Uji Penetrasi SQLInjection

## Pendahuluan

Keamanan adalah faktor penting untuk mengembangkan sebuah sistem. Menjadi tantangan sendiri bagi para pengembang aplikasi pada internet, karena pada awal mula pengembangan internet tujuan utama hadirnya internet adalah untuk mengakomodasi kebutuhan komunikasi yang menghubungkan berbagai perangkat tanpa terkendala jarak dan waktu, sehingga faktor keamanan menjadi salah satu kriteria penting, namun sering terlupakan.

Ada banyak cara untuk menguji apakah sebuah sistem rentan terhadap serangan SQL Injection. SQL Injection menjadi tantangan tersendiri untuk diuji karena celah ini sering digunakan oleh para penyerang untuk menyerang database melalui bahasa _Structured Query Language_ yang ditanamkan melalui back-end.

## Dasar Teori

 [SQL Injection](#sql-injection).
 
###SQL Injection
 
 SQL Injection adalah suatu serangan yang terdiri dari penyisipan atau *injection* query melalui input data dari client ke aplikasi. SQL Injection yang berhasil dilakukan akan membaca data sensitif dari database, memodifikasi isi database (insert, select, update) dan mengeksekusi operasi administrasi database (seperti shutdown DBMS).
 Serangan SQL Injection adalah serangan yang bertipe injeksi, dimana perintah SQL di inject atau di input untuk mendapatkan hasil dari perintah SQL yang telah dibuat.

####Model Ancaman
 
 * SQL Injection memungkinkan penyerang untuk mengambil identitas, merusak data, juga menyebabkan kegagalan transaksi atau mengubah isi saldo, serta memungkinkan untuk membuka seluruh data pada sistem, menghancurkan data atau membuat data tersebut tidak tersedia, dan juga menjadi administrator dari database server.
 * SQL Injection sangat umum terjadi pada server berbasiskan PHP dan ASP.
 * Kekuatan dari serangan SQL Injection terbatas pada kemampuan penyerangnya, dan untuk mengurangi serangannya, maka pertahanan terhadap SQL Injection perlu dilakukan, karena SQL Injection akan mengakibatkan dampak yang sangat besar jika berhasil diimplementasikan.

####Testing SQL Injection

Biasanya, langkah untuk mencari celah sistem untuk diinjeksi menggunakan metode SQL Injection adalah memahami kapan aplikasi terhubung dengan database untuk mengakses beberapa data. Contoh dari hubungan antara aplikasi dengan database adalah:

* Form Autentikasi: Saat autentikasi dilakukan dengan menggunakan web form, kemungkinan pengecekan user akan dilakukan terhadap database yang berisi seluruh username dan password.

* Search Engine: String yang dimasukkan oleh user dapat digunakan sebagai query SQL yang mengekstrak seluruh isi database yang ada.



###Wordpress
 
###WPScan
 
###SQLMap

## Instalasi
 [Instalasi](lalal).

## Uji Penetrasi SQL Injection
 [Uji Penetrasi SQL Injection](lalal)

## Kesimpulan dan Saran

 [Defence dan Countermeasure](lalala).

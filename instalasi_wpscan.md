WPScan adalah tool yang berguna untuk membantu proses injeksi SQL. Aplikasi ini akan melakukan scan ke target dan memberikan *vulnerability* yang tersedia. Beberapa artikel yang membahas vulnerability tersebut di internet juga akan ditampilkan. Berikut adalah tutorial instalasi WPScan di linux.

Pertama, install semua dependency yang dibutuhkan oleh wpscan.
```bash
sudo apt-get update
sudo apt-get install apt-get libcurl4-openssl-dev libxml2 libxml2-dev libxslt1-dev ruby-dev build-essential libgmp-dev zlib1g-dev
```

WPScan bisa didownload dengan cara melakukan *clone* pada github di project WPScan. Jika komputer yang akan digunakan belum memiliki git, install git terlebih dahulu.
```bash
sudo apt-get update
sudo apt-get install git
```

Clone project WPScan dengan cara
```bash
git clone https://github.com/wpscanteam/wpscan.git
cd wpscan
sudo gem install bundler && bundle install --without test development
```

WPScan bisa dijalankan dengan menggunakan ruby
```bash
ruby wpscan.rb
```


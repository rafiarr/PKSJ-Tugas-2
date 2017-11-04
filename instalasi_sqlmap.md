SQLMap adalah alat untuk melakukan penetration testing dengan memanfaatkan teknik sql injection. Cara instalasinya seperti berikut.

Download SQLMap terbaru melalui terminal
```bash
wget 'https://github.com/sqlmapproject/sqlmap/tarball/master' --output-document=sqlmap.tar.gz
```

Ekstrak dengan perintah berikut ini
```bash
tar -xvf sqlmap.tar.gz
```

Di direktori tersebut akan ada folder dengan nama sqlmapproject-sqlmap-xxxxxxx. Masuk ke folder tersebut dan sqlmap siap untuk dijalankan dengan python.
```bash
cd sqlmapproject-sqlmap-xxxxxxx
python sqlmap.py -u http://www.site.com/alamat/website/yang/vulnerable --dbs
```



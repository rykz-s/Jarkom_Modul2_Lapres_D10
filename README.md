# Jarkom_Modul2_Lapres_D10

### 05111840000129 Ryukazu Andara Saviestyan
### 05111840000155 Muhamat Samsu Dhuha
### Kelompok D10

## Soal
```
Semeru adalah salah satu gunung yang terkenal di Jawa Timur. Bibah adalah salah satu juru kunci
Semeru. Bibah ingin menyebarkan keindahan Semeru pada dunia sehingga dia membeli 3 buah server
yang berada di MALANG, MOJOKERTO dan PROBOLINGGO. Server MALANG akan digunakan
sebagai DNS Server Master, MOJOKERTO akan digunakan sebagai DNS Server Slave dan
PROBOLINGGO akan digunakan sebagai Web Server. Selain 3 server terdapat 2 klien yang digunakan
untuk testing oleh Bibah yaitu GRESIK dan SIDOARJO. Untuk menyambungkan semua jaringan
tersebut Bibah memberi router di SURABAYA.
Kalian diminta untuk membuat sebuah website utama dengan
```
1. alamat http://semeruyyy.pw yang memiliki!
2. alias http://www.semeruyyy.pw, dan!
3. subdomain http://penanjakan.semeruyyy.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO serta dibuatkan!
4. reverse domain untuk domain utama. Untuk mengantisipasi server dicuri/rusak, Bibah minta dibuatkan!
5. DNS Server Slave pada MOJOKERTO agar Bibah tidak terganggu menikmati keindahan Semeru pada Website. Selain website utama Bibah juga meminta dibuatkan
6. subdomain dengan alamat http://gunung.semeruyyy.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO. Bibah juga ingin memberi petunjuk mendaki gunung semeru kepada anggota komunitas sehingga dia meminta dibuatkan.
7. subdomain dengan nama http://naik.gunung.semeruyyy.pw, domain ini diarahkan ke IP Server PROBOLINGGO.
Setelah selesai membuat keseluruhan domain, kamu diminta untuk segera mengatur web server.
8. Domain http://semeruyyy.pw memiliki DocumentRoot pada /var/www/semeruyyy.pw. Awalnya web dapat diakses menggunakan alamat http://semeruyyy.pw/index.php/home. Karena dirasa alamat urlnya kurang bagus, maka
9. diaktifkan mod rewrite agar urlnya menjadi http://semeruyyy.pw/home.
10.Web http://penanjakan.semeruyyy.pw akan digunakan untuk menyimpan assets file yang memiliki DocumentRoot pada /var/www/penanjakan.semeruyyy.pw dan memiliki struktur folder sebagai berikut:
```
/var/www/penanjakan.semeruyyy.pw
                                /public/javascripts
                                /public/css
                                /public/images
                                /errors
```
11. Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan.
12. Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache.
13. Untuk mengakses file assets javascript awalnya harus menggunakan url http://penanjakan.semeruyyy.pw/public/javascripts. Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http://penanjakan.semeruyyy.pw/js. Untuk web http://gunung.semeruyyy.pw belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai.
14. sedangkan web http://naik.gunung.semeruyyy.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot web berada pada /var/www/naik.gunung.semeruyyy.pw. Dikarenakan web http://naik.gunung.semeruyyy.pw bersifat private
15. Bibah meminta kamu membuat web http://naik.gunung.semeruyyy.pw agar diberi autentikasi password dengan username “semeru” dan password “kuynaikgunung” supaya aman dan tidak sembarang orang bisa mengaksesnya. Saat Bibah mengunjungi IP PROBOLINGGO, yang muncul bukan web utama http://semeruyyy.pw melainkan laman default Apache yang bertuliskan “It works!”.
16. Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http://semeruyyy.pw.
17. Karena pengunjung pada /var/www/penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.

## Jawab

#### Note
```
Untuk Nomer 1 - 7 Harap melakukan service bind9 restart sebelum melakukan pengetesan,
Untuk nomer 8 - 17 Harap melakukan service apache2 restart sebelum melakukan pengetesan.
Hal ini dilakukan per-nomer untuk mengaktifkan konfigurasi yang telah diupdate.
```

#### Persiapan

<br>

<center>
  
![img](/img/persiapan1.png)

</center>

<br>

1.
``` 
Pada uml malang lakukan konfigurasi seperti berikut pada file named.conf.local, lalu lakukan konfigurasi lagi pada file semerud10.pw yang berada pada direktori jarkom.
Untuk mengecek apakah berhasil dilakukan ping semerud10.pw pada uml gresik.
```
<center>
  
![img](/img/no1.png)

![img](/img/no1.2.png)

![img](/img/no1.3.png)

</center>

<br>

2. 
``` 
Pada uml malang lakukan konfigurasi seperti berikut pada file semerud10.pw yang berada di direktori jarkom.
Untuk mengecek apakah berhasil dilakukan ping www.semerud10.pw pada uml gresik.
```
<center>
  
![img](/img/no2.png)

![img](/img/no2.1.png)

</center>

<br>

3. 
```
Pada uml malang lakukan konfigurasi seperti berikut pada file semerud10.pw yang berada di direktori jarkom.
Untuk mengecek apakah berhasil dilakukan ping penanjakan.semerud10.pw pada uml gresik.
```
<center>
  
![img](/img/no3.png)
  
![img](/img/no3.1.png)

</center>

<br>

4. 
```
Pada uml malang lakukan konfigurasi pada file named.conf.local kemudian lakukan konfigurasi pada file yang telah dibuat yaitu pada file 79.151.10.in-addr.arpa seperti pada gambar.
Untuk mengecek apakah berhasil dilakukan dengan mengetik host -t PTR 10.151.79.92 pada uml gresik.
```
<center>
  
![img](/img/no4.png)

![img](/img/no4a.png)

![img](/img/no4b.png)
</center>

<br>

5. 
```
Pada uml malang lakukan konfigurasi pada file named.conf.local kemudian lakukan konfigurasi lagi pada uml mojokerto untuk file named.conf.local jangan lupa untuk mematikan service bind9 pada uml malang.
Untuk mengecek apakah berhasil dilakukan ping semerud10.pw pada uml gresik maka akan mengarah ke ip malang.
```
<center>
  
![img](/img/no5.png)

![img](/img/no5.1.png)
  
![img](/img/no5.2.png)

</center>

<br>

6. 
```
Pada uml malang lakukan konfigurasi untuk file semerud10.pw seperti pada gambar 6 lalu untuk file named.conf.options lakukan comment pada dnssec-validation auto; kemudian tambahkan sintaks seperti pada gambar 6.1, untuk named.conf.local pada uml malang juga dikonfigurasi seperti pada gambar 6.2.
Pada uml mojokerto juga dilakukan hal serupa yaitu melakukan konfigurasi pada file named.conf.local dan named.conf.options seperti pada gambar dibawah, kemudian pada file gunung.semerud10.pw dikonfigurasi seperti gambar dibawah.
Untuk mengecek apakah berhasil dilakukan ping gunung.semerud10.pw pada uml gresik.
```
<center>
  
![img](/img/no6.png)

![img](/img/no6.1.png)

![img](/img/no6.2.png)

![img](/img/no6.3.png)

![img](/img/no6.4.png)

![img](/img/no6.5.png)

![img](/img/no6.6.png)

</center>

<br>

7. 
```
Pada uml mojokerto, tambahkan konfigurasi seperti gambar dibawah untuk file gunung.semerud10.pw yang berada pada direktori delegasi.
Untuk mengecek apakah berhasil dilakukan ping naik.gunung.semerud10.pw pada uml gresik.
```
<center>
  
![img](/img/no7.1.png)

![img](/img/no7.png)

</center>

<br>

8.
```
Pada uml probolinggo, masuk ke direktori sites-available kemudian cp file default dan rename dengan nama semerud10.pw lalu lakukan konfigurasi seperti gambar dibawah.
Untuk mengecek apakah berhasil dilakukan dengan mengakses situs semerud10.pw
```
<center>
  
![img](/img/no8.png)

![img](/img/no8.1.png)

</center>

<br>

9.
```
Pada uml probolinggo, masuk ke directori /var/www/semerud10.pw kemudian buat file .htaccess lalu isikan sintaks seperti gambar 9, kemudian lakukan konfigurasi pada file semerud10.pw yang berada pada direktori sites-available seperti gambar 9.1.
Untuk mengecek apakah berhasil dilakukan dengan mengakses situs semerud10.pw/home
```
<center>
  
![img](/img/no9.png)

![img](/img/no9.1.png)

![img](/img/no9.2.png)

</center>

<br>

10.
```
Pada uml probolinggo, masuk ke direktori sites-available kemudian cp file default dan rename dengan nama penanjakan.semerud10.pw lalu lakukan konfigurasi seperti gambar dibawah.
```
<center>
  
![img](/img/no10.png)

![img](/img/no10.1.png)

</center>

<br>

11.
```
Pada uml probolinggo, lakukan konfigurasi pada file penanjakan.semerud10.pw seperti gambar dibawah. Untuk direktori yang dibolehkan listing maka ditambahkan Options +Indexes, sedangkan jika tidak diperbolehkan listing maka ditambahkan Options -Indexes, maka hasilnya akan seperti gambar dibawah dengan cara mengakses penanjakan.semerud10.pw/direktori

```
<center>
  
![img](/img/no11.png)

![img](/img/no11.1.png)

![img](/img/no11.2.png)

![img](/img/no11.3.png)

![img](/img/no11.4.png)

</center>

<br>

12.
```
Pada uml probolinggo, lakukan konfigurasi pada file penanjakan.semerud10.pw dengan menambahkan sintaks seperti pada gambar.
Untuk mengecek apakah berhasil dilakukan dengan mengakses situs penanjakan.semerud10.pw/aJcjdcje maka akan mengarah ke halaman error.
```
<center>
  
![img](/img/no12.png)

![img](/img/no12.1.png)

</center>

<br>

13.
```
Pada uml probolinggo, lakukan konfigurasi pada file penanjakan.semerud10.pw dengan menambahkan sintaks Options +Indexes pada direktori yang mengarah kepada js dan Alias "/js" ...
Untuk mengecek apakah berhasil dilakukan dengan mengakses situs penanjakan.semerud10.pw/js maka akan mengarah ke halaman javascripts.
```
<center>
  
![img](/img/no13.png)

![img](/img/no13.1.png)

</center>

<br>

14.
```
Pada uml probolinggo, masuk ke direktori sites-available kemudian cp file default dan rename dengan nama naik.gunung.semerud10.pw lalu lakukan konfigurasi seperti gambar dibawah.
Jangan lupa untuk menambahkan Listen 8888 pada file ports.conf yang terletak pada direktori /etc/apache2
Untuk mengecek apakah berhasil dilakukan dengan mengakses situs naik.gunung.semerud10.pw
```
<center>
  
![img](/img/no14.png)

![img](/img/no14.1.png)

</center>

<br>

15.
```
Pada uml probolinggo, lakukan konfigurasi pada file naik.gunung.semerud10.pw dengan menambahkan sintaks seperti pada gambar dibawah. Lalu mulai menambahkan user dengan cara seperti pada gambar 15.1.
Untuk mengecek apakah berhasil dilakukan dengan mengakses situs naik.gunung.semerud10.pw
```
<center>
  
![img](/img/no15.png)

![img](/img/no15.1.png)

![img](/img/no15.2.png)

</center>

<br>

16.
```
Pada uml probolinggo, lakukan konfigurasi pada file default seperti pada gambar dibawah. Kemudian masuk ke direktori /var/www lalu membuat file .htaccess dan diisikan sintaks seperti pada gambar dibawah.
Untuk mengecek apakah berhasil dilakukan dengan mengakses ping probolinggo yaitu 10.151.79.92 maka akan berubah menjadi semerud10.pw
```
<center>
  
![img](/img/no16.1.png)

![img](/img/no16.png)

![img](/img/no16.2.png)

</center>

<br>

17.
```
Pada uml probolinggo, lakukan konfigurasi pada file penanjakan.semerud10.pw seperti pada gambar dibawah. Kemudian masuk ke direktori /var/www/penanjakan.semerud10.pw lalu membuat file .htaccess dan diisikan sintaks seperti pada gambar dibawah.
Untuk mengecek apakah berhasil dilakukan dengan mengakses situs penanjakan.semerud10.pw/public/images/bukansemeruaja.jpg maka akan redirect ke link penanjakan.semerud10.pw/public/images/semeru.jpg
```
<center>
  
![img](/img/no17.png)

![img](/img/no17.1.png)

![img](/img/no17.2.png)

</center>

<br>

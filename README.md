## Laporan Soal Shift Modul 2 DNS dan Web Server

Kalian diminta untuk membuat sebuah website utama dengan 

(1) alamat http://semeruyyy.pw yang memiliki

![gambar](/images/1.jpg)

Topologi

konfigurasi zone "semerua13.pw" 

![gambar](/images/2.png)

tambahkan semerua13.pw tipenya NS dan Petakan IP probolinggo

![gambar](/images/3.png)

testing

![gambar](/images/4.png)

(2) alias http://www.semeruyyy.pw, dan 

alias , www CNAME 

![gambar](/images/5.png)

testing

![gambar](/images/6.png)

(3) subdomain http://penanjakan.semeruyyy.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO serta dibuatkan 

nano /etc/bind/jarkom/semerua13.pw
tambah konfigurasi penanjakan

![gambar](/images/7.png)

testing

![gambar](/images/8.png)

(4) reverse domain untuk domain utama. Untuk mengantisipasi server dicuri/rusak, Bibah minta dibuatkan

tambah konfigurasi zone "71.151.10.in-addr.arpa" 

![gambar](/images/9.png)

tambahkan byte ke 4 IP probolinggo

![gambar](/images/10.png)

testing

![gambar](/images/11.png)

(5) DNS Server Slave pada MOJOKERTO agar Bibah tidak terganggu menikmati keindahan Semeru pada Website. Selain website utama Bibah juga meminta dibuatkan 

also-notify (masukan IP Mojokerto)

![gambar](/images/12.png)

type slave (IP malang)

![gambar](/images/13.png)

testing

![gambar](/images/14.png)

(6) subdomain dengan alamat 
http://gunung.semeruyyy.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO. Bibah juga ingin memberi petunjuk mendaki gunung semeru kepada anggota komunitas sehingga dia meminta dibuatkan 

edit konfigurasi server malang
konfigurasi ns1

![gambar](/images/48.png)

allow transfer

![gambar](/images/49.png)

edit konfirguasi server mojokerto

konfigurasi gunung.semerua13.pw

![gambar](/images/50.png)

buat direktori delegasi dan atur konfigurasi seperti dibawah

![gambar](/images/15.png)

testing

![gambar](/images/16.png)

(7) subdomain dengan nama http://naik.gunung.semeruyyy.pw, domain ini diarahkan ke IP Server PROBOLINGGO. Setelah selesai membuat keseluruhan domain, kamu diminta untuk segera mengatur web server. 

edit konfigurasi spt soal 6

![gambar](/images/17.png)

testing

![gambar](/images/18.png)

(8) Domain http://semeruyyy.pw memiliki DocumentRoot   pada /var/www/semeruyyy.pw. Awalnya web dapat diakses menggunakan alamat http://semeruyyy.pw/index.php/home. Karena dirasa alamat urlnya  kurang bagus, maka 

![gambar](/images/19.png)

![gambar](/images/20.png)

(9) diaktifkan mod rewrite agar urlnya menjadi http://semeruyyy.pw/home.

![gambar](/images/21.png)

![gambar](/images/22.png)

![gambar](/images/23.png)

(10) Web http://penanjakan.semeruyyy.pw akan digunakan untuk menyimpan assets file yang  memiliki DocumentRoot  pada /var/www/penanjakan.semeruyyy.pw dan memiliki struktur folder sebagai berikut: 
 /var/www/penanjakan.semeruyyy.pw 
/public/javascripts 
/public/css  
/public/images 
/errors  

![gambar](/images/24.png)

![gambar](/images/25.png)

![gambar](/images/27.png)

(11) Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan. 

![gambar](/images/27.png)

![gambar](/images/28.png)

![gambar](/images/29.png)

(12) Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache. 

![gambar](/images/30.png)

![gambar](/images/31.png)

![gambar](/images/32.png)

(13) Untuk mengakses file assets javascript awalnya harus menggunakan url http://penanjakan.semeruyyy.pw/public/javascripts. Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http://penanjakan.semeruyyy.pw/js.   Untuk web http://gunung.semeruyyy.pw belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai. 

![gambar](/images/33.png)

![gambar](/images/34.png)

![gambar](/images/35.png)

(14) sedangkan web http://naik.gunung.semeruyyy.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot  web berada pada /var/www/naik.gunung.semeruyyy.pw. Dikarenakan web http://naik.gunung.semeruyyy.pw bersifat private 

![gambar](/images/36.png)

![gambar](/images/37.png)

![gambar](/images/38.png)

(15) Bibah meminta kamu membuat web http://naik.gunung.semeruyyy.pw agar
diberi autentikasi password dengan username “semeru” dan password “kuynaikgunung” supaya aman dan tidak sembarang orang bisa mengaksesnya.  Saat Bibah mengunjungi IP PROBOLINGGO, yang muncul bukan web utama http://semeruyyy.pw melainkan laman default Apache yang bertuliskan “It works!”. 

![gambar](/images/39.png)

![gambar](/images/40.png)

![gambar](/images/41.png)

(16) Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http://semeruyyy.pw. 

![gambar](/images/42.png)

![gambar](/images/43.png)

(17) Karena pengunjung pada /var/www/penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.

![gambar](/images/44.png)

![gambar](/images/45.png)

![gambar](/images/46.png)

![gambar](/images/47.png)

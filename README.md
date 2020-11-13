## Laporan Soal Shift Modul 2 DNS dan Web Server

![gambar](/images/1.jpg)

topologi.sh

Kalian diminta untuk membuat sebuah website utama dengan 

(1) alamat http://semeruyyy.pw yang memiliki

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


(8) Domain http://semeruyyy.pw memiliki DocumentRoot   pada /var/www/semeruyyy.pw.

Copy file default.conf menjadi semerua13.pw, kemudian ganti servername, severalias dan documentrootnya.

![gambar](/images/19.png)

Testing

![gambar](/images/20.png)


(9) Awalnya web dapat diakses menggunakan alamat http://semeruyyy.pw/index.php/home. Karena dirasa alamat urlnya  kurang bagus, maka diaktifkan mod rewrite agar urlnya menjadi http://semeruyyy.pw/home.

Kita beri AllowOverride All pada folder /var/www/semerua13.pw

![gambar](/images/21.png)

Kita beri ReWrite rulenya ^home$ index.php/home [NC]

![gambar](/images/22.png)

Testing

![gambar](/images/23.png)


(10) Web http://penanjakan.semeruyyy.pw akan digunakan untuk menyimpan assets file yang  memiliki DocumentRoot  pada /var/www/penanjakan.semeruyyy.pw dan memiliki struktur folder sebagai berikut: 
- /var/www/penanjakan.semeruyyy.pw 
- /public/javascripts 
- /public/css  
- /public/images 
- /errors  

Copy file default.conf menjadi penanjakan.semerua13.pw, kemudian ganti servername, severalias dan documentrootnya.

![gambar](/images/24.png)

List isi /var/www/penanjakan.semerua13.pw dan /var/www/penanjakan.semerua13.pw/public

![gambar](/images/25.png)

Tampilan web penanjakan.semerua13.pw

![gambar](/images/26.png)


(11) Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan. 

Kita berikan Options -Indexes untuk semua folder dalam /var/www/penanjakan.semerua13.pw/public/

![gambar](/images/27.png)

folder /public bisa dilisting

![gambar](/images/28.png)

folder /public/images tidak dapat dilisting

![gambar](/images/29.png)


(12) Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache. 

Kita beri AllowOverride All pada direktori /var/www/penanjakan.semerua13.pw

![gambar](/images/30.png)

Buka file .htaccess yang berada pada /var/www/penanjakan.semerua13.pw kemudian kita tambahkan ``ErrorDocument 404 /errors/404.html`` agar ketika terjadi error 404 akan membuka file /error/404.html

![gambar](/images/31.png)

Testing ketika kita membuka penanjakan.semerua13.pw/abc 

![gambar](/images/32.png)


(13) Untuk mengakses file assets javascript awalnya harus menggunakan url http://penanjakan.semeruyyy.pw/public/javascripts. Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http://penanjakan.semeruyyy.pw/js.   Untuk web http://gunung.semeruyyy.pw belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai. 

Kita tambahkan Alias dalam file penanjakan.semerua13.pw kita seperti permintaan soal

![gambar](/images/33.png)

Testing ketika kita membuka penanjakan.semerua13.pw/js hasilnya adalah forbidden dan bukan 404 not found. Forbidden sendiri terjadi karena tadi kita tidak diperbolehkan mengakses direktori dalam /public.

![gambar](/images/34.png)


(14) sedangkan web http://naik.gunung.semeruyyy.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot  web berada pada /var/www/naik.gunung.semeruyyy.pw. Dikarenakan web http://naik.gunung.semeruyyy.pw bersifat private 

Kita tambahkan ``Listen 8888`` dalam file ports.conf

![gambar](/images/36.png)

Kemudian untuk file naik.gunung.semerua13.pw kita ganti virtual host dari 80 menjadi 8888

![gambar](/images/37.png)

Testing membuka naik.gunung.semerua13.pw:8888

![gambar](/images/38.png)


(15) Bibah meminta kamu membuat web http://naik.gunung.semeruyyy.pw agar
diberi autentikasi password dengan username “semeru” dan password “kuynaikgunung” supaya aman dan tidak sembarang orang bisa mengaksesnya.   

Pertama kita jalakan ``htpasswd -bc /var/www/naik.gunung.semerua13.pw/.htpasswd semeru kuynaikgunung`` pada uml. Statement tersebut digunakan untuk membuat file htpasswd pada /var/www/naik.gunung.semerua13.pw/ dengan username semeru dan password kuynaikgunung. Kemudian kita berikan AllowOverride All pada direktori /var/www/naik.gunung.semerua13.pw

![gambar](/images/39.png)

Kita tambahkan file .htaccess pada /var/www/naik.gunung.semerua13.pw

![gambar](/images/40.png)

Testing ketika kita membuka naik.gunung.semerua13.pw:8888, kita akan diminta untuk memasukkan username dan password

![gambar](/images/51.png)


(16) Saat Bibah mengunjungi IP PROBOLINGGO, yang muncul bukan web utama http://semeruyyy.pw melainkan laman default Apache yang bertuliskan “It works!”. Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http://semeruyyy.pw. 

Kita tambahkan ``Redirect / http:www.semerua13.pw/`` pada file default.conf

![gambar](/images/42.png)

Testing ketika kita mamasukkan ip Probolinggo, yaitu 10.151.73.116, maka kita akan diarahkan ke semerua13.pw

![gambar](/images/43.png)


(17) Karena pengunjung pada /var/www/penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.

Kita tambahklan AllowOverride All untuk direktori /var/www/penanjakan.semerua13.pw

![gambar](/images/44.png)

Kemudian pada .htaccess nya kita tambahkan RewriteRule sesuai ketentuan yang diminta soal

![gambar](/images/45.png)

Testing ketika membuka penanjakan.semerua13.pw/public/images/semeru.jpg

![gambar](/images/46.png)

Testing ketika membuka penanjakan.semerua13.pw/public/images/aaaasemeruaaaa.jpg

![gambar](/images/47.png)

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e8/Joomla%21-Logo.svg/2560px-Joomla%21-Logo.svg.png" alt="drawing" width="850"/>

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Maintenance](#Maintenance) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:--:|:--:|:--:|:--:|:--:|:--:|:--:

## Anggota Kelompok 5 | P2
1. Adri Aulia Mahran                         G6419
2. Citra Regita Nurtalia Wahyu Santosa       G6401201002
3. Naura Zhafira                             G6401201121

## Sekilas Tentang
[`^ back to top ^`](#)

Joomla! adalah sistem manajemen konten (CMS) gratis dan sumber terbuka yang dibangun di PHP Joomla! memungkinkan pengguna untuk mempublikasikan berbagai jenis situs web, seperti blog pribadi, aplikasi pemerintah, intranet dan ekstranet perusahaan, situs web bisnis kecil dan besar, dan lain -lain.


## Instalasi
[`^ back to top ^`](#)

**Kebutuhan Sistem**
- Ubuntu 20.04 VPS. We will use one of our SSD 2 VPS hosting plans.
- system user with sudo privileges
- MySQL database server version 5.1 or newer (5.5.3 + is recommended)
- Apache web server version 2.0 or newer (2.4 + is recommended)
- PHP version 5.3.10 or newer (7.3 + is recommended)

**Tahapan Instalasi**
1. Login ke akun Google Engine dan mengakses server menggunakan SSH yang disediakan oleh Google Virtual Machine.
     ```
     $ ssh crnwscitra@34.128.81.68 -p 22
    ```
2. Memastikan bahwa sistem sudah terbarukan.
     ```
     $ sudo apt-get update
     $ sudo apt-get upgrade
    ```
4. Penginstallan kebutuhan sistem `Apache webserver`, `PHP`, dan `MySQL`.
    ```
    $ sudo apt install apache2
    $ sudo apt-get install php
    $ sudo apt-get install libapache2-mod-php
    $ sudo apt-get install php-mysql
    $ sudo apt install php php-common libapache2-mod-php php-cli php-fpm php-mysql php-json php-opcache php-gmp php-curl php-intl php-mbstring php-xmlrpc         php-gd php-xml php-zip
    $ sudo mysql_secure_installation
    $ sudo apt-get install wget
    $ sudo apt-get install unzip
    ```
6. Pengunduhan aplikasi **Joomla** ke dalam sistem
     ```
     $ sudo wget https://downloads.joomla.org/cms/joomla4/4-0-3/Joomla_4-0-3-Stable-Full_Package.zip

     ```
8. Ekstrak file aplikasi **Joomla** yang sudah diunduh
     ```
     $ sudo unzip Joomla_4-0-3-Stable-Full_Package.zip -d /var/www/html/joomla
     ```
10. Ekstrak file pada direktori`/var/www/html/joomla` sebagai root direktori dari aplikasi **Joomla**
     ```
     $ sudo unzip Joomla_4-0-3-Stable-Full_Package.zip -d /var/www/html/joomla
     ```
12. Ubah kepemilikandari direktori ```/var/www/html/joomla```  ke  ```www-data```
     ```
     $ sudo chown -R www-data: /var/www/html/joomla
     ```
14. Membuat konfigurasi apache virtual host pada instalasi **Joomla**
     ```
     $ sudo nano /etc/apache2/sites-available/joomla.conf
     ```
     dan mengedit file joomla.conf dengan dengan baris berikut
     ```
     <VirtualHost *:80>
     ServerAdmin webadmin@34.128.81.68
     DocumentRoot /var/www/html/joomla/
     ServerName 34.128.81.68
     ServerAlias 34.128.81.68

     <Directory /var/www/html/joomla/>
          Options FollowSymlinks
          AllowOverride All
          Require all granted
     </Directory>

     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined
     </VirtualHost>
     ```
16. Setelah file tersimpan, kita harus menonaktifkan dulu default virtual host, lalu aktifkan **Joomla** virtual host
     ``` 
     $ sudo a2dissite 000-default
     $ sudo a2ensite joomla.conf 
     ```
18. Restart ```Apache2``` untuk menerapkan perubahan
     ```
     $ sudo systemctl restart apache2
     ```


## Konfigurasi
[`^ back to top ^`](#)
- Konfigurasi aplikasi dapat diakses setelah masuk ke akun admin

- Akses menu **Konfigurasi Global** dapat ditemukan pada submenu disebelah kiri layar

<img src="https://github.com/naurazhaf/komdat-kel5/blob/main/pictures/config1.png" alt="gambar" width="850"/>

- Pengaturan situs dapat dirubah sesuai yang dibutuhkan

<img src="https://github.com/naurazhaf/komdat-kel5/blob/main/pictures/config2.png" alt="gambar" width="850"/>

- Pengaturan server dapat dirubah sesuai yang dibutuhkan

<img src="https://github.com/naurazhaf/komdat-kel5/blob/main/pictures/config3.png" alt="gambar" width="850"/>

- Untuk manajemen website, mengenai modul dan lainnya dapat diatur di menu-menu berikut

<img width="183" alt="image" src="https://user-images.githubusercontent.com/84652339/197002278-fbfc06f0-6145-4f28-b762-ebbcfc430712.png">


##  Maintenance
[`^ back to top ^`](#)

Maintenance pada server diperlukan untuk memaksimalkan kinerja aplikasi dan meminimalisir terjadinya error dimasa yang akan datang Salah satu bentuk maintenance dapat dilakkan dengan membersihkan cache dan cache yang sudah kadaluwarsa.
- Opsi pembersihan cache dapat ditemukan dalam submenu dari menu Sistem

<img src="https://github.com/naurazhaf/komdat-kel5/blob/main/pictures/maintenance1.png" alt="gambar" width="850"/>

- Pembersihan Cache

<img src="https://github.com/naurazhaf/komdat-kel5/blob/main/pictures/maintenance2.png" alt="gambar" width="850"/>

- Pembersihan cache kadaluwarsa

<img src="https://github.com/naurazhaf/komdat-kel5/blob/main/pictures/maintenance3.png" alt="gambar" width="850"/>

- Pemeriksaan

<img src="https://github.com/naurazhaf/komdat-kel5/blob/main/pictures/maintenance4.png" alt="gambar" width="850"/>


Pembaruan aplikasi juga merupakan salah satu bentuk Maintenance. Menu pembaharuan dapat ditemukan pada menu panel kendali dan terdapat pada bar sebelah kiri aplikasi.

<img src="https://github.com/naurazhaf/komdat-kel5/blob/main/pictures/maintenance5.png" alt="gambar" width="400"/>

Tentunya, ketika kita sedang mengkonfigurasi ulang **Joomla!**, aplikasi perlu dirubah ke _maintenance mode_. Langkah untuk mengaktifkan _maintenance mode_:

1. Login sebagai admin ke aplikasi

2. Pilih menu Sistem dan pilih Konfigurasi Global pada menu _dropdown_ yang muncul

<img src="https://github.com/naurazhaf/komdat-kel5/blob/main/pictures/maintenance7.png" alt="gambar" width="400"/>

3. Lihat pada pengaturan situs, terhadap pilihan untuk memadamkan situs aplikasi

<img src="https://github.com/naurazhaf/komdat-kel5/blob/main/pictures/maintenance8.png" alt="gambar" width="400"/>

4. Klik tombol `Ya` atau `Tidak` untuk memadamkan situs aplikasi


## Cara Pemakaian
[`^ back to top ^`](#)

- Buka aplikasi website

- Login terlebih dahulu, pada halamat sample site

<img width="560" alt="image" src="https://user-images.githubusercontent.com/84652339/197003061-c86226d6-9e6b-4f50-93ee-aadb7f191115.png">

- Jika belum memiliki akun dapat register terlebih dahulu

<img width="477" alt="image" src="https://user-images.githubusercontent.com/84652339/197004608-c99758d5-6a02-4479-a6ab-96dc34841cb4.png">

- Lalu, kita dapat melihat menu beranda

<img width="456" alt="image" src="https://user-images.githubusercontent.com/84652339/197004489-b286329e-b2a4-47a5-a1c8-b58eb9edd13f.png">

- Sebelum menuliskan artikel kita harus login terlebih dahulu

## Kelebihan dan kekurangan
[`^ back to top ^`](#)

Terdapat kelebihan dan kekurangan dari aplikasi yang diimplementasi disini.

**kelebihan**
- Instalasi yang relatif mudah dilakukan.
- Penggunaan PHP yang bersahabat bagi pemula.
- Pembesaran skala aplikasi mudah dan praktis.
- Variasi terjemahan kedalam berbagai bahasa sehinggga mempermudah dalam mempelajarinya.

**kekurangan**
- Tracker tidak tersedia.
- Joomla jarang muncul di hasil pencarian pertama.
- Media yang didukung terbatas.

Ketika membandingkan **Joomla!** dengan Getsimple CMS, **Joomla!** memiliki keunggulan seperti penyimpanan yang tersimpan pada server dibanding dengan Getsimple yang mengandalkan penyimpanan secara lokal. Akan tetapi Getsimple diperuntukan untuk pengembangan aplikasi skala kecil tidak seperti Joomla! sehingga Joomla! tidak sefleksiblel Getsimple.


## Referensi
[`^ back to top ^`](#)
- [Joomla!](https://www.joomla.org/) - Joomla!
- [Keunggulan dan kelemahan Joomla!](https://idcloudhost.com/mengenal-kelebihan-dan-kekurangan-menggunakan-joomla-dalam-merancang-situs-web-dan-blog/
) - idCloudHost
- [Dokumentasi Instalasi](https://linuxhostsupport.com/blog/how-to-install-joomla-3-9-on-ubuntu-20-04/
) - Linux Support
- [Google Cloud COmputing](https://cloud.google.com/) - Google



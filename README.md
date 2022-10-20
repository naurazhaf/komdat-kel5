![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e8/Joomla%21-Logo.svg/2560px-Joomla%21-Logo.svg.png)

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:


## Sekilas Tentang
[`^ back to top ^`](#)

Joomla adalah sistem manajemen konten (CMS) gratis dan sumber terbuka yang dibangun di PHP Joomla memungkinkan pengguna untuk mempublikasikan berbagai jenis situs web, seperti blog pribadi, aplikasi pemerintah, intranet dan ekstranet perusahaan, situs web bisnis kecil dan besar, dan lain -lain.


## Instalasi
[`^ back to top ^`](#)
- Ubuntu 20.04 VPS. We will use one of our SSD 2 VPS hosting plans.
- system user with sudo privileges
- MySQL database server version 5.1 or newer (5.5.3 + is recommended)
- Apache web server version 2.0 or newer (2.4 + is recommended)
- PHP version 5.3.10 or newer (7.3 + is recommended)
1. Login ke akun Google Engine dan mengakses server menggunakan SSH yang disediakan oleh Google Virtual Machine.
     ```
     $ ssh ctrrnws@34.128.81.68 -p 22
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
14. Membuat jonfigurasi apache vortual host pada instalasi **Joomla**
     ```
     $ sudo nano /etc/apache2/sites-available/joomla.conf
     ```
     dan mengedit file joomla.conf dengan dengan baris berikut
     ```
     <VirtualHost *:80>
     ServerAdmin admin@your_domain.com
     DocumentRoot /var/www/html/joomla/
     ServerName your_domain.com
     ServerAlias www.your_domain.com

     <Directory /var/www/html/joomla/>
          Options FollowSymlinks
          AllowOverride All
          Require all granted
     </Directory>

     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined
     </VirtualHost>
     ```
16. Setelah file tersimpan, lalu aktifkan **Joomla** virtual host
     ``` 
     $ sudo a2ensite joomla.conf 
     ```
18. Restart ```Apache2``` untuk menerapkan perubahan
     ```
     $ sudo systemctl restart apache2
     ```


## Konfigurasi (opsional)
[`^ back to top ^`](#)
Pada file php.ini dilakukan perubahan guna meningkatkan fungsi dan kinerja aplikasi:
- memory_limit = 512M
- upload_max_filesize = 256M
- post_max_size = 256M 
- max_execution_time = 300
- output_buffering = off
- date.timezone = America/Chicago

##  Maintenance (opsional)
[`^ back to top ^`](#)

Setting tambahan untuk maintenance secara periodik, misalnya:
- buat backup database tiap pekan
- hapus direktori sampah tiap hari
- dll


## Otomatisasi (opsional)
[`^ back to top ^`](#)

Skrip shell untuk otomatisasi instalasi, konfigurasi, dan maintenance.


## Cara Pemakaian
[`^ back to top ^`](#)

- Tampilan aplikasi web
- Fungsi-fungsi utama
- Isi dengan data real/dummy (jangan kosongan) dan sertakan beberapa screenshot


## Pembahasan
[`^ back to top ^`](#)

- Pendapat anda tentang aplikasi web ini
    - kelebihan
    - kekurangan
- Bandingkan dengan aplikasi web lain yang sejenis


## Referensi
[`^ back to top ^`](#)

Cantumkan tiap sumber informasi yang anda pakai.

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



## Konfigurasi (opsional)
Pada file php.ini dilakukan perubahan guna meningkatkan fungsi dan kinerja aplikasi:
memory_limit = 512M
upload_max_filesize = 256M
post_max_size = 256M 
max_execution_time = 300
output_buffering = off
date.timezone = America/Chicago

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

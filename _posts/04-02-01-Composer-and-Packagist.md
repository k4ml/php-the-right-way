---
title: Composer dan Packagist
isChild: true
anchor: composer_and_packagist
---

## Composer dan Packagist {#composer_and_packagist_title}

Composer adalah sebuah pengelola ketergantungan (_dependency manager_) yang brilian untuk PHP. Daftarkan ketergantungan proyek Anda dalam file `composer.json`, lalu dengan beberapa perintah sederhana, Composer secara otomatis akan mendownload ketergantungan proyek Anda dan melakukan setup autoloading untuk Anda.

Sudah ada banyak _library_ PHP yang kompatibel dengan Composer, siap untuk digunakan dalam proyek Anda. "Paket-paket" tersebut terdaftar pada [Packagist] [1], repositori resmi untuk _library_ PHP yang kompatibel dengan Composer.

### Cara Install Composer

Anda dapat menginstal Composer di lokal (dalam direktori kerja Anda saat ini, meskipun hal ini tidak lagi dianjurkan) atau global (misalnya `/usr/local/bin`). Kita berasumsi bahwa Anda ingin menginstal Composer lokal. Dari direktori root proyek Anda:

    curl -s https://getcomposer.org/installer | php

Perintah di atas akan men-download `composer.phar` (arsip biner PHP). Anda dapat menjalankan composer dengan `php` untuk mengelola dependensi proyek Anda. <strong> Harap dicatat bahwa </ strong> Jika Anda mendownload dengan melakukan `pipe` langsung ke PHP, silakan baca sumber kode nya terlebih dulu untuk mengkonfirmasi bahwa kode tersebut aman.

#### Install di Windows

Untuk pengguna Windows cara termudah untuk memulai adalah dengan menggunakan [ComposerSetup] [6] installer, yang melakukan instalasi global dan set up `$ PATH` Anda sehingga Anda dapat memanggil `composer` dari direktori manapun dalam `Command Line` Anda.

### Cara Install Composer (manual)

Menginstal Composer secara manual adalah teknik canggih; Namun, ada berbagai alasan mengapa pengembang mungkin lebih memilih metode ini vs menggunakan rutin instalasi interaktif. Instalasi interaktif memeriksa instalasi PHP Anda untuk memastikan bahwa:

- versi PHP yang sedang digunakan mencukupi kebutuhan
- `Phar` file dapat dijalankan dengan benar
- hak akses direktori tertentu yang cukup
- ekstensi bermasalah tertentu tidak dimuat
- Pengaturan tertentu pada `php.ini` telah diatur

Karena instalasi manual tidak melakukan pemeriksaan di atas, Anda harus memutuskan apakah _trade-off_ nya sangat berharga untuk Anda. Dengan demikian, di bawah ini adalah bagaimana untuk mendapatkan Komposer secara manual:

    curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
    chmod +x $HOME/local/bin/composer

_Path_ `$HOME/local/bin` (atau direktori pilihan Anda) seharusnya sudah masuk dalam `$PATH` -- variabel lingkungan Anda. Hal ini akan mengakibatkan perintah `composer` menjadi tersedia.

Bila Anda menemukan dokumentasi yang menyatakan untuk menjalankan `Composer` sebagai `php composer.phar install`, Anda dapat mengganti dengan:

    composer install
    
Bagian ini akan menganggap Anda telah menginstal komposer global.

### Cara mendefinisikan ketergantungan dan cara installnya

Composer melacak dependensi proyek Anda dalam sebuah file yang bernama `composer.json`. Anda dapat mengelolanya dengan teks editor jika Anda suka, atau menggunakan `Composer` itu sendiri. Perintah `composer require` dapat menambahkan ketergantungan proyek dan jika Anda tidak memiliki file `composer.json`, file itu akan dibuat. Berikut ini adalah contoh yang menambahkan [Twig] [2] sebagai ketergantungan proyek Anda.

	composer require twig/twig:~1.8

Sebagai alternatif, perintah `composer init` akan memandu Anda melalui penciptaan file `composer.json` untuk proyek Anda. Selain itu, jika anda telah Anda membuat file `composer.json`, Anda dapat memberitahu Composer untuk men-download dan menginstal dependensi Anda ke direktori `vendor/`. Hal ini juga berlaku untuk proyek-proyek yang telah anda download yang sudah menyediakan file `composer.json`:

    composer install

Selanjutnya, tambahkan baris ini ke file utama aplikasi PHP Anda; ini akan memberitahu PHP untuk menggunakan autoloader Composer sebagai dependensi proyek Anda.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Sekarang Anda dapat menggunakan dependensi proyek Anda, dan mereka akan otomatis diambil pada permintaan.

### Meng-update ketergantungan

Composer membuat sebuah file bernama `composer.lock` yang menyimpan versi yang tepat dari setiap paket yang di-download ketika Anda pertama kali menjalankan `php composer.phar install`. Jika Anda berbagi proyek Anda dengan pengembang lain dan file `composer.lock` merupakan bagian dari distribusi Anda, ketika mereka menjalankan `php composer.phar install` mereka akan mendapatkan versi yang sama seperti Anda. Untuk memperbarui dependensi, jalankan `php composer.phar update`.

Hal ini sangat berguna ketika Anda mendefinisikan persyaratan versi yang fleksibel. Misalnya persyaratan versi ~ 1,8 berarti "sesuatu yang lebih baru dari 1.8.0, tetapi kurang dari 2.0.x-dev". Anda juga dapat menggunakan `*` wildcard seperti dalam `1.8. *`. Sekarang dengan menjalankan perintah `php composer.phar update`, Composer akan meng-upgrade semua dependensi Anda ke versi terbaru sesuai dengan batasan yang Anda tetapkan.

### Notifikasi Update

Untuk menerima pemberitahuan tentang rilis versi baru Anda dapat mendaftar untuk [VersionEye] [3], sebuah layanan web yang dapat memonitor
GitHub dan BitBucket menyumbang `composer.json` file dan mengirim email dengan rilis paket baru.

### Cek ketergantungan Anda terhadap masalah keamanan

The [Security Advisories Checker] [4] adalah layanan web dan alat perintah baris, keduanya akan memeriksa file `composer.lock` Anda dan memberitahu Anda jika Anda perlu memperbarui dependensi Anda.

* [Pelajari Composer][5]

[1]: http://packagist.org/
[2]: http://twig.sensiolabs.org
[3]: https://www.versioneye.com/
[4]: https://security.sensiolabs.org/
[5]: http://getcomposer.org/doc/00-intro.md
[6]: https://getcomposer.org/Composer-Setup.exe


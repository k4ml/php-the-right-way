---
isChild: true
anchor: command_line_interface
---

## Command Line Interface {#command_line_interface_title}

Pada dasarnya, PHP diciptakan untuk menulis aplikasi web. Akan tetapi PHP juga berguna untuk scripting program command line interface (CLI). CLI dengan PHP dapat membantu Anda mengotomatisasi tugas-tugas umum seperti pengujian, distribusi, dan aplikasi administratif.

Program CLI PHP sangat bermanfaat karena Anda dapat menggunakan kode aplikasi Anda secara langsung tanpa harus membuat dan mengamankan web GUI untuk itu. Hanya pastikan untuk tidak menempatkan script CLI PHP di root web publik Anda!

Coba jalankan PHP dari baris perintah Anda:

{% highlight bash %}
> php -i
{% endhighlight %}

Opsi `-i` akan menampilkan konfigurasi PHP Anda seperti fungsi [`phpinfo`] [phpinfo].

Mari kita menulis "Hello, $ name" Program CLI sederhana. Untuk mencobanya, membuat file bernama `hello.php`, seperti di bawah ini.

{% highlight php %}
<?php
if ($argc != 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}

PHP set up dua variabel khusus berdasarkan argumen apa script Anda dijalankan. [`$` argc] [argc] adalah variabel integer yang berisi argumen * count * dan [`$ argv`] [argv] adalah variabel array yang berisi nilai * setiap argumen *. Argumen pertama selalu nama file script PHP Anda, dalam hal ini `hello.php`.

Expresi `exit ()` digunakan dengan nomor selain nol untuk memberitahu shell bahwa perintah gagal. Kode keluar yang umum digunakan dapat ditemukan [di sini] [exit-kode].

Untuk menjalankan script kita di atas, jalankan baris perintah:

{% highlight bash %}
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
{% endhighlight %}


 * [Pelajari tentang menjalankan PHP dari command line][php-cli]
 * [Pelajari tentang setting Windows untuk menjalankan PHP dari command line][php-cli-windows]

[phpinfo]: http://php.net/manual/en/function.phpinfo.php
[cli-options]: http://www.php.net/manual/en/features.commandline.options.php
[argc]: http://php.net/manual/en/reserved.variables.argc.php
[argv]: http://php.net/manual/en/reserved.variables.argv.php
[php-cli]: http://php.net/manual/en/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/en/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits

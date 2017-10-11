---
post_title: "Belajar Menggunakan WP-CLI, Command Line Tool untuk WordPress"
layout: post
published: false
---
Pendahuluan {.no-mar-top}
-------------------------

WP-CLI merupakan sebuah program *command line* untuk mengelola website yang dibuat menggunakan WordPress. WP merupakan singkatan dari WordPress, sedangkan CLI merupakan kependekan dari *Command Line Interface*. Jadi, Dengan menggunakan WP-CLI Anda bisa mengutak-atik website WordPress Anda melalui *command prompt*.

Instalasi
---------

Contoh Penggunaan
-----------------

### Menginstal WordPress

1.  Mendownload WordPress versi terbaru menggunakan perintah `wp core download`

    <pre class="command-line" data-user="mi" data-host="localhost" data-output="2-5"><code class="language-bash">wp core download --path=belajarpemrograman.dev
    Creating directory '/var/www/belajarpemrograman.dev/'.
    Downloading WordPress 4.8.1 (en_US)...
    md5 hash verified: f3dd0e033519aa363eb07e13c6676e3c
    Success: WordPress downloaded.</code></pre>

2.  Membuat file wp-config.php dengan menggunakan perintah `wp config create`

    <pre class="command-line" data-user="mi" data-host="localhost" data-output="3"><code class="language-bash">cd belajarpemrograman.dev
    wp config create --dbname=belajarpemrograman --dbuser=root --dbprefix=bp_
    Success: Generated 'wp-config.php' file.</code></pre>

3.  Membuat database (MySQL) baru menggunakan nama database, username dan password database yang telah disimpan di file wp-config.php.

    <pre class="command-line" data-user="mi" data-host="localhost" data-output="2"><code class="language-bash">wp db create
    Success: Database created.</code></pre>

4.  Menginstal WordPress menggunakan `wp core install`

    <pre class="command-line" data-user="mi" data-host="localhost" data-output="2"><code class="language-bash">wp core install --url=belajarpemrograman.dev --title="Belajar Pemrograman" --admin_user=admin_istrator --admin_password=1lakhsdfi32kf --admin_email=mikhsan@belajarpemrograman.org
    Success: WordPress installed successfully.</code></pre>

Referensi
---------

-   [WP-CLI Handbook](https://make.wordpress.org/cli/handbook/quick-start/)
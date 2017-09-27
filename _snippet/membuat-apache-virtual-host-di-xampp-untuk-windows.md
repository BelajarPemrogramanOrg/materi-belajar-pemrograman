---
ID: 909
post_title: >
  Membuat Apache Virtual Host di XAMPP
  untuk Windows
author: Muhammad Ikhsan
post_excerpt: |
  <h2 class="no-mar-top">Contoh Kasus</h2>
  
  Saya ingin membuat virtual host di komputer saya dengan domain <code>belajarpemrograman.dev</code> untuk digunakan selama development. File-file kodingan saya simpan di lokasi <code>C:\xampp\htdocs\belajarpemrograman</code>. Jadi, untuk mengaksesnya melalui browser, saya dapat menggunakan <code>http://belajarpemrograman.dev</code>. Tidak perlu panjang-panjang <code>http://localhost/belajarpemrograman</code>. Selain itu, kelihatan lebih keren, kan!
  
  <h2>Langkah-Langkah</h2>
  
  <ol><li>Buka file konfigurasi tambahan Apache <code>httpd-vhosts.conf</code> dalam lokasi <code>C:\xampp-php5\apache\conf\extra</code></li>
  <li>Pada bagian akhir dari file, tambahkan konfigurasi berikut
  
  <pre>
  &lt;VirtualHost belajarpemrograman.dev:80&gt;
  DocumentRoot "C:/xampp/htdocs/belajarpemrograman"
  ServerAdmin belajarpemrograman.dev
  &lt;Directory "C:/xampp/htdocs/belajarpemrograman"&gt;
  Options Indexes FollowSymLinks
  AllowOverride All
  Require all granted
  &lt;/Directory&gt;
  &lt;/VirtualHost&gt;</pre></li></ol>
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/apache/membuat-apache-virtual-host-di-xampp-untuk-windows/
published: true
post_date: 2017-09-27 09:18:23
---
Contoh Kasus {.no-mar-top}
--------------------------

Saya ingin membuat virtual host di komputer saya dengan domain `belajarpemrograman.dev` untuk digunakan selama development. File-file kodingan saya simpan di lokasi `C:\xampp\htdocs\belajarpemrograman`. Jadi, untuk mengaksesnya melalui browser, saya dapat menggunakan `http://belajarpemrograman.dev`. Tidak perlu panjang-panjang `http://localhost/belajarpemrograman`. Selain itu, kelihatan lebih keren, kan!

Langkah-Langkah
---------------

1.  Buka file konfigurasi tambahan Apache `httpd-vhosts.conf` dalam lokasi `C:\xampp-php5\apache\conf\extra`
2.  Pada bagian akhir dari file, tambahkan konfigurasi berikut

    ```
    <VirtualHost belajarpemrograman.dev:80>
        DocumentRoot "C:/xampp/htdocs/belajarpemrograman"
        ServerAdmin belajarpemrograman.dev
        <Directory "C:/xampp/htdocs/belajarpemrograman">
            Options Indexes FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>
    </VirtualHost>
    ```

    Sesuaikan konfigurasi dengan kebutuhan Anda. Direktori tidak harus berada di lokasi `C:/xampp/htdocs`. Kalaupun file-file PHP untuk project yang ingin Anda setting berada di lokasi `D:/belajarpemrograman`, Anda dapat menggunakannya. Maksud saya, tidak harus dipindahkan ke `C:/xampp/htdocs`.

3.  Buka file `hosts` dengan lokasi `C:\Windows\System32\drivers\etc\hosts` menggunakan hak akses Administrator.
4.  Tambahkan baris berikut ke dalam file `hosts`

    ```
    127.0.0.1 belajarpemrograman.dev
    ```

    Konfigurasi di atas mengatur agar ketika kita mengakses `belajarpemrograman.dev`, Windows akan mengarahkan ke `127.0.0.1` alias localhost.

5.  Restart Apache
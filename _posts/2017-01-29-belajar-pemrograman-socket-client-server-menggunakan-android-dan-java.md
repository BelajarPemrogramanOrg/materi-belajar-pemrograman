---
ID: 151
post_title: 'Belajar Pemrograman Socket Client &#8211; Server Menggunakan Android dan Java'
author: Muhammad Ikhsan
post_date: 2017-01-29 14:48:07
post_excerpt: |
  Dalam tutorial ini, kita akan membuat dua buah program sederhana untuk menerapkan komunikasi client - server menggunakan socket. Aplikasi client yg akan kita buat berupa sebuah aplikasi Android, sedangkan aplikasi server berupa program yg ditulis dalam bahasa pemrograman Java yg dijalankan di komputer. Anda dapat mendownload source code aplikasi yg akan kita buat <a href="http://belajarpemrograman.app/pemrograman-jaringan/belajar-pemrograman-socket-client-server-menggunakan-android-dan-java/#download-source-code">pada bagian akhir dari tulisan ini</a>.
  <h2>Detail Aplikasi</h2>
  Berikut merupakan detail dari aplikasi yg akan kita buat:
  <ul>
  <li>Sebuah aplikasi Android akan dibuat sebagai client. Aplikasi diberi nama <strong>Panggil Saya</strong>. <em>(Gak usah protes soal nama.. Silahkan kalo mau ganti. hehe)</em></li>
  <li>Sebuah aplikasi yg ditulis dengan Java akan dijalankan sebagai server dalam sebuah komputer.</li>
  <li>Untuk menjalankannya, perangkat Android dan komputer harus berada dalam satu jaringan, misalnya keduanya terkoneksi pada jaringan wireless yg sama. Dapat menggunakan <em>tether</em>.</li>
  <li>Aplikasi client (aplikasi Android) akan mengirimkan <code>{nama orang}</code>, dan server akan memberikan balasan berupa <code>Halo, {nama orang}!</code>. Contoh: client mengirimkan <code>Ikhsan</code>, kemudian server akan membalasnya dengan <code>Halo, Ikhsan!</code>.</li>
  </ul>
layout: post
permalink: >
  http://belajarpemrograman.org/belajar-pemrograman-socket-client-server-menggunakan-android-dan-java/
published: true
---
Dalam tutorial ini, kita akan membuat dua buah program sederhana untuk menerapkan komunikasi client - server menggunakan socket. Aplikasi client yg akan kita buat berupa sebuah aplikasi Android, sedangkan aplikasi server berupa program yg ditulis dalam bahasa pemrograman Java yg dijalankan di komputer. Anda dapat mendownload source code aplikasi yg akan kita buat <a href="http://belajarpemrograman.org/pemrograman-jaringan/belajar-pemrograman-socket-client-server-menggunakan-android-dan-java/#download-source-code">pada bagian akhir dari tulisan ini</a>.
<h2>Detail Aplikasi</h2>
Berikut merupakan detail dari aplikasi yg akan kita buat:
<ul>
 	<li>Sebuah aplikasi Android akan dibuat sebagai client. Aplikasi diberi nama <strong>Panggil Saya</strong>. <em>(Gak usah protes soal nama.. Silahkan kalo mau ganti. hehe)</em></li>
 	<li>Sebuah aplikasi yg ditulis dengan Java akan dijalankan sebagai server dalam sebuah komputer.</li>
 	<li>Untuk menjalankannya, perangkat Android dan komputer harus berada dalam satu jaringan, misalnya keduanya terkoneksi pada jaringan wireless yg sama. Dapat menggunakan <em>tether</em>.</li>
 	<li>Aplikasi client (aplikasi Android) akan mengirimkan <code>{nama orang}</code>, dan server akan memberikan balasan berupa <code>Halo, {nama orang}!</code>. Contoh: client mengirimkan <code>Ikhsan</code>, kemudian server akan membalasnya dengan <code>Halo, Ikhsan!</code>.</li>
 	<li>Antarmuka aplikasi Android terdiri dari:
<ul>
 	<li>Sebuah <code>EditText</code> untuk mengisikan IP server</li>
 	<li>Sebuah <code>EditText</code> untuk mengisikan port yg digunakan oleh server untuk menerima request</li>
 	<li>Sebuah <code>EditText</code> untuk mengisikan nama orang yg akan dikirimkan ke server</li>
 	<li>Sebuah <code>Button</code> untuk mengirimkan request ke server</li>
 	<li>Sebuah <code>TextView</code> untuk menampilkan respon dari server</li>
</ul>
</li>
</ul>
Berikut merupakan <em>screenshot</em> yang dapat membantu menggambarkan jalannya aplikasi yg akan kita buat.

[gallery type="rectangular" link="file" size="medium" ids="176,180,182"]
<h2>Mengenal Socket</h2>
<strong><em>Wait</em>,</strong> sebelum kita lanjutkan, pastikan kita sudah mengerti apa yg dimaksud dengan <em>socket</em> yg dari tadi disebut-sebut. Kalau kelihatan ribet, setidaknya dibaca saja. Semoga nanti setelah praktik membuat aplikasinya dan berhasil menjalankannya, jadi lebih ngerti.

Mengenai pemrograman socket menggunakan bahasa pemrograman Java yang tidak dibahas secara mendetail dalam tulisan ini, Anda dapat membacanya pada tulisan lain di website ini yg berjudul <a href="http://belajarpemrograman.app/pemrograman-jaringan/belajar-pemrograman-socket-menggunakan-java/">Belajar Pemrograman Socket Menggunakan Java</a>.
<h3>Pengertian Socket</h3>
<ul>
 	<li>Socket merupakan sebuah titik akhir dalam komunikasi dua arah antara dua program pada suatu jaringan.</li>
 	<li>Sebuah socket terdiri dari alamat IP dan port. Contoh: <code>172.20.10.5:8888</code>.
<code>172.20.10.5</code> merupakan alamat IP dan <code>8888</code> merupakan port.</li>
</ul>
Dalam komunikasi antara 2 program (client dan server), masing-masing memiliki socket sebagai titik akhir dalam komunikasi. Jika client ingin meminta request kepada server, maka client akan menghubungi socket milik server. Begitu pula sebaliknya, ketika server akan memberikan balasan kepada client, maka server akan mengirimkan balasan tersebut ke socket milik client.
<h3>Contoh Skenario Penggunaan Socket</h3>
Sebagai contoh, Anda mengakses sebuah website melalui browser, misalnya <a href="http://example.com" target="_blank">example.com</a>. Browser di komputer Anda merupakan sebuah aplikasi client yg meminta request ke <em>web server</em> yg meng-<em>host</em> <a href="http://example.com" target="_blank">example.com</a>. Browser Anda akan meminta agar sistem operasi Anda menyiapkan socket untuk komunikasi ke server dengan <em>hostname </em><a href="http://example.com" target="_blank">example.com</a> dan port <code>80</code> (nomor port yg digunakan untuk <code>http</code>). Dalam paket jaringan yg dikirimkan oleh sistem operasi, akan disertakan beberapa informasi, termasuk alamat IP dan port komputer Anda yg digunakan untuk komunikasi socket, dan alamat IP dan nomor port tujuan (server). Selanjutnya, jika semuanya berjalan dengan baik, server akan menerima request dan dapat memberikan respon yg sesuai kepada client.

Dari contoh yg disebutkan di atas, client harus sudah mengetahui socket (alamat IP dan nomor port) milik server yg dituju. Kemudian, socket milik client secara otomatis dibuat oleh sistem operasi yg akan sebenarnya membuat request. Dalam request yg dikirimkan ke server, disertakan socket asal dan tujuan, sehingga server dapat memeriksa terlebih dahulu apakah request yg diterimanya memang benar-benar ditujukan kepadanya. Selain itu, dengan informasi alamat socket milik client, server akan mengetahui ke manakah server akan memberikan balasan.
<h2>Kode Program</h2>
<h3>Aplikasi Server</h3>
Aplikasi server yg kita buat akan menggunakan port <code>8888</code>. Adapun alamat IP yg digunakan server merupakan alamat IP komputer di mana server dijalankan. Anda dapat menjalankan <code>ipconfig</code> di <em>command prompt</em> (jika Anda menggunakan Windows) untuk mengecek IP komputer Anda.

<strong>File: <code>PanggilSayaServer.java</code></strong>

https://gist.github.com/alwayzmile/49e022a23e9bc888e9a35384d37a3627

Mari kita <em>compile</em> dan jalankan kode di atas.
<pre>&gt; javac PanggilSayaServer.java
&gt; java PanggilSayaServer
PanggilSayaServer sedang berjalan, menunggu request dari client.

</pre>
Untuk menghentikan server, gunakan <strong>Ctrl+C</strong>.
<h3>Aplikasi Client</h3>
Mari kita buat sebuah project Android baru dengan nama <strong>Panggil Saya</strong>. Saya menggunakan Android Studio 2.2 dan Java 1.8. Untuk nama package aplikasi, saya menggunakan <code>com.mikhsan.practice.panggilsaya</code>. Minimum SDK saya set API 16: Android 4.1 (Jelly Bean). Hal-hal tersebut, seperti nama aplikasi, bukanlah merupakan suatu ketentuan, silahkan dirubah sesuai keinginan Anda. Namun, jika Anda menggunakan nama package yg berbeda, pastikan Anda juga menyesuaikannya pada kode yg akan kita buat.

Mari kita buat tampilan antarmukanya terlebih dahulu.

<strong>File: <code>activity_main.xml</code></strong>

https://gist.github.com/alwayzmile/437818373ed252fc27bd639cc8d81fec#file-activity_main-xml

Untuk menangani masalah pembuatan request ke server dan menerima respon dari server, yg kemudian menampilkan respon tersebut, kita akan membuat sebuah kelas baru dengan nama <code>Communication</code>.

<strong>File: <code>Communication.java</code></strong>

https://gist.github.com/alwayzmile/437818373ed252fc27bd639cc8d81fec#file-Communication-java

Selanjutnya, kita akan menginisialisasi objek <code>Communication</code> setiap kali tombol <strong>Panggil Saya!</strong> dan memulai komunikasi dengan server. Kode tersebut akan kita tambahkan ke file <code>MainActivity.java</code>.

<strong>File: <code>MainActivity.java</code></strong>

https://gist.github.com/alwayzmile/437818373ed252fc27bd639cc8d81fec#file-MainActivity-java

Dan yang terakhir, karena kita melakukan komunikasi jaringan, maka kita perlu menambahkan sebuah <code>uses-permission</code> tag ke file <code>AndroidManifest.xml</code>.

<strong>File: <code>AndroidManifest.xml</code></strong>

https://gist.github.com/alwayzmile/437818373ed252fc27bd639cc8d81fec#file-AndroidManifest-xml
<h2 id="download-source-code">Download Source Code</h2>
[su_button url="http://belajarpemrograman.org/wp-content/uploads/2017/02/PanggilSayaServer.zip" background="#909090" icon="icon: cloud-download"]Download Server Source Code[/su_button] [su_button url="http://belajarpemrograman.org/wp-content/uploads/2017/02/AndroidPanggilSaya.zip" background="#909090" icon="icon: cloud-download"]Download Client Source Code[/su_button]
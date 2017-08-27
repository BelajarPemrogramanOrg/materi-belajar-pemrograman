---
ID: 169
post_title: >
  Belajar Pemrograman Socket Menggunakan
  Java
author: Muhammad Ikhsan
post_date: 2017-01-28 23:05:42
post_excerpt: >
  Kita akan mengenal istilah socket dalam
  pemrograman jaringan komputer. Dengan
  bekal ilmu pengetahuan tentang
  pemrograman socket, kita dapat memiliki
  dasar ilmu untuk membuat aplikasi
  browser, chat, game online multi-user,
  email client/server dan berbagai
  aplikasi lainnya yg membutuhkan
  jaringan. Dalam tulisan ini kita akan
  mempelajari konsep socket dan dasar dari
  penerapannya dalam bahasa pemrograman
  Java.
layout: post
permalink: >
  http://belajarpemrograman.org/belajar-pemrograman-socket-menggunakan-java/
published: true
---
Dalam tulisan ini, kita akan mengenal istilah socket dalam pemrograman jaringan komputer. (<em>Ya, kalau setelah baca judulnya, kok ada yg belum nangkep, kita ngomongin apa.? Kenapa kok nyebut socket-socket..? Jawabannya, kita sedang bicara tentang pemrograman jaringan komputer.)</em> Dalam tulisan ini kita akan mempelajari konsep dan dasar penerapan pemrograman socket menggunakan Java.
<h2>Pendahuluan</h2>
Aplikasi seperti apakah yg dapat kita buat dengan memiliki bekal ilmu mengenai pemrograman socket? Dengan bekal ilmu pengetahuan tentang pemrograman socket, kita dapat memiliki dasar ilmu untuk membuat aplikasi/program:
<ul>
 	<li>browser,</li>
 	<li>chat,</li>
 	<li>game online multi-user,</li>
 	<li>email client/server</li>
 	<li>dan berbagai aplikasi lainnya yg membutuhkan jaringan.</li>
</ul>
Wow, banyak hal <em>wah </em>yg dapat dihasilkan.

Salah satu kesamaan dari berbagai jenis aplikasi yg disebutkan, yaitu menggunakan komunikasi jaringan antara client dan server. <strong>Komunikasi client - server dilakukan dari satu titik sumber ke satu titik tujuan.</strong> Browser, yg Anda gunakan untuk mengakses website ini, akan menghubungi web server yang menyediakan website ini. Kemudian web server akan memberikan balasan berupa konten website pada url yg diminta kepada browser Anda.

<strong>Komunikasi antara client dan server dilakukan secara dua arah.</strong> Selain browser dapat mengirim permintaan kepada web server, browser juga dapat menerima balasan dari server. Begitu pula dengan web server, web server dapat menerima permintaan dan juga mengirimkan balasan dari permintaan. Sehingga, baik browser maupun web server dapat menjadi <strong>titik sumber</strong> dan <strong>titik tujuan</strong>. Kedua titik ini dapat disebut sebagai <em><strong>endpoint</strong></em>, atau dalam Bahasa Indonesia, saya artikan menjadi titik akhir.
<h2>Apa Itu Socket?</h2>
Socket merupakan sebuah titik akhir dalam komunikasi dua arah antara dua program pada suatu jaringan. Sebuah socket terdiri dari alamat IP dan port. Contoh: <code>172.20.10.5:80</code>. <code>172.20.10.5</code> merupakan alamat IP dan <code>80</code> merupakan nomor port.
<h3>Alamat IP dan Nomor Port</h3>
Jika sudah jelas bahwa setiap komputer di Internet memiliki alamat IP yg unik, lalu apa dan untuk apakah nomor port? Satu komputer dengan satu alamat IP dapat melakukan lebih dari satu komunikasi jaringan. Sebuah komputer dengan alamat IP <code>172.20.10.5</code> yg memiliki aplikasi web server terinstall di dalamnya, bukan berarti tidak bisa digunakan untuk menjadi server bagi aplikasi chat yang akan kita buat. Bukan berarti juga komputer tersebut tidak dapat digunakan untuk menjadi mail server atau file server.

Oleh karenanya, ketika sebuah komputer client hendak menghubungi web server yg memiliki alamat IP <code>172.20.10.5</code>, client membutuhkan identitas tambahan yg menunjukkan alamat persisnya web server. Alamat IP saja tidak cukup. Sehingga digunakanlah nomor port. Secara default, web server menggunakan port <code>80</code>. Maka, client dapat menghubungi web server melalui alamat socket <code>172.20.10.5:80</code>.

Lebih lanjut lagi, client dan server dapat kita jalankan pada komputer yg sama, dengan alamat IP yg sama, namun menggunakan port yg berbeda. Jadi, untuk belajar dan mencoba membuat program menggunakan socket, kita tidak harus memiliki dua komputer yang terhubung melalui jaringan.
<h3>Komunikasi Menggunakan Socket</h3>
Biasanya, sebuah aplikasi sebagai server dijalankan dalam sebuah komputer dengan socket menggunakan port tertentu. Ketika dijalankan, server hanya menunggu jika ada permintaan dari client yg ditujukan ke socket milik server.

Untuk membuat koneksi ke server, client harus sudah mengetahui socket dari server. Dengan kata lain, client harus sudah mengetahui alamat IP (atau bisa juga dalam bentuk <em>hostname </em>seperti <a href="http://example.com" target="_blank">example.com</a>) dan port yg dituju dalam pengiriman request. Dalam request tersebut, client menyertakan alamat IP dan port milik client (yaitu sumber request yg biasanya sudah ditentukan oleh sistem operasi milik client) dan alamat IP dan port yg dituju (milik server). Server siap-siap saja menerima request dari client dengan IP mana saja dan port apa saja, selagi request tersebut diarahkan ke alamat IP dan port yg digunakan oleh aplikasi server.
<h2>Pemrograman Socket di Java</h2>
Sekarang, mari kita pelajari dasar-dasar implementasinya menggunakan Java.

<h3>Membuka Socket di Client</h3>
<em>Class</em> yg berhubungan dengan socket, tersedia di dalam package <code>java.net</code>. Sehingga ketika kita membutuhkan kelas <code>ServerSocket</code> dan <code>Socket</code> kita dapat meng-<em>import</em>-nya dengan menggunakan kode berikut.
<pre><code class="language-java line-numbers">import java.net.ServerSocket;
import java.net.Socket;</code></pre>
Ketika kita akan menghubungkan client ke server dengan alamat IP server <code>192.168.1.1</code> dan nomor port server <code>8888</code>, kita menggunakan kode berikut.
<pre><code class="language-java line-numbers">Socket socket = null;
socket = new Socket("192.168.1.1", 8888);</code></pre>
Untuk menangani <code>IOException</code> yg dapat terjadi dalam pembukaan socket, kode di atas dapat diubah menjadi seperti berikut.
<pre><code class="language-java line-numbers">Socket socket = null;
try {
  socket = new Socket("192.168.1.1", 8888);
} catch (IOException e) {
  e.printStackTrace();
}</code></pre>
Perlu diketahui bahwa port nomor 0 hingga 1023 telah di-<em>reserved</em>, digunakan sebagai port untuk layanan-layanan standar seperti port 80 untuk <abbr title="Hypertext Transfer Protocol">HTTP</abbr> dan port 21 untuk <abbr title="File Transfer Protocol">FTP</abbr>. Sehingga, kita gunakan nomor port &gt; 1023 dalam pembuatan socket.

<h3>Membuka Socket di Server</h3>
Di sisi server, kita akan perlu menggunakan <code>ServerSocket</code> untuk membuka socket yg akan menerima request dari client. Misalkan, server akan mendengarkan <em>(listen to)</em> port nomor 8888, maka kita gunakan kode berikut.
<pre><code class="language-java line-numbers">ServerSocket serverSocket = null;
try {
  serverSocket = new ServerSocket(8888);
} catch (IOException e) {
  e.printStackTrace();
}</code></pre>
Untuk meng-<em>accept</em> (menerima) permintaan dari client, kita perlu membuat sebuah <code>Socket</code> yg khusus akan digunakan untuk melayani permintaan dari client tertentu. Kode untuk ini dapat disisipkan ke kode di atas sehingga menjadi seperti berikut.
<pre><code class="language-java line-numbers">ServerSocket serverSocket = null;
try {
  serverSocket = new ServerSocket(8888);
<strong>  Socket socket = serverSocket.accept();</strong>
} catch (IOException e) {
  e.printStackTrace();
}</code></pre>

<h3>Membuat Input Stream</h3>
Agar client dapat <strong>menerima</strong> respon dari server, kita dapat menggunakan <code>DataInputStream</code>.
<pre><code class="language-java line-numbers">DataInputStream input;
try {
  input = new DataInputStream(socket.getInputStream());
} catch (IOException e) {
  System.out.println(e);
}</code></pre>

Begitu pula di sisi server, <code>DataInputStream</code> juga dapat digunakan untuk <strong>menerima</strong> request dari client.
<pre><code class="language-java line-numbers">DataInputStream input;
try {
  input = new DataInputStream(serverSocket.getInputStream());
} catch (IOException e) {
  System.out.println(e);
}</code></pre>

<h3>Membuat Output Stream</h3>
<code>DataOutputStream</code> atau <code>PrintStream</code> dapat kita gunakan untuk <strong>mengirim</strong> request dari client ke server.
<pre><code class="language-java line-numbers">PrintStream output;
try {
  output = new PrintStream(socket.getOutputStream());
} catch (IOException e) {
  System.out.println(e);
}</code></pre>

<pre><code class="language-java line-numbers">DataOutputStream output;
try {
  output = new DataOutputStream(socket.getOutputStream());
} catch (IOException e) {
  System.out.println(e);
}</code></pre>

Di server, kita juga dapat menggunakan <code>DataOutputStream</code> dan <code>PrintStream</code> untuk <strong>mengirim</strong> informasi ke client.

<h2>Contoh Pengaplikasian Pemrograman Socket</h2>
Contoh pengaplikasian dari materi pemrograman socket menggunakan Java ini dapat dilihat di materi belajar <a href="https://belajarpemrograman.org/belajar-pemrograman-socket-client-server-menggunakan-android-dan-java/">Belajar Pemrograman Socket Client – Server Menggunakan Android dan Java</a>. Contoh yang dijelaskan pada materi tersebut sangatlah sederhana. Dalam materi tersebut kita belajar membuat sebuah aplikasi Android sebagai client dan sebuah aplikasi <em>console</em> sebagai server. User mengisikan nama dan alamat socket server. Kemudian, saat tombol <code>Panggil Saya</code> ditekan, server akan memberikan balasan berupa text dengan format <code>Hai, Nama!</code>.

Demikian materi belajar ini. Sebenarnya, masih banyak yang dapat kita pelajari tentang pemrograman socket. Materi ini dimaksudkan untuk memberikan gambaran umumnya. Materi-materi belajar tentang pemrograman jaringan di website ini, akan dimasukkan ke dalam kategori <a href="/category/pemrograman-jaringan/">Pemrograman Jaringan</a>. Anda juga dapat menemukannya di <a href="https://www.google.com/search?q=pemrograman+jaringan" target="_blank">Google</a> dengan kata kunci <code>pemrograman jaringan</code>. Selamat mengeksplorasi lebih lanjut!
<h4></h4>

<hr />

<h4>Referensi:</h4>
<ul>
 	<li>Penjelasan dan gambar tentang socket: <a href="https://docs.oracle.com/javase/tutorial/networking/sockets/definition.html" target="_blank">What is a Socket?</a></li>
 	<li>Penjelasan tentang pemrograman socket di Java: <a href="http://www.javaworld.com/article/2077322/core-java/core-java-sockets-programming-in-java-a-tutorial.html" target="_blank">Sockets programming in Java: A tutorial</a></li>
</ul>
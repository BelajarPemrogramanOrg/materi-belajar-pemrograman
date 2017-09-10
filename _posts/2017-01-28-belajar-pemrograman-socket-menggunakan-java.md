---
ID: 169
post_title: >
  Belajar Pemrograman Socket Menggunakan
  Java
author: Muhammad Ikhsan
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
post_date: 2017-01-28 23:05:42
---
Dalam tulisan ini, kita akan mengenal istilah socket dalam pemrograman jaringan komputer. (*Ya, kalau setelah baca judulnya, kok ada yg belum nangkep, kita ngomongin apa.? Kenapa kok nyebut socket-socket..? Jawabannya, kita sedang bicara tentang pemrograman jaringan komputer.)* Dalam tulisan ini kita akan mempelajari konsep dan dasar penerapan pemrograman socket menggunakan Java.

Pendahuluan {#pendahuluan}
-----------

Aplikasi seperti apakah yg dapat kita buat dengan memiliki bekal ilmu engenai pemrograman socket? Dengan bekal ilmu pengetahuan tentang pemrograman socket, kita dapat memiliki dasar ilmu untuk membuat aplikasi/program:

-   browser,
-   chat,
-   game online multi-user,
-   email client/server
-   dan berbagai aplikasi lainnya yg membutuhkan jaringan.

Wow, banyak hal *wah* yg dapat dihasilkan. Salah satu kesamaan dari berbagai jenis aplikasi yg disebutkan, yaitu menggunakan komunikasi jaringan antara client dan server. **Komunikasi client - server dilakukan dari satu titik sumber ke satu titik tujuan.** Browser, yg Anda gunakan untuk mengakses website ini, akan menghubungi web server yang menyediakan website ini. Kemudian web server akan memberikan balasan berupa konten website pada url yg diminta kepada browser Anda.

**Komunikasi antara client dan server dilakukan secara dua arah.** Selain browser dapat mengirim permintaan kepada web server, browser juga dapat menerima balasan dari server. Begitu pula dengan web server, web server dapat menerima permintaan dan juga mengirimkan balasan dari permintaan. Sehingga, baik browser maupun web server dapat menjadi **titik sumber** dan **titik tujuan**. Kedua titik ini dapat disebut sebagai ***endpoint***, atau dalam Bahasa Indonesia, saya artikan menjadi titik akhir.

Apa Itu Socket? {#apa-itu-socket}
---------------

Socket merupakan sebuah titik akhir dalam komunikasi dua arah antara dua program pada suatu jaringan. Sebuah socket terdiri dari alamat IP dan port. Contoh: `172.20.10.5:80`. `172.20.10.5` merupakan alamat IP dan `80` merupakan nomor port.

### Alamat IP dan Nomor Port {#alamat-ip-dan-nomor-port}

Jika sudah jelas bahwa setiap komputer di Internet memiliki alamat IP yg unik, lalu apa dan untuk apakah nomor port? Satu komputer dengan satu alamat IP dapat melakukan lebih dari satu komunikasi jaringan. Sebuah komputer dengan alamat IP `172.20.10.5` yg memiliki aplikasi web server terinstall di dalamnya, bukan berarti tidak bisa digunakan untuk menjadi server bagi aplikasi chat yang akan kita buat. Bukan berarti juga komputer tersebut tidak dapat digunakan untuk menjadi mail server atau file server. 

Oleh karenanya, ketika sebuah komputer client hendak menghubungi web server yg memiliki alamat IP `172.20.10.5`, client membutuhkan identitas tambahan yg menunjukkan alamat persisnya web server. Alamat IP saja tidak cukup. Sehingga digunakanlah nomor port. Secara default, web server menggunakan port `80`. Maka, client dapat menghubungi web server melalui alamat socket `172.20.10.5:80`. 

Lebih lanjut lagi, client dan server dapat kita jalankan pada komputer yg sama, dengan alamat IP yg sama, namun menggunakan port yg berbeda. Jadi, untuk belajar dan mencoba membuat program menggunakan socket, kita tidak harus memiliki dua komputer yang terhubung melalui jaringan.

### Komunikasi Menggunakan Socket {#komunikasi-menggunakan-socket}

Biasanya, sebuah aplikasi sebagai server dijalankan dalam sebuah komputer dengan socket menggunakan port tertentu. Ketika dijalankan, server hanya menunggu jika ada permintaan dari client yg ditujukan ke socket milik server.

Untuk membuat koneksi ke server, client harus sudah mengetahui socket dari server. Dengan kata lain, client harus sudah mengetahui alamat IP (atau bisa juga dalam bentuk *hostname* seperti [example.com]) dan port yg dituju dalam pengiriman request. Dalam request tersebut, client menyertakan alamat IP dan port milik client (yaitu sumber request yg biasanya sudah ditentukan oleh sistem operasi milik client) dan alamat IP dan port yg dituju (milik server). Server siap-siap saja menerima request dari client dengan IP mana saja dan port apa saja, selagi request tersebut diarahkan ke alamat IP dan port yg digunakan oleh aplikasi server.

Pemrograman Socket di Java {#pemrograman-socket-di-java}
--------------------------

Sekarang, mari kita pelajari dasar-dasar implementasinya menggunakan Java.

### Membuka Socket di Client {#membuka-socket-di-client}

*Class* yg berhubungan dengan socket, tersedia di dalam package `java.net`. Sehingga ketika kita membutuhkan kelas `ServerSocket` dan `Socket` kita dapat meng-*import*-nya dengan menggunakan kode berikut.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
import java.net.ServerSocket;
import java.net.Socket;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ketika kita akan menghubungkan client ke server dengan alamat IP server `192.168.1.1` dan nomor port server `8888`, kita menggunakan kode berikut.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
Socket socket = null;
socket = new Socket(&quot;192.168.1.1&quot;, 8888);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Untuk menangani `IOException` yg dapat terjadi dalam pembukaan socket, kode di atas dapat diubah menjadi seperti berikut.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
Socket socket = null;
try {
  socket = new Socket(&quot;192.168.1.1&quot;, 8888);
} catch (IOException e) {
  e.printStackTrace();
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Perlu diketahui bahwa port nomor 0 hingga 1023 telah di-*reserved*, digunakan sebagai port untuk layanan-layanan standar seperti port 80 untuk HTTP dan port 21 untuk FTP. Sehingga, kita gunakan nomor port &gt; 1023 dalam pembuatan socket.

### Membuka Socket di Server {#membuka-socket-di-server}

Di sisi server, kita akan perlu menggunakan `ServerSocket` untuk membuka socket yg akan menerima request dari client. Misalkan, server akan mendengarkan *(listen to)* port nomor 8888, maka kita gunakan kode berikut.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
ServerSocket serverSocket = null;
try {
  serverSocket = new ServerSocket(8888);
} catch (IOException e) {
  e.printStackTrace();
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Untuk meng-*accept* (menerima) permintaan dari client, kita perlu membuat sebuah `Socket` yg khusus akan digunakan untuk melayani permintaan dari client tertentu. Kode untuk ini dapat disisipkan ke kode di atas sehingga menjadi seperti berikut.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
ServerSocket serverSocket = null;
try {
  serverSocket = new ServerSocket(8888);
  Socket socket = serverSocket.accept();
} catch (IOException e) {
  e.printStackTrace();
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Membuat Input Stream {#membuat-input-stream}

Agar client dapat **menerima** respon dari server, kita dapat menggunakan `DataInputStream`.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
DataInputStream input;
try {
  input = new DataInputStream(socket.getInputStream());
} catch (IOException e) {
  System.out.println(e);
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Begitu pula di sisi server, `DataInputStream` juga dapat digunakan untuk **menerima** request dari client.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
DataInputStream input;
try {
  input = new DataInputStream(serverSocket.getInputStream());
} catch (IOException e) {
  System.out.println(e);
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Membuat Output Stream {#membuat-output-stream}

`DataOutputStream` atau `PrintStream` dapat kita gunakan untuk **mengirim** request dari client ke server.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
PrintStream output;
try {
  output = new PrintStream(socket.getOutputStream());
} catch (IOException e) {
  System.out.println(e);
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
DataOutputStream output;
try {
  output = new DataOutputStream(socket.getOutputStream());
} catch (IOException e) {
  System.out.println(e);
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Di server, kita juga dapat menggunakan `DataOutputStream` dan `PrintStream` untuk **mengirim** informasi ke client.

Contoh Pengaplikasian Pemrograman Socket {#contoh-pengaplikasian-pemrograman-socket}
----------------------------------------

Contoh pengaplikasian dari materi pemrograman socket menggunakan Java ini dapat dilihat di materi belajar [Belajar Pemrograman Socket Client – Server Menggunakan Android dan Java]. Contoh yang dijelaskan pada materi tersebut sangatlah sederhana. Dalam materi tersebut kita belajar membuat sebuah aplikasi Android sebagai client dan sebuah aplikasi *console* sebagai server. User mengisikan nama dan alamat socket server. Kemudian, saat tombol `Panggil Saya` ditekan, server akan memberikan balasan berupa text dengan format `Hai, Nama!`.

Demikian materi belajar ini. Sebenarnya, masih banyak yang dapat kita pelajari tentang pemrograman socket. Materi ini dimaksudkan untuk memberikan gambaran umumnya. Materi-materi belajar tentang pemrograman jaringan di website ini, akan dimasukkan ke dalam kategori [Pemrograman Jaringan]. Anda juga dapat menemukannya di [Google] dengan kata kunci `pemrograman jaringan`. Selamat mengeksplorasi lebih lanjut!

------------------------------------------------------------------------

Referensi: {#referensi}
----------

-   Penjelasan dan gambar tentang socket: [What is a Socket?]
-   Penjelasan tentang pemrograman socket di Java: [Sockets programming
    in Java: A tutorial]

[example.com]: http://example.com
[Belajar Pemrograman Socket Client – Server Menggunakan Android dan Java]: https://belajarpemrograman.org/belajar-pemrograman-socket-client-server-menggunakan-android-dan-java/
[Pemrograman Jaringan]: /category/pemrograman-jaringan/
[Google]: https://www.google.com/search?q=pemrograman+jaringan
[What is a Socket?]: https://docs.oracle.com/javase/tutorial/networking/sockets/definition.html
[Sockets programming in Java: A tutorial]: http://www.javaworld.com/article/2077322/core-java/core-java-sockets-programming-in-java-a-tutorial.html

*[HTTP]: Hypertext Transfer Protocol
*[FTP]: File Transfer Protocol
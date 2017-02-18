---
ID: 39
post_title: 'Belajar Pemrograman Bash Shell di Linux 1: Pengenalan'
author: Muhammad Ikhsan
post_date: 2016-11-07 07:23:15
post_excerpt: |
  Dalam tulisan ini Anda akan mengenal pemrograman bash shell di Linux. Dimulai dengan pengertian bash, memeriksa shell yang aktif sebagai langkah persiapan sebelum memulai pemrograman bash, dan akhirnya Anda akan membuat dua <em>bash script</em> sederhana dan menjalankannya.
  <h2>Apa Itu bash?</h2>
  Singkatnya, <code>bash</code> merupakan sebuah program komputer seperti halnya program-program lain pada komputer, namun bash didesain agar Anda dapat berkomunikasi dengannya melalui perintah yang Anda berikan dan respon yang Anda terima.
  
  Setiap program di komputer memiliki kemampuan untuk dapat mengerjakan tugas-tugas spesifik yang membantu memudahkan pekerjaan <em>user</em>, antara lain memutar lagu, mengakses website, melakukan penghitungan, dan lain sebagainya. Akan tetapi, bash tidak melakukan tugas-tugas tersebut. Bash berperan untuk menerima perintah dari Anda sebagai <em>user</em> dan mengerjakan perintah tersebut. Sehingga, agar Anda dapat memberikan perintah yang dapat dimengerti oleh bash dengan baik, diciptakanlah bahasa untuk komunikasi tersebut. Bahasa itulah yang disebut bahasa bash shell.
  
  <em>Bash (Bourne Again shell)</em> hanya merupakan salah satu dari beberapa program yang bertindak untuk menerima perintah dari <em>user</em> untuk berinteraksi dengan program lain. Program seperti ini dikenal sebagai program <strong><em>shell</em></strong>. Beberapa program shell yang terkemuka selain bash antarai lain C shell (<code>csh</code>), Bourne shell (<code>sh</code>), Korn shell (<code>ksh</code>), dan Zshell (<code>zsh</code>). Masing-masing shell memiliki bahasa yang berbeda, meskipun dijumpai banyak kesamaan perintah-perintah yang digunakan. Perlu diingat bahwa artikel ini akan membahas mengenai pemrograman bash shell, sehingga pastikan bahwa Anda mengeksekusi kode bash shell pada bash shell, bukan shell yang lain.
layout: post
permalink: >
  http://belajarpemrograman.org/belajar-pemrograman-bash-shell-di-linux-1-pengenalan/
published: true
---
Dalam tulisan ini Anda akan mengenal pemrograman bash shell di Linux. Dimulai dengan pengertian bash, memeriksa shell yang aktif sebagai langkah persiapan sebelum memulai pemrograman bash, dan akhirnya Anda akan membuat dua <em>bash script</em> sederhana dan menjalankannya.
<h2>Apa Itu bash?</h2>
Singkatnya, <code>bash</code> merupakan sebuah program komputer seperti halnya program-program lain pada komputer, namun bash didesain agar Anda dapat berkomunikasi dengannya melalui perintah yang Anda berikan dan respon yang Anda terima.

Setiap program di komputer memiliki kemampuan untuk dapat mengerjakan tugas-tugas spesifik yang membantu memudahkan pekerjaan <em>user</em>, antara lain memutar lagu, mengakses website, melakukan penghitungan, dan lain sebagainya. Akan tetapi, bash tidak melakukan tugas-tugas tersebut. Bash berperan untuk menerima perintah dari Anda sebagai <em>user</em> dan mengerjakan perintah tersebut. Sehingga, agar Anda dapat memberikan perintah yang dapat dimengerti oleh bash dengan baik, diciptakanlah bahasa untuk komunikasi tersebut. Bahasa itulah yang disebut bahasa bash shell.

<em>Bash (Bourne Again shell)</em> hanya merupakan salah satu dari beberapa program yang bertindak untuk menerima perintah dari <em>user</em> untuk berinteraksi dengan program lain. Program seperti ini dikenal sebagai program <strong><em>shell</em></strong>. Beberapa program shell yang terkemuka selain bash antarai lain C shell (<code>csh</code>), Bourne shell (<code>sh</code>), Korn shell (<code>ksh</code>), dan Zshell (<code>zsh</code>). Masing-masing shell memiliki bahasa yang berbeda, meskipun dijumpai banyak kesamaan perintah-perintah yang digunakan. Perlu diingat bahwa artikel ini akan membahas mengenai pemrograman bash shell, sehingga pastikan bahwa Anda mengeksekusi kode bash shell pada bash shell, bukan shell yang lain.
<h2>Memeriksa Shell Aktif</h2>
Untuk memastikan bahwa Anda sedang menggunakan bash, coba jalankan perintah berikut:
<pre>$ echo "$BASH_VERSION"
4.3.46(1)-release</pre>
Jika Anda tidak memperoleh output apa-apa atau memperoleh peringatan undefined variable, maka kemungkinkan Anda sedang tidak menggunakan bash. Anda dapat menjalankan bash dengan memanggil perintah <code>bash</code>.

Perintah <code>echo</code> yang digunakan di atas merupakan salah satu perintah bawaan bash yang bertugas untuk menampilkan informasi ke standard output, yang defaultnya adalah monitor. <code>$BASH_VERSION</code> merupakan sebuah variabel internal bash yang menunjukkan informasi mengenai versi bash.

Cara lain untuk memeriksa shell yang sedang aktif, Anda dapat menjalankan perintah berikut:
<pre>$ echo $0
bash</pre>
<code>$0</code> akan memberikan nilai balik berupa nama dari proses yang sedang dijalankan. Jika dijalankan melalui shell, maka akan berisi nama shell yang sedang aktif, pada kasus ini bash. Dan jika digunakan di shell script, maka berisi nama script yang sedang dijalankan.
<h2>Membuat Shell Script</h2>
<h3>Contoh 1</h3>
Buat sebuah file dengan nama <code>hello</code>. Anda dapat menggunakan editor apa saja yang Anda kehendaki, <code>vi</code>, <code>vim</code>, <code>emacs</code>, <code>nano</code>, <code>gedit</code>, atau yang lainnya. Kemudian ketikkan script berikut:

https://gist.github.com/alwayzmile/0138d8fb3f706354590c06af2e21440a#file-hello

Simpan file, kemudian rubah hak akses file tersebut agar dapat dieksekusi:
<pre>$ chmod 755 hello</pre>
Jalankan shell script pertama kita:
<pre>$ ./hello
Hello World!
Anda sedang berada di direktori /home/user/Documents/Writing/Code/bash</pre>
<h4><strong>Catatan untuk script <code>hello</code>:</strong></h4>
<ul>
 	<li><code>#!/bin/bash</code> menyatakan bahwa script tersebut harus dijalankan di bash shell. <code>/bin/bash</code> merupakan lokasi dari bash interpreter yang akan menerjemahkan dan menjalankan bash script. Anda dapat mendapatkan lokasi ini dengan menjalankan perintah:
<pre>$ which bash
/bin/bash</pre>
</li>
 	<li><code>$PWD</code> merupakan sebuah variabel yang sudah didefinisikan oleh bash. Dengan meletakkan variabel dalam tanda petik dua ("), bash akan mengganti pernyataan variabel tersebut dengan nilainya, kemudian barulah perintah (dalam kasus ini perintah <code>echo</code>) dijalankan. Nilai variabel <code>$PWD</code> adalah path direktori aktif, layaknya output dari perintah <code>pwd</code>.</li>
</ul>
<h3>Contoh 2</h3>
Berikut merupakan sebuah contoh lain:

https://gist.github.com/alwayzmile/0138d8fb3f706354590c06af2e21440a#file-tampilkaninfo

Simpan file tersebut dengan nama <code>tampilkaninfo</code>, kemudian rubah hak akses file agar dapat dieksekusi, dan jalankan.
<pre>$ chmod 755 tampilkaninfo
$ ./tampilkaninfo
Halo user!
Anda sedang menjalankan file bash script './tampilkaninfo'
Hari ini tanggal 06 November 2016
Anda sedang berada di lokasi /home/user/Documents/Writing/Code/bash
Berikut merupakan beberapa file yang terdapat pada direktori aktif:
hello  tampilkaninfo</pre>
<h4>Catatan untuk script <code>tampilkaninfo</code>:</h4>
<ul>
 	<li>Baris yang diawali dengan <code>#</code>, selain baris <code>#!/bin/bash</code>, merupakan komentar dan akan diabaikan oleh shell</li>
 	<li>Variabel <code>$USER</code> menyimpan nama <em>user</em>. <code>$USER</code> merupakan salah satu variabel lingkungan <em>(environment variable)</em> yang telah didefinisikan nilainya oleh sistem, dan perubahan terhadap nilai variabel lingkungan mempengaruhi kerja sistem.</li>
 	<li>Telah dijelaskan sebelumnya, jika variabel <code>$0</code> digunakan di shell script, maka akan memiliki nilai nama file script tersebut.</li>
 	<li>Dengan menggunakan argumen <code>-n</code> pada <code>echo</code>, teks tidak diakhiri dengan <em>newline</em> (ganti baris). Sehingga tulisan <code>Hari ini tanggal </code> dan hasil pemanggilan perintah <code>date +"%d %B %Y"</code> (untuk menampilkan tanggal lokal saat script dijalankan dengan format tanggal "tanggal namabulan tahun") dapat ditampilkan dalam baris yang sama.</li>
 	<li>Tulisan <code>Anda sedang berada di lokasi </code> dengan hasil pemanggilan perintah <code>pwd</code> juga dapat ditampilkan pada baris yang sama dengan meniadakan newline pada akhir output pemanggilan echo.</li>
</ul>
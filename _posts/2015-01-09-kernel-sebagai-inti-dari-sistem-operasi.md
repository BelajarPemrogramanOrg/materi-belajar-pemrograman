---
ID: 118
post_title: Kernel Sebagai Inti dari Sistem Operasi
author: Muhammad Ikhsan
post_date: 2015-01-09 00:26:56
post_excerpt: |
  Istilah kernel biasanya mengacu pada pengertian sistem operasi sebagai perangkat lunak yang mengelola dan mengalokasikan sumber daya komputer (seperti CPU, RAM, dan perangkat lainnya). Meskipun memungkinkan untuk menjalankan sebuah program di mesin komputer tanpa adanya kernel, namun dengan adanya kernel akan sangat memudahkan bagi programmer dengan telah ditanganinya pengelolaan dan pengalokasian sumber daya komputer oleh kernel.
  
  Kernel Linux biasanya berada pada lokasi /boot/vmlinuz atau yang menyerupai lokasi tersebut. Pada generasi awal UNIX, file kernel <i>executable </i>tersebut dinamai <i>unix.</i> Kemudian setelah UNIX mengimplementasikan virtual memory, nama kernel tersebut berubah menjadi <i>vmunix.</i> Sedangkan pada Linux, nama kernel menjadi sebagaimana nama sistemnya, <i>linux</i>, dengan mengganti huruf <i>x </i>dengan huruf <i>z</i>, sehingga menjadi <i>vmlinuz</i>.
layout: post
permalink: >
  https://belajarpemrograman.org/kernel-sebagai-inti-dari-sistem-operasi/
published: true
---
Istilah kernel biasanya mengacu pada pengertian sistem operasi sebagai perangkat lunak yang mengelola dan mengalokasikan sumber daya komputer (seperti CPU, RAM, dan perangkat lainnya). Meskipun memungkinkan untuk menjalankan sebuah program di mesin komputer tanpa adanya kernel, namun dengan adanya kernel akan sangat memudahkan bagi programmer dengan telah ditanganinya pengelolaan dan pengalokasian sumber daya komputer oleh kernel.

Kernel Linux biasanya berada pada lokasi /boot/vmlinuz atau yang menyerupai lokasi tersebut. Pada generasi awal UNIX, file kernel <i>executable </i>tersebut dinamai <i>unix.</i> Kemudian setelah UNIX mengimplementasikan virtual memory, nama kernel tersebut berubah menjadi <i>vmunix.</i> Sedangkan pada Linux, nama kernel menjadi sebagaimana nama sistemnya, <i>linux</i>, dengan mengganti huruf <i>x </i>dengan huruf <i>z</i>, sehingga menjadi <i>vmlinuz</i>.
<h2><b>Tugas-Tugas Kernel</b></h2>
<ul>
 	<li>
<h3>Process scheduling (penjadwalan proses)</h3>
Sebuah komputer memiliki satu atau lebih Central Processing Unit (CPU) yang mengeksekusi perintah-perintah dari program. Sebuah kernel terus memantau kondisi dari setiap proses. Beberapa proses dapat bertempat di memori komputer secara serempak dan masing-masing proses dapat memperoleh porsi penggunaan di CPU. Keputusan yang menentukan proses mana sajakah yang akan menerima bagian penggunaan di CPU dan untuk berapa lamakah bagian penggunaan itu disediakan untuk proses-proses tersebut diatur oleh <i>process scheduler</i> (bukan diatur oleh proses-proses itu sendiri)<i>.</i></li>
 	<li>
<h3>Manajemen memori</h3>
Kernel mengecek setiap <i>request</i> untuk dapat ditempatkan pada memori, jika memungkinkan, maka kernel mengalokasikan sebagian dari memori yang belum digunakan. Dalam lingkungan<i> </i>sistem operasi yang mendukung <i>multiuser</i>, kernel membuat sebuah tabel yang terus memantau pengguna manakah yang menggunakan bagian memori tertentu pada memori. Setiap proses terpisah satu sama lainnya. Sehingga sebuah proses tidak dapat mengusik proses lainnya.</li>
 	<li>
<h3>Menyediakan sistem file</h3>
Kernel menyediakan sistem file pada media penyimpanan yang mengijinkan pembuatan file, pemanggilan file, perubahan file, penghapusan file, dll.</li>
 	<li>
<h3>Menjalankan dan menghentikan proses</h3>
Kernel dapat memuat sebuah program ke dalam memori dan kemudian menyediakan sumber daya (seperti CPU, memori, dan akses ke file-file) yang dibutuhkan oleh program untuk dapat berjalan. Keadaan ketika program dijalankan tersebut disebut <i>proses</i>. Ketika sebuah proses telah selesai dijalankan, kernel memastikan bahwa semua sumberdaya yang digunakan oleh proses tersebut telah dikembalikan kondisinya seperti sebelum digunakan agar dapat digunakan oleh proses yang lain.</li>
 	<li>
<h3>Akses ke perangkat-perangkat input/output<i>
</i></h3>
Dengan dihubungkannya berbagai perangkat seperti mouse, monitor, keyboard, printer, dan berbagai perangkat lainnya memungkinkan sebuah komputer untuk dapat berkomunikasi dengan lingkungan luar (baik dengan menerima input, maupun memberikan output). Kernel menyediakan program dengan antarmuka yang memudahkan akses antara komputer dengan dengan perangkat-perangkat tersebut.</li>
 	<li>
<h3>Networking</h3>
Kernel dapat mendukung pengiriman dan penerimaan pesan melalui jaringan berupa paket-paket jaringan.</li>
 	<li>
<h3>Menyediakan Application Programming Interface untuk pemanggilan system call</h3>
Sebuah proses dapat meminta agar kernel mengerjakan tugas-tugas tertentu. Proses-proses tersebut dapat menyampaikan permintaannya dengan menjalankan perintah-perintah yang dikenal sebagai <i>system call.</i></li>
</ul>
Pada sistem operasi yang mendukung adanya <i>multiuser</i>, sistem operasi menyediakan abstraksi yang dikenal sebagai <i>virtual private computer. </i>Setiap pengguna dapat log in ke sebuah sistem dan mengerjakan berbagai tugas yang terpisah dari pengguna yang lain. Sebagai contoh, setiap pengguna memiliki direktori kerja (<i>home directory</i>)<i> </i>masing-masing. Selanjutnya, ketika beberapa pengguna menjalankan program secara bersamaan, setiap pengguna akan memiliki bagian CPU masing-masing. Kernel mengatasi berbagai perselisihan yang dapat terjadi dalam pengaksesan sumber daya perangkat keras, sehingga hal tersebut berada di luar pengetahuan pengguna.
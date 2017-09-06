---
ID: 118
post_title: Kernel Sebagai Inti dari Sistem Operasi
author: Muhammad Ikhsan
post_excerpt: |
  Istilah kernel biasanya mengacu pada pengertian sistem operasi sebagai perangkat lunak yang mengelola dan mengalokasikan sumber daya komputer (seperti CPU, RAM, dan perangkat lainnya). Meskipun memungkinkan untuk menjalankan sebuah program di mesin komputer tanpa adanya kernel, namun dengan adanya kernel akan sangat memudahkan bagi programmer dengan telah ditanganinya pengelolaan dan pengalokasian sumber daya komputer oleh kernel.
  
  Kernel Linux biasanya berada pada lokasi /boot/vmlinuz atau yang menyerupai lokasi tersebut. Pada generasi awal UNIX, file kernel <i>executable </i>tersebut dinamai <i>unix.</i> Kemudian setelah UNIX mengimplementasikan virtual memory, nama kernel tersebut berubah menjadi <i>vmunix.</i> Sedangkan pada Linux, nama kernel menjadi sebagaimana nama sistemnya, <i>linux</i>, dengan mengganti huruf <i>x </i>dengan huruf <i>z</i>, sehingga menjadi <i>vmlinuz</i>.
layout: post
permalink: >
  http://belajarpemrograman.org/kernel-sebagai-inti-dari-sistem-operasi/
published: true
post_date: 2015-01-09 00:26:56
---
Definisi Kernel {#definisi-kernel}
------------------

Istilah kernel biasanya mengacu pada pengertian sistem operasi sebagai perangkat lunak yang mengelola dan mengalokasikan sumber daya komputer (seperti CPU, RAM, dan perangkat lainnya). Meskipun memungkinkan untuk menjalankan sebuah program di mesin komputer tanpa adanya kernel, namun dengan adanya kernel akan sangat memudahkan bagi programmer dengan telah ditanganinya pengelolaan dan pengalokasian sumber daya komputer oleh kernel. 

Kernel Linux biasanya berada pada lokasi /boot/vmlinuz atau yang menyerupai lokasi tersebut. Pada generasi awal UNIX, file kernel *executable* tersebut dinamai *unix.* Kemudian setelah UNIX mengimplementasikan virtual memory, nama kernel tersebut berubah menjadi *vmunix.* Sedangkan pada Linux, nama kernel menjadi sebagaimana nama sistemnya, *linux*, dengan mengganti huruf *x* dengan huruf *z*, sehingga menjadi *vmlinuz*.

Tugas-Tugas Kernel {#tugas-tugas-kernel}
------------------

-   Process scheduling (penjadwalan proses) {#process-scheduling-penjadwalan-proses}
    Sebuah komputer memiliki satu atau lebih Central Processing Unit (CPU) yang mengeksekusi perintah-perintah dari program. Sebuah kernel terus memantau kondisi dari setiap proses. Beberapa proses dapat bertempat di memori komputer secara serempak dan masing-masing proses dapat memperoleh porsi penggunaan di CPU. Keputusan yang menentukan proses mana sajakah yang akan menerima bagian penggunaan di CPU dan untuk berapa lamakah bagian penggunaan itu disediakan untuk proses-proses tersebut diatur oleh *process scheduler* (bukan diatur oleh proses-proses itu sendiri)*.*

-   Manajemen memori {#manajemen-memori}
    Kernel mengecek setiap *request* untuk dapat ditempatkan pada memori, jika memungkinkan, maka kernel mengalokasikan sebagian dari memori yang belum digunakan. Dalam lingkungan ** sistem operasi yang mendukung *multiuser*, kernel membuat sebuah tabel yang terus memantau pengguna manakah yang menggunakan bagian memori tertentu pada memori. Setiap proses terpisah satu sama lainnya. Sehingga sebuah proses tidak dapat mengusik proses lainnya.

-   Menyediakan sistem file {#menyediakan-sistem-file}
    Kernel menyediakan sistem file pada media penyimpanan yang mengijinkan pembuatan file, pemanggilan file, perubahan file, penghapusan file, dll.

-   Menjalankan dan menghentikan proses {#menjalankan-dan-menghentikan-proses}
    Kernel dapat memuat sebuah program ke dalam memori dan kemudian menyediakan sumber daya (seperti CPU, memori, dan akses ke file-file) yang dibutuhkan oleh program untuk dapat berjalan. Keadaan ketika program dijalankan tersebut disebut *proses*. Ketika sebuah proses telah selesai dijalankan, kernel memastikan bahwa semua sumberdaya yang digunakan oleh proses tersebut telah dikembalikan kondisinya seperti sebelum digunakan agar dapat digunakan oleh proses yang lain.

-   Akses ke perangkat-perangkat input/output ** {#akses-ke-perangkat-perangkat-inputoutput}
    Dengan dihubungkannya berbagai perangkat seperti mouse, monitor, keyboard, printer, dan berbagai perangkat lainnya memungkinkan sebuah komputer untuk dapat berkomunikasi dengan lingkungan luar (baik dengan menerima input, maupun memberikan output). Kernel menyediakan program dengan antarmuka yang memudahkan akses antara komputer dengan dengan perangkat-perangkat tersebut.

-   Networking {#networking}
    Kernel dapat mendukung pengiriman dan penerimaan pesan melalui jaringan berupa paket-paket jaringan.

-   Menyediakan Application Programming Interface untuk pemanggilan system call {#menyediakan-application-programming-interface-untuk-pemanggilan-system-call}
    Sebuah proses dapat meminta agar kernel mengerjakan tugas-tugas tertentu. Proses-proses tersebut dapat menyampaikan permintaannya dengan menjalankan perintah-perintah yang dikenal sebagai *system call.* 

Pada sistem operasi yang mendukung adanya *multiuser*, sistem operasi menyediakan abstraksi yang dikenal sebagai *virtual private computer.* Setiap pengguna dapat log in ke sebuah sistem dan mengerjakan berbagai tugas yang terpisah dari pengguna yang lain. Sebagai contoh, setiap pengguna memiliki direktori kerja (*home directory*) ** masing-masing. Selanjutnya, ketika beberapa pengguna menjalankan program secara bersamaan, setiap pengguna akan memiliki bagian CPU masing-masing. Kernel mengatasi berbagai perselisihan yang dapat terjadi dalam pengaksesan sumber daya perangkat keras, sehingga hal tersebut berada di luar pengetahuan pengguna.
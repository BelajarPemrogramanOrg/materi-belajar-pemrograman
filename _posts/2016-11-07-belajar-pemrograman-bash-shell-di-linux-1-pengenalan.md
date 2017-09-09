---
ID: 39
post_title: 'Belajar Pemrograman Bash Shell di Linux 1: Pengenalan'
author: Muhammad Ikhsan
post_excerpt: 'Dalam materi belajar ini Anda akan mengenal pemrograman bash shell di Linux. Dimulai dengan pengertian bash, memeriksa shell yang aktif sebagai langkah persiapan sebelum memulai pemrograman bash, dan akhirnya Anda akan membuat dua <em>bash script</em> sederhana dan menjalankannya.'
layout: post
permalink: >
  http://belajarpemrograman.org/belajar-pemrograman-bash-shell-di-linux-1-pengenalan/
published: true
post_date: 2016-11-07 07:23:15
---
Dalam materi belajar ini Anda akan mengenal pemrograman bash shell di Linux. Dimulai dengan pengertian bash, memeriksa shell yang aktif sebagai langkah persiapan sebelum memulai pemrograman bash, dan akhirnya Anda akan membuat dua *bash script* sederhana dan menjalankannya.

Apa Itu bash? {#apa-itu-bash}
-------------

Singkatnya, `bash` merupakan sebuah program komputer seperti halnya program-program lain pada komputer, namun bash didesain agar Anda dapat berkomunikasi dengannya melalui perintah yang Anda berikan dan respon yang Anda terima.

Setiap program di komputer memiliki kemampuan untuk dapat mengerjakan tugas-tugas spesifik yang membantu memudahkan pekerjaan *user*, antara lain memutar lagu, mengakses website, melakukan penghitungan, dan lain sebagainya. Akan tetapi, bash tidak melakukan tugas-tugas tersebut. Bash berperan untuk menerima perintah dari Anda sebagai *user* dan mengerjakan perintah tersebut. Sehingga, agar Anda dapat memberikan perintah yang dapat dimengerti oleh bash dengan baik, diciptakanlah bahasa untuk komunikasi tersebut. Bahasa itulah yang disebut bahasa bash shell.

*Bash (Bourne Again shell)* hanya merupakan salah satu dari beberapa program yang bertindak untuk menerima perintah dari *user* untuk berinteraksi dengan program lain. Program seperti ini dikenal sebagai program ***shell***. Beberapa program shell yang terkemuka selain bash antarai lain C shell (`csh`), Bourne shell (`sh`), Korn shell (`ksh`), dan Zshell (`zsh`). Masing-masing shell memiliki bahasa yang berbeda, meskipun dijumpai banyak kesamaan perintah-perintah yang digunakan. Perlu diingat bahwa artikel ini akan membahas mengenai pemrograman bash shell, sehingga pastikan bahwa Anda mengeksekusi kode bash shell pada bash shell, bukan shell yang lain.

Memeriksa Shell Aktif {#memeriksa-shell-aktif}
---------------------

Untuk memastikan bahwa Anda sedang menggunakan bash, coba jalankan perintah berikut:

```
$ echo &quot;$BASH_VERSION&quot;
4.3.46(1)-release
```

Jika Anda tidak memperoleh output apa-apa atau memperoleh peringatan undefined variable, maka kemungkinkan Anda sedang tidak menggunakan bash. Anda dapat menjalankan bash dengan memanggil perintah `bash`.

Perintah <code>echo</code> yang digunakan di atas merupakan salah satu perintah bawaan bash yang bertugas untuk menampilkan informasi ke standard output, yang defaultnya adalah monitor. <code>$BASH_VERSION</code> merupakan sebuah variabel internal bash yang menunjukkan informasi mengenai versi bash.

Cara lain untuk memeriksa shell yang sedang aktif, Anda dapat menjalankan perintah berikut:

```
$ echo $0
bash
```

`$0` akan memberikan nilai balik berupa nama dari proses yang sedang dijalankan. Jika dijalankan melalui shell, maka akan berisi nama shell yang sedang aktif, pada kasus ini bash. Dan jika digunakan di shell script, maka berisi nama script yang sedang dijalankan.

Membuat Shell Script {#membuat-shell-script}
--------------------

Bash dapat dijalankan dalam 2 mode:

-   Mode Interaktif
    Anda telah menggunakan mode ini ketika menjalankan `echo $0` di atas untuk memeriksa shell yang sedang aktif. Bash shell menunggu perintah dari Anda, dan seketika setelah Anda menekan tombol <kbd>Enter</kbd>, perintah tersebut dikerjakan oleh bash. Setelah selesai, bash kembali siap menerima perintah dari Anda.
-   Mode non-interaktif
    Anda dapat menuliskan rentetan perintah dalam sebuah file *script* untuk dieksekusi oleh bash. Anda cukup menyebutkan nama file yang berisikan *script* tersebut.

Pada bagian ini kita akan belajar menggunakan mode non-interaktif, yaitu dengan membuat dan menjalankan dua bash script sederhana.

### Contoh 1 {#contoh-1}

Buat sebuah file dengan nama `hello`. Anda dapat menggunakan editor apa saja yang Anda kehendaki, `vi`, `vim`, `emacs`, `nano`, `gedit`, atau yang lainnya. Kemudian ketikkan script berikut:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-bash .line-numbers}
#!/bin/bash
echo &quot;Hello World!&quot;
echo &quot;Anda sedang berada di direktori $PWD&quot;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Simpan file, kemudian rubah hak akses file tersebut agar dapat dieksekusi:

```
$ chmod 755 hello
```

Jalankan shell script pertama kita:

```
$ ./hello
Hello World!
Anda sedang berada di direktori /home/user/Documents/Writing/Code/bash
```

#### Penjelasan untuk script `hello`: {#catatan-untuk-script-hello}

-   `#!/bin/bash` menyatakan bahwa script tersebut harus dijalankan di bash shell. `/bin/bash` merupakan lokasi dari bash interpreter yang akan menerjemahkan dan menjalankan bash script. Anda dapat mendapatkan lokasi ini dengan menjalankan perintah:

    ```
    $ which bash
    /bin/bash
    ```

-   `$PWD` merupakan sebuah variabel yang sudah didefinisikan oleh bash. Dengan meletakkan variabel dalam tanda petik dua ("), bash akan mengganti pernyataan variabel tersebut dengan nilainya, kemudian barulah perintah (dalam kasus ini perintah `echo`) dijalankan. Nilai variabel `$PWD` adalah path direktori aktif, layaknya output dari perintah `pwd`.

### Contoh 2 {#contoh-2}

Berikut merupakan sebuah contoh lain:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-bash .line-numbers}
#!/bin/bash
# Menampilkan beberapa informasi
 
# Menampilkan nama user
echo &quot;Halo $USER!&quot;
 
# Menampilkan nama file shell script yang sedang dijalankan
echo &quot;Anda sedang menjalankan file bash script &#039;$0&#039;&quot;
 
# Menampilkan tanggal lokal
echo -n &quot;Hari ini tanggal &quot;; date +&quot;%d %B %Y&quot;
 
# Menampilkan nama direktori aktif
echo -n &quot;Anda sedang berada di lokasi &quot;; pwd
 
# Menampilkan isi direktori aktif
echo &quot;Berikut merupakan beberapa file yang terdapat pada direktori aktif:&quot;;
ls
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Simpan file tersebut dengan nama `tampilkaninfo`, kemudian rubah hak
akses file agar dapat dieksekusi, dan jalankan.

```
$ chmod 755 tampilkaninfo
$ ./tampilkaninfo
Halo user!
Anda sedang menjalankan file bash script &#039;./tampilkaninfo&#039;
Hari ini tanggal 06 November 2016
Anda sedang berada di lokasi /home/user/Documents/Writing/Code/bash
Berikut merupakan beberapa file yang terdapat pada direktori aktif:
hello  tampilkaninfo
```

#### Penjelasan untuk script `tampilkaninfo`: {#catatan-untuk-script-tampilkaninfo}

-   Baris yang diawali dengan `#`, selain baris `#!/bin/bash`, merupakan komentar dan akan diabaikan oleh shell
-   Variabel `$USER` menyimpan nama *user*. `$USER` merupakan salah satu variabel lingkungan *(environment variable)* yang telah didefinisikan nilainya oleh sistem, dan perubahan terhadap nilai variabel lingkungan mempengaruhi kerja sistem.
-   Telah dijelaskan sebelumnya, jika variabel `$0` digunakan di shell script, maka akan memiliki nilai nama file script tersebut.
-   Dengan menggunakan argumen `-n` pada `echo`, teks tidak diakhiri dengan *newline* (ganti baris). Sehingga tulisan `Hari ini tanggal ` dan hasil pemanggilan perintah `date +"%d %B %Y"` (untuk menampilkan tanggal lokal saat script dijalankan dengan format tanggal “tanggal namabulan tahun”) dapat ditampilkan dalam baris yang sama.
-   Tulisan `Anda sedang berada di lokasi ` dengan hasil pemanggilan perintah `pwd` juga dapat ditampilkan pada baris yang sama dengan meniadakan newline pada akhir output pemanggilan echo.
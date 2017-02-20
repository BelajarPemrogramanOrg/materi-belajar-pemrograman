---
ID: 42
post_title: Perintah-Perintah Dasar Linux
author: Muhammad Ikhsan
post_date: 2016-11-04 21:53:59
post_excerpt: 'Dalam artikel ini akan dibahas mengenai beberapa perintah-perintah dasar Linux berikut contoh-contoh penggunaannya. Perintah-perintah dasar yang akan dibahas antara lain <code>cd</code> untuk mengganti direktori aktif, <code>pwd</code> menampilkan nama direktori aktif, <code>ls</code> untuk menampilkan isi sebuah direktori, dan lain-lain.'
layout: post
permalink: >
  https://belajarpemrograman.org/perintah-perintah-dasar-linux/
published: true
---
Dalam tulisan ini akan dibahas mengenai beberapa perintah-perintah dasar Linux berikut contoh-contoh penggunaannya.
<h2><code>cd</code> - Pindah lokasi direktori aktif <em>(change directory)</em></h2>
<ul>
 	<li>Pindah ke direktori/folder bernama Documents yang terdapat pada lokasi direktori aktif:
<pre>$ cd Documents</pre>
</li>
 	<li>Pindah ke direktori induk:
<pre>$ cd ..</pre>
</li>
 	<li>Pindah ke direktori root:
<pre>$ cd /</pre>
</li>
 	<li>Pindah ke direktori login atau <em>home directory</em> yang merupakan direktori yang pertama kali dibuka saat user login:
<pre>$ cd
$ cd ~</pre>
Anda dapat pindah direktori ke <em>home directory</em> dengan memanggil perintah <code>cd</code> dengan tanpa argumen atau dengan menggunakan <em>tilde</em> (<code>~</code>) sebagai direktori tujuan.</li>
</ul>
<h2><code>pwd</code> - Menampilkan nama direktori aktif</h2>
<pre>$ pwd
/home/user
$ cd ..
$ pwd
/home</pre>
<h2><code>ls</code> - Menampilkan isi sebuah direktori</h2>
<ul>
 	<li>Menampilkan daftar nama file dalam direktori aktif, selain file-file yang diawali dengan titik (.):
<pre>$ ls
Desktop    examples.desktop  Public
Documents  Music             Templates
Downloads  Pictures          Videos</pre>
</li>
 	<li>Menampilkan semua file termasuk file yang namanya diawali dengan titik (.):
<pre>$ ls -a
.                   .gconf           Public
..                  .gitconfig       .s
.apport-ignore.xml  .gnome2          .subversion
.bash_history       .gnome2_private  .sudo_as_admin_successful
.bash_logout        .gnupg           Templates
.bashrc             .gphoto          .thumbnails
.cache              .heroku          .thunderbird
.compiz             .ICEauthority    Videos
.composer           .local           .vim
.config             .mozilla         .viminfo
.dbus               Music            .vimrc
Desktop             .mysql_history   .vimrc:
.dmrc               .nano            .Xauthority
Documents           .netrc           .xsession-errors
Downloads           Pictures         .xsession-errors.old
examples.desktop    .profile</pre>
Dapat kita lihat bahwa file spesial <code>.</code> yang merujuk pada direktori aktif dan file <code>..</code> yang merujuk pada direktori induk juga turut ditampilkan</li>
 	<li>Menampilkan isi direktori dengan beberapa detail seperti hak akses file <em>(file permission)</em>:
<pre>$ ls -l
total 44
drwxr-xr-x 3 alwayzmile alwayzmile 4096 Okt 18 18:23 Desktop
drwxr-xr-x 4 alwayzmile alwayzmile 4096 Okt 31 20:57 Documents
drwxr-xr-x 4 alwayzmile alwayzmile 4096 Okt 27 01:17 Downloads
-rw-r--r-- 1 alwayzmile alwayzmile 8980 Agu 14 22:37 examples.desktop
drwxr-xr-x 2 alwayzmile alwayzmile 4096 Agu 14 23:18 Music
drwxr-xr-x 2 alwayzmile alwayzmile 4096 Agu 14 23:18 Pictures
drwxr-xr-x 2 alwayzmile alwayzmile 4096 Agu 14 23:18 Public
drwxr-xr-x 2 alwayzmile alwayzmile 4096 Agu 14 23:18 Templates
drwxr-xr-x 2 alwayzmile alwayzmile 4096 Agu 14 23:18 Videos</pre>
</li>
 	<li>Menampilkan isi direktori tertentu:
<pre>$ ls -l ~/Documents
total 8
drwxrwxr-x 8 alwayzmile alwayzmile 4096 Okt 30 11:33 LLL
drwxrwxr-x 2 alwayzmile alwayzmile 4096 Okt 31 20:59 Writing</pre>
Argumen-argumen lain termasuk <code>-a</code> yang telah disebutkan sebelumnya juga dapat digunakan. Untuk melihat daftar lengkap argumen-argumen lain yang dapat digunakan berikut dengan penjelasannya, gunakan perintah <code>man ls</code>.</li>
</ul>
<h2><code>cp</code> - Mengkopi file <em>(copy)</em></h2>
<ul>
 	<li>Demo mengkopi file <code>examples.desktop</code> ke file baru dengan nama <code>newexamples.desktop</code>:
<pre>$ ls
Desktop    examples.desktop  Public
Documents  Music             Templates
Downloads  Pictures          Videos
$ cp examples.desktop newexamples.desktop
$ ls
Desktop           Music                Templates
Documents         newexamples.desktop  Videos
Downloads         Pictures
examples.desktop  Public</pre>
Apabila nama file <code>newexamples.desktop</code> sudah ada, maka file tersebut akan ditimpa dengan file baru hasil kopi tanpa meminta konfirmasi terlebih dahulu</li>
 	<li>Mengkopi file dengan menampilkan konfirmasi apabila sudah ada nama file target:
<pre>$ cp -i examples.desktop newexamples.desktop
cp: overwrite 'newexamples.desktop'?</pre>
</li>
 	<li>Mengkopi file dari direktori tertentu ke direktori aktif, juga tampilkan peringatan bila nama file target sudah ada:
<pre>$ cp -i Documents/catatan.odt .</pre>
File <code>catatan.odt</code> di direktori <code>Documents</code> dikopi ke direktori aktif dengan nama file target yang sama, yaitu <code>catatan.odt</code></li>
 	<li>Mengkopi file dari direktori tertentu ke direktori aktif dengan memberikan nama file baru:
<pre>$ cp -i Documents/catatan.odt newcatatan.odt</pre>
File <code>catatan.odt</code> akan dikopi ke direktori aktif dengan nama file <code>newcatatan.odt</code></li>
 	<li>Mengkopi direktori beserta isinya:
<pre>$ cp -r Data DataHasilKopi</pre>
</li>
</ul>
<h2><code>mv</code> - Memindahkan/rename file <em>(move)</em></h2>
Proses memindahkan file dapat dilihat sebagai proses mengkopi file dari fileSumber ke fileTarget yang diikuti dengan penghapusan fileSumber.

Merename fileNamaLama menjadi fileNamaBaru dapat dilihat sebagai mengkopi file fileNamaLama ke file fileNamaBaru diikuti dengan penghapusan fileNamaLama; yang mana fileNamaLama dan fileNamaBaru berada pada lokasi yang sama.
<ul>
 	<li>Merename <code>fileNamaLama.txt</code> menjadi <code>fileNamaBaru.txt</code>:
<pre>$ mv fileNamaLama.txt fileNamaBaru.txt</pre>
</li>
 	<li>Rename direktori <code>dirLama</code> menjadi <code>dirBaru</code>:
<pre>$ mv dirLama dirBaru</pre>
</li>
 	<li>Memindahkan file dari direktori aktif ke sebuah direktori:
<pre> mv file.txt /home/user/Documents/</pre>
</li>
 	<li>Memindahkan file dari sebuah direktori ke direktori aktif:
<pre>$ mv /home/user/Documents/file.txt .</pre>
</li>
 	<li>Memindahkan file dari sebuah direktori ke direktori aktif dan memberikan nama file baru untuk file yang dipindah:
<pre>$ mv /home/user/Documents/file.txt ./fileNamaBaru.txt</pre>
</li>
 	<li>Memindahkan semua file di direktori aktif dengan ekstensi .jpg ke direktori <code>Pictures</code>:
<pre>$ mv *.jpg Pictures</pre>
</li>
 	<li>Memindahkan beberapa file ke sebuah direktori:
<pre>$ mv file1.txt file2.txt -t /home/user/Documents/</pre>
</li>
</ul>
<h2><code>rm</code> - Menghapus file/direktori <em>(remove)</em></h2>
<ul>
 	<li>Menghapus sebuah file:
<pre>$ rm file.txt</pre>
</li>
 	<li>Menghapus sebuah direktori kosong:
<pre>$ rm -d NamaDirektoriKosong</pre>
</li>
 	<li>Menghapus sebuah direktori beserta semua isinya:
<pre>$ rm -r NamaDirektori</pre>
</li>
</ul>
<h2><code>mkdir</code> - Membuat direktori baru <em>(make directories)</em></h2>
<pre>$ mkdir namaDirektori</pre>
<h2><code>cat</code> - Menampilkan isi sebuah file</h2>
Isi file akan ditampilkan pada standard output, yang mana biasanya adalah sebuah monitor
<pre>$ cat file.txt
Ini merupakan konten dari file.txt</pre>
<h2><code>ln</code> - Membuat link</h2>
Jika Anda memiliki sebuah file dengan path <code>/path/menuju/file/tujuan</code>, maka Anda dapat membuat sebuah link yang merujuk ke lokasi file tersebut dengan nama link dan lokasi link sesuai yang Anda kehendaki. Sehingga ketika link tersebut dibuka, maka sistem akan membuka file yang ditautkan dengan link tersebut, yaitu <code>/path/menuju/file/tujuan</code>. Tingkah laku link yang seperti ini mungkin mengingatkan kita pada <em>shortcut</em> di Windows.

Terdapat dua jenis link, yaitu <em>hard link</em> dan <em>symbolic link</em>.
<ul>
 	<li>Membuat link keras <em>(hard link)</em>:
<pre>ln targetLink namaLink</pre>
Sebuah blok lokasi di harddisk, tempat di mana data tersimpan, memiliki nama yang dapat dipanggil untuk mengakses data tersebut. Misalnya data tersebut merupakan sebuah file dengan nama <code>targetLink</code>. Anda dapat memberikan nama baru untuk file tersebut, misalnya <code>namaLink</code>. Nama-nama inilah yang disebut sebagai <em>hard link</em>.</li>
 	<li>Membuat link simbolik <em>(symbolic link)</em>:
<pre>ln -s targetLink namaLink</pre>
Link simbolik <code>namaLink</code> bukan merupakan nama lain dari <code>targetLink</code>, namun namaLink memiliki informasi mengenai lokasi di mana <code>targetLink</code> berada. Sehingga ketika <code>namaLink</code> dibuka, <code>namaLink</code> dapat menunjukkan lokasi <code>targetLink</code>, dan sistem dapat membuka file <code>targetLink</code> berdasarkan informasi lokasi tersebut. Akan tetapi jika file <code>targetLink</code> dipindahkan ke lokasi baru, <code>namaLink</code> tidak dapat berfungsi karena tidak dapat menemukan<code> targetLink</code> di lokasi yang diketahuinya.</li>
</ul>
---
post_title: "Menjadi Jagoan Emacs"
layout: post
published: false
---
## Pendahuluan {.no-mar-top}

Saya berniat untuk memulai belajar pemrograman Ruby. Kemudian saya mulai memikirkan editor apa yang akan dipakai. Apakah mau pakai VS Code saja, editor yang saya pakai untuk kerja, atau yang lainnya.

<button class="btn btn-danger btn-sm" data-toggle="collapse" data-target="#curhatan" style="text-transform: none">Lanjut Baca Curhatan</button>

<div id="curhatan" class="collapse" style="border-left: 1px solid #da4453; padding-left: 10px;">
Saat itu, saya sedang mencari-cari materi belajar bahasa pemrograman Ruby. Blusukan klik link ini dan itu. Hingga sampailah saya ke websitenya mas <a href="https://agung-setiawan.com/">Agung Setiawan</a>. Tiba-tiba, muncul popup yang mengiklankan bukunya yang berjudul "Vim untuk Semua". Dalam pikiran saya, "Hmm, vim.. Ya, vim.. Iya, iya, itu yang dulu aku sempat <em>struggle</em> mempelajarinya." Sesaat kemudian, "Eh, tunggu dulu. Bukan, bukan... Kalau <code>vim</code> aku sempat enjoy beberapa waktu lalu menggunakannya. Karena hanya untuk nulis-nulis dikit (kalau pas lagi pakai Linux aja), jadinya gak merasa kesulitan."

"Trus, apa ya? .." Tiba-tiba teringat, "Oh, itu <a href="https://www.gnu.org/software/emacs/">Emacs</a>!!! Saya memang sempat <em>struggle</em> membiasakan diri menggunakannya." Sebelumnya, saya juga pernah galau memikirkan editor apa yang hendak dipakai untuk bekerja. Pada saat itu, saya bekerja sebagai WordPress developer. Saya mencoba membandingkan beberapa editor satu per satu, dan akhirnya saya memilih Emacs. Tapi karena ternyata cukup memakan waktu untuk membiasakan diri menggunakannya, jadi ditunda dulu belajar Emacs-nya. Pakai editor yang biasa dipakai saja.
</div>

Keputusan untuk menggunakan Emacs saya buat setelah membaca sebuah *slide* di SlideShare oleh **Yukihiro Matsumoto**, pembuat bahasa pemrograman Ruby. *Slide*-nya berjudul [How Emacs changed my Life](https://www.slideshare.net/yukihiro_matz/how-emacs-changed-my-life). Yukihiro Matsumoto mengatakan, "Jika ada sesuatu yang tidak saya suka dari Emacs, maka saya bisa merubahnya sesuai kehendak saya." Bebas... "Hmm, menarik", pikir saya. Ada juga yang mengatakan bahwa Emacs itu seperti sebuah sistem operasi dengan wujud *text-editor*. Di Emacs, kita bisa main game, mengatur jadwal di kalender, komunikasi via email, dan tentu saja ngoding. Apapun... Yaa, kalau ada yang kurang, kita bisa tambahkan sendiri.

## Instalasi

Di Windows, Anda dapat mendownload Emacs melalui [GNU FTP Server](http://ftp.gnu.org/gnu/emacs/windows/). Cari versi yang paling baru, angkanya paling gede. Saat tulisan ini dibuat, versi terbarunya adalah `25.2`.

## Keyboard Shortcut Umum

Bekerja menggunakan Emacs banyak melibatkan penggunaan rangkaian *keyboard shortcut*. Terutama tombol <kbd>CTRL</kbd> dan <kbd>META</kbd> alias <kbd>ALT</kbd> sangat banyak dipakai. Biar gak terlalu panjang menuliskan 4 huruf `CTRL` atau `META` untuk mewakili sebuah tombol, di dunia Emacs kita menggunakan singkatan-singkatan berikut:

-   `C-` untuk tombol <kbd>CTRL</kbd>
-   `M-` untuk tombol <kbd>ALT</kbd>
-   `S-` untuk tombol <kbd>SHIFT</kbd>

Jadi, *keyboard shortcut* `C-h C-h` berarti kita harus menekan tombol <kbd>CTRL</kbd> + <kbd>h</kbd> dua kali.

| Keyboard shortcut    | Penjelasan   
| -------------------- | -------------
| `C-h C-h`            | Membuka bantuan (*help*)
| `C-g`                | Keluar

## Sumber Materi Belajar {#sumber-materi-belajar}

Berikut merupakan beberapa referensi yang digunakan untuk belajar Emacs sekaligus menulis materi belajar ini.

-   [Absolute Beginner's Guide to Emacs](http://www.jesshamrick.com/2012/09/10/absolute-beginners-guide-to-emacs/)
-   <a href="https://panthema.net/2015/0819-emacs-Beating-the-Learning-Curve-From-Zero-to-Lightspeed/emacs%20Tutorial%20-%20Beating%20the%20Learning%20Curve%20-%20From%20Zero%20to%20Lightspeed.pdf">Emacs - Beating the Learning Curve</a>

-   [GNU Emacs Manual](https://www.gnu.org/software/emacs/manual/pdf/emacs.pdf)
-   [An Introduction to Programming in Emacs Lisp](https://www.gnu.org/software/emacs/manual/pdf/eintr.pdf)
-   [Emacs for ENSIME](http://ensime.org/editors/emacs/)
-   [Mastering Emacs](https://www.masteringemacs.org/)
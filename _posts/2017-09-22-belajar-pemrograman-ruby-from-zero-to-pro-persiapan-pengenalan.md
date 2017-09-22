---
ID: 613
post_title: 'Belajar Pemrograman Ruby from Zero to Pro &#8211; Bagian 1 Persiapan &#038; Pengenalan'
author: Muhammad Ikhsan
post_excerpt: 'Bagian pertama dari seri materi belajar pemrograman Ruby: <em>from Zero to Pro</em>, yaitu persiapan dan pengenalan. Materi belajar ini memperkenalkan Anda pada bahasa pemrograman Ruby, yang mana GitHub, Airbnb, dan BukaLapak gunakan untuk website mereka. Setelah pengenalan, materi dilanjutkan dengan penginstalan Ruby dan penggunaan modul Interactive Ruby (<code>irb</code>). Dan tentu saja, karena ini bagian pertama, kita akan membuat <code>hello-world.rb</code>.'
layout: post
permalink: >
  http://belajarpemrograman.org/belajar-pemrograman-ruby-from-zero-to-pro-persiapan-pengenalan/
published: true
post_date: 2017-09-22 22:46:22
---
Pendahuluan {.no-mar-top}
-------------------------

Saya sudah beberapa kali melirik [Bahasa pemrograman Ruby](https://www.ruby-lang.org/en/). Namun, belum memiliki kesempatan untuk benar-benar membenamkan diri mempelajarinya. Ceritanya, bos saya berkata bahwa mencari programmer Ruby itu sulit. Kalau mau kerja sebagai programmer Ruby, gajinya gede. Salah satu alasannya, karena susah dicarinya. Bahkan, tadinya bos saya mencarinya *Ruby programmer*. Tapi, karena susah, akhirnya pakai PHP saja, yang sudah (sangat) banyak penggemarnya di Indonesia (termasuk saya). Setelah browsing-browsing, sepertinya apa yang disampaikan bos ada benarnya. Hmmm, jadi kepingin belajar Ruby nih...

`# Pendahuluan alias curhatan ini masih berlanjut.`
`# Anda tidak harus membaca selengkapnya untuk mulai belajar.`
`# Tapi, kalau betah, silahkan..! (Btw, ini contoh baris komen di Ruby)`

<button class="btn btn-danger btn-sm" data-toggle="collapse" data-target="#curhatan" style="text-transform: none">Lanjut Baca Curhatan</button>

<div id="curhatan" class="collapse" style="border-left: 1px solid #da4453; padding-left: 10px;">
Saya ini hitungannya suka je-Jepang-an, hal-hal yang berkaitan dengan Jepang. Saya hobi nonton anime (sekarang sudah kurang karena kesibukan), baca manga, belajar Bahasa Jepang. Bahkan saya berkeinginan untuk melanjutkan studi di Jepang. Tapi kok, saya belum pernah mencoba belajar bahasa pemrograman Ruby yang diprakarsai oleh orang Jepang,
 <strong>Yukihiro Matsumoto</strong>. <em>(Hampir saja saya menuliskannya "Yukihir<strong>a</strong> Matsumoto", keingat Yukihir<strong>a</strong> Souma dari anime <a href="https://myanimelist.net/anime/28171/Shokugeki_no_Souma">Shokugeki no Souma</a>. wkwkwk..)</em> Ya, tentu saja Ruby yang dirilis ke publik pada tahun 1995 sebagai software open source, bisa menjadi sepopuler ini juga berkat kontribusi dari banyak orang dari seluruh dunia. Termasuk orang-orang Indonesia.

Selain itu, belakangan ini, saya mendapat informasi bahwa ada kesempatan memperoleh beasiswa pelatihan programming intensif Ruby on Rails yang diadakan oleh <a href="https://www.go-jek.com/">GO-JEK</a>. Pelatihan tersebut diadakan melalui program <a href="http://kolla.education/go-scholartech-ror/">GO-SCHOLAR TECH Ruby on Rails</a> yang bekerjasama dengan <a href="http://kolla.education/">KollaEdu</a>. Apalagi ada kesempatan untuk berkarir di GO-JEK setelah selesai pelatihan. Wah,.. pingin ikutan nih. Sayangnya, saya tidak bisa ikut karena pekerjaan. Wait,.. itu tidak mengijinkan saya beralasan untuk tidak bisa belajar Ruby. 

Tambahan lagi, kabarnya pada tahun 2017 ini akan diadakan <a href="http://ruby.id/conf/2017/">RubyConf</a> pertama di Indonesia.
</div>

Saya belum seorang yg ahli di Ruby. Jadi, jika Anda memiliki keyakinan "belajarlah dari ahlinya!", mungkin tulisan ini tidak tepat untuk Anda. <strong>Namun, jika Anda tidak keberatan belajar Ruby bersama saya, dari nol hingga menjadi pro, mari kita mulai!</strong>

Sumber Materi Belajar
---------------------

Karena saya juga masih belajar, jadi saya perlu mencari sumber materi belajar yang akan digunakan. Di bawah ini merupakan beberapa link ke materi belajar yang akan saya gunakan. Daftar tersebut dapat bertambah dan berkurang seiring berjalannya waktu.

-   [Ruby Official Website](https://www.ruby-lang.org/)
-   [Ruby Documentation](http://ruby-doc.com)
-   [Learn Ruby the Hard Way](https://learnrubythehardway.org/book/)
-   [Jalan Pintas: Mengenal Pemrograman Ruby](http://nyan.catcyb.org/mengenal-ruby/)
-   [Belajar Ruby dan Ruby on Rails Melalui Screencast](https://www.idrails.com/)
-   [Why's (Poignant) Guide to Ruby](http://poignant.guide)

Mengenal Bahasa Pemrograman Ruby
--------------------------------

|                          |                                                                         |
| ------------------------ | ----------------------------------------------------------------------- |
| __Website__              | [www.ruby-lang.org](https://ruby-lang.org)
| __Open Source__          | Ya
| __Source Code__          | [https://github.com/ruby/ruby](https://github.com/ruby/ruby)
| __Pemrakarsa__           | Yukihiro Matsumoto
| __Tahun Pertama Keluar__ | 1995
| __Ekstensi File__        | `.rb`

Beberapa website yang dibuat menggunakan bahasa pemrograman Ruby:

-   [GitHub](http://github.com/)
-   [Airbnb](https://www.airbnb.com/)
-   [BukaLapak](https://www.bukalapak.com/)
-   [Scribd](https://www.scribd.com/)
-   [Goodreads](https://www.goodreads.com/)

Menginstal Ruby
---------------

Pertama-tama, Anda dapat mengecek apakah Ruby sudah terinstal dengan menjalankan perintah berikut di terminal.

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2"><code class="language-bash">ruby --version
ruby 2.4.1p111 (2017-03-22 revision 58053) [x86_64-linux-gnu]</code></pre>

Apabila Ruby sudah terinstal, seharusnya muncul informasi versi ruby seperti di atas (tidak perlu sama persis). Namun jika belum, muncul error `command not found` atau sejenisnya. Silahkan instal terlebih dahulu. Untuk Windows, Anda dapat gunakan [RubyInstaller](https://rubyinstaller.org/). Sedangkan untuk *platform* lain, silahkan ikuti petunjuk di [dokumentasi Ruby](https://www.ruby-lang.org/id/documentation/installation/).

Belajar Ruby Menggunakan Shell Interactive Ruby `irb`
-----------------------------------------------------

`irb` merupakan sebuah modul Ruby yang mengijinkan Anda memasukkan kode program Ruby secara interaktif. Anda dapat langsung melihat output dari kode tersebut. Sama seperti ketika Anda menggunakan console di browser, Python command line, Node.js CLI, Laravel Tinker. *Programming environment* yang seperti ini disebut sebagai __REPL (Read-Eval-Print Loop)__. 

Kenapa kok namanya REPL? Karena memang cara kerjanya program-program itu memang begitu: 

1.  __Read__ (baca) kode program yang Anda inputkan,
2.  **Eval**uate atau kerjakan kode, 
3.  __Print__ (tampilkan) hasil evaluation/pengerjaan kode ke layar,
4.  __Loop__ (ulangi) dari nomor 1, dengan menunggu kode berikutnya yang Anda inputkan

Menggunakan `irb` bisa menjadi cara yang baik untuk memulai belajar Ruby. Anda menginputkan kode program Ruby, seketika itu juga `irb` akan memberikan output dari kode tersebut. Untuk memulainya, silahkan buka aplikasi terminal di OS Anda (seperti gnome-terminal atau cmd.exe). Kemudian jalankan perintah `irb`. Interactive Ruby akan terbuka dan muncul prompt seperti `irb(main):001:0>` (tidak harus sama) di terminal.

### Contoh 1: `"Halo Ruby..!"`

Anda bisa menjalankan `"Halo Ruby..!"`, dan `irb` akan memberikan hasil evaluasi berupa string `"Halo Ruby...!"`. Seperti yang Anda lihat di bawah ini, hasil evaluasi inputan Anda ditampilkan setelah `=> `.

<pre class="interactive-ruby" data-output="2"><code class="language-ruby">"Haro Ruby..!"
=> "Halo Ruby..!"</code></pre>

### Contoh 2: Kalkulator

Anda juga bisa memperlakukan `irb` selayaknya kalkulator.

<pre class="interactive-ruby" data-output="2,4,6,8,10"><code class="language-ruby">354 * 313
=> 110802
354 - 313
=> 41
354 + 313
=> 667
10 ** 3
=> 1000
1.0 / 3.0
=> 0.3333333333333333</code></pre>

### Contoh 3: Error!

Jika terdapat kesalahan pada perintah yang Anda berikan, tentu saja Ruby juga akan memberi tahu Anda salahnya dimana dan kira-kira kenapa. Sama halnya jika Anda memberikan perintah yang tidak ia kenali.

<pre class="interactive-ruby" data-output="2-5,7-9,11-14"><code class="language-ruby">3 / 0
ZeroDivisionError: divided by 0
        from (irb):34:in `/'
        from (irb):34
        from /usr/bin/irb:11:in `&lt;main&gt;'
tuliskan "Halo.. Mau belajar Ruby ya?\n"
NoMethodError: undefined method `katakan' for main:Object
        from (irb):35
        from /usr/bin/irb:11:in `&lt;main&gt;'
5 kali tuliskan "Iya.."
SyntaxError: (irb):36: syntax error, unexpected tIDENTIFIER, expecting end-of-input
5 kali tuliskan "iya.. "
      ^
        from /usr/bin/irb:11:in `&lt;main&gt;'</code></pre>

### Contoh 4: Saling Mengerti

Meski begitu, sebenarnya kalau Anda bisa _ngertiin_ dia, dia bakal _ngertiin_ Anda balik kok..! Apapun yang Anda minta, akan dia kabulkan seketika itu juga, asalkan Anda memberikan perintah yang tepat, dapat ia pahami, dan sanggup ia kerjakan.

<pre class="interactive-ruby" data-output="2,4,5,7"><code class="language-ruby">0 / 3
=> 0
print "Halo.. Mau belajar Ruby ya?\n"
Halo.. Mau belajar Ruby ya?
=> nil
5.times { print "Iya.." }
Iya..Iya..Iya..Iya..Iya..=> 5</code></pre>

### Contoh 5: Salah Paham, Kah?

Hmmm, namun, Anda tetap harus berhati-hati dengan adanya kesalahpahaman antara Anda dan Ruby. Kesalahpahaman antar manusia saja sudah biasa, apalagi antara manusia dengan komputer yang tidak mempedulikan konteks.

-   Oke, Anda ingin meminta bantuan Ruby untuk melakukan penghitungan matematika. Kalau masalah hitung-hitungan biasa, sudah tidak diragukan lagi kehebatan komputer.

    Soal nomor 1, `27 / 3 * 45`:

    <pre class="interactive-ruby" data-output="2"><code class="language-ruby">27 / 3 * 45
    => 405</code></pre>

    Oke, berarti jawabannya `405`. Sekarang, lanjut ke nomor 2:

    <pre class="interactive-ruby" data-output="2"><code class="language-ruby">23 / 46 * 808 + 1
    => 1</code></pre>

    Loh, kok yang nomor dua gak masuk akal jawabannya? Masak, cuman `1` jawabannya? Hmm, jadi ragu-ragu. Jangan-jangan yang nomor 1 juga salah. Tapi, kok Ruby gak ngasih tahu apa-apa sih kalau misalnya ada error di kode yang dimasukkan.

    Inti masalahnya, jika penghitungan Anda melibatkan _koma-komaan_, Anda harus memberitahukannya pada Ruby. Karena <code>23 / 46 = <strong>0</strong>.5</code> dan Anda tidak meminta Ruby untuk melibatkan _koma-komaan_, jadi dia hanya mengambil `0`-nya saja. Dan tentu saja, `0 * 808 + 1 = 1`. Seolah-olah Ruby berkata, "Jadi, saya gak salah dong..!"

    Gunakan kode berikut untuk melibatkan _koma-komaan_:

    <pre class="interactive-ruby" data-output="2"><code class="language-ruby">23 / 46 * 808 + 1
    => 405.0</code></pre>

-   Awalnya, karena belum tahu banyak tentang Ruby, jadi hanya ingin ngetes. Apakah memang benar seperti ini cara menghitung persenan di Ruby. Misalnya, 10% dari 100.

    <pre class="interactive-ruby" data-output="2"><code class="language-ruby">10%(100)
    => 10</code></pre>

    Yup, benar...! Oke, kalau begitu sekarang mulai menghitung yang beneran. Ini kebetulan sedang ada diskon 10% di Tokopedia. Dihitung dulu, biar bisa kira-kira, 10% dari 4.560.000.

    <pre class="interactive-ruby" data-output="2"><code class="language-ruby">10%(4560000)
    => 10</code></pre>

    Loh, loh, loh... Kok tetap `10` sih?

    Sebenarnya Ruby tidak mengalami masalah sedikitpun dalam memahami perintah Anda. Dia betul-betul mengerti bagaimana cara menghitung `10%(4560000)`. Tapi, masalahnya, pemahaman dia terhadap perintah tersebut tidak sama dengan apa yang sebetulnya Anda maksud. Meskipun tulisannya sama, namun tulisan tersebut dimaknai sedikit berbeda oleh Ruby. Sama halnya dengan tulisan "CAT" dan "AIR". Meskipun tulisannya sama, namun maknanya dalam Bahasa Indonesia sangat berbeda dengan maknanya dalam Bahasa Inggris.

    Operator `%` dalam bahasa pemrograman Ruby, dan juga beberapa bahasa pemrograman lainnya (seperti PHP dan JavaScript), digunakan untuk menghitung modulo (sisa bagi). Bukan untuk melambangkan persen atau per seratus. `7 / 2 = 3 sisa 1`, jadi `3 % 2 = 1`. 

    Kemudian, `10 / 100 = 0 sisa 10`, jadi `10 % 100 = 10`. Selain itu, jika Anda menginginkan perkalian, Anda tidak bisa menuliskannya `10(10)`, gunakan `10 * 10`. Atau jika Anda bersikeras ingin menggunakan `(` dan `)`, silahkan gunakan `10 * (10)`. Tetap saja Anda memerlukan operator `*` untuk perkalian.

Membuat `hello-world.rb`
------------------------

Kita akan mengakhiri materi belajar Ruby bagian persiapan & pengenalan ini dengan membuat sebuah file berisikan kode Ruby. Buat file dengan nama `hello-world.rb`. Kemudian isikan kode berikut:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-ruby .line-numbers}
puts &quot;Hello World!&quot;
print &quot;Hello Ruby!\n&quot;
print &quot;Ada yang memanggil saya, \&quot;Hai, kamu..!\&quot;&quot;
print &#039; Heh?&#039;
&quot;Saya diam saja&quot;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Simpan file tersebut. Untuk menjalankan kode program Ruby di dalam sebuah file, Anda bisa jalankan perintah `ruby <nama file>` di terminal.

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2-4"><code class="language-bash">ruby hello-world.rb
Hello World!
Hello Ruby!
Ada yang memanggil saya, "Hai, kamu..!" Heh?</code></pre>

Jadi,

-   `puts` membuat baris baru secara otomatis setelah string `Hello World!`
-   `print` meminta kita menambahkan `\n` di akhir string untuk menyisipkan baris baru
-   `\` merupakan *escape character*, digunakan untuk meng-*output*-kan karakter khusus. Misalnya, `\n` untuk baris baru dan `\"` untuk meng-*output*-kan karakter `"` di antara _string literal_ `"`. Dapat dilihat pada contoh:
 <code>"..saya, \<strong style="color: blue">"</strong>Hai, kamu..!\<strong style="color: blue">"</strong> Heh?"</code>
-   Baris `"Saya diam saja"` tidak ditampilkan di layar terminal karena kita memang tidak meminta Ruby untuk melakukannya. Bukan karena Ruby mengabaikannya.

Pada kenyataannya, Anda tidak akan membuat "Hello World!" untuk pekerjaan Anda. Anda akan dituntut untuk menyelesaikan masalah nyata di kehidupan dengan membuat program. Oleh karenanya, masih banyak yang harus kita pelajari.

Terima kasih, semoga bermanfaat dan sampai jumpa di materi belajar pemrograman Ruby bagian berikutnya..!

&nbsp;

--------------------------------------------------------

*Gambar diambil dari [udemy](https://www.udemy.com/learn-ruby-programming-the-easy-way-lite/)*
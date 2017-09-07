---
ID: 123
post_title: >
  Mengenal Pemrograman Berorientasi Objek
  (Menggunakan PHP)
author: Muhammad Ikhsan
post_excerpt: 'Pemrograman berorientasi objek atau OOP (Object Oriented Programming) merupakan paradigma pemrograman yang <strong>memandang program sebagai kumpulan objek</strong> yang <strong>dapat menyimpan data</strong> dan <strong>dapat mengerjakan suatu tindakan</strong>.'
layout: post
permalink: >
  http://belajarpemrograman.org/mengenal-pemrograman-berorientasi-objek-menggunakan-php/
published: true
post_date: 2017-01-28 14:13:58
---
Pemrograman berorientasi objek atau OOP (Object Oriented Programming) merupakan paradigma pemrograman yang **memandang program sebagai kumpulan objek** yang **dapat menyimpan data** dan **dapat mengerjakan suatu tindakan**.

Penjelasan {#penjelasan}
----------

Ketika Anda melakukan pendaftaran akun baru di sebuah situs jejaring sosial, misalnya Facebook, biasanya Anda diminta untuk mengisi data diri Anda, seperti nama Anda, email, password akun yang Anda kehendaki, tanggal lahir Anda, dll. Setelah mengisikan semua data yg diminta dan menyelesaikan semua proses pendaftaran, maka Anda dapat login ke akun baru tersebut dan menggunakan berbagai fitur Facebook yg telah disediakan untuk Anda sebagai pengguna. Anda dapat menambahkan teman, menerima permintaan teman, membuat status baru, me-*like* status, membuat komentar pada status, dan masih banyak lagi. Jika kita anggap setiap pengguna Facebook merupakan sebuah objek, maka kita dapat merancang karakteristik objek `pengguna Facebook` sebagai berikut:

```
Setiap pengguna Facebook:
  Memiliki data:
    Nama
    Email
    Password
    ....
  Dapat melakukan:
    Tambah teman
    Buat status baru
    Like status
    ....
```

Contoh di atas dimaksudkan untuk memberi gambaran umum mengenai *class*, *property/attribute*, dan *method/function.*

-   Sebuah kelas (*class*) menunjukkan **kerangka** atau rancangan dari objek. Kerangka `Mobil` menunjukkan bagaimana susunan setiap mobil, baik itu `Mobil A`, `Mobil B`, `Mobil C`, atau mobil-mobil lainnya yg dibuat menggunakan kerangka `mobil`.
-   *Property* digunakan untuk menggambarkan sifat-sifat dari sebuah objek.
-   *Method* menunjukkan apa saja yg dapat dikerjakan oleh objek tersebut.

Dengan menggunakan tiga istilah tersebut, contoh rancangan karakteristik pengguna Facebook di atas dapat dituliskan ulang sebagai berikut:

```
class pengguna Facebook
  property:
    Nama
    Email
    Password
    ....
  method:
    Tambah teman
    Buat status baru
    Like status
    ....
```

Contoh Kode Program {#contoh-kode-program}
-------------------

Kode di bawah ini akan melakukan hal-hal berikut:

1.  Membuat kelas `Mobil`
2.  Membuat 2 buah objek berdasarkan rancangan yg dibuat dalam kelas `Mobil`. Dua objek mobil tersebut kita beri nama `mobil_A` dan `mobil_B`
3.  Menyalakan mesin `mobil_A` dan `mobil_B`
4.  Menampilkan status mobil
5.  Mematikan mesin `mobil_A`
6.  Menampilkan kembali status mobil

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-php .line-numbers}
&lt;?php
// Membuat rancangan Mobil
class Mobil {
  // Beberapa property yg dimiliki oleh Mobil: warna, merek, kecepatan_maksimum, status_mesin (status mesin nyala atau mati)
  public $warna;
  public $merek;
  public $kecepatan_maksimum;
  public $status_mesin = &quot;mati&quot;;
&nbsp;
  // method untuk menyalakan mesin mobil
  function nyalakan_mesin() {
    // Kode untuk menyalakan mesin mobil
    // ...
    $this-&gt;status_mesin = &quot;nyala&quot;;
  }
&nbsp;
  // method untuk mematikan mesin mobil
  function matikan_mesin() {
    // Kode untuk mematikan mesin mobil
    // ...
    $this-&gt;status_mesin = &quot;mati&quot;;
  }
}
&nbsp;
// Membuat objek mobil berdasarkan rancangan yg telah dibuat dalam class Mobil
$mobil_A = new Mobil();
$mobil_B = new Mobil();
&nbsp;
// Menyalakan mesin mobil_A dan mobil_B
$mobil_A-&gt;nyalakan_mesin();
$mobil_B-&gt;nyalakan_mesin();
&nbsp;
// Menampilkan status mesin mobil_A dan mobil_B
echo &#039;#1 Status mesin mobil_A: &#039; . $mobil_A-&gt;status_mesin . &#039;&lt;br&gt;&#039;;
echo &#039;#1 Status mesin mobil_B: &#039; . $mobil_B-&gt;status_mesin . &#039;&lt;br&gt;&#039;;
&nbsp;
// Mematikan mesin mobil_A
$mobil_A-&gt;matikan_mesin();
&nbsp;
// Menampilkan kembali status mesin mobil_A dan mobil_B
echo &#039;#2 Status mesin mobil_A: &#039; . $mobil_A-&gt;status_mesin . &#039;&lt;br&gt;&#039;;
echo &#039;#2 Status mesin mobil_B: &#039; . $mobil_B-&gt;status_mesin . &#039;&lt;br&gt;&#039;;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Contoh di atas akan memberikan hasil sebagai berikut:

```
#1 Status mesin mobil_A: nyala
#1 Status mesin mobil_B: nyala
#2 Status mesin mobil_A: mati
#2 Status mesin mobil_B: nyala
```
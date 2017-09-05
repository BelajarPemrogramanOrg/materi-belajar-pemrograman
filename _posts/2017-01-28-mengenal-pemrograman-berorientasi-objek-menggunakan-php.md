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
Pemrograman berorientasi objek atau OOP (Object Oriented Programming) merupakan paradigma pemrograman yang <strong>memandang program sebagai kumpulan objek</strong> yang <strong>dapat menyimpan data</strong> dan <strong>dapat mengerjakan suatu tindakan</strong>.

<h2 id="penjelasan">Penjelasan</h2>

Ketika Anda melakukan pendaftaran akun baru di sebuah situs jejaring sosial, misalnya Facebook, biasanya Anda diminta untuk mengisi data diri Anda, seperti nama Anda, email, password akun yang Anda kehendaki, tanggal lahir Anda, dll. Setelah mengisikan semua data yg diminta dan menyelesaikan semua proses pendaftaran, maka Anda dapat login ke akun baru tersebut dan menggunakan berbagai fitur Facebook yg telah disediakan untuk Anda sebagai pengguna. Anda dapat menambahkan teman, menerima permintaan teman, membuat status baru, me-<em>like</em> status, membuat komentar pada status, dan masih banyak lagi. Jika kita anggap setiap pengguna Facebook merupakan sebuah objek, maka kita dapat merancang karakteristik objek <code>pengguna Facebook</code> sebagai berikut:

<pre><code>Setiap pengguna Facebook:
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
</code></pre>

Contoh di atas dimaksudkan untuk memberi gambaran umum mengenai <em>class</em>, <em>property/attribute</em>, dan <em>method/function.</em>

<ul>
<li>Sebuah kelas (<em>class</em>) menunjukkan <strong>kerangka</strong> atau rancangan dari objek. Kerangka <code>Mobil</code> menunjukkan bagaimana susunan setiap mobil, baik itu <code>Mobil A</code>, <code>Mobil B</code>, <code>Mobil C</code>, atau mobil-mobil lainnya yg dibuat menggunakan kerangka <code>mobil</code>.</li>
<li><em>Property</em> digunakan untuk menggambarkan sifat-sifat dari sebuah objek.</li>
<li><em>Method</em> menunjukkan apa saja yg dapat dikerjakan oleh objek tersebut.</li>
</ul>

Dengan menggunakan tiga istilah tersebut, contoh rancangan karakteristik pengguna Facebook di atas dapat dituliskan ulang sebagai berikut:

<pre><code>class pengguna Facebook
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
</code></pre>

<h2 id="contoh-kode-program">Contoh Kode Program</h2>

Kode di bawah ini akan melakukan hal-hal berikut:

<ol>
<li>Membuat kelas <code>Mobil</code></li>
<li>Membuat 2 buah objek berdasarkan rancangan yg dibuat dalam kelas <code>Mobil</code>. Dua objek mobil tersebut kita beri nama <code>mobil_A</code> dan <code>mobil_B</code></li>
<li>Menyalakan mesin <code>mobil_A</code> dan <code>mobil_B</code></li>
<li>Menampilkan status mobil</li>
<li>Mematikan mesin <code>mobil_A</code></li>
<li>Menampilkan kembali status mobil</li>
</ol>

<pre><code class="language-php line-numbers">&lt;?php
// Membuat rancangan Mobil
class Mobil {
  // Beberapa property yg dimiliki oleh Mobil: warna, merek, kecepatan_maksimum, status_mesin (status mesin nyala atau mati)
  public $warna;
  public $merek;
  public $kecepatan_maksimum;
  public $status_mesin = "mati";
 
  // method untuk menyalakan mesin mobil
  function nyalakan_mesin() {
    // Kode untuk menyalakan mesin mobil
    // ...
    $this-&gt;status_mesin = "nyala";
  }
 
  // method untuk mematikan mesin mobil
  function matikan_mesin() {
    // Kode untuk mematikan mesin mobil
    // ...
    $this-&gt;status_mesin = "mati";
  }
}
 
// Membuat objek mobil berdasarkan rancangan yg telah dibuat dalam class Mobil
$mobil_A = new Mobil();
$mobil_B = new Mobil();
 
// Menyalakan mesin mobil_A dan mobil_B
$mobil_A-&gt;nyalakan_mesin();
$mobil_B-&gt;nyalakan_mesin();
 
// Menampilkan status mesin mobil_A dan mobil_B
echo '#1 Status mesin mobil_A: ' . $mobil_A-&gt;status_mesin . '&lt;br&gt;';
echo '#1 Status mesin mobil_B: ' . $mobil_B-&gt;status_mesin . '&lt;br&gt;';
 
// Mematikan mesin mobil_A
$mobil_A-&gt;matikan_mesin();
 
// Menampilkan kembali status mesin mobil_A dan mobil_B
echo '#2 Status mesin mobil_A: ' . $mobil_A-&gt;status_mesin . '&lt;br&gt;';
echo '#2 Status mesin mobil_B: ' . $mobil_B-&gt;status_mesin . '&lt;br&gt;';
</code></pre>

Contoh di atas akan memberikan hasil sebagai berikut:

<pre><code>#1 Status mesin mobil_A: nyala
#1 Status mesin mobil_B: nyala
#2 Status mesin mobil_A: mati
#2 Status mesin mobil_B: nyala
</code></pre>
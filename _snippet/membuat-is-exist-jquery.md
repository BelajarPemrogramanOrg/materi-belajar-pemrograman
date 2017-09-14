---
ID: 427
post_title: Membuat isExist() di jQuery
author: Muhammad Ikhsan
post_excerpt: |
  Memeriksa apakah sebuah elemen DOM element exist atau tidak:
  <pre class="language-javascript line-numbers"><code>$.fn.exists = function() {
  return this.length &gt; 0
  };</code></pre>
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/jquery/membuat-is-exist-jquery/
published: true
post_date: 2017-02-02 07:55:01
---
Seringkali perlu dilakukan pengecekan terlebih dahulu apakah suatu elemen HTML *exist*, sebelum melakukan suatu tindakan tertentu yang melibatkan elemen HTML tersebut. Misalnya, kita hendak memeriksa keberadaan elemen dengan *selector* `#header .main-nav` pada sebuah dokumen HTML. Dengan menggunakan jQuery, biasanya solusi untuk masalah ini adalah dengan menggunakan kondisi `($('#header .main-nav').length > 0)`.

Kode {#kode}
----

Karena hal tersebut sering diperlukan, mari kita buat sebuah plugin jQuery sederhana untuknya.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-javascript .line-numbers}
$.fn.exists = function() { 
  return this.length &gt; 0;
};
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Penggunaan {#penggunaan}
----------

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-javascript .line-numbers}
if ($(&#039;#header .main-nav&#039;).exists()) {
  // lakukan sesuatu
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Saya sering melakukan pengecekan keberadaan elemen HTML untuk memastikan bahwa hanya script yang dibutuhkan oleh halaman saja yang dieksekusi oleh browser. Terkadang juga ada script yang dijalankan dengan asumsi bahwa suatu elemen HTML *exist*, sehingga perlu dilakukan validasi terlebih dahulu agar tidak terjadi error.
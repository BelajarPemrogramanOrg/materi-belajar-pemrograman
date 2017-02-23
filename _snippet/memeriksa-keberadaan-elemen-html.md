---
ID: 427
post_title: Memeriksa Keberadaan Elemen HTML
author: Muhammad Ikhsan
post_date: 2017-02-23 07:55:01
post_excerpt: 'Seringkali perlu dilakukan pengecekan terlebih dahulu apakah suatu elemen HTML <em>exist</em>, sebelum melakukan suatu tindakan tertentu yang melibatkan elemen HTML tersebut. Misalnya, kita hendak memeriksa keberadaan elemen dengan <em>selector</em> <code>#header .main-nav</code>.'
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/memeriksa-keberadaan-elemen-html/
published: true
---
Seringkali perlu dilakukan pengecekan terlebih dahulu apakah suatu elemen HTML <em>exist</em>, sebelum melakukan suatu tindakan tertentu yang melibatkan elemen HTML tersebut. Misalnya, kita hendak memeriksa keberadaan elemen dengan <em>selector</em> <code>#header .main-nav</code>. Dengan menggunakan jQuery, biasanya solusi untuk masalah ini adalah dengan memeriksa kondisi <code>($('#header .main-nav').length &gt; 0)</code>.
<h2>Kode</h2>
Karena hal tersebut sering diperlukan, mari kita buat sebuah plugin jQuery sederhana untuknya.
<pre><code class="language-javascript">$.fn.exists = function() { return this.length &gt; 0 };</code></pre>
<h2>Penggunaan</h2>
<pre><code class="language-javascript">if ($('#header .main-nav').exists()) {
  // lakukan sesuatu
}</code></pre>
Saya sering melakukan pengecekan keberadaan elemen HTML untuk memastikan bahwa hanya script yang dibutuhkan oleh halaman saja yang dieksekusi oleh browser. Terkadang juga ada script yang dijalankan dengan asumsi bahwa suatu elemen HTML <em>exist</em>, sehingga perlu dilakukan validasi terlebih dahulu agar tidak terjadi error.
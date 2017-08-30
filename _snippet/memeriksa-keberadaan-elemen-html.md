---
ID: 427
post_title: >
  Memeriksa Keberadaan Elemen HTML
  Menggunakan jQuery
author: Muhammad Ikhsan
post_excerpt: |
  Memeriksa apakah sebuah elemen DOM element exist atau tidak:
  <pre class="language-javascript line-numbers"><code>$.fn.exists = function() {
  return this.length &gt; 0
  };</code><div class="open-snippet">Lihat Snippet</div></pre>
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/jquery/memeriksa-keberadaan-elemen-html/
published: true
post_date: 2017-02-23 07:55:01
---
Seringkali perlu dilakukan pengecekan terlebih dahulu apakah suatu elemen HTML <em>exist</em>, sebelum melakukan suatu tindakan tertentu yang melibatkan elemen HTML tersebut. Misalnya, kita hendak memeriksa keberadaan elemen dengan <em>selector</em> <code>#header .main-nav</code> pada sebuah dokumen HTML. Dengan menggunakan jQuery, biasanya solusi untuk masalah ini adalah dengan menggunakan kondisi <code>($('#header .main-nav').length &gt; 0)</code>.
<h2>Kode</h2>
Karena hal tersebut sering diperlukan, mari kita buat sebuah plugin jQuery sederhana untuknya.
<pre><code class="language-javascript">$.fn.exists = function() { return this.length &gt; 0 };</code></pre>
<h2>Penggunaan</h2>
<pre><code class="language-javascript">if ($('#header .main-nav').exists()) {
  // lakukan sesuatu
}</code></pre>
Saya sering melakukan pengecekan keberadaan elemen HTML untuk memastikan bahwa hanya script yang dibutuhkan oleh halaman saja yang dieksekusi oleh browser. Terkadang juga ada script yang dijalankan dengan asumsi bahwa suatu elemen HTML <em>exist</em>, sehingga perlu dilakukan validasi terlebih dahulu agar tidak terjadi error.
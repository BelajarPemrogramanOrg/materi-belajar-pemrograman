---
ID: 274
post_title: >
  Mengenal HTML, CSS, JavaScript (Model
  Standar Web)
author: Muhammad Ikhsan
post_excerpt: |
  Komponen dasar untuk membangun sebuah website adalah HTML, CSS, dan JavaScript. Masing-masing memiliki peran yang berbeda.
  
  <ul>
  <li><strong>HTML</strong> HTML <em>(Hypertext Markup Language)</em> digunakan untuk membentuk struktur dan memasukkan konten dari sebuah halaman website, seperti judul halaman website, header, paragraf, form, tombol, link, dan lain sebagainya</li>
  <li><strong>CSS</strong> CSS <em>(Cascading Stylesheet)</em> digunakan untuk memberikan <em>style</em> pada halaman website sehingga website tampak menarik dan mudah digunakan.</li>
  <li><strong>JavaScript</strong> JavaScript merupakan bahasa pemrograman yg dapat dimengerti dan dieksekusi oleh browser. Dengan menggunakan JavaScript, kita dapat membuat website menjadi interaktif dan dinamis.</li>
  </ul>
layout: post
permalink: >
  http://belajarpemrograman.org/mengenal-html-css-javascript/
published: true
post_date: 2017-02-08 17:13:42
---
Saat ini, ada banyak sekali teknologi dapat digunakan untuk membuat sebuah website. Mungkin Anda pernah dengar HTML, CSS, JavaScript, jQuery, Bootstrap, AngularJS, React. Atau pernah juga mendengar Laravel, Django, Ruby on Rails,… Yaa, semua itu dapat digunakan untuk membuat sebuah website. Maaf, saya tidak berniat menakut-nakuti Anda untuk belajar *web development*. Anda tidak harus mempelajari semua teknologi itu. Anda boleh memilih, apa yang sesuai dengan kebutuhan dan pekerjaan Anda. Tapi, saya rasa Anda tidak bisa memilih soal 3 hal ini, yaitu HTML, CSS dan JavaScript.

Model Standar Website {#model-standar-website}
---------------------

Komponen dasar untuk membangun sebuah website adalah HTML, CSS, dan JavaScript. Masing-masing memiliki peran yang berbeda.

-   **HTML** HTML *(Hypertext Markup Language)* digunakan untuk membentuk struktur dan memasukkan konten dari sebuah halaman website, seperti judul halaman website, header, paragraf, form, tombol, link, dan lain sebagainya.
-   **CSS** CSS *(Cascading Stylesheet)* digunakan untuk memberikan *style* pada halaman website sehingga website tampak menarik dan mudah digunakan. Dengan menggunakan CSS, kita dapat mengatur warna teks dalam paragraf pada halaman website, atau ukuran font teks pada konten tabel, mengatur jarak antar beberapa tombol, dan lain sebagainya.
-   **JavaScript** JavaScript merupakan bahasa pemrograman yg dapat dimengerti dan dieksekusi oleh browser. Dengan menggunakan JavaScript, kita dapat membuat website menjadi interaktif dan dinamis. Misalnya, Anda dapat membuat slideshow foto, membuat popup notifikasi, atau menampilkan dan menyembunyikan sebuah blok tulisan.

Demo HTML + CSS + JavaScript {#demo-html-css-javascript}
----------------------------

Untuk melihat lebih jelas bagaimana HTML, CSS, dan JavaScript saling berhubungan satu sama lain, mari kita gunakan sebuah contoh nyata. Gambar gif di bawah ini mengilustrasikan sebuah kotak teks untuk menuliskan pesan dengan panjang maksimal 255 karakter.

<img class="aligncenter size-full wp-image-537" src="http://belajarpemrograman.org/wp-content/uploads/2017/02/demo-maksimal-jumlah-karakter-belajar-pemrograman-web.gif" alt="Ilustrasi penggunaan HTML, JavaScript, dan CSS untuk membuat kotak teks dengan batasan panjang karakter - BelajarPemrograman" width="207" height="89" />

### Penjelasan {#penjelasan}

Berikut penjelasan singkat mengenai peran HTML, CSS, dan JavaScript untuk membuatnya:

-   Struktur dan konten pokok, yaitu tulisan "Message", kotak teks, dan tulisan "255 character(s) left" dibuat dalam **HTML**.
-   **CSS** digunakan untuk men-*style* struktur konten tersebut, termasuk membuat tulisan "Message" menjadi tebal. Jarak antara garis tepi kotak teks dengan tulisan di dalamnya juga di-*style* menggunakan CSS.
-   **JavaScript** digunakan untuk menghitung dan menampilkan banyaknya sisa karakter ketika *user* menulis di kotak teks.

### Source Code {#source-code}

Berikut merupakan *source code* dari contoh di atas.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-markup .line-numbers}
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&nbsp;
&lt;head&gt;
    &lt;style class=&quot;cp-pen-styles&quot;&gt;
        .container {
            margin-top: 1em;
        }
    &lt;/style&gt;
&lt;/head&gt;
&nbsp;
&lt;body&gt;
    &lt;label for=&quot;message&quot;&gt;Message&lt;/label&gt;&lt;br&gt;
    &lt;input type=&quot;text&quot; class=&quot;form-control&quot; id=&quot;message&quot; /&gt;&lt;br&gt;
    &lt;small&gt;&lt;span id=&quot;char-count&quot;&gt;255&lt;/span&gt; character(s) left&lt;/small&gt;
    &lt;script&gt;
        var messageTextBox = document.getElementById(&quot;message&quot;);
        var charCountText = document.getElementById(&quot;char-count&quot;);
        var nCharMax = 255;
&nbsp;
        var displayNCharLeft = function (event) {
            var nCharLeft = nCharMax - messageTextBox.value.length;
            if (nCharLeft &gt;= 0) {
                charCountText.innerHTML = nCharLeft;
            } else {
                charCountText.innerHTML = 0;
                messageTextBox.value = messageTextBox.value.substr(0, nCharMax);
            }
        };
&nbsp;
        messageTextBox.addEventListener(&quot;keypress&quot;, displayNCharLeft);
        messageTextBox.addEventListener(&quot;keyup&quot;, displayNCharLeft);
    &lt;/script&gt;
&lt;/body&gt;
&nbsp;
&lt;/html&gt;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Coba sendiri di CodePen!

Di bawah ini saya *embed* kode dan hasil kode demo di atas menggunakan CodePen, sehingga Anda dapat mencoba menjalankannya langsung. Di sini, kode HTML, CSS, dan JavaScript dipisahkan dalam tab yg berbeda.

<p class="codepen" data-height="265" data-theme-id="0" data-slug-hash="qXGWEZ" data-default-tab="html,result" data-user="nakirinakuru" data-embed-version="2" data-pen-title="Maximum #Character in TextBox - Vanilla JS">See the Pen <a href="https://codepen.io/nakirinakuru/pen/qXGWEZ/">Maximum #Character in TextBox - Vanilla JS</a> by Nakiri Nakuru (<a href="https://codepen.io/nakirinakuru">@nakirinakuru</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

Tambahan: AJAX {#tambahan-ajax}
--------------

Pada awalnya, saya tidak ingin menambahkan bagian ini. Tapi karena saya rasa pengetahuan tentang AJAX ini sangatlah penting dalam teknologi website modern, sehingga saya tambahkan bagian ini.

AJAX (**A**synchronous **J**avaScript **a**nd **X**ML) merupakan suatu teknik yang menggunakan JavaScript dan XML untuk melakukan pertukaran data dengan server di balik layar. “Di balik layar”, maksudnya, Anda bisa:

-   merubah isi halaman website dengan data dari server tanpa perlu me-reload halaman website
-   meminta data ke server setelah halaman di-load
-   menerima data dari server setelah halaman di-load

Berikut merupakan beberapa contoh penggunaan AJAX:

-   Fitur chat Facebook (atau yang lainnya) dapat menampilkan adanya pesan-pesan baru tanpa perlu me-reload atau me-refresh halaman website. Berarti, ada pertukaran data antara fitur chat tersebut dengan server Facebook
-   Fitur upload data ke server dengan menampilkan informasi berapa persen bagian dari data yang sudah terupload
-   Menampilkan hasil pencarian bahkan sebelum user menekan tombol cari
-   Memberikan saran kata kunci pencarian
-   Menampilkan artikel berikutnya setelah user hendak selesai membaca sebuah artikel
-   dll.

Penutup {#penutup}
-------

Di sini, saya hanya membahas konsepnya saja. Anda dapat mempelajari AJAX setelah memiliki fondasi yang baik tentang JavaScript. Dan lebih mudah lagi, jika Anda telah mempelajari jQuery atau sebuah framework JavaScript seperti AngularJS. Selamat belajar!

## Referensi {#referensi}

-   [https://www.w3.org/community/webed/wiki/The_web_standards_model_-_HTML_CSS_and_JavaScript](https://www.w3.org/community/webed/wiki/The_web_standards_model_-_HTML_CSS_and_JavaScript)
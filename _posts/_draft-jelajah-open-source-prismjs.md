---
post_title: "Jelajah Open Source: PrismJS"
layout: post
published: false
---
Mengenal PrismJS {.no-mar-top}
------------------------------

[PrismJS](http://prismjs.com/index.html) merupakan sebuah library open source _syntax highligher_. _Syntax highlighter_ digunakan untuk memberi style (seperti warna tulisan) pada source code agar lebih mudah dan nyaman dibaca. Selain PrismJS, terdapat beberapa _syntax highlighter_ lainnya seperti [SyntaxHighlighter](http://alexgorbatchev.com/SyntaxHighlighter/) dan [highlight.js](https://highlightjs.org/). Saya membahas PrismJS karena syntax highlighter inilah yang saat ini digunakan oleh BelajarPemrograman.

|                         |                                                                         |
| ----------------------- | ----------------------------------------------------------------------- |
| __Source Code__         | [https://github.com/PrismJS/prism/](https://github.com/PrismJS/prism/)
| __Bahasa Pemrograman__  | JavaScript
| __Lisensi__             | [MIT](https://github.com/PrismJS/prism/blob/gh-pages/LICENSE)

Struktur File/Folder Source Code PrismJS
----------------------------------------

Saya tidak tahu apakah di masa depan source code PrismJS akan mengalami banyak perubahan, namun source code yang saya ulas kurang lebih berada di [rilis v1.8.1](https://github.com/PrismJS/prism/releases/tag/v1.8.1). Saya sudah mengecek [versi 1.0.0](https://github.com/PrismJS/prism/releases/tag/v1.0.0), dan struktur foldernya tidak mengalami perubahan. Perubahan yang jelas ketara, di rilis pertamanya hanya terdapat 132 file _languge definition_ di folder `/components/` (termasuk file-file _minified javascript_). Namun, di versi 1.8.1, kini sudah ada 254 file. Selain itu, jumlah plugin-nya juga bertambah, dari 9 menjadi 25.

Source code ini juga menyertakan kode untuk [website PrismJS](http://prismjs.com/index.html). Berikut merupakan penjelasan tentang beberapa file/folder source code:

-   `/components/` berisikan file-file `.js` untuk *language definition*. *Language definition* mendifinisikan setiap token yang digunakan pada bahasa pemrograman dalam regex.
    -   `prism-abap.js` merupakan file yang berisi *language definition* untuk bahasa pemrograman ABAP
    -   `prism-actionscript.js`
    -   `prism-ada.js`
    -   ...
-   `/examples/` berisikan contoh-contoh kode dalam setiap bahasa pemrograman yang didukung.
    -   `prism-abap.html`
    -   `prism-actionscript.html`
    -   `prism-ada.html`
    -   ...
-   `/img/`
-   `/plugins/` berisikan source code untuk berbagai plugin yang dapat digunakan untuk memberikan fitur ekstra pada PrismJS. Setiap plugin dimasukkan dalam folder terpisah.
    -   `autolinker/`
    -   `autoloader/`
    -   `command-line/`
    -   ...
-   `/templates/`
-   `/tests/` berisikan file-file *test case*
-   `/themes/` berisikan file-file `.css` tema PrismJS
    -   `prism-coy.css`
    -   `prism-dark.css`
    -   `prism-funky.css`
-   `/.gitignore` mengatur file/direktori apa saja yang tidak ingin kita masukkan ke repositori git. Yang menarik di sini adalah, [leaverou](http://lea.verou.me/) menggunakan nama file dengan pola `hide-*.js` untuk file-file tambahan yang tidak ingin di*commit* ke repositori.
-   `/.npmignore` mengatur file/direktori apa saja yang tidak ingin kita masukkan ke package npm. PrismJS dapat ditemukan di [repositori npm](https://www.npmjs.com/package/prismjs) dengan nama `prismjs`.
-   `/travis.yml` merupakan file [YAML](http://yaml.org/) untuk konfigurasi [Travis CI](https://travis-ci.org/). Travis CI digunakan untuk mengotomasi proses test dan build setiap kali kita commit ke repository di GitHub.

Belajar regex (Regular Expression)
----------------------------------

File-file _language definition_ `.js` dalam folder `components` berisikan regular expression untuk menentukan komponen-komponen dari source code yang akan ditampilkan oleh PrismJS. Nah, di sini kita bisa belajar banyak tentang regex. Sembari belajar, saya menemukan beberapa tool di Internet yang dapat dimanfaatkan untuk mempermudah kita dalam belajar regular expression:

-   [regular expression 101](https://regex101.com/)

    Di website ini, kita bisa memasukkan regular expression dan mendapatkan penjelasan tentangnya. Dijelaskan bagian per bagian secara detail. Kemudian, kita bisa mencoba memasukkan string untuk diuji apakah sesuai dengan regex. Kalau string cocok dengan regex, akan diberikan penjelasan tentang pencocokannya juga.

-   [Regexper](https://regexper.com/)

    Dengan menggunaka Regexper, kita dapat memperoleh grafik yang rapi dan mudah dimengerti dari regex yang kita masukkan.
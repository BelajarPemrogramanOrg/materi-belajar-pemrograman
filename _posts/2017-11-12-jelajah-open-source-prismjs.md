---
ID: 948
post_title: 'Jelajah Open Source: PrismJS'
author: Muhammad Ikhsan
post_excerpt: '<a href="http://prismjs.com/index.html">PrismJS</a> merupakan sebuah library open source <em>syntax highligher</em>. <em>Syntax highlighter</em> digunakan untuk men-<em>style</em> source code agar lebih mudah dan nyaman dibaca. Selain PrismJS, terdapat beberapa <em>syntax highlighter</em> lainnya seperti <a href="http://alexgorbatchev.com/SyntaxHighlighter/">SyntaxHighlighter</a> dan <a href="https://highlightjs.org/">highlight.js</a>. <em>Syntax highlighter</em> yang digunakan oleh BelajarPemrograman adalah PrismJS. Oleh karena itu, pada kesempatan ini kita akan membahas PrismJS.'
layout: post
permalink: >
  http://belajarpemrograman.org/jelajah-open-source-prismjs/
published: true
post_date: 2017-11-12 22:35:12
---
Mengenal PrismJS {.no-mar-top}
------------------------------

[PrismJS](http://prismjs.com/index.html) merupakan sebuah library open source _syntax highligher_. _Syntax highlighter_ digunakan untuk men-*style* source code agar lebih mudah dan nyaman dibaca. Selain PrismJS, terdapat beberapa _syntax highlighter_ lainnya seperti [SyntaxHighlighter](http://alexgorbatchev.com/SyntaxHighlighter/) dan [highlight.js](https://highlightjs.org/). _Syntax highlighter_ yang digunakan oleh BelajarPemrograman adalah PrismJS. Oleh karena itu, pada kesempatan ini kita akan membahas PrismJS.

|                         |                                                                         |
| ----------------------- | ----------------------------------------------------------------------- |
| __Source Code__         | [https://github.com/PrismJS/prism/](https://github.com/PrismJS/prism/)
| __Bahasa Pemrograman__  | JavaScript
| __Pembuat Awal__        | [Lea Verou](http://lea.verou.me/)
| __Lisensi__             | [MIT](https://github.com/PrismJS/prism/blob/gh-pages/LICENSE)

Struktur File/Folder Source Code PrismJS
----------------------------------------

Source code yang akan kita bahas berada di [rilis v1.8.4](https://github.com/PrismJS/prism/releases/tag/v1.8.4). Struktur foldernya tidak berubah sejak [versi 1.0.0](https://github.com/PrismJS/prism/releases/tag/v1.0.0). Perubahan yang ketara, pada versi 1.0.0 hanya terdapat 132 file _languge definition_ di folder `/components/` (termasuk file-file _minified javascript_). Sedangkan di versi 1.8.4, kini sudah ada 254 file. Selain itu, jumlah plugin-nya juga bertambah, dari 9 menjadi 25.

Source code ini juga menyertakan kode untuk [website PrismJS](http://prismjs.com/index.html). Berikut merupakan penjelasan tentang beberapa file/folder source code:

-   `/components/` berisikan file-file `.js` untuk _language definition_. _Language definition_ mendifinisikan setiap token pada bahasa pemrograman tertentu. Token-token tersebut diekspresikan dalam _regular expression_.
    -   `prism-abap.js` merupakan file yang berisi _language definition_ untuk bahasa pemrograman ABAP
    -   `prism-actionscript.js`
    -   `prism-ada.js`
    -   ...
-   `/examples/` berisikan contoh-contoh kode untuk setiap bahasa pemrograman yang didukung.
    -   `prism-abap.html`
    -   `prism-actionscript.html`
    -   `prism-ada.html`
    -   ...
-   `/img/`
-   `/plugins/` berisikan source code untuk plugin-plugin guna memberikan fitur ekstra. Setiap plugin memiliki foldernya tersendiri.
    -   `autolinker/`
    -   `autoloader/`
    -   `command-line/`
    -   ...
-   `/templates/`
-   `/tests/` berisikan file-file test
-   `/themes/` berisikan file-file `.css` tema PrismJS
    -   `prism-coy.css`
    -   `prism-dark.css`
    -   `prism-funky.css`
-   `/.gitignore` mengatur file/direktori apa saja yang tidak ingin kita masukkan ke repositori git. Yang menarik di sini adalah, [leaverou](http://lea.verou.me/) menggunakan nama file dengan pola `hide-*.js` untuk file-file tambahan yang tidak ingin di*commit* ke repositori.
-   `/.npmignore` mengatur file/direktori apa saja yang tidak ingin kita masukkan ke package npm. PrismJS dapat ditemukan di [repositori npm](https://www.npmjs.com/package/prismjs) dengan nama `prismjs`.
-   `/travis.yml` merupakan file [YAML](http://yaml.org/) untuk konfigurasi [Travis CI](https://travis-ci.org/). Travis CI digunakan untuk mengotomasi proses test dan build pada setiap commit.

Belajar regex (Regular Expression)
----------------------------------

File-file _language definition_ `.js` dalam folder `components` berisikan regular expression untuk mendefinisikan kumpulan token dari source code dalam bahasa pemrograman tertentu. Nah, di sini kita bisa belajar banyak tentang regex. Untuk membantu proses belajar, tool berikut dapat digunakan:

-   [regular expression 101](https://regex101.com/)

    Di website ini, kita bisa memasukkan regular expression dan mendapatkan penjelasan tentangnya. Dijelaskan bagian per bagian secara detail. Kemudian, kita bisa mencoba memasukkan string untuk diuji apakah sesuai dengan regex. Kalau string cocok dengan regex, akan diberikan penjelasan tentang pencocokannya juga.

-   [Regexper](https://regexper.com/)

    Dengan menggunaka Regexper, kita dapat memperoleh grafik yang rapi dan mudah dimengerti dari regex yang kita inputkan.

Langsung saja kita mulai. Coba kita lihat sebagian kode pada file _language definition_ untuk CSS, `components/prism-css.js`:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-javascript .line-numbers}
Prism.languages.css = {
	&#039;comment&#039;: /\/\*[\s\S]*?\*\//,
	&#039;atrule&#039;: {
		pattern: /@[\w-]+?.*?(?:;|(?=\s*\{))/i,
		inside: {
			&#039;rule&#039;: /@[\w-]+/
			// See rest below
		}
	},
	&#039;url&#039;: /url\((?:([&quot;&#039;])(?:\\(?:\r\n|[\s\S])|(?!\1)[^\\\r\n])*\1|.*?)\)/i,
	&#039;selector&#039;: /[^{}\s][^{};]*?(?=\s*\{)/,
	&#039;string&#039;: {
		pattern: /(&quot;|&#039;)(?:\\(?:\r\n|[\s\S])|(?!\1)[^\\\r\n])*\1/,
		greedy: true
	},
	&#039;property&#039;: /[\w-]+(?=\s*:)/i,
	&#039;important&#039;: /\B!important\b/i,
	&#039;function&#039;: /[-a-z0-9]+(?=\()/i,
	&#039;punctuation&#039;: /[(){};:]/
};

Prism.languages.css[&#039;atrule&#039;].inside.rest = Prism.util.clone(Prism.languages.css);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Kode di atas mendefinisikan token-token untuk `language` CSS.

-   `comment`, `atrule`, `url`, `selector`, `string`, `property`, `important`, `function`, dan `punctuation` merupakan nama token.
-   Setiap token memiliki definisi dalam regular expression. Definisi tersebut dapat dibuat dengan menggunakan cara singkat

    ```
    'namatoken': /regex/
    ```

    atau dengan cara panjang

    ```
    'namatoken': {
        pattern: /regex/
    }
    ```

    Dengan menggunakan cara panjang, objek yang mendefinisikan token dapat memiliki atribut-atribut tambahan seperti `inside`, `greedy`, [dan lain-lain](http://prismjs.com/extending.html). Contohnya dapat dilihat pada definisi token `string`:

    ```
    'string': {
        pattern: /("|')(?:\\(?:\r\n|[\s\S])|(?!\1)[^\\\r\n])*\1/,
	greedy: true
    },
    ```

-   Komentar di CSS diekspresikan dengan format `/* Sebuah komentar */`, yaitu diawali dengan `/*` dan diakhiri dengan `*/`. Token untuk komentar didefinisikan sebagai berikut:

    ```
    'comment': /\/\*[\s\S]*?\*\//
    ```

    *Wow*, itu regex bacanya gimana? Intinya, karakter apa saja (baik _white space_ atau bukan) sebanyak apapun (boleh sepanjang 0, 1, 2, ... karakter) yang diapit oleh `/*` dan `*/`. [regexper](https://regexper.com/#%2F%5C%2F%5C*%5B%5Cs%5CS%5D*%3F%5C*%5C%2F%2F) menghasilkan diagram cantik lagi mudah dimengerti berikut:

    ![Regex untuk token comment di CSS](http://belajarpemrograman.org/wp-content/uploads/2017/11/regex-css-comment.png)


Dengan menggunakan _language definition_, PrismJS dapat menentukan token-token pada source code. Selanjutnya, setiap token dapat memiliki style yang diatur oleh file CSS di tema PrismJS.

Penutup
-------

Demikian merupakan awal dari perjalanan jelajah open source PrismJS. Jika teman-teman tertarik untuk melanjutkan perjalanan ini, semoga tulisan ini dapat membantu untuk memulai. PrismJS hanyalah salah satu dari milyaran repositori open source. Sistem operasi, ada yang open source. Text editor, ada yang open source. Photo editor, ada yang open source. 3D modelling software, ada yg open source. Browser, ada yang open source. Aplikasi chat, ada yang open source. Dan seterusnya. Itu semua bebas kita pelajari, gunakan, dan kembangkan sesuai dengan lisensinya. Wah, gak bakal kekurangan bahan belajar. Terus semangat ya...!
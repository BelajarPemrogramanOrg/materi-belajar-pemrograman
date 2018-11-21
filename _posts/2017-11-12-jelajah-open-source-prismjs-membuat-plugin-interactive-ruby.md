---
ID: 946
post_title: 'Jelajah Open Source: PrismJS – Membuat Plugin Interactive Ruby'
author: Muhammad Ikhsan
post_excerpt: ""
layout: post
permalink: >
  http://belajarpemrograman.org/jelajah-open-source-prismjs-membuat-plugin-interactive-ruby/
published: true
post_date: 2017-11-12 22:35:11
---
Pendahuluan {.no-mar-top}
-------------------------

Untuk digunakan pada materi belajar Ruby di website ini, saya terpikir untuk membuat plugin *interactive ruby*. Plugin ini akan menampilkan prompt `irb` (interactive ruby), seperti `irb(main):001:0>`, `irb(main):002:0>`, `irb(main):003:0>`, dan seterusnya. Ngomong-ngomong, prompt ini sebetulnya dapat dikonfigurasi sesuai keinginan, bisa hanya dengan `>>`, atau `irb :001>`, atau format lainnya.

Demo
----

<img src="http://belajarpemrograman.org/wp-content/uploads/2017/09/demo-prismjs-plugin-interactive-ruby-belajar-pemrograman.png" alt="demo-prismjs-plugin-interactive-ruby-belajar-pemrograman" width="563" height="133" class="alignnone size-full wp-image-841" />

Gambar di atas menunjukkan hasil dari penggunaan PrismJS dengan kode berikut:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-markup .line-numbers}
&lt;pre class=&quot;interactive-ruby&quot; data-output=&quot;2,4,5&quot;&gt;&lt;code class=&quot;language-ruby&quot;&gt;&quot;Hello World!&quot;
=&gt; &quot;Hello World!&quot;
puts &quot;Hello World!&quot;
&quot;Hello World!&quot;
=&gt; nil&lt;/code&gt;&lt;/pre&gt;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Langkah-Langkah
---------------

Sudah ada plugin PrismJS yang memiliki fitur prompt, yaitu plugin [Command Line](http://prismjs.com/plugins/command-line/). Jadi, supaya cepat selesai, saya menggunakan plugin Command Line sebagai kode dasar untuk plugin Interactive Ruby.

Berikut di bawah ini langkah-langkah yang saya lakukan:

1.  Kopas *source code* plugin Command Line

    *Source code* plugin Command Line terletak di `PrismJS/plugins/command-line`. Kopas folder tersebut, dan rename menjadi `interactive-ruby`. Rename juga file-file yang ada di folder, dari `*command-line*` menjadi `*interactive-ruby*`.

    Source code terdiri dari 3 bagian:
    - `prism-interactive-ruby.js` merupakan file utama plugin,
    - `prism-interactive-ruby.css` utk style ketika plugin diterapkan, dan
    - `index.html` berisi contoh dan dokumentasi cara menggunakan plugin.

2.  Modifikasi kode dalam file `prism-interactive-ruby.js` menjadi seperti berikut:

    ```javascript
    (function() {

    if (typeof self === 'undefined' || !self.Prism || !self.document) {
        return;
    }

    Prism.hooks.add('complete', function (env) {
        if (!env.code) {
            return;
        }

        // Hanya bisa digunakan untuk tag <code> yang diletakkan di dalam tag <pre> (bukan penggunaan inline).
        var pre = env.element.parentNode;
        var clsReg = /\s*\binteractive-ruby\b\s*/;
        if (
            !pre || !/pre/i.test(pre.nodeName) ||
                // Hentikan jika baik <pre> maupun <code> tidak memiliki class
            (!clsReg.test(pre.className) && !clsReg.test(env.element.className))
        ) {
            return;
        }

        if (env.element.querySelector('.interactive-ruby-prompt')) {
            // Hentikan jika prompt sudah dibuats.
            return;
        }

        if (clsReg.test(env.element.className)) {
            // Hapus class "interactive-ruby" dari tag <code>
            env.element.className = env.element.className.replace(clsReg, '');
        }
        if (!clsReg.test(pre.className)) {
            // Tambahkan class "interactive-ruby" ke tag <pre>
            pre.className += ' interactive-ruby';
        }

        var getAttribute = function(key, defaultValue) {
            return (pre.getAttribute(key) || defaultValue).replace(/"/g, '&quot');
        };

        // Mendata semua nomor baris yang menunjukkan output dari perintah Ruby. -- cwells
        var totalLines = env.code.split('\n').length;
        console.log(env.code.split('\n'));
        var outputLineNums = new Array();
        var outputSections = pre.getAttribute('data-output') || '';
        outputSections = outputSections.split(',');
        for (var i = 0; i < outputSections.length; i++) {
            var outputRange = outputSections[i].split('-');
            var outputStart = parseInt(outputRange[0]);
            var outputEnd = outputStart; // Default: end at the first line when it's not an actual range. -- cwells
            if (outputRange.length === 2) {
                outputEnd = parseInt(outputRange[1]);
            }

            if (!isNaN(outputStart) && !isNaN(outputEnd)) {
                for (var j = outputStart; j <= outputEnd && j <= totalLines; j++) {
                    outputLineNums.push(j);
                }
            }
        }

        // Contoh:
        // getPaddedNumber(1, 3)
        // => "001"
        // getPaddedNumber(25, 5)
        // => "00025"
        var getPaddedNumber = function(num, charCount) {
            if (typeof charCount == 'undefined') {
                charCount = 3;
            }

            var paddedNum = num.toString();
            while (paddedNum.length < charCount) {
                paddedNum = '0' + paddedNum;
            }
            return paddedNum;
        };

        // Buat "baris" untuk menjadi prompt interactive-ruby. -- cwells
        var lines = '';
        var inputLineNum = 1;
        for (var i = 0; i < totalLines; i++) {
            var curLineNum = i + 1;
            if (outputLineNums.indexOf(curLineNum) === -1) {
                var promptText = 'irb(main):' + getPaddedNumber(inputLineNum) + ':0>';
                lines += '<span data-prompt="' + promptText + '"></span>';
                inputLineNum++;
            } else {
                lines += '<span></span>';
            }
        }

        // Buat elemen wrapper. -- cwells
        var prompt = document.createElement('span');
        prompt.className = 'interactive-ruby-prompt';
        prompt.innerHTML = lines;

        env.element.innerHTML = prompt.outerHTML + env.element.innerHTML;
    });

    }());
    ```

    Di setiap folder plugin yg sudah ada, selalu ada versi _minified_ dari file `.js` yg dipakai. Kita juga perlu menambahkannya. Mudahnya, tanya saja `minify js` di Google, ada banyak _online tool_ yg bisa dipakai.

3.  Modifikasi kode dalam file `prism-interactive-ruby.css` menjadi seperti berikut:

    ```css
    .interactive-ruby-prompt {
        border-right: 1px solid #999;
        display: block;
        float: left;
        font-size: 100%;
        letter-spacing: -1px;
        margin-right: 1em;
        pointer-events: none;

        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
    }

    .interactive-ruby-prompt > span:before {
        color: #999;
        content: ' ';
        display: block;
        padding-right: 0.8em;
    }

    .interactive-ruby-prompt > span[data-prompt]:before {
        content: attr(data-prompt);
    }
    ```

3.  Menambahkan informasi dokumentasi dan contoh penggunaan plugin dengan mengedit file `index.html`. Menggunakan file ini, kita bisa sekalian mengecek apakah plugin yg kita buat berjalan sesuai harapan. Karna kodenya panjang, dan kebanyakan hanya konten, langsung lihat di <https://github.com/muhikhsan101/prism/blob/interactive-ruby/plugins/interactive-ruby/index.html> saja.

Kode lengkap plugin, termasuk utk file js dan css-nya bisa dilihat di <https://github.com/muhikhsan101/prism/tree/interactive-ruby/plugins/interactive-ruby>. Bedanya, yg di GitHub, komen2nya saya buat dalam Bahasa Inggris. Saya rasa gak masalah ya.

Penutup
-------

Demikian adalah langkah-langkah yg saya lakukan untuk membuat plugin PrismJS: Interactive Ruby. Yaitu, sebuah plugin sederhana untuk memodifikasi tampilan kode yg diinputkan pada `irb`, sehingga memiliki _prompt_ dan _line number_. Ini hanya contoh, masih bisa diimprove agar lebih serupa dengan prompt `irb` yg sebenarnya.

Tujuan dari tulisan ini adalah untuk memberikan contoh dan motivasi (jg utk diri saya sendiri), bahwa kita bisa belajar banyak dari proyek open source. Kita juga bisa turut berkontribusi pada proyek yg kita suka. Entah itu dengan membantu menerjemahkan teks UI / dokumentasi ke dalam Bahasa Indonesia, solve bug, menambahkan fitur, dll.

Terima kasih, semoga bermanfaat.
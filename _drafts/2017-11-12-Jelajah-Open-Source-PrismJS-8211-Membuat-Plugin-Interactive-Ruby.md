---
ID: 946
post_title: 'Jelajah Open Source: PrismJS &#8211; Membuat Plugin Interactive Ruby'
author: Muhammad Ikhsan
post_excerpt: ""
layout: post
permalink: http://belajarpemrograman.org/?p=946
published: false
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

    *Source code* plugin Command Line terletak di `PrismJS/plugins/command-line`. Kopas folder tersebut, dan rubah nama folder menjadi `interactive-ruby`. *Rename* juga file-file yang terdapat di folder tersebut, dari *substring* `command-line` menjadi `interactive-ruby`.

2.  Modifikasi kode dalam file `prism-interactive-ruby.js` menjadi seperti berikut:

    <pre class="language-javascript line-numbers"><code>(function() {
    &nbsp;
    if (typeof self === 'undefined' || !self.Prism || !self.document) {
    	return;
    }
    &nbsp;
    Prism.hooks.add('complete', function (env) {
    	if (!env.code) {
    		return;
    	}
    &nbsp;
    	// Hanya bisa digunakan untuk tag &lt;code&gt; yang diletakkan di dalam tag &lt;pre&gt; (bukan penggunaan inline).
    	var pre = env.element.parentNode;
    	var clsReg = /s*binteractive-rubybs*/;
    	if (
    		!pre || !/pre/i.test(pre.nodeName) ||
    			// Hentikan jika baik &lt;pre&gt; maupun &lt;code&gt; tidak memiliki class 
    		(!clsReg.test(pre.className) && !clsReg.test(env.element.className))
    	) {
    		return;
    	}
    &nbsp;
    	if (env.element.querySelector('.interactive-ruby-prompt')) {
    		// Hentikan jika prompt sudah dibuat
    		return;
    	}
    &nbsp;
    	if (clsReg.test(env.element.className)) {
    		// Hapus class "interactive-ruby" dari tag &lt;code&gt;
    		env.element.className = env.element.className.replace(clsReg, '');
    	}
    	if (!clsReg.test(pre.className)) {
    		// Tambahkan class "interactive-ruby" ke tag &lt;pre&gt;
    		pre.className += ' interactive-ruby';
    	}
    &nbsp;
    	var getAttribute = function(key, defaultValue) {
    		return (pre.getAttribute(key) || defaultValue).replace(/"/g, '&quot');
    	};
    &nbsp;
    	// Mendata semua nomor baris yang menunjukkan output dari perintah Ruby. -- cwells
    	var totalLines = env.code.split('n').length;
    	console.log(env.code.split('n'));
    	var outputLineNums = new Array();
    	var outputSections = pre.getAttribute('data-output') || '';
    	outputSections = outputSections.split(',');
    	for (var i = 0; i &lt; outputSections.length; i++) {
    		var outputRange = outputSections[i].split('-');
    		var outputStart = parseInt(outputRange[0]);
    		var outputEnd = outputStart; // Default: hanya n, bukan range (n1-n2). -- cwells
    		if (outputRange.length === 2) {
    			outputEnd = parseInt(outputRange[1]);
    		}
    &nbsp;
    		if (!isNaN(outputStart) && !isNaN(outputEnd)) {
    			for (var j = outputStart; j &lt;= outputEnd && j &lt;= totalLines; j++) {
    				outputLineNums.push(j);
    			}
    		}
    	}
    &nbsp;
    	// Contoh:
    	// getPaddedNumber(1, 3)
    	// =&gt; "001"
    	// getPaddedNumber(25, 5)
    	// =&gt; "00025"
    	var getPaddedNumber = function(num, charCount) {
    		if (typeof charCount == 'undefined') {
    			charCount = 3;
    		}
    &nbsp;
    		var paddedNum = num.toString();
    		while (paddedNum.length &lt; charCount) {
    			paddedNum = '0' + paddedNum;
    		}
    		return paddedNum;
    	};
    &nbsp;
    	// Buat "baris" untuk menjadi prompt interactive-ruby. -- cwells
    	var lines = '';
    	var inputLineNum = 1;
    	for (var i = 0; i &lt; totalLines; i++) {
    		var curLineNum = i + 1;
    		if (outputLineNums.indexOf(curLineNum) === -1) {
    			var promptText = 'irb(main):' + getPaddedNumber(inputLineNum) + ':0';
    			lines += '&lt;span data-prompt="' + promptText + '"&gt;&lt;/span&gt;';
    			inputLineNum++;
    		} else {
    			lines += '&lt;span&gt;&lt;/span&gt;';
    		}
    	}
    &nbsp;
    	// Buat elemen wrapper. -- cwells
    	var prompt = document.createElement('span');
    	prompt.className = 'interactive-ruby-prompt';
    	prompt.innerHTML = lines;
    
    	env.element.innerHTML = prompt.outerHTML + env.element.innerHTML;
    });
    &nbsp;
    }());
    </code></pre>

3.  Modifikasi kode dalam file `prism-interactive-ruby.css` menjadi seperti berikut:

    <pre class="language-css line-numbers"><code>.interactive-ruby-prompt {
    	border-right: 1px solid #999;
    	display: block;
    	float: left;
    	font-size: 100%;
    	letter-spacing: -1px;
    	margin-right: 1em;
    	pointer-events: none;
    &nbsp;
    	-webkit-user-select: none;
    	-moz-user-select: none;
    	-ms-user-select: none;
    	user-select: none;
    }
    &nbsp;
    .interactive-ruby-prompt > span:before {
    	color: #999;
    	content: ' ';
    	display: block;
    	padding-right: 0.8em;
    }
    &nbsp;
    .interactive-ruby-prompt > span[data-prompt]:before {
    	content: attr(data-prompt);
    }
    </code></pre>
---
ID: 705
post_title: Menguasai Perintah-Perintah Penting npm
author: Muhammad Ikhsan
post_excerpt: 'npm (Node Package Manager) merupakan <em>package manager</em> untuk JavaScript. Dengan menggunakan npm, developer dapat mencari, mendapatkan, menggunakan dan berbagi package-package JavaScript. Dalam materi belajar ini akan dibahas beberapa perintah <code>npm</code> yang menurut saya penting, mulai dari inisialisasi <code>package.json</code> hingga untuk membuka dokumentasi package.'
layout: post
permalink: >
  http://belajarpemrograman.org/menguasai-perintah-perintah-penting-npm/
published: true
post_date: 2017-09-19 00:45:19
---
npm (Node Package Manager) merupakan <em>package manager</em> untuk JavaScript. Dengan menggunakan npm, developer dapat mencari, mendapatkan, menggunakan dan berbagi package-package JavaScript. Dalam materi belajar ini akan dibahas beberapa perintah <code>npm</code> yang menurut saya penting, mulai dari inisialisasi <code>package.json</code> hingga untuk membuka dokumentasi package.

&nbsp;

<h2>Inisialisasi <code>package.json</code></h2>

File <code>package.json</code> merupakan sebuah dokumen yang berisikan informasi mengenai sebuah modul. Informasi tersebut antar lain nama, versi, deskripsi, keyword, license, dan lain-lain. Ketika Anda membuat modul baru, Anda dapat menjalankan perintah berikut untuk membuat file <code>package.json</code>.

<pre><code class="language-bash">npm init
</code></pre>

Anda akan diminta memberikan nama modul yang Anda buat, versi, deskripsi, dll untuk dimasukkan ke dalam file <code>package.json</code>.

&nbsp;

<h2>Instalasi Package</h2>

<h3>Instal <em>dependency</em> modul</h3>

File <code>package.json</code> dalam folder modul Anda biasanya menyertakan informasi mengenai <em>dependency</em> yang dibutuhkan. <em>Dependency</em> merupakan package yang harus terinstal agar project Anda bisa dijalankan. Gunakan perintah berikut untuk menginstal dependency-dependency tersebut.

<pre><code class="language-bash">npm install
</code></pre>

Dengan menjalankan perintah tersebut, package-package yang menjadi <em>dependency</em> akan disimpan ke dalam folder <code>node_modules</code>.

<h3>Instal package untuk digunakan secara global</h3>

Yang dimaksud dengan global adalah bahwa package dapat diakses dari lokasi mana saja di komputer, seperti halnya menginstal sebuah program. Biasanya, package yang diinstal secara global adalah package yang hendak digunakan sebagai <em>command line tool</em>.

<pre><code class="language-bash"># Format perintah:
npm install -g &lt;nama package&gt;
# Contoh penggunaan:
npm install -g webpack
# Setelah terinstall, dapat coba dijalankan:
webpack -v
</code></pre>

<h3>Instal package untuk digunakan secara lokal</h3>

Untuk menggunakan sebuah package pada modul Anda, Anda bisa memanggilnya dengan menggunakan perintah <code>require("namaPackage")</code>. Sebelum Anda dapat me-<code>require</code> package tersebut, tentu saja Anda perlu menginstalnya terlebih dahulu.

<pre><code class="language-bash"># Format perintah:
npm install &lt;nama package&gt;
# Contoh:
npm install express
</code></pre>

Package yang diinstal akan dimasukkan ke dalam folder <code>&lt;folder project&gt;/node_modules</code>. Perintah di atas tidak turut menambahkan nama serta package yang diinstal ke dalam file <code>package.json</code> sebagai <em>dependency</em>.

<h3>Instal package sekaligus update informasi <code>dependencies</code> di <code>package.json</code></h3>

Di sini, kita ingin menginstal sebuah package sekaligus memasukkan informasi nama dan versi package ke dalam file <code>package.json</code> sebagai <em>dependency</em>.

<pre><code class="language-bash"># Format perintah:
npm install --save &lt;nama package&gt;
# Contoh:
npm install --save express
</code></pre>

<h3>Instal package sekaligus update informasi <code>devDependencies</code> di <code>package.json</code></h3>

Setelah menginstal semua <em>dependency</em> yang tercantum pada bagian <code>dependencies</code> dalam file <code>package.json</code>, modul yang Anda buat seharusnya dapat dijalankan. Namun, bisa jadi Anda membutuhkan dependency tambahan yang Anda gunakan sebagai bagian dari development environment, misalnya untuk testing. <em>Dependency</em> tersebut dapat Anda tambahkan ke dalam file <code>package.json</code> dalam item <code>devDependencies</code>.

<pre><code class="language-bash"># Format perintah:
npm install --save-dev &lt;nama package&gt;
# Contoh:
npm install --save-dev gulp
</code></pre>

<h3>Install package lokal dari sebuah repositori git</h3>

<pre><code class="language-bash"># Format perintah:
npm install &lt;url repo&gt;
# Contoh 1:
npm install git+https://github.com/bendrucker/smallest.git
# Contoh 2:
npm install git://github.com/bendrucker/smallest.git
# Contoh 3:
npm install https://github.com/bendrucker/smallest.git
# Contoh 4:
npm install --save git+https://github.com/bendrucker/smallest.git
</code></pre>

&nbsp;

<h2>Penghapusan Package</h2>

Untuk menghapus package, kurang lebih caranya sama seperti dengan penginstalannya. Bedanya, kita menggunakan perintah <code>uninstall</code>.

<pre><code class="language-bash"># Menghapus package global:
npm uninstall -g webpack
# Menghapus package lokal:
npm uninstall express
# Menghapus package sekaligus update informasi dependencies di package.json:
npm uninstall --save express
# Menghapus package sekaligus update informasi devDependencies di package.json:
npm uninstall --save-dev gulp
</code></pre>

&nbsp;

<h2>Memperbarui Package</h2>

<h3>Memperbarui package global</h3>

<pre><code class="language-bash">npm update -g
</code></pre>

<h3>Memperbarui package lokal</h3>

<pre><code class="language-bash">npm update
</code></pre>

&nbsp;

<h2>Melihat Daftar Package</h2>

<h4>Melihat daftar package global</h4>

<pre><code class="language-bash"># Hanya daftar:
npm ls -g
# Daftar disertai detail:
npm ls -gl
</code></pre>

<h3>Melihat daftar package lokal</h3>

<pre><code class="language-bash"># Hanya daftar:
npm ls
# Daftar disertai detail
npm ls -l
</code></pre>

<h3>Melihat daftar package dengan informasi versi yang <em>outdated</em></h3>

Anda dapat melihat daftar package-package yang menjadi <em>dependency</em> modul Anda beserta informasi versinya dengan menjalankan perintah berikut.

<pre class="command-line" data-user="mi" data-host="localhost" data-output="2-7"><code class="language-bash">npm outdated
Package       Current  Wanted  Latest  Location
chai            2.3.0   2.3.0   4.1.2  prismjs
gulp-replace    0.5.4   0.5.4   0.6.1  prismjs
gulp-uglify     0.3.2   0.3.2   3.0.0  prismjs
mocha           2.5.3   2.5.3   3.5.3  prismjs
yargs          3.32.0  3.32.0   9.0.1  prismjs</code></pre>

<ul>
<li>Kolom <code>Current</code> menunjukkan versi yang modul Anda gunakan.</li>
<li>Kolom <code>Wanted</code> menunjukkan versi yang dikehendaki modul Anda.</li>
<li>Kolom <code>Latest</code> menunjukkan versi terbaru yang tersedia untuk diinstal.</li>
</ul>

&nbsp;

<h2>Konfigurasi npm</h2>

<h3>Melihat daftar semua flag konfigurasi npm</h3>

<pre><code class="language-bash">npm config ls -l
</code></pre>

<h3>Mengatur nilai flag konfigurasi npm</h3>

Misalnya Anda ingin merubah nilai flag konfigurasi <code>save</code> menjadi <code>true</code> (defaultnya <code>false</code>).

<pre><code class="language-bash">npm config set save true
</code></pre>

Dengan nilai flag konfigurasi <code>save</code> diubah menjadi <code>true</code>, kini parameter <code>--save</code> secara default akan digunakan untuk setiap pemanggilan <code>npm install</code>.

<h3>Mengatur nilai default untuk <code>npm init</code></h3>

<pre><code class="language-bash">npm config set init-author-name "Muhammad Ikhsan"
npm config set init-author-email "muhikhsan101@gmail.com"
npm config set init-author-url "https://belajarpemrograman/author/mikhsan"
npm config set init-license "MIT"
npm config set init-version "0.1.0"
</code></pre>

&nbsp;

<h2>Membuka Dokumentasi Package</h2>

Anda bisa membuka dokumentasi dari sebuah package dengan menjalankan perintah berikut.

<pre><code class="language-bash"># Format perintah
npm docs &lt;nama package&gt;
# Contoh 1:
npm docs express
# Contoh 2 (membuka lebih dari satu dokumentasi package):
npm docs webpack browserify
</code></pre>

Dokumentasi akan dibuka melalui browser.
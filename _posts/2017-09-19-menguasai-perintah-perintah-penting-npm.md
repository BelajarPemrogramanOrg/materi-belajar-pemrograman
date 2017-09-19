---
ID: 705
post_title: Menguasai Perintah-Perintah Penting npm
author: Muhammad Ikhsan
post_excerpt: >
  Materi ini berisi daftar penggunaan
  perintah-perintah npm yang (menurut
  saya) penting dan sering diperlukan.
layout: post
permalink: >
  http://belajarpemrograman.org/menguasai-perintah-perintah-penting-npm/
published: true
post_date: 2017-09-19 00:45:19
---
Pendahuluan {.no-mar-top}
-------------------------

npm merupakan *package manager* untuk JavaScript. Dengan menggunakan npm, developer dapat mencari, mendapatkan, menggunakan dan berbagi package-package JavaScript. Dalam materi belajar ini akan dibahas beberapa perintah `npm` yang sering digunakan oleh *JavaScript developer* dalam pekerjaannya.

Inisialisasi `package.json`
---------------------------

File `package.json` merupakan sebuah dokumen yang berisikan informasi mengenai sebuah modul. Informasi tersebut antar lain nama, versi, deskripsi, keyword, license, dan lain-lain. Ketika Anda membuat modul baru, Anda dapat menjalankan perintah berikut untuk membuat file `package.json`.

```
npm init
```

Anda akan diminta memberikan nama modul yang Anda buat, versi, deskripsi, dll untuk dimasukkan ke dalam file `package.json`.

Instalasi Package
---------------------------------

##### Instal *dependency* modul

File `package.json` dalam folder modul Anda biasanya menyertakan informasi mengenai *dependency* yang dibutuhkan. *Dependency* merupakan package yang harus terinstal agar project Anda bisa dijalankan. Gunakan perintah berikut untuk menginstal dependency-dependency tersebut.

```
npm install
```

Dengan menjalankan perintah tersebut, package-package yang menjadi *dependency* akan disimpan ke dalam folder `node_modules`.

##### Instal package untuk digunakan secara global

Yang dimaksud dengan global adalah bahwa package dapat diakses dari lokasi mana saja di komputer, seperti halnya menginstal sebuah program. Biasanya, package yang diinstal secara global adalah package yang hendak digunakan sebagai *command line tool*.

```
# Format perintah:
npm install -g &lt;nama package&gt;
# Contoh penggunaan:
npm install -g webpack
# Setelah terinstall, dapat coba dijalankan:
webpack -v
```

##### Instal package untuk digunakan secara lokal

Untuk menggunakan sebuah package pada modul Anda, Anda bisa memanggilnya dengan menggunakan perintah `require("namaPackage")`. Sebelum Anda dapat me-`require` package tersebut, tentu saja Anda perlu menginstalnya terlebih dahulu.

```
# Format perintah:
npm install &lt;nama package&gt;
# Contoh:
npm install express
```

Package yang diinstal akan dimasukkan ke dalam folder `<folder project>/node_modules`. Perintah di atas tidak turut menambahkan nama serta package yang diinstal ke dalam file `package.json` sebagai *dependency*.

##### Instal package sekaligus update informasi `dependencies` di `package.json`

Di sini, kita ingin menginstal sebuah package sekaligus memasukkan informasi nama dan versi package ke dalam file `package.json` sebagai *dependency*.

```
# Format perintah:
npm install --save &lt;nama package&gt;
# Contoh:
npm install --save express
```

##### Instal package sekaligus update informasi `devDependencies` di `package.json`

Setelah menginstal semua *dependency* yang tercantum pada bagian `dependencies` dalam file `package.json`, modul yang Anda buat seharusnya dapat dijalankan. Namun, bisa jadi Anda membutuhkan dependency tambahan yang Anda gunakan sebagai bagian dari development environment, misalnya untuk testing. *Dependency* tersebut dapat Anda tambahkan ke dalam file `package.json` dalam item `devDependencies`.

```
# Format perintah:
npm install --save-dev &lt;nama package&gt;
# Contoh:
npm install --save-dev gulp
```

##### Install package lokal dari sebuah repositori git

```
# Format perintah:
npm install &lt;url repo&gt;
# Contoh 1:
npm install git+https://github.com/bendrucker/smallest.git
# Contoh 2:
npm install git://github.com/bendrucker/smallest.git
# Contoh 3:
npm install https://github.com/bendrucker/smallest.git
# Contoh 4:
npm install --save git+https://github.com/bendrucker/smallest.git
```

Penghapusan Package
-------------------

Untuk menghapus package, kurang lebih caranya sama seperti dengan penginstalannya. Bedanya, kita menggunakan perintah `uninstall`.

```
# Menghapus package global:
npm uninstall -g webpack
# Menghapus package lokal:
npm uninstall express
# Menghapus package sekaligus update informasi dependencies di package.json:
npm uninstall --save express
# Menghapus package sekaligus update informasi devDependencies di package.json:
npm uninstall --save-dev gulp
```

Memperbarui Package
-------------------

##### Memperbarui package global

```
npm update -g
```

##### Memperbarui package lokal

```
npm update
```

Melihat Daftar Package
----------------------

##### Melihat daftar package global

```
# Hanya daftar:
npm ls -g
# Daftar disertai detail:
npm ls -gl
```

##### Melihat daftar package lokal

```
# Hanya daftar:
npm ls
# Daftar disertai detail
npm ls -l
```

##### Melihat daftar package dengan informasi versi yang *outdated*

Anda dapat melihat daftar package-package yang menjadi *dependency* modul Anda beserta informasi versinya dengan menjalankan perintah berikut.

<pre class="command-line" data-user="mikhsan" data-host="belajarpemrograman" data-output="2-7"><code class="language-bash">npm outdated
Package       Current  Wanted  Latest  Location
chai            2.3.0   2.3.0   4.1.2  prismjs
gulp-replace    0.5.4   0.5.4   0.6.1  prismjs
gulp-uglify     0.3.2   0.3.2   3.0.0  prismjs
mocha           2.5.3   2.5.3   3.5.3  prismjs
yargs          3.32.0  3.32.0   9.0.1  prismjs</code></pre>

-   Kolom `Current` menunjukkan versi yang modul Anda gunakan.
-   Kolom `Wanted` menunjukkan versi yang dikehendaki modul Anda.
-   Kolom `Latest` menunjukkan versi terbaru yang tersedia untuk diinstal.

Konfigurasi npm
---------------

##### Melihat daftar semua flag konfigurasi npm

```
npm config ls -l
```

##### Mengatur nilai flag konfigurasi npm

Misalnya Anda ingin merubah nilai flag konfigurasi `save` menjadi `true` (defaultnya `false`).

```
npm config set save true
```

Dengan nilai flag konfigurasi `save` diubah menjadi `true`, kini parameter `--save` secara default akan digunakan untuk setiap pemanggilan `npm install`.

##### Mengatur nilai default untuk `npm init`

```
npm config set init-author-name &quot;Muhammad Ikhsan&quot;
npm config set init-author-email &quot;muhikhsan101@gmail.com&quot;
npm config set init-author-url &quot;https://belajarpemrograman/author/mikhsan&quot;
npm config set init-license &quot;MIT&quot;
npm config set init-version &quot;0.1.0&quot;
```

Dokumentasi Package
-------------------

Anda bisa membuka dokumentasi dari sebuah package dengan menjalankan perintah berikut.

```
# Format perintah
npm docs &lt;nama package&gt;
# Contoh 1:
npm docs express
# Contoh 2 (membuka lebih dari satu dokumentasi package):
npm docs webpack browserify
```

Dokumentasi akan dibuka melalui browser.
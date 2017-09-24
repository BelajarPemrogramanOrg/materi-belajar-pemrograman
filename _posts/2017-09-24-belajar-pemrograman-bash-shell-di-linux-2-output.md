---
ID: 571
post_title: 'Belajar Pemrograman Bash Shell di Linux 2: Output'
author: Muhammad Ikhsan
post_excerpt: 'Program <code>bash</code> beroperasi pada antarmuka berbasis teks (<em>text-based interface</em>), misalnya melalui program terminal. Beberapa contoh program terminal antara lain <code>gnome-terminal</code> dan <code>konsole</code> di Linux, <code>Terminal</code> di Mac OS, dan <code>cmd.exe</code> pada Windows. Bentuk interaksi dasar antara user dan program adalah dengan memberikan/menerima input dan output. Secara default, output ditampilkan di layar melalui program <em>terminal</em>. Selain itu, output juga dapat disimpan ke dalam file atau dikirimkan menjadi input untuk perintah yang lain. Pada materi belajar ini, Anda akan belajar untuk membuat output pada pemrograman bash shell dengan menggunakan perintah <code>echo</code> dan <code>printf</code>.'
layout: post
permalink: >
  http://belajarpemrograman.org/belajar-pemrograman-bash-shell-di-linux-2-output/
published: true
post_date: 2017-09-24 12:40:12
---
Pada materi berjudul [Belajar Pemrograman Bash Shell di Linux 1: Pengenalan], Anda telah mempelajari apa itu shell, bash, bahasa bash shell, dan juga telah membuat serta menjalankan 2 *script* bash shell sederhana. Pada materi ini, Anda akan belajar untuk membuat output pada pemrograman bash shell dengan menggunakan perintah `echo` dan `printf`.

------------------------------------------------------------------------

__Daftar Materi Belajar Pemrograman Bash Shell di Linux:__
1.  [Pengenalan](https://belajarpemrograman.org/belajar-pemrograman-bash-shell-di-linux-1-pengenalan/)
2.  Output _(Materi Ini)_

------------------------------------------------------------------------

Program `bash` beroperasi pada antarmuka berbasis teks (*text-based interface*), misalnya melalui program terminal. Beberapa contoh program terminal antara lain `gnome-terminal` dan `konsole` di Linux, `Terminal` di Mac OS, dan `cmd.exe` pada Windows. Nah, saat program terminal dibuka, secara otomatis program shell dijalankan oleh terminal. Sehingga, kita sebagai user berinteraksi dengan `bash` melalui program terminal.

Bentuk interaksi dasar antara user dan program adalah dengan memberikan/menerima input dan output. Secara default, output ditampilkan di layar melalui program *terminal*. Selain itu, output juga dapat disimpan ke dalam file atau dikirimkan menjadi input untuk perintah yang lain. Demikian pula dengan input, tidak hanya bisa berasal dari *keyboard*, namun juga bisa dari file atau dari output perintah lain. Dalam materi belajar bash bagian 2 ini, kita akan membahas tentang output terlebih dahulu. Input akan dibahas pada materi belajar pemrograman bash pada bagian 3.

Menggunakan `echo`
------------------

Seperti yang telah kita lakukan pada bagian sebelumnya, kita bisa menggunakan perintah bash `echo` untuk memberikan output. Mari kita praktikkan penggunaannya.

#### Menampilkan tulisan atau *string*
     
<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2,4,6"><code class="language-bash">echo Saya sedang belajar pemrograman
Saya sedang belajar pemrograman
echo "Saya sedang belajar pemrograman"
Saya sedang belajar pemrograman
echo 'Saya sedang belajar pemrograman'
Saya sedang belajar pemrograman</code></pre>

Pada kasus ini, output dari ketiga pemanggilan `echo` tersebut sama. Baik tanpa menggunakan petik, menggunakan petik satu, maupun petik dua, menghasilkan output `Saya sedang belajar pemrograman`. Namun, perlu dipahami bahwa terdapat perbedaan dalam `echo` menafsirkan tiga perintah tersebut. Anda akan mempelajarinya beberapa saat lagi.

#### Menampilkan tulisan dengan spasi lebar

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2,4,6,8,10"><code class="language-bash">echo Saya     sedang     belajar     pemrograman
Saya sedang belajar pemrograman
echo "Saya"     "sedang"     "belajar"     "pemrograman"
Saya sedang belajar pemrograman
echo "Saya" "sedang" "belajar" "pemrograman"
Saya sedang belajar pemrograman
echo "Saya     sedang     belajar     pemrograman"
Saya     sedang     belajar     pemrograman
echo 'Saya     sedang     belajar     pemrograman'
Saya     sedang     belajar     pemrograman</code></pre>

Ketika saya ingin menuliskan <code>Saya &nbsp; &nbsp; sedang &nbsp; &nbsp; belajar &nbsp; &nbsp; pemrograman</code> dengan 5 spasi sebagai pemisah antar kata, ternyata cara `echo` biasa yang tanpa tanda petik tidak menghasilkan seperti yang saya harapkan. Mengapa? Karena rentetan kata `Saya`, `sedang`, `belajar`, `pemrograman` tersebut masing-masing dianggap sebagai argumen yang berbeda oleh `echo`. Maksudnya, `echo` menerima `Saya     sedang     belajar     pemrograman` sebagai 4 rentetan karakter yang harus di-*output*-kan, bukan sebagai satu kesatuan.

Sama halnya dengan <code>echo "Saya" &nbsp; &nbsp; "sedang" &nbsp; &nbsp; "belajar" &nbsp; &nbsp; "pemrograman"</code>, spasinya juga gak ngaruh. `echo` menerimanya sebagai 4 argumen. Lalu bagaimana cara mengatasinya? Kita harus membuat `echo` mengerti bahwa *string* tersebut adalah satu kesatuan berikut dengan spasinya. Kita bisa menggunakan petik satu (`'`), maupuan petik dua (`"`) yang mengapit tuilisan tersebut agar dianggap sebagai satu kesatuan, sebagai satu *string* utuh.

#### Menampilkan nilai variabel

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="3,5"><code class="language-bash">ngapain="belajar pemrograman"
echo ngapain
ngapain
echo $ngapain
belajar pemrograman</code></pre>

-   Pada baris pertama, tulisan atau *string* `belajar pemrograman` disimpan dalam variabel `ngapain`.
-   Untuk meng-*output*-kan nilai variabel `ngapain`, kita menggunakan perintah `echo` dengan menyertakan `$ngapain` sebagai argumen. Tanda `$` sebelum nama variabel digunakan untuk memanggil nilai dari variabel. Sehingga, pada dasarnya perintah yang dijalankan adalah `echo "belajar pemrograman"`.

#### Menampilkan nilai variabel dalam string
    
<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="3,5"><code class="language-bash">ngapain="belajar pemrograman"
echo "Saya sedang $ngapain"
Saya sedang belajar pemrograman
echo 'Saya sedang $ngapain'
Saya sedang $ngapain</code></pre>

Nah, di sini kita bisa lihat perbedaan antara penggunaan petik satu dan petik dua. String yang diapit dengan petik satu (`'`), diproses apa adanya tanpa mengubah `$ngapain` menjadi nilai variabel terlebih dahulu.

#### `echo` untuk Menulis File

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="3"><code class="language-bash">echo "Saya sedang belajar pemrograman" > ngapain.txt
cat ngapain.txt
Saya sedang belajar pemrograman</code></pre>

Karakter `>` digunakan untuk mengarahkan output ke lokasi tertentu. Dalam kasus ini, output dari `echo` diarahkan untuk dimasukkan ke file `ngapain.txt`, tidak ditampilkan di terminal. Anda bisa menggunakan perintah Linux `cat` untuk mengecek isi file `ngapain.txt` seperti pada contoh di atas.

Sebagai tambahan, penggunaan `>` tidak terbatas hanya untuk `echo`. Anda bisa mengarahkan output perintah-perintah lain untuk disimpan hasilnya ke dalam file. Misalnya, di bawah ini dicontohkan penggunaannya untuk membuat file yang berisi nama-nama file di direktori aktif.

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="3,4"><code class="language-bash">ls > isi-folder.txt
cat isi-folder.txt
isi-folder.txt
ngapain.txt</code></pre>

Menggunakan `printf`
--------------------

Selain `echo`, Anda juga bisa menggunakan `printf` untuk menuliskan output. Contoh-contoh dan aturan yang telah dijelaskan di atas untuk `echo` berlaku pula untuk `printf`. Namun, perintah `printf` memiliki beberapa fitur tambahan yang sebagiannya akan dicontohkan di bawah ini.

#### Menulis Beberapa Baris Kalimat

Satu perbedaan mendasar antara `printf` dan `echo` adalah `printf` tidak otomatis menambahkan baris baru di akhir baris. Kita harus menambahkannya manual menggunakan karakter `\n`. Kalau kita lupa menambahkannya, maka tulisan tersebut akan muncul sebaris dengan *prompt* perintah baru.

<pre class="language-bash"><code>$ printf "Baris pertama"
Baris pertama$ echo "Baris selanjutnya\n"
Baris selanjutnya</code></pre>

Berdasarkan hal tersebut, berarti kita juga bisa meng-*output*-kan beberapa baris tulisan sekaligus.

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2-4"><code class="language-bash">echo "Baris pertama\nBaris kedua\nBaris ketiga\n"
Baris pertama
Baris kedua
Baris ketiga</code></pre>

#### Melakukan Pemformatan Teks

Yang dimaksud pemformatan di sini, Anda bisa memformat suatu teks untuk ditulis sebagai *string*, bilangan bulat, bilangan desimal dan sebagainya.

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2,4"><code class="language-bash">printf '%s = %3.2f\n' 'Pi' 3.14159
Pi = 3.14
printf '%s = %3.2f\n' 'e' 2.71828
e = 2.72</code></pre>

-   Penggunaan perintah `printf` di `bash` sangat mirip dengan fungsi `printf()` dalam bahasa pemrograman C.
-   Argumen pertama (contoh: `'%s = %3.2f\n%5s = %3.2f\n'`) merupakan string yang berisikan format output. 
-   Argumen-argumen berikutnya merupakan nilai yang hendak di-*format* ketika `printf` menghasilkan *output*. 
-   Pada contoh, `'Pi'` ditampilkan ke layar terminal sebagai *string*, dengan pemformatan `%5s`. 
-   Kemudian, `3.14159` ditampilkan menjadi `3.14` dengan menggunakan format `%3.2f`. Format `%3.2f` berarti tulisan ditampilkan dalam `3` digit format bilangan *floating-point* (bilangan desimal) dengan `2` digit di belakang koma.

#### Mengatur Lebar String

```
Pi = 3.14
e = 2.72
```

Dua baris di atas akan terlihat lebih menarik apabila ditampilkan seperti berikut:

```
Pi = 3.14
 e = 2.72
```

atau

```
Pi = 3.14
e  = 2.72
```

Untuk melakukannya, Anda dapat menggunakan format `%s` pada `printf` dengan menyertakan *modifier* seperti berikut.

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2"><code class="language-bash">printf '%2s = %3.2f\n%2s = %3.2f\n' 'Pi' 3.14159 'e' 2.71828
Pi = 3.14
 e = 2.72</code></pre>

atau

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2"><code class="language-bash">printf '%-2s = %3.2f\n%-2s = %3.2f\n' 'Pi' 3.14159 'e' 2.71828
Pi = 3.14
e  = 2.72</code></pre>

Dapat disimpulkan bahwa:
 
-   `%2s` membuat string menjadi (minimum) selebar 2 karakter. String `Pi` dan `e` ditampilkan rata kanan.
-   `%-2s` membuat string menjadi (minimum) selebar 2 karakter. String `Pi` dan `e` ditampilkan rata kanan.

#### Membuat Garis Horizontal

Anda bisa membuat garis dengan menuliskan karakter `-` secara berulang, seperti berikut.

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2,4"><code class="language-bash">printf "%s\n" -------------------------
-------------------------
echo -------------------------
-------------------------</code></pre>

Namun, ada cara yang lebih ringkas, yaitu dengan memanfaatkan perintah `tr`.

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2,4"><code class="language-bash">printf "%25s\n" | tr " " -
-------------------------</code></pre>

**Penjelasan:**

Untuk mempermudah, kita pisahkan menjadi dua bagian terlebih dahulu (dipisahkan oleh ` | `). Setelah kita bahas apa itu `|`, barulah kita gabungkan.

-   `printf "%25s\n"`

    Seperti yang telah dibahas sebelumnya, ini berarti kita menyiapkan tempat untuk tulisan selebar 25 karakter dengan diletakkan rata kanan. Lalu apa yang ditulis? Jika perintahnya `printf "%25s\n" Testing`, maka sudah jelas hasilnya akan menjadi tulisan <code> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Testing</code>. Kalau masih penasaran, langsung dicoba saja.

    <pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="2,4"><code class="language-bash">printf "%25s\n"
    <span style="background: #bbb">                        &nbsp;</span>
    printf "%25s\n"
    <span style="background: #bbb">                  Testing</span></code></pre>

    Ternyata `printf "%25s\n"` tanpa argumen tambahan memberikan output berupa sebaris tulisan berisi karakter spasi (` `) sepanjang 25 karakter.

-   `tr " " -`

    `tr` dapat digunakan untuk mengganti karakter tertentu dalam string input menjadi karakter lain. Misalnya, `tr " " -` digunakan untuk mengganti karakter spasi ` ` dalam string input menjadi karakter `-`.

-   `|`

    Ingat apa yang terjadi ketika Anda menjalankan 
    `echo "Saya sedang belajar pemrograman" > ngapain.txt` 
    pada pembahasan tentang `echo`? 

    Output dari menjalankan perintah `echo "Saya sedang belajar pemrograman"` dimasukkan ke dalam file `ngapain.txt`. Dengan kata lain, output tersebut menjadi input untuk penulisan isi file `ngapain.txt`. 

    Atau, output dari perintah di sisi kiri `>` menjadi input untuk file yang namanya ditulis di sisi kanan `>`.

    Hampir serupa dengan `>`, pada `|`:
    output dari perintah di sisi kiri `|` menjadi input untuk perintah di sisi kanan `
    
-   `printf "%25s\n" | tr " " -`

    -   Perintah di sisi kiri `|` memiliki output berupa spasi selebar 25 karakter (`<code> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `). Hasil dari perintah tersebut menjadi output untuk perintah di sisi kanan.
    -   Perintah di sisi kanan `|` menerima input. Kemudian, semua karakter spasi pada input dirubah menjadi karakter minus. Hasil perubahan tersebutlah yang kemudian ditampilkan ke layar, `-------------------------`.
    

#### Membuat Tabel

Setelah mempelajari materi di atas, kin Anda dapat memformat teks sehingga dapat tampil rapi sebagai sebuah tabel.

Buat file dengan nama `tabel`, kemudian masukkan kode berikut.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-bash .line-numbers}
#!/bin/bash
format_baris_judul=&quot;| %-12s | %24s |\n&quot;
format_baris_data=&quot;| %-12s | %24.2f |\n&quot;
printf &quot;/%41s\\\\\n&quot; | tr &quot; &quot; -
printf &quot;$format_baris_judul&quot; &quot;Planet&quot; &quot;Jarak Orbit (Juta km)&quot;
printf &quot;$format_baris_judul&quot; | tr &quot; &quot; -
printf &quot;$format_baris_judul&quot; &quot;Merkurius&quot; &quot;57,91&quot;   &quot;Venus&quot;    &quot;108,21&quot;  \
                             &quot;Bumi&quot;      &quot;149,60&quot;  &quot;Mars&quot;     &quot;227,94&quot;  \
                             &quot;Jupiter&quot;   &quot;778,41&quot;  &quot;Saturnus&quot; &quot;1426,72&quot; \
                             &quot;Uranus&quot;    &quot;2870,97&quot; &quot;Neptunus&quot; &quot;4498,25&quot;
printf &quot;\\%41s/\n&quot; | tr &quot; &quot; -
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Simpan file, dan jalankan.

<pre class="command-line" data-user="mi" data-host="belajarpemrograman" data-output="3-14"><code class="language-bash">chmod u+x tabel
./tabel
/-----------------------------------------\
| Planet       |    Jarak Orbit (Juta km) |
|--------------|--------------------------|
| Merkurius    |                    57,91 |
| Venus        |                   108,21 |
| Bumi         |                   149,60 |
| Mars         |                   227,94 |
| Jupiter      |                   778,41 |
| Saturnus     |                  1426,72 |
| Uranus       |                  2870,97 |
| Neptunus     |                  4498,25 |
\-----------------------------------------/</code></pre>

------------------------------------------------------------------------

Referensi: {#referensi}
-----------------------

-   [Bash Academy - Inception (What is bash, and where does it live?)](http://guide.bash.academy/inception/)
-   [The printf Command](http://wiki.bash-hackers.org/commands/builtin/printf)

[Belajar Pemrograman Bash Shell di Linux 1: Pengenalan]: https://belajarpemrograman.org/belajar-pemrograman-bash-shell-di-linux-1-pengenalan/
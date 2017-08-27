---
ID: 238
post_title: Catatan Belajar Bahasa Pemrograman Java
author: Muhammad Ikhsan
post_date: 2017-02-06 11:31:16
post_excerpt: >
  Tulisan ini berisikan catatan-catatan yg
  bersifat sebagai referensi mengenai
  bahasa pemrograman Java yg dikumpulkan
  oleh penulis sembari mempelajarinya.
  Tujuan utamanya, sebenarnya untuk
  catatan pribadi, agar lebih mudah dalam
  me-review. Namun, penulis berharap
  catatan ini juga dapat bermanfaat bagi
  orang lain.
layout: post
permalink: >
  http://belajarpemrograman.org/catatan-belajar-bahasa-pemrograman-java/
published: true
---
Tulisan ini berisikan catatan-catatan yg bersifat sebagai referensi mengenai bahasa pemrograman Java yg dikumpulkan oleh penulis sembari mempelajarinya. Tujuan utamanya, sebenarnya untuk catatan pribadi, agar lebih mudah dalam me-<em>review</em>. Namun, penulis berharap catatan ini juga dapat bermanfaat bagi orang lain.
<h2>Tentang Java</h2>
<ul>
 	<li><em>Object-oriented (class based)</em>, penulisan program di Java mengharuskan pembuatan kelas dan objek. Meskipun kita hanya ingin membuat sebuah program Hello World, kita harus membuatkan sebuah kelas untuknya.</li>
 	<li><em>Case-sensitive</em>, maksudnya huruf besar dan huruf kecil dalam penulisan kode berpengaruh. Sehingga <code>helloWorld</code>, <code>HelloWorld</code>, <code>helloworld</code>, maupun <code>HELLOWORLD</code> dianggap berbeda.</li>
 	<li><em>Statically-typed</em>, maksudnya setiap variabel di Java harus dideklarasikan tipe variabelnya terlebih dahulu sebelum variabel tersebut dapat digunakan.</li>
</ul>
<h2>Hello World!</h2>
<h4><strong>File: <code>HelloWorld.java</code></strong></h4>
<pre><code class="language-java line-numbers">class HelloWorld {
  public static void main (String[] args) {
    System.out.println("Hello World!");
  }
}</code></pre>
<h4><strong>Catatan</strong></h4>
<ul>
 	<li>Nama file harus memiliki ekstensi <code>.java</code></li>
 	<li>Nama kelas <em>(class)</em> <code>HelloWorld</code> dan nama file harus sama, <code>HelloWorld</code>.java</li>
 	<li>Sebagai titik awal jalannya sebuah program <em>(entry point)</em>, sebuah kelas harus memiliki metode <code>main</code>.</li>
 	<li>Metode <em>(method) </em>main harus dideklarasikan dengan <code>public static void main(String[] args)</code>.
<em>(<code>String args[]</code> dapat digunakan untuk menggantikan <code>String[] args</code>.)</em></li>
</ul>
<h4><strong>Cara menjalankannya</strong></h4>
<ul>
 	<li>Untuk mengkompilasi <em>(compile)</em> kode program Java melalui <em>command prompt</em> atau <em>console</em>, gunakan perintah
<pre>javac HelloWorld.java</pre>
<code>HelloWorld.java</code> merupakan nama file yg berisikan kode program Java yg akan dikompilasi.</li>
 	<li>Setelah kompilasi menggunakan <code>javac</code> seperti di atas, akan tercipta sebuah file baru dengan nama <code>HelloWorld.class</code> yg berisikan <em>bytecode</em> Java. File <em>bytecode class</em> (<code>HelloWorld.class</code>) tersebut dapat kita jalankan melalui JVM (Java Virtual Machine) menggunakan perintah berikut
<pre>java HelloWorld</pre>
Tanpa ekstensi <code>.class</code>.</li>
</ul>
<h4>Diagram</h4>
Proses mulai dari penulisan kode program sampai eksekusi program dapat digambarkan ke dalam diagram berikut.

<img class="aligncenter wp-image-305 size-full" src="http://belajarpemrograman.org/wp-content/uploads/2017/02/editor-compiler-jvm.jpg" alt="Urutan proses dari penulisan kode sampai eksekusi program java - Belajar Pemrograman Java" width="743" height="196" />
<h2>Komentar</h2>
Komentar tidak akan diproses oleh <em>compiler</em>.
<ul>
 	<li>Sebaris komentar dapat ditulis dengan diawali <code>//</code>.
<pre>// Keseluruhan satu baris ini adalah komentar</pre>
</li>
 	<li>Komentar bisa juga ditulis dengan diapit oleh <code>/*</code> dan <code>*/</code>.
<pre>/* Hanya tulisan yg terapit inilah yg merupakan komentar */

/**
 * Ini juga merupakan sebuah komentar,
 * karena pada dasarnya, tulisan ini juga diapit oleh /* dan */
 */</pre>
</li>
</ul>
<h2>Tipe Data Primitif</h2>
Sebuah tipe data merupakan metode pengklasifikasian nilai dari sebuah variabel. Dengan tipe data, kita dapat mengetahui nilai apa yg dapat disimpan dalam sebuah variabel dan operasi apa saja yg dapat diterapkan pada variabel. Tipe data primitif di Java merupakan tipe data dasar yang disediakan oleh Java.
<table style="width: 825.767px">
<thead>
<tr style="height: 24px">
<th style="height: 24px;width: 74px">Tipe Data</th>
<th style="height: 24px;width: 107px">Ukuran Memori</th>
<th style="height: 24px;width: 621.767px">Catatan</th>
</tr>
</thead>
<tbody>
<tr style="height: 25px">
<td style="height: 25px;width: 74px"><code>byte</code></td>
<td style="height: 25px;width: 107px">1 byte</td>
<td style="height: 25px;width: 621.767px">Rentang nilai: -128 sampai 127</td>
</tr>
<tr style="height: 25.6833px">
<td style="height: 25.6833px;width: 74px"><code>short</code></td>
<td style="height: 25.6833px;width: 107px">2 byte</td>
<td style="height: 25.6833px;width: 621.767px">Rentang nilai: -32.768 sampai 32.767</td>
</tr>
<tr style="height: 25px">
<td style="height: 25px;width: 74px"><code>int</code></td>
<td style="height: 25px;width: 107px">4 byte</td>
<td style="height: 25px;width: 621.767px">Rentang nilai: -2.147.483.648 sampai 2.147.483.647</td>
</tr>
<tr style="height: 49px">
<td style="height: 49px;width: 74px"><code>long</code></td>
<td style="height: 49px;width: 107px">8 byte</td>
<td style="height: 49px;width: 621.767px">Rentang nilai: -9.223.372.036.854.775.808 sampai 9.223.372.036.854.775.807.
Literal-nya diakhiri dengan <code>L</code>, contoh <code>11L</code>.</td>
</tr>
<tr style="height: 25px">
<td style="height: 25px;width: 74px"><code>float</code></td>
<td style="height: 25px;width: 107px">4 byte</td>
<td style="height: 25px;width: 621.767px">Rentang nilai: kurang lebih dari 1,18 x 10<sup>-38</sup> sampai 3.4 x 10<sup>38</sup>. Literalnya diakhiri dengan <code>F</code>, contoh <code>0.5F</code>.</td>
</tr>
<tr style="height: 25px">
<td style="height: 25px;width: 74px"><code>double</code></td>
<td style="height: 25px;width: 107px">8 byte</td>
<td style="height: 25px;width: 621.767px">Rentang nilai: kurang lebih dari 2,23 x 10<sup>-308</sup> sampai 1.80 x 10<sup>308</sup>.</td>
</tr>
<tr style="height: 25px">
<td style="height: 25px;width: 74px"><code>boolean</code></td>
<td style="height: 25px;width: 107px"></td>
<td style="height: 25px;width: 621.767px">Memiliki nilai <code>true</code> atau <code>false</code></td>
</tr>
<tr style="height: 25px">
<td style="height: 25px;width: 74px"><code>char</code></td>
<td style="height: 25px;width: 107px">2 byte</td>
<td style="height: 25px;width: 621.767px">Rentang nilai: <code>'\u0000'</code> (atau 0) sampai <code>'\uffff'</code> (atau 65535). Yaitu sebuah 16-bit merepresentasikan karakter Unicode.</td>
</tr>
</tbody>
</table>
<ul>
 	<li>Field dari sebuah kelas, jika tidak diinisialisasi dengan sebuah nilai, maka akan memiliki nilai default yang ditentukan oleh compiler. Nilai default tersebut, secara umum, adalah 0 atau null tergantung tipe datanya.</li>
 	<li>Variabel lokal harus diinisialisasi dengan sebuah nilai terlebih dahulu sebelum digunakan.</li>
 	<li>Asal-muasal rentang nilai tipe data <code>byte</code>, [-128, 127].
<ul>
 	<li>1 byte = 8 bit</li>
 	<li>8 bit biner (basis 2) dapat digunakan untuk menghasilkan bilangan desimal (basis 10) sebanyak 256 angka. (256 didapat dari 2<sup>8</sup>). Sehingga 1 byte (= 8 bit) dapat merepresentasikan bilangan desimal dalam rentang 0 - 255. Dengan algoritma tertentu, 8 digit biner tersebut juga dapat turut merepresentasikan bilangan bulat negatif dengan rentang bilangan -128 - 127 (seperti pada tipe data <code>byte</code>). Yg mana jumlah hitungan bilangan yg direpresentasikannya tetap 256.</li>
</ul>
</li>
</ul>
<h2>Literal</h2>
Literal merepresentasikan suatu nilai pada program. Misalnya, <code>354</code> dapat digunakan untuk merepresentasikan nilai bilangan "tiga ratus lima puluh empat" dalam kode Java untuk variabel dengan tipe <code>int</code>.
<h4>Literal Integer (Bilangan Bulat)</h4>
<ul>
 	<li><strong>Literal <code>long</code></strong>
Integer literal dengan tipe data <code>long</code> dituliskan dengan akhiran karakter <code>L</code> atau <code>l</code>. Agar mudah dibaca sebaiknya gunakan akhiran <code>L</code>, menggunakan huruf kapital.</li>
 	<li><strong>Literal <code>int</code></strong>
Jika tidak menggunakan akhiran <code>L</code> atau <code>l</code>, maka dianggap sebagai <code>int</code>.</li>
 	<li>Nilai untuk tipe data bilangan bulat <code>byte</code>, <code>short</code>, <code>int</code>, dan <code>long</code> dapat dibuat menggunakan literal <code>int</code>. Jadi, kita bisa memasukkan nilai ke dalam variabel dengan tipe data <code>long</code> dengan literal <code>int</code>, yaitu tanpa menambahkan <code>L</code> atau <code>l</code> setelah nilai bilangan. Lalu, apa bedanya antara yg menggunakan <code>L</code> dengan yg tidak?</li>
 	<li>Mengekspresikan literal bilangan bulat dapat ditulis dalam sistem bilangan berikut:
<ul>
 	<li>Biner, sistem bilangan basis 2, yang digitnya terdiri dari 0 dan 1. Gunakan prefiks <code>0b</code> untuk menunjukkan nilai biner.</li>
 	<li>Desimal, sistem bilangan basis 10, yang digitnya terdiri dari 0, 1, 2, 3, 4, 5, 6, 7, 8, 9.</li>
 	<li>Heksadesimal, sistem bilangan basis 16, yang digitnya terdiri dari 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F. Gunakan prefiks <code>0x</code> untuk menunjukkan nilai heksadesimal.</li>
</ul>
</li>
</ul>
<h4>Literal Floating-Point</h4>
<ul>
 	<li>Literal <code>float</code>, diakhiri dengan <code>F</code> atau <code>f</code>.</li>
 	<li>Literal <code>double</code>, secara opsional diakhiri dengan <code>D</code> atau <code>d</code>.</li>
</ul>
<h4>Literal Boolean</h4>
<ul>
 	<li><code>true</code> untuk menunjukkan nilai boolean true</li>
 	<li><code>false</code> untuk menunjukkan nilai boolean false</li>
</ul>
<h4>Literal Karakter dan String</h4>
<ul>
 	<li>Literal untuk memuat tipe data <code>char</code> maupun <code>String</code> dapat mengandung karakter Unicode (UTF-16) apapun.</li>
 	<li>Escape sequence <code>\u</code> dapat digunakan untuk menyatakan karakter Unicode. Misal: <code>\u304f</code> untuk menyatakan karakter ku dalam penulisan hiragana dalam Bahasa Jepang.</li>
 	<li>Literal untuk tipe data <code>char</code> diapit di antara <code>'</code> dan <code>'</code>.</li>
 	<li>Literal untuk tipe data <code>String</code> diapit di antara <code>"</code> dan <code>"</code>.</li>
</ul>
<h2>Escape Sequence</h2>
<table>
<thead>
<tr>
<th>Escape Sequence</th>
<th>Merepresentasikan</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>\t</code></td>
<td>Tab</td>
</tr>
<tr>
<td><code>\b</code></td>
<td>Backspace</td>
</tr>
<tr>
<td><code>\n</code></td>
<td>Baris baru (new line)</td>
</tr>
<tr>
<td><code>\r</code></td>
<td>Carriage return</td>
</tr>
<tr>
<td><code>\f</code></td>
<td>Formfeed</td>
</tr>
<tr>
<td><code>\'</code></td>
<td>Petik satu (<code>'</code>)</td>
</tr>
<tr>
<td><code>\"</code></td>
<td>Petik dua (<code>"</code>)</td>
</tr>
<tr>
<td><code>\\</code></td>
<td>Backslash (<code>\</code>)</td>
</tr>
</tbody>
</table>
<h4>Contoh Penggunaan</h4>
Untuk menampilkan tulisan <code>"Makasih ya..!", kata Ambar.</code>
<pre>System.out.println("\"Makasih ya...!\", kata Ambar.");</pre>
<h2>Deklarasi dan Pernyataan Assignment</h2>
<ul>
 	<li>Mendeklarasikan sebuah variabel dengan tipe data <code>int</code> dan nama variabel <code>hargaA</code>.
<pre>int hargaA;</pre>
</li>
 	<li>Dengan menggunakan pernyataan assignment <em>(assignment statement)</em>, masukkan nilai <code>24</code> ke dalam variabel <code>hargaA</code>.
<pre>hargaA = 10000;</pre>
</li>
 	<li>Mendeklarasikan variabel sekaligus dengan menentukan nilai variabel yang disimpannya.
<pre>int hargaB = 5000;</pre>
</li>
 	<li>Mendeklarasikan beberapa variabel sekaligus. Variabel <code>uangDibayarkan</code> sekalian diberikan nilai.
<pre>int uangDibayarkan = 20000, 
    totalHarga, 
    kembalian;</pre>
</li>
 	<li>Memasukkan nilai hasil penjumlahan dan pengurangan menggunakan operator (<code>+</code> dan <code>-</code>) ke dalam variabel.
<pre>totalHarga = hargaA + hargaB;
kembalian = uangDibayarkan - totalHarga;</pre>
</li>
</ul>
<h2>Konvensi Penamaan</h2>
<table>
<thead>
<tr style="height: 24px">
<th style="height: 24px">Penamaan</th>
<th style="height: 24px">Konvensi</th>
<th style="height: 24px">Contoh</th>
</tr>
</thead>
<tbody>
<tr style="height: 48px">
<td style="height: 48px">Kelas dan interface</td>
<td style="height: 48px">Setiap kata diawali dengan huruf kapital</td>
<td style="height: 48px"><code>Chat</code>, <code>SimpleChat</code></td>
</tr>
<tr style="height: 48px">
<td style="height: 48px">Objek dan variabel</td>
<td style="height: 48px">Diawali dengan huruf kecil. Setiap kata berikutnya diawali dengan huruf kapital.</td>
<td style="height: 48px"><code>message</code>, <code>newMessage</code></td>
</tr>
<tr style="height: 24.5667px">
<td style="height: 24.5667px">Method</td>
<td style="height: 24.5667px">Sama seperti konvensi untuk objek dan variabel</td>
<td style="height: 24.5667px"><code>getMessages</code></td>
</tr>
<tr style="height: 24px">
<td style="height: 24px">Konstanta</td>
<td style="height: 24px">Gunakan huruf kapital semua. Setiap kata dipisahkan dengan <code>_</code></td>
<td style="height: 24px"><code>IMAGE_DIR</code>, <code>PORT</code></td>
</tr>
</tbody>
</table>
<h2>Reserved Keyword</h2>
Reserved keywords, maksudnya Kita tidak boleh menggunakannya sebagai nama <em>identifier</em>, seperti nama kelas, nama variable, atau nama method.
<table border="0" summary="" width="100%" cellpadding="0">
<tbody>
<tr style="height: 25px">
<td style="height: 25px" align="left" width="20%"><code>abstract</code></td>
<td style="height: 25px" align="left" width="20%"><code>continue</code></td>
<td style="height: 25px" align="left" width="20%"><code>for</code></td>
<td style="height: 25px" align="left" width="20%"><code>new</code></td>
<td style="height: 25px" align="left" width="20%"><code>switch</code></td>
</tr>
<tr style="height: 25px">
<td style="height: 25px" width="20%"><code>assert</code></td>
<td style="height: 25px" align="left" width="20%"><code>default</code></td>
<td style="height: 25px" align="left" width="20%"><code>goto</code></td>
<td style="height: 25px" align="left" width="20%"><code>package</code></td>
<td style="height: 25px" align="left" width="20%"><code>synchronized</code></td>
</tr>
<tr style="height: 25.0166px">
<td style="height: 25.0166px" align="left" width="20%"><code>boolean</code></td>
<td style="height: 25.0166px" align="left" width="20%"><code>do</code></td>
<td style="height: 25.0166px" align="left" width="20%"><code>if</code></td>
<td style="height: 25.0166px" align="left" width="20%"><code>private</code></td>
<td style="height: 25.0166px" align="left" width="20%"><code>this</code></td>
</tr>
<tr style="height: 25px">
<td style="height: 25px" align="left" width="20%"><code>break</code></td>
<td style="height: 25px" align="left" width="20%"><code>double</code></td>
<td style="height: 25px" align="left" width="20%"><code>implements</code></td>
<td style="height: 25px" align="left" width="20%"><code>protected</code></td>
<td style="height: 25px" align="left" width="20%"><code>throw</code></td>
</tr>
<tr style="height: 25px">
<td style="height: 25px" align="left" width="20%"><code>byte</code></td>
<td style="height: 25px" align="left" width="20%"><code>else</code></td>
<td style="height: 25px" align="left" width="20%"><code>import</code></td>
<td style="height: 25px" align="left" width="20%"><code>public</code></td>
<td style="height: 25px" align="left" width="20%"><code>throws</code></td>
</tr>
<tr style="height: 25px">
<td style="height: 25px" align="left" width="20%"><code>case</code></td>
<td style="height: 25px" align="left" width="20%"><code>enum</code></td>
<td style="height: 25px" align="left" width="20%"><code>instanceof</code></td>
<td style="height: 25px" align="left" width="20%"><code>return</code></td>
<td style="height: 25px" align="left" width="20%"><code>transient</code></td>
</tr>
<tr style="height: 25px">
<td style="height: 25px" align="left" width="20%"><code>catch</code></td>
<td style="height: 25px" align="left" width="20%"><code>extends</code></td>
<td style="height: 25px" align="left" width="20%"><code>int</code></td>
<td style="height: 25px" align="left" width="20%"><code>short</code></td>
<td style="height: 25px" align="left" width="20%"><code>try</code></td>
</tr>
<tr style="height: 25px">
<td style="height: 25px" align="left" width="20%"><code>char</code></td>
<td style="height: 25px" align="left" width="20%"><code>final</code></td>
<td style="height: 25px" align="left" width="20%"><code>interface</code></td>
<td style="height: 25px" align="left" width="20%"><code>static</code></td>
<td style="height: 25px" align="left" width="20%"><code>void</code></td>
</tr>
<tr style="height: 25px">
<td style="height: 25px" align="left" width="20%"><code>class</code></td>
<td style="height: 25px" align="left" width="20%"><code>finally</code></td>
<td style="height: 25px" align="left" width="20%"><code>long</code></td>
<td style="height: 25px" align="left" width="20%"><code>strictfp</code></td>
<td style="height: 25px" align="left" width="20%"><code>volatile</code></td>
</tr>
<tr style="height: 25px">
<td style="height: 25px" align="left" width="20%"><code>const</code></td>
<td style="height: 25px" align="left" width="20%"><code>float</code></td>
<td style="height: 25px" align="left" width="20%"><code>native</code></td>
<td style="height: 25px" align="left" width="20%"><code>super</code></td>
<td style="height: 25px" align="left" width="20%"><code>while</code></td>
</tr>
</tbody>
</table>
Keyword <code>const</code> dan <code>goto</code> termasuk dalam <em>reserved keywords</em> meskipun keduanya tidak digunakan di Java.
<h2>Logika Percabangan/Pemilihan</h2>
<h4>Pernyataan if</h4>
<pre><code class="language-java line-numbers">// Absolut dari x
if (x &lt; 0) {
  x = -x;
}</code></pre>
<h4>Pernyataan if-else</h4>
<pre><code class="language-java line-numbers">// Mencari nilai maksimum dari x dan y
if (x &gt; y) {
  max = x;
} else {
  max = y;
}</code></pre>
<h4>Pernyataan switch</h4>
<pre><code class="language-java line-numbers">// Menampilkan nama hari berdasarkan representasinya dalam angka (0 - 6)
// Dimulai dari `0` sebagai Minggu sampai `6` sebagai Sabtu
switch (day) {
  case 0:
    System.out.println("Minggu");
    break;
  case 1:
    System.out.println("Senin");
    break;
  case 2:
    System.out.println("Selasa");
    break;
  case 3:
    System.out.println("Rabu");
    break;
  case 4:
    System.out.println("Kamis");
    break;
  case 5:
    System.out.println("Jumat");
    break;
  default:
    System.out.println("Sabtu");
    break;
}</code></pre>
<h2>Logika Pengulangan</h2>
<h4>Pernyataan while</h4>
<pre><code class="language-java line-numbers">// Menghitung hasil penjumlahan dari 1 + 2 + 3 + ... + n selama hasilnya kurang dari 50
int i = 1,
    sum = 0;
while ((sum + i) &lt; 50) {
  sum = sum + i;
  i++;
}</code></pre>
<h4>Pernyataan for</h4>
<pre><code class="language-java line-numbers">// Menghitung hasil penjumlahan dari 1 + 2 + 3 + ... + n
int sum = 0;
int n = 10;
for (int i = 1; i &lt;= n; i++) {
  sum = sum + i;
}</code></pre>
<h4>Pernyataan do-while</h4>
<pre><code class="language-java line-numbers">/** 
 * Menampilkan tulisan `Hello world!` sebanyak minimal sekali.
 * Berulang-ulang tampilkan tulisan `Hello World!` selama bilangan acak
 * yang dihasilkan oleh `Math.random() * 10 + 1` kurang dari 8
 */
double random;
do {
  System.out.println("Hello World!");
  random = Math.random() * 10 + 1;
} while (random &lt; 8);
</code></pre>
<h2>Java Enum</h2>
Enum digunakan untuk mendefinisikan daftar konstanta, untuk melambangkan nilai-nilai tetap yang saling berkaitan. Misalnya, dalam pembuatan game, daripada kita menyebut tingkat kesulitan game dengan nilai 1, 2, 3 dari yang termudah hingga yang tersulit, akan lebih mudah jika kita menyebutnya dengan EASY, MEDIUM, HARD. Contoh:
<pre><code class="language-java line-numbers">public enum Difficulty {
  EASY,
  MEDIUM,
  HARD
}
</code></pre>
Selanjutnya, untuk merujuk pada tinggak kesulitan game tertentu pada enum Difficulty, dapat menggunakan:
<pre><code class="language-java">Difficulty difficulty = Difficulty.MEDIUM;</code></pre>
<h2>Package Standar</h2>
<table>
<tbody>
<tr>
<td><code>java.applet</code></td>
<td>Applet, yaitu program Java yg dijalankan langsung di sebuah halaman website</td>
</tr>
<tr>
<td><code>java.awt</code></td>
<td>Grafik dan GUI</td>
</tr>
<tr>
<td><code>java.beans</code></td>
<td>Dukungan untuk komponen yang berdasar pada JavaBeans</td>
</tr>
<tr>
<td><code>java.io</code></td>
<td>Input dan output</td>
</tr>
<tr>
<td><code>java.lang</code></td>
<td>Fungsionalitas dasar bahasa pemrograman java dan tipe data dasar. Package ini dapat digunakan tanpa perlu memanggilnya menggunakan <code>import</code>.</td>
</tr>
<tr>
<td><code>java.math</code></td>
<td>Aritmetika dengan beragam presisi angka</td>
</tr>
<tr>
<td><code>java.net</code></td>
<td>Networking</td>
</tr>
<tr>
<td><code>java.nio</code></td>
<td>Non-blocking Input/Output</td>
</tr>
<tr>
<td><code>java.rmi</code></td>
<td>RMI (Remote Method Invocation), yaitu sebuah sistem yang mengijinkan sebuah objek yang berjalan pada sebuah JVM (Java Virtual Machine) untuk memanggil sebuah objek yang berjalan di JVM yang berbeda.</td>
</tr>
<tr>
<td><code>java.security</code></td>
<td>Dukungan keamanan</td>
</tr>
<tr>
<td><code>java.sql</code></td>
<td>Dukungan database</td>
</tr>
<tr>
<td><code>java.text</code></td>
<td>Internasionalisasi pemformatan teks dan angka</td>
</tr>
<tr>
<td><code>java.time</code></td>
<td>Tanggal, waktu, durasi, zona waktu, dll.</td>
</tr>
<tr>
<td><code>java.util</code></td>
<td>Berbagai utilitas, seperti dukungan struktur data, regular expression, logging, dll.</td>
</tr>
</tbody>
</table>
&nbsp;

<hr />

<h2>Referensi</h2>
<ul>
 	<li><a href="https://docs.oracle.com/javase/8/docs/" target="_blank">https://docs.oracle.com/javase/8/docs/</a></li>
 	<li><a href="https://dzone.com/refcardz/core-java" target="_blank">https://dzone.com/refcardz/core-java</a></li>
 	<li><a href="http://introcs.cs.princeton.edu/java/11cheatsheet/" target="_blank">http://introcs.cs.princeton.edu/java/11cheatsheet/</a></li>
</ul>
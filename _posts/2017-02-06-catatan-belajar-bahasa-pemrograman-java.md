---
ID: 238
post_title: >
  Panduan Ringkas Belajar Bahasa
  Pemrograman Java
author: Muhammad Ikhsan
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
post_date: 2017-02-06 11:31:16
---
Tulisan ini berisikan catatan-catatan yg bersifat sebagai referensi mengenai bahasa pemrograman Java yg dikumpulkan oleh penulis sembari mempelajarinya. Tujuan awalnya, sebenarnya untuk catatan pribadi, agar lebih mudah dalam me-*review*. Namun, penulis berharap catatan ini juga dapat bermanfaat bagi orang lain.

## Tentang Java {#tentang-java}

-   *Object-oriented (class based)*, penulisan program di Java mengharuskan pembuatan kelas dan objek. Meskipun kita hanya ingin membuat sebuah program Hello World, kita harus membuatkan sebuah kelas untuknya.
-   *Case-sensitive*, maksudnya huruf besar dan huruf kecil dalam penulisan kode berpengaruh. Sehingga `helloWorld`, `HelloWorld`, `helloworld`, maupun `HELLOWORLD` dianggap beda.
-   *Statically-typed*, maksudnya setiap variabel di Java harus dideklarasikan tipe variabelnya terlebih dahulu dapat digunakan.

## Hello World! {#hello-world}

#### File `HelloWorld.java`

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
class HelloWorld {
  public static void main (String[] args) {
    System.out.println(&quot;Hello World!&quot;);
  }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#### Catatan

-   Nama file harus memiliki ekstensi `.java`
-   Nama kelas *(class)* `HelloWorld` dan nama file harus sama, `HelloWorld`.java
-   Sebagai titik awal jalannya sebuah program *(entry point)*, sebuah kelas harus memiliki metode `main`.
-   Metode *(method)* `main` harus dideklarasikan dengan `public static void main(String[] args)`. Atau `String args[]` dapat digunakan untuk menggantikan `String[] args`.

#### Cara menjalankan `HelloWorld.java`

-   Untuk mengkompilasi *(compile)* kode program Java melalui *command prompt* atau *console*, gunakan perintah

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    javac HelloWorld.java
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    `HelloWorld.java` merupakan nama file yg berisikan kode program Java yg akan dikompilasi.

-   Setelah kompilasi menggunakan `javac` seperti di atas, akan tercipta sebuah file baru dengan nama `HelloWorld.class` yg berisikan *bytecode* Java. File *bytecode class* (`HelloWorld.class`) tersebut dapat kita jalankan melalui JVM (Java Virtual Machine) menggunakan perintah berikut

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    java HelloWorld
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    Tanpa ekstensi `.class`.

#### Diagram

Proses mulai dari penulisan kode program sampai eksekusi program dapat digambarkan ke dalam diagram berikut.
<img class="aligncenter wp-image-305 size-full" src="http://belajarpemrograman.org/wp-content/uploads/2017/02/editor-compiler-jvm.jpg" alt="Urutan proses dari penulisan kode sampai eksekusi program java - Belajar Pemrograman Java" width="743" height="196" />

## Komentar {#komentar}

Komentar tidak akan diproses oleh `compiler`.

-   Sebaris komentar dapat ditulis dengan diawali `//`.

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    // Keseluruhan satu baris ini adalah komentar
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Komentar bisa juga ditulis dengan diapit oleh `/*` dan `*/`.

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    /* Hanya tulisan yg terapit inilah yg merupakan komentar */

    /**
     * Ini juga merupakan sebuah komentar,
     * karena pada dasarnya, tulisan ini juga diapit oleh /* dan */
     */
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Tipe Data Primitif {#tipe-data-primitif}

Sebuah tipe data merupakan metode pengklasifikasian nilai dari sebuah variabel. Dengan tipe data, kita dapat mengetahui nilai apa yg dapat disimpan dalam sebuah variabel dan operasi apa saja yg dapat diterapkan pada variabel. Tipe data primitif di Java merupakan tipe data dasar yang disediakan oleh Java.

| Tipe Data | Ukuran Memori | Catatan                                                                                                                               |
|-----------|---------------|---------------------------------------------------------------------------------------------------------------------------------------|
| `byte`    | 1 byte        | Rentang nilai: -128 sampai 127                                                                                                        |
| `short`   | 2 byte        | Rentang nilai: -32.768 sampai 32.767                                                                                                  |
| `int`     | 4 byte        | Rentang nilai: -2.147.483.648 sampai 2.147.483.647                                                                                    |
| `long`    | 8 byte        | Rentang nilai: -9.223.372.036.854.775.808 sampai 9.223.372.036.854.775.807. Literal-nya diakhiri dengan `L`, contoh `11L`.            |
| `float`   | 4 byte        | Rentang nilai: kurang lebih dari 1,18 x 10<sup>-38</sup> sampai 3.4 x 10<sup>38</sup>. Literalnya diakhiri dengan `F`, contoh `0.5F`. |
| `double`  | 8 byte        | Rentang nilai: kurang lebih dari 2,23 x 10<sup>-308</sup> sampai 1.80 x 10<sup>308</sup>.                                             |
| `boolean` |               | Memiliki nilai `true` atau `false`                                                                                                    |
| `char`    | 2 byte        | Rentang nilai: `'\u0000'` (atau 0) sampai `'\uffff'` (atau 65535). Yaitu sebuah 16-bit merepresentasikan karakter Unicode.            |

-   Field dari sebuah kelas, jika tidak diinisialisasi dengan sebuah nilai, maka akan memiliki nilai default yang ditentukan oleh compiler. Nilai default tersebut, secara umum, adalah 0 atau null tergantung tipe datanya.
-   Variabel lokal harus diinisialisasi dengan sebuah nilai terlebih dahulu sebelum digunakan.
-   Asal-muasal rentang nilai tipe data `byte`, \[-128, 127\].
    -   1 byte = 8 bit
    -   8 bit biner (basis 2) dapat digunakan untuk menghasilkan bilangan desimal (basis 10) sebanyak 256 angka. (256 didapat dari 2<sup>8</sup>). Sehingga 1 byte (= 8 bit) dapat merepresentasikan bilangan desimal dalam rentang 0 - 255. Dengan algoritma tertentu, 8 digit biner tersebut juga dapat turut merepresentasikan bilangan bulat negatif dengan rentang bilangan -128 - 127 (seperti pada tipe data `byte`). Yg mana jumlah hitungan bilangan yg direpresentasikannya tetap 256.

## Literal {#literal}

Literal merepresentasikan suatu nilai pada program. Misalnya, `354` dapat digunakan untuk merepresentasikan nilai bilangan “tiga ratus lima puluh empat” dalam kode Java untuk variabel dengan tipe `int`.

#### Literal Integer (Bilangan Bulat) {#literal-integer-bilangan-bulat}

-   **Literal `long`** Integer literal dengan tipe data `long` dituliskan dengan akhiran karakter `L` atau `l`. Agar mudah dibaca sebaiknya gunakan akhiran `L`, menggunakan huruf kapital.
-   **Literal `int`** Jika tidak menggunakan akhiran `L` atau `l`, maka dianggap sebagai `int`.
-   Nilai untuk tipe data bilangan bulat `byte`, `short`, `int`, dan `long` dapat dibuat menggunakan literal `int`. Jadi, kita bisa memasukkan nilai ke dalam variabel dengan tipe data `long` dengan literal `int`, yaitu tanpa menambahkan `L` atau `l` setelah nilai bilangan. Lalu, apa bedanya antara yg menggunakan `L` dengan yg tidak?
-   Mengekspresikan literal bilangan bulat dapat ditulis dalam sistem bilangan berikut:
    -   Biner, sistem bilangan basis 2, yang digitnya terdiri dari 0 dan 1. Gunakan prefiks `0b` untuk menunjukkan nilai biner.
    -   Desimal, sistem bilangan basis 10, yang digitnya terdiri dari 0, 1, 2, 3, 4, 5, 6, 7, 8, 9.
    -   Heksadesimal, sistem bilangan basis 16, yang digitnya terdiri dari 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F. Gunakan prefiks `0x` untuk menunjukkan nilai heksadesimal.

#### Literal Floating-Point {#literal-floating-point}

-   Literal `float`, diakhiri dengan `F` atau `f`.
-   Literal `double`, secara opsional diakhiri dengan `D` atau `d`.

#### Literal Boolean {#literal-boolean}

-   `true` untuk menunjukkan nilai boolean true
-   `false` untuk menunjukkan nilai boolean false

#### Literal Karakter dan String {#literal-karakter-dan-string}

-   Literal untuk memuat tipe data `char` maupun `String` dapat mengandung karakter Unicode (UTF-16) apapun.
-   Escape sequence `\u` dapat digunakan untuk menyatakan karakter Unicode. Misal: `\u304f` untuk menyatakan karakter ku dalam penulisan hiragana dalam Bahasa Jepang.
-   Literal untuk tipe data `char` diapit di antara `'` dan `'`.
-   Literal untuk tipe data `String` diapit di antara `"` dan `"`.

## Escape Sequence {#escape-sequence}

| Escape Sequence | Merepresentasikan     |
|-----------------|-----------------------|
| `\t`            | Tab                   |
| `\b`            | Backspace             |
| `\n`            | Baris baru (new line) |
| `\r`            | Carriage return       |
| `\f`            | Formfeed              |
| `\'`            | Petik satu (`'`)      |
| `\"`            | Petik dua (`"`)       |
| `\\`            | Backslash (`\`)       |

#### Contoh Penggunaan {#contoh-penggunaan}

Untuk menampilkan tulisan `"Makasih ya..!", kata Ambar.`

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
System.out.println(&quot;\&quot;Makasih ya...!\&quot;, kata Ambar.&quot;);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Deklarasi dan Pernyataan Assignment {#deklarasi-dan-pernyataan-assignment}

-   Mendeklarasikan sebuah variabel dengan tipe data `int` dan nama variabel `hargaA`.

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    int hargaA;
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Dengan menggunakan pernyataan assignment *(assignment statement)*, masukkan nilai `24` ke dalam variabel `hargaA`.

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    hargaA = 10000;
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Mendeklarasikan variabel sekaligus dengan menentukan nilai variabel yang disimpannya.

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    int hargaB = 5000;
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Mendeklarasikan beberapa variabel sekaligus. Variabel `uangDibayarkan` sekalian diberikan nilai.

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    int uangDibayarkan = 20000, 
        totalHarga, 
        kembalian;
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   Memasukkan nilai hasil penjumlahan dan pengurangan menggunakan operator (`+` dan `-`) ke dalam variabel.

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    totalHarga = hargaA + hargaB;
    kembalian = uangDibayarkan - totalHarga;
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Konvensi Penamaan {#konvensi-penamaan}

| Penamaan            | Konvensi                                                                         | Contoh                  |
|---------------------|----------------------------------------------------------------------------------|-------------------------|
| Kelas dan interface | Setiap kata diawali dengan huruf kapital                                         | `Chat`, `SimpleChat`    |
| Objek dan variabel  | Diawali dengan huruf kecil. Setiap kata berikutnya diawali dengan huruf kapital. | `message`, `newMessage` |
| Method              | Sama seperti konvensi untuk objek dan variabel                                   | `getMessages`           |
| Konstanta           | Gunakan huruf kapital semua. Setiap kata dipisahkan dengan `_`                   | `IMAGE_DIR`, `PORT`     |

## Reserved Keyword {#reserved-keyword}

Reserved keywords, maksudnya Kita tidak boleh menggunakannya sebagai nama *identifier*, seperti nama kelas, nama variable, atau nama method.

|            |            |              |             |                |
|------------|------------|--------------|-------------|----------------|
| `abstract` | `continue` | `for`        | `new`       | `switch`       |
| `assert`   | `default`  | `goto`       | `package`   | `synchronized` |
| `boolean`  | `do`       | `if`         | `private`   | `this`         |
| `break`    | `double`   | `implements` | `protected` | `throw`        |
| `byte`     | `else`     | `import`     | `public`    | `throws`       |
| `case`     | `enum`     | `instanceof` | `return`    | `transient`    |
| `catch`    | `extends`  | `int`        | `short`     | `try`          |
| `char`     | `final`    | `interface`  | `static`    | `void`         |
| `class`    | `finally`  | `long`       | `strictfp`  | `volatile`     |
| `const`    | `float`    | `native`     | `super`     | `while`        |

Keyword `const` dan `goto` termasuk dalam *reserved keywords* meskipun keduanya tidak digunakan di Java.

## Logika Percabangan/Pemilihan {#logika-percabanganpemilihan}

#### Pernyataan if {#pernyataan-if}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
// Absolut dari x
if (x &lt; 0) {
  x = -x;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#### Pernyataan if-else {#pernyataan-if-else}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
// Mencari nilai maksimum dari x dan y
if (x &gt; y) {
  max = x;
} else {
  max = y;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#### Pernyataan switch {#pernyataan-switch}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
// Menampilkan nama hari berdasarkan representasinya dalam angka (0 - 6)
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
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Logika Pengulangan {#logika-pengulangan}

#### Pernyataan while {#pernyataan-while}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
// Menghitung hasil penjumlahan dari 1 + 2 + 3 + ... + n selama hasilnya kurang dari 50
int i = 1,
    sum = 0;
while ((sum + i) &lt; 50) {
  sum = sum + i;
  i++;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#### Pernyataan for {#pernyataan-for}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
// Menghitung hasil penjumlahan dari 1 + 2 + 3 + ... + n
int sum = 0;
int n = 10;
for (int i = 1; i &lt;= n; i++) {
  sum = sum + i;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#### Pernyataan do-while {#pernyataan-do-while}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
/**
 * Menampilkan tulisan `Hello world!` sebanyak minimal sekali.
 * Berulang-ulang tampilkan tulisan `Hello World!` selama bilangan acak
 * yang dihasilkan oleh `Math.random() * 10 + 1` kurang dari 8
 */
double random;
do {
  System.out.println(&quot;Hello World!&quot;);
  random = Math.random() * 10 + 1;
} while (random &lt; 8);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Java Enum {#java-enum}

Enum digunakan untuk mendefinisikan daftar konstanta, untuk melambangkan nilai-nilai tetap yang saling berkaitan. Misalnya, dalam pembuatan game, daripada kita menyebut tingkat kesulitan game dengan nilai 1, 2, 3 dari yang termudah hingga yang tersulit, akan lebih mudah jika kita menyebutnya dengan EASY, MEDIUM, HARD. Contoh:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
public enum Difficulty {
  EASY,
  MEDIUM,
  HARD
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Selanjutnya, untuk merujuk pada tinggak kesulitan game tertentu pada enum Difficulty, dapat menggunakan:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Difficulty difficulty = Difficulty.MEDIUM;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Package Standar {#package-standar}

|                 |                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `java.applet`   | Applet, yaitu program Java yg dijalankan langsung di sebuah halaman website                                                                                                                            |
| `java.awt`      | Grafik dan GUI                                                                                                                                                                                         |
| `java.beans`    | Dukungan untuk komponen yang berdasar pada JavaBeans                                                                                                                                                   |
| `java.io`       | Input dan output                                                                                                                                                                                       |
| `java.lang`     | Fungsionalitas dasar bahasa pemrograman java dan tipe data dasar. Package ini dapat digunakan tanpa perlu memanggilnya menggunakan `import`.                                                           |
| `java.math`     | Aritmetika dengan beragam presisi angka                                                                                                                                                                |
| `java.net`      | Networking                                                                                                                                                                                             |
| `java.nio`      | Non-blocking Input/Output                                                                                                                                                                              |
| `java.rmi`      | RMI (Remote Method Invocation), yaitu sebuah sistem yang mengijinkan sebuah objek yang berjalan pada sebuah JVM (Java Virtual Machine) untuk memanggil sebuah objek yang berjalan di JVM yang berbeda. |
| `java.security` | Dukungan keamanan                                                                                                                                                                                      |
| `java.sql`      | Dukungan database                                                                                                                                                                                      |
| `java.text`     | Internasionalisasi pemformatan teks dan angka                                                                                                                                                          |
| `java.time`     | Tanggal, waktu, durasi, zona waktu, dll.                                                                                                                                                               |
| `java.util`     | Berbagai utilitas, seperti dukungan struktur data, regular expression, logging, dll.                                                                                                                   |

--------------------------------------------------------------------------

## Referensi {#referensi}

-   [https://docs.oracle.com/javase/8/docs](https://docs.oracle.com/javase/8/docs)
-   [https://dzone.com/refcardz/core-java](https://dzone.com/refcardz/core-java)
-   [http://introcs.cs.princeton.edu/java/11cheatsheet](http://introcs.cs.princeton.edu/java/11cheatsheet)
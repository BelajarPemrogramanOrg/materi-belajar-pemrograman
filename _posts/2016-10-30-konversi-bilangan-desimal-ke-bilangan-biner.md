---
ID: 7
post_title: >
  Program C untuk Konversi Bilangan
  Desimal ke Bilangan Biner
author: Muhammad Ikhsan
post_date: 2016-10-30 05:40:10
post_excerpt: |
  Bilangan desimal merupakan sistem bilangan yang umum kita pakai dalam kehidupan sehari-hari, yang mana satu digit angka dalam bilangan desimal dapat berupa angka 0, 1, 2, 3, 4, 5, 6, 7, 8, atau 9. Terdapat 10 nilai yang dapat kita gunakan dalam 1 digit bilangan desimal, oleh karenanya bilangan desimal juga disebut sebagai bilangan basis 10.
  
  Bilangan biner merupakan sistem bilangan yang digit-digitnya terdiri dari nilai 0 atau 1. Bilangan biner hanya terdiri dari 2 nilai, 0 atau 1, sehingga bilangan biner juga disebut sebagai bilangan basis 2. Bilangan biner digunakan dalam sistem digital, termasuk komputer digital. Karena komputer menggunakan bilangan biner untuk representasi informasi, dan kita menggunakan bilangan desimal untuk representasi angka dalam sehari-hari, seringkali kita membutuhkan pengkonversian bilangan dari desimal ke biner atau sebaliknya.
layout: post
permalink: >
  http://belajarpemrograman.org/konversi-bilangan-desimal-ke-bilangan-biner/
published: true
---
Pada kesempatan ini, akan dibahas contoh program untuk melakukan konversi bilangan dalam representasi desimal ke bilangan dalam representasi biner.
<h2>Pengenalan</h2>
Bilangan desimal merupakan sistem bilangan yang umum kita pakai dalam kehidupan sehari-hari, yang mana satu digit angka dalam bilangan desimal dapat berupa angka 0, 1, 2, 3, 4, 5, 6, 7, 8, atau 9. Terdapat 10 ragam nilai yang dapat kita gunakan dalam 1 digit bilangan desimal. Oleh karenanya, bilangan desimal juga disebut sebagai bilangan basis 10. Untuk menunjukkan basis 10, terkadang bilangan dituliskan dengan format x<sub>10</sub>.

Bilangan biner merupakan sistem bilangan yang digit-digitnya terdiri dari nilai 0 atau 1. Satu digit bilangan biner dapat bernilai 1 atau 0. Karena hanya terdiri dari 0 dan 1, bilangan biner juga disebut sebagai bilangan basis 2. Untuk menunjukkan basisnya, biasanya bilangan biner dituliskan dengan format x<sub>2</sub>. Bilangan biner digunakan dalam sistem digital, termasuk komputer digital.

Di bawah ini ditunjukkan beberapa bilangan dalam representasi desimal dan binernya.
<pre style="width: 12em;"> DESIMAL     BINER

 　0      =       0
 　1      =       1
 　2      =      10
 　3      =      11
 　4      =     100
 　5      =     101
 　6      =     110
 　7      =     111
 　8      =    1000
　15      =    1111
　16      =   10000
　31      =   11111
　32      =  100000
　63      =  111111
　64      = 1000000</pre>
<h2>Desimal vs Biner</h2>
Kita mengenal istilah satuan, puluhan, ratusan, ribuan, dan seterusnya dalam pelajaran Matematika di bangku sekolah dasar. Misalnya, bilangan <code>354</code>, terdiri dari <code>3</code> ratusan, <code>5</code> puluhan, dan <code>4</code> satuan. Angka <code>3</code> dalam <code>354</code> disebut sebagai ratusan karena memiliki nilai <code>300</code>, yaitu <code>3 x 100</code>. Sedangkan <code>5</code> disebut sebagai puluhan karena <code>5</code> dalam <code>354</code> memiliki nilai <code>50</code>, yaitu <code>5 x 10</code>. Begitu pula dengan <code>4</code> disebut sebagai satuan karena mewakili nilai <code>4 x 1 = 4</code>.
<pre>354 = 3 ratusan + 5 puluhan + 4 satuan
354 = 300       + 50        + 4
354 = (3 x 100) + (5 x 10)  + (4 x 1)
354 = (3 x 10<sup>2</sup>) + (5 x 10<sup>1</sup>) + (4 x 10<sup>0</sup>)</pre>
Pada dasarnya, bilangan dalam representasi biner dapat dijabarkan dengan cara yang serupa. Pada contoh di bawah ini kita akan membandingkan keduanya.
<pre>54<sub>10</sub> = 5 puluhan + 4 satuan
54<sub>10</sub> = 50        + 4
54<sub>10</sub> = (5 x 10)  + (4 x 1)
54<sub>10</sub> = (5 x 10<sup>1</sup>) + (4 x 10<sup>0</sup>)

110110<sub>2</sub> = (1 x 2<sup>5</sup>) + (1 x 2<sup>4</sup>) + (0 x 2<sup>3</sup>) + (1 x 2<sup>2</sup>) + (1 x 2<sup>1</sup>) + (0 x 2<sup>0</sup>)
110110<sub>2</sub> = (1 x 32) + (1 x 16) + (0 x 8)  + (1 x 4)  + (1 x 2)  + (0 x 1)
110110<sub>2</sub> = 32       + 16       + 0        + 4        + 2        + 0
110110<sub>2</sub> = 54<sub>10</sub></pre>
Meskipun bukan merupakan pembahasan kita pada materi ini, contoh di atas telah menunjukkan bagaimana konversi dari bilangan biner ke bilangan desimal.
<h2>Konversi Desimal -&gt; Biner</h2>
Untuk melakukan konversi dari bilangan desimal ke bilangan biner, kita akan menggunakan algoritma "divide by 2", alias "dibagi 2". Dalam algoritma ini, diasumsikan bahwa bilangan yang akan dikonversi memiliki nilai &gt; 0.

Algoritma ini menggunakan sisa dari hasil pembagian dengan 2 untuk memperoleh digit-digit biner. Misalnya,
<ul>
 	<li>10 / 2 = 5 sisa 0,</li>
 	<li>5 / 2 = 2 sisa 1.</li>
</ul>
Sisa bagi ini sering juga disebut sebagai modulo dalam Matematika, sehingga
<ul>
 	<li>10 modulo 2 = 0,</li>
 	<li>5 modulo 2 = 1.</li>
</ul>
Dengan berdasar pada sifat bilangan ganjil dan genap dapat kita katakan bahwa
<ul>
 	<li>semua bilangan ganjil di-modulo-2 sama dengan 1, dan</li>
 	<li>semua bilangan genap di-modulo-2 sama dengan 0.</li>
</ul>
Dengan berbekal dasar tersebut, contoh di bawah ini akan menunjukkan langkah-langkah konversi bilangan desimal ke bilangan biner.
<pre>354<sub>10</sub> = ...<sub>2</sub>

354 / 2 = 177 sisa <strong>0</strong>             <span style="color: #a39d9d;"><strong>0</strong></span>
177 / 2 = 88  sisa <strong>1</strong>            <span style="color: #a39d9d;"><strong>1</strong>0</span>
88  / 2 = 44  sisa <strong>0</strong>           <span style="color: #a39d9d;"><strong>0</strong>10</span>
44  / 2 = 22  sisa <strong>0</strong>          <span style="color: #a39d9d;"><strong>0</strong>010</span>
22  / 2 = 11  sisa <strong>0</strong>         <span style="color: #a39d9d;"><strong>0</strong>0010</span>
11  / 2 = 5   sisa <strong>1</strong>        <span style="color: #a39d9d;"><strong>1</strong>00010</span>
5   / 2 = 2   sisa <strong>1</strong>       <span style="color: #a39d9d;"><strong>1</strong>100010</span>
2   / 2 = 1   sisa <strong>0      <span style="color: #a39d9d;">0</span></strong><span style="color: #a39d9d;">1100010</span>
1   / 2 = 0   sisa <strong>1</strong>     <strong>1</strong>01100010

354<sub>10</sub> = 101100010<sub>2</sub></pre>
<h2>Kode Program</h2>
<h3>Metode 1</h3>
Pada kode program di bawah ini, kita akan menggunakan tipe data integer (<code>int</code>) baik untuk input desimal maupun output biner. Seolah-olah keduanya merupakan bilangan desimal. Tujuan penggunaan <code>int</code> adalah agar kita dapat menggunakan bilangan hasil perpangkatan dari <code>10</code> untuk memasukkan sebuah digit biner. Sehingga, untuk menyusun rangkaian digit biner <code>1101</code>, kita dapat melakukannya dengan cara:
<pre>1 * 10<sup>0</sup> = 1 *    1  =     1
0 * 10<sup>1</sup> = 0 *   10  =     0
1 * 10<sup>2</sup> = 1 *  100  =   100
1 * 10<sup>3</sup> = 1 * 1000  =  1000
                     -------- +
                       1101</pre>
<strong>Catatan:</strong>
Metode ini hanya mampu menyimpan jumlah digit maksimal bergantung dengan nilai maksimal yang dapat disimpan menggunakan tipe data <code>int</code>. Misalnya, di compiler di komputer saya menggunakan 4 byte untuk menyimpan nilai dengan tipe data <code>int</code>. Oleh karena itu, maksimal nilai desimal yang dapat dikonversi adalah <code>1023<sub>10</sub></code> atau <code>1111111111<sub>2</sub></code> dalam biner.
<h4>File <code>00000-konversi-desimal-ke-biner.c</code></h4>
<pre><code class="language-c line-numbers">#include &lt;stdio.h&gt;

// Fungsi untuk konversi dari desimal ke biner
int dec2bin(int decimal) {
    int binary = 0,  // Output bilangan biner
        bit,         // Sebuah digit biner hasil modulo 2
        exp_10 = 1;  // 10^0, 10^1, 10^2 ...
                     // Pangkat 0, 1, 2, ... sesuai banyaknya digit biner
                     // Dimulai dengan nilai awal 10^0 = 1

    while(decimal &gt; 0) {
        // Modulo 2 dari `decimal` menghasilkan sebuah digit biner
        bit = decimal % 2;
        // Masukkan digit biner `bit` ke dalam `binary`
        binary += exp_10 * bit;
        // Kerjakan `decimal / 2` dan masukkan hasil baginya ke `decimal`
        decimal /= 2;

        // Kalikan 10 untuk menaikkan pangkat dari 10.
        // 1   * 10 = 10^1 = 10
        // 10  * 10 = 10^2 = 100
        // 100 * 10 = 10^3 = 1000
        exp_10 *= 10;
    }

    return binary;
}

int main() {
    int decimal, // Input bilangan desimal
        binary;  // Output bilangan biner

    printf("Masukkan bilangan desimal: ");
    scanf("%d", &amp;decimal);
    binary = dec2bin(decimal);
    printf("Bilangan desimal %d = %d dalam sistem bilangan biner\n", decimal, binary);

    return 0;
}
</code></pre>
<h4>Output</h4>
<pre>Masukkan bilangan desimal: 354
Bilangan desimal 354 = 101100010 dalam sistem bilangan biner</pre>
<h3>Metode 2</h3>
Dalam metode 2 ini, kita akan menggunakan string untuk menyimpan representasi biner. Kita akan melakukan konkatinasi (<em>concatination</em>) digit biner pada string biner. Misalnya, di bawah ini kita akan menyusun rangkaian digit biner <code>1101</code>.
<pre>concat(    "", "1" ) =    "1"
concat(   "1", "1" ) =   "11"
concat(  "11", "0" ) =  "011"
concat( "011", "1" ) = "1011"</pre>
Dengan cara ini, karena kita menggunakan string biner, permasalahan pada metode 1 tidak terjadi lagi. Sehingga tidak ada masalah dengan batasan nilai maksimal yang dapat disimpan pada variabel bertipe integer.
<h4>File <code>00001-konversi-desimal-ke-biner.c</code></h4>
<pre><code class="language-c line-numbers">#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include &lt;string.h&gt;

// Fungsi untuk menyatukan 2 string
char* concat(const char *s1, const char *s2) {
    char *result = malloc(strlen(s1)+strlen(s2)+1); // +1 untuk zero-terminator
    strcpy(result, s1);
    strcat(result, s2);

    return result;
}

// Fungsi untuk konversi dari desimal ke biner
char* dec2bin(int decimal) {
    int bit;           // Sebuah digit biner hasil modulo 2
    char bitString[1]; // Sebuah digit biner hasil modulo 2 sebagai string
    char *binary = ""; // Output biner

    while(decimal &gt; 0) {
        // Modulo 2 dari `decimal` menghasilkan sebuah digit biner
        bit = decimal % 2;
        // Masukkan string yang merepresentasikan `bit` ke dalam `bitString`
        sprintf(bitString, "%d", bit);
        // Masukkan digit biner `bit` ke dalam `binary`
        binary = concat(bitString, binary);
        // Kerjakan `decimal / 2` dan masukkan hasil baginya ke `decimal`
        decimal /= 2;
    }

    return binary;
}

int main() {
    int decimal;   // Input bilangan desimal
    char *binary;  // Output bilangan biner

    printf("Masukkan bilangan desimal: ");
    scanf("%d", &amp;decimal);
    binary = dec2bin(decimal);
    printf("Bilangan desimal %d = %s dalam sistem bilangan biner\n", decimal, binary);

    return 0;
}
</code></pre>
<h4>Output</h4>
<pre>Masukkan bilangan desimal: 315141
Bilangan desimal 354 = 1001100111100000101 dalam sistem bilangan biner</pre>
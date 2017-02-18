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
Pada kesempatan ini, akan dibahas contoh program untuk konversi bilangan desimal ke bilangan biner. Bilangan desimal merupakan sistem bilangan yang umum kita pakai dalam kehidupan sehari-hari, yang mana satu digit angka dalam bilangan desimal dapat berupa angka 0, 1, 2, 3, 4, 5, 6, 7, 8, atau 9. Terdapat 10 nilai yang dapat kita gunakan dalam 1 digit bilangan desimal, oleh karenanya bilangan desimal juga disebut sebagai bilangan basis 10.

Bilangan biner merupakan sistem bilangan yang digit-digitnya terdiri dari nilai 0 atau 1. Bilangan biner hanya terdiri dari 2 nilai, 0 atau 1, sehingga bilangan biner juga disebut sebagai bilangan basis 2. Bilangan biner digunakan dalam sistem digital, termasuk komputer digital. Karena komputer menggunakan bilangan biner untuk representasi informasi, dan kita menggunakan bilangan desimal untuk representasi angka dalam sehari-hari, seringkali kita membutuhkan pengkonversian bilangan dari desimal ke biner atau sebaliknya.
<h2>KODE</h2>
<pre><code class="language-c line-numbers">#include <stdio.h>

int main() {
    int desimal,                // Input bilangan desimal
        desimal_tmp,
        biner = 0,              // Output bilangan biner
        digit_biner,            // Sebuah digit biner hasil modulo 2
        sepuluh_pangkat = 1;    // 10^0, 10^1, 10^2 ... sesuai banyaknya digit biner
                                // Dimulai dengan nilai awal 10^0 = 1

    printf("Masukkan bilangan desimal: ");
    scanf("%d", &desimal);

    // Supaya `desimal` tidak berubah, simpan nilainya ke `desimal_tmp` 
    // yg akan dijadikan patokan berhentinya pengulangan
    desimal_tmp = desimal;
    while(desimal_tmp > 0) {
        // Modulo 2 dari `desimal_tmp` menghasilkan nilai dari sebuah digit biner
        digit_biner = desimal_tmp % 2;
        biner += sepuluh_pangkat * digit_biner;

        // Kalikan 10 untuk menaikkan pangkat dari 10.
        // 1   * 10 = 10^1 = 10
        // 10  * 10 = 10^2 = 100
        // 100 * 10 = 10^3 = 1000
        sepuluh_pangkat *= 10;
        desimal_tmp /= 2;
    }

    printf("Bilangan desimal %d = %d dalam sistem bilangan biner\n", desimal, biner);

    return 0;
}</code></pre>
<h2>OUTPUT</h2>
<pre><code class="language-none">$ gcc 00000-konversi-desimal-ke-biner.c
$ ./a.out
Masukkan bilangan desimal: 134
Bilangan desimal 134 = 10000110 dalam sistem bilangan biner</code></pre>
<h2>CATATAN</h2>
Berikut di bawah ini merupakan catatan yang dapat membantu menjelaskan langkah-langkah konversi bilangan desimal ke bilangan biner yang dikerjakan oleh program.

<img class="aligncenter wp-image-27" title="Langkah-Langkah Konversi Bilangan Desimal ke Bilangan Biner (http://belajarpemrograman.app)" src="http://belajarpemrograman.org/wp-content/uploads/2016/10/belajar-pemrograman-program-c-konversi-bilangan-desimal-ke-biner_ia7nug.jpg" alt="Langkah-Langkah Konversi Bilangan Desimal ke Bilangan Biner (http://belajarpemrograman.app)" width="5085" height="3519" />
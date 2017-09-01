---
ID: 317
post_title: >
  Apa Perbedaan Antara Assign Nilai ke
  Variabel long di Java Menggunakan L dan
  Tidak Menggunakannya?
author: Muhammad Ikhsan
post_excerpt: |
  Di materi yang berjudul <a href="http://belajarpemrograman.org/catatan-belajar-bahasa-pemrograman-java/">Catatan Belajar Bahasa Pemrograman Java</a>, dijelaskan bahwa untuk mengekspresikan nilai dari sebuah variabel bertipe <code>long</code> dapat digunakan literal <code>int</code> (misal 1000) atau literal <code>long</code>, yaitu dengan menambahkan <code>L</code> atau <code>l</code> di akhir penulisan nilai bilangan (misal 1000L). Jika keduanya bisa digunakan, lalu apa bedanya?
  <pre>long longNumber  = 1000;
  long longNumberL = 1000L;</pre>
layout: post
permalink: >
  http://belajarpemrograman.org/assign-nilai-variabel-long-di-java/
published: true
post_date: 2017-02-14 09:19:17
---
## Pertanyaan

Di materi yang berjudul [Catatan Belajar Bahasa Pemrograman Java](http://belajarpemrograman.org/catatan-belajar-bahasa-pemrograman-java/), dijelaskan bahwa untuk assign nilai variabel bertipe `long` di Java dapat digunakan literal `int` (misal `1000`) atau literal `long`, yaitu dengan menambahkan `L` atau `l` di akhir penulisan nilai bilangan (misal `1000L`). Namun, jika ternyata keduanya bisa digunakan, lalu apa bedanya?

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
long longNumber = 1000;
long longNumberL = 1000L;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Jawaban

- Rentang nilai dalam tipe data `int`:
Minimal -2.147.483.648
Maksimal 2.147.483.647

- Rentang nilai dalam tipe data `long`:
Minimal -9.223.372.036.854.775.808
Maksimal 9.223.372.036.854.775.807

Untuk meng-*assign* sebuah nilai bilangan bulat dalam rentang nilai dari -2.147.483.648 sampai 2.147.483.647 ke sebuah variabel bertipe `long`, kita dapat menggunakan literal `int`.

Namun untuk meng-assign sebuh nilai bilangan bulat yang tidak berada dalam rentang nilai tipe data `int`, namun masih dalam rentang nilai tipe data `long`, kita harus menggunakan literal `long`. Yaitu dengan menambahkan `L` atau `l` di akhir penulisan bilangan.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
// Memasukkan nilai ke dalam variabel bertipe long menggunakan literal int.
// Selama nilai tersebut masih dalam rentang nilai tipe data int,
// maka tidak terjadi error.
long longNumber = 1000;

// Memasukkan nilai ke dalam variabel bertipe long menggunakan literal int.
// Karena rentang nilai tipe data int maksimal 2147483647,
// maka akan terjadi error saat kompilasi.
long longNumber = 2147483648;

// Memasukkan nilai ke dalam variabel bertipe long menggunakan literal long.
// Karena 2147483648 masih berada di dalam rentang nilai tipe data long,
// maka tidak terjadi error.
long longNumberL = 2147483648L;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Baik `L` maupun `l` dapat digunakan dalam literal `long`, keduanya sama saja. Namun, untuk *readibility* alias supaya mudah dibaca, sebaiknya gunakan kapital `L`. Bilangan 313 ditulis dengan literal `long` menggunakan `313L` lebih mudah dikenali sebagai 313 daripada jika dituliskan `313l`. Gampang terbaca salah, dikira angka 3131.

--------------------------------------------------------------------------

*Featured image* dimodifikasi dari gambar di [http://maxpixel.freegreatpicture.com/Question-Hatena-The-Trouble-Think-About-Annoying-1184896](http://maxpixel.freegreatpicture.com/Question-Hatena-The-Trouble-Think-About-Annoying-1184896)
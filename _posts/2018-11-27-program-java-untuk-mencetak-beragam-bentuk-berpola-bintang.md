---
ID: 994
post_title: >
  Program Java untuk Mencetak Beragam
  Bentuk Berpola Bintang
author: Muhammad Ikhsan
post_excerpt: ""
layout: post
permalink: >
  http://belajarpemrograman.org/program-java-untuk-mencetak-beragam-bentuk-berpola-bintang/
published: true
post_date: 2018-11-27 00:55:18
---
Mencetak pola bintang merupakan salah satu latihan yg umum dilakukan ketika belajar logika pengulangan, alias _looping_. Entah itu membuat pola segitiga siku-siku, segitiga sama kaki, diamond, atau yg lain.

Dalam materi ini, kita akan melihat 8 kasus pola bintang dan contoh penyelesaiannya dalam Java. Hemm, saya harap, materi ini memang untuk belajar ya, bukan sekedar dikopas untuk menjawab tugas lab, atau PR.

Berikut merupakan daftar pola `*` (bintang) yg akan kita _print_ menggunakan `for` looping.

1. Garis horizontal
1. Kotak
1. Segitiga siku-siku
1. Segitiga siku-siku #2
1. Segitiga sama kaki
1. Segitiga sama kaki #2
1. Diamon

Agar lebih mudah dimengerti, dan fokus pada logika _looping_-nya, kodenya saya pecah2 per bentuk ya.. Nanti di akhir materi, akan saya berikan kode lengkapnya.

Garis Horizontal
----------------

Kita mulai dari yg paling mudah dulu ya, membuat sebuah garis lurus.

```
*****
```

Sudah jelas, bahwa kita hanya perlu mencetak `*` sebanyak `n` kali. Untuk contoh di atas, berarti, `5` kali.

```java
int n = 5;
for (int i = 1; i &lt;= n; i++) {
  System.out.print(&#039;*&#039;);
}
```

Kotak
-----

Kita lanjutkan dengan membuat sebuah kotak dengan dimensi `n` x `n`.

```
*****
*****
*****
*****
*****
```

Di sini kita akan mencetak 5 garis horizontal, dengan masing-masing garis sepanjang 5 bintang.

Berarti, kita cukup mengulangi menjalankan kode-untuk-mencetak-garis-horizontal, sebanyak 5 kali.

```java
int n = 5;
for (int i = 1; i &lt;= n; i++) {
  for (int j = 1; j &lt;= n; j++) {
    System.out.print(&#039;*&#039;);
  }
  System.out.println();
}
```

Segitiga Siku-siku
------------------

Kita lanjutkan dengan bentuk segitiga paling sederhana ini.

```
*
**
***
****
*****
```

- Pada baris ke-1, cetak 1 `*`.
- Pada baris ke-2, cetak 2 `*`.
- Pada baris ke-3, cetak 3 `*`.
- dst. sampai baris ke-`n`.

```java
int n = 5;
for (int i = 1; i &lt;= n; i++) {
  for (int j = 1; j &lt;= i; j++) {
    System.out.print(&#039;*&#039;);
  }
  System.out.println();
}
```

Segitiga Siku-Siku #2
---------------------

```
    *
   **
  ***
 ****
*****
```

Saya akan mencontohkan 2 cara, yaitu:
1. kombinasi spasi dengan `*`, dan
2. menggunakan `printf`.

#### Kombinasi ` ` (spasi) dengan `*`

Pada cara pertama, kita akan menyusun setiap baris dengan kombinasi antara sekumpulan ` ` (spasi) (spasi) dan `*` (bintang).

- Pada baris ke-1, cetak (4 ` ` (spasi) dan 1 `*`)
- Pada baris ke-2, cetak (3 ` ` (spasi) dan 2 `*`)
- Pada baris ke-3, cetak (2 ` ` (spasi) dan 3 `*`)
- dst. sampai baris ke-`n`.

```java
int n = 5;
for (int i = 1; i &lt;= n; i++) {
  String stars = &quot;&quot;;
  for (int j = n - i; j &gt;= 1; j--) {
    stars += &quot; &quot;;
  }
  for (int j = 1; j &lt;= i; j++) {
    stars += &quot;*&quot;;
  }
  System.out.println(stars);
}
```

#### Menggunakan `printf`

Pada cara kedua, kita akan menggunakan `printf`.

Kita akan memformat string, dengan aturan:
- setiap baris dicetak dengan panjang yang tetap (`n` karakter),
- apabila jumlah karakter ada string kurang dari `n`, sisipkan karakter ` ` (spasi) (spasi) di depannya

Begini contoh penggunaan `printf`:

```java
// Mencetak &quot;    *&quot; (tanpa petik)
System.out.printf(&quot;%5s&quot;, &quot;*&quot;);
```

`%5s` merupakan format untuk mencetak `s`tring, dengan memberi tempat sepanjang 5 karakter utk string tersebut.

Sekarang, saatnya kita membuat segitiga pola bintang:

```java
int n = 5;
for (int i = 1; i &lt;= n; i++) {
  String stars = &quot;&quot;;
  for (int j = 1; j &lt;= i; j++) {
    stars += &quot;*&quot;;
  }
  System.out.printf(&quot;%&quot; + n + &quot;s%n&quot;, stars);
}
```

Di atas, saya juga menggunakan `%n` untuk membuat baris baru (_new line_). Dalam hal ini, sama dengan `\n`.

Segitiga Sama Kaki
------------------

```
    *
   ***
  *****
 *******
*********
```

Bentuk di atas ada kemiripannya dengan 2 segitiga siku-siku yg telah dibuat sebelumnya:

```
    *
   **     *
  ***  +  **
 ****     ***
*****     ****
```

Kita bisa gunakan 2 cara seperti halnya Segitiga Siku-Siku #2.

#### Kombinasi ` ` (spasi) dengan `*`

- Pada baris ke-1, cetak (4 ` ` (spasi) dan 1 `*`)
- Pada baris ke-2, cetak (3 ` ` (spasi) dan 3 `*`)
- Pada baris ke-3, cetak (2 ` ` (spasi) dan 5 `*`)
- dst. sampai baris ke-`n`.

Pola 1, 3, 5, 7, 9 dapat diperoleh dari `i + i - 1` atau `2 * i - 1`.

```
2 * 1 - 1 = 1
2 * 2 - 1 = 3
2 * 3 - 1 = 5
2 * 4 - 1 = 7
2 * 5 - 1 = 9
```

```java
int n = 5;
for (int i = 1; i &lt;= n; i++) {
  String stars = &quot;&quot;;
  for (int j = n - i; j &gt;= 1; j--) {
    stars += &quot; &quot;;
  }
  for (int j = 1; j &lt;= (2 * i - 1); j++) {
    stars += &quot;*&quot;;
  }
  System.out.println(stars);
}
```

#### Menggunakan `printf`

```java
int n = 5;
for (int i = 1; i &lt;= n; i++) {
  String stars = &quot;&quot;;
  for (int j = 1; j &lt;= (2 * i - 1); j++) {
    stars += &quot;*&quot;;
  }
  System.out.printf(&quot;%&quot; + (n + i - 1) + &quot;s%n&quot;, stars);
}
```

Segitiga Sama Kaki #2
---------------------

```
*********
 *******
  *****
   ***
    *
```

Mirip dengan segitiga sama kaki sebelumnya, cuman, dibalik. Jadinya, kodenya juga mirip. Kalau sebelumnya pakai `i++`, sekarang pakai `i--`.

#### Kombinasi ` ` (spasi) dengan `*`

```java
int n = 5;
for (int i = n; i &gt;= 1; i--) {
  String stars = &quot;&quot;;
  for (int j = 1; j &lt;= n - i; j++) {
    stars += &quot; &quot;;
  }
  for (int j = (2 * i - 1); j &gt;= 1; j--) {
    stars += &quot;*&quot;;
  }
  System.out.println(stars);
}
```

#### Menggunakan `printf`

```java
int n = 5;
for (int i = n; i &gt;= 1; i--) {
  String stars = &quot;&quot;;
  for (int j = (2 * i - 1); j &gt;= 1; j--) {
    stars += &quot;*&quot;;
  }
  System.out.printf(&quot;%&quot; + (n + i - 1) + &quot;s%n&quot;, stars);
}
```

Diamon
------

```
    *
   ***
  *****
 *******
*********
 *******
  *****
   ***
    *
```

Di atas merupakan diamon untuk `n = 5`.

Bentuk diamon tersebut dapat dibagi menjadi 2 segitiga sama kaki, yg sudah kita buat sebelumnya.

```
    *
   ***
  *****
 *******
*********

    +

 *******
  *****
   ***
    *
```

Kita bagi diamon menjadi 2 bagian: bagian atas (`top`) dan bawah (`botom`).

Bagian atas terdiri dari 5 baris, sedangkan bagian bawah terdiri dari 4 baris.

Dengan kata lain, bagian atas terdiri dari `n` baris, sedangkan bagian bawah terdiri dari `n - 1` baris.

```java
int n = 5;
String top = &quot;&quot;, bottom = &quot;&quot;;
for (int i = 1; i &lt;= n; i++) {
  String stars = &quot;&quot;;
  for (int j = 1; j &lt;= n - i; j++) {
    stars += &quot; &quot;;
  }
  for (int j = 1; j &lt;= (i * 2 - 1); j++) {
    stars += &quot;*&quot;;
  }
  stars += &quot;\n&quot;;
  top += stars;
  if (i &lt; n) {
    bottom = stars + bottom;
  }
}
System.out.print(top + bottom);
```

Kode di atas mirip dengan kode untuk membuat segitiga sama kaki, yg menggunakan ` ` (spasi) dan `*`.

Kita tidak membuat _loop_ tersendiri untuk membuat bagian bawah diamon. Kita memanfaatkan operasi penggabungan string (_concatenation_). Seusai penyusunan sebuah baris pada `top`, sebuah baris pada `bottom` juga tersusun.

```java
String top = &quot;&quot;, bottom = &quot;&quot;;

top += &quot;1&quot;;                // &quot;1&quot;
bottom = &quot;1&quot; + bottom;     // &quot;1&quot;

top += &quot;22&quot;;               // &quot;122&quot;
bottom = &quot;22&quot; + bottom;    // &quot;221&quot;

top += &quot;333&quot;;              // &quot;122333&quot;
bottom += &quot;333&quot; + bottom;  // &quot;333221&quot;
```

Gabungan
--------

Baik, demikianlah penggunaan `for` _looping_ untuk nge-`print()` beberapa bentuk berpola `*`. Diharapkan, setelah nyaman menggunakan `for` loop pada contoh-contoh di atas, sekarang kita bisa menyelesaikan soal yg serupa entah bagaimanapun bentuk yg diminta. Lebih dari itu, kita sudah bisa menentukan kapan dan bagaimana cara menggunakannya untuk menyelesaikan persoalan yg dihadapi.

Seperti yg dijanjikan sebelumnya, berikut merupakan kode lengkap, yg meliput semua bentuk-bentuk di atas.

```java
import java.util.Scanner;

public class StarKumpulan {
  public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);
    int option, n;

    System.out.print("\n" +
      "PRINT() POLA BINTANG\n" +
      "====================\n");

    do {
      System.out.print("\n" +
        "Pilihan:\n" +
        "1. Garis Horizontal\n" +
        "2. Kotak\n" +
        "3. Segitiga Siku-Siku\n" +
        "4. Segitiga Siku-Siku #2\n" +
        "5. Segitiga Sama Kaki\n" +
        "6. Segitiga Sama Kaki #2\n" +
        "7. Diamon\n" +
        "0. Keluar\n");
      System.out.print("\nPilih: ");
      option = scanner.nextInt();

      if (option >= 1 && option <= 7) {
        System.out.print("\nInput n: ");
        n = scanner.nextInt();
        System.out.print("\n");
        switch (option) {
          case 1:
            printStarGarisHorizontal(n);
            break;
          case 2:
            printStarKotak(n);
            break;
          case 3:
            printStarSegitigaSikuSiku(n);
            break;
          case 4:
            printStarSegitigaSikuSiku2(n);
            break;
          case 5:
            printStarSegitigaSamaKaki(n);
            break;
          case 6:
            printStarSegitigaSamaKaki2(n);
            break;
          case 7:
            printStarDiamon(n);
            break;
        }

        System.out.print("\nTekan ENTER untuk melanjutkan...");
        scanner.nextLine();
        scanner.nextLine();
      }
    } while(option != 0);
    scanner.close();
  }

  private static void printStarGarisHorizontal(int n) {
    for (int i = 1; i <= n; i++) {
      System.out.print('*');
    }
    System.out.print("\n");
  }

  private static void printStarKotak(int n) {
    for (int i = 1; i <= n; i++) {
      for (int j = 1; j <= n; j++) {
        System.out.print('*');
      }
      System.out.print("\n");
    }
  }

  private static void printStarSegitigaSikuSiku(int n) {
    for (int i = 1; i <= n; i++) {
      for (int j = 1; j <= i; j++) {
        System.out.print('*');
      }
      System.out.print("\n");
    }
  }

  private static void printStarSegitigaSikuSiku2(int n) {
    // Menggunakan kombinasi ` ` (spasi) dan `*`
    for (int i = 1; i <= n; i++) {
      String stars = "";
      for (int j = n - i; j >= 1; j--) {
        stars += " ";
      }
      for (int j = 1; j <= i; j++) {
        stars += "*";
      }
      System.out.println(stars);
    }

    // Menggunakan `printf`
    // for (int i = 1; i <= n; i++) {
    //     String stars = "";
    //     for (int j = 1; j <= i; j++) {
    //         stars += "*";
    //     }
    //     System.out.printf("%" + n + "s%n", stars);
    // }
  }

  private static void printStarSegitigaSamaKaki(int n) {
    // Menggunakan kombinasi ` ` (spasi) dan `*`
    for (int i = 1; i <= n; i++) {
      String stars = "";
      for (int j = n - i; j >= 1; j--) {
        stars += " ";
      }
      for (int j = 1; j <= (2 * i - 1); j++) {
        stars += "*";
      }
      System.out.println(stars);
    }

    // Menggunakan `printf`
    // for (int i = 1; i <= n; i++) {
    //     String stars = "";
    //     for (int j = 1; j <= (2 * i - 1); j++) {
    //         stars += "*";
    //     }
    //     System.out.printf("%" + (n + i - 1) + "s%n", stars);
    // }
  }

  private static void printStarSegitigaSamaKaki2(int n) {
    // Menggunakan kombinasi ` ` (spasi) dan `*`
    for (int i = n; i >= 1; i--) {
      String stars = "";
      for (int j = 1; j <= n - i; j++) {
        stars += " ";
      }
      for (int j = (2 * i - 1); j >= 1; j--) {
        stars += "*";
      }
      System.out.println(stars);
    }

    // Menggunakan `printf`
    // for (int i = n; i >= 1; i--) {
    //     String stars = "";
    //     for (int j = (2 * i - 1); j >= 1; j--) {
    //         stars += "*";
    //     }
    //     System.out.printf("%" + (n + i - 1) + "s%n", stars);
    // }
  }

  private static void printStarDiamon(int n) {
    String top = "", bottom = "";
    for (int i = 1; i <= n; i++) {
      String stars = "";
      for (int j = 1; j <= n - i; j++) {
        stars += " ";
      }
      for (int j = 1; j <= (i * 2 - 1); j++) {
        stars += "*";
      }
      stars += "\n";
      top += stars;
      if (i < n) {
        bottom = stars + bottom;
      }
    }
    System.out.println(top + bottom);
  }
}
```

Demikian ilmu yg bisa saya bagikan pada kesempatan ini.

Terima kasih.

Semoga bermanfaat.
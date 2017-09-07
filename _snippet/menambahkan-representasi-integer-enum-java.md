---
ID: 452
post_title: >
  Menambahkan Representasi Integer pada
  Enum di Java
author: Muhammad Ikhsan
post_excerpt: |
  <pre><code class="language-java line-numbers">public enum Difficulty {
  LOW   (1), // Memanggil constructor dengan nilai 1
  MEDIUM(2),
  HARD  (3); // Diakhiri dengan ;
  
  private final int difficultyValue;
  
  Level(int difficultyValue) {
  this.difficultyValue = difficultyValue;
  }
  
  public int getDifficultyValue() {
  return this.difficultyValue;
  }
  }</code><div class="open-snippet">Lihat Snippet</div></pre>
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/java/menambahkan-representasi-integer-enum-java/
published: true
post_date: 2017-02-10 05:06:52
---
Terkadang kita perlu menambahkan representasi integer untuk suatu value pada sebuah enum di Java. Biasanya ini diperlukan ketika kita ingin melakukan suatu kalkulasi yang melibatkan nilai yang diwakilkan oleh konstan yang kita letakkan di enum. Kasus lain, misalnya ketika kita ingin menyimpan nilai pada sebuah enum ke database, yang mana di database nilai tersebut disimpan sebagai integer. Solusi untuk masalah ini, kita dapat menambahkan metode untuk mengatur dan memperoleh representasi integer pada nilai di enum seperti di snippet berikut.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
public enum Difficulty {
    LOW   (1), // Memanggil constructor dengan nilai 1
    MEDIUM(2),
    HARD  (3); // Diakhiri dengan ;

    private final int difficultyValue;

    Level(int difficultyValue) {
    this.difficultyValue = difficultyValue;
    }

    public int getDifficultyValue() {
    return this.difficultyValue;
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Selanjutnya, untuk memperoleh representasi integer dari sebuah Difficulty, kita dapat memanggilnya seperti berikut.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
Difficulty difficulty = Difficulty.HARD;
int difficultyLevel = difficulty.getDifficultyValue();
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
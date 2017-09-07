---
ID: 563
post_title: >
  Menghapus Semua Tabel di Sebuah Database
  MySQL
author: Muhammad Ikhsan
post_excerpt: |
  Seringkali pas mau import hasil dump sebuah database, kita perlu mengosongkan database. Atau dengan kata lain, perlu menghapus semua tabel di sebuah database. Oke, kalau kita memiliki <em>privilege</em> untuk <code>CREATE</code> dan <code>DROP</code> database, kita menghapus databasenya dulu, kemudian kita buat lagi. Sayangnya, kondisinya tidak selalu begitu.
  
  Jika Anda memiliki <code>grep</code>, maka Anda dapat gunakan snippet berikut:
  
  <pre class="language-bash"><code>mysqldump -u[username] -p[password] --add-drop-table --no-data [databasename] | grep ^DROP | mysql -u[username] -p[password] [databasename]</code><div class="open-snippet">Lihat Snippet</div></pre>
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/mysql/hapus-semua-tabel-dalam-database-mysql/
published: true
post_date: 2017-09-07 08:36:26
---
Seringkali pas mau import hasil dump sebuah database atau karena hal-hal lainnya, kita perlu mengosongkan database. Atau dengan kata lain, perlu menghapus semua tabel di sebuah database. Oke, kalau kita memiliki *privilege* untuk `CREATE` dan `DROP` database, kita menghapus databasenya dulu, kemudian kita buat lagi. Sayangnya, kondisinya tidak selalu begitu.

Jika Anda memiliki `grep`, maka Anda dapat gunakan snippet berikut:

```
mysqldump -u[username] -p[password] --add-drop-table --no-data [databasename] | grep ^DROP | mysql -u[username] -p[password] [databasename]
```

Namun jika Anda di Windows dan tidak memiliki `grep`, Anda dapat gunakan:

```
mysqldump -u[username] -p[password] --add-drop-table --no-data [databasename] | findstr ^DROP | mysql -u[username] -p[password] [databasename]
```

## Penggunaan

- Ganti `[username]`, `[password]`, dan `[databasename]` dengan username, password, dan nama database yang akan dihapus.

- Terutama jika Anda menggunakan Windows, pastikan `mysqldump` dan `mysql` telah berada di *variable environment* `PATH`. Atau, jalankan perintah di atas dengan direktori aktif di lokasi di mana `mysql` terinstal.
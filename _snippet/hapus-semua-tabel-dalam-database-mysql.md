---
ID: 563
post_title: >
  Menghapus Semua Tabel di Sebuah Database
  MySQL
author: Muhammad Ikhsan
post_excerpt: |
  Jika Anda memiliki <code>grep</code>, maka Anda dapat gunakan snippet berikut:
  
  <pre class="language-bash"><code>mysqldump -u[username] -p[password] --add-drop-table --no-data [databasename] | grep ^DROP | mysql -u[username] -p[password] [databasename]</code></pre>
  

  Namun jika Anda di Windows dan tidak memiliki `grep`, Anda dapat gunakan:
  
  
  <pre class="language-bash"><code>mysqldump -u[username] -p[password] --add-drop-table --no-data [databasename] | findstr ^DROP | mysql -u[username] -p[password] [databasename]</code></pre>
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/mysql/hapus-semua-tabel-dalam-database-mysql/
published: false
post_date: 2017-09-07 08:36:26
---
Karena alasan tertentu, kadang kala kita perlu mengosongkan sebuah database. Dengan kata lain menghapus semua tabel di sebuah database. Kalau kita memiliki *privilege* untuk `CREATE` dan `DROP` database, kita bisa menghapus database dulu, kemudian dibuat lagi. Ambil amannya saja, saya anggap kita tidak memilikinya.

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
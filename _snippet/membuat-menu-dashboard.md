---
ID: 430
post_title: >
  Membuat Custom Menu di Dashboard
  WordPress
author: Muhammad Ikhsan
post_excerpt: |
  <pre><code class="language-php line-numbers">/**
  * Menambahkan submenu pengaturan materi BP
  */
  add_action( 'admin_menu', 'bp_tutorial_setting_submenu' );
  function bp_tutorial_setting_submenu() {
  add_submenu_page(
  'options-general.php',
  __( 'Pengaturan Materi BP', 'belajar-pemrograman' ),
  __( 'Materi BP', 'belajar-pemrograman' ),
  'manage_options',
  'bp-tutorial-setting',
  bp_tutorial_setting_page
  ); ...</code><div class="open-snippet">Lihat Snippet</div></pre>
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/wordpress/membuat-menu-dashboard/
published: true
post_date: 2017-02-23 18:36:45
---
Dalam pembuatan plugin WordPress, kita dapat menambahkan halaman untuk pengaturan plugin sebagai submenu dari menu *default* WordPress. Biasanya, diletakkan sebagai submenu dari menu Settings alias Pengaturan. Atau, kita juga bisa membuat menu sendiri khusus untuk plugin yang kita buat. Kemudian, kita bisa tambahkan juga beberapa submenu yang dibutuhkan.

Membuat Submenu dari Menu Utama Settings {#membuat-submenu-dari-menu-utama-settings}
----------------------------------------
Jika plugin yang dibuat hanya membutuhkan satu halaman baru di dashboard, maka sebaiknya tidak membuat menu utama baru. Cukup buat saja sebuah submenu dari menu *default* dashboard WordPress. Dalam contoh ini, kita akan membuat sebuah halaman pengaturan plugin. Oleh karenanya, kita akan membuat sebuah submenu dari menu utama Settings dengan cara membuat fungsi yang memanggil fungsi [add_submenu_page] yang di-*hook* ke action `admin_menu`. Selanjutnya, kita juga akan menentukan konten dari submenu tersebut dengan menempatkan konten tersebut ke dalam fungsi yang akan dipanggil ketika submenu diakses.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-php .line-numbers}
/**
 * Menambahkan submenu pengaturan materi BP
 */
add_action( &#039;admin_menu&#039;, &#039;bp_tutorial_setting_submenu&#039; );
function bp_tutorial_setting_submenu() {
    add_submenu_page(
        &#039;options-general.php&#039;,
        __( &#039;Pengaturan Materi BP&#039;, &#039;belajar-pemrograman&#039; ),
        __( &#039;Materi BP&#039;, &#039;belajar-pemrograman&#039; ),
        &#039;manage_options&#039;,
        &#039;bp-tutorial-setting&#039;,
        &#039;bp_tutorial_setting_page&#039;
    );
}
 
/**
 * Konten halaman pengaturan materi BP
 */
function bp_tutorial_setting_page() {
?&gt;
    
    &lt;div class=&quot;wrap&quot;&gt;
        &lt;h1&gt;&lt;?php _e( &#039;Pengaturan Materi BP&#039;, &#039;belajar-pemrograman&#039; ); ?&gt;&lt;/h1&gt;
        &lt;p&gt;&lt;?php _e( &#039;Ini merupakan halaman pengaturan materi BP&#039;, &#039;belajar-pemrograman&#039; ); ?&gt;&lt;/p&gt;
    &lt;/div&gt;
 
&lt;?php
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Keterangan {#keterangan}

-   **Baris 6-13** digunakan untuk menambahkan submenu `Materi BP`

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-php .line-numbers}
    add_submenu_page(
        'options-general.php',
        __( 'Pengaturan Materi BP', 'belajar-pemrograman' ),
        __( 'Materi BP', 'belajar-pemrograman' ),
        'manage_options',
        'bp-tutorial-setting',
        'bp_tutorial_setting_page'
    );
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   **Baris 7**: `options-general.php` merupakan *slug* dari menu utama Settings alias Pengaturan
-   **Baris 8**: menentukan judul halaman submenu. Judul ini akan digunakan pada tag `<title></title>` halaman pengaturan
-   **Baris 9**: menentukan label submenu yang akan ditampilkan pada bilah menu dashboard
-   **Baris 10**: menentukan minimal *capability* yang harus dimiliki user untuk dapat mengakses konten submenu
-   **Baris 11**: menentukan slug dari submenu yang kita buat
-   **Baris 12**: menentukan nama fungsi yang akan dipanggil untuk menampilkan konten
-   Jika submenu ingin dibuat sebagai sub dari beberapa menu utama *default* WordPress yang lain, maka gunakan salah satu dari slug berikut untuk menggantikan `options-general.php` pada **baris 7**:
    -   `index.php` untuk menu utama Dashboard
    -   `edit.php` untuk menu utama Posts
    -   `upload.php` untuk menu utama Media
    -   `edit.php?post_type=page` untuk menu utama Pages
    -   `edit-comments.php` untuk menu utama Comments
    -   `edit.php?post_type=sebuah_custom_post_type` untuk menu utama dari sebuah custom post type
    -   `themes.php` untuk menu utama Appearance
    -   `plugins.php` untuk menu utama Plugins
    -   `users.php` untuk menu utama Users
    -   `tools.php` untuk menu utama Tools

Membuat Menu Utama dan Submenu Terpisah {#membuat-menu-utama-dan-submenu-terpisah}
---------------------------------------

Kali ini, kita akan membuat sebuah menu utama beserta beberapa submenunya di dashboard. Biasanya, ini dilakukan jika plugin membutuhkan beberapa halaman dan menu terpisah untuk penyediaan fitur-fiturnya maupun sebagai halaman pengaturan.

Pembuatan menu utama pada kode di bawah ini sangat mirip dengan kode sebelumnya. Untuk membuat menu utama, kita akan menggunakan fungsi [add_menu_page].

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-php .line-numbers}
/**
 * Menambahkan menu dan submenu plugin
 */
add_action( &#039;admin_menu&#039;, &#039;bp_tutorial_main_menu&#039; );
function bp_tutorial_main_menu() {
    $parent_slug = &#039;bp-tutorial&#039;;
 
    add_menu_page(
        __( &#039;Pengaturan Materi BP&#039;, &#039;belajar-pemrograman&#039; ),
        __( &#039;Materi BP&#039;, &#039;belajar-pemrograman&#039; ),
        &#039;manage_options&#039;,
        $parent_slug,
        &#039;bp_tutorial_material_setting_page&#039;,
        &#039;dashicons-book-alt&#039;,
        81
    );
 
    add_submenu_page(
        $parent_slug,
        __( &#039;Pengaturan Snippet BP&#039;, &#039;belajar-pemrograman&#039; ),
        __( &#039;Snippet BP&#039;, &#039;belajar-pemrograman&#039; ),
        &#039;manage_options&#039;,
        $parent_slug . &#039;-snippet&#039;,
        &#039;bp_tutorial_snippet_setting_page&#039;
    );
}
 
/**
 * Konten halaman pengaturan materi BP
 */
function bp_tutorial_material_setting_page() {
?&gt;
 
    &lt;div class=&quot;wrap&quot;&gt;
        &lt;h1&gt;&lt;?php _e( &#039;Pengaturan Materi BP&#039;, &#039;belajar-pemrograman&#039; ); ?&gt;&lt;/h1&gt;
        &lt;p&gt;&lt;?php _e( &#039;Ini merupakan halaman pengaturan materi BP&#039;, &#039;belajar-pemrograman&#039; ); ?&gt;&lt;/p&gt;
    &lt;/div&gt;
 
&lt;?php
}

/**
 * Konten halaman pengaturan snippet BP
 */
function bp_tutorial_snippet_setting_page() {
?&gt;
 
    &lt;div class=&quot;wrap&quot;&gt;
        &lt;h1&gt;&lt;?php _e( &#039;Pengaturan Snippet BP&#039;, &#039;belajar-pemrograman&#039; ); ?&gt;&lt;/h1&gt;
        &lt;p&gt;&lt;?php _e( &#039;Ini merupakan halaman pengaturan snippet BP&#039;, &#039;belajar-pemrograman&#039; ); ?&gt;&lt;/p&gt;
    &lt;/div&gt;
 
&lt;?php
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Keterangan {#keterangan}

-   **Baris 8 - 16** digunakan untuk menambahkan menu utama `Materi BP`

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-php .line-numbers}
    add_menu_page(
        __( 'Pengaturan Materi BP', 'belajar-pemrograman' ),
        __( 'Materi BP', 'belajar-pemrograman' ),
        'manage_options',
        $parent_slug,
        'bp_tutorial_material_setting_page',
        'dashicons-book-alt',
        81
    );
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   **Baris 9**: menentukan judul halaman menu. Judul ini akan digunakan dalam tag `<title></title>`
-   **Baris 10**: menentukan label menu yang akan digunakan
-   **Baris 11**: menentukan minimal *capability* yang harus dimiliki user untuk mengakses menu
-   **Baris 12**: menentukan slug dari menu. Pembuatan submenu dari menu utama ini akan memerlukan slug ini
-   **Baris 13**: `bp_tutorial_material_setting_page` merupakan nama fungsi yang akan dipanggil untuk menampilkan konten dari menu.
-   **Baris 14**: menentukan icon pada menu. Icon dapat ditentukan dengan memasukkan url gambar. Silahkan cek daftar parameter add\_menu\_page. Icon juga dapat ditentukan dengan menambahkan nama kelas CSS Dashicons, seperti yang kita lakukan di sini.
-   **Baris 15**: menentukan posisi menu pada bilah menu dashboard. Nilai paling kecil ditempatkan di posisi paling atas.

**Selesai.**

------------------------------------------------------------------------

Terlalu panjang catatannya.. Apakah seperti ini masih disebut snippet? Kuatir kelupaan saja kalau gak dicatat. Lahee, padahal udah ada link ke dokumentasi WordPress. Sudahlah.. Snippet atau bukan, tulisan ini dikelompokkan ke dalam kelompok snippet di website ini. Silahkan kalau mau komen.

[add_submenu_page]: https://developer.wordpress.org/reference/functions/add_submenu_page/
[add_menu_page]: https://developer.wordpress.org/reference/functions/add_menu_page/
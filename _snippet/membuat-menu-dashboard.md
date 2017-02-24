---
ID: 430
post_title: Membuat Menu di Dashboard
author: Muhammad Ikhsan
post_date: 2017-02-23 18:36:45
post_excerpt: 'Dalam pembuatan plugin WordPress, kita dapat menambahkan halaman untuk pengaturan plugin sebagai submenu dari menu <em>default</em> WordPress. Biasanya, diletakkan sebagai submenu dari menu Settings alias Pengaturan. Atau, kita juga bisa membuat menu sendiri khusus untuk plugin yang kita buat.'
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/membuat-menu-dashboard/
published: true
---
Dalam pembuatan plugin WordPress, kita dapat menambahkan halaman untuk pengaturan plugin sebagai submenu dari menu <em>default</em> WordPress. Biasanya, diletakkan sebagai submenu dari menu Settings alias Pengaturan. Atau, kita juga bisa membuat menu sendiri khusus untuk plugin yang kita buat. Kemudian, kita bisa tambahkan juga beberapa submenu yang dibutuhkan.
<h2>Membuat Submenu dari Menu Utama Settings</h2>
Jika plugin yang dibuat hanya membutuhkan satu halaman baru di dashboard, maka sebaiknya tidak membuat menu utama baru. Cukup buat saja sebuah submenu dari menu <em>default</em> dashboard WordPress.

Dalam contoh ini, kita akan membuat sebuah halaman pengaturan plugin. Oleh karenanya, kita akan membuat sebuah submenu dari menu utama Settings dengan cara membuat fungsi yang memanggil fungsi <a href="https://developer.wordpress.org/reference/functions/add_submenu_page/" target="_blank"><code>add_submenu_page</code></a> yang di-<em>hook</em> ke action <code>admin_menu</code>. Selanjutnya, kita juga akan menentukan konten dari submenu tersebut dengan menempatkan konten tersebut ke dalam fungsi yang akan dipanggil ketika submenu diakses.
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
        'bp_tutorial_setting_page'
    );
}
 
/**
 * Konten halaman pengaturan materi BP
 */
function bp_tutorial_setting_page() {
?&gt;
 
    &lt;div class="wrap"&gt;
        &lt;h1&gt;&lt;?php _e( 'Pengaturan Materi BP', 'belajar-pemrograman' ); ?&gt;&lt;/h1&gt;
        &lt;p&gt;&lt;?php _e( 'Ini merupakan halaman pengaturan materi BP', 'belajar-pemrograman' ); ?&gt;&lt;/p&gt;
    &lt;/div&gt;
 
&lt;?php
}</code></pre>
<h3>Keterangan</h3>
<ul>
 	<li><strong>Baris 6-13</strong> digunakan untuk menambahkan submenu <code>Materi BP</code>
<pre data-start="6"><code class="language-php line-numbers">    add_submenu_page(
        'options-general.php',
        __( 'Pengaturan Materi BP', 'belajar-pemrograman' ),
        __( 'Materi BP', 'belajar-pemrograman' ),
        'manage_options',
        'bp-tutorial-setting',
        'bp_tutorial_setting_page'
    );</code></pre>
</li>
 	<li><strong>Baris 7</strong>: <code>options-general.php</code> merupakan <em>slug</em> dari menu utama Settings alias Pengaturan</li>
 	<li><strong>Baris 8</strong>: menentukan judul halaman submenu. Judul ini akan digunakan pada tag <code>&lt;title&gt;&lt;/title&gt;</code> halaman pengaturan</li>
 	<li><strong>Baris 9</strong>: menentukan label submenu yang akan ditampilkan pada bilah menu dashboard</li>
 	<li><strong>Baris 10</strong>: menentukan minimal <em>capability</em> yang harus dimiliki user untuk dapat mengakses konten submenu</li>
 	<li><strong>Baris 11</strong>: menentukan slug dari submenu yang kita buat</li>
 	<li><strong>Baris 12</strong>: menentukan nama fungsi yang akan dipanggil untuk menampilkan konten</li>
 	<li>Jika submenu ingin dibuat sebagai sub dari beberapa menu utama <em>default</em> WordPress yang lain, maka gunakan salah satu dari slug berikut untuk menggantikan <code>options-general.php</code> pada <strong>baris 7</strong>:
<ul>
 	<li><code>index.php</code> untuk menu utama Dashboard</li>
 	<li><code>edit.php</code> untuk menu utama Posts</li>
 	<li><code>upload.php</code> untuk menu utama Media</li>
 	<li><code>edit.php?post_type=page</code> untuk menu utama Pages</li>
 	<li><code>edit-comments.php</code> untuk menu utama Comments</li>
 	<li><code>edit.php?post_type=sebuah_custom_post_type</code> untuk menu utama dari sebuah custom post type</li>
 	<li><code>themes.php</code> untuk menu utama Appearance</li>
 	<li><code>plugins.php</code> untuk menu utama Plugins</li>
 	<li><code>users.php</code> untuk menu utama Users</li>
 	<li><code>tools.php</code> untuk menu utama Tools</li>
</ul>
</li>
</ul>
<h2>Membuat Menu Utama dan Submenu Terpisah</h2>
Kali ini, kita akan membuat sebuah menu utama beserta beberapa submenunya di dashboard. Biasanya, ini dilakukan jika plugin membutuhkan beberapa halaman dan menu terpisah untuk penyediaan fitur-fiturnya maupun sebagai halaman pengaturan.

Pembuatan menu utama pada kode di bawah ini sangat mirip dengan kode sebelumnya. Untuk membuat menu utama, kita akan menggunakan fungsi <a href="https://developer.wordpress.org/reference/functions/add_menu_page/" target="_blank"><code>add_menu_page</code></a>.
<pre><code class="language-php line-numbers">/**
 * Menambahkan menu dan submenu plugin
 */
add_action( 'admin_menu', 'bp_tutorial_main_menu' );
function bp_tutorial_main_menu() {
    $parent_slug = 'bp-tutorial';
 
    add_menu_page(
        __( 'Pengaturan Materi BP', 'belajar-pemrograman' ),
        __( 'Materi BP', 'belajar-pemrograman' ),
        'manage_options',
        $parent_slug,
        'bp_tutorial_material_setting_page',
        'dashicons-book-alt',
        81
    );
 
    add_submenu_page(
        $parent_slug,
        __( 'Pengaturan Snippet BP', 'belajar-pemrograman' ),
        __( 'Snippet BP', 'belajar-pemrograman' ),
        'manage_options',
        $parent_slug . '-snippet',
        'bp_tutorial_snippet_setting_page'
    );
}
 
/**
 * Konten halaman pengaturan materi BP
 */
function bp_tutorial_material_setting_page() {
?&gt;
 
    &lt;div class="wrap"&gt;
        &lt;h1&gt;&lt;?php _e( 'Pengaturan Materi BP', 'belajar-pemrograman' ); ?&gt;&lt;/h1&gt;
        &lt;p&gt;&lt;?php _e( 'Ini merupakan halaman pengaturan materi BP', 'belajar-pemrograman' ); ?&gt;&lt;/p&gt;
    &lt;/div&gt;
 
&lt;?php
}
 
/**
 * Konten halaman pengaturan snippet BP
 */
function bp_tutorial_snippet_setting_page() {
?&gt;
 
    &lt;div class="wrap"&gt;
        &lt;h1&gt;&lt;?php _e( 'Pengaturan Snippet BP', 'belajar-pemrograman' ); ?&gt;&lt;/h1&gt;
        &lt;p&gt;&lt;?php _e( 'Ini merupakan halaman pengaturan snippet BP', 'belajar-pemrograman' ); ?&gt;&lt;/p&gt;
    &lt;/div&gt;
 
&lt;?php
}</code></pre>
<h3>Keterangan</h3>
<ul>
 	<li><strong>Baris 8 - 16</strong> digunakan untuk menambahkan menu utama <code>Materi BP</code>
<pre data-start="8"><code class="language-php line-numbers">    add_menu_page(
        __( 'Pengaturan Materi BP', 'belajar-pemrograman' ),
        __( 'Materi BP', 'belajar-pemrograman' ),
        'manage_options',
        $parent_slug,
        'bp_tutorial_material_setting_page',
        'dashicons-book-alt',
        81
    );</code></pre>
</li>
 	<li><strong>Baris 9</strong>: menentukan judul halaman menu. Judul ini akan digunakan dalam tag <code>&lt;title&gt;&lt;/title&gt;</code></li>
 	<li><strong>Baris 10</strong>: menentukan label menu yang akan digunakan</li>
 	<li><strong>Baris 11</strong>: menentukan minimal <em>capability</em> yang harus dimiliki user untuk mengakses menu</li>
 	<li><strong>Baris 12</strong>: menentukan slug dari menu. Pembuatan submenu dari menu utama ini akan memerlukan slug ini</li>
 	<li><strong>Baris 13</strong>: <code>bp_tutorial_material_setting_page</code> merupakan nama fungsi yang akan dipanggil untuk menampilkan konten dari menu.</li>
 	<li><strong>Baris 14</strong>: menentukan icon pada menu. Icon dapat ditentukan dengan memasukkan url gambar. Silahkan cek daftar parameter add_menu_page. Icon juga dapat ditentukan dengan menambahkan nama kelas CSS Dashicons, seperti yang kita lakukan di sini.</li>
 	<li><strong>Baris 15</strong>: menentukan posisi menu pada bilah menu dashboard. Nilai paling kecil ditempatkan di posisi paling atas.</li>
</ul>
<strong>Selesai.</strong>

<hr />

Terlalu panjang catatannya.. Apakah seperti ini masih disebut snippet? Kuatir kelupaan saja kalau gak dicatat. Lahee, padahal udah ada link ke dokumentasi WordPress. Sudahlah.. Snippet atau bukan, tulisan ini dikelompokkan ke dalam kelompok snippet di website ini. Silahkan kalau mau komen.
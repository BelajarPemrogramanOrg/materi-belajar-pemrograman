---
ID: 436
post_title: >
  Menambah Taxonomy ke URL Post di
  WordPress
author: Muhammad Ikhsan
post_excerpt: |
  <pre><code class="language-php line-numbers">/**
  * Mengganti `%snippet_tag%` dengan nama tag pada link snippet
  */
  add_filter( 'post_type_link', 'bp_tutorial_snippet_link', 1, 2 );
  function bp_tutorial_snippet_link( $post_link, $id = 0 ){
  $post = get_post( $id );
  
  if ( is_object( $post ) &amp;&amp; $post-&gt;post_type == 'snippet' ) {
  $terms = wp_get_object_terms( $post-&gt;ID, 'snippet_tag' );
  if ( $terms ) {
  foreach ( $terms as $term ){ ...</code><div class="open-snippet">Lihat Snippet</div></pre>
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/wordpress/menambah-taxonomy-url-post-wordpress/
published: true
post_date: 2017-02-24 07:59:48
---
Kasus {#kasus .no-mar-top}
-----

Saya telah membuat sebuah custom post type dengan nama `snippet`. Pada opsi `rewrite` untuk rewrite permalink, saya atur slug-nya `snippet/%snippet_tag%`. Slug tersebut dibuat dengan harapan bahwa `%snippet_tag%` akan otomatis diganti dengan nama tag snippet. Sehingga permalink yang dihasilkan untuk custom post type snippet akan menjadi seperti `https://example.com/snippet/sebuah-tag/slug-dari-sebuah-custom-post`. Register custom post type dan taxonomy dilakukan dengan menggunakan kode berikut:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-php .line-numbers}
/**
 * Membuat Custom Post Type (CPT) snippet
 */
add_action( &#039;init&#039;, &#039;bp_tutorial_snippet_custom_post_type&#039; );
function bp_tutorial_snippet_custom_post_type() {
    // Opsi untuk pembuatan CPT
    $args = array(
        &#039;label&#039;               =&gt; __( &#039;Snippet&#039;, &#039;belajar-pemrograman&#039; ),
        &#039;public&#039;              =&gt; true,
        &#039;publicly_queryable&#039;  =&gt; true,
        &#039;show_ui&#039;             =&gt; true,
        // Menentukan fitur-fitur yang akan ditampilkan pada editor post type
        &#039;supports&#039;            =&gt; array( &#039;title&#039;, &#039;editor&#039;, &#039;excerpt&#039;, &#039;author&#039;, &#039;thumbnail&#039;, &#039;comments&#039;, &#039;custom-fields&#039; ),
        &#039;has_archive&#039;         =&gt; &#039;snippet&#039;,
        // hierarchical jika di-set menjadi true, maka post dapat memiliki child post atau subpost
        &#039;hierarchical&#039;        =&gt; false,
        &#039;show_in_menu&#039;        =&gt; true,
        &#039;exclude_from_search&#039; =&gt; false,
        &#039;capability_type&#039;     =&gt; &#039;post&#039;,
        &#039;rewrite&#039;             =&gt; array( &#039;slug&#039; =&gt; &#039;snippet/%snippet_tag%&#039;, &#039;with_front&#039; =&gt; false ),
        &#039;query_var&#039;           =&gt; true,
        &#039;menu_position&#039;       =&gt; 5,
        &#039;menu_icon&#039;           =&gt; &#039;dashicons-book-alt&#039;,
    );
 
    // Daftarkan CPT
    register_post_type( &#039;snippet&#039;, $args );
}
 
/**
 * Membuat custom taxonomy snippet_tag
 */
add_action( &#039;init&#039;, &#039;bp_tutorial_snippet_tag_custom_taxonomy&#039; );
function bp_tutorial_snippet_tag_custom_taxonomy() {
    $args = array(
        &quot;label&quot;              =&gt; __( &#039;Tag Snippet&#039;, &#039;belajar-pemrograman&#039; ),
        &quot;public&quot;             =&gt; true,
        &quot;hierarchical&quot;       =&gt; false,
        &quot;show_ui&quot;            =&gt; true,
        &quot;show_in_menu&quot;       =&gt; true,
        &quot;show_in_nav_menus&quot;  =&gt; true,
        &quot;query_var&quot;          =&gt; true,
        &quot;rewrite&quot;            =&gt; array( &#039;slug&#039; =&gt; &#039;snippet&#039;, &#039;with_front&#039; =&gt; false ),
        &quot;show_admin_column&quot;  =&gt; true,
        &quot;show_in_quick_edit&quot; =&gt; true,
    );
 
    // Daftarkan custom taxonomy dan hubungkan dengan CPT snippet
    register_taxonomy( &quot;snippet_tag&quot;, array( &quot;snippet&quot; ), $args );
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Nah, jika berhenti sampai di situ saja, maka link yang dihasilkan akan berbentuk seperti `https://example.com/snippet/%snippet_tag%/slug-dari-sebuah-custom-post`. Ini bukan seperti yang saya harapkan.

Lalu bagaimana agar saya bisa mengganti `%snippet_tag%` dengan nama tag snippet?

Solusi {#solusi}
------

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-php .line-numbers}
/**
 * Mengganti `%snippet_tag%` dengan nama tag pada link snippet
 */
add_filter( 'post_type_link', 'bp_tutorial_snippet_link', 1, 2 );
function bp_tutorial_snippet_link( $post_link, $id = 0 ){
    $post = get_post( $id );
 
    if ( is_object( $post ) && $post->post_type == 'snippet' ) {
        $terms = wp_get_object_terms( $post->ID, 'snippet_tag' );
        if ( $terms ) {
            foreach ( $terms as $term ){
                if ( 0 == $term->parent ){
                    return str_replace( '%snippet_tag%' , $term->slug , $post_link );
                }
            }
        } else {
            // Jika tidak ditemukan, gunakan default nama tag `uncategorized`
            return str_replace( '%snippet_tag%' , 'uncategorized', $post_link );
        }
    }
 
    return $post_link;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
---
ID: 436
post_title: >
  Menambahkan Custom Taxonomy pada URL
  Custom Post Type
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
  http://belajarpemrograman.org/snippet/wordpress/menambahkan-custom-taxonomy-url-custom-post-type/
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
add_action( 'init', 'bp_tutorial_snippet_custom_post_type' );
function bp_tutorial_snippet_custom_post_type() {
    // Opsi untuk pembuatan CPT
    $args = array(
        'label'               => __( 'Snippet', 'belajar-pemrograman' ),
        'public'              => true,
        'publicly_queryable'  => true,
        'show_ui'             => true,
        // Menentukan fitur-fitur yang akan ditampilkan pada editor post type
        'supports'            => array( 'title', 'editor', 'excerpt', 'author', 'thumbnail', 'comments', 'custom-fields' ),
        'has_archive'         => 'snippet',
        // hierarchical jika di-set menjadi true, maka post dapat memiliki child post atau subpost
        'hierarchical'        => false,
        'show_in_menu'        => true,
        'exclude_from_search' => false,
        'capability_type'     => 'post',
        'rewrite'             => array( 'slug' => 'snippet/%snippet_tag%', 'with_front' => false ),
        'query_var'           => true,
        'menu_position'       => 5,
        'menu_icon'           => 'dashicons-book-alt',
    );
 
    // Daftarkan CPT
    register_post_type( 'snippet', $args );
}
 
/**
 * Membuat custom taxonomy snippet_tag
 */
add_action( 'init', 'bp_tutorial_snippet_tag_custom_taxonomy' );
function bp_tutorial_snippet_tag_custom_taxonomy() {
    $args = array(
        "label"              => __( 'Tag Snippet', 'belajar-pemrograman' ),
        "public"             => true,
        "hierarchical"       => false,
        "show_ui"            => true,
        "show_in_menu"       => true,
        "show_in_nav_menus"  => true,
        "query_var"          => true,
        "rewrite"            => array( 'slug' => 'snippet', 'with_front' => false ),
        "show_admin_column"  => true,
        "show_in_quick_edit" => true,
    );
 
    // Daftarkan custom taxonomy dan hubungkan dengan CPT snippet
    register_taxonomy( "snippet_tag", array( "snippet" ), $args );
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
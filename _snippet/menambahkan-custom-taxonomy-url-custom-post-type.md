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
<h2 id="kasus" class="no-mar-top">Kasus</h2>

Saya telah membuat sebuah custom post type dengan nama <code>snippet</code>. Pada opsi <code>rewrite</code> untuk rewrite permalink, saya atur slug-nya <code>snippet/%snippet_tag%</code>. Slug tersebut dibuat dengan harapan bahwa <code>%snippet_tag%</code> akan otomatis diganti dengan nama tag snippet. Sehingga permalink yang dihasilkan untuk custom post type snippet akan menjadi seperti <code>https://example.com/snippet/sebuah-tag/slug-dari-sebuah-custom-post</code>. Register custom post type dan taxonomy dilakukan dengan menggunakan kode berikut:

<pre><code class="language-php line-numbers">/**
 * Membuat Custom Post Type (CPT) snippet
 */
add_action( 'init', 'bp_tutorial_snippet_custom_post_type' );
function bp_tutorial_snippet_custom_post_type() {
    // Opsi untuk pembuatan CPT
    $args = array(
        'label'               =&gt; __( 'Snippet', 'belajar-pemrograman' ),
        'public'              =&gt; true,
        'publicly_queryable'  =&gt; true,
        'show_ui'             =&gt; true,
        // Menentukan fitur-fitur yang akan ditampilkan pada editor post type
        'supports'            =&gt; array( 'title', 'editor', 'excerpt', 'author', 'thumbnail', 'comments', 'custom-fields' ),
        'has_archive'         =&gt; 'snippet',
        // hierarchical jika di-set menjadi true, maka post dapat memiliki child post atau subpost
        'hierarchical'        =&gt; false,
        'show_in_menu'        =&gt; true,
        'exclude_from_search' =&gt; false,
        'capability_type'     =&gt; 'post',
        'rewrite'             =&gt; array( 'slug' =&gt; 'snippet/%snippet_tag%', 'with_front' =&gt; false ),
        'query_var'           =&gt; true,
        'menu_position'       =&gt; 5,
        'menu_icon'           =&gt; 'dashicons-book-alt',
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
        "label"              =&gt; __( 'Tag Snippet', 'belajar-pemrograman' ),
        "public"             =&gt; true,
        "hierarchical"       =&gt; false,
        "show_ui"            =&gt; true,
        "show_in_menu"       =&gt; true,
        "show_in_nav_menus"  =&gt; true,
        "query_var"          =&gt; true,
        "rewrite"            =&gt; array( 'slug' =&gt; 'snippet', 'with_front' =&gt; false ),
        "show_admin_column"  =&gt; true,
        "show_in_quick_edit" =&gt; true,
    );
 
    // Daftarkan custom taxonomy dan hubungkan dengan CPT snippet
    register_taxonomy( "snippet_tag", array( "snippet" ), $args );
}
</code></pre>

Nah, jika berhenti sampai di situ saja, maka link yang dihasilkan akan berbentuk seperti <code>https://example.com/snippet/%snippet_tag%/slug-dari-sebuah-custom-post</code>. Ini bukan seperti yang saya harapkan.

Lalu bagaimana agar saya bisa mengganti <code>%snippet_tag%</code> dengan nama tag snippet?

<h2 id="solusi">Solusi</h2>

<pre><code class="language-php line-numbers">/**
 * Mengganti `%snippet_tag%` dengan nama tag pada link snippet
 */
add_filter( 'post_type_link', 'bp_tutorial_snippet_link', 1, 2 );
function bp_tutorial_snippet_link( $post_link, $id = 0 ){
    $post = get_post( $id );

    if ( is_object( $post ) &amp;&amp; $post-&gt;post_type == 'snippet' ) {
        $terms = wp_get_object_terms( $post-&gt;ID, 'snippet_tag' );
        if ( $terms ) {
            foreach ( $terms as $term ){
                if ( 0 == $term-&gt;parent ){
                    return str_replace( '%snippet_tag%' , $term-&gt;slug , $post_link );
                }
            }
        } else {
            // Jika tidak ditemukan, gunakan default nama tag `uncategorized`
            return str_replace( '%snippet_tag%' , 'uncategorized', $post_link );
        }
    }

    return $post_link;
}
</code></pre>
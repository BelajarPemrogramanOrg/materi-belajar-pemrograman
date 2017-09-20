---
ID: 761
post_title: Menggunakan AJAX di WordPress
author: Muhammad Ikhsan
post_excerpt: |
  Pertama, <em>enqueue</em> file JavaScript yang digunakan untuk melakukan request dan menerima respon menggunakan AJAX. (Misal, nama file-nya <code>my-script.js</code>)
  
  <pre class="language-php line-numbers"><code>add_action( 'wp_enqueue_scripts', 'my_enqueue_ajax_script' );
  function my_enqueue_ajax_script() {
  wp_enqueue_script( 'my-script', WP_PLUGIN_URL . '/my_plugin/assets/my-script.js', array( 'jquery' ) );
  wp_localize_script( 'my-script', 'my_script', array( 'ajaxurl' => admin_url( 'admin-ajax.php' ) ) );
  }</code></pre>
  
  Kemudian, buat kode JavaScript untuk mengirimkan request dan menangani respon dari server.
layout: snippet
permalink: >
  http://belajarpemrograman.org/snippet/wordpress/menggunakan-ajax-di-wordpress/
published: true
post_date: 2017-09-20 08:01:19
---
1.  Enqueue file JavaScript yang digunakan untuk melakukan request dan menerima respon menggunakan AJAX. (Misal, nama file-nya `my-script.js`)

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-php .line-numbers}
    add_action( 'wp_enqueue_scripts', 'my_enqueue_ajax_script' );
    function my_enqueue_ajax_script() {
    	wp_enqueue_script( 'my-script', WP_PLUGIN_URL . '/my_plugin/assets/my-script.js', array( 'jquery' ) );
    	wp_localize_script( 'my-script', 'my_script', array( 'ajaxurl' => admin_url( 'admin-ajax.php' ) ) );
    }</code></pre>
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

2.  Buat kode JavaScript untuk mengirimkan request dan menangani respon dari server.

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-javascript .line-numbers}
    var post_data = {
    	action : 'my_action',
    	var1   : 'nilai dari var1'
    };

    $.ajax({
    	url      : my_script.ajaxurl,
    	type     : 'post',
    	dataType : 'json',
    	data     : post_data,
    	success  : function( response ) {
    		// Jika sukses
    	}
    });
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

3.  Buat kode PHP untuk menangani request dan mengirimkan respon dari client/browser.

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-php .line-numbers}
    add_action( 'wp_ajax_my_action', 'my_action' );
    function my_action() {
    	$var1 = $_POST['var1'];

    	$data = array();
    	$data['content'] = $var1;
    	echo json_encode( $data );

    	wp_die();
    }
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~